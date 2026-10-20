# ReplicatedStorage

Content both sides need.

Instances under `ReplicatedStorage` are copied to every client. It is the usual home for RemoteEvents, RemoteFunctions, and ModuleScripts that both the server and clients require.

## Members

ReplicatedStorage has no properties, events, or methods beyond the shared Instance members. See [Instance](../globals/instance.md).

## Example

```lua
-- Script on the server, and a LocalScript on each client
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Settings = require(ReplicatedStorage:WaitForChild("Settings"))
local ping = ReplicatedStorage:WaitForChild("Ping")

print(Settings.respawnDelay)
```

Both sides can find the same instance by the same path, which is what makes it a good meeting point. `WaitForChild` is the safe lookup when a client script may run before replication finishes.

## See also

- [RemoteEvent](../classes/remoteevent.md): a channel kept here.
- [ModuleScript](../classes/modulescript.md): shared code kept here.
- [ServerScriptService](serverscriptservice.md): the server-only container.
- [API Reference](../api/api.md)
