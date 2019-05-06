> This documentation is valid for widget V1-V4

# Notices API
This feature requires an application with a widget which has defined notice categories.

## Request

```
GET https://:application-name.humany.net/:widget-name/notices/:page-name-or-notice-id
```

| Segment                | Pattern           | Information     |
|------------------------|-------------------|-----------------|
| Application domain     | ```https://:subdomain.humany.net``` | This identifies your Knowledge-Base |
| Projection             | ```/:projection```                  | The name of the widget which has been configured to provide notices. |
| API                    | ```/notices```                      | The notices API |
| Page name or notice Id | ```/:page-name-or-notice-id```      | If an id (integral value) is specified, the corresponding notice ("single-item") will be returned. |

### Special case regarding notice translations

Given that the security settings of the current widget doesn't require authentication, and that the current notice is accessible on the current widget, you may also use this route to access the notices translations. The translations of a notice, if any, can be found on the "Translations" property.

If the name of a page/tab is specified, returns the page along with the configured notices. (To find the name of a page open the widget and look at the URL when navigating to the page, e.g. for http://www.yoursite.se/help#humany-help=/**text1** then text1 would be the page name)

If the parameter is omitted, notices for the FAQ page will be returned.

### Custom parameters
To pass custom parameters add a query string with the name of that paramter prefixed with "p.", e.g. ?p.customertype=value

## Response (single item)
```javascript
{
    "Body":"<p>html</p>\n",
    "Attributes":{},
    "Categories":[3324,3323],
    "Created":"2017-03-29T08:46:58.79078Z",
    "FirstPublishedDate":"2017-03-29T08:46:58.8338124Z",    
    "Id":3325,
    "Translations": {
      "sv": 3325,
      "en": 1129,
      "da": 108
    },
    "Modified":"2017-03-29T08:46:58.79078Z",
    "Tags":[],
    "Read":null,
    "RelativeUrl":"n3325/",
    "Title":"text",
    "Type":"listNotice"
}
```

## Response (page)
```javascript
{
    // Notices are small notifications displayed in specific areas of the interface (top, middle, bottom)
    "Notices":[
        {
            // Content to display
            "Body":"<p>html</p>\n",
            "FirstPublishedDate":"2017-06-21T09:18:30.8229144Z",
            "Id":4329,
            "Translations": {
                "sv": 4329,
                "en": 556,
                "da": 901
            },
            "Modified":"2017-06-21T09:18:30.7953853Z",
            // Specified area from admin
            "Type":"noticeRowTop"
        }
    ],
    // NoticeLists are larger notifications displayed in specific order specified in admin.
    // They can either have a title and be expandable or be displayed as inline html
    "NoticeLists":[
        {
            "Id":3323,
            "Symbol":null,
            "Title":"Synlig",
            "Notices":[],
            "ListNotices":[
                {
                    "Body":"<p>html</p>\n",
                    "Attributes":{},
                    "Categories":[3324,3323],
                    "Created":"2017-03-29T08:46:58.79078Z",
                    "FirstPublishedDate":"2017-03-29T08:46:58.8338124Z",
                    "Id":3325,
                    "Translations": {
                      "sv": 3325,
                      "en": 1129,
                      "da": 108
                    },
                    "Modified":"2017-03-29T08:46:58.79078Z",
                    "Tags":[],
                    "Read":null,
                    "RelativeUrl":"n3325/",
                    "Title":"text",
                    "Type":"listNotice"
                }
            ]
        }
    ]
}
```

## Example (page)
```javascript
// REQUEST

var applicationName = "help";
var interfaceName = "admin-help-en";
var tabName = "";

$.ajax({
    url: "https://" + applicationName + ".humany.net/" + interfaceName + "/notices/" + tabName,
    dataType: "json",
    type : "GET",
    success : function(r) {
        console.log(r);
    }
});

// OUTPUT

{
    "Name":"index",
    "Notices":[
        {
            "Body":"<p>topp</p>\n",
            "Attributes":{},
            "Categories":[4325],
            "Created":"2017-06-21T09:18:30.7953853Z",
            "FirstPublishedDate":"2017-06-21T09:18:30.8229144Z",
            "Id":4329,
            "Translations": {
              "sv": 4329,
              "en": 556,
              "da": 901
            },
            "Modified":"2017-06-21T09:18:30.7953853Z",
            "Tags":[],
            "Read":null,
            "RelativeUrl":"n4329/",
            "Title":"topp",
            "Type":"noticeRowTop"
        }
    ],
    "NoticeLists":[
        {
            "Id":3323,
            "Symbol":null,
            "Title":"Synlig",
            "Notices":[],
            "ListNotices":[
                {
                    "Body":"<p>Listnotiser visas efter att man klickar på titeln</p>\n",
                    "Attributes":{},
                    "Categories":[3324,3323],
                    "Created":"2017-03-29T08:46:58.79078Z",
                    "FirstPublishedDate":"2017-03-29T08:46:58.8338124Z",
                    "Id":3325,
                    "Translations": {
                      "sv": 3325,
                      "en": 1129,
                      "da": 108
                    },
                    "Modified":"2017-03-29T08:46:58.79078Z",
                    "Tags":[],
                    "Read":null,
                    "RelativeUrl":"n3325/",
                    "Title":"Listnotis",
                    "Type":"listNotice"
                }
            ]
        }
    ]
}
```
