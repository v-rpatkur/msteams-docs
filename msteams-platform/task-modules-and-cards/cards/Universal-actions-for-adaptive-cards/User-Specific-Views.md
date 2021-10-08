---
title: User Specific Views
description: Sample for User Specific Views using Universal Actions
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
---

# User Specific Views

Earlier if Adaptive Cards were sent in a Teams conversation, all users see the exact same card content. With the introduction of the Universal Actions model and `refresh` for Adaptive Cards, bot developers can now provide User Specific Views of Adaptive Cards to users. The same Adaptive Card can now refresh to a User Specific Adaptive Card. Maximum 60 different users can see a different version of the card with additional information or actions. The Adaptive Card provides powerful scenarios like approvals, poll creator controls, ticketing, incident management, and project management cards.

For example, Megan, a safety inspector at Contoso, wants to create an incident and assign it to Alex. Megan also wants everyone in the team to be aware about the incident. Megan uses Contoso incident reporting message extension powered by Universal Actions for Adaptive Cards.

# [Mobile](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Mobile User Specific Views":::

# [Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="User Specific Views":::

* * *

## User Specific Views for Adaptive Cards

The following code provides an example of Adaptive Cards:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView",
      "data": {
            "refresh info": "<refresh info>"
      }
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ]
}
```

**To send Adaptive Cards, refresh User Specific Views, and invoke requests to the bot**

1. When Megan creates a new incident, the bot sends the Adaptive Card or common card with incident details in the Teams conversation.
2. Now this card automatically refreshes to User Specific View for Megan and Alex. Alex's and Megan's user MRIs are added in `userIds` property of `refresh` property of the Adaptive Card JSON. The card remains the same for other users in the conversation.
3. For Megan, automatic refresh triggers an `adaptiveCard/action` invoke request to the bot. The bot can return an incident creator card with `Edit` button as a response to this invoke request.
4. Similarly for Alex, automatic refresh triggers another `adaptiveCard/action` invoke request to the bot. The bot can return an incident owner card `Resolve` button as a response to this invoke request.

## Invoke request sent from Teams client to the bot

The following code provides an example of an invoke request sent from Alex's and Megan's Teams client to the bot:

```JSON
{ 
  "type": "invoke",
  "name": "adaptiveCard/action",

  // ... other properties omitted for brevity

  "value": { 
    "action": { 
      "type": "Action.Execute", 
      "id": "", 
      "verb": "editOrResolveView",
      "data": { 
            "refresh info": "<refresh info>"
      } 
    },
    "trigger": "automatic" 
  }
}
```

## adaptiveCard/action invoke response card

The following code provides an example of an adaptiveCard/action invoke response card for Megan:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Edit",
      "verb": "edit",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## adaptiveCard/action invoke response card for Alex

The following code provides an example of an adaptiveCard/action invoke response card for Alex:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Resolve",
      "verb": "resolve",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## Invoke response to return Adaptive Cards

The following code provides an example of an invoke response to return Adaptive Cards:

```C#
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.adaptive.card",
    value = card
 });
```

Card design guidelines to keep in mind while designing User Specific Views:

* You can create a maximum of **60 User Specific Views** for a particular card sent to a chat or channel by specifying their `userIds` in the `refresh` section.
* **Base Card:** The base version of the card that the bot developer sends to the chat. The base version is the version of the Adaptive Card for all users who are not specified in the `userIds` section.
* A message update can be used to update the base card and simultaneously refresh the User Specific Card. Opening the chat or channel also refreshes the card for users with refresh enabled.
* For scenarios with larger groups where users switch to a view on action, which needs dynamic updates for responders, you can keep adding up to 60 users to the `userIds` list. You can remove the first responder from the list when the 61st user responds. For the users who get removed from the `userIds` list, you can provide a manual refresh button or use the refresh button in the message options menu to get the latest result.
* Give a prompt to users to get a User Specific View, where they see only a particular view of the card or some actions.

## Code sample

|Sample name | Description | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Sequential Workflows Adaptive Cards | Demonstrate how to implement Sequential Workflows, User Specific Views, and up to date Adaptive Cards in bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## See also

* [Work with Universal Actions for Adaptive Cards](Work-with-universal-actions-for-adaptive-cards.md)
* [Up to date views](Up-To-Date-Views.md)
