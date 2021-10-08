---
title: Create deep links 
description: Describes deep links and how to use them in your apps
ms.topic: how-to
ms.localizationpriority: medium
keywords: teams deep link deeplink
---

# Create deep links 

You can create links to information and features within Teams. The scenarios where creating deep links are useful are as follows:

* Navigating the user to the content within one of your app's tabs. For instance, your app can have a bot that sends messages notifying the user of an important activity. When the user taps on the notification, the deep link navigates to the tab so that the user can view more details about the activity.
* Your app automates or simplifies certain user tasks, such as creating a chat or scheduling a meeting, by pre populating the deep links with required parameters. This avoids the need for users to manually enter information.

> [!NOTE]
>
> A deeplink launches the browser first before navigating to content. The behaviour of deep links on Teams entities are as follows:
>
> **Tab**:  
> ✔ Directly navigates to the deeplink url.
>
> **Bot**:  
> ✔ Deeplink in card body: Opens in browser first.  
> ✔ Deeplink added to OpenURL action in Adaptive Card: Directly navigates to the deeplink url.  
> ✔ Hyperlink markdown text in the card: Opens in browser first.  
>
> **Chat**:  
> ✔ Text message hyperlink markdown: Directly navigates to deeplink url.  
> ✔ Link pasted in general chat conversation: Directly navigates to deeplink url.

## Deep linking to your tab

You can create deep links to entities in Teams. This is used to create links that navigate to content and information within your tab. For example, if your tab contains a task list, team members can create and share links to individual tasks. When you select the link, it navigates to your tab which focuses on the specific item. To implement this, you add a **copy link** action to each item, in whatever way best suits your UI. When the user takes this action, you call `shareDeepLink()` to display a dialog box containing a link that the user can copy to the clipboard. When you make this call, you also pass an ID for your item, which you get back in the [context](~/tabs/how-to/access-teams-context.md) when the link is followed and your tab is reloaded.

Alternatively, you can also generate deep links programmatically, using the format specified later in this topic. You can use deep links in [bot](~/bots/what-are-bots.md) and [connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) messages that inform users about changes to your tab, or to items within it.

> [!NOTE]
> This deep link is different from the links provided by the **Copy link to tab** menu item, which just generates a deep link that points to this tab.

>[!NOTE]
> Currently, shareDeepLink does not work on mobile platforms.

### Show a deep link to an item within your tab

To show a dialog box that contains a deep link to an item within your tab, call `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })`.

Provide the following fields:

* `subEntityId`: A unique identifier for the item within your tab to which you are deep linking.
* `subEntityLabel`: A label for the item to use for displaying the deep link.
* `subEntityWebUrl`: An optional field with a fallback URL to use if the client does not support rendering the tab.

### Generate a deep link to your tab

> [!NOTE]
> Personal tabs have a `personal` scope, while channel and group tabs use `team` or `group` scopes. The two tab types have a slightly different syntax since only the configurable tab has a `channel` property associated with its context object. See the [manifest](~/resources/schema/manifest-schema.md) reference for more information on tab scopes.

> [!NOTE]
> Deep links work properly only if the tab was configured using the v0.4 or later library and because of that has an entity ID. Deep links to tabs without entity IDs still navigate to the tab but cannot provide the sub entity ID to the tab.

Use the following format for a deep link that you can use in a bot, connector, or messaging extension card:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> If the bot sends a message containing a `TextBlock` with a deep link, then a new browser tab is opened when the user selects the link. This happens in Chrome and in the Microsoft Teams desktop app, both running on Linux.
> If the bot sends the same deep link URL into an `Action.OpenUrl`, then the Teams tab is opened in the current browser tab when the user selects the link. A new browser tab is not opened.

The query parameters are:

| Parameter name | Description | Example |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | The ID from your manifest. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | The ID for the item in the tab, which you provided when [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md).|Tasklist123|
| `entityWebUrl` or `subEntityWebUrl`&emsp; | An optional field with a fallback URL to use if the client does not support rendering the tab. | `https://tasklist.example.com/123` or `https://tasklist.example.com/list123/task456` |
| `entityLabel` or `subEntityLabel`&emsp; | A label for the item in your tab, to use when displaying the deep link. | Task List 123 or "Task 456 |
| `context`&emsp; </br></br>* `subEntityId`&emsp;</br></br> * `channelId`&emsp;| A JSON object containing the following fields:</br></br> * An ID for the item within the tab. </br></br> *  The Microsoft Teams channel ID that is available from the tab [context](~/tabs/how-to/access-teams-context.md). | 
| `subEntityId`&emsp; | An ID for the item within the tab. |Task456 |
| `channelId`&emsp; | The Microsoft Teams channel ID that is available from the tab [context](~/tabs/how-to/access-teams-context.md). This property is only available in configurable tabs with a scope of **team**. It is not available in static tabs, which have a scope of **personal**.| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |

