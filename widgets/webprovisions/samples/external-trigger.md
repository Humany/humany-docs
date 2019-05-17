---
path: '/widgets/webprovisions/samples/external-trigger'
date: '2017-11-07'
title: 'External trigger'
---

# External trigger
This sample demonstrates how to activate a widget based on external events. The following code will activate the `'dummy'` widget when the user clicks the `'trigger'` element. 
```javascript
const triggerElement = document.getElementById('trigger');
triggerElement.addEventListener('click', (event) => {
  event.preventDefault();
  humany.widgets.find('dummy').activate(/*[args...]*/);
});
```

### Activation behaviour
What happens when you call `activate()` depends on the widget type. _Lightbox_ doesn't need any further instructions, while _Inline_ and _List_ require a `widgetDOMElement` to be passed as an argument. The `widgetDOMElement` will act as the container for the widget:

```javascript
// render 'my-inline' inside the 'container' element
humany.widgets.find('my-inline').activate({
  widgetDOMElement: document.getElementById('container')
});
```

_Floating_ and _Bot_, on the other hand, will by default render a "trigger badge" that the user must click before the "main" view is rendered. This is not very user-friendly in the above scenario, where you already have provided your own "trigger badge" for the user to click. In such a case you can set `renderTriggerElement` to `false` when activating the widget, then manually invoke the `start` command as below:

```javascript
const widget = humany.widgets.find('my-floating');
widget.activate({ renderTriggerElement: false });
widget.invoke('start');
```

Refer to the documentation of each widget type for more information about available arguments and commands.