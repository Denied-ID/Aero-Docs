# print

Writes a line to the Output panel.

`print` converts each argument with `tostring`, joins the results with tabs, and writes one line. An Instance converts to its name, so printing a part tells you which one a variable holds.

## Signature

| Call | Returns |
| --- | --- |
| `print(...)` | nothing |

Any number of arguments is allowed, including none. There is no formatting step: tabs separate the values and a newline ends the line.

## Example

```lua
print("Loaded", 12, "parts")

local crate = Instance.new("Part")
crate.Name = "Crate"
print(crate)                 -- Crate
```

## See also

- [warn](warn.md): the same output with a warning label.
- [Perf](../services/perf.md): timings written to the Output.
- [API Reference](../api/api.md)
