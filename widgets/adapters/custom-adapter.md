# Custom adapter
The following sample shows how to create and register a custom adapter on widgets. Custom adapters allows you to execute your own javascript code in response to posting a from in a Contact Method.

### Prerequisites
The implementation must be at version 2 or higher. The implementation can be upgraded from the Interfaces section and the UPGRADE button in the toolbar area. If no button is visible it means you are already using the latest version.

## Overview
An adapter is a javascript object that is mapped to a specific type of Contact Method. It can provide custom behaviour to a Contact Method inside a widget, e.g. posting a form to an external service.

## 1. Create a Contact Method
Login to Humany admin and create a Contact Method of type Adapter.

![](images/create-contact-method.png)

Specify a `Client name` under Adapter settings, e.g. "my-adapter". Then click Save.

![](images/adapter-settings.png)

**IMPORTANT:** Make sure to make the Contact Method added to your widget. For more information, read the FAQ inside Humany admin.

## Create the adapter
Create a plain javascript object with the property `map` set to the client name you specified inside the Contact Method and an `execute()` function, as shown below. The `execute()` function will be invoked when the associated Contact Method is executed inside the widget. 
```javascript
var MyAdapter = {
  map: 'my-adapter',
  execute: function(data, context) {
    console.log('The adapter is executed with the following data:', data);
    return { success: true };
  }
};
```

### execute(data, context, next): ExecuteResult
`data` contains data for the current action. Here you can access information about the Contact Method and any posted form data. Use can use this to pass form data to an external service.

`context` contains references to the current `WidgetData` and its `container`.

`next` is a function which references the parent adapter, if available. This is invoked to chain multiple adapters and delegate to default functionality.

#### ExecuteResult (object or Promise)
An object describing the outcome of the action.

`success` (boolean) indicating whether the action has succeeded.

`keepForm` (boolean) indicating whether the original form should be kept visible.

`confirmationText` (string) custom confirmation text. If not set the default confirmation text will be used.

`suppressConfirmation` (boolean) indicating whether the confirmation text should be supressed.


## Register the adapter
To make the adapter available it must be registered through the configuration API. Execute the following code _after_ the Humany embed script:
```javascript
Humany.configure(function(config) {
  // Register the adapter on ALL widgets in the implementation:
  config.registerAdapter(MyAdapter);

  // Register the adapter on a single widget in the implementation:
  // config('my-widget').registerAdapter(MyAdapter);
})
```