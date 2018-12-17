# Accessability
All Humany widgets using Webprovisions can be configured to improve the accessability.
To configure the accessability settings of your widgets, use the accessability configuration API.

## In Widget Configuration
Currently there are two options that can be configured. In order to use the accessability configuration API, you need to add it to your configuration API extensions as described below:

```javascript
import { accessabilityConfigurationApi } from '@humany/utils';

const humany = window.humany = Humany.createFromGlobal(
  window.humany, 
  { 
    configurationApiExtensions: [
      accessabilityConfigurationApi,
    ],
  }
);
```

### Bound Focus
This option makes the widget "bound". When tabbing through the widget's elements and reaching the end, the next element tabbed to will be the first element in the widget.
This means that the focus will not leave the widget when using the tab key.

```javascript
config.accessability({
  boundFocus: true, // defaults to false
});
```

### Highlight Focus
This option makes it easier to determine which element has focus, by giving it a glow / yellow background.

```javascript
config.accessability({
  highlightFocus: true, // defaults to false
});
```
