# UIStroke

Draws an outline around the interface object it sits in.

A `UIStroke` is a child of a [Frame](frame.md) or another interface object. The outline follows the object's shape, including rounded corners.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| Color | Color3 | The outline color. |
| Thickness | number | Width in pixels. Default 1. |
| Transparency | number | 0 is solid, 1 is invisible. |
| Enabled | boolean | Whether the outline draws. |
| LineJoinMode | number | 0 round, 1 bevel, 2 miter. |
| ApplyStrokeMode | number | 0 border, 1 contextual. |

## Members

UIStroke has no methods of its own. It also has the shared Instance members; see [Instance](../globals/instance.md).

## Example

```lua
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 160, 0, 48)
frame.BackgroundColor3 = Color3.fromRGB(28, 28, 34)

local corner = Instance.new("UICorner", frame)
corner.CornerRadius = UDim.new(0.2, 0)

local stroke = Instance.new("UIStroke", frame)
stroke.Color = Color3.fromRGB(90, 150, 230)
stroke.Thickness = 2
stroke.LineJoinMode = 0
```

## See also

- [UICorner](uicorner.md): rounded corners under the same outline.
- [UIGradient](uigradient.md): a gradient across the fill.
- [Frame](frame.md): the usual parent.
- [API Reference](../api/api.md)
