# Perf

Frame timings and per-script cost, written to the Output on demand.

## Methods

| Method | What it does |
| --- | --- |
| Report() | Writes the last frame's stage timings and the costliest scripts to the Output. |
| StageSeconds(stage) | Returns the last completed frame's seconds for one `stage`. Valid names for the `stage` parameter are `Camera`, `Physics`, `Prediction`, `ClientScripts`, `Replication`, and `Scripts`. |
| ScriptCost(name) | Returns one script's cost as a table with `Runs`, `AverageSeconds`, `WorstSeconds`, and `TotalSeconds`. `name` is the script's full path, or `Unattributed` for runs that did not come from a script. |

## What a report holds

Both halves of a session can be measured. The server records its scripts, physics, and replication stages. The client records camera, client scripts, replication, and prediction. A Studio playtest runs a real server and a real client in one process, so one report shows both sides. A standalone server or client reports only its own half.

Per script, the report lists how many times it ran, its average cost, its worst single run, and its total. Time a script spends waiting does not count; only the time it spends running does. Runs that did not come from a Script, like the console, are listed separately.

Stage timings are wall-clock time for the last completed frame. Call Report again after a change to compare.

`StageSeconds` and `ScriptCost` read the same numbers, so a script can react to them while the game runs. The cost table carries `Runs`, `AverageSeconds`, `WorstSeconds`, and `TotalSeconds`.

```lua
local Perf = game:GetService("Perf")

if Perf:StageSeconds("Physics") > 0.01 then
    -- This is a slow frame! Stop spawning debris until it recovers.
end
```

## Example

```lua
game:GetService("Perf"):Report()
```

## See also

- [Testing your place](../tutorials/testing-your-place.md): the playtest pair the report measures.
- [API Reference](../api/index.md)
