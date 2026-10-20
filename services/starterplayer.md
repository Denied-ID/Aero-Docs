# StarterPlayer

Client-side content that runs where it sits.

`StarterPlayer` holds the scripts that should run on each client. Unlike StarterGui and StarterPack, its contents are not copied: a LocalScript placed here runs in place on the client.

## Members

StarterPlayer has no properties, events, or methods beyond the shared Instance members. See [Instance](../globals/instance.md).

## Example

```lua
-- LocalScript in StarterPlayer
local Players = game:GetService("Players")

print(script:GetFullName())    -- StarterPlayer.Camera

local cameraScript = nil
for _, child in ipairs(script.Parent:GetChildren()) do
    if child:IsA("LocalScript") then
        cameraScript = child
    end
end
```

## See also

- [LocalScript](../classes/localscript.md): the class that runs here.
- [StarterGui](startergui.md): interface copied into each player.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
