# Humanoid

Makes a model walk, jump, and take damage.

A `Humanoid` sits inside a character model next to the parts that make up its body. It reads movement input, moves the character, and reports when the character dies.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| WalkSpeed | number | Movement speed in studs per second. |
| JumpPower | number | Stored, but the jump arc uses a fixed jump height, so changing this does not change a jump. |
| Health | number | Current health. |
| MaxHealth | number | The value the health bar is drawn against. Replicated health is capped to it. |
| AutoRotate | boolean | Whether the character turns to face the direction it moves. |

None of these values are clamped. Setting `Health` above `MaxHealth` or a negative `WalkSpeed` stores the number as given.

The engine sets `Health` to 0 when the character's root falls below `y = -25` world units, about -100 studs. That kill plane is how a fall out of the map ends a life.

## Events

| Event | Callback arguments | When it fires |
| --- | --- | --- |
| Died | none | Health reached 0. |
| StateChanged | oldState, newState | The character moved between its states. |

The state names are `Standing`, `Running`, `Jumping`, `Freefall`, `KnockedBack`, and `Dead`. There is no `State` property to read, so keep the last value from `StateChanged` if you need to know it later.

## Members

Humanoid has no methods of its own. It also has the shared Instance members; see [Instance](../globals/instance.md).

## Example

```lua
local Players = game:GetService("Players")

local function giveSpeed(player, character)
    local humanoid = character and character:FindFirstChildOfClass("Humanoid")
    if not humanoid then
        return
    end

    humanoid.WalkSpeed = 24
    humanoid.Died:Connect(function ()
        print(player.Name, "died")
    end)
end

Players.PlayerAdded:Connect(function (player)
    player.Changed:Connect(function (property)
        if property == "Character" then
            giveSpeed(player, player.Character)
        end
    end)

    giveSpeed(player, player.Character)
end)
```

Player has no `CharacterAdded` event. The character arrives as a change to `Player.Character`, which is what the example listens for.

## See also

- [Player](player.md): the player a character belongs to.
- [Model](model.md): the group a character is built in.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
