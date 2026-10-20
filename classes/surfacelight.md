# SurfaceLight

A cone of light from one face of a part.

Parent a `SurfaceLight` to a part and it shines out of the face you name. It has the settings every light has, plus the cone angle and the face.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| Color | Color3 | The light color, clamped from 0 to 1 per channel. |
| Brightness | number | Intensity, clamped from 0 to 100. Default 2. |
| Range | number | Reach in studs, clamped from 0 to 512. Default 16. 0 means no limit. |
| Shadows | boolean | Whether the light casts shadows. |
| Enabled | boolean | Whether the light shines. |
| Angle | number | The full cone angle in degrees, clamped from 0 to 180. Default 45. |
| Face | Enum.NormalId | The face of the part the light comes out of. |

## Members

SurfaceLight has no methods of its own. It also has the shared Instance members; see [Instance](../globals/instance.md).

## Example

```lua
local sign = Instance.new("Part")
sign.Size = Vector3.new(8, 2, 0.5)
sign.Position = Vector3.new(0, 10, 0)
sign.Anchored = true
sign.Parent = workspace

local glow = Instance.new("SurfaceLight", sign)
glow.Face = Enum.NormalId.Front
glow.Color = Color3.fromRGB(120, 200, 255)
glow.Range = 20
glow.Angle = 90
```

## See also

- [PointLight](pointlight.md): light in every direction.
- [SpotLight](spotlight.md): a cone from a face too.
- [Part](part.md): the usual parent.
- [API Reference](../api/api.md)
