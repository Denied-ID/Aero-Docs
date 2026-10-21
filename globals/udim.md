# UDim

A length that scales with its parent, plus pixels.

A `UDim` holds two numbers: a scale, which is a fraction of the parent's size, and an offset, which is a fixed number of pixels. The final length is `scale * parentSize + offset`.

Most interface code uses [UDim2](udim2.md), which holds a `UDim` for each axis. Use `UDim` alone when a single length is enough, such as a corner radius.

## Creating one

| Call | Result |
| --- | --- |
| `UDim.new()` | `0` scale, `0` offset. |
| `UDim.new(scale, offset)` | The two values. Missing arguments count as 0. |

## Members

| Member | Type | What it is |
| --- | --- | --- |
| Scale | number | The fraction of the parent's size. |
| Offset | number | The pixels added after the scale. |

Both members are read-only.

## Operators

| Operator | Result |
| --- | --- |
| a + b, a - b | Adds or subtracts scale and offset separately. |
| a * n, n * a | Multiplies both the scale and the offset. |
| a == b | True when both parts are closer than `1e-4`. |

There is no unary minus and no division. To subtract a UDim, subtract it.

## Example

```lua
local padding = UDim.new(0.05, 8)
print(padding)    -- {0.05, 8}

local doubled = padding * 2
print(doubled)    -- {0.1, 16}
```

## See also

- [UDim2](udim2.md): a UDim for each axis.
- [API Reference](../api/index.md)
