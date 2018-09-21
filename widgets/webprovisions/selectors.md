# Selectors
Selectors can be used to search specific widgets or implementations in a Humany runtime, as well as to specify unique widgets and implementations to apply configuration commands to. A selector can be a `string` or a `Descriptor` object.

### Widgets
For widgets the primary entity is the widget key, and in basic setups this is sufficient for selecting a unique widget, as shown below.
```javascript
// string selector
const widget = humany.widgets.find('the-widget');
// object selector
const widget = humany.widgets.find({ widget: 'the-widget' });
```
It's important to note that widget keys are not guarenteed to be unique in a multi-implementation setup. For this reason it's good practice to make the selector more specific by also specifying the implementation key and even tenant, as illustrated in examples below.

**Limit on implementation and widget (_not_ guarenteed unique):**
```javascript
// string selector
const widget = humany.widgets.find('my-implementation:the-widget');

// object selector
const widget = humany.widgets.find({
  implementation: 'my-implementation',
  widget: 'the-widget',
});
```
**Limit on tenant, implementation key and widget key (guarenteed unique):**
```javascript
// string selector
const widget = humany.widgets.find('tenant:my-implementation:the-widget');

// object selector
const widget = humany.widgets.find({
  tenant: 'tenant',
  implementation: 'my-implementation',
  widget: 'the-widget',
});
```
### Implementations
For implementations the primary entity is the implementation key. An implementation selector is constructed the same way as for widgets, except for leaving out the widget key part.

**Limit on implementation key only (_not_ guarenteed unique):**
```javascript
// string selector
const implementation = humany.implementations.find('my-implementation');

// object selector
const implementation = humany.implementations.find({ implementation: 'my-implementation' });
```

**Limit on tenant and implementation key (guarenteed unique):**
```javascript
// string selector
const implementation = humany.implementations.find('tenant:my-implementation');

// object selector
const implementation = humany.implementations.find({
  tenant: 'tenant',
  implementation: 'my-implementation',
});
```
An implementation selector can be used to limit `configure` handlers in a multi-implementation setup.
```javascript
humany.configure('my-implementation', (config) => {
  // this config section will be applied to 'my-implementation' only
});

humany.configure('tenant:*', (config) => {
  // this config section will be applied to all implementations on a specific tenant
});

// ...or:
humany.configure({ tenant: 'tenant' }, (config) => {
  // this config section will be applied to all implementations on a specific tenant
});
```
