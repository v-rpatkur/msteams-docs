---
title: What's new
description: Describes all the new developer features in Microsoft Teams
ms.topic: reference
ms.localizationpriority: medium
keywords: teams what's new latest
---

# What's new for developers in Microsoft Teams

Discover Microsoft Teams platform features that are generally available (GA) and in developer preview.

> [!IMPORTANT]
> You can now get latest Teams platform updates by subscribing to the RSS feed [![download feed](~/assets/images/RSSfeeds.png)](https://aka.ms/TeamsPlatformUpdates). For more information, see [configure RSS feed](#get-latest-updates).

## GA features

Microsoft Teams platform features that are available to all app developers.

<br>

<details>

<summary><b>2021</b></summary>

| **Date** | **Notes** | **Changed topics** |
| -------- | --------- | ------------------ |
|10/05/2021| Hide Teams app until Admin allows to unhide the app. | [Hide Teams app until admin approves](concepts/design/enable-app-customization.md#hide-teams-app-until-admin-approves) 
|10/05/2021|Plan your apps for Teams mobile|[Plan responsive tabs for Teams mobile](concepts/design/plan-responsive-tabs-for-teams-mobile.md)|
|10/04/2021| New Developer Portal for Teams introduced for managing your Teams apps. | [Developer Portal for Teams](concepts/build-and-test/teams-developer-portal.md) |
|09/21/2021|Teams supports AAD Object ID and UPN in user mention for bots and Incoming Webhooks. |[AAD Object ID and UPN in user mention](task-modules-and-cards/cards/cards-format.md#format-cards-with-markdown), [Cards- Overview](task-modules-and-cards/what-are-cards.md#support-for-aad-object-id-and-upn-in-user-mention)|
|09/08/2021|Meeting stage is now available in GA.|[Enable and configure your apps for Teams meetings](apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md)|
|08/16/2021| Support for input validation on Adaptive Cards (v1.3 for all capabilities) and Universal Actions (v1.4 for bot sent cards). |[Input validation](/adaptive-cards/authoring-cards/input-validation), [Universal Actions for Adaptive Cards v1.4](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/overview.md) |
|08/09/2021|Meeting stage is now available in GA.|[Enable and configure your apps for Teams meetings](apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md)|
|08/30/2021| Custom Together Mode scenes feature combines participants into a single virtual scene and places their video streams in pre-determined seats. | [Custom Together Mode scenes](~/apps-in-teams-meetings/teams-together-mode.md) |
|08/25/2021| Introduced step-by-step guide to create a Teams bot with Single sign-on (SSO). | [Step-by-step guide to create Teams bot with SSO](sbs-bots-with-sso.yml) |
|08/19/2021| Installation update event received when you install a bot to a conversation thread. | [Installation update event](bots/how-to/conversations/subscribe-to-conversation-events.md#installation-update-event) |
|08/12/2021|Build tabs with Adaptive Cards|[Build tabs with Adaptive Cards](tabs/how-to/build-adaptive-card-tabs.md)|
|08/04/2021| Tabs will no longer have margins surrounding their experiences.  | [Removing tab margins](resources/removing-tab-margins.md) |
|07/08/2021|Meeting app extensibility is available on mobile. Mobile clients support apps during meeting. |[Meeting app extensibility](apps-in-teams-meetings/meeting-app-extensibility.md)|
|06/28/2021|Integrate People Picker capability.|[Integrate People Picker capability](concepts/device-capabilities/people-picker-capability.md)|  
|06/25/2021| Introduced step-by-step guide to send proactive messages. | [Step-by-step guide to send proactive messages](sbs-send-proactive.yml) |
|06/09/2021| Stage view for images in Adaptive Cards with `allowExpand` attribute. | [Stage view for images in Adaptive Cards](~/task-modules-and-cards/cards/cards-format.md) |
|05/31/2021| Conversational tabs. | [Start and continue conversations about content in your tabs](~/tabs/how-to/conversational-tabs.md) |
|05/24/2021| Updated Teams app design guidelines with mobile patterns and more.|[Designing your Teams app](~/concepts/design/design-teams-app-overview.md)
|05/13/2021| Added information on mConnect and Skooler.|[Moodle learning management system](resources/moodle-overview.md)
|05/10/2021| Manifest v1.10 is released.|[Manifest schema](resources/schema/manifest-schema.md) |
|05/10/2021| New app customization feature.| [Enable orgs to customize your app](concepts/design/enable-app-customization.md) |
|05/07/2021| Deep links for audio and video calls in chat. |[Deep links](concepts/build-and-test/deep-links.md#deep-linking-to-an-audio-or-audio-video-call) |
|04/30/2021|New guidance on how to publish apps to the Teams store.|[Publish your app to the Teams store](concepts/deploy-and-publish/appsource/publish.md), [Teams store validation guidelines](concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) |
|04/29/2021 | Support for Universal Actions for Adaptive Cards v1.4. | [Universal Actions for Adaptive Cards](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/overview.md) |
|04/29/2021 | User Specific Views. | [User Specific Views](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/User-Specific-Views.md) |
|04/29/2021 | Sequential Workflows. | [Sequential Workflows](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/Sequential-Workflows.md) |
|04/29/2021 | Up to date cards. | [Up to date cards](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/Up-To-Date-Views.md) |
|04/08/2021| App customization feature.|[Design teams app overview](concepts/design/enable-app-customization.md), [App studio overview](concepts/build-and-test/app-studio-overview.md#connectors), and [Manifest schema](resources/schema/manifest-schema-dev-preview.md) |
|03/18/2021|Notice: Update to version 4.10 or above of the Bot Framework SDK, as we've started with the deprecation process for `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync`. | [Bot API Changes for Team/Chat Members](resources/team-chat-member-api-changes.md) |
|03/05/2021|Default install scope and group capability.| [Default install scope and group capability](concepts/deploy-and-publish/add-default-install-scope.md) |
|03/05/2021|Reorder personal app tabs.|[Reorder the chat tab in personal apps](tabs/how-to/create-personal-tab.md#reorder-static-personal-tabs)|
|03/04/2021|Information masking in Adaptive cards.| [Information masking in Adaptive cards](task-modules-and-cards/cards/cards-format.md#information-masking-in-adaptive-cards) |
|02/19/2021|Added location capabilities. <br/> Location capabilities information is added in the device capabilities overview, native device permissions, integrate media capabilities, and QR or barcode scanner capability files.|[Overview](concepts/device-capabilities/device-capabilities-overview.md), [Request device permissions](concepts/device-capabilities/native-device-permissions.md), [Integrate media capabilities](concepts/device-capabilities/mobile-camera-image-permissions.md), [Integrate QR or barcode scanner capability](concepts/device-capabilities/qr-barcode-scanner-capability.md), [Integrate location capabilities](concepts/device-capabilities/location-capability.md) |
|02/18/2021|Added QR or barcode scanner capability. <br/> QR or barcode scanner  capability information is added in the device capabilities overview, native device permissions, and integrate media capabilities files.|[Overview](concepts/device-capabilities/device-capabilities-overview.md), [Request device permissions](concepts/device-capabilities/native-device-permissions.md), [Integrate media capabilities](concepts/device-capabilities/mobile-camera-image-permissions.md), [Integrate QR or barcode scanner capability](concepts/device-capabilities/qr-barcode-scanner-capability.md) |
|02/09/2021|Added device capabilities overview. <br/> Microphone capability information is added in the native device permissions and integrate media capabilities files.|[Overview](concepts/device-capabilities/device-capabilities-overview.md), [Request device permissions](concepts/device-capabilities/native-device-permissions.md), [Integrate media capabilities](concepts/device-capabilities/mobile-camera-image-permissions.md)|

<br>

</details>

<br>

<details>
  
<summary><b>2020</b></summary>

| **Date** | **Notes** | **Changed topics** |
| -------- | --------- | ------------------ |
|11/30/2020|Identity platform integration with Teams Toolkit and Visual Studio Code for tabs.|[Single sign-on authentication with Teams Toolkit and Visual Studio Code for tabs](toolkit/visual-studio-code-tab-sso.md)|
|11/16/2020|Teams app manifest updated to version 1.8.|[Reference: Manifest schema for Microsoft Teams](resources/schema/manifest-schema.md)|
|11/10/2020|Teams bot design guidelines.|[Bot design guidelines](bots/design/bots.md)|
|09/30/2020|Sending and receiving files to bots on mobile devices is now supported.|[Send and receive files through your bot](resources/bot-v3/bots-files.md)|
|09/22/2020|New information for getting started with Teams development.|[Build your first Teams app overview](build-your-first-app/build-first-app-overview.md)|
|09/18/2020|Support for in-meeting Teams apps (Release Preview).|[Create apps for Teams meetings](apps-in-teams-meetings/create-apps-for-teams-meetings.md) and [Apps in Teams meetings](apps-in-teams-meetings/teams-apps-in-meetings.md)|
|08/19/2020|Import Teams messages with Microsoft Graph.|[Import third-party platform messages to Teams using Microsoft Graph](graph-api/import-messages/import-external-messages-to-teams.md)
|08/12/2020 |Adaptive Cards support in incoming webhook moved to GA.|[Send adaptive cards using an incoming webhook](~/webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook) |
|08/10/2020|Get started building Teams apps with the Visual Studio Toolkit.|[Build apps with the Microsoft Teams Toolkit and Visual Studio Code](toolkit/visual-studio-overview.md) |
|08/06/2020|Support for Tabs SSO authentication.|[Develop an SSO Microsoft Teams Tab](tabs/how-to/authentication/auth-aad-sso.md#develop-an-sso-microsoft-teams-tab) |
|07/27/2020 | Graph proactive bots and messages (Public Preview).|[Enable proactive bot installation and proactive messaging in Teams with Microsoft Graph](graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)|
|07/22/2020 |Mobile device capability updates.|[Request device permissions for your Microsoft Teams tab](concepts/device-capabilities/native-device-permissions.md) |
|07/20/2020|Teams App Validation Tool for AppSource submissions.|[Teams App Validation Tool](concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
|07/15/2020|Create a virtual assistant for Teams.|[Virtual Assistant for Microsoft Teams](samples/virtual-assistant.md)|
|07/14/2020|Surfacing a native loading indicator documentation.|[Showing a native loading indicator](tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)
|07/01/2020|Get started building Teams apps with the Visual Studio Code Toolkit.|[Build apps with the Microsoft Teams Toolkit and Visual Studio Code](toolkit/visual-studio-code-overview.md) |
|07/01/2020|Single sign-on for tabs GA for Teams web and desktop clients.|[Single Sign-On (SSO)](tabs/how-to/authentication/auth-aad-sso.md)|
|06/05/2020| Manifest schema updated to version 1.7.| [Reference: Manifest schema for Microsoft Teams](resources/schema/manifest-schema.md)|
|05/18/2020|Integrate Power Virtual Agents with Teams.|[Integrate a Power Virtual Agents chatbot with Microsoft Teams](bots/how-to/add-power-virtual-agents-bot-to-teams.md)|
|04/01/2020|Integrate WFM systems with Shifts Connector for Teams.|[Microsoft Teams Shifts WFM connectors](samples/shifts-wfm-connectors.md)
|03/24/2020 | Added support for retrieving a single member of a conversation, and additional support for retrieving paged members. | [Get Teams context for your bot](~/bots/how-to/get-teams-context.md) |

<br>

</details>

<br>

<details>
  
<summary><b>2019</b></summary>

| **Date** | **Notes** | **Changed topics** |
| -------- | --------- | ------------------ |
| 12/26/2019 | The `replyToId` parameter in payloads sent to a bot is no longer encrypted, allowing you to use this value to construct deeplinks to these messages. Message payloads include the encrypted values in the parameter `legacy.replyToId`.  |
| 11/05/2019 | Single sign-on using the Teams JavaScript SDK. | [Single sign-on](tabs/how-to/authentication/auth-aad-sso.md) |
| 10/31/2019 | Conversational bots and messaging extension documentation updated to reflect the 4.6 Bot Framework SDK. Documentation for the v3 SDK is available in the Resources section. | All bot and messaging extension documentation. |
| 10/31/2019 | New documentation structure, and major article refactoring. Please report any dead links or 404's by creating a GitHub Issue. | All of them! |
| 09/13/2019 | Request bot is installed from action-based messaging extension. | [Initiate actions with messaging extensions](resources/messaging-extension-v3/create-extensions.md#request-to-install-your-conversational-bot)
| 08/28/2019 | Support for private channels in tabs and Connectors. | [Get context for your tab](tabs/how-to/access-teams-context.md#retrieve-context-in-private-channels) |
| 06/20/2019 | Share an external website, from an external website, into a Teams channel. | [Share to Teams](~/share-to-teams.md) |
| 05/25/2019 | Respond with bot message from task module. | [Respond with bot message from task module](resources/messaging-extension-v3/create-extensions.md#respond-with-an-adaptive-card-message-sent-from-a-bot) |
| 05/25/2019 | Bots in group chats. | [Interact with a bot in group chat or channel](~/concepts/bots/bot-conversations/bots-conv-channel.md) |
| 05/20/2019 | App manifest localization. | [App localization](~/publishing/apps-localization.md) |
| 05/20/2019 | Message actions. | [Message Actions](resources/messaging-extension-v3/create-extensions.md#action-type-message-extensions) |
| 05/20/2019 | Link unfurling (custom URL previews). | [Link unfurling](messaging-extensions/how-to/link-unfurling.md)|
| 05/06/2019 | Application Certification program for store apps. | [Application Certification](~/concepts/deploy-and-publish/appsource/post-publish/overview.md#complete-microsoft-365-certification) |
| 05/06/2019 | App Templates are now available. | [App Templates](~/samples/app-templates.md) |
| 04/23/2019 | Action-based Messaging Extensions are now available. | [Action-based Message Extensions](~/concepts/messaging-extensions/create-extensions.md) |
| 02/18/2019 | Creating deep links to private chat. | [Deep linking to a chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 01/23/2019 | Surfacing SKU and licenceType information in the tab context. | [Tab Context](~/concepts/tabs/tabs-context.md) |

<br>

</details>

<br>

<details>

<summary><b>2018</b></summary>

| **Date** | **Notes** | **Changed topics** |
| -------- | --------- | ------------------ |
| 11/12/2018 | Tabs in group chat is now available in the released version of Teams. As part of this work, the tabs section has been reworked for clarity.| [Configurable tabs](~/concepts/tabs/tabs-configurable.md) |
| 11/11/2018 | Getting started for Node JS and for .NET/C# has been updated to use App Studio in Teams, and a new section has been added on hosting Node based Teams apps in Azure. | [Get started on the Microsoft Teams platform with C#/.NET and App Studio](~/get-started/get-started-dotnet-app-studio.md),  [Get started on the Microsoft Teams platform with Node JS and App Studio](~/get-started/get-started-nodejs-app-studio.md), [Host your Node Teams app in Azure](~/get-started/get-started-nodejs-in-azure.md)|
| 11/09/2018 | You can now create deep links to private chats between users. | [Deep linking to a chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 11/08/2018 | SharePoint Framework 1.7 has shipped and with it a new feature to use Microsoft Teams tab as a SharePoint Framework web part. | [Tabs in SharePoint](~/concepts/tabs/tabs-in-sharepoint.md) |
| 11/05/2018 | The **task module** feature was released. A task module allows you to create modal popup experiences in your Teams application, from both bots and tabs. Inside the popup, you can run your own custom HTML/JavaScript code, show an `<iframe>`-based widget such as a YouTube or Microsoft Stream video, or display an [Adaptive card](/adaptive-cards/). | [Task module Overview](~/concepts/task-modules/task-modules-overview.md), [task module in tabs](~/concepts/task-modules/task-modules-tabs.md),  [task module in bots](~/concepts/task-modules/task-modules-bots.md) |
| 10/05/2018 | Formatting information for cards has been updated and tested in the desktop, iOS, and Android clients for Teams. | [Cards](~/concepts/cards/cards.md), [Card formatting](~/concepts/cards/cards-format.md) |
| 09/24/2018 | Calls and online meetings APIs for Microsoft Graph were released to beta, and Teams apps can now interact with users in rich ways using voice and video. | [Calls and online meetings bots](~/concepts/calls-and-meetings/registering-calling-bot.md), [Real-time media concepts](~/concepts/calls-and-meetings/real-time-media-concepts.md), [Registering a calling bot](~/concepts/calls-and-meetings/registering-calling-bot.md), [Debugging and local testing](~/concepts/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md), [Application-hosted media](~/concepts/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md), [Handling incoming call notifications](~/concepts/calls-and-meetings/call-notifications.md) |
| 09/11/2018 | Tab configuration pages are now significantly taller. | [Tab Design](tabs/design/tabs.md) |
| 08/15/2018 | Adaptive cards are now supported in Teams.|[Adaptive card actions in Teams](task-modules-and-cards/cards/cards-reference.md#adaptive-card) |
| 08/10/2018 | Client support for DevTools.| [DevTools for the Microsoft Teams Desktop Client](~/resources/dev-preview/developer-preview-tools.md)|
| 08/08/2018 | Messaging extensions now supports multiple commands. | [composeExtensions.commands](~/resources/schema/manifest-schema.md#composeextensionscommands)|
| 08/07/2018 | Inline configuration is now supported in Connectors. The Connectors documentation has also been revised and expanded for clarity.| [Connectors](~/concepts/connectors/connectors.md)|
| 08/06/2018 | Your bot can now send and receive files.| [Send and receive files through your bot](~/bots/how-to/bots-filesv4.md)|
| 07/23/2018 | Information about app re-certification has been added to the Publishing section. |[Manifest permissions](resources/schema/manifest-schema.md#permissions)|
| 07/16/2018 | More space has been allocated to the tab configuration page. | [The tab configuration page is significantly taller](tabs/design/tabs.md)|
| 07/12/2018 | Information on guest access. | [Guest access in Microsoft Teams](/microsoftteams/guest-access#guest-access-overview)|
| 06/07/2018 | Information for the Microsoft Teams Tenant App Catalog has been added. | [Publish your Microsoft Teams app](~/publishing/apps-publish.md)|
| 05/29/2018 | Adaptive cards are supported in Teams. | [Adaptive card actions in Teams](task-modules-and-cards/cards/cards-reference.md) |
| 04/17/2018 | replyToID has been added to the payload for the `Invoke` and `MessageBack` card actions. This is especially useful if you need to update the message that the card action came from. | [Card actions](~/concepts/cards/cards-actions.md)|
| 04/12/2018 | Added this topic to track changes to the Teams programming interface and this documentation set. | [What's new](~/whats-new.md)|
| 04/10/2018 | Changed authentication URLs to consistently use the tenant ID in the path. | [Authentication flow for Tabs](~/concepts/authentication/auth-flow-tab.md), [AAD Tab authentication](~/concepts/authentication/auth-tab-AAD.md)|
| 04/06/2018 | Added design guidelines for using the Command Box. |[Command box](~/resources/design/framework/command-box.md)|
| 04/02/2018 | Using bots to send notifications for your app. |[Notification-only bots](~/concepts/bots/bots-notification-only.md)|
| 03/27/2018 | Expanded documentation for proactive messaging. |[Starting a conversation](./concepts/bots/bot-conversations/bots-conv-proactive.md)|
| 03/15/2018 | Refactored documentation for cards. |[Cards](~/concepts/cards/cards.md), [Card actions](~/concepts/cards/cards-actions.md), [Card formatting](~/concepts/cards/cards-format.md), [Card reference](~/concepts/cards/cards-reference.md)|
| 03/03/2018 | Added documentation for Teams App Studio. |[Quickly develop apps with Teams App Studio](~/get-started/get-started-app-studio.md), [Using the control library in App Studio](~/get-started/app-studio-component-library.md)|
| 02/27/2018 | Added sample code to demonstrate AsTeamsChannelAccounts() method. |[Get context for your bot](~/concepts/bots/bots-context.md)|
| 02/05/2018 | Added topics for getting started using C#. |[Get started on the Microsoft Teams platform with C#/.NET](./get-started/get-started-dotnet-app-studio.md)|

<br>

</details>

## Developer preview

Developer preview is a public program that provides early access to unreleased Teams platform features.  

| **Date** | **Notes** | **Changed topics** |
| -------- | --------- | ------------------ |
|06/23/2021| Meeting Details API and real-time Teams meeting events. | [Create apps for Teams meetings](~/apps-in-teams-meetings/API-references.md#meeting-details-api) |
|06/21/2021|Uninstall behavior for personal app with bot | [Uninstall behavior updates in personal apps with bots](bots/how-to/conversations/subscribe-to-conversation-events.md#uninstall-behavior-for-personal-app-with-bot)|
|06/16/2021| Resource-specific consent for chats. |[Resource-specific consent](graph-api/rsc/resource-specific-consent.md), [Test resource-specific consent permissions in Teams](graph-api/rsc/test-resource-specific-consent.md)|
|05/25/2021| Updated Teams Toolkit for [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) and [Visual Studio](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit&ssr=false#overview). | [Get started with Teams app development](~/get-started/prerequisites.md) |
|05/24/2021|Bots can be enabled to receive all channel messages using resource-specific consent (RSC).|[Receive all messages with RSC](~/bots/how-to/conversations/channel-messages-with-rsc.md), [bot conversation overview](~/bots/how-to/conversations/conversation-basics.md), [channel and group conversations](~/bots/how-to/conversations/channel-and-group-conversations.md), and [developer preview manifest schema](~/resources/schema/manifest-schema-dev-preview.md) |
|05/21/2021|Tabs link unfurling and stage view|[Tabs link unfurling and stage view](tabs/tabs-link-unfurling.md) |

For more information, see [public developer preview for Teams](~/resources/dev-preview/developer-preview-intro.md).

## Teams app template catalog

Along with new features, we also provide [production-ready Teams app templates](samples/app-templates.md) that you can deploy right away or modify to your needs. Newly added templates are indicated with a star ☆.

## Submit your feedback

We encourage Teams developers to ask questions, file bugs, submit feature requests, and make contributions. You can submit feedback through any of the [available channels](feedback.md).

## Get latest updates

You can get the latest Teams platform updates by configuring to the [RSS feed](https://aka.ms/TeamsPlatformUpdates).

**To configure RSS feed**

1. Open Microsoft Teams.
1. Select **Teams** from the left pane.
1. Select a channel in the team.
1. Select ellipses &#x25CF;&#x25CF;&#x25CF; and from the dropdown list, select **Connectors**.
1. Search for **RSS** in the **Connectors** dialog box that appears.
1. Select **Configure**.
1. Enter a name in **Enter a name for your RSS connection.**.
1. Enter **https://aka.ms/TeamsPlatformUpdates** in **Address for RSS feed**.
1. Select the frequency of the feed from the **Digest frequency** dropdown list.
1. Select **Save**.
