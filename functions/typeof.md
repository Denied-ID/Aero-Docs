# typeof

Names the type of a value.

`typeof` returns a string describing the value. For the engine's own values it returns the name used across this reference: `Instance` for anything in the tree, `Enum` for a list, `EnumItem` for one item from a list.

## Engine values

| Value | What typeof returns |
| --- | --- |
| `game`, `workspace`, or any instance | Instance |
| `Enum.Material` | Enum |
| `Enum.Material.Plastic` | EnumItem |
| an event, such as `Players.PlayerAdded` | Signal |
| the result of `Connect` | Connection |
| `Vector3.new()` | Vector3 |
| `Vector2.new()` | Vector2 |
| `Color3.new()` | Color3 |
| `CFrame.new()` | CFrame |
| `UDim.new()` | UDim |
| `UDim2.new()` | UDim2 |
| `BrickColor.Red` | BrickColor |
| `Random.new()` | Random |
| `TweenInfo.new()` | TweenInfo |

## Luau's own values

| Value | What typeof returns |
| --- | --- |
| `nil` | nil |
| `true` | boolean |
| `42` | number |
| `"text"` | string |
| `{}` | table |
| a function | function |
| a coroutine thread | thread |
| a buffer | buffer |

`type` reports the same names for the built-ins and `userdata` for the engine's values, because underneath they are userdata. `typeof` is the one that tells them apart.

## Example

```lua
print(typeof(game))                  -- Instance
print(typeof(Enum.Material.Plastic)) -- EnumItem
print(typeof(task.wait))             -- function
print(typeof(workspace))             -- Instance
```

## See also

- [The Luau standard library](../scripting/luau.md): the rest of what the VM provides.
- [Instance](../globals/instance.md): the objects typeof reports as Instance.
- [API Reference](../api/api.md)
