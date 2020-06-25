---
title: "List relations"
description: "Get a list of the relation objects and their properties."
author: "**TODO: Provide Github Name. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
localization_priority: Normal
ms.prod: "**TODO: Add MS prod. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
doc_type: apiPageType
---

# List relations
Namespace: microsoft.graph.termStore

Get a list of the [relation](../resources/relation.md) objects and their properties.

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
GET /termStore/groups/{groupId}/sets/{setId}/relations
GET /termStore/groups/{groupId}/sets/{setId}/terms/{termId}/relations
GET /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/relations
GET /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/terms/{termId}/relations
```

## Optional query parameters
This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|

## Request body
Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [relation](../resources/relation.md) objects in the response body.

## Examples

### Request
<!-- {
  "blockType": "request",
  "name": "get_relation"
}
-->
``` http
GET https://graph.microsoft.com/beta/termStore/groups/{groupId}/sets/{setId}/relations
```


### Response
**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "collection(microsoft.graph.termstore.relation)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json
{
  "value": [
    {
      "@odata.type": "#microsoft.graph.termStore.relation",
      "id": "052c749c-749c-052c-9c74-2c059c742c05",
      "relationship": "String"
    }
  ]
}
```

