# Render Pipeline Properties

Render pipeline passes and extractors often expose properties that affect how a scene is rendered, for example the tonemapping curve or the strength of an effect. These values are normally fixed on the [render pipeline](render-pipeline-overview.md) asset, but they can also be *driven dynamically* at runtime, without any C++ or script code, using [blackboards](../../misc/blackboards.md).

## Blackboard-Driven Properties

An `ezView` looks for blackboard entries whose key is structured as `<PassName>.<PropertyName>` or `<ExtractorName>.<PropertyName>`. Whenever such an entry exists, and its name matches a render pass or extractor of the view's active render pipeline as well as one of its member properties, that property is overwritten with the entry's value every frame.

Two blackboards are checked, in this order of priority:

1. **World Blackboard:** Every [world](../../misc/blackboards.md) has its own blackboard. Use this for values that should apply to every camera looking at that world, for example a global fog setting.
2. **View Blackboard:** An optional, camera-specific blackboard, configured through the `BlackboardName` property on the [camera component](../camera-component.md). Entries here take priority over entries with the same key from the world blackboard. This is useful for camera-specific overrides, for instance on a [render to texture (TODO)](../render-to-texture/render-to-texture.md) camera that should not be affected by the world's blackboard.

To find out which `<PassName>.<PropertyName>` keys are available, inspect the render passes and extractors of the [render pipeline](render-pipeline-overview.md) that is in use.

## Populating the Blackboard

Rather than writing to the blackboard from code, the recommended approach is to use a [Volume Sampler Component](../../gameplay/volume-sampler-component.md) with its `WriteToBlackboard` property enabled. It samples values out of [volume components](../../effects/post-processing/volume-components.md) at the camera's position and writes them into the target blackboard using the matching keys, so that render pipeline properties (such as color grading or exposure) change smoothly depending on which area of a level the camera is in.

## See Also

* [Volume Components](../../effects/post-processing/volume-components.md)
* [Volume Sampler Component](../../gameplay/volume-sampler-component.md)
* [Blackboards](../../misc/blackboards.md)
* [Camera Component](../camera-component.md)
* [Fog](../../effects/fog.md)
