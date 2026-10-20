# BrickColor

A named color from the classic palette.

A `BrickColor` stores a palette number, not a freely mixed color. The palette has 158 entries, the classic block-derived colors plus a few extra ranges. Use it when you want a color that matches the parts already in a place, or when a stored number is easier to pass around than three channels.

## Creating one

| Call | Result |
| --- | --- |
| `BrickColor.new("Bright red")` | The entry with that exact name. The name is case-sensitive. |
| `BrickColor.new(21)` | The entry with that palette number. |
| `BrickColor.new(Color3.new(1, 0, 0))` | The nearest palette color to the given Color3. |
| `BrickColor.new(1, 0, 0)` | The nearest palette color to three channels from 0 to 1. |

An unknown name raises `NotAColor is not a valid BrickColor name`. An unknown number is not an error: it resolves to 194, Medium stone grey.

The three-number form takes channels from 0 to 1, the same range as [Color3](color3.md), not 0 to 255.

## Palette members

These constants return commonly used entries:

| Constant | Palette number | Name |
| --- | --- | --- |
| BrickColor.White() | 1 | White |
| BrickColor.Gray() | 194 | Medium stone grey |
| BrickColor.DarkGray() | 199 | Dark stone grey |
| BrickColor.Black() | 26 | Black |
| BrickColor.Red() | 21 | Bright red |
| BrickColor.Yellow() | 24 | Bright yellow |
| BrickColor.Green() | 28 | Dark green |
| BrickColor.Blue() | 23 | Bright blue |

`BrickColor.Green()` really is Dark green. The name was kept when the palette was matched, and Bright green has a different number.

`BrickColor.Random()` returns a random entry from the palette. Its generator is separate from `math.random` and from any [Random](random.md) you create.

## Members

| Member | Type | What it is |
| --- | --- | --- |
| Number | number | The palette number. |
| Name | string | The palette name, such as `Bright red`. |
| Color | Color3 | The same color as channels from 0 to 1. |
| r, g, b | number | Shortcuts for the three channels of `Color`. |

The members are read-only.

## Comparing them

Two BrickColors are equal when their palette numbers match. The palette contains a few colors that share the same channels under different names. Those are different BrickColors and compare unequal, which is what lets a place keep its names straight.

Printing one gives its name.

## Example

```lua
local brick = BrickColor.new("Bright red")
print(brick.Name)       -- Bright red
print(brick.Number)     -- 21
print(brick.Color)      -- 1, 0, 0

local grey = BrickColor.new(9999)
print(grey.Name)        -- Medium stone grey
```

## See also

- [Color3](color3.md): colors mixed from channels.
- [Part](../classes/part.md): the usual place a BrickColor ends up.
- [API Reference](../api/api.md)
