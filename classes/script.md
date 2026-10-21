# Script

Luau code that runs on the server.

A `Script` holds its code in `Source` and starts it when the place begins. It runs on the server only: a client never runs one. Use a [LocalScript](localscript.md) for code that has to run on each player's machine.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| Source | string | The code text. Writing it stores the text; it does not recompile or restart a script that is already running. |
| Disabled | boolean | While true, the script does not start and its threads are stopped. Setting it back to false lets it start again from the top. |
| Running | boolean | True once the script has started and has not been stopped. Read-only. |

## Where it runs

Placement usually makes no difference: a Script in Workspace, ReplicatedStorage, or ServerScriptService runs on the server. Destroying a script, or setting its parent to nil, stops it.

The exception is StarterGui and StarterPack. Contents of those two are copied to each player, so a Script inside them is skipped where it sits and runs from the copy the player receives. Running the template as well would print everything twice and wire the copy to the wrong tree.

## Example

```lua
-- Script in ServerScriptService
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function (player)
    print(player.Name, "joined")
end)

print("server started")
```

## See also

- [LocalScript](localscript.md): code that runs on each client.
- [ModuleScript](modulescript.md): code that runs only when required.
- [Client and server](../scripting/client-and-server.md): the two halves of a place.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
