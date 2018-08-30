# Custom container element
The default behaviour for widget types _Floating_ and _Bot_ is to render a "floating badge" that the user must click to activate the main view of the widget. In some cases, however, you may want to render the widget inline (as in the behaviour of the _Inline_ and _List_ widget types).

To accomplish this you need to replace the default bootstrapper with custom activation logic. By default the bootstrapper will scan the document for "trigger elements" and activate each widget according to its normal behaviour, which for _Floating_ and _Bot_ is to render a "floating badge" as described above.

### 1. Do not use the "trigger element"
To prevent the bootstrapper from activating the widget you should _not_ add the "trigger element" to the page, as you would normally do.

### 2. Activate using the Widget API
The next step is to activate the widget programmatically using the Widget API. Implement the following code into your page and replace the variables according to your setup:

```javascript
// make sure the Humany installation script has executed before running this code

const implementationName = 'default';
const widgetName = 'my-floating';
const containerElementId = 'widget-container';

humany.configure((config) => 
  config.ready((implementation) => {
    if(implementation.name === implementationName) {
      const myFloating = implementation.widgets.get(widgetName);
      myFloating.activate({
        widgetDOMElement: document.getElementById(containerElementId),
        renderTriggerElement: false,
      });
      myFloating.invoke('start');
    }
  });
);
```
_Note: Code above uses ES6 syntax, which not all browser versions support. Transpile to ES5 for legacy support._