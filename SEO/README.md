> NOTE: This is widgets **V3** documentation. The [widgets **V4** documentation is over here](https://github.com/Humany/humany-docs/). For [more information about widget versions check here](https://github.com/Humany/humany-docs/widgets/versions.md).

# Setting up SEO support for widgets
This tutorial describes, in a few simple steps, how to implement full SEO support for your Humany widget. The full SEO support is currently only available for Inline widgets.

### 1. Decide a location and define routes for your inline widget
Decide where on your website you want the widget to be rendered. All requests, including requests for sub-routes, should be directed to a single view that is responsible for rendering the SEO-content and activate the widget.

In this tutorial we will assume the following url: `www.example.com/help`

All traffic to `www.example.com/help` (including sub-routes) should be directed to a single view. This is done differently depending on your platform and we will add more code examples upon request.

In ASP.NET MVC this is how you would configure the RouteCollection:

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
  routes.MapRoute(
    name: "Help",
    url: "help/{*path}",
    defaults: new { controller = "Help", action = "Index", path = UrlParameter.Optional }
  );
}
```
		
The `{*path}` segment will copy everything after the slash to a parameter in your controller action. This path is important. You will use it when calling the Humany SEO service to retreive the correct content.

### 2. Fetch HTML from the Humany SEO service
Moving on to the controller, you will use the above `path` parameter to call the Humany SEO service. The call is a simple HTTP GET request containing query strings with the current `path` and the `basePath`.

**Pattern for the request:**
```
GET https://{tenant}.humany.net/{widget-name}/{path}?mode=seo&base={basePath}
```
In our example, lets assume the Inline widget is named "customer-service". The request for the start-view would then look like this:
```
GET https://{tenant}.humany.net/customer-service/?mode=seo&base=/help
```
For a request to www.example.com/help/contact, the call to the Humany SEO service should look like this:
```
GET https://{tenant}.humany.net/customer-service/contact?mode=seo&base=/help
```
The result from the service is plain html and is ready to be rendered as part of your default layout.

Sample C# code for the controller action:
```csharp
public ActionResult Index(string path)
{
  ViewBag.WidgetHtml = DownloadWidgetHtml("customer-service", "/help", path);
  return View();
}

private string DownloadWidgetHtml(string widgetName, string basePath, string path)
{
  // Add "mode" and "base" to the existing query string collection
  var queryString = HttpUtility.ParseQueryString(Request.Url.Query);
  queryString.Add("mode", "seo");
  queryString.Add("base", basePath);

  // Build the remote url and append the above query strings
  var url = new UriBuilder(String.Concat("https://{tenant}.humany.net/", widgetName, "/", path));
  url.Query = queryString.ToString();

  // Download and return content as a string (using HTTP GET)
  using (var client = new WebClient())
    return client.DownloadString(url.ToString());
}
```

The response from humany also contains some headers that can be useful in order to improve SEO:
* Page-Canonical-Url
* Page-Description
* Page-Title

### 3. Display the widget html in your view
When the html is fetched from the Humany SEO service you are ready to complete the view. Just put the response html in the same place the widget should be displayed. In ASP.NET MVC with Razor it would look something like this:
```aspx
	<div class="main">
		@Html.Raw(ViewBag.WidgetHtml)
	</div>
```
If you view the the result you should see the widget, but without styling. To apply the styling, add a reference to the following stylesheet:
```html
<link href="//{tenant}.humany.net/{implementationName}/widgets.css" rel="stylesheet" type="text/css" />
```
**Important:** Pay attention to the `implementationName` parameter above. It must be replaced with the URI friendly name of the implementation the current Inline widget belongs to.

### 4. Bootstrap the Humany implementation
The final task is to activate the default javascript widget script. Simply include the installation code for the implementation the widget belongs to. The code is available in the Humany portal on respective widget or implementation, e.g.:

	<script>
		(function (n, t, i, r, u, f, e) { f = t.createElement(u); f.async = !0; f.src = i; e = t.getElementsByTagName(u)[0]; e.parentNode.insertBefore(f, e); n[r] = n[r] || { _c: [], configure: function (t) { n[r]._c.push(t) } } })
		(window, document, "//{tenant}.humany.net/default/embed.js", "Humany", "script");
	</script>
		
The Humany embed script will now identify the pre-compiled html and replace it with the default javascript widget, working and looking the same way as you are used to. Regular users will probably not see any difference, but we have now enabled the widget to be indexed by Google and other search engines.

In addition, since the different views in the widget is now represented by a real physical page, we can take advantage of `pushState`, which is available in all modern browsers. This gives the advantage of friendly urls during widget operations which also conform to a SEO page. This is done automatically by the bootstrapper and no additional configuration is required. The widget routing will use the `basePath` you specified in your request to the Humany SEO service, and construct all widget links on top of that.

## Meta data
To be able to render a proper title and description for each page, the SEO Service provides response headers for `Page-Title` and `Page-Description`. Use them to construct the head part of your page.
