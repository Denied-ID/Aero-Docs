# StarterGui

The interface every player starts with.

Children of `StarterGui` are copied into each player's PlayerGui when the player joins. Edit the templates here; the copies are what players see. On a respawn, the reset setting below decides whether PlayerGui is rebuilt from the templates again.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| ResetPlayerGuiOnSpawn | boolean | Whether PlayerGui is emptied and rebuilt from StarterGui on each spawn. |

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| SetCoreGuiEnabled(type, enabled) | nothing | Shows or hides one of the engine's interface elements. |
| GetCoreGuiEnabled(type) | boolean | Whether that element is enabled. |

`type` is an `Enum.CoreGuiType`: `PlayerList`, `Health`, `Backpack`, `Chat`, `All`, or `EmotesMenu`. An invalid value raises `N is not a valid CoreGuiType`.

Only the player list, the health display, and chat have something to show or hide. The backpack and emotes menu record the flag and change nothing, and `GetCoreGuiEnabled` reads that recorded flag back.

## Example

```lua
local StarterGui = game:GetService("StarterGui")

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.PlayerList, false)
StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Health, false)

print(StarterGui:GetCoreGuiEnabled(Enum.CoreGuiType.Health))    -- false
```

Run this from a LocalScript, because each client controls its own interface.

## See also

- [ScreenGui](../classes/screengui.md): the layers copied from here.
- [CoreGui](coregui.md): the elements the methods above control.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
