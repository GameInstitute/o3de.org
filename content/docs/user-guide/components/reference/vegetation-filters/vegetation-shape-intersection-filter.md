---
title: Vegetation Shape Intersection Filter Component
linktitle: Vegetation Shape Intersection Filter
description: Use the Vegetation Shape Intersection Filter component to contain vegetation instance placement within the bounds of a shape in your Open 3D Engine (O3DE) level.
weight: 400
---

Add the **Vegetation Shape Intersection Filter** component to contain vegetation or blocker instance placement within the bounds of a **Shape** component.

## Provider

[Vegetation Gem](/docs/user-guide/gems/reference/environment/vegetation/)

## Dependencies

Add one of the following required components when using the Vegetation Shape Intersection Filter component:
- [Vegetation Layer Blender](./../vegetation/vegetation-layer-blender)
- [Vegetation Layer Blocker](./../vegetation/vegetation-layer-blocker)
- [Vegetation Layer Blocker (Mesh)](./../vegetation/vegetation-layer-blocker-mesh)
- [Vegetation Layer Spawner](./../vegetation/layer-spawner)

## Vegetation Shape Intersection Filter properties

![Vegetation Shape Intersection Filter component properties](/images/user-guide/components/reference/vegetation-filters/vegetation-shape-intersection-filter-component.png)

| 属性 | 说明 | 值 | 默认值 |
|-|-|-|-|
| **Filter Stage** | Defines if filters are applied before or after modifiers. | `PreProcess`, `PostProcess`, or `Default` | `Default` |
| **Shape Entity Id** | Selects an entity with a shape component. Instances are placed only within the bounds of the shape. | EntityId | None |

## ShapeIntersectionFilterRequestBus

Use the following request functions with the `ShapeIntersectionFilterRequestBus` EBus interface to communicate with Vegetation Shape Intersection Filter components in your game.

| Method Name | Description | Parameter | Return | Scriptable |
|-|-|-|-|-|
| `GetShapeEntityId` | Returns the **Shape Entity Id** property of a Shape Intersection Filter. | None | EntityId | Yes |
| `SetShapeEntityId` | Sets the **Shape Entity Id** property of a Shape Intersection Filter.  | EntityId | None | Yes |
