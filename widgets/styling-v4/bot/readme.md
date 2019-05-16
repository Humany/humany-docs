# Bot

## Content
- [Main layout](#main-layout)
- [Components](#components)

## Main layout

- **Header** - `humany-header`

    Contains the avatar, heading, tagline and close button in mobile view.
  
    ![](images/header.png)

- **Content** - `humany-content`

    Contains the conversation with bot and user messages and the message box with a help button.
  
    ![](images/content.png)

## Components

- **Avatar** - `humany-avatar`

    An avatar image.

    ![](images/avatar.png)

- **Conversation** - `humany-converstaion`

    A wrapper for the entire conversation.

    ![](images/conversation.png)

- **Conversation group list** - `humany-conversation-group-list`

    The messages are separated into two groups, agent and user. Each consecutive message of the same type is put into a conversation group list. If the next message is not of the same type as the previous. It is put into a new group list.

    - **Conversation group list - Agent** - `humany-conversation-group-list-agent`

        All messages from the bot.

        ![](images/conversation-group-list-agent.png)

        - **Conversation group list item - Agent** - `humany-conversation-group-list-item`

            Each item in the group list.

            ![](images/conversation-group-list-item-agent.png)

            - **Agent avatar** - `humany-avatar`

                Avatar displayed at the bottom to the left of the last group list item.

                ![](images/group-list-item-avatar.png)

            - **Conversation entry - Agent** - `humany-conversation-entry`

                A conversation entry. Contains a `humany-content-view` and a `humany-sender`. The content view is rendered as a white chat bubble with the sender below.

                ![](images/content-view-agent.png)
                ![](images/sender-agent.png)
        

    - **Conversation group list - User** - `humany-conversation-group-list-agent`

        All messages from the user.

        ![](images/conversation-group-list-user.png)

        - **Conversation group list item - User** - `humany-conversation-group-list-item`

            Each item in the group list.

            ![](images/conversation-group-list-item-user.png)

            - **Conversation entry - User** - `humany-conversation-entry`

                A conversation entry. Contains a `humany-content-view` and a `humany-sender`. The content view is rendered as a blue chat bubble with the sender below.

                ![](images/content-view-user.png)
                ![](images/sender-user.png)

- **Recommendation list** - `humany-recommendation-list`

    A list of yellow colored action buttons. Can contain an optional Paragraph component.
    
    ![](images/recommendation-list.png)
    ![](images/recommendation-list-dialog.png)

- **Suggestion list** - `humany-suggestion-list`

    A list of actions. Can contain an optional Paragraph component.
    
    ![](images/suggestion-list.png)

- **Gentle list** - `humany-gentle-list`

    A list of light grey colored actions. Can contain an optional Paragraph component.
    
    ![](images/gentle-list.png)
    ![](images/gentle-list-feedback.png)

- **Contact list** - `humany-contact-list`

    A list of contact methods.

    ![](images/contact-list.png)

- **Guide** - `humany-guide`

    A guide. Can contain forms, contact method-, dialog- and feedback lists.

    ![](images/guide.png)

    - **Feedback list** - `humany-feedback-option-list`

        ![](images/feedback-list.png)

    - **Dialog list** - `humany-dialog-list`
    
        ![](images/dialog-list.png)

- **Message box** - `humany-message-box`

    A wrapper for an input, search- and browse button.

    - **Input** - `humany-message-box-input`

        Input field for user input.

        ![](images/message-box-input.png)

    - **Browse button** - `humany-message-box-help-link`

        Button to browse for categories and/or guides.

        ![](images/message-box-help-button.png)

    - **Search button** - `humany-message-box-search-button`

        Hidden by default. Shown when the message box input is focused or has content.

        ![](images/message-box-send-button.png)

- **Category list** - `humany-category-list`

    A scrollable list of categories. Only displays the top level categories.

    ![](images/category-list.png)