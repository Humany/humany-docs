> This documentation is valid for widget V1-V4

# Matching API

Search for answers and retrieve content from the knowledge base.

## General URL pattern

The subsequent API:s all assume the request is prefixed using the following pattern.

| Segment               | Pattern           | Information     |
|-----------------------|-------------------|-----------------|
| Application domain    | ```https://:subdomain.humany.net``` | This identifies your Knowledge-Base |
| Projection            | ```/:projection```                  | This is the name of the interface to interact with. This configures which (sub)set of the Knowledge Base to make available for consumption |
| API                   | ```/[guides|categories]```           | Specific content to retrieve |
| Guide ID (optional)   | ```/:guideId```                     | Id to specific guide |
| Connection ID (optional) | ```/:connectionId```             | Identifier to answer version within a guide |


## List/Search Guides

This API is intended for retrieving a ranked list of guides and searching for guides.

| Query               | Pattern           | Information     |
|-----------------------|-------------------|-----------------|
| client (required)     | ```client=:clientId<GUID>```    | This identifies the user interacting with the API |
| site (optional)     | ```site=:site<string>```                  | The web address the user was visiting when first looking for help |
| phrase (optional)     | ```phrase=:phrase<string>```                  | The search phrase |
| skip (optional)       | ```skip=:skip<number>```                  | Number of items to omit from the start of the returned list |
| take (optional)       | ```take=:take<number>```                  | Number maximum number of items include in the list |

Example:
```
POST https://support.humany.net/api-exempel/guides
```

[Try online](https://codesandbox.io/s/jlvlkm18z5)

