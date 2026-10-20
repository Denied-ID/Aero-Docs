# TextBox

A field the player can type into.

A `TextBox` is a [TextLabel](textlabel.md) that accepts typing. It has the text members, the [Frame](frame.md) members, and five settings for editing and placeholder text.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| PlaceholderText | string | Text shown while the field is empty. |
| PlaceholderColor3 | Color3 | Color of the placeholder. Default is a mid grey. |
| ClearTextOnFocus | boolean | Clears the text when the player starts typing. Default true. |
| TextEditable | boolean | Whether the player can change the text. Default true. |
| MultiLine | boolean | Accepts line breaks. Default false. |

## Members

TextBox has every [TextLabel](textlabel.md) member, which includes every [Frame](frame.md) member, plus the shared Instance members in [Instance](../globals/instance.md).

The focus signals that exist inside the engine are not exposed to scripts. Read `Text` when you need the current value, for example from a button next to the field.

## Example

```lua
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui

local screen = Instance.new("ScreenGui")
screen.Name = "Prompt"
screen.Parent = playerGui

local field = Instance.new("TextBox", screen)
field.Size = UDim2.new(0, 260, 0, 40)
field.Position = UDim2.new(0.5, -130, 0.5, -20)
field.BackgroundTransparency = 0
field.Text = ""
field.PlaceholderText = "Type a name"
field.TextSize = 18
field.ClearTextOnFocus = true

local submit = Instance.new("TextButton", screen)
submit.Size = UDim2.new(0, 90, 0, 30)
submit.Position = UDim2.new(0.5, -45, 0.5, 30)
submit.Text = "Save"

submit.MouseButton1Click:Connect(function ()
    print("name is", field.Text)
end)
```

## See also

- [TextLabel](textlabel.md): the text members.
- [TextButton](textbutton.md): a button instead of a field.
- [Frame](frame.md): the layout members.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
