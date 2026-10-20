# Model

A group of parts you can name and handle as one.

A `Model` is a container for parts, usually the pieces of one object such as a gate, a vehicle, or a character. Scripts can hand the whole model around instead of a list of parts, and `PrimaryPart` marks the part that stands for it.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| PrimaryPart | Instance or nil | The part that represents the model. Any instance is accepted; the engine does not check that it is a part or that it is inside the model. |

## Members

Model also has the members every Instance has. See [Instance](../globals/instance.md).

## Example

```lua
local gate = Instance.new("Model")
gate.Name = "Gate"
gate.Parent = workspace

local post = Instance.new("Part", gate)
post.Name = "Post"
post.Size = Vector3.new(2, 12, 2)
post.Position = Vector3.new(0, 6, 0)

local bar = Instance.new("Part", gate)
bar.Name = "Bar"
bar.Size = Vector3.new(12, 1, 1)
bar.Position = Vector3.new(0, 10, 0)

gate.PrimaryPart = post
print(gate.PrimaryPart.Name)    -- Post
```

## See also

- [Folder](folder.md): a container without a primary part.
- [Part](part.md): what a model is usually made of.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
