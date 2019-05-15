# Accessing the API
To enable the Widget API you need to activate version 4 on your implementation. Right-click on your implementation and select "Edit". Expand the "Versions" section and select "4 (latest)".

## In code
Install Humany by embedding the installation code from the Humany portal. This will make a global `humany` object available. However, the implementation is loaded asynchronously and if you access the `humany` object immediately after the installation code there is no guarantee the implementation has initialized.

Use the `ready()` command to specify a handler for when the implementation is initialized.

```javascript
humany.configure((config) => 
  config.ready((implementation) => {
    console.log(`implementation '${implementation.name}' is now ready`, implementation);
  });
);
```

### Multiple implementations
The `ready()` handler will execute once for every installed implementation. In a multi-implementation setup you can limit the `configurator` by passing a selector object as shown below.

```javascript
humany.configure((config) => 
  config({ implementation: 'default' }).ready((implementation) => {
    console.log(`implementation 'default' is now ready`));
  });
);
```

**Next step:** [Activating a widget](activate-widget.md)
