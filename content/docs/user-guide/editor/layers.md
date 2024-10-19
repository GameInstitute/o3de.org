---
description: ' 使用 Open 3D Engine 中的实体大纲管理器管理实体。 '
title: 使用图层
draft: true
---

使用 O3DE 图层系统将关卡数据组织成离散文件。图层系统可以分割关卡内容，这样开发团队的成员就可以异步处理关卡的不同方面。

图层是标准的 O3DE 实体，带有一个特殊的编辑器专用图层组件。在游戏中，该组件在层次结构中显示为一个空实体。当您导出游戏时，您设计的行为将保持不变，关卡中的所有实体都会添加到导出数据中。

**主题**
+ [创建图层](#creating-layers)
+ [修改图层](#modifying-layers)
+ [将实体添加到图层](#adding-entities-to-layers)
+ [保存图层](#saving-layers)
+ [恢复图层](#recovering-layers)
+ [图层相关组件](#layer-specific-components)

## 创建图层

创建图层后，您可以向该图层添加实体。这可以帮助您组织游戏中的内容。例如，您可以为所有角色实体创建一个图层，为植被创建另一个图层。

**To create a layer**

1. In O3DE Editor, choose **Tools**, **Entity Outliner**.

1. In the **Entity Outliner**, right-click and choose **Create layer**.

![Right-click in the Entity Outliner and choose Create layer.](/images/user-guide/component/entity_system/creating-layers.png)

1. With the layer selected in the **Entity Outliner**, you can modify its properties in the **Entity Inspector**.

![Right-click in the Entity Outliner and choose Create layer.](/images/user-guide/component/entity_system/modifying-layers-inspector.png)
****


## Modifying a Layer 

After you create a layer, you can modify it by adding entities, reorganizing its hierarchy, adding nested layers, renaming the layer, and so on.

**To show a layer's context menu**

1. In the **Entity Outliner**, right-click the layer.

1. You can do the following in the context menu.

   Actions highlighted in yellow affect the selected layer. The other options are standard context menu actions that don't affect the selected layer.

   ![Right-click in the Entity Outliner and choose Create layer.](/images/user-guide/component/entity_system/modifying-layers.png)

   The following options in the context menu perform actions on the selected layer.
****


### Layer Hierarchies 

You can nest layers within other layers. This is useful if you want to organize the enitites in your level. This behavior is similar to creating hierarchies for parent and child entities.

![Right-click in the Entity Outliner and choose Create layer.](/images/user-guide/component/entity_system/layer-hierarchies.png)

{{< note >}}
You can't make a layer a child of a non-layer entity and you can't save a layer in a slice.
{{< /note >}}

You can nest layers to break up your level into smaller, more workable sections. If you are creating a large level, for example, you might have a single vegetation layer. If you have just one vegetation layer, then only one environment artist could edit this layer at a time. To allow multiple artists to work on the vegetation layer at once, you can nest other layers within the vegetation layer and assign each nested layer to different artists. This helps build a well-organized hierarchy to keep the game's structure efficient.

## Adding Entities to a Layer 

Layers can contain freestanding (non-slice) entities and slices.

**To add an entity to a layer**
+ In the **Entity Outliner**, do one of the following:

  1. Select and drag an entity to a layer or within the layer hierarchy.

  1. Right-click an entity, pause on **Assign to layer**, and then select a layer.

## Saving a Layer 

The component entity system saves references to layers and their hierarchies in the level data. When you add or remove a layer from your level, you must save your level before making more changes. If you don't save your level, layers and their contents will not load correctly the next time you open the level.

O3DE layers are saved as `.layer` files in the `level_name/layers` directory. The layer's filename is saved as `layer_name.layer`. If a layer is nested within another layer, then the parent layer name is prepended to the layer filename.

When a layer contains unsaved changes, an asterisk (\*) appears next to the layer name. After you save the level or the layer, the asterisk is removed.

![Right-click in the Entity Outliner and choose Create layer.](/images/shared/shared-saving-layers.png)

Layer names at the same hierarchy level must be unique. Layers at the same hierarchy level with duplicate names display a warning (**\!**) and can't be saved until you rename them.

![Right-click in the Entity Outliner and choose Create layer.](/images/user-guide/component/entity_system/saving-layers-duplicate.png)

**To save your level and all layers**
+ In O3DE Editor, choose **File**, **Save** or press **Ctrl+S**.

**To save specific layers only**

1. Select the layer you want to save, or press **CTRL** and then select multiple layers.

1. In the **Entity Outliner**, right-click the selection and choose **Save**.

## Recovering a Layer 

If you delete a layer from a level in O3DE Editor, you can reimport it.

**To reimport a deleted layer**

1. Using a file browser, copy onto your desktop the layer file for the layer that you want to recover, such as `level_name\layer\layer_name.layer`.

1. In O3DE Editor, create a new layer in your level and enter the same name as the deleted layer.

1. Save the level and close O3DE Editor.

1. Copy the layer file from your desktop into O3DE's layer directory, such as `level_name/layers`.

1. Rename the copied layer file to match and replace the layer that you created in O3DE Editor.

1. Reopen the level. The newly created layer now references the recovered layer information.

## Layer-Specific Components 

A layer is simply an entity with special rules. As such, you can add layer-specific components to layers. By default, O3DE doesn't contain any layer-specific components, but you can create your own, such as special layer components for streaming or tags.

Any given component can appear in only one context menu. By default, O3DE has the **Game**, **System**, and **Layer** contexts for components.

You can test creating a layer-specific component by editing the **Comment** component.

**To modify the Comment component**

1. In a text editor, open the `EditorCommentComponent.cpp` file.

1. Change the `AZ_CRC` attribute to **Layer** and delete the CRC value.

1. Save the file.

1. In O3DE Editor, add the **Comment** component to a layer.
