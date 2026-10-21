# Color3

A color mixed from red, green, and blue.

Each channel is a number from 0 to 1. `Color3` is used anywhere a color is set: parts, lights, interface objects, and effects.

## Creating one

| Call | Result |
| --- | --- |
| `Color3.new()` | Black. Every missing argument counts as 0. |
| `Color3.new(r, g, b)` | The raw channel values. They are not clamped. |
| `Color3.fromRGB(r, g, b)` | Channels given from 0 to 255, stored from 0 to 1. Values outside the range are clamped. |
| `Color3.fromHSV(h, s, v)` | Built from hue, saturation, and value. All three arguments are required. |
| `Color3.fromHex("#ff8800")` | Built from a hex string. |

`fromRGB` treats a missing argument as 0, so `Color3.fromRGB()` is black. A non-finite channel such as NaN becomes white.

`fromHSV` wraps the hue into the 0 to 1 range, so negative hues work. Saturation and value are clamped. A saturation of 0 or less gives a grey.

`fromHex` accepts an optional leading `#` and needs exactly six hex digits. A malformed string does not raise: it returns white. That makes a typo in a color constant look like a deliberate white, so check the result if the color matters.

## Members

| Member | Type | What it is |
| --- | --- | --- |
| R, G, B | number | The channels from 0 to 1. Lowercase `r`, `g`, and `b` also work. |

The channels are read-only.

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| Lerp(other, alpha) | Color3 | Mixes toward `other`. Values outside 0 to 1 extrapolate. |
| ToHSV() | 3 numbers | Hue, saturation, and value. Hue is in the 0 to 1 range. |
| ToHex() | string | Six lowercase hex digits with no `#`, such as `ff8800`. |

## Operators

| Operator | Result |
| --- | --- |
| a + b, a - b | Component-wise. Results are not clamped. |
| a * b | Component-wise product. |
| a * n, n * a | Scales each channel by the number. |
| a / n | Divides each channel by the number. |
| a == b | True when every channel is closer than `1e-4`. |

There is no division between two colors, and dividing by zero does not raise. The channel becomes infinity or NaN instead.

## Example

```lua
local orange = Color3.fromRGB(255, 136, 0)
print(orange)              -- 1, 0.533333, 0
print(orange:ToHex())      -- ff8800

local faded = orange:Lerp(Color3.new(1, 1, 1), 0.5)
print(faded:ToHex())       -- ffc480
```

## See also

- [BrickColor](brickcolor.md): a color picked from a fixed palette.
- [Part](../classes/part.md): where a color usually goes.
- [API Reference](../api/index.md)
