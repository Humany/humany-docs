# Widget life cycle

A widget consists of a `$widget` object, normally referred to as "the widget", and the `$instance` object which is the instantiated widget type controlling the actual style and behaviour of the visual widget interface. The `$widget` object can be in any of the following states.

### `deactivated`
The **deactivated** state is the default state when a widget is created. At this state no configuration commands have been applied, including plugins, and it does not yet have its `$instance` object created.
```javascript
widget.state; // 'deactivated'
widget.container.get('$instance'); // undefined
widget.container.get('$plugins'); // undefined
widget.invoke('[command]'); // invalid operation - command is ignored
```
From **deactivated** state the widget can transition to **activating** state.

### `activating`
When a widget is activated by a call to `activate()` it enters the **activating** state. At this phase configuration commands are applied and the `$instance` object is created, along with any applicable plugins. The `$instance.initialize()` hook will execute as the final step of this phase.

From **activating** state the widget will transition to **activated** state.

### `activated`
When a widget enters the **activated** state the `$instance.activate()` hook will execute. The `$instance` is now ready to receive commands. 
```javascript
widget.state; // 'activated'
widget.container.get('$instance'); // instanceof $type
widget.container.get('$plugins'); // array of plugins
widget.invoke('[command]'); // command is delegated to the $instance object
```
This state will persist until the client navigates away from the page or a call to `deactivate()` is made:
```javascript
widget.deactivate(); // widget will transition to 'deactivating' state
```

### `deactivating`
When a widget is deactivated it will transition to the **deactivating** state. The `deactivate()` hook will execute on the `$instance` object as well as on any registered plugin. At the end of this phase the widget's `Container` and `EventManager` are cleared before the widget is restored to its initial **deactivated** state.

## Destroying a widget
In a regular setup there is no need to destroy a widget. Widgets are created as part of the implementation and their `$widget` objects should remain available on the implementation, either activated or deactivated. 

However, in custom standalone setups where widgets are created dynamically at runtime, it may be desirably to completely destroy a widget and remove it from its implementation. For this purpose there is a `destroy()` helper you can use. It will deactivate the widget and remove any relations to its implementation.

```javascript
import { destroy } from '@humany/widget-core';

// ...

const widget = implementation.widgets.get('my-widget'); // $widget object

await destroy(widget);

implementation.widgets.get('my-widget'); // undefined
```