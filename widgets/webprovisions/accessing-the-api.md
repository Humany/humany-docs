# Accessing the API
To enable the API you need to activate Webprovisions for your implementation. Right-click on your implementation and select "Edit". Expand the "Platform" section and select "Webprovisions".

## In code
Install Humany by embedding the installation code from the Humany portal. This will make a global `humany` object available. However, the full API will be loaded asynchronously, and if you access the `humany` object immediately after the installation code there is no guarantee the runtime is fully loaded.

The following code will ensure the runtime is fully loaded for the `'default'` implementation. Change the implementation name depending on your setup.
```javascript
humany.configure('default', (config) => 
  config.ready((implementation) => {
    console.log('implementation is now ready', implementation);
  });
);
```

**Next step:** [Activating a widget](activate-widget.md)