Examples:

* Link to a configurable tab itself: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link to a task item within the configurable tab: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link to a static tab itself: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link to a task item within the static tab: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Ensure that all query parameters are properly URI encoded. You must follow the preceeding examples using the last example:

> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### Consume a deep link from a tab

When navigating to a deep link, Microsoft Teams simply navigates to the tab and provides a mechanism through the Microsoft Teams JavaScript library to retrieve the sub-entity ID if it exists.

The [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) call returns a context that includes the `subEntityId` field if the tab is navigated through a deep link.

## Deep linking from your tab

You can deeplink to content in Teams from your tab. This is useful if your tab needs to link to other content in Teams, such as to a channel, message, another tab or even to open a scheduling dialog. To trigger a deeplink from your tab you should call:

```Javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

This call navigates you to the correct URL, or trigger a client action, such as opening a scheduling or app install dialog. See the following example:

```Javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=​​​​​​​test%3Acontent​​​​​​​​​​​​​​");

// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

## Deep linking to a chat

You can create deep links to private chats between users by specifying the set of participants. If a chat does not exist with the specified participants, the link navigates the user to an empty new chat. New chats are  created in draft state until the user sends the first message. Otherwise, you can specify the name of the chat if it does not already exist, along with text that should be inserted into the user's compose box. You can think of this feature as a shortcut for the user taking the manual action of navigating to or creating the chat, and then typing out the message.

As an example use case, if you are returning an Office 365 user profile from your bot as a card, this deep link can allow the user to easily chat with that person.

### Generate a deep link to a chat

Use this format for a deep link that you can use in a bot, connector, or messaging extension card:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Example: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

The query parameters are:

* `users`: The comma-separated list of user IDs representing the participants of the chat. The user that performs the action is always included as a participant. Currently, the User ID field supports the Azure AD UserPrincipalName, such as an email address only.
* `topicName`: An optional field for chat's display name, in the case of a chat with 3 or more users. If this field is not specified, the chat's display name is based on the names of the participants.
* `message`: An optional field for the message text that you want to insert into the current user's compose box while the chat is in a draft state.

To use this deep link with your bot, specify this as the URL target in your card's button or tap action through the `openUrl` action type.

## Generate deep links to file in channel

The following deep link format can be used in a bot, connector, or messaging extension card:

`https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

The query parameters are:

* `fileId`: Unique file ID from Sharepoint Online, aka sourcedoc. For example 1FA202A5-3762-4F10-B550-C04F81F6ACBD
* `tenantId`: Tenant ID example, 0d9b645f-597b-41f0-a2a3-ef103fbd91bb
* `fileType`: Supported file type, such as docx, pptx, xlsx, and pdf
* `objectUrl`: Object URL of the file. The format is `https://{tenantName}.sharepoint.com/sites/{TeamName}/SharedDocuments/{ChannelName}/FileName.ext`. For example, `https://microsoft.sharepoint.com/teams/(filepath)`
* `baseUrl`: Base URL of the file. The format is `https://{tenantName}.sharepoint.com/sites/{TeamName}`. For example, `https://microsoft.sharepoint.com/teams`
* `serviceName`: Name of the service, app ID. For example, teams.
* `threadId`: The threadId is the team ID of the team where the file is stored. It is optional and cannot be set for files stored in a user's OneDrive folder. threadId - 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype
* `groupId`: Group ID of the file, ae063b79-5315-4ddb-ba70-27328ba6c31e 

> [!NOTE]
> You can see `threadId` and `groupId` in the URL from the channel.  

The following deep link format is used in a bot, connector, or messaging extension card:
`https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

The following example format shows the deeplink to files:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=0d9b645f-597b-41f0-a2a3-ef103fbd91bb&fileType=pptx&objectUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform%2FShared%20Documents%2FFC7-%20Bot%20and%20Action%20Infra%2FKaizala%20Actions%20in%20Adaptive%20Cards%20-%20Deck.pptx&baseUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform&serviceName=teams&threadId=19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype&groupId=ae063b79-5315-4ddb-ba70-27328ba6c31e`

### Serialization of this object:
```
{
fileId: "5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80",
tenantId: "0d9b645f-597b-41f0-a2a3-ef103fbd91bb",
filetype: = "pptx",
objectUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform/Shared Documents/FC7- Bot and Action Infra/Kaizala Actions in Adaptive Cards - Deck.pptx",
baseUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform",
serviceName: "teams",
threadId: = "19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype",
groupId: "ae063b79-5315-4ddb-ba70-27328ba6c31e"
}
```

