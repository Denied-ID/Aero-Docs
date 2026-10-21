# UIGradient

Blends two colors across the interface object it sits in.

A `UIGradient` is a child of a [Frame](frame.md) or another interface object. Paint moves from `Color0` at the start of the gradient to `Color1` at the end, and `Rotation` turns the direction.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| Color0 | Color3 | The color at the start. Default is a green. |
| Color1 | Color3 | The color at the end. Default is a lighter green. |
| Transparency0 | number | Opacity at the start. 0 is solid. |
| Transparency1 | number | Opacity at the end. |
| Rotation | number | Direction in degrees. 0 runs left to right. |
| Enabled | boolean | Whether the gradient applies. |

The `Rotation` here is unrelated to the rotation of a part.

## Members

UIGradient has no methods of its own. It also has the shared Instance members; see [Instance](../globals/instance.md).

## Example

```lua
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui

local screen = Instance.new("ScreenGui")
screen.Parent = playerGui

local bar = Instance.new("Frame", screen)
bar.Size = UDim2.new(0, 240, 0, 24)
bar.BackgroundColor3 = Color3.new(1, 1, 1)
bar.BackgroundTransparency = 0

local gradient = Instance.new("UIGradient", bar)
gradient.Color0 = Color3.fromRGB(80, 200, 255)
gradient.Color1 = Color3.fromRGB(70, 100, 230)
gradient.Rotation = 90
```

## See also

- [UICorner](uicorner.md): rounded corners.
- [UIStroke](uistroke.md): an outline.
- [Frame](frame.md): the usual parent.
- [API Reference](../api/index.md)
