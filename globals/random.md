# Random

Random numbers with its own seed.

`Random.new` returns a generator that you hold and pass around. Two generators do not share a stream, so seeding one does not affect another, and nothing here touches `math.random`.

## Creating one

| Call | Result |
| --- | --- |
| `Random.new()` | A generator seeded from the clock, so two calls give different streams. |
| `Random.new(seed)` | A generator that always produces the same sequence for the same seed. |

The seed can be any number, including a fraction. Its bits are mixed into the starting state, so `0.5` and `2` give unrelated sequences. The same seed produces the same sequence on every build of the engine, which makes a seed safe to store in a save file.

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| NextNumber() | number | A number from 0 up to, but not including, 1. |
| NextNumber(min, max) | number | A number from `min` up to, but not including, `max`. |
| NextInteger(min, max) | number | A whole number from `min` to `max`, with both ends included. |
| NextUnitVector() | Vector3 | A direction on the unit sphere, evenly spread. |
| Clone() | Random | A second generator with the same state. Both then produce the same numbers. |
| Shuffle(table) | nothing | Reorders the array part of the table in place. |

`NextNumber(min, max)` needs both bounds. Calling it with one bound raises an argument error.

`NextInteger` requires whole numbers within about 9 quadrillion of zero, and `max` must not be less than `min`. Both ends are reachable, which makes it the call for dice and indexes.

`Shuffle` only touches the numbered part of the table. String keys are left where they are. A seeded shuffle of `n` items always consumes `n - 1` numbers, so the result is reproducible.

## Example

```lua
local rng = Random.new(1234)

print(rng:NextNumber())         -- 0 up to 1
print(rng:NextInteger(1, 6))    -- 1 to 6, both ends included

local deck = {"Ace", "King", "Queen", "Jack"}
rng:Shuffle(deck)

for _, card in deck do
    print(card)
end
```

## See also

- [BrickColor](brickcolor.md): a palette with its own random picker.
- [Vector3](vector3.md): what `NextUnitVector` returns.
- [API Reference](../api/index.md)
