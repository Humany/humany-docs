# CSS Migration from 4.0 to 4.1
This document describes the changes of custom styling that is required to migrate a default styled v4 implementation to v4.1.

## Rule 1
```
.humany-trigger button
```

### Type:
Modification

### Details:
- Change `border` to `3px dashed transparent`.
- Change `padding` to `8px`.
- Remove `line-height`.

## Rule 2:
```
.humany-trigger.humany-tabbing button:focus
```

### Type:
Addition

### Details:
```css
border-color: #990AE3;
background-color: #FFFFFF !important;
```

## Rule 3:
```css
.humany-trigger.humany-tabbing button:focus i
```

### Type:
Addition

### Details:
```css
color: #990AE3;
```

## Rule 4:
```css
.humany-trigger.humany-tabbing button:focus .humany-close,
.humany-trigger.humany-tabbing button:focus .humany-close path
```

### Type:
Addition

### Details:
```css
fill: #990AE3;
```

## Rule 5:
```css
.humany-trigger .humany-close
```

### Type:
Modification

### Details:
- Change `left` to `13px`.
- Change `top` to `6px`.

## Rule 6:
```css
.humany-trigger .humany-loader,
.humany-trigger .humany-loader:after
```

### Type:
Modification

### Details:
- Change `top` to `10px`.
- Change `left` to `9px`.

## Rule 7:
```css
.humany-trigger:not(.humany-has-text) span
```

### Type
Addition

### Condition
Positioned after:
```css
.humany-trigger span
```

### Details
```css
display: none;
```