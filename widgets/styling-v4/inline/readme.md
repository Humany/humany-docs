
# Inline
## Main layout

- **Header** - `humany-header`

    Contains the navigation links to each of the widget tabs, top row notices, search field and middle row notices.

    ![](images/inline-header.png)
  
- **Content** - `humany-content`

    Contains the breadcrumb, categories, guide list, list notices, free text notices, tags and foot notices.

    ![](images/inline-content.png)

- **Footer** - `humany-footer`

    Contains the copyright.

    ![](images/inline-footer.png)

## Components

- **Tabs** - `humany-tabs`

    A row with links to each tab.

    ![](images/inline-tabs.png)

- **Top and middle row notices** - `humany-top-notice, humany-middle-notice`
    
    Displays a single closeable notice at a time with paging.

    - **Top:**

        ![](images/inline-top-row-notices.png)

    - **Middle:**

        ![](images/inline-middle-row-notices.png)

- **Search** - `humany-search`
    
    A wrapper for the search field.
    
    *Looks differently depending on the chosen theme.*

    - **Standard theme:**

        ![](images/inline-search-standard.png)

    - **Iconic theme:**

        ![](images/inline-search-iconic.png)

- **Breadcrumb** - `humany-breadcrumb-list`

    When some kind of navigation is present, when searching, when selecting a category etc. A breadcrumb is shown with each navigation step.
    
    *Currently only available for the iconic theme*

    ![](images/inline-breadcrumb.png)

- **Category list** - `humany-category-list-wrapper`

    Contains the full category tree, uses `humany-item-list`, and a loader which is shown when fetching categories. 
    
    *Looks and behaves differently depending on the chosen theme.*

    - **Standard theme**
    
      Displayed statically on the right hand side.

      ![](images/inline-category-list-standard.png)

      
    - **Iconic theme**
    
      Displayed above the guide list when no category is chosen then moves to the right of the guide list once a category is chosen.

      - **No category chosen:**

         ![](images/inline-category-list-iconic.png)

      - **Category chosen:**
      
        ![](images/inline-category-list-iconic-category-chosen.png)

- **Guide list** - `humany-guide-list`

    Contains the guide list, uses `humany-item-list`, and a loader which is shown when fetching guides.

    ![](images/inline-guide-list.png)

- **List and free text notices** - `humany-categorized-notice-list`

    Contains both list and free text notices separated by category.

    ![](images/inline-categorized-notice-list.png)

    - **List notice:** - `humany-list-notice`

        ![](images/inline-list-notice.png)

    - **Expanded list notice:** - `humany-list-notice, humany-expanded`

        ![](images/inline-list-notice-expanded.png)
    
    - **Free text notice:** - `humany-free-text-notice`

        ![](images/inline-free-text-notice.png)

- **Foot notices** - `humany-bottom-notice-list`

    Contains a list of all the foot notices.

    ![](images/inline-foot-notices.png)

- **Guide** - `humany-guide`

    An opened guide. Can contain contact method, dialog and feedback lists.

    ![](images/inline-guide.png)

    - **Feedback list** - `humany-feedback-list`
    ![](images/inline-feedback-list.png)

    - **Dialog list** - `humany-dialog-list`
    ![](images/inline-dialog-list.png)

- **Contact method selector** - `humany-contact-selector`

    Levels of contact method categories. If selected category has sub categories, those categories will be displayed in another level.
    If not the contact methods within the selected category will be display in a contact method list.

    *Looks differently depending on the chosen theme.*

    - **Standard theme**

        - **First level, no category chosen**

            ![](images/inline-contact-selector-standard.png)

        - **Second level, category chosen, contact methods displayed**

            ![](images/inline-contact-selector-second-level-standard.png)
            ![](images/inline-contact-selector-contact-methods-standard.png)


    - **Iconic theme**

        - **First level, no category chosen**

            ![](images/inline-contact-selector-iconic.png)

        - **Second level, category chosen, contact methods displayed**

            ![](images/inline-contact-selector-second-level-iconic.png)
            ![](images/inline-contact-selector-contact-methods-iconic.png)

- **Contact method list** - `humany-contact-list`

    Simple list of contact methods.

    ![](images/inline-contact-list.png)