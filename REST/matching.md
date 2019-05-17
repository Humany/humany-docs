---
path: '/rest/matching'
date: '2017-11-07'
title: 'Matching'
---

> This documentation is valid for widget V1-V4

# Matching API

Search for answers and retrieve content from the knowledge base.

## General URL pattern

The subsequent API:s assume the request follows the following general pattern.

| Segment               | Pattern           					| Type 		| Information     	|
|-----------------------|---------------------------------------|-----------|--------------------|
| Application domain    | ```https://:subdomain.humany.net``` 	|       	| This identifies your Knowledge-Base |
| Projection            | ```/:projection```          			| string	| This is the name of the interface to interact with. This configures which (sub)set of the Knowledge Base to make available for consumption |
| API                   | ```/[guides,categories]```          	|       	| Specific content to retrieve |
| Guide ID (optional)   | ```/:guideId```                     	| number	| Id to specific guide |
| Connection ID (optional) | ```/:connectionId```             	| string	| Identifier to answer version within a guide |
| Client (required)     | ```?client=:clientId```       		| GUID		| This identifies the user interacting with the API |
| Answer version (optional) | ```&perspective=:perspective```	| Default, string	| The answer version to display, this is either "Default" or the name of the answer version |
| Site (optional)     	| ```&site=:site```             		| string	| The web address the user was visiting when first looking for help |
| Phrase (optional)     | ```&phrase=:phrase```       			| string	| The search phrase |
| Skip (optional)       | ```&skip=:skip```           			| number	| The number of items to omit from the start of the returned matches |
| Take (optional)       | ```&take=:take```           			| number	| The maximum number of items include in the matches |
| Categories (optional) | ```&categories=:categories```   		| number[]	| Filter guides by category |
| Tags (optional)       | ```&tags=:tags```   					| number[]	| Filter guides by tag |
| Reader (optional)     | ```&reader=:reader```   				| string	| Resolve guide read status per user |
| Attributes (optional) | ```&attributes=:attributes``` 		| string	| Filter guides by attribute value |
| Sorting (optional)    | ```&sorting.type=:sorting```   		| popularity, title, lastmodified, firstpublished	| Sort guides by |
| Sort direction (optional) | ```&sorting.direction=:sortingDirection```	| ascending, descending	| Sort guides by |
| Include categories (optional) | ```&includeCategories=:includeCategories```	| boolean	| Sort guides by |
| Expand categories (optional) | ```&expand=:categoryExpansion```	| none, children, descendants	| Include sub-cateogires with categories |

## List/Search guides

This API is intended for retrieving a ranked list of guides and searching for guides.

Example (get guides ranked by popularity):
```
POST https://support.humany.net/api-exempel/guides?client=453430cb-ad3e-4186-846a-7de22e4a525d
```

Example (sesarch guides ranked by relevance):
```
POST https://support.humany.net/api-exempel/guides?client=453430cb-ad3e-4186-846a-7de22e4a525d&phrase=hello
```

[Try online](https://codesandbox.io/s/lx66003r57)

## Get single guide

Example (get guide by id):
```
POST https://support.humany.net/api-exempel/guides/697?client=453430cb-ad3e-4186-846a-7de22e4a525d&phrase=hello
```

[Try online](https://codesandbox.io/s/moyr2x8wwp)

