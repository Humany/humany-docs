# Plugin authoring

## Stateless plugin
A stateless plugin is a plain javascript function passed to the `plugin()` configuration command when configurating the Humany runtime:

```javascript
const statelessPlugin = (container, settings) => {
  // executed when widget is initialized
};

humany.configure((config) => {
  config.plugin(statelessPlugin);
});
```
Stateless plugins are executed when the widget is initialized but have no additional life-cycle hooks associated to the widget. The current widget's `Container` instance along with the plugin settings are passed as an object argument to the function.

The `Container` gives you access to all registered services on the widget, providing many ways to extend and override default functionality. The following example subscribes to the `'router:change'` event on the widget, which is triggered by the `Router` service when a navigation is performed.

```js
const navigationReportingPlugin = (container, settings) => {
  const { events } = container.get('$widget');
  events.subscribe('router:change', (event, data) => {
    const { previous, next } = data;
    trackRouterChange(previous, next);
  });
};
```

Altough the above code attaches an event handler to the `events.subscribe()` function it is safe from a memory-leak perspective. Managed event handlers are cleared when the widget is deactivated. When using external events, however, you will need to explicitly remove any event handlers when the widget is deactivated. Use stateful plugins for that, as described below.

## Stateful plugins
A stateful plugin is a constructable javascript class passed to the `plugin()` configuration command. It has the same life-cycle hooks as a widget. Optionally it can extend from the `Plugin` class, which gives convenient access to the `Widget` and `EventManager` objects.

In the following example we define a plugin that attaches a click event handler on a DOM element and reacts to it by commanding the widget to start.

```javascript
import { Plugin } from '@humany/widget-core';

class StatefulPlugin extends Plugin {

  elements = [];

  initialize() {
    // executed when widget instance is initialized
    const { selector, eventType } = this.settings;
    this.elements = document.querySelectorAll(selector);
    this.elements.forEach((element) => {
      element.addEventListener(eventType, this.onElementClick);
    });
  }

  onElementClick(event) {
    event.preventDefault();
    this.widget.invoke('start');
  }

  deactivate() {
    // executed just before the widget instance is deactivated
    const { eventType } = this.settings;
    this.elements.forEach((element) => {
      element.removeEventListener(eventType, this.onElementClick)
    });
  }
}

humany.configure((config) => {
  config.plugin(StatefulPlugin);
});
```

