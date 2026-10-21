# Players

Everyone connected, and the signals for joining and leaving.

`Players` holds one [Player](../classes/player.md) per connected client. It is where a script finds players and where it hears about new ones.

## Members

| Member | Type | What it does |
| --- | --- | --- |
| LocalPlayer | Player or nil | The player for this client. Read-only, and always nil on the server. |
| MaxPlayers | number | The player limit. Stored and replicated; connections are not refused because of it. |
| PlayerAdded | event | Fires on the server when someone joins. |
| PlayerRemoving | event | Fires on the server before someone leaves. |

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| GetPlayers() | array of Player | Every player currently connected. |

## Connecting to joins

A script that connects to `PlayerAdded` may have missed players who joined before it ran. Loop `GetPlayers` after connecting to catch them:

```lua
local Players = game:GetService("Players")

local function greet(player)
    print("hello", player.Name)
end

Players.PlayerAdded:Connect(greet)

for _, player in ipairs(Players:GetPlayers()) do
    greet(player)
end
```

`LocalPlayer` is set on a client. Reading it on the server gives nil, so guard it before use.

`PlayerAdded` and `PlayerRemoving` fire on the server only. A client sees players arrive as they replicate, but gets neither signal, so a client script that needs to react to a join has to watch for the Player instance another way.

## Example

```lua
local Players = game:GetService("Players")

Players.PlayerRemoving:Connect(function (player)
    print(player.Name, "left")
end)

print(#Players:GetPlayers(), "players connected")
```

## See also

- [Player](../classes/player.md): the player object.
- [StarterGui](startergui.md): what each player's interface starts from.
- [StarterPack](starterpack.md): what each player's backpack starts from.
- [API Reference](../api/index.md)
