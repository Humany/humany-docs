# SEO Service API reference

## Request
Make a real-time HTTP request to Humany servers to receive pre-rendered HTML/CSS.

`https://seo.humany.net/v2/{tenant}/{widget}/{route}?{querystring}&seoBaseUrl={seoBaseUrl}`

Parameter | Description | Required | Example
--- | --- | --- | ---
`tenant` | Your customer identifier, same as in Humany Core administration | yes | demobolaget
`widget` | From widgets base-URL | yes | inline_demo
`route` | Route within the widget | optional
`querystring` | | optional
`seoBaseUrl` | Change widget links to be based upon `seoBaseUrl`. Should start with `/`, which is automatically added if not provided. | optional | %2fkundtjanst

URL that you are requesting will be canonized according to the widget URL canonization rules. Querystring parameters will be sorted and insignificant parameters will be removed. Rules for canonization **will change over time**.

## Response

### Timeout and response code
The SEO service should be expected to respond within 4000ms. **Timeout or any error code should be treated as non-signifact for the end-user and the page should be delivered to the end-user as if SEO was not active.** Timeout and errors should be logged for performance monitoring and investigation of errors.

Fonts, images and CSS stylesheets are considered **non-significant resources** - errors while fetching these are ignored. An error while fetching any other resource type cause the page to be considered erroneous. JavaScript parsing or execution errors are ignored.

The page/widget is expected to mark its "load successful" event. If this does happen within the timeout, the page is considered erroneous.

Common codes
- HTTP CODE 200 - OK
- HTTP CODE 403 - if the page or a significant resource are not publicly accessible
- HTTP CODE 404 - if the page has not been indexed yet; or the page or a significant resource does not exist
- HTTP CODE 5xx - if the page or a significant resource cannot be fetched
- HTTP CODE 598 - if the page timed out before "load successful" event, custom HTTP code `598 Content not Humany-SEO compatible`
- HTTP CODE 599 - if a request to the page or a significant resource was blocked by browser security, unlikely to happen, CORS checks are disabled, custom HTTP code `599 Request blocked in browser`

### HTTP headers
All header values are URL-encoded, to support line-breaks and non-ASCII characters.

All timestamps are UTC, sortable ISO 8601.

- `HumanyCanonical` - canonical URL
  - Your server should inject `<link rel="canonical" href="{value}" />` into `<head>`. Remember to HTML-encode the value.
- `HumanyContentRenderedOn` - time when the page was crawled and rendered by ACE Knowledge (Humany)
- `HumanyContentModifiedOn` - latest time when the page contents has changed, by comparison of HTML/CSS and headers
- `HumanyCssHref` - optional, fully qualified URL to CSS that must be included on the page, preferably in the `<head>` tag
- `HumanyPageTitle` - optional, available on guide and category pages, can be used as page `<title>` in `<head>`
- `HumanyPageDescription` - optional, available on guide pages
  - Your server should inject `<meta name="description" content="{value}"/>` into `<head>`. Remember to HTML-encode the value.
- `HumanyRobotsAllowIndexing` - optional, default is `true`. If present and the value is `false`, then the page (currenly guides only) has requested not to be indexed by search engines.
  - Your server should inject `<meta name="robots" content="noindex"/>` into `<head>`.
  - HTML content will be empty.
  - Headers `HumanyCssHref`, `HumanyPageTitle` and `HumanyPageDescription` will not be provided.
  - This does not imply no-follow.
- `HumanyGuideModifiedOn` - optional, available on guide pages, latest time when the guide was modified

### HTML and CSS
Response body is HTML, which can include inline CSS (used mainly in V5). Whole body can be directly injected into your page. These is no need to separate HTML and CSS.
