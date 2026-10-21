# workspace

Shortcut for the Workspace service.

`workspace` is the same instance as `game:GetService("Workspace")`. The engine sets it when the place loads, so scripts can use it without a lookup.

## What lives here

Parts, models, and characters sit under `workspace`, and that is what makes them part of the world. Creating a part does not put it anywhere by itself; setting its parent does.

```lua
local part = Instance.new("Part")
part.Position = Vector3.new(0, 10, 0)
part.Parent = workspace
```

Destroying the part removes it from the world, along with anything parented under it.

## Members

Workspace has the shared Instance members plus the world properties and the `Raycast` method. See [Workspace](../services/workspace.md) for the full reference.

## See also

- [Workspace](../services/workspace.md): the service page.
- [Part](../classes/part.md): the most common thing to put here.
- [API Reference](../api/index.md)
