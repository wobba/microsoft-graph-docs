---
title: "set resource type"
description: "**TODO: Add Description**"
author: "**TODO: Provide Github Name. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
localization_priority: Normal
ms.prod: "**TODO: Add MS prod. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
doc_type: resourcePageType
---

# set resource type

Namespace: microsoft.graph.termStore

**TODO: Add Description**


Inherits from [entity](../resources/entity.md).

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List sets](../api/set-list.md)|[set](../resources/termstore-set.md) collection|Get a list of the [set](../resources/set.md) objects and their properties.|
|[Create set](../api/termstore-set-create.md)|[set](../resources/termstore-set.md)|Create a new [set](../resources/termstore-set.md) object.|
|[Get set](../api/termstore-set-get.md)|[set](../resources/termstore-set.md)|Read the properties and relationships of a [set](../resources/termstore-set.md) object.|
|[Update set](../api/termstore-set-update.md)|[set](../resources/termstore-set.md)|Update the properties of a [set](../resources/termstore-set.md) object.|
|[Delete set](../api/termstore-set-delete.md)|None|Deletes a [set](../resources/termstore-set.md) object.|
|[List children](../api/termstore-set-list-children.md)|[term](../resources/termstore-term.md) collection|Get the terms from the children navigation property.|
|[Create children](../api/termstore-set-post-children.md)|[term](../resources/termstore-term.md)|Create a new children object.|
|[Get children](../api/termstore-set-get-term.md)|[term](../resources/termstore-term.md)|Read the properties and relationships of a [term](../resources/term.md) object.|
|[Update children](../api/termstore-set-update-children.md)|[term](../resources/termstore-term.md)|Update the properties of a children object.|
|[Delete children](../api/termstore-set-delete-children.md)|None|Delete a [term](../resources/termstore-term.md) object.|
|[List parentGroup](../api/termstore-set-list-parentgroup.md)|[group](../resources/termstore-group.md) collection|Get the groups from the parentGroup navigation property.|
|[Create parentGroup](../api/termstore-set-post-parentgroup.md)|[group](../resources/termstore-group.md)|Create a new parentGroup object.|
|[Get parentGroup](../api/termstore-set-get-group.md)|[group](../resources/termstore-group.md)|Read the properties and relationships of a [group](../resources/group.md) object.|
|[Update parentGroup](../api/termstore-set-update-parentgroup.md)|[group](../resources/termstore-group.md)|Update the properties of a parentGroup object.|
|[Delete parentGroup](../api/termstore-set-delete-parentgroup.md)|None|Delete a [group](../resources/termstore-group.md) object.|
|[List relations](../api/termstore-set-list-relations.md)|[relation](../resources/termstore-relation.md) collection|Get the relations from the relations navigation property.|
|[Create relations](../api/termstore-set-post-relations.md)|[relation](../resources/termstore-relation.md)|Create a new relations object.|
|[Get relations](../api/termstore-set-get-relation.md)|[relation](../resources/termstore-relation.md)|Read the properties and relationships of a [relation](../resources/relation.md) object.|
|[Update relations](../api/termstore-set-update-relations.md)|[relation](../resources/termstore-relation.md)|Update the properties of a relations object.|
|[Delete relations](../api/termstore-set-delete-relations.md)|None|Delete a [relation](../resources/termstore-relation.md) object.|
|[List terms](../api/termstore-set-list-terms.md)|[term](../resources/termstore-term.md) collection|Get the terms from the terms navigation property.|
|[Create terms](../api/termstore-set-post-terms.md)|[term](../resources/termstore-term.md)|Create a new terms object.|
|[Get terms](../api/termstore-set-get-term.md)|[term](../resources/termstore-term.md)|Read the properties and relationships of a [term](../resources/term.md) object.|
|[Update terms](../api/termstore-set-update-terms.md)|[term](../resources/termstore-term.md)|Update the properties of a terms object.|
|[Delete terms](../api/termstore-set-delete-terms.md)|None|Delete a [term](../resources/termstore-term.md) object.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|**TODO: Add Description**|
|description|String|**TODO: Add Description**|
|id|String|**TODO: Add Description** Inherited from [entity](../resources/termstore-entity.md)|
|localizedNames|[localizedName](../resources/termstore-localizedname.md) collection|**TODO: Add Description**|
|properties|[keyValue](../resources/termstore-intune-keyvalue.md) collection|**TODO: Add Description**|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|children|[term](../resources/termstore-term.md) collection|**TODO: Add Description**|
|parentGroup|[group](../resources/termstore-group.md)|**TODO: Add Description**|
|relations|[relation](../resources/termstore-relation.md) collection|**TODO: Add Description**|
|terms|[term](../resources/termstore-term.md) collection|**TODO: Add Description**|

## JSON representation
The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.termStore.set",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.termStore.set",
  "id": "String (identifier)",
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

