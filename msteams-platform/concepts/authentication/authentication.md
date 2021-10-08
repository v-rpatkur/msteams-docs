---
title: Authenticating app users
description: Describes authentication in Teams and how to use it in the apps
ms.topic: conceptual
ms.localizationpriority: medium
keywords: teams authentication OAuth SSO AAD
---
# Authenticate users in Microsoft Teams

> [!Note]
> Web-based authentication on mobile clients requires version 1.4.1 or later of the Teams JavaScript client SDK.

To access user information protected by Azure Active Directory (AAD) and to access data from services like Facebook and Twitter, the app establishes a trusted connection with those providers. If the app uses Microsoft Graph APIs in the user scope, authenticate the user to retrieve the appropriate authentication tokens.

In Teams, there are two different authentication flows for the app. Perform a traditional web-based authentication flow in a [content page](~/tabs/how-to/create-tab-pages/content-page.md) embedded in a tab, a configuration page, or a task module. If the app contains a conversational bot, use the OAuthPrompt flow and optionally the Azure Bot Framework's token service to authenticate a user as part of a conversation.

## Web-based authentication flow

Use the web-based authentication flow for [tabs](~/tabs/what-are-tabs.md) and choose to use it with [conversational bots](~/bots/what-are-bots.md) or [messaging extensions](~/messaging-extensions/what-are-messaging-extensions.md). Use the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) in a web content page to enable authentication. After enabling authentication, embed the content page in a tab, a configuration page, or a task module. For more information on web-based authentication flow, see:

* [Add authentication to the Teams bot](~/bots/how-to/authentication/add-authentication.md) describes how to use web-based authentication flow with a conversational bot.
* [Authentication flow in tabs](~/tabs/how-to/authentication/auth-flow-tab.md) describes how tab authentication works in Teams. This shows a typical web-based authentication flow used for tabs.
* [AAD authentication in tabs](~/tabs/how-to/authentication/auth-tab-AAD.md) describes how to connect to AAD from within a tab in the app in Teams.
* [Silent authentication AAD](~/tabs/how-to/authentication/auth-silent-AAD.md) describes how to reduce sign-in or consent prompts in the app using AAD.
* [.Net or C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) or [JavaScript or Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) provides samples for web-based authentication.

## The OAuthPrompt flow for conversational bots

The Azure Bot Framework’s OAuthPrompt makes authentication easier for apps using conversational bots. Use Azure Bot Framework's token service to assist with token caching.

For more information on using OAuthPrompt, see:

* [Bot authentication flow overview](~/bots/how-to/authentication/auth-flow-bot.md) describes how authentication works within a bot in the app in Teams. This shows a non-web-based authentication flow used for bots on Teams web, desktop app, and mobile apps.
* [Bot authentication](~/bots/how-to/authentication/add-authentication.md) describes how to add OAuth authentication to the Teams bot.

## Code sample

Bot Framework v4 authentication samples.

| **Sample name** | **Description** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Bot authentication | This sample shows how to get started with authentication in a bot for Microsoft Teams. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |
| Tab, Bot and Messaging Extension (ME) SSO | This sample shows SSO for Tab, Bot and ME - search, action, linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) | Not available |


## Configure the identity provider

Regardless of the app's authentication flow, configure the identity provider to communicate with the Teams app. Most samples and walkthroughs primarily deal with using AAD as the identity provider. The concepts however, apply regardless of the identity provider. 

For more information, see [configuring an identity provider](~/concepts/authentication/configure-identity-provider.md).

