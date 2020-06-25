---
title: "List sets"
description: "Get the sets from the sets navigation property."
author: "**TODO: Provide Github Name. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
localization_priority: Normal
ms.prod: "**TODO: Add MS prod. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
doc_type: apiPageType
---

# List sets
Namespace: microsoft.graph.termStore

Get the sets from the sets navigation property.

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
GET /termStore/sets
GET /termStores/{termStoresId}/sets
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

If successful, this method returns a `200 OK` response code and a collection of [set](../resources/set.md) objects in the response body.

## Examples

### Request
<!-- {
  "blockType": "request",
  "name": "get_set"
}
-->
``` http
GET https://graph.microsoft.com/beta/termStore/sets
```


### Response
**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "collection(microsoft.graph.termstore.set)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json
{
  "value": [
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
  ]
}
```

