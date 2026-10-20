# Part

A solid block. The basic building piece.

A `Part` is a physical object with a position, a size, a look, and a collision shape. Most of a place is made of parts.

## Creating one

```lua
local part = Instance.new("Part")
part.Size = Vector3.new(4, 1, 2)
part.Position = Vector3.new(0, 5, 0)
part.Anchored = true
part.Parent = workspace
```

## Position and size

| Property | Type | What it does |
| --- | --- | --- |
| CFrame | CFrame | Position and rotation together. |
| Position | Vector3 | The center, in studs. |
| Orientation | Vector3 | Rotation in degrees. `Rotation` is an alias. |
| Size | Vector3 | Extents in studs. Each axis is clamped from 1 to 2048, and non-finite values are ignored. |

Writing `CFrame` or `Position` on a part that belongs to a character moves the whole character so the limb lands there, not just the limb.

Sphere and Cylinder parts use one extent for all three axes. Setting `Size` on one of them applies the X value to all three, and reading it back gives that uniform size.

## Appearance

| Property | Type | What it does |
| --- | --- | --- |
| Color | Color3 | The surface color. |
| BrickColor | BrickColor | Reading returns the palette entry closest to `Color`. Writing also accepts a Color3. |
| Transparency | number | 0 is solid, 1 is invisible. Not clamped. |
| Reflectance | number | How mirror-like the surface is. Not clamped. |
| Metallic | number | Clamped from 0 to 1. |
| Roughness | number | Clamped from 0 to 1. |
| Material | Enum.Material | The surface material, by enum item, name, or number. |
| StudTiling | Vector2 | Studs per stud on each axis, clamped from 0.01 to 64. |
| StudOffset | Vector2 | Where the stud pattern starts, clamped from -100 to 100. |
| StudBump | number | How far studs rise, clamped from 0 to 1. |

`BrickColor` is only a view of `Color`: the part stores channels, not a palette number, so two palette colors with the same channels are indistinguishable when read back.

`Shape` takes `Enum.PartType` or one of the strings `Block`, `Ball`, `Sphere`, `Cylinder`, `Wedge`, and `CornerWedge`. Prefer the strings. The enum values for `Ball` and `Cylinder` are numbered differently from the stored shapes, so assigning `Enum.PartType.Cylinder` gives you a sphere.

## Physics

| Property | Type | What it does |
| --- | --- | --- |
| Anchored | boolean | A part that does not fall or move on its own. |
| CanCollide | boolean | Whether other parts collide with it. |
| CastShadow | boolean | Whether it casts a shadow. |
| Mass | number | Read-only. The size cubed times the density, or 0 when `Massless`. |
| Massless | boolean | Excludes the part from the assembly's mass. |
| Velocity | Vector3 | World velocity in studs per second. |
| AssemblyLinearVelocity | Vector3 | The linear velocity of the whole assembly, in studs per second. |
| AssemblyAngularVelocity | Vector3 | The angular velocity of the whole assembly, in the solver's units. |
| CustomPhysicalProperties | table or nil | Density, Friction, Elasticity, FrictionWeight, and ElasticityWeight, as a table. `nil` clears it. |

Writing a velocity value wakes a sleeping part, but only when the value actually changes.

## Surfaces

`TopSurface`, `BottomSurface`, `FrontSurface`, `BackSurface`, `RightSurface`, and `LeftSurface` each take an `Enum.SurfaceType`, a name, or a number. Only `Studs` and `Inlet` change how a face draws; the others are stored and render as smooth.

## Members

Part has the members every Instance has, and no methods of its own. See [Instance](../globals/instance.md).

## Example

```lua
local platform = Instance.new("Part")
platform.Name = "Platform"
platform.Size = Vector3.new(20, 1, 20)
platform.Position = Vector3.new(0, 0, 0)
platform.Anchored = true
platform.Color = Color3.fromRGB(90, 140, 200)
platform.Material = Enum.Material.Slate
platform.Parent = workspace
```

Any unanchored part starts falling as soon as it is parented into Workspace.

## See also

- [MeshPart](meshpart.md): a part with a mesh shape.
- [CFrame](../globals/cframe.md): positions and rotations.
- [Enum](../globals/enum.md): materials, shapes, and surface types.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
