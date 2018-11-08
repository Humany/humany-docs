# Activate widget using a V3 adapter
This sample shows how to activate a V4 widget using a V3 custom adapter.

## Prerequisites
A html page containing the Humany installation script for:
- one V3 implementation containing the source widget
- one V4 implementation containing the target widget

### 1. Define a V3 custom adapter
Follow the [tutorial on how to create a custom adapter](https://github.com/Humany/humany-docs/blob/master/widgets/adapters/custom-adapter.md) and add it  to your source widget inside the Humany portal. In this tutorial we assume you have created a custom adapter named **'Questions about shipping'** with the client name **'shipping-faq-widget'**. When we are done we will be able to pop-up the target widget by clicking the defined contact method inside the source widget.

### 2. Create the javascript adapter
When the contact method is added to the source widget we need to map it to a javascript handler in code. The following code registers a javascript adapter on the source implementation.

```js
Humany.configure((config) => {
  config.registerAdapter({
    map: 'shipping-faq-widget',
    execute: () => {
      // this code is executed when the user clicks
      // the 'Questions about shipping' contact method
    },
  });
});
```
**Note:** Up to V3 of the widget framework, only one implementation can exist on the same page. From V4 this limitation is removed, making it possible to have multiple implementations side-by-side. The above code uses a `Humany.configure()` block (with capital **H**). This is used to configure the current V3 implementation. To configure V4 implementations, [see the V4 documentation](https://github.com/Humany/humany-docs/tree/master/widgets/webprovisions).

### 3. Activate and start the target widget
When the user clicks the 'Questions about shipping' contact method, the `execute()` function of your adapter handler will be called. Implement the code below to activate and start the target widget.

```js
execute: () => {
  const targetWidget = window.humany.widgets.find('name-of-target-widget');
  targetWidget.activate().then(() => {
    // target widget has been activated.
    // start it by invoking the 'start' command.
    return targetWidget.invoke('start');
  }).then(() => {
    // the target widget has been started and rendered.
  });
}
```
**Note:** The above code uses the V4 widget API (`window.humany` with lower-case **H**) to get a reference to the target widget. For more information about the V4 widget API, [see the V4 documentation](https://github.com/Humany/humany-docs/tree/master/widgets/webprovisions).

## Routing
When invoking the `start` command the widget will be started in its default location, which in most cases is the **index** route. In order to navigate to a specific route you can use the _RoutingService_, registered as `router` on the widget's container:
```js
execute: () => {
  const targetWidget = window.humany.widgets.find('name-of-target-widget');
  targetWidget.activate().then(() => {
    return targetWidget.invoke('start');
  }).then(() => {
    return targetWidget.container.getAsync('router');
  }).then((router) => {
    router.navigate('contact');
  });
}
```
**Note:** The _RoutingService_ is only available in view-based widgets and is not available in conversational widgets such as Bot.
