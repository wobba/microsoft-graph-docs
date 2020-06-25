---
title: "store resource type"
description: "**TODO: Add Description**"
author: "**TODO: Provide Github Name. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
localization_priority: Normal
ms.prod: "**TODO: Add MS prod. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
doc_type: resourcePageType
---

# store resource type

Namespace: microsoft.graph.termStore

**TODO: Add Description**


Inherits from [entity](../resources/entity.md).

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List stores](../api/store-list.md)|[store](../resources/termstore-store.md) collection|Get a list of the [store](../resources/store.md) objects and their properties.|
|[Create store](../api/termstore-store-post-termstores.md)|[store](../resources/termstore-store.md)|Create a new [store](../resources/termstore-store.md) object.|
|[Get store](../api/termstore-store-get.md)|[store](../resources/termstore-store.md)|Read the properties and relationships of a [store](../resources/termstore-store.md) object.|
|[Update store](../api/termstore-store-update.md)|[store](../resources/termstore-store.md)|Update the properties of a [store](../resources/termstore-store.md) object.|
|[Delete store](../api/termstore-store-delete.md)|None|Deletes a [store](../resources/termstore-store.md) object.|
|[List groups](../api/termstore-store-list-groups.md)|[group](../resources/termstore-group.md) collection|Get the groups from the groups navigation property.|
|[Create groups](../api/termstore-store-post-groups.md)|[group](../resources/termstore-group.md)|Create a new groups object.|
|[Get groups](../api/termstore-store-get-group.md)|[group](../resources/termstore-group.md)|Read the properties and relationships of a [group](../resources/group.md) object.|
|[Update groups](../api/termstore-store-update-groups.md)|[group](../resources/termstore-group.md)|Update the properties of a groups object.|
|[Delete groups](../api/termstore-store-delete-groups.md)|None|Delete a [group](../resources/termstore-group.md) object.|
|[List sets](../api/termstore-store-list-sets.md)|[set](../resources/termstore-set.md) collection|Get the sets from the sets navigation property.|
|[Create sets](../api/termstore-store-post-sets.md)|[set](../resources/termstore-set.md)|Create a new sets object.|
|[Get sets](../api/termstore-store-get-set.md)|[set](../resources/termstore-set.md)|Read the properties and relationships of a [set](../resources/set.md) object.|
|[Update sets](../api/termstore-store-update-sets.md)|[set](../resources/termstore-set.md)|Update the properties of a sets object.|
|[Delete sets](../api/termstore-store-delete-sets.md)|None|Delete a [set](../resources/termstore-set.md) object.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|defaultLanguageTag|String|**TODO: Add Description**|
|id|String|**TODO: Add Description** Inherited from [entity](../resources/termstore-entity.md)|
|languageTags|String collection|**TODO: Add Description**|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|groups|[group](../resources/termstore-group.md) collection|**TODO: Add Description**|
|sets|[set](../resources/termstore-set.md) collection|**TODO: Add Description**|

## JSON representation
The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.termStore.store",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.termStore.store",
  "id": "String (identifier)",
  "defaultLanguageTag": "String",
  "languageTags": [
    "String"
  ]
}
```

