---
title: "Create terms"
description: "Create a new terms object."
author: "**TODO: Provide Github Name. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
localization_priority: Normal
ms.prod: "**TODO: Add MS prod. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
doc_type: apiPageType
---

# Create terms
Namespace: microsoft.graph.termStore

Create a new terms object.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/concepts/permissions-reference.md).

|Permission type|Permissions (from most to least privileged)|
|:---|:---|
|Delegated (work or school account)|**TODO: Provide applicable permissions.**|
|Delegated (personal Microsoft account)|**TODO: Provide applicable permissions.**|
|Application|**TODO: Provide applicable permissions.**|

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /termStore/groups/{groupId}/sets/{setId}/terms
POST /termStore/groups/{groupId}/sets/{setId}/children
POST /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/terms
POST /termStore/groups/{groupId}/sets/{setId}/terms/{termId}/children
POST /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/children
POST /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/terms/{termId}/children
```

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|
|Content-Type|application/json. Required.|

## Request body
In the request body, supply a JSON representation of the [term](../resources/termstore-term.md) object.

The following table shows the properties that are required when you create the [term](../resources/termstore-term.md).

|Property|Type|Description|
|:---|:---|:---|
|id|String|**TODO: Add Description** Inherited from [entity](../resources/termstore-entity.md)|
|labels|[localizedLabel](../resources/termstore-localizedlabel.md) collection|**TODO: Add Description**|
|createdDateTime|DateTimeOffset|**TODO: Add Description**|
|lastModifiedDateTime|DateTimeOffset|**TODO: Add Description**|
|descriptions|[localizedDescription](../resources/termstore-localizeddescription.md) collection|**TODO: Add Description**|
|properties|[keyValue](../resources/termstore-intune-keyvalue.md) collection|**TODO: Add Description**|



## Response

If successful, this method returns a `201 Created` response code and a [term](../resources/termstore-term.md) object in the response body.

## Examples

### Request
<!-- {
  "blockType": "request",
  "name": "create_term_from_"
}
-->
``` http
POST https://graph.microsoft.com/beta/termStore/groups/{groupId}/sets/{setId}/terms
Content-Type: application/json
Content-length: 366

{
  "@odata.type": "#microsoft.graph.termStore.term",
  "labels": [
    {
      "@odata.type": "microsoft.graph.termStore.localizedLabel"
    }
  ],
  "descriptions": [
    {
      "@odata.type": "microsoft.graph.termStore.localizedDescription"
    }
  ],
  "properties": [
    {
      "@odata.type": "microsoft.graph.termStore.keyValue"
    }
  ]
}
```


### Response
**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.termstore.term"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json
{
  "@odata.type": "#microsoft.graph.termStore.term",
  "id": "81be9856-9856-81be-5698-be815698be81",
  "labels": [
    {
      "@odata.type": "microsoft.graph.termStore.localizedLabel"
    }
  ],
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "descriptions": [
    {
      "@odata.type": "microsoft.graph.termStore.localizedDescription"
    }
  ],
  "properties": [
    {
      "@odata.type": "microsoft.graph.termStore.keyValue"
    }
  ]
}
```

