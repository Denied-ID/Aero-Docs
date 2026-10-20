# Perf

Frame timings and per-script cost, written to the Output on demand.

## Methods

| Method | What it does |
| --- | --- |
| Report() | Writes the last frame's stage timings and the costliest scripts to the Output. |

## What a report holds

Both halves of a session can be measured. The server records its scripts, physics, and replication stages. The client records camera, client scripts, replication, and prediction. A Studio playtest runs a real server and a real client in one process, so one report shows both sides. A standalone server or client reports only its own half.

Per script, the report lists how many times it ran, its average cost, its worst single run, and its total. Time a script spends waiting does not count; only the time it spends running does. Runs that did not come from a Script, like the console, are listed separately.

Stage timings are wall-clock time for the last completed frame. Call Report again after a change to compare.

## Example

```lua
game:GetService("Perf"):Report()
```

## See also

- [API Reference](../api/api.md)
