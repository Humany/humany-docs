# Notices API
This feature requires an application with a widget which has defined notice categories.

## Request
  GET https://**:application-name**.humany.net/**:widget-name**/notices/**:tab-name**

## Response
```
{
    // Notices are small notifications displayed in specific areas of the interface (top, middle, bottom)
    "Notices":[
        {
            // Content to display
            "Body":"<p>html</p>\n",
            "FirstPublishedDate":"2017-06-21T09:18:30.8229144Z",
            "Id":4329,
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

## Example
```
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
