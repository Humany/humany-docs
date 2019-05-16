# Bot

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

        - **Avatar** - `humany-avatar`

        Avatar displayed at the bottom to the left of the last group list item.

        ![](images/group-list-item-avatar.png)

        - **Conversation entry - Agent**

        A conversation entry. Contains a `humany-content-view` and a `humany-sender`. The content view is rendered as a white chat bubble with the sender below.

        ![](images/content-view-agent.png)

        ![](images/sender-agent.png)
    
