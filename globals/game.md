# game

The root of the instance tree, and the way to reach every service.

`game` is the DataModel at the root of the instance tree. Services sit directly under it, and `game:GetService` reaches one without a script needing to know where it sits.

## Members

`game` is an Instance, so the shared properties and methods apply: `Name`, `Parent`, `ClassName`, `GetChildren`, `FindFirstChild`, and the child signals. See [Instance](instance.md) for that list.

| Member | Returns | What it does |
| --- | --- | --- |
| GetService(name) | Instance | Returns the service with that class name. |

## GetService

| Call | Result |
| --- | --- |
| `game:GetService("Players")` | The Players service. |
| `game:GetService("Workspace")` | The Workspace service. |
| `game:GetService("Nope")` | Error: `Nope is not a valid service name` |
| `part:GetService("Players")` | Error: `GetService is only available on the DataModel (game)` |

A place has all seventeen services: CoreGui, Kits, Lighting, Perf, Physics, Players, ReplicatedStorage, RunService, ServerScriptService, SoundService, StarterGui, StarterPack, StarterPlayer, Store, TweenService, UserInputService, and Workspace. `GetService` returns the existing one, so calling it from many scripts is normal. If a service has been removed, the call builds a new one and parents it under `game`.

Only services may sit directly under `game`. Moving anything else there raises an error that ends with `only services may live there`. Parts and models belong under Workspace.

## Example

```lua
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

print(game.ClassName)       -- DataModel
print(RunService:IsServer()) -- true on the server, false in a LocalScript
print(#Players:GetPlayers())
```

## See also

- [workspace](workspace.md): the shortcut for the Workspace service.
- [Instance](instance.md): the shared members every object has.
- [API Reference](../api/index.md)
