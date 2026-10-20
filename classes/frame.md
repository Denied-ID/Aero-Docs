# Frame

A box that holds other interface objects.

A `Frame` is the basic interface container. It has a position, a size, a background, and a border, and it can hold labels, buttons, images, and more frames. A frame draws when it sits under a [ScreenGui](screengui.md).

## Position and size

| Property | Type | What it does |
| --- | --- | --- |
| Position | UDim2 | Where the frame sits inside its parent. |
| Size | UDim2 | How large the frame is. |
| AnchorPoint | UDim2 | Which point of the frame `Position` refers to. `0.5, 0.5` centers it. |
| AbsolutePosition | Vector2 | The position in pixels on screen. Read-only. |
| AbsoluteSize | Vector2 | The size in pixels on screen. Read-only. |

The read-only pair is what layout code uses after a resize, because it has already applied the scale parts.

## Appearance

| Property | Type | What it does |
| --- | --- | --- |
| BackgroundColor3 | Color3 | The fill color. |
| BackgroundTransparency | number | 0 is solid, 1 is invisible. Default is 1, so a new frame draws nothing until you lower it. |
| BorderColor3 | Color3 | The border color. |
| BorderSizePixel | number | Border width in pixels. 0 removes the border. |
| Visible | boolean | Whether the frame and everything inside it draws. |
| Active | boolean | Whether the frame takes mouse input. |
| ClipsDescendants | boolean | Whether children are cut off at the frame's edges. |
| ZIndex | number | Draw order among siblings. Higher draws on top. |

## Events

All eight take no arguments.

| Event | When it fires |
| --- | --- |
| MouseEnter | The mouse moved onto the frame. |
| MouseLeave | The mouse moved off the frame. |
| MouseButton1Click | Left click pressed and released on the frame. |
| MouseButton1Down | Left button pressed on the frame. |
| MouseButton1Up | Left button released on the frame. |
| MouseButton2Click | Right click pressed and released on the frame. |
| MouseButton2Down | Right button pressed on the frame. |
| MouseButton2Up | Right button released on the frame. |

Mouse events need `Active` set to true.

## Members

Frame has no class-specific methods. It also has the shared Instance members; see [Instance](../globals/instance.md).

## Example

```lua
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui

local screen = Instance.new("ScreenGui")
screen.Name = "Hud"
screen.Parent = playerGui

local panel = Instance.new("Frame", screen)
panel.Name = "Panel"
panel.Size = UDim2.new(0, 220, 0, 90)
panel.Position = UDim2.new(0.5, -110, 0, 16)
panel.BackgroundColor3 = Color3.fromRGB(24, 24, 28)
panel.BackgroundTransparency = 0
panel.BorderSizePixel = 1
panel.BorderColor3 = Color3.fromRGB(70, 70, 80)

panel.MouseEnter:Connect(function ()
    panel.BackgroundColor3 = Color3.fromRGB(40, 40, 48)
end)
```

## See also

- [ScreenGui](screengui.md): the layer a frame draws in.
- [TextLabel](textlabel.md): text inside a frame.
- [UDim2](../globals/udim2.md): how position and size are written.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
