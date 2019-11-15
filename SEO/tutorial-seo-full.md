NOTE: This is widgets **V4** documentation. The [widgets **V3** documentation is over here](https://github.com/Humany/humany-docs/tree/v3/seo). For [more information about widget versions check here](https://github.com/Humany/humany-docs/widgets/versions.md).

See [Known issues](known-issues.md)  

# Setting up SEO support for widgets
This tutorial describes, in a few simple steps, how to implement full SEO support for your Humany widget. The full SEO support is currently only available for Inline widgets.

Take a look at [this repository](https://github.com/Humany/humany-customer-seo) for a reference implementation in .NET Core 3.
[Here](api.md) is the API documentation for the SEO service.

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
Moving on to the controller, you will use the above `path` parameter to call the Humany SEO service. The call is a simple HTTP GET request containing query strings with the current `path` and the `seoBaseUrl`.

**Pattern for the request:**
```
GET https://seo.humany.net/v2/{your-application-name-in-ace-knowledge}/{widget-name}/{path}?seoBaseUrl={seoBaseUrl}
```
In our example, lets assume the Inline widget is named "customer-service", and your application in ACE Knowledge is called "seo-customer". The request for the start-view would then look like this:
```
GET https://seo.humany.net/v2/seo-customer/customer-service/?seoBaseUrl=/help
```
For a request to www.example.com/help/contact, the call to the Humany SEO service should look like this:
```
GET https://seo.humany.net/v2/seo-customer/customer-service/contact?seoBaseUrl=/help
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
  queryString.Add("seoBaseUrl", basePath);

  // Build the remote url and append the above query strings
  var myApplication = "seo-customer";
  var url = new UriBuilder($"https://seo.humany.net/v2/{myApplication}/{widgetName}/path");
  url.Query = queryString.ToString();

  // Download and return content as a string (using HTTP GET)
  using (var client = new WebClient())
    return client.DownloadString(url.ToString());
}
```

The response from humany also contains some headers that can be useful in order to improve SEO. Please refer to the [API documentation](api.md).

### 3. Display the widget html in your view
When the html is fetched from the Humany SEO service you are ready to complete the view. Just put the response html in the same place the widget should be displayed, and make sure the parent element has the correct `id` and `data-base-path` attributes. In ASP.NET MVC with Razor it would look something like this:
```aspx
	<div id="humany_{your-widget-uri-name}" data-base-path="{seoBaseUrl}">
		@Html.Raw(ViewBag.WidgetHtml)
	</div>
```
If you view the the result you should see the widget, but without styling. To apply the styling, add a reference to the following stylesheet:
```html
<link rel="stylesheet" type="text/css" href="{the-link-in-CssHref-header}" />
```


### 4. Bootstrap the Humany implementation
The final task is to activate the default javascript widget script. Simply include the installation code for the implementation the widget belongs to. The first part of the code code is available in the Humany portal on respective widget or implementation, e.g.:

	<script>
    (function (a, b, c, d, e, f, g) {
      for (var h, i = /[?&]{1}(humany[^=]*)=([^&#]*)/g; h = i.exec(a.location.search);)c += (-1 < c.indexOf("?") ? "&" : "?") + h[1] + "=" + h[2];
      f = b.createElement(e), f.async = !0, f.src = c, g = b.getElementsByTagName(e)[0], g.parentNode.insertBefore(f, g), a[d] = a[d] || { _c: [], configure: function () { a[d]._c.push(arguments) } }; var j = d.toLowerCase(); a[j] = a[j] || { _c: [], configure: function () { a[j]._c.push(arguments) } }
    })(window, document, "//{your-application-name-in-ace-knowledge}.humany.net/default/embed.js", "Humany", "script");

    // push-state config:
    window.humany.configure((config) => { config({ type: '@humany/inline-widget' }).routing({ mode: 'browser', basePath: '{base-path-goes-here}' }) });
	</script>
		
The Humany embed script will now identify the pre-compiled html and replace it with the default javascript widget, working and looking the same way as you are used to. Regular users will probably not see any difference, but we have now enabled the widget to be indexed by Google and other search engines.

In addition, since the different views in the widget is now represented by a real physical page, we can take advantage of `pushState`, which is available in all modern browsers. This gives the advantage of friendly urls during widget operations which also conform to a SEO page. This is done by the second part of the script above. **Note** that you will need to set `basePath` in the script!

## Meta data
To be able to render a proper title and description for each page, the SEO Service provides a response header for `HumanyPageTitle`. Use it to construct the head part of your page.
