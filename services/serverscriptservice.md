# ServerScriptService

Server-only content.

Instances under `ServerScriptService` stay on the server. Clients never receive them, which makes it the place for server scripts and for data the players should not read.

## Members

ServerScriptService has no properties, events, or methods beyond the shared Instance members. See [Instance](../globals/instance.md).

## Example

```lua
-- Script in ServerScriptService
print(script.Parent.Name)    -- ServerScriptService

local Players = game:GetService("Players")
Players.PlayerAdded:Connect(function (player)
    print(player.Name, "joined")
end)
```

A Script placed here runs on the server. A LocalScript placed here never runs, because the server has no client side to run it on.

## See also

- [Script](../classes/script.md): the class that runs on the server.
- [ReplicatedStorage](replicatedstorage.md): content shared with clients.
- [API Reference](../api/index.md)
