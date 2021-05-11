# One Widget Floating Template - Subcategories migration instructions

This guide illustrates the process of converting a standard widget created with the Floating template to replace the `guide-category-dropdown` component with the multi-level version of the `guide-category-list` component.

## Step 1: Replace the dropdown component

### Add component defition to `components` object and remove the dropdown definition

```diff
{
  "components": {
+   "guide-category-list": {
+     "type": "guide-category-list",
+     "properties": {
+       "levels": "all",
+       "mode": [{
+         "type": "circles",
+         "scrollable": true
+       },
+       {
+         "type":"pills"
+       }],
+       "route": "index",
+       "matchFilters": {
+         "search": true,
+         "tag": true
+       },
+       "categoryAriaLabel": "Kategori: {{category}}", // Localized text variable
+       "activeCategoryAriaLabel": "Vald Kategori: {{category}}" // Localized text variable
+     }
+   },
-   "guide-category-dropdown": {
-     "type": "guide-category-dropdown",
-     "properties": {
-       "matchFilters": {
-         "search": true,
-         "tag": true
-       },
-       "rootCategoryHeader": "Alla kategorier",
-       "categoryAriaLabel": "Kategori: {{category}}",
-       "activeCategoryAriaLabel": "Vald Kategori: {{category}}"
-     }
-   },
  }
}
```

### Replace component references

```diff
{
  "components": {
    "index-area": {
      "children": [
        [...]
-       "guide-category-dropdown",
+       "guide-category-list",
      ]
    },
    "browse-area": {
      "children": [
        [...]
-       "guide-category-dropdown",
+       "guide-category-list",
      ]
    },
    "search-area": {
      "children": [
        [...]
-       [
-           "guide-category-dropdown",
-           {
-             "properties": {
-               "showMatchCount": true,
-               "route": "search"
-             }
-           }
-       ],
+       "guide-category-list",
      ]
    }
  }
}
```

## Step 2 (OPTIONAL): Restructure views

By default the floating template has three different views for browsing (`index`, `search` and `browse`). This comes with the effect or sliding transitions between view shifts, which is something that might not always be desirable.

### Remove the definitions for `search-area` and `browse-area`

```diff
{
  "components": {
-   "browse-area": {
-     // remove entire object including props and children
-   },
-   "search-area": {
-     // remove entire object including props and children
-   }
  }
}
```

### Update route props

```diff
{
  "components": {
    "widget-header": {
      "properties": {
        [...]
+       "route": "index" //enables click on header to go to index page
      }
    },
    "search": {
      "properties": {
        [...]
+       "route": "index"
      }
    },
    "guide-list": {
      "properties": {
+       "routes": {
+         "page": "index"
+       }
      }
    },
    "tag-list": {
      "properties": {
        [...]
+       "route": "index"
      }
    },
    "related-tag-list": {
      "properties": {
        [...]
+       "route": "index"
      }
    }
  }
}
```

### Remove `guide-category-browser` component as it is no longer in use

```diff
  "components": {
-   "guide-category-browser": {
-     // remove entire object including props and children
-   }
  }
```

### Update the `views` object

```diff
{
  "views": {
    "index": {
-     "path": "/",
+     "path": [
+       "/",
+       "/c:guideCategory(\\d+)-:uriName"
+     ]
      "entry": "index-area"
    },
-    "browse": {
-      "path": [
-        "/browse",
-        "/browse/c:guideCategory(\\d+)-:uriName"
-     ],
-      "entry": "browse-area"
-   },
-   "search": {
-     "path": "/search",
-     "entry": "search-area"
-    },
    //remaining routes unchanged
  }
}
```
