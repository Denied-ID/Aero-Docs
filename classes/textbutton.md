# TextButton

A button with a text label on it.

A `TextButton` is a [TextLabel](textlabel.md) the player can click. It has the same text settings and the same [Frame](frame.md) members, and it adds no properties of its own.

## Members

TextButton has every member of [TextLabel](textlabel.md), which includes every member of [Frame](frame.md), plus the shared Instance members in [Instance](../globals/instance.md).

There is no `Activated` event. Use `MouseButton1Click` for a left click and `MouseButton2Click` for a right click.

## Example

```lua
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui

local screen = Instance.new("ScreenGui")
screen.Name = "Menu"
screen.Parent = playerGui

local button = Instance.new("TextButton", screen)
button.Size = UDim2.new(0, 180, 0, 44)
button.Position = UDim2.new(0.5, -90, 0.5, -22)
button.BackgroundColor3 = Color3.fromRGB(45, 110, 200)
button.Text = "Play"
button.TextColor3 = Color3.new(1, 1, 1)
button.TextSize = 18

local clicks = 0
button.MouseButton1Click:Connect(function ()
    clicks = clicks + 1
    button.Text = "Clicked " .. clicks
end)
```

## See also

- [TextLabel](textlabel.md): the text members.
- [Frame](frame.md): the layout members.
- [TextBox](textbox.md): text the player can type.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
