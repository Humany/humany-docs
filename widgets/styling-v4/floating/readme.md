# Floating

## Main layout
- **Header** - `humany-header`

    Contains the avatar, heading, tagline, back button, search toggle button and close button in mobile view.

    ![](images/floating-header.png)

- **Content** - `humany-content`

    Contains the top notices, categories, search field, guide list, guides, contact methods, list notices, free text notices and foot notices.

    ![](images/floating-content.png)

- **Footer** - `humany-footer`

    Positioned absolutely at the bottom on top of the main content, contains the copyright and the button to navigate to the contact view.

    ![](images/floating-footer.png)

## Components
- **Avatar** - `humany-avatar`

    An avatar image.

    ![](images/floating-avatar.png)

- **Top and middle row notices** - `humany-top-notice`

    Top and middle row notices are grouped and displayed together.

    ![](images/floating-top-notice.png)

- **Categories** - `humany-category-list`

    The categories are not rendered as a 'traditional' tree in this widget. They are separated on top and sub categories. Contains a hidden loader which is shown when fetching categories.

    ![](images/floating-categories.png)

    - **Top categories** - `humany-top-categories`

        ![](images/floating-top-categories.png)
        
    - **Sub categories** - `humany-sub-categories`

        ![](images/floating-sub-categories.png)

- **Search** - `humany-search-wrapper`
    
    The search field is hidden, tucked away to the left of the category list, by default. It is shown when clicking on the search button in the header.

    ![](images/floating-search-wrapper.png)

- **Guide list** - `humany-guide-list`

    Contains the guide list, uses `humany-item-list`, and a loader which is shown when fetching guides.

    ![](images/floating-guide-list.png)


- **List and free text notices** - `humany-categorized-notice-list`

    Contains both list and free text notices separated by category.

    ![](images/floating-categorized-notice-list.png)

    - **List notice:** - `humany-list-notice`

    ![](images/floating-list-notice.png)

    - **Expanded list notice:** - `humany-list-notice, humany-expanded`

    ![](images/floating-list-notice-expanded.png)
    
    - **Free text notice:** - `humany-free-text-notice`

    ![](images/floating-free-text-notice.png)

- **Foot notices** - `humany-bottom-notice-list`

    Contains a list of all the foot notices.

    ![](images/floating-foot-notices.png)

    
- **Guide** - `humany-guide`

    An opened guide. Can contain contact method, dialog and feedback lists.

    ![](images/floating-guide.png)

    - **Feedback list** - `humany-feedback-list`

    ![](images/floating-feedback-list.png)

    - **Dialog list** - `humany-dialog-list`
    
    ![](images/floating-dialog-list.png)

- **Contact method selector** - `humany-contact-list`

    Levels of contact method categories. If selected category has sub categories, those categories will be displayed in another level.
    If not, the contact methods within the selected category will be displayed in a contact method list.

    ![](images/floating-contact-selector.png)

- **Contact method list** - `humany-contact-list`

    Simple list of contact methods.

    ![](images/floating-contact-list.png)

- **Contact button** - `humany-contact-button`

    Button to navigate to the contact view. Positioned inside `humany-contact-button-wrapper` which is positioned absolutely at the bottom.

    ![](images/floating-contact-button.png)