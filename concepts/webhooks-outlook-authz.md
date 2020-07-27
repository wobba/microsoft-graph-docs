---
title: "Reduce missing subscriptions and change notifications for Outlook resources (preview)"
description: "Outlook might suspend delivery of change notifications due to security events such as user's password reset. Special lifecycle events - `subscriptionRemoved` and `missed` - need to be handled to ensure uninterrupted delivery of change notifications."
author: "baywet"
localization_priority: Priority
ms.custom: graphiamtop20
---

# Reduce missing subscriptions and change notifications for Outlook resources (preview) 

Apps subscribing to change notifications for Outlook resources might get their subscriptions removed and miss some change notifications. Apps should implement logic to detect and recover from the loss, and resume a continuous change notification flow.

Certain events in Outlook can cause a subscription to be removed. These events include:

- User's password has been reset
- User's device is out of compliance
-	User's account has been revoked

When such an event happens, Outlook sends a special lifecycle notification, `subscriptionRemoved`.

Outlook also sends another lifecycle notification, `missed`, if a change notification cannot be delivered to an app.

An app subscribing to change notifications for Outlook resources, such as **message** and **event**, should listen to the `subscriptionRemoved` and `missed` signals and do the following:

- Upon receiving a `subscriptionRemoved` lifecycle notification, the app should recreate the subscription in order to maintain a continuous flow.
- On receiving a `missed` lifecycle notification, the app should resynchronize resource data using Microsoft Graph.

To receive lifecycle notifications, you can use the existing **notificationUrl** endpoint that already receives change notifications, or you can register a separate **lifecycleNotificationUrl** to receive `subscriptionRemoved` and `missed` lifecycle notifications in a separate endpoint.

## Creating a subscription

When creating a subscription, you must specify a separate notification endpoint using the **lifecycleNotificationUrl** property. If you specify the endpoint, all current and future types of lifecycle notifications will be delivered there. Otherwise, `subscriptionRemoved` and `missed` lifecycle notifications will not be delivered.

> **Note:** The **lifecycleNotificationUrl** property can only be set or read using Microsoft Graph beta APIs. However, subscriptions created using beta APIs are stored in the same production environment as those created using v1.0, so you can implement the new Outlook flow in addition to your subscriptions creating using v1.0 APIs.

> Subscriptions created via the v1.0 APIs will receive lifecycle notifications. 

### Subscription request example

```http
POST https://graph.microsoft.com/beta/subscriptions
Content-Type: application/json
{
  "changeType": "created,updated",
  "notificationUrl": "https://webhook.azurewebsites.net/api/resourceNotifications",
  "lifecycleNotificationUrl": "https://webhook.azurewebsites.net/api/lifecycleNotifications",
  "resource": "/users/{id}/messages",
  "expirationDateTime": "2019-03-20T11:00:00.0000000Z",
  "clientState": "<secretClientState>"
}
```
 
> **Important:** Use the same hostname for both notifications URLs. 

