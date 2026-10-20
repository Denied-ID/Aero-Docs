# InputObject

One input, described.

An `InputObject` is handed to [UserInputService](../services/userinputservice.md) listeners. It says what was pressed or moved and where it happened. You read them; the engine creates them.

## Properties

| Property | Type | What it is |
| --- | --- | --- |
| KeyCode | Enum.KeyCode | The key involved, for keyboard input. |
| UserInputType | Enum.UserInputType | Keyboard, mouse button, wheel, touch, or focus. |
| UserInputState | Enum.UserInputState | Begin, Change, End, Cancel, or None. |
| Position | Vector3 | Screen pixels in X and Y. For the mouse wheel, Z holds the wheel delta. |
| Delta | Vector3 | How far the input moved, in pixels. Wheel delta in Z. |

All five are read-only.

## Members

An InputObject has no methods or events of its own, and the shared Instance members do not do much on one. See [Instance](../globals/instance.md).

## Example

```lua
local UserInputService = game:GetService("UserInputService")

UserInputService.InputBegan:Connect(function (input, gameProcessed)
    if gameProcessed then
        return
    end

    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        print("clicked at", input.Position.X, input.Position.Y)
    elseif input.KeyCode == Enum.KeyCode.E then
        print("E pressed")
    end
end)
```

## See also

- [UserInputService](../services/userinputservice.md): where input objects come from.
- [Enum](../globals/enum.md): the key and input lists.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
