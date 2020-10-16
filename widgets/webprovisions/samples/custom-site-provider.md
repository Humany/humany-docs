# Custom Site Provider
The `site` parameter is passed on all requests made from widgets to the ACE Knowledge backend. The value is used to build contextual match results as well as providing the value for visibility criterias. 

By default, the `site` parameter value is constructed from the current `window.location` and only vary on `host` and `pathnamn`, which means `protocol`, `search` and `hash` is excluded. To change the default behaviour, register a custom site provider as shown below.

```js
humany.configure((config) => {
  config.container.registerAsync('siteProvider', () => {
    return () => {
      // return custom site parameter value here
    }
  });
});
```
