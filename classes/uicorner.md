# UICorner

Rounds the corners of the interface object it sits in.

Add a `UICorner` as a child of a [Frame](frame.md) or another interface object and its corners are drawn rounded. The radius comes from one UDim, so it can scale with the parent.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| CornerRadius | UDim | The corner radius. The scale part is a fraction of the parent's shorter side; the offset part is pixels. |

## Members

UICorner has no methods of its own. It also has the shared Instance members; see [Instance](../globals/instance.md).

## Example

```lua
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui

local screen = Instance.new("ScreenGui")
screen.Parent = playerGui

local frame = Instance.new("Frame", screen)
frame.Size = UDim2.new(0, 160, 0, 48)
frame.BackgroundColor3 = Color3.fromRGB(40, 40, 46)
frame.BackgroundTransparency = 0

local corner = Instance.new("UICorner", frame)
corner.CornerRadius = UDim.new(0.25, 0)
```

## See also

- [UIStroke](uistroke.md): an outline around the same object.
- [UIGradient](uigradient.md): a color gradient across it.
- [Frame](frame.md): the usual parent.
- [API Reference](../api/api.md)
