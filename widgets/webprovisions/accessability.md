# Accessibility
All Humany widgets from V4 are WCAG combatible. To configure the accessibility settings of your widgets, use the following configuration commands.

### Bound Focus
This option makes the widget "bound". When tabbing through the widget's elements and reaching the end, the next element tabbed to will be the first element in the widget.
This means that the focus will not leave the widget when using the tab key.

```javascript
config.accessibility({
  boundFocus: true, // defaults to false
});
```

### Highlight Focus
This option makes it easier to determine which element has focus, by giving it a dotted outline.

```javascript
config.accessibility({
  highlightFocus: true, // defaults to false
});
```

## Standalone setup
In order to use the accessibility configuration API in a standalone setup, you need to add it to your configuration API extensions as described below:

```javascript
import { accessibilityConfigurationApi } from '@humany/utils';

const humany = window.humany = Humany.createFromGlobal(
  window.humany, 
  { 
    configurationApiExtensions: [
      accessibilityConfigurationApi,
    ],
  }
);
```
