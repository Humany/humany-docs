# REST API

API access require a valid Humany application subscription and an *interface* that has been configured from within the administration portal.

## API structure

With these prerequisites in place GET/POST requests are directed to an URL with the following pattern:

| Scheme | Application subdomain | Humany domain  | Interface name   | API       | Optional | |
|--------|-----------------------|-------------|---------------------|-----------|----------|-|
| | This identifies your Knowledge-Base | | The interface to interact with. It's the means of projecting a (sub)set of the Knowledge Base and make it available for consumption | Different API options use different keywords for this segment | Depending on the specific API additional segments may be used |
| https:// | :your-subdomain     | .humany.net | /:interface-name    | /:api     | /:id-or-other
| e.g.     |                     |             |                     |           |
| https:// | support             | .humany.net | /service-portal     | /guides    | /123 | *Get the guide with id 123*
| https:// | support             | .humany.net | /service-portal     | /contacts  | | *List all contacft methods*

## Query strings

Additionally query string parameters are passed. These query parameters are shared across multiple API:s

| Name   | Purpose |
|--------|---------|
| client | A GUID that uniquely identifies a user. This parameter should remain the same throughout the lifetime of the user |
| site | The canonical URL of page the user was visiting when first looking for help |
| skip | The number of items in a list to skip |
| take | The number of items in a list to include |
| p.* | The pattern for additional parameters (a.k.a. entities) to pass in |

## Authentication

Access to the API can be access restricted from the administration portal. When using login authentication method additional information may be passed which indicates from where the user can log in. 

## Matching API

Search for answers and retrieve content from the knowledge base.

[Read more](matching.md)

## Notices API

List notices, news and alerts.

[Read more](notices.md)

## Contact API

List and navigate to contact methods and post form data.

[Read more](contact.md)

## Conversation API

This API is subject to change and supported.

## Knowledge Base API

This API is subject to change and supported.

### Webhook

Pass information posted to the **Web Service** contact method to an external web hook and display the response to the user in the web widget.

[Read more](webhook.md)
