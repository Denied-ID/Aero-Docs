# Folder

A container that keeps the Explorer organized and can hold anything.

A `Folder` is a container with no behavior of its own. Parts, scripts, other folders, and interface objects can all live under one, which gives scripts a single name to find and a single object to clone.

## Members

A Folder adds nothing to the members every Instance has. See [Instance](../globals/instance.md) for `Name`, `Parent`, `ClassName`, the child signals, and the method list.

## Example

```lua
local loot = Instance.new("Folder")
loot.Name = "Loot"
loot.Parent = workspace

for index = 1, 3 do
    local part = Instance.new("Part", loot)
    part.Name = "Coin" .. index
    part.Position = Vector3.new(index * 3, 5, 0)
end

print(#loot:GetChildren())    -- 3
```

## See also

- [Model](model.md): a group that also names a primary part.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/index.md)
