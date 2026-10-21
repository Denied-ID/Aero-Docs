# PointLight

A light that shines in every direction from a point.

Parent a `PointLight` to a part and the part lights its surroundings from its center. It has the five settings every light has and nothing more.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| Color | Color3 | The light color, clamped from 0 to 1 per channel. |
| Brightness | number | Intensity, clamped from 0 to 100. Default 2. |
| Range | number | Reach in studs, clamped from 0 to 512. Default 16. 0 means no limit. |
| Shadows | boolean | Whether the light casts shadows. |
| Enabled | boolean | Whether the light shines. |

## Members

PointLight has no methods of its own. It also has the shared Instance members; see [Instance](../globals/instance.md).

## Example

```lua
local lamp = Instance.new("Part")
lamp.Size = Vector3.new(1, 1, 1)
lamp.Position = Vector3.new(0, 12, 0)
lamp.Anchored = true
lamp.Parent = workspace

local light = Instance.new("PointLight", lamp)
light.Color = Color3.fromRGB(255, 200, 120)
light.Brightness = 3
light.Range = 24
light.Shadows = true
```

## See also

- [SpotLight](spotlight.md): a cone instead of every direction.
- [SurfaceLight](surfacelight.md): light from one face of a part.
- [Part](part.md): the usual parent.
- [API Reference](../api/index.md)
