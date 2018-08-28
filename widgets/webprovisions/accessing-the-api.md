# Accessing the API
To enable the Widget API you need to activate version 4 on your implementation. Right-click on your implementation and select "Edit". Expand the "Versions" section and select "4 (beta)".

## In code
Install Humany by embedding the installation code from the Humany portal. This will make a global `humany` object available. However, the full API will be loaded asynchronously, and if you access the `humany` object immediately after the installation code there is no guarantee the implementation has fully loaded. To ensure the implementation has loaded, execute the following code:
```javascript
humany.configure((config) => 
  config.ready((implementation) => {
    console.log(`implementation '${implementation.name}' is now ready`, implementation);
  });
);
```

**Next step:** [Activating a widget](activate-widget.md)