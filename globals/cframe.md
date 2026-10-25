# CFrame

A position plus a rotation in 3D.

A `CFrame` holds a position and a 3x3 rotation matrix. It is how parts, cameras, and attachment points are placed, and how you move a point from one object's space into another's. All angles are in radians.

## Creating one

`CFrame.new` reads its arguments by count:

| Arguments | Result |
| --- | --- |
| none | The identity frame: position `(0, 0, 0)`, no rotation. |
| 1 Vector3 | That position, no rotation. |
| 2 Vector3 | `eye` and `target`: a frame at `eye` looking at `target`. |
| 3 numbers | `x, y, z`, no rotation. |
| 7 numbers | `x, y, z, qx, qy, qz, qw`: position plus quaternion rotation. |
| 12 or more numbers | `x, y, z` then the nine matrix values in row order. Extra arguments are ignored. |

Any other count raises `invalid argument count to CFrame.new (5)`, with the actual count in the message.

The other constructors live on the `CFrame` table:

| Constructor | What it makes |
| --- | --- |
| `CFrame.identity` | The identity frame, as a constant rather than a call. |
| `CFrame.Angles(rx, ry, rz)` | A rotation, applied in X, then Y, then Z order. |
| `CFrame.fromEulerAnglesXYZ(rx, ry, rz)` | The same as `CFrame.Angles`. |
| `CFrame.fromEulerAnglesYXZ(rx, ry, rz)` | A rotation in Y, then X, then Z order. |
| `CFrame.fromOrientation(rx, ry, rz)` | The same as `fromEulerAnglesYXZ`. |
| `CFrame.fromAxisAngle(axis, angle)` | A rotation of `angle` around `axis`. |
| `CFrame.fromMatrix(position, right, up, back?)` | A frame from three axes. `back` is the third column, so the frame looks along its negation. It defaults to the cross product of `right` and `up`. |
| `CFrame.lookAt(eye, target, up?)` | A frame at `eye` facing `target`. `up` defaults to `(0, 1, 0)`. |

## Members

| Member | Type | What it does |
| --- | --- | --- |
| X, Y, Z | number | The position components. |
| Position | Vector3 | The position. `p` is a shorter alias. |
| LookVector | Vector3 | The direction the frame faces. This is the negated third column of the matrix, so an unrotated frame looks along `(0, 0, -1)`. |
| RightVector | Vector3 | The frame's right side. First matrix column. |
| UpVector | Vector3 | The frame's up side. Second matrix column. |
| Rotation | CFrame | A copy with the position set to zero and the rotation kept. |
| R00 to R22 | number | The nine matrix values, by row and column. |

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| Inverse() | CFrame | The opposite transform, which undoes this one. |
| Lerp(goal, alpha) | CFrame | Slides the position and slerps the rotation toward `goal`. `alpha` is not clamped. |
| GetComponents() | 12 numbers | `x, y, z` then the nine matrix values. |
| ToEulerAnglesXYZ() | 3 numbers | Rotation as X, Y, Z angles in radians. |
| ToEulerAnglesYXZ() | 3 numbers | Rotation as Y, X, Z angles in radians. `ToOrientation()` is the same function. |
| ToAxisAngle() | Vector3, number | An axis and an angle in radians. |
| PointToWorldSpace(point) | Vector3 | Moves a point from this frame's space into world space. |
| PointToObjectSpace(point) | Vector3 | Moves a world point into this frame's space. |
| VectorToWorldSpace(direction) | Vector3 | Rotates a direction into world space, without moving it by the position. |
| VectorToObjectSpace(direction) | Vector3 | Rotates a world direction into this frame's space. |
| ToWorldSpace(cf) | CFrame | `self * cf`. |
| ToObjectSpace(cf) | CFrame | `self:Inverse() * cf`. |

## Operators

| Operator | Result |
| --- | --- |
| a * b | Combines two frames. The position becomes `a.Position + a.Rotation * b.Position`, and the rotation becomes `a.Rotation * b.Rotation`. |
| a * v | Moves the point `v` into world space, including the position. Same as `PointToWorldSpace`. |
| a + v, a - v | Moves the position by the Vector3 `v` and keeps the rotation. |
| a == b | True when all twelve values are closer than `1e-5`. |

`CFrame + CFrame` raises an error, and so does `Vector3 * CFrame`. There is no division operator.

Combining frames reads right to left in effect: in `a * b`, a point is first moved by `b`, then by `a`. This makes `a * b` the right way to place a child in a parent's space.

## Rotation order

`CFrame.Angles` and `CFrame.fromOrientation` both take three angles, but they apply them in a different order. A frame built with `Angles(10, 20, 30)` is not the same as one built with `fromOrientation(10, 20, 30)`.

Use `Angles` when you have X, Y, Z angles from a tool that lists them that way. Use `fromOrientation` when you have heading, pitch, and roll, because it applies the Y rotation first.

## Example

```lua
local base = CFrame.new(0, 5, 0)
local door = base * CFrame.Angles(0, math.rad(90), 0)

print(door.Position)      -- 0, 5, 0
print(door.LookVector)    -- -1, 0, 4.37114e-08

local hinge = door * Vector3.new(0, 0, -3)
print(hinge.X, hinge.Y, hinge.Z)   -- -3, 5, 1.31134e-07
```

The near-zero values are what 90 degrees comes out as in single precision. Use `math.rad(90)` for reading, and compare frames with `==` rather than exact component values.

## See also

- [Vector3](vector3.md): points and directions.
- [Part](../classes/part.md): the object most CFrames describe.
- [API Reference](../api/index.md)
