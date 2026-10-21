# ScrollingFrame

A frame with a scrollable canvas inside it.

A `ScrollingFrame` shows part of a larger area and lets the player scroll to the rest. Children are laid out against the canvas height while their X follows the frame's own width, so the canvas usually needs to be taller than the frame.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| CanvasSize | UDim2 | The size of the scrollable area. Children lay out against its Y; their X uses the frame's own width. |
| CanvasPosition | Vector2 | How far the canvas is scrolled, in pixels. Assigning a value wins over an ease already in flight. |
| ScrollingEnabled | boolean | Whether the mouse wheel moves the canvas. |
| ScrollBarThickness | number | Width reserved on the right when `VerticalScrollBarInset` is 1, in pixels. Default 12. |
| ScrollBarImageColor3 | Color3 | Stored for scripts that draw their own bar. The engine draws no bar, so on its own this changes nothing. |
| VerticalScrollBarInset | number | 0 reserves nothing, 1 takes `ScrollBarThickness` off the children's width. Clamped to those two values. |
| AbsoluteCanvasSize | Vector2 | The canvas size in pixels. Read-only. |

There is no scrollbar in the engine. `ScrollBarThickness` and `VerticalScrollBarInset` exist so content can be laid out clear of a bar you add yourself as ordinary widgets beside the frame; a bar parented inside the frame would scroll away with the canvas.

The mouse wheel goes to the innermost scrolling frame around the object under the pointer that is `Active`, so set `Active` on the frame or on the content that should scroll.

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
list.BackgroundTransparency = 0
list.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
list.CanvasSize = UDim2.new(0, 0, 0, 540)
list.VerticalScrollBarInset = 1
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
