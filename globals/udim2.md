# UDim2

A screen position and size that survives resizing.

`UDim2` holds a [UDim](udim.md) for the X axis and one for the Y axis. Each part is a fraction of the parent plus a pixel count, so an interface element can sit at 50 percent of the screen and stay there when the window changes size.

## Creating one

| Call | Result |
| --- | --- |
| `UDim2.new()` | All four numbers are 0. |
| `UDim2.new(xScale, xOffset, yScale, yOffset)` | One call with all four numbers. Missing arguments count as 0. |
| `UDim2.new(x, y)` | Two UDim values, one per axis. |
| `UDim2.fromScale(x, y)` | Scale only, offsets 0. |
| `UDim2.fromOffset(x, y)` | Offsets only, scale 0. |

The two-UDim form only applies when both arguments are UDim values. Passing a single UDim, or a UDim next to a number, falls through to the four-number form and raises a type error.

## Members

| Member | Type | What it is |
| --- | --- | --- |
| X | UDim | The horizontal part. `Width` is an alias. |
| Y | UDim | The vertical part. `Height` is an alias. |

Both members are read-only. Read the numbers through them, as in `size.X.Scale`.

## Operators

| Operator | Result |
| --- | --- |
| a + b, a - b | Adds or subtracts each of the four numbers. Both sides must be UDim2. |
| -a | Negates all four numbers. |
| a * n, n * a | Multiplies the scale of each axis. Offsets are left alone. |
| a == b | True when all four numbers are within `1e-4`. |

The multiplication rule differs from UDim, where a number scales both the scale and the offset. There is no division operator.

## Example

```lua
local size = UDim2.new(0.5, 0, 0, 48)
print(size)             -- {0.5, 0}, {0, 48}

local half = size * 0.5
print(half)             -- {0.25, 0}, {0, 48}

local centered = UDim2.new(0.5, 0, 0.5, 0)
print(centered.X.Scale) -- 0.5
```

## See also

- [UDim](udim.md): one axis on its own.
- [Frame](../classes/frame.md): an object placed with UDim2.
- [API Reference](../api/api.md)
