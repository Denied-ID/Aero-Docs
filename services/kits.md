# Kits

A kit is a named build that lives in the place, and copies of one kit can stay linked.

## Methods

| Method | What it does |
| --- | --- |
| Build(name) | Clones the kit called `name` into the Workspace and returns the copy, or `nil` when no kit carries that name. |

## Linking copies

Kit copies that share the same `KitId` stay in sync while you edit: move a brick in one and it moves in all of them, add a brick and it appears in all of them. The most recent edit wins.

The kit's own name, position, and parent belong to each copy and never sync, so every copy can sit where it needs to sit. Set `KitId` to an empty string to break one copy away; copies made with Clone or copy and paste keep the link.

Syncing happens while you edit. During play, scripts change their own copies and nothing propagates.

## Example

```lua
local kits = game:GetService("Kits")

for i = 1, 3 do
    kits:Build("Watchtower")
end
```

## See also

- [API Reference](../api/api.md)
