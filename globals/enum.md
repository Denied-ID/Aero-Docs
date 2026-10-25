# Enum

Named lists of options.

An enum is a fixed set of named values. `Enum.Material.Plastic` names one option from the Material list, and properties that take a material accept that value. Every option also has a number, which is what the engine stores and what replication and save files carry.

## Reading an item

| Expression | Result |
| --- | --- |
| `Enum.Material` | The Material enum type. |
| `Enum.Material.Plastic` | One item from that type. |
| `Enum.GetEnums()` | A table of every enum type. |

An unknown type raises `Nope is not a valid member of Enum`. An unknown item on a real type raises `Nope is not a valid member of Enum.Material`.

## Enum types

Each type has a `GetEnumItems` method that returns its items in the order they were registered:

```lua
for _, item in Enum.Material:GetEnumItems() do
    print(item.Name, item.Value)
end
```

## Enum items

| Member | Type | What it does |
| --- | --- | --- |
| Name | string | The item name, such as `Plastic`. `name` is an alias. |
| Value | number | The stored number. `value` is an alias. |
| EnumType | string | The name of the list the item came from, such as `"Material"`. |

`EnumType` is a string, not an enum type. Compare it with `item.EnumType == "Material"`.

Two items are equal when they come from the same list and have the same value. Printing an item gives its full name, as in `Enum.Material.Plastic`. `typeof` reports `"EnumItem"` for an item and `"Enum"` for a type.

## The lists

Every list below carries the number the engine stores, which is what replication and save files use.

### Material

| Item | Value |
| --- | --- |
| Plastic | 256 |
| SmoothPlastic | 272 |
| Neon | 288 |
| Wood | 512 |
| WoodPlanks | 528 |
| Slate | 800 |
| Concrete | 816 |
| Granite | 832 |
| Marble | 848 |
| Brick | 864 |
| Pebble | 880 |
| Cobblestone | 896 |
| CorrodedMetal | 1040 |
| DiamondPlate | 1056 |
| Foil | 1072 |
| Metal | 1088 |
| Grass | 1280 |
| Sand | 1296 |
| Fabric | 1312 |
| Glass | 1568 |
| ForceField | 1584 |

### PartType

| Item | Value |
| --- | --- |
| Block | 0 |
| Ball | 1 |
| Cylinder | 2 |
| Wedge | 3 |
| CornerWedge | 4 |

### LightingTechnology

| Item | Value | What it does |
| --- | --- | --- |
| Compatibility | 0 | The older flat lighting: ambient never varies by surface orientation. |
| Dynamic | 1 | The directional look: ambient varies by surface orientation. |

See [Lighting](../services/lighting.md).

### BlastFalloff

| Item | Value | What it does |
| --- | --- | --- |
| Constant | 0 | Full push at every distance inside the radius. |
| Linear | 1 | Fades evenly from the epicenter to the edge. |
| Quadratic | 2 | The fade steepens near the edge, so most of the push stays near the center. |
| Sharp | 3 | Nearly everything at the center, almost nothing past half the radius. |

A raw number works as well, read as the exponent on the fade curve, so `1.5` sits between Linear and Quadratic. See [Physics](../services/physics.md).

### NormalId

| Item | Value |
| --- | --- |
| Right | 0 |
| Top | 1 |
| Back | 2 |
| Left | 3 |
| Bottom | 4 |
| Front | 5 |

### EasingStyle

| Item | Value |
| --- | --- |
| Linear | 0 |
| Sine | 1 |
| Back | 2 |
| Quad | 3 |
| Quart | 4 |
| Quint | 5 |
| Bounce | 6 |
| Elastic | 7 |
| Exponential | 8 |
| Circular | 9 |
| Cubic | 10 |

### EasingDirection

| Item | Value |
| --- | --- |
| In | 0 |
| Out | 1 |
| InOut | 2 |

### UserInputType

| Item | Value |
| --- | --- |
| MouseButton1 | 0 |
| MouseButton2 | 1 |
| MouseButton3 | 2 |
| MouseWheel | 3 |
| MouseMovement | 4 |
| Touch | 7 |
| Keyboard | 8 |
| Focus | 9 |
| None | 10 |

### KeyCode

| Item | Value |
| --- | --- |
| Unknown | 0 |
| Backspace | 8 |
| Tab | 9 |
| Return | 13 |
| Escape | 27 |
| Space | 32 |
| Zero to Nine | 48 to 57, in order |
| A to Z | 97 to 122, in order |
| Up | 273 |
| Down | 274 |
| Right | 275 |
| Left | 276 |
| RightShift | 303 |
| LeftShift | 304 |
| RightControl | 305 |
| LeftControl | 306 |
| RightAlt | 307 |
| LeftAlt | 308 |

### CameraType

| Item | Value |
| --- | --- |
| Fixed | 0 |
| Attach | 1 |
| Watch | 2 |
| Track | 3 |
| Follow | 4 |
| Custom | 5 |
| Scriptable | 6 |
| Orbital | 7 |

### RenderPriority

| Item | Value |
| --- | --- |
| First | 0 |
| Input | 100 |
| Camera | 200 |
| Character | 300 |
| Last | 2000 |

### UserInputState

| Item | Value |
| --- | --- |
| Begin | 0 |
| Change | 1 |
| End | 2 |
| Cancel | 3 |
| None | 4 |

### PlaybackState

| Item | Value |
| --- | --- |
| Begin | 0 |
| Delayed | 1 |
| Playing | 2 |
| Paused | 3 |
| Completed | 4 |
| Cancelled | 5 |

### CoreGuiType

| Item | Value |
| --- | --- |
| PlayerList | 0 |
| Health | 1 |
| Backpack | 2 |
| Chat | 3 |
| All | 4 |
| EmotesMenu | 5 |

### SurfaceType

| Item | Value | What it does |
| --- | --- | --- |
| Smooth | 0 | A plain face. The default, and what every other value reads back as. |
| Glue | 1 | Kept as the number you give it, and drawn as a plain face. |
| Weld | 2 | Kept as the number you give it, and drawn as a plain face. |
| Studs | 3 | Kept, and drawn as studs. |
| Inlet | 4 | Kept, and drawn as an inlet. |
| Universal | 5 | Kept as the number you give it, and drawn as a plain face. |
| Hinge | 6 | Kept as the number you give it, and drawn as a plain face. |
| Motor | 7 | Kept as the number you give it, and drawn as a plain face. |
| SteppingMotor | 8 | Kept as the number you give it, and drawn as a plain face. |
| SmoothNoOutlines | 10 | Kept as the number you give it, and drawn as a plain face. |

Only `Studs` and `Inlet` change how a face draws. Every other value is stored as the number you gave it and reads back as `Smooth`.

## Example

```lua
local part = Instance.new("Part")
part.Material = Enum.Material.Neon

if part.Material == Enum.Material.Neon then
    print("glowing")
end

print(Enum.Material.Neon.EnumType)   -- Material
```

## See also

- [Instance](../globals/instance.md): objects whose properties take enum items.
- [TweenInfo](tweeninfo.md): easing styles and directions.
- [Physics](../services/physics.md): blasts, and the falloff enum they take.
- [Part](../classes/part.md): materials, shapes, and the surface faces.
- [API Reference](../api/index.md)
