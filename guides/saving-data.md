# Saving data

Values that outlast the session, stored beside the place.

The [Store](../services/store.md) service keeps saved values with the place itself, in a sidecar file next to the place file. Both calls are server-only; a LocalScript that tries either raises an error.

## Read with a default

Get returns nil for a key that has no value yet:

```lua
local store = game:GetService("Store")

local wins = store:Get("wins") or 0
```

## Write when the value changes

Set saves right away, and the store handles the disk on its own. It writes about two seconds after the last Set, at least every ten seconds while a script keeps setting, and it flushes anything pending at shutdown. A script can Set after every change and leave the writing to the store. The trade is small: a crash can lose up to ten seconds of changes, and never leaves a half-written file behind.

```lua
store:Set("wins", wins + 1)
```

## Keep players apart

Keys are one flat namespace for the whole place. When a value belongs to one player, put the UserId in the key:

```lua
local key = player.UserId .. ":wins"
```

Load it when the player joins, and remember that a script can miss a join that happened before it ran. Connect to `PlayerAdded` first, then walk the players already present:

```lua
local Players = game:GetService("Players")
local store = game:GetService("Store")

local function load(player)
    local wins = store:Get(player.UserId .. ":wins") or 0
    print(player.Name, "has", wins, "wins")
end

Players.PlayerAdded:Connect(load)

for _, player in ipairs(Players:GetPlayers()) do
    load(player)
end
```

## What a value can be

A boolean, a number, a string, a Vector3, a CFrame, a Color3, or a table of those. Instances cannot be saved, and a table holding one raises an error. The bounds: keys up to 256 bytes, 4096 keys, 16 MiB of file.

## Show it to the player

Clients cannot read the store, so send them a copy when a value changes:

```lua
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local winsChanged = ReplicatedStorage:WaitForChild("WinsChanged")

winsChanged:FireClient(player, wins)
```

The client listens with `OnClientEvent` and draws what arrives.

## Testing

A playtest reads the place's saved values and writes to a temporary copy, so testing never changes the real save.

## See also

- [Store](../services/store.md): the calls and their write timing.
- [Players](../services/players.md): joins, leaves, and the players already present.
- [RemoteEvent](../classes/remoteevent.md): sending a saved value to a client.
- [Testing your place](../tutorials/testing-your-place.md): the playtest copy of the save.
- [API Reference](../api/index.md)