## Deep linking to an app

Create deeplinks for the app after the app is listed in the Teams store. To create a link to launch Teams, append the following URL to your app ID: `https://teams.microsoft.com/l/app/<your-app-id>`. A dialog box appears to install the app. 
  
## Deep linking for SharePoint Framework tabs

The following deep link format can be used in a bot, connector or messaging extension card:
`https://teams.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> When a bot sends a TextBlock message with a deep link, a new browser tab opens when users select the link. This happens in Chrome and Microsoft Teams desktop app running on Linux.
> If the bot sends the same deep link URL into an `Action.OpenUrl`, the Teams tab opens in the current browser when the user selects the link. No new browser tab is opened.

The query parameters are:

* `appID`: Your manifest ID, for example **fe4a8eba-2a31-4737-8e33-e5fae6fee194**.

* `entityID`: The item ID that you provided when [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md). For example, **tasklist123**.
* `entityWebUrl`: An optional field with a fallback URL to use if the client does not support rendering of the tab - `https://tasklist.example.com/123` or `https://tasklist.example.com/list123/task456`.
* `entityName`: A label for the item in your tab, to use when displaying the deep link, Task List 123 or Task 456.

Example: https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList

## Deep linking to the scheduling dialog

> [!NOTE]
> This feature is currently in developer preview.

You can create deep links to the Teams built-in scheduling dialog. This is especially useful if your app helps the user complete calendar or scheduling related tasks.

### Generate a deep link to the scheduling dialog

Use the following format for a deep link that you can use in a bot, Connector, or messaging extension card:
`https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Example: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=​​​​​​​test%3Acontent​​​​​​​​​​​​​​`

> [!NOTE]
> The search parameters don't support `+` signal in place of whitespace (` `). Ensure your uri encoding code returns `%20` for spaces for example, `?subject=test%20subject` is good, but `?subject=test+subject` is bad.

The query parameters are:

* `attendees`: The optional comma-separated list of user IDs representing the attendees of the meeting. The user performing the action is the meeting organizer. The User ID field currently only supports the Azure AD UserPrincipalName, typically an email address.
* `startTime`: The optional start time of the event. This should be in [long ISO 8601 format](https://en.wikipedia.org/wiki/ISO_8601), for example *2018-03-12T23:55:25+02:00*.
* `endTime`: The optional end time of the event, also in ISO 8601 format.
* `subject`: An optional field for the meeting subject.
* `content`: An optional field for the meeting details field.

> [!NOTE]
> Currently, specifying the location is not supported. You must specify the UTC offset, it means time zones when generating your start and end times.

To use this deep link with your bot, you can specify this as the URL target in your card's button or tap action through the `openUrl` action type.

## Deep linking to an audio or audio-video call

You can create deep links to invoke audio only or audio-video calls to a single user or a group of users, by specifying the call type, as *audio* or *av*, and the participants. After the deep link is invoked and before placing the call, Teams desktop client prompts a confirmation to make the call. In case of group call, you can call a set of VoIP users and a set of PSTN users in the same deeplink invocation. 

In case of a video call, the client will ask for confirmation and turn on the caller's video for the call. The receiver of the call has a choice to respond through audio only or audio and video, through the Teams call notification window.

> [!NOTE]
> This deeplink cannot be used for invoking a meeting.

### Generate a deep link to a call

| Deep link | Format | Example |
|-----------|--------|---------|
| Make an audio call | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,&lt;user2&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com |
| Make an audio and video call | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,&lt;user2&gt;&withVideo=true | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true |
|Make an audio and video call with an optional parameter source | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,&lt;user2&gt;&withVideo=true&source=demoApp | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true&source=demoApp |  
| Make an audio and video call to a combination of VoIP and PSTN users | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,4:&lt;phonenumber&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,4:9876543210 |
  
Following are the query parameters:
* `users`: The comma-separated list of user IDs representing the participants of the call. Currently, the User ID field supports the Azure AD UserPrincipalName, typically an email address, or in case of a PSTN call, it supports a pstn mri 4:&lt;phonenumber&gt;.
* `withVideo`: This is an optional parameter, which you can use to make a video call. Setting this parameter will only turn on the caller's camera. The receiver of the call has a choice to answer through audio or audio and video call through the Teams call notification window. 
* `Source`: This is an optional parameter, which informs about the source of the deeplink.

## Code sample

| Sample name | Description | C# |Node.js|
|-------------|-------------|------|----|
|Deep Link consuming Subentity ID  |Microsoft Teams sample app for demonstrating deeplink from bot chat to tab consuming Subentity ID.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/nodejs)|

## See also

[Integrate web apps](~/samples/integrate-web-apps-overview.md)

