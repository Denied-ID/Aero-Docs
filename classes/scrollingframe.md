# ScrollingFrame

A frame with a scrollable canvas inside it.

A `ScrollingFrame` shows part of a larger area and lets the player scroll to the rest. Children are laid out on the canvas, not on the visible frame, so the canvas usually needs to be taller than the frame.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| CanvasSize | UDim2 | The size of the scrollable area. |
| CanvasPosition | Vector2 | How far the canvas is scrolled, in pixels. |
| ScrollingEnabled | boolean | Whether the player can scroll it. |
| ScrollBarThickness | number | Width of the bar in pixels. Default 12. |
| ScrollBarImageColor3 | Color3 | The bar color. |
| VerticalScrollBarInset | number | 0 hides the bar, 1 always shows it. |
| AbsoluteCanvasSize | Vector2 | The canvas size in pixels. Read-only. |

`VerticalScrollBarInset` is clamped to 0 or 1, so other numbers quietly become one of those.

The mouse wheel goes to the scrolling frame around the object under the pointer that is `Active`, so set `Active` on the frame or on the content that should scroll.

## Members

ScrollingFrame has every [Frame](frame.md) member, plus the shared Instance members in [Instance](../globals/instance.md). It has no methods of its own.

## Example

```lua
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui

local screen = Instance.new("ScreenGui")
screen.Name = "List"
screen.Parent = playerGui

local list = Instance.new("ScrollingFrame", screen)
list.Size = UDim2.new(0, 240, 0, 300)
list.Position = UDim2.new(0, 16, 0, 16)
list.CanvasSize = UDim2.new(0, 0, 0, 540)
list.ScrollBarThickness = 8
list.Active = true

for index = 1, 12 do
    local row = Instance.new("TextLabel", list)
    row.Size = UDim2.new(1, -12, 0, 40)
    row.Position = UDim2.new(0, 4, 0, (index - 1) * 44)
    row.BackgroundTransparency = 0.9
    row.Text = "Row " .. index
    row.TextXAlignment = 0
end
```

## See also

- [Frame](frame.md): the members this class starts from.
- [UDim2](../globals/udim2.md): canvas sizes.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
