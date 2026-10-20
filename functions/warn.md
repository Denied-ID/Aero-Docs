# warn

Writes a warning line to the Output panel.

`warn` joins its arguments the same way `print` does, then puts `Warn: ` in front of the line. The prefix is part of the message text, so it still shows up in logs that cannot color the output.

## Signature

| Call | Returns |
| --- | --- |
| `warn(...)` | nothing |

## Example

```lua
local target = workspace:FindFirstChild("Door")

if not target then
    warn("Door is missing from the workspace")
end
```

The Output panel shows `Warn: Door is missing from the workspace`.

## See also

- [print](print.md): the plain output call.
- [Troubleshooting](../getting-started/troubleshooting.md): what to do with the errors you find.
- [API Reference](../api/api.md)
