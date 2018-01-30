# Always show search bar 
```css
/* Hide toggle button for search bar  */
#humany_widget-name.humany-widget .humany-head-btns .humany-toggle-search {
    display: none;
}

/* Show search by default */
#humany_widget-name.humany-widget .humany-search-placeholder,
#humany_widget-name.humany-widget .humany-search {
    position: relative;
    padding: 0;
    left: 0;
    top: 0;
}

/* Move search icon */
#humany_widget-name.humany-widget .humany-search .humany-icon-svg {
    left: 15px;
}

/* Move button-wrapper (clear-button) to far right of input */
#humany_widget-name.humany-widget .button-wrapper {
    right: 0;
}

/* Remove default border on search input */
#humany_widget-name.humany-widget .humany-search input {
    border: none;
}

/* Don't move search when phrase present */
#humany_widget-name.humany-widget .humany-secondary.humany-show-search {
    transform: none !important;
    height: auto;
}
```
