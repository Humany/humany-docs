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

- **Guide list** - `humany-guide-list`

    Contains the guide list, uses `humany-item-list`, and a loader which is shown when fetching guides.

    ![](inline-guide-list.png)
- **Category list** - `humany-category-list-wrapper`

    Contains the full category tree, uses `humany-item-list`, and a loader which is shown when fetching categories. Is rendered and behave differently depending on the chosen theme.

    - **Standard theme**
    
      Displayed statically on the right hand side.

      ![](inline-category-list-standard.png)

      
    - **Iconic theme**
    
      Displayed above the guide list when no category is chosen then moves to the right of the guide list once a category is chosen.

      **No category chosen:**
      ![](inline-category-list-iconic.png)
      
      **Category chosen:**
      ![](inline-category-list-iconic-category-chosen.png)


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