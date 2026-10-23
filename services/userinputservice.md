# UserInputService

Keyboard and mouse input on the client.

`UserInputService` reports input as it happens and answers questions about what is held right now. It only works on a client, where there is a keyboard and a pointer to read. Touch and gamepad have no path through the engine.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| KeyboardEnabled | boolean | Always true. Read-only. |
| MouseEnabled | boolean | Always true. Read-only. |
| TouchEnabled | boolean | Always false, because touch input is not implemented. Read-only. |
| GamepadEnabled | boolean | Always false, because gamepad input is not implemented. Read-only. |
| MouseBehavior | number | Stored, but nothing reads it, so the mouse is never captured. |

## Events

| Event | Callback arguments | When it fires |
| --- | --- | --- |
| InputBegan | input, gameProcessed | A key or mouse button went down. |
| InputEnded | input, gameProcessed | It came back up. |
| InputChanged | input, gameProcessed | The mouse wheel turned. |

`input` is an [InputObject](../classes/inputobject.md). The `gameProcessed` flag is false on every event; the engine's own interface does not claim input.

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| GetMouseLocation() | Vector2 | The pointer position in screen pixels. |
| GetMouseDelta() | Vector2 | How far the pointer moved during this frame. Reading it twice in one frame gives the same number. |
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
    elseif input.UserInputType == Enum.UserInputType.MouseButton1 then
        print("clicked at", input.Position.X, input.Position.Y)
    end
end)

UserInputService.InputChanged:Connect(function (input, gameProcessed)
    if input.UserInputType == Enum.UserInputType.MouseWheel then
        print("wheel", input.Position.Z)
    end
end)
```

## See also

- [InputObject](../classes/inputobject.md): what each event carries.
- [LocalScript](../classes/localscript.md): where client input belongs.
- [Player input](../guides/player-input.md): the guide that puts these events to work.
- [Enum](../globals/enum.md): key codes and input types.
- [API Reference](../api/index.md)
