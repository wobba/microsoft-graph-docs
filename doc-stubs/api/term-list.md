---
title: "List terms"
description: "Get a list of the term objects and their properties."
author: "**TODO: Provide Github Name. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
localization_priority: Normal
ms.prod: "**TODO: Add MS prod. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
doc_type: apiPageType
---

# List terms
Namespace: microsoft.graph.termStore

Get a list of the [term](../resources/term.md) objects and their properties.

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
GET /termStore/groups/{groupId}/sets/{setId}/terms
GET /termStore/groups/{groupId}/sets/{setId}/children
GET /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/terms
GET /termStore/groups/{groupId}/sets/{setId}/terms/{termId}/children
GET /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/children
GET /termStores/{termStoresId}/groups/{groupId}/sets/{setId}/terms/{termId}/children
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

If successful, this method returns a `200 OK` response code and a collection of [term](../resources/term.md) objects in the response body.

## Examples

### Request
<!-- {
  "blockType": "request",
  "name": "get_term"
}
-->
``` http
GET https://graph.microsoft.com/beta/termStore/groups/{groupId}/sets/{setId}/terms
```


### Response
**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "collection(microsoft.graph.termstore.term)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json
{
  "value": [
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
  ]
}
```

