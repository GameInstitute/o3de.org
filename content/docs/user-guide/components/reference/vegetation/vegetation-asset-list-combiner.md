---
linkTitle: Vegetation Asset List Combiner
title: Vegetation Asset List Combiner Component
description: Combine multiple vegetation asset lists with the Vegetation Asset List Combiner component in Open 3D Engine (O3DE).
weight: 200
---

Use the **Vegetation Asset List Combiner** component to group multiple vegetation asset lists.  This component allows you to keep vegetation asset lists small, focused, and reusable; combine only the asset lists you need for a vegetation layer.

## Provider

[Vegetation Gem](/docs/user-guide/gems/reference/environment/vegetation/)

## Vegetation Asset List Combiner properties

![Vegetation Asset List Combiner component properties](/images/user-guide/components/reference/vegetation/vegetation-asset-list-combiner-component.png)

| 属性 | 说明 | 值 | 默认值 |
|-|-|-|-|
| **Descriptor Providers** | An array of vegetation asset lists that will be combined by this component. | Array: Vegetation Asset List | None |

## DescriptorListCombinerRequestBus

Use the following request functions with the `DescriptorListCombinerRequestBus` EBus interface to communicate with Vegetation Asset List Combiner components in your game.

| Method Name | Description | Parameter | Return | Scriptable |
|-|-|-|-|-|
| `AddDescriptorEntityId` | Adds an entity with a **Vegetation Asset List** component to an array of **Descriptor Providers**. | EntityId | None | Yes |
| `GetDescriptorEntityId` | Returns the EntityId of a **Descriptor Provider** at the specified index. | Descriptor Providers Index: Integer | EntityId | Yes |
| `GetNumDescriptors` | Returns the number of entries in a **Descriptor Providers** array. | None | Count: Integer | Yes |
| `RemoveDescriptorEntityId` | Removes an entity from an array of **Descriptor Providers**. | EntityId | None | Yes |
| `SetDescriptorEntityId` | Updates the EntityId of an entry in an array of **Descriptor Providers**. | Descriptor Providers Index: Integer, EntityId | None | Yes |
