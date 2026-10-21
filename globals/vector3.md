# Vector3

A point or direction in 3D space.

`Vector3` stores three numbers: x, y, and z. Positions, sizes, directions, and velocities all use it. In the world, the units are studs.

## Creating one

| Call | Result |
| --- | --- |
| `Vector3.new()` | `(0, 0, 0)` |
| `Vector3.new(x, y, z)` | The three values. Missing arguments count as 0. |
| `Vector3.zero` | `(0, 0, 0)` |
| `Vector3.one` | `(1, 1, 1)` |

## Members

The components are read-only. This type accepts capitalized names only: `X`, `Y`, and `Z`, not `x`, `y`, and `z`.

| Member | Type | What it is |
| --- | --- | --- |
| X, Y, Z | number | The components. |
| Magnitude | number | Length: the square root of `x*x + y*y + z*z`. |
| Unit | Vector3 | The same direction at length 1. A zero vector gives `(0, 0, 0)`. |

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| Dot(other) | number | Dot product of the two vectors. |
| Cross(other) | Vector3 | Cross product of the two vectors. |
| Lerp(other, alpha) | Vector3 | Moves `alpha` of the way from this vector to `other`. Values outside 0 to 1 extrapolate. |

## Operators

| Operator | Result |
| --- | --- |
| a + b, a - b | Component-wise sum or difference. |
| -a | Negates each component. |
| a * n, n * a | Scales each component by the number. |
| a / n | Divides each component by the number. Dividing by zero raises an error. |
| a == b | True only when all three components are exactly equal. |

Multiplication needs a number on one side. `Vector3 * Vector3` raises an error, so use `Dot` or `Cross` when you mean those.

Equality is exact, with no tolerance. Two vectors that should match can compare false if they arrived by different arithmetic, so compare `(a - b).Magnitude` against a small number when that matters.

## Example

```lua
local origin = Vector3.new(0, 10, 0)
local target = Vector3.new(30, 10, 0)

local offset = target - origin
print(offset.Magnitude)    -- 30
print(offset.Unit)         -- 1, 0, 0
print(offset:Dot(Vector3.one))  -- 30
```

## See also

- [CFrame](cframe.md): a position plus a rotation.
- [Vector2](vector2.md): the flat version.
- [API Reference](../api/index.md)
