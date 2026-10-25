# Building an interface

Panels, labels, and buttons that answer the player.

Everything on screen draws under a [ScreenGui](../classes/screengui.md), and the layer is a template: build it once in [StarterGui](../services/startergui.md) and each joining player receives a copy in their own PlayerGui.

## Lay the interface down

In the Explorer, click StarterGui, then drag a ScreenGui onto it from the Insert palette. Put a Frame under the ScreenGui the same way.

A new frame draws nothing, because `BackgroundTransparency` starts at 1. Give the frame a `BackgroundColor3` and set the transparency to 0 to see the panel.

## Put things where you want them

`Position` and `Size` are [UDim2](../globals/udim2.md): a fraction of the parent plus a pixel count on each axis, so a panel can sit at half the screen and stay there through a resize.

```lua
button.Position = UDim2.new(0.5, 0, 0.5, 0)
button.AnchorPoint = UDim2.new(0.5, 0.5, 0.5, 0.5)
```

`AnchorPoint` names which point of the object `Position` refers to, which is the shortest route to a centered anything. `UDim2.fromOffset(180, 44)` gives a pixel size with no scale part.

## Words and buttons

A [TextLabel](../classes/textlabel.md) draws text inside its bounds: `Text`, `TextColor3`, `TextSize`, and the two alignments. A [TextButton](../classes/textbutton.md) is a TextLabel the player can click. Connect `MouseButton1Click` for a left click; there is no Activated event.

| Property | Type | What it does |
| --- | --- | --- |
| Text | string | The string to draw. |
| TextColor3 | Color3 | The text color. |
| TextSize | number | Height in pixels. Default 18. |
| TextXAlignment | number | 0 left, 1 center, 2 right. |
| TextYAlignment | number | 0 top, 1 middle, 2 bottom. |

The two alignments are plain numbers, not enum items. [TextLabel](../classes/textlabel.md) holds the full property list.

A [UICorner](../classes/uicorner.md) under any of them rounds the corners, and a UIStroke draws an outline.

## Make it answer

Put a LocalScript under the ScreenGui, next to the things it drives. The copy in PlayerGui is what runs, and `script.Parent` finds the layer from inside it:

```lua
local panel = script.Parent:WaitForChild("Panel")
local toggle = panel:WaitForChild("Toggle")

local shown = false
panel.Visible = shown

toggle.MouseButton1Click:Connect(function ()
    shown = not shown
    panel.Visible = shown
end)
```

Hover colors read the mouse events, which need `Active` set to true on the object:

```lua
toggle.MouseEnter:Connect(function ()
    toggle.BackgroundColor3 = Color3.fromRGB(70, 120, 210)
end)

toggle.MouseLeave:Connect(function ()
    toggle.BackgroundColor3 = Color3.fromRGB(45, 110, 200)
end)
```

## Layers and respawns

Three [ScreenGui](../classes/screengui.md) properties control a whole layer:

| Property | Type | What it does |
| --- | --- | --- |
| Enabled | boolean | Whether the layer draws at all. |
| DisplayOrder | number | Draw order between layers, with higher values on top. |
| ResetOnSpawn | boolean | Whether the layer is dropped and rebuilt when the character respawns. Default true, so turn it off when an interface should carry over a respawn. |

## Moving things

[TweenService](../services/tweenservice.md) animates parts, humanoids, and SoundService, and nothing else. A tween built on a Frame runs, fires Completed, and moves nothing. Interface motion is a property write: set `Position` or `Visible` from code and the object lands where you put it.

## See also

- [ScreenGui](../classes/screengui.md): the layer everything draws in.
- [StarterGui](../services/startergui.md): the templates each player receives.
- [Frame](../classes/frame.md): containers, appearance, and the mouse events.
- [Player input](player-input.md): keys and clicks away from the interface.
- [API Reference](../api/index.md)