> **Note:** You need to validate both endpoints as described in [Managing subscriptions](webhooks.md#managing-subscriptions).
If you choose to use the same URL for both endpoints you will receive and respond to two validation requests.

> **Note:** You cannot update (`PATCH`) the existing subscriptions to add the **lifecycleNotificationUrl** property. You should remove such existing subscriptions, and create new subscriptions and specify the **lifecycleNotificationUrl** property. Existing subscriptions without **lifecycleNotificationUrl** property will not receive the `subscriptionRemoved` and `missed`.

## Responding to subscriptionRemoved notifications

The `subscriptionRemoved` lifecycle notification informs you that a subscription has been removed and should be recreated, if you want to continue receiving change notifications. 

You can create a long-lived subscription (3 days), and change notifications will start flowing to the **notificationUrl**. However, the conditions of access to the resource data might change over time. For example, an event in the Outlook service might occur that requires the app to re-authenticate the user. In such a case, the flow is as follows:

1. Outlook detects that a subscription needs to be removed from Microsoft Graph.
    
    There is no set cadence for these events. They might occur frequently for some resources, and almost never for others.

2. Microsoft Graph sends a `subscriptionRemoved` lifecycle notification to the **lifecycleNotificationUrl** (if specified).  

3. You can respond to this lifecycle notification by creating a new subscription for the same resource. To do this, you need to present a valid access token; in some cases this means the app needs to re-authenticate the user to obtain a new valid access token.

4. If you successfully create a new subscription, change notifications will start flowing again. However, if you fail (for example, the app can't obtain a valid access token), change notifications will not be sent.

5. After creating the new subscription, you can sync the resource data to identify any missing changes.

### subscriptionRemoved notification example

```json
{
  "value": [
    {
      "subscriptionId":"<subscription_guid>",
      "subscriptionExpirationDateTime":"2019-03-20T11:00:00.0000000Z",
      "tenantId": "<tenant_guid>",
      "clientState":"<secretClientState>",
      "lifecycleEvent": "subscriptionRemoved"
    }
  ]
}
```

A few things to note about this type of notification:
- The `"lifecycleEvent": "subscriptionRemoved"` field designates this notification as related to subscription removal. Other types of lifecycle notifications are also possible, and new ones will be introduced in the future.
- The lifecycle notification does not contain any information about a specific resource, because it is not related to a resource change, but to the subscription state change.
- Similar to change notifications, lifecycle notifications can be batched together (in the **value** array), each with a possibly different **lifecycleEvent** value. Process each lifecycle notification in the batch accordingly.

> **Note:** for a full description of the data sent when change notifications are delivered, see [changeNotificationCollection](/graph/api/resources/changenotificationcollection).

### Actions to take

1. [Acknowledge](webhooks.md#change-notifications) the receipt of the lifecycle notification, by responding to the POST call with `202 - Accepted`.
2. [Validate](webhooks.md#change-notifications) the authenticity of the lifecycle notification.
3. Ensure that the app has a valid access token to take the next step. 
  > **Note:** If you're using one of the [authentication libraries](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries), they will handle this for you by either reusing a valid cached token, or obtaining a new token, including asking the user to sign in again (with a new password). Note that obtaining a new token might fail, because the conditions of access might have changed, and the caller might no longer be allowed access to the resource data.

4. Create a new subscription using the standard process described [here](webhooks.md#subscription-request-example).

  > **Note:** This action might fail, because the authorization checks performed by the system might deny the app or the user access to the resource. It might be necessary for the app to obtain a new access token from the user to successfully reauthorize a subscription. You can retry these actions later, at any time; for example, when the conditions of access have changed. Any resource changes in the time period from when the lifecycle notification was sent, to when the app recreates the subscription successfully, will be lost. The app will need to fetch those changes on its own.

5. After creating the new subscription, sync any missing resource data from the last known time you received a change notification for this resource; for example: `GET https://graph.microsoft.com/v1.0/users/{id}/messages?$filter=createdDateTime+ge+{LastTimeNotificationWasReceived}`

## Responding to missed notifications

These signals inform you that some change notifications might not have been delivered. You should decide if you ignore or handle these signals.

### Notification example

```json
{
  "value": [
    {
      "subscriptionId":"<subscription_guid>",
      "subscriptionExpirationDateTime":"2019-03-20T11:00:00.0000000Z",
      "tenantId": "<tenant_guid>",
      "clientState":"<secretClientState>",
      "lifecycleEvent": "missed"
    }
  ]
}
```

A few things to note about this type of notification:
- The `"lifecycleEvent": "missed"` field designates this as a signal about missed change notifications. Other types of lifecycle notifications are also possible, and new ones will be introduced in the future.
- The lifecycle notification does not contain any information about a specific resource, because it is not related to a resource change, but to the subscription state change.
- Similar to change notifications, lifecycle notifications might be batched together (in the **value** array), each with a possibly different **lifecycleEvent** value. Process each lifecycle notification in the batch accordingly.

> **Note:** for a full description of the data sent when change notifications are delivered, see [changeNotificationCollection](/graph/api/resources/changenotificationcollection).

### Actions to take

1. [Acknowledge](webhooks.md#change-notifications) the receipt of the lifecycle notification, by responding to the POST call with `202 - Accepted`.
    - If you ignore these signals, do nothing else. Otherwise:
2. [Validate](webhooks.md#change-notifications) the authenticity of the lifecycle notification.
3. Perform a full data resync of the resource to identify the changes that were not delivered as notifications. 


## Future-proof the code handling lifecycle notifications

In the future, Microsoft Graph will add more types of subscription lifecycle notifications. They will be posted to the same endpoint: **lifecycleNotificationUrl**, but they will have a different value under **lifecycleEvent** and might contain a slightly different schema and properties, specific to the scenario for which they will be issued.

You should implement your code in a future-proof way so it does not break when Microsoft Graph introduces new types of lifecycle notifications. We recommend the following approach:

1. Explicitly identify each lifecycle notification as an event that you support, using the **lifecycleEvent** property. For example, look for the `"lifecycleEvent": "subscriptionRemoved"` property to identify a specific event, and handle it.

2. Watch for announcements of lifecycle notifications for new scenarions. There might be more types of lifecycle notifications in the future.

3. In your app, ignore any lifecycle notification that the app does not recognize, and log them to gain awareness.

4. At your discretion, look up the related documentation for new lifecycle notifications and implement support for them as appropriate.

## See also

- [Subscription resource type](/graph/api/resources/subscription?view=graph-rest-1.0)
- [Get subscription](/graph/api/subscription-get?view=graph-rest-1.0)
- [Create subscription](/graph/api/subscription-post-subscriptions?view=graph-rest-1.0)
- [Delete subscription](/graph/api/subscription-delete?view=graph-rest-1.0)
- [Update subscription](/graph/api/subscription-update?view=graph-rest-1.0)
