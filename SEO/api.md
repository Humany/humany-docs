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

Common codes
- HTTP CODE 403 - if the page or parts of the page are not publicly accessible
- HTTP CODE 404 - if the page has not been indexed yet; or the page or parts of the page do not exist
- HTTP CODE 599 - if the page has errors and cannot be rendered correctly, custom HTTP code `599 Content not Humany-SEO compatible`
- HTTP CODE 200 - OK

### HTTP headers
All header values are URL-encoded, to support line-breaks and non-ASCII characters.

All timestamps are UTC, sortable ISO 8601.

- `HumanyCanonical` - canonical URL
- `HumanyContentRenderedOn` - time when the page was indexed
- `HumanyContentModifiedOn` - latest time when the page contents has changed, by comparison of HTML/CSS and headers
- `HumanyCssHref` - optional, fully qualified URL to CSS that must be included on the page, preferably in the `<head>` tag
- `HumanyPageTitle` - optional, available on guide and category pages
- `HumanyGuideModifiedOn` - optional, latest time when the guide was modified

### HTML and CSS
Response body is HTML, which can include inline CSS (used mainly in V5). Whole body can be directly injected into your page. These is no need to separate HTML and CSS.
