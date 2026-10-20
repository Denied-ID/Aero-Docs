# StarterGui

The interface every player starts with.

Children of `StarterGui` are copied into each player's PlayerGui when their character spawns. Edit the templates here; the copies are what players see.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| ResetPlayerGuiOnSpawn | boolean | Whether PlayerGui is emptied and rebuilt from StarterGui on each spawn. |

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| SetCoreGuiEnabled(type, enabled) | nothing | Shows or hides one of the engine's own interface elements. |
| GetCoreGuiEnabled(type) | boolean | Whether that element is enabled. |

`type` is an `Enum.CoreGuiType`: `PlayerList`, `Health`, `Backpack`, `Chat`, `All`, or `EmotesMenu`. An invalid value raises `N is not a valid CoreGuiType`.

## Example

```lua
local StarterGui = game:GetService("StarterGui")

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Backpack, false)
StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Health, false)

print(StarterGui:GetCoreGuiEnabled(Enum.CoreGuiType.Health))    -- false
```

Run this from a LocalScript, because each client controls its own interface.

## See also

- [ScreenGui](../classes/screengui.md): the layers copied from here.
- [CoreGui](coregui.md): the elements the methods above control.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
