# Workspace

The place world.

`Workspace` is the root of everything in the scene. Parts, models, characters, and lights live under it, and it is the object you query when you need to know what a ray hits.

## Members

Workspace has no properties of its own. It has the shared Instance members, including `ChildAdded` and `GetChildren`, which are how you find things in the world. See [Instance](../globals/instance.md).

The global `workspace` points at this service, so `workspace.Part` and `game:GetService("Workspace").Part` reach the same instance.

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| Raycast(origin, direction, maxDistance, params) | table or nil | Finds the nearest part along a ray. |

### Raycast

| Argument | Type | What it does |
| --- | --- | --- |
| origin | Vector3 | Where the ray starts, in studs. |
| direction | Vector3 | Where it points. The length does not matter; the direction is normalized. A zero vector raises `Raycast direction must be non-zero`. |
| maxDistance | number | How far to look, in studs. Default 1000. |
| params | table or nil | Optional filters. |

The `params` table accepts two fields:

| Field | Type | What it does |
| --- | --- | --- |
| IgnoreCanCollide | boolean | When true, parts with `CanCollide` off are skipped. |
| FilterDescendantsInstances | array of Instance | Skips these instances and everything under them. |

A hit returns a table with four fields:

| Field | Type | What it is |
| --- | --- | --- |
| Instance | Instance | The part that was hit. |
| Position | Vector3 | The hit point, in studs. |
| Normal | Vector3 | The surface normal at the hit point. |
| Distance | number | How far along the ray the hit is, in studs. |

Nothing in range gives `nil`, not an empty table.

On a client, physics runs on the server, so the ray sees the interpolated positions the renderer is showing, about 50 ms behind the live simulation.

## Example

```lua
local origin = Vector3.new(0, 10, 0)
local direction = Vector3.new(0, -1, 0)

local result = workspace:Raycast(origin, direction, 100, {
    IgnoreCanCollide = true,
    FilterDescendantsInstances = { workspace.Character },
})

if result then
    print("hit", result.Instance.Name, "at", result.Position, "in", result.Distance, "studs")
else
    print("nothing below")
end
```

## See also

- [Part](../classes/part.md): the usual thing a ray hits.
- [Vector3](../globals/vector3.md): origins and directions.
- [game](../globals/game.md): the service container.
- [API Reference](../api/api.md)
