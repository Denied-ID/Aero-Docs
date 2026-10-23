# Player input

Keys and mouse buttons as they happen, read from a client.

Input is a client thing. The keyboard and the pointer live on that half, and the server has neither, so input code belongs in a [LocalScript](../classes/localscript.md). [UserInputService](../services/userinputservice.md) reports each key, button, and wheel turn when it happens, and answers questions about what is held right now.

## React to a key

Drop a LocalScript into StarterPlayer and connect to `InputBegan`:

```lua
local UserInputService = game:GetService("UserInputService")

UserInputService.InputBegan:Connect(function (input)
    if input.KeyCode == Enum.KeyCode.F then
        print("flashlight")
    end
end)
```

Every event hands you an [InputObject](../classes/inputobject.md). `KeyCode` is the key for keyboard input, `UserInputType` separates keyboard from mouse, and `Position` holds the screen pixels. A wheel turn reports its amount in `Position.Z`.

## Tell a click from a key

```lua
UserInputService.InputBegan:Connect(function (input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        print("clicked at", input.Position.X, input.Position.Y)
    elseif input.KeyCode == Enum.KeyCode.E then
        print("interact")
    end
end)
```

A click meant for an interface is better served where it lands: [TextButton](../classes/textbutton.md) and the [frame](../classes/frame.md) mouse events carry the click with no hit-testing of your own.

## Ask what is held

`InputBegan` reports the moment a key went down. For a key that matters the whole time it is held, like sprint on Shift, ask once per frame:

```lua
local RunService = game:GetService("RunService")

RunService:BindToRenderStep("Sprint", Enum.RenderPriority.Last.Value, function ()
    if UserInputService:IsKeyDown(Enum.KeyCode.LeftShift) then
        -- sprinting this frame
    end
end)
```

`BindToRenderStep` runs before each rendered frame, on the client. Binding the same name again replaces the earlier callback, and `RunService:UnbindFromRenderStep("Sprint")` removes the whole thing.

The wheel arrives through `InputChanged` with `UserInputType.MouseWheel`, and `GetMouseLocation()` and `GetMouseDelta()` answer where the pointer is and how far it moved this frame.

## The gameProcessed flag

Each callback also receives a `gameProcessed` flag. It reads false on every event: the engine's own interface does not claim input, so nothing in it takes a key away from a script.

## Touch and gamepad

Neither has a path through the engine. `TouchEnabled` and `GamepadEnabled` always read false, so build for the keyboard and mouse.

## See also

- [UserInputService](../services/userinputservice.md): the events and the held-key questions.
- [InputObject](../classes/inputobject.md): what each event carries.
- [RunService](../services/runservice.md): per-frame work on the client.
- [Building an interface](building-an-interface.md): clicks that land on buttons instead.
- [API Reference](../api/index.md)
