# RemoteEvent

Sends values between the server and clients.

A RemoteEvent is a named channel between the two sides. A Script on the server listens with `OnServerEvent` and answers with `FireClient` or `FireAllClients`. A LocalScript sends with `FireServer` and listens with `OnClientEvent`.

## Events

| Event | Callback arguments | When it fires |
| --- | --- | --- |
| OnServerEvent | player, ... | A client called `FireServer`. `player` is who sent it. |
| OnClientEvent | ... | The server called `FireClient` or `FireAllClients`. |

## Methods

| Method | Works on | What it does |
| --- | --- | --- |
| FireServer(...) | client | Sends the arguments to the server. |
| FireClient(player, ...) | server | Sends the arguments to one player. |
| FireAllClients(...) | server | Sends the arguments to every player. |

Calling one from the wrong side raises an error, such as `FireServer can only be called from the client` or `FireClient can only be called from the server`.

## What can be sent

| Value | How it arrives |
| --- | --- |
| nil, boolean, number, string | As given. |
| Vector3, CFrame, Color3 | As given. |
| Instance | By reference. An instance the receiving side does not have arrives as nil. |
| table | String or number keys. Arrays keep their order. |

Tables can nest up to 32 levels. A deeper table raises `table exceeds the maximum nesting depth (32)`, a table that contains itself raises `table cannot be nested inside itself (cyclic reference)`, and a key of another type raises `table keys must be strings or numbers`.

Functions, threads, and other types cannot cross the wire.

## Example

```lua
-- Script in ServerScriptService
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local ping = ReplicatedStorage:WaitForChild("Ping")

ping.OnServerEvent:Connect(function (player, message)
    print(player.Name, "sent", message)
    ping:FireClient(player, "pong")
end)
```

```lua
-- LocalScript
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local ping = ReplicatedStorage:WaitForChild("Ping")

ping.OnClientEvent:Connect(function (message)
    print("server replied", message)
end)

ping:FireServer("hello")
```

## See also

- [RemoteFunction](remotefunction.md): a call that returns a value.
- [Players](../services/players.md): where players come from.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
