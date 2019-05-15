# CSS in Humany Widgets
*This documentation is intended for widgets in v4 implementations.*

## Commonly used classes
All of our classes are prefixed with `'humany-'` to make it easier to scope our CSS.

Class | Description
------|------------
`humany-link`|Base-class used for every link. Not used for links in guide content.
`humany-paragraph`|Container for a `h2` title and a `div` containing any passed html. e.g. used for rendering guides.
`humany-list`|Base-class used for every list. Not used for lists in guide content.
`humany-item-list`|Contains a `humany-paragraph` and a `humany-list`.
`humany-html`|Contains any content of html, e.g. guide bodies.


## Widget types

## Inline
### Main layout

- **Header** - `humany-header`

    Contains the navigation links to each of the widget tabs, top row notices, search field and middle row notices.

    ![](inline-header.png)
  
- **Content** - `humany-content`

    Contains the breadcrumb, categories, guide list, list notices, free text notices, tags and foot notices.

    ![](inline-content.png)

- **Footer** - `humany-footer`

    Contains the copyright.

    ![](inline-footer.png)

### Components

- **Tabs** - `humany-tabs`

    A row with links to each tab.

    ![](inline-tabs.png)

- **Top and middle row notices** - `humany-top-notice, humany-middle-notice`
    
    Displays a single closeable notice at a time with paging.

    - **Top:**
    ![](inline-top-row-notices.png)

    - **Middle:**
    ![](inline-middle-row-notices.png)

- **Search** - `humany-search`
    
    A `div` with a search `input`. 
    
    *Looks differently depending on the chosen theme.*

    - **Standard theme:**
    ![](inline-search-standard.png)

    - **Iconic theme:**
    ![](inline-search-iconic.png)

- **Breadcrumb** - `humany-breadcrumb-list`

    When some kind of navigation is present, when searching, when selecting a category etc. A breadcrumb is shown with each navigation step.
    
    *Currently only available for the iconic theme*

    ![](inline-breadcrumb.png)

- **Category list** - `humany-category-list-wrapper`

    Contains the full category tree, uses `humany-item-list`, and a loader which is shown when fetching categories. 
    
    *Looks and behaves differently depending on the chosen theme.*

    - **Standard theme**
    
      Displayed statically on the right hand side.

      ![](inline-category-list-standard.png)

      
    - **Iconic theme**
    
      Displayed above the guide list when no category is chosen then moves to the right of the guide list once a category is chosen.

      **No category chosen:**
      ![](inline-category-list-iconic.png)

      **Category chosen:**
      ![](inline-category-list-iconic-category-chosen.png)

- **Guide list** - `humany-guide-list`

    Contains the guide list, uses `humany-item-list`, and a loader which is shown when fetching guides.

    ![](inline-guide-list.png)

- **List and free text notices** - `humany-categorized-notice-list`

    Contains both list and free text notices separated by category.

    - **List notice:**
    ![](inline-list-notice.png)

    - **Expanded list notice:**
    ![](inline-list-notice-expanded.png)
    
    - **Free text notice:**
    ![](inline-free-text-notice.png)

- **Foot notices** - `humany-bottom-notice-list`

    Contains a list of all the foot notices.

    ![](inline-foot-notices.png)

- **Guide** - `humany-guide`

    An opened guide. Can contain contact method, dialog and feedback lists.

    ![](inline-guide.png)

    - **Feedback list** - `humany-feedback-list`
    ![](inline-feedback-list.png)

    - **Dialog list** - `humany-dialog-list`
    ![](inline-dialog-list.png)

- **Contact method selector** - `humany-contact-selector`

    Levels of contact method categories. If selected category has sub categories, those categories will be displayed in another level.
    If not the contact methods within the selected category will be display in a contact method list.

    *Looks differently depending on the chosen theme.*

    - **Standard theme**

        **First level, no category chosen**
        ![](inline-contact-selector-standard.png)

        **Second level, category chosen, contact methods displayed**
        ![](inline-contact-selector-second-level-standard.png)
        ![](inline-contact-selector-contact-methods-standard.png)


    - **Iconic theme**

        **First level, no category chosen**
        ![](inline-contact-selector-iconic.png)

        **Second level, category chosen, contact methods displayed**
        ![](inline-contact-selector-second-level-iconic.png)
        ![](inline-contact-selector-contact-methods-iconic.png)

- **Contact method list** - `humany-contact-list`

    Simple list of contact methods.

    ![](inline-contact-list.png)


## Floating
### Main layout
- **Header** - `humany-header`

    Contains the avatar, heading, tagline, back button, search toggle button and close button in mobile view.

    ![](floating-header.png)

- **Content** - `humany-content`

    Contains the top and middle row notices grouped together, categories, search field, guide list, guides, contact methods, list notices, free text notices and foot notices.

    ![](floating-content.png)

- **Footer** - `humany-footer`

    Positioned absolutely at the bottom on top of the main content, contains the copyright and the button to navigate to the contact view.

    ![](floating-footer.png)

### Components

## Bot
### Main layout
- **Header** - `humany-header`

    Contains the avatar, heading, tagline and close button in mobile view.
  
    ![](bot-header.png)

- **Content** - `humany-content`

    Contains the conversation with bot and user messages and the message box with a help button.
  
    ![](bot-content.png)
    
### Components





# **TO-DO:**
- Components for all widget types
- Document usage of data-attributes
- Interactive classes `humany-phrase-present`, `humany-category-{{current route}}` etc..

