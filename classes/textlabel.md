# TextLabel

A line of text on the screen.

A `TextLabel` draws a string inside the bounds of a [Frame](frame.md). It has every Frame member, plus the text settings below.

## Text

| Property | Type | What it does |
| --- | --- | --- |
| Text | string | The string to draw. |
| TextColor3 | Color3 | The text color. |
| TextTransparency | number | 0 is solid, 1 is invisible. |
| TextSize | number | Height in pixels. Default 18. |
| Font | string | The font name. Default `Arial`. This is a string, not an `Enum.Font`. |
| TextXAlignment | number | 0 left, 1 center, 2 right. |
| TextYAlignment | number | 0 top, 1 middle, 2 bottom. |
| TextWrapped | boolean | Wraps long lines inside the frame. |
| TextScaled | boolean | Stores the flag for scaling text to the frame. Text still renders at `TextSize`. |
| TextStrokeTransparency | number | 0 draws a full outline, 1 draws none. Default 1. |
| TextStrokeColor3 | Color3 | The outline color. |
| TextBounds | Vector2 | The measured size of the drawn text in pixels. Read-only, and zero until the label has been drawn once. |

The alignment values are plain numbers, not enum items.

## Members

TextLabel has every [Frame](frame.md) member, plus the shared Instance members in [Instance](../globals/instance.md). It has no methods of its own.

## Example

```lua
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui

local screen = Instance.new("ScreenGui")
screen.Name = "Hud"
screen.Parent = playerGui

local label = Instance.new("TextLabel", screen)
label.Size = UDim2.new(0, 240, 0, 32)
label.Position = UDim2.new(0, 16, 0, 16)
label.BackgroundTransparency = 1
label.Text = "Waves cleared: 0"
label.TextColor3 = Color3.fromRGB(235, 235, 240)
label.TextSize = 20
label.TextXAlignment = 0
label.TextYAlignment = 1
```

## See also

- [Frame](frame.md): the members this class starts from.
- [TextButton](textbutton.md): text that can be clicked.
- [TextBox](textbox.md): text the player can type.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/index.md)
