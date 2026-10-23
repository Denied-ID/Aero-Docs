# Testing your place

Play runs a real server and a real client inside Studio.

## The two starts

| Button | Key | What runs |
| --- | --- | --- |
| Play | F5 | The full pair: a server and one client, and you get a character to walk. |
| Run | F6 | The server half only. No character; server scripts still run. |

The pair is the real thing. The server half runs the same simulation a dedicated Aero server runs, and the client half sends input through the same networking a player's client uses, connected over a loopback this machine makes to itself.

In Play, the viewport shows the client's half: the world as your player receives it. In Run, it shows the server's tree.

## Snapshots and Reset

Both starts take a snapshot of the place first, so the place you edit is never the one being simulated. Reset (Shift+F5) ends the test and puts the place back exactly as it was; edits made during a test are discarded.

If the place has unsaved changes, Studio saves it before the test starts. That setting is on the Autosave page under Edit > Settings, and it is on by default.

## Pause and Step

Pause (F7) freezes the simulation. While paused, the viewport shows the server's half of the test, and Step (F8) advances the world by one frame.

## Both halves in one Output

Prints and errors from the two halves land in the same Output panel, so a server script and a client script can be watched together while the test runs.

For timings, one report covers both sides:

```lua
game:GetService("Perf"):Report()
```

The report names the server's scripts, physics, and replication stages, then the client's camera, scripts, replication, and prediction. See [Perf](../services/perf.md).

The [Store](../services/store.md) sidecar plays along too: a test reads the place's saved values and writes to a temporary copy, so playtesting never changes the real save.

## Where to go next

- [Perf](../services/perf.md): reading the report.
- [Troubleshooting](../guides/troubleshooting.md): when the test stops at a red line.
- [Studio Tour](../getting-started/studio-tour.md): the rest of the toolbar.
