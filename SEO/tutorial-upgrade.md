## SEO Light
No changes on your site are required. See [tutorial-seo-light.md](tutorial-seo-light.md)  

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