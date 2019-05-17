---
path: '/widgets/styling-v2/inline/big-category-tree'
date: '2017-11-07'
title: 'Big category tree'
---

# Keep size of categories in index view on inline and lightbox widgets using iconic theme

```css
/* Always keep category container width */
#humany_widget-name.humany-widget .humany-view-index .humany-secondary {
    width: 100%;
}

/* Never show 'All categories'-category */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree .humany-category-0 {
    display: none;
}

/* Always center categories and position the list relatively to act as anchor for sub category lists */
#humany_widget-name.humany-widget .humany-category-tree ul {
    text-align: center;
    position: relative;
}

/* Always keep category size, positioning, etc */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li {
    display: inline-block;
    position: static;
    width: 145px;
    vertical-align: top;
}

/* Always keep category text size, positioning, etc */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li a {
    font-weight: normal;
    text-transform: none;
    font-size: 14px;
    line-height: 20px;
    display: block;
    text-align: center;
    padding: 7.5px 0;
    margin: 0;
    border: none;
}

/* Push below content down to make space for absolutely positioned children
  Note: This might need changing depending on how many levels of sub categories is used 
*/
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li.humany-expanded {
    margin-bottom: 145px;
}

/* Always color category background when selected or expanded */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li.humany-selected>a,
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li.humany-expanded>a {
    background-color: #3A3E41;
}

/* Always color category text when selected or expanded */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li.humany-selected>a,
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li.humany-expanded>a,
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li.humany-selected>a>i,
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li.humany-expanded>a>i {
    color: #FFFFFF;
}

/* Always keep icon size and positioning */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li a i {
    margin: 0 auto 15px;
    text-align: center;
    display: block;
    float: none;
    line-height: 32px;
}

/* Always keep fa icon size */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li a i.fa {
    font-size: 40px;
}

/* Always keep custom icon size */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li a i.humany-custom-icon {
    width: 3em;
    height: 3em;
}

/* Hide category guide count */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li a span {
    display: none;
}

/* Position sub categories absolutely relatively to their parent category */
#humany_widget-name.humany-widget .humany-view-index .humany-category-tree ul li ul {
    position: absolute;
    width: 100%;
    left: 0;
    top: 100px;
}

/* Always hide notices in humany-secondary */
#humany_widget-name.humany-widget .humany-view-index .humany-secondary .humany-notice-column {
    display: none;
}

/* Always show and set width humany-tertiary */
#humany_widget-name.humany-widget .humany-view-index .humany-tertiary {
    display: block;
    float: right;
    width: 40%;
}

/* Static width on humany-primary */
#humany_widget-name.humany-widget .humany-view-index .humany-primary {
    width: 55%;
}
```
