# Vector2

A point on a flat surface, like a screen.

`Vector2` stores two numbers, x and y. Interface positions, mouse movement, and screen sizes use it.

## Creating one

| Call | Result |
| --- | --- |
| `Vector2.new()` | `(0, 0)` |
| `Vector2.new(x, y)` | The two values. Missing arguments count as 0. |
| `Vector2.zero` | `(0, 0)` |
| `Vector2.one` | `(1, 1)` |
| `Vector2.xAxis` | `(1, 0)` |
| `Vector2.yAxis` | `(0, 1)` |

## Members

This type accepts either case: `X` or `x`, `Magnitude` or `magnitude`.

| Member | Type | What it is |
| --- | --- | --- |
| X, Y | number | The components. |
| Magnitude | number | Length: the square root of `x*x + y*y`. |
| Unit | Vector2 | The same direction at length 1. A vector shorter than about `1e-8` gives `(0, 0)`. |

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| Dot(other) | number | Dot product. |
| Cross(other) | number | The 2D cross product: `x1*y2 - y1*x2`. Unlike [Vector3](vector3.md), this returns a number, not a vector. |
| Angle(other) | number | Angle between the two vectors, in radians. |
| Lerp(other, alpha) | Vector2 | Moves `alpha` of the way to `other`. Values outside 0 to 1 extrapolate. |
| Min(other) | Vector2 | The smaller of each pair of components. |
| Max(other) | Vector2 | The larger of each pair of components. |
| Abs() | Vector2 | Makes both components positive. |

## Operators

| Operator | Result |
| --- | --- |
| a + b, a - b | Component-wise sum or difference. |
| -a | Negates each component. |
| a * b | Component-wise product. |
| a * n, n * a | Scales each component. |
| a / b, a / n | Component-wise division, or division by a number. |
| a == b | True when both components are closer than `1e-4` to each other. |

Division by zero does not raise here. The affected component becomes infinity or NaN, which is easy to miss, so guard the divisor yourself.

## Example

```lua
local screen = Vector2.new(1280, 720)
local center = screen * 0.5
print(center)                          -- 640, 360

local move = Vector2.new(3, 4)
print(move.Magnitude)                  -- 5
print(move.Unit)                       -- 0.6, 0.8
```

## See also

- [Vector3](vector3.md): the 3D version.
- [UDim2](udim2.md): how interface sizes are written.
- [API Reference](../api/api.md)
