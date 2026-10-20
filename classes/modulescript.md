# ModuleScript

Luau code that runs only when another script requires it.

A `ModuleScript` never starts on its own. It holds a chunk in `Source` that runs the first time [require](../functions/require.md) asks for it, and the value it returns is cached for every later call in that script VM.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| Source | string | The code text. Writing it stores the text; a module that has already been required keeps its cached result. |
| Disabled | boolean | Stored like the same property on a Script. Modules start through `require`, not through the script scanner. |

## Members

ModuleScript adds no events or methods. It also has the members every Instance has; see [Instance](../globals/instance.md).

## Example

```lua
-- ModuleScript in ReplicatedStorage, named Settings
return {
    roundsToWin = 3,
    respawnDelay = 5,
}
```

```lua
-- Script
local Settings = require(game:GetService("ReplicatedStorage").Settings)
print(Settings.respawnDelay)    -- 5
```

## See also

- [require](../functions/require.md): how a module is loaded and cached.
- [Script](script.md): code that starts by itself.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
