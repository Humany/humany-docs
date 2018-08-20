# Activating a widget
Widgets can be activated with trigger links or manually by using the Widget API.

## Trigger links
After you have installed Humany on your site, the bootstrapper will automatically scan the document for "trigger links" and activate their corresponding widgets. This is the easiest way to activate a widget as it doesn't require any techincal knowledge.

Below is the format of a trigger link. Refer to the Humany portal for a unique trigger link for each widget.

```
<a href="//[application].humany.net/[widget-name]>
```

### Lazy-loaded trigger links
In case you lazy-load trigger links the bootstrapper may not be able to detect them. This may be an issue if the markup is modified by external scripts after the DOM content has loaded. In this case you will need to instruct the bootstrapper to re-scan the document in order to find and activate trigger links.

```javascript
// scan entire document
humany.scan();

// make a partial scan
humany.scan(document.getElementById('some-container'));
```
The `scan()` function returns a `Promise` containing an array of newly activated widgets.

## Widget API
Sometimes the "trigger link" approach is not enough and you need more detailed control over the activation, e.g. when inside a SPA or a WebView inside a mobile app. This is how you activate the widget using the API.

### Find widget by name
You can access a widget from the global `humany` object or from the implementation object. Either way, first ensure the runtime is fully loaded [as decribed here](accessing-the-api.md), then execute one of the following lines:
```javascript
// implementation object (recommended)
const widget = implementation.widgets.get('widget-name');

// global object
const widget = humany.widgets.find('widget-name');
```

### Activate widget
Without a "trigger link" a widget must be activated manually. Just call `activate()` on the widget object.
```javascript
widget.activate().then(() => {
  // widget is activated
});
```

### Invoke commands
Once the widget is activated you can invoke commands on it. Available commands are unique for each widget type. Refer to each widget's API documentation for more information.

```javascript
widget.invoke('command', args...);
```

### Destroy
In a SPA environment you may also need to destroy the widget manually, e.g. during page transitions:
```javascript
widget.deactivate();
```