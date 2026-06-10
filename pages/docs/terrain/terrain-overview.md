# Terrain and Vegetation

![Terrain overview](media/terrain-overview.jpg)

## Terrain

ezEngine includes a brush-based [terrain system](terrain-plugin-overview.md) for creating heightfield and voxel terrain. Terrain is shaped by placing brush objects in the scene. The system is non-destructive, so brushes can be repositioned or removed at any time.

## Vegetation

Vegetation can be created with standard meshes. Using custom [visual shaders](../materials/visual-shaders.md), a basic per-vertex wind animation can be applied.

Additionally, ezEngine has built in support for [Kraut](kraut-overview.md), a system for procedurally generating tree meshes.

Finally, there is a [procedural placement system](procedural/procedural-object-placement.md) to scatter objects, typically plants, around the current player position.

## See Also

* [Terrain System](terrain-plugin-overview.md)
* [Procedural Object Placement](procedural/procedural-object-placement.md)
