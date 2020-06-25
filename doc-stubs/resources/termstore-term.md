---
title: "term resource type"
description: "**TODO: Add Description**"
author: "**TODO: Provide Github Name. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
localization_priority: Normal
ms.prod: "**TODO: Add MS prod. See [topic-level metadata reference](https://msgo.azurewebsites.net/add/document/guidelines/metadata.html#topic-level-metadata)**"
doc_type: resourcePageType
---

# term resource type

Namespace: microsoft.graph.termStore

**TODO: Add Description**


Inherits from [entity](../resources/entity.md).

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List children](../api/termstore-set-list-children.md)|[term](../resources/termstore-term.md) collection|Get the terms from the children navigation property.|
|[Create children](../api/termstore-set-post-children.md)|[term](../resources/termstore-term.md)|Create a new children object.|
|[Update children](../api/termstore-set-update-children.md)|[term](../resources/termstore-term.md)|Update the properties of a children object.|
|[Get children](../api/termstore-set-get-term.md)|[term](../resources/termstore-term.md)|Read the properties and relationships of a [term](../resources/term.md) object.|
|[Delete children](../api/termstore-set-delete-children.md)|None|Delete a [term](../resources/termstore-term.md) object.|
|[List terms](../api/term-list.md)|[term](../resources/termstore-term.md) collection|Get a list of the [term](../resources/term.md) objects and their properties.|
|[Create term](../api/termstore-term-create.md)|[term](../resources/termstore-term.md)|Create a new [term](../resources/termstore-term.md) object.|
|[Get term](../api/termstore-term-get.md)|[term](../resources/termstore-term.md)|Read the properties and relationships of a [term](../resources/termstore-term.md) object.|
|[Update term](../api/termstore-term-update.md)|[term](../resources/termstore-term.md)|Update the properties of a [term](../resources/termstore-term.md) object.|
|[Delete term](../api/termstore-term-delete.md)|None|Deletes a [term](../resources/termstore-term.md) object.|
|[List children](../api/termstore-term-list-children.md)|[term](../resources/termstore-term.md) collection|Get the terms from the children navigation property.|
|[Create children](../api/termstore-term-post-children.md)|[term](../resources/termstore-term.md)|Create a new children object.|
|[Get children](../api/termstore-term-get-term.md)|[term](../resources/termstore-term.md)|Read the properties and relationships of a [term](../resources/term.md) object.|
|[Update children](../api/termstore-term-update-children.md)|[term](../resources/termstore-term.md)|Update the properties of a children object.|
|[Delete children](../api/termstore-term-delete-children.md)|None|Delete a [term](../resources/termstore-term.md) object.|
|[List relations](../api/termstore-term-list-relations.md)|[relation](../resources/termstore-relation.md) collection|Get the relations from the relations navigation property.|
|[Create relations](../api/termstore-term-post-relations.md)|[relation](../resources/termstore-relation.md)|Create a new relations object.|
|[Get relations](../api/termstore-term-get-relation.md)|[relation](../resources/termstore-relation.md)|Read the properties and relationships of a [relation](../resources/relation.md) object.|
|[Update relations](../api/termstore-term-update-relations.md)|[relation](../resources/termstore-relation.md)|Update the properties of a relations object.|
|[Delete relations](../api/termstore-term-delete-relations.md)|None|Delete a [relation](../resources/termstore-relation.md) object.|
|[List set](../api/termstore-term-list-set.md)|[set](../resources/termstore-set.md) collection|Get the sets from the set navigation property.|
|[Add set](../api/termstore-term-post-set.md)|[set](../resources/termstore-set.md)|Add set by posting to the set collection.|
|[Remove set](../api/termstore-term-delete-set.md)|None|Remove a [set](../resources/termstore-set.md) object.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|**TODO: Add Description**|
|descriptions|[localizedDescription](../resources/termstore-localizeddescription.md) collection|**TODO: Add Description**|
|id|String|**TODO: Add Description** Inherited from [entity](../resources/termstore-entity.md)|
|labels|[localizedLabel](../resources/termstore-localizedlabel.md) collection|**TODO: Add Description**|
|lastModifiedDateTime|DateTimeOffset|**TODO: Add Description**|
|properties|[keyValue](../resources/termstore-intune-keyvalue.md) collection|**TODO: Add Description**|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|children|[term](../resources/termstore-term.md) collection|**TODO: Add Description**|
|relations|[relation](../resources/termstore-relation.md) collection|**TODO: Add Description**|
|set|[set](../resources/termstore-set.md)|**TODO: Add Description**|

## JSON representation
The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.termStore.term",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.termStore.term",
  "id": "String (identifier)",
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

