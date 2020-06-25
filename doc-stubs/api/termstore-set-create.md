---
title: "Create set"
description: "Create a new set object."
author: "**TODO: Provide Github Name. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
localization_priority: Normal
ms.prod: "**TODO: Add MS prod. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
doc_type: apiPageType
---

# Create set
Namespace: microsoft.graph.termStore

Create a new [set](../resources/termstore-set.md) object.

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
POST /termStore/sets
POST /termStores/{termStoresId}/sets
```

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|
|Content-Type|application/json. Required.|

## Request body
In the request body, supply a JSON representation of the [set](../resources/termstore-set.md) object.

The following table shows the properties that are required when you create the [set](../resources/termstore-set.md).

|Property|Type|Description|
|:---|:---|:---|
|id|String|**TODO: Add Description** Inherited from [entity](../resources/termstore-entity.md)|
|localizedNames|[localizedName](../resources/termstore-localizedname.md) collection|**TODO: Add Description**|
|description|String|**TODO: Add Description**|
|createdDateTime|DateTimeOffset|**TODO: Add Description**|
|properties|[keyValue](../resources/termstore-intune-keyvalue.md) collection|**TODO: Add Description**|



## Response

If successful, this method returns a `201 Created` response code and a [set](../resources/termstore-set.md) object in the response body.

## Examples

### Request
<!-- {
  "blockType": "request",
  "name": "create_set_from_"
}
-->
``` http
POST https://graph.microsoft.com/beta/termStore/sets
Content-Type: application/json
Content-length: 288

{
  "@odata.type": "#microsoft.graph.termStore.set",
  "localizedNames": [
    {
      "@odata.type": "microsoft.graph.termStore.localizedName"
    }
  ],
  "description": "String",
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
  "@odata.type": "microsoft.graph.termstore.set"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json
{
  "@odata.type": "#microsoft.graph.termStore.set",
  "id": "3607e9f9-e9f9-3607-f9e9-0736f9e90736",
  "localizedNames": [
    {
      "@odata.type": "microsoft.graph.termStore.localizedName"
    }
  ],
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "properties": [
    {
      "@odata.type": "microsoft.graph.termStore.keyValue"
    }
  ]
}
```

