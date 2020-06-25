---
title: "Create relations"
description: "Create a new relations object."
author: "**TODO: Provide Github Name. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
localization_priority: Normal
ms.prod: "**TODO: Add MS prod. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
doc_type: apiPageType
---

# Create relations
Namespace: microsoft.graph.termStore

Create a new relations object.

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
POST /termStore/groups/{groupId}/sets/{setId}/relations
POST /termStore/groups/{groupId}/sets/{setId}/terms/{termId}/relations
POST /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/relations
POST /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/terms/{termId}/relations
```

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|
|Content-Type|application/json. Required.|

## Request body
In the request body, supply a JSON representation of the [relation](../resources/termstore-relation.md) object.

The following table shows the properties that are required when you create the [relation](../resources/termstore-relation.md).

|Property|Type|Description|
|:---|:---|:---|
|id|String|**TODO: Add Description** Inherited from [entity](../resources/termstore-entity.md)|
|relationship|relationType|**TODO: Add Description**. Possible values are: `pin`, `reuse`.|



## Response

If successful, this method returns a `201 Created` response code and a [relation](../resources/termstore-relation.md) object in the response body.

## Examples

### Request
<!-- {
  "blockType": "request",
  "name": "create_relation_from_"
}
-->
``` http
POST https://graph.microsoft.com/beta/termStore/groups/{groupId}/sets/{setId}/relations
Content-Type: application/json
Content-length: 89

{
  "@odata.type": "#microsoft.graph.termStore.relation",
  "relationship": "String"
}
```


### Response
**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.termstore.relation"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json
{
  "@odata.type": "#microsoft.graph.termStore.relation",
  "id": "052c749c-749c-052c-9c74-2c059c742c05",
  "relationship": "String"
}
```

