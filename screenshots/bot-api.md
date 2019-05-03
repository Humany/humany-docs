# Bot API Overview

![bot-api](bot-api.png)

[Edit](http://www.nomnoml.com.s3-website-eu-west-1.amazonaws.com/#view/%5B%3Cusecase%3EWidget%20Analytics%20(GA)%5D%20-%3E%20%5BWidget%20Tracking%5D%0A%5BWidget%20Tracking%5D%20-%3E%20%5B%3Cabstract%3EDataSource%5D%0A%5B%3Cusecase%3EAce%20Chat%5D%20-%3E%20%5BWidget%20Chat%5D%0A%5BWidget%20Chat%5D%20-%3E%20%5B%3Cabstract%3EDataSource%5D%0A%5B%3Cusecase%3EBankID%5D%20-%3E%20%5BConversation%20Platform%5D%0A%5B%3Cusecase%3EPlugins%5D%20-%3E%20%5BConversation%20Platform%5D%0A%5BConversation%20Platform%5D%20-%3E%20%5B%3Cabstract%3EDataSource%5D%0A%5B%3Cusecase%3EWidget%20Types%20Bot%5D%20-%3E%20%5B%3Cabstract%3EDataSource%5D%0A%5B%3Cusecase%3EWidget%20Types%20Bot%5D%20-%3E%20%5BCore%5D%0A%5BWidget%20Contact%20Adapter%5D%20-%3E%20%5BCore%5D%0A%5BWidget%20Contact%20Adapter%5D%20-%3E%20%5BWidget%20Forms%5D%0A%5B%3Cabstract%3EDataSource%5D%20-%3E%20%5B%3Cabstract%3EConversations%20API%5D%0A%5B%3Cabstract%3EDataSource%5D%20-%3E%20%5BServiceClient%5D%0A%5BServiceClient%5D%20-%3E%20%5BContact%20API%5D%0A)

```
[<usecase>Widget Analytics (GA)] -> [Widget Tracking]
[Widget Tracking] -> [<abstract>DataSource]
[<usecase>Ace Chat] -> [Widget Chat]
[Widget Chat] -> [<abstract>DataSource]
[<usecase>BankID] -> [Conversation Platform]
[<usecase>Plugins] -> [Conversation Platform]
[Conversation Platform] -> [<abstract>DataSource]
[<usecase>Widget Types Bot] -> [<abstract>DataSource]
[<usecase>Widget Types Bot] -> [Core]
[Widget Contact Adapter] -> [Core]
[Widget Contact Adapter] -> [Widget Forms]
[<abstract>DataSource] -> [<abstract>Conversations API]
[<abstract>DataSource] -> [ServiceClient]
[ServiceClient] -> [Contact API]
```