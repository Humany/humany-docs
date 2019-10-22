# Upgrading SEO

**We strongly recommend creating a copy of the widget before upgrading.**
* Create a copy of the widget
* Upgrade the copy to an implementation with Widget Version >= 4
* (If using full SEO) Make the necessary changes to your site (see below) in your test environment
* Test!
* Rename your widget copy to its original name (and make the corresponding name changes on your site)

## SEO Light
No changes on your site are required. See [tutorial-seo-light.md](tutorial-seo-light.md)  
**Note** that the link to your site from the top of the widget page is missing in SEO v2.0, but will be re-implemented in v2.1.  
See [known-issues.md](known-issues.md).

## Full SEO
See how to implement from scratch: [tutorial-seo-full.md](tutorial-seo-full.md)  

The API changes are as follows:
* The service now resides at `https://seo.humany.net` instead of `https://{your-application-name-in-ace-knowledge}.humany.net`
  * Use `https://seo.humany.net/{your-application-name-in-ace-knowledge}/{widget-name}/{path}?seoBaseUrl={seoBaseUrl}`
  * **Not** `https://{your-application-name-in-ace-knowledge}.humany.net/{widget-name}/{path}?mode=seo&base={base}`
* Response headers have changed:
  * `Page-Description` has been removed
  * `Page-Title` has been changed to `HumanyPageTitle`
  * `Page-Canonical-Url` has been changed to `HumanyCanonicalUrl`
  * Additional headers are available
* An additional line of configuration is needed in the JavaScript:
  * `window.humany.configure((config) => { config({ type: '@@humany/inline-widget' }).routing({ mode: 'browser', basePath: '{base-path-goes-here}' }) });`
* Add stylesheet link in `head` section `<link rel="stylesheet" type="text/css" href="{the-link-in-CssHref-header}">`
* The element where the widget is rendered should have the id `humany_{your-widget-uri-name}` and the attribute `data-base-path="{seoBaseUrl}"`
