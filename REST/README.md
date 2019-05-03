# REST API

API access require a valid Humany application subscription and an *interface* that has been configured from within the administration portal.

## API structure

With the application and interface prerequisites in place you can access the API using GET/POST requests. The API accepts and emits JSON-formatted results and conforms to the following pattern:

| Segment               | Pattern           | Information |
|-----------------------|-------------------|-|
| Scheme                | https://          | |
| Application subdomain | :subdomain        | This identifies your Knowledge-Base |
| Humany domain         | .humany.net       | |
| Projection            | /:projection      | This is the name of the interface to interact with. This configures which (sub)set of the Knowledge Base to make available for consumption |
| API                   | /:api             | API options use different keywords for this segment |
| Optional              | /:extra           | Depending on the specific API zero or more additional segments may be used |

## Query strings

Additionally query string parameters are passed. These query parameters are shared across multiple API:s

| Name   | Purpose |
|--------|---------|
| client | A GUID that uniquely identifies a user. This parameter should remain the same throughout the lifetime of the user |
| site | The canonical URL of page the user was visiting when first looking for help |
| skip | The number of items in a list to skip |
| take | The number of items in a list to include |
| p.* | The pattern for additional parameters (a.k.a. entities) to pass in |

## Examples

**Get the guide with id 123**

```
POST https://support.humany.net/service-portal/guides/123
```

**List all contacft methods**

```
GET https://support.humany.net/service-portal/contacts
```

## Authentication

Access to the API can be made pubic or access restricted from wthin the administration portal. When access-restricting an interface using the login authentication method additional information may be passed which indicates an URL where the user can log in. 

## Config request

To retreive information about the widget iself such as texts, UI settings etc.

V4:
```
-
```

V3:
```
 /:projection/config
```

## Matching API

Search for answers and retrieve content from the Bnowledge Base.

[Read more](matching.md)

## Notices API

List notices, news and alerts.

[Read more](notices.md)

## Contact API

List and navigate to contact methods and post form data.

[Read more](contact.md)

### Webhook

Pass information posted to the **Web Service** contact method to an external web hook and display the response to the user in the web widget.

[Read more](webhook.md)

## Conversation API

This API is subject to change and supported.

## Knowledge Base API

This API is subject to change and supported.
