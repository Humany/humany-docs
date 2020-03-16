# How does SEO for widgets in Ace Knowledge work?

SEO (Search Engine Optimization), or Search Engine Optimization, is a collective name for the various methods used to get a web page to rank as high as possible in search results on different search engines such as Google. Here is a description of how our SEO service works.

### SEO service

When you enable SEO on a widget, the content is indexed by our SEO service and the result is stored in a database. The content of this database (pre-rendered HTML pages) can then be made available when the customer creates and adds a SEO component to their web server. Only inline widgets supports our SEO service as each view in the widget is required to have its own unique URL.

### Overview

![](img/schema_overview.png)

The image above describes the flow of our SEO service. In this scenario, we assume that the client has built and published an SEO component, which contacts our SEO service, on their web server.

[You can read more about how to create your own SEO component here](tutorial-seo-full.md).  

1.  The customers administrator enables SEO on a widget in the ACE Knowledge management interface.
2.  ACE knowledge core registers the widget in the SEO Service.
3.  SEO crawlers ask the SEO Service for jobs.
    *   The SEO Crawler starts indexing the widget.
    *   The SEO Crawler reports HTML, CSS and internal links back to the SEO Service.
    *   The process continues until all pages are indexed
4.  The customers web page is indexed by the search engine.
5.  Visitors search on the search engine and are linked to the customer's website

In steps 4 and 5, the visitor's browsers renders the page as follows:

*   The customer's web server contacts ACE Knowledge's SEO Service to obtain pre-rendered HTML.
*   The customer's web server sends pre-rendered HTML among the first calls to the visitor - the content is displayed immediately.
*   The visitor's browser continues to fetch and load the widget.
*   When the widget is complete, its contents is displayed.

![](img/schema_detailed.png)

### Queues

ACE knowledge's SEO Service has two queues with different priorities for indexing content in the widget.

**High-priority queue**

The high-priority-queue responds to changes in ACE Knowledge Core, eg. in guides or when activating SEO on a widget. Changes detected in the high-priority queue are indexed directly and are available within 1-2 minutes.

**Low-priority queue**

One example of a change running in the low-priority-queue is statistics that update the  <wbr>ACE Knowledge's top lists. Changes detected in the low-priority-queue are indexed once a day, outside of office hours, to reduce the load on ACE knowledge's servers. The low-priority-queue is run only if the high-priority queue is empty.


# How do I enable SEO for a widget?
Our latest SEO service works for inline TODO widgets from version 4 and above. To enable SEO for a widget, you edit it under the "Enable Search Engine Optimization" section and change the setting from "SEO is not enabled" to any of the following alternatives:

1.  Index on your application domain _yourApplication.humany.net_
    *   This enables search engine optimization for your Ace Knowledge widgets domain. A user who finds your content on Google will land on a page in this domain and be redirected to the URL you specified in step 3 of the "Embed on your site" section under the SEO section when editing your widget. [Read more here.](tutorial-seo-light.md)
2.  Index on Own Domain
    *   This allows you to have your widgets contents indexed on a domain that you control yourself. This requires that you create and add an SEO component to your server. [Read more here.](tutorial-seo-full.md)

_Note: Related to the launch of our new SEO service for version 4 widgets and above, it will no longer be possible to enable SEO on older widget versions. In this case, the implementation needs to be upgraded. However, if SEO is already enabled on an older widget, this SEO will continue to work._

## Example
For widgets (in implementation V4 or higher) with SEO enabled, example can be seen on https://seo-example.humany.net
