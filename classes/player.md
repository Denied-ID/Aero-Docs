# Player

One person in the game.

A `Player` is the engine's record of a connected client: its id, the character it controls, and the containers its interface and tools are copied into. The [Players](../services/players.md) service holds them all.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| UserId | number | The player's id. Read-only. |
| Character | Instance or nil | The character in the world. Spawning sets it and losing the character clears it. Writing accepts any instance, with no check that it is a character. |
| Backpack | Instance or nil | The container tools are copied into. Read-only, and updated from a child named `Backpack`. |
| PlayerGui | Instance or nil | The container interface is copied into. Read-only, and updated from a child named `PlayerGui`. |

## Events

A Player has only the shared Instance events. There is no `CharacterAdded` or `CharacterRemoving`. When a character arrives or goes away, the engine fires `Changed` with `"Character"`, which is the signal to watch.

## Example

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function (player)
    print(player.Name, player.UserId)

    player.Changed:Connect(function (property)
        if property == "Character" and player.Character then
            print("spawned", player.Character:GetFullName())
        end
    end)
end)
```

## See also

- [Players](../services/players.md): the list of players and the join signals.
- [Humanoid](humanoid.md): the part of a character that moves and takes damage.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
