# UserInputService

Keyboard, mouse, touch, and gamepad input on the client.

`UserInputService` reports input as it happens and answers questions about what is held right now. It only works on a client, where there is a keyboard and a pointer to read.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| KeyboardEnabled | boolean | Whether a keyboard is present. Read-only. |
| MouseEnabled | boolean | Whether a mouse is present. Read-only. |
| TouchEnabled | boolean | Whether touch input is present. Read-only. |
| GamepadEnabled | boolean | Whether a gamepad is present. Read-only. |
| MouseBehavior | number | How the mouse is captured: 0 default, 1 lock to center, 2 lock where it is. Writable, with no validation. |

## Events

| Event | Callback arguments | When it fires |
| --- | --- | --- |
| InputBegan | input, gameProcessed | A key, button, or touch went down. |
| InputEnded | input, gameProcessed | It came back up. |
| InputChanged | input, gameProcessed | It moved or changed state. |

`input` is an [InputObject](../classes/inputobject.md). `gameProcessed` is true when the engine's own interface has already handled the event, which is the usual reason a click on a menu should not also fire a game action.

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| GetMouseLocation() | Vector2 | The pointer position in screen pixels. |
| GetMouseDelta() | Vector2 | How far the pointer moved since the last check. |
| IsKeyDown(keyCode) | boolean | Whether that key is held. |
| IsMouseButtonPressed(button) | boolean | Whether that mouse button is held. |

`IsKeyDown` takes an `Enum.KeyCode` or its number. `IsMouseButtonPressed` takes an `Enum.UserInputType` such as `MouseButton1` or its number.

## Example

```lua
local UserInputService = game:GetService("UserInputService")

UserInputService.InputBegan:Connect(function (input, gameProcessed)
    if gameProcessed then
        return
    end

    if input.KeyCode == Enum.KeyCode.F then
        print("flashlight")
    end
end)

UserInputService.InputChanged:Connect(function (input, gameProcessed)
    if not gameProcessed and input.UserInputType == Enum.UserInputType.MouseMovement then
        local pointer = UserInputService:GetMouseLocation()
        print(pointer.X, pointer.Y)
    end
end)
```

## See also

- [InputObject](../classes/inputobject.md): what each event carries.
- [LocalScript](../classes/localscript.md): where client input belongs.
- [Enum](../globals/enum.md): key codes and input types.
- [API Reference](../api/api.md)
