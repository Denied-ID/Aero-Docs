# LocalScript

Luau code that runs on each player's machine.

A `LocalScript` holds its code in `Source` and starts it on a client. It never runs on the server, so it is the place for input, the camera, and anything that touches that player's interface.

## Members

LocalScript has the same members as [Script](script.md): `Source`, `Disabled`, and the read-only `Running`. The difference is where they start.

A LocalScript is not a subclass of Script, so `IsA("Script")` is false even though the same properties work.

## Where it runs

A LocalScript runs on the client it belongs to. On the server it stays idle.

StarterGui and StarterPack are copied to each player, so a LocalScript inside one runs from the copy in PlayerGui or Backpack, not from the template.

StarterPlayer is not copied, so a LocalScript there runs in place on the client.

## Example

```lua
-- LocalScript in StarterPlayer
local UserInputService = game:GetService("UserInputService")

UserInputService.InputBegan:Connect(function (input, gameProcessed)
    if gameProcessed then
        return
    end

    if input.KeyCode == Enum.KeyCode.Space then
        print("jump pressed on this client")
    end
end)
```

## See also

- [Script](script.md): code that runs on the server.
- [UserInputService](../services/userinputservice.md): input on the client.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
