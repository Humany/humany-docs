# Humany Technical Documentation

Technical documentation on humany API, widgets and integration options

## Overview

Humany supports a number of integration options. Depending on your use case you may prefer to use specialized plugins, a more general plugin API, direct REST integration or webhook actions.

Another consideration is type of interface being targeted. There are two main types of interface widgets - conversational and view-based.

## View Based Widgets (Inline and Floating)

The following picture describes the relation between API options in a view-based widget such as **inline** or **floating**.

![API Overview](screenshots/widget-api.png)

## Conversational Widgets (Bot)

The following picture describes the relation between API options in the bot conversational widget.

![API Overview](screenshots/bot-api.png)


# Widget APIs

## Speialized Plugin APIs

### Tracking

### Chat

### Callback

## Adapter

## Generic Plugin API

### Messages

### Parameters

### ServiceClient

### Widget UI

# REST APIs

API requests are typically requests GET/POST requests through a "projection" path (a.k.a. widget-name), 
  e.g. https://**:application-name**.humany.net/**:widget-name**/guides.

A projection is the name of a widget that defines which categories, languages etc. that are returned.

## Conversation API

The conversational API is not currently supported and is subject to change.

## Matching API

Search for answers and retrieve content from the knowledge base.

## Notices API

List notices, news and alerts.

## Contact API

List and navigate to contact methods and post form data.

### Webhook

Pass information posted to the **Web Service* contact method to an external web hook and display the response to the user in the web widget.
