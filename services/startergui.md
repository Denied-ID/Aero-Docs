# StarterGui

The interface every player starts with.

Children of `StarterGui` are copied into each player's PlayerGui when the player joins. Edit the templates here, because the copies are what players see. On a respawn, ScreenGuis with [ResetOnSpawn](../classes/screengui.md) are dropped and rebuilt from the templates again.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| CoreGuiPlayerList | boolean | Whether the player list is shown. |
| CoreGuiHealth | boolean | Whether the health display is shown. |
| CoreGuiChat | boolean | Whether the chat window is shown. |
| CoreGuiConnectionMeter | boolean | Whether the connection meter is shown. |

All four are saved with the place.

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| SetCoreGuiEnabled(type, enabled) | nothing | Shows or hides one of the engine's interface elements. |
| GetCoreGuiEnabled(type) | boolean | Whether that element is enabled. |

`type` is an `Enum.CoreGuiType`: `PlayerList`, `Health`, `Chat`, `ConnectionMeter`, or `All`. An invalid value raises `N is not a valid CoreGuiType`.

Only the player list, the health display, chat, and the connection meter have something to show or hide.

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
- [Building an interface](../guides/building-an-interface.md): a panel built from these templates.
- [CoreGui](coregui.md): the elements the methods above control.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/index.md)
