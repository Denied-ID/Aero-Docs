# SpotLight

A cone of light.

Parent a `SpotLight` to a part and it shines from one face in a cone. It has the settings every light has, plus the cone angle and the face it points out of.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| Color | Color3 | The light color, clamped from 0 to 1 per channel. |
| Brightness | number | Intensity, clamped from 0 to 100. Default 2. |
| Range | number | Reach in studs, clamped from 0 to 512. Default 16. 0 means no limit. |
| Shadows | boolean | Whether the light casts shadows. |
| Enabled | boolean | Whether the light shines. |
| Angle | number | The full cone angle in degrees, clamped from 0 to 180. Default 45. |
| Face | Enum.NormalId | The face of the part the cone comes out of. |

`Angle` is the whole spread of the cone, not the distance from the center to one edge.

## Members

SpotLight has no methods of its own. It also has the shared Instance members; see [Instance](../globals/instance.md).

## Example

```lua
local housing = Instance.new("Part")
housing.Size = Vector3.new(2, 2, 2)
housing.Position = Vector3.new(0, 14, 0)
housing.Anchored = true
housing.Parent = workspace

local beam = Instance.new("SpotLight", housing)
beam.Face = Enum.NormalId.Bottom
beam.Angle = 60
beam.Range = 40
beam.Brightness = 4
```

## See also

- [PointLight](pointlight.md): light in every direction.
- [SurfaceLight](surfacelight.md): a cone from a surface.
- [Enum](../globals/enum.md): the NormalId list.
- [API Reference](../api/api.md)
