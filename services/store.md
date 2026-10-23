# Store

Saves values with the place, on the server.

## Methods

| Method | What it does |
| --- | --- |
| Get(key) | Returns the value saved under `key`, or `nil` when the key has none. |
| Set(key, value) | Saves `value` under `key`. Passing `nil` deletes the key. |

`key` is a string. `value` can be a boolean, number, string, Vector3, CFrame, Color3, or a table of those. Tables cannot contain Instances, and the call raises an error if one does.

Call both methods from a Script. A LocalScript raises an error instead, because a client cannot read or write the save.

## Where values live

The values are stored beside the place file, in `town.aestore` next to `town.aepl`. They belong to that place, so copying the place with its sidecar carries its saved values along.

A change is written about two seconds after the last Set, and any pending change is written when the server shuts down. If a script keeps setting values, the store still writes at least every ten seconds. Get sees a value as soon as Set returns, before it reaches disk. A crash can lose up to ten seconds of changes, but never leaves a half-written file behind.

A playtest reads the place's saved values and writes to a temporary copy, so testing never changes the real save.

## Limits

| Limit | Value |
| --- | --- |
| Key length | 256 bytes |
| Keys per place | 4096 |
| File size | 16 MiB |

## Example

```lua
local store = game:GetService("Store")

local wins = store:Get("wins") or 0
store:Set("wins", wins + 1)

store:Set("inventory", { "sword", "torch" })
print(store:Get("inventory")[1])
```

## See also

- [Saving data](../guides/saving-data.md): loading on join and saving on change.
- [API Reference](../api/index.md)
