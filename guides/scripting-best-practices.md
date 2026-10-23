# Scripting best practices

Habits that keep scripts quick to run and easy to fix.

## Name things for what they do

The Explorer name is a lookup key. Dot access, [FindFirstChild](../globals/instance.md), and the full path in an error message all use it, so a place with fourteen parts named Part is a place where `workspace.Door` is impossible. Scripts earn the same treatment: a script named GiveSpeed is a script you can find again in six weeks.

## Give one script one job

Server code for the round, client code for the interface, shared code in a [ModuleScript](../classes/modulescript.md) under [ReplicatedStorage](../services/replicatedstorage.md). A module returns its value once and every later [require](../functions/require.md) gets the cached copy, so two scripts that require the same module work with the same table. A module must return something, and two modules that require each other fail on the spot.

## Reach things once, at the top

Take every service in the first lines and find every object before the work starts. [WaitForChild](../globals/instance.md) is the tool for objects that may still be arriving: replication is still moving when a client script starts, and reaching through a nil stops the script with an error. Inside work that runs every frame, hoist the lookup out of the loop.

## React, do not poll

The engine tells a script when things happen. `ChildAdded` when something arrives, [Died](../classes/humanoid.md) when a character dies, [Heartbeat](../services/runservice.md) once per frame. A loop that re-reads the tree looking for changes duplicates what a Connect already does, and pays for it every frame. Save the per-frame signals for work that genuinely needs each frame, like reading held keys.

## Disconnect what you are done with

A connection keeps its callback alive for every fire after the reason for it is gone. Call [Disconnect](../globals/instance.md) on it, which is safe to call twice, and read the `Connected` flag when the state matters. Destroy goes further and disconnects everything under the object it removes.

## Yield on purpose

A script that runs without yielding past five seconds is stopped with `Script exceeded its run budget`. [task.wait](../functions/task.md) hands control back and starts a fresh budget on resume, and even a zero wait resumes on a later frame. `task.delay` takes its duration, `task.defer` runs when the current step ends, and `task.spawn` starts a function on its own thread right away. What task.wait returns is the time that really passed, not the time you asked for.

## Treat remote arguments as suggestions

OnServerEvent hands the server the player, and the player is the one part of the message the engine guarantees. Everything after it is whatever the sending client chose to put there. Check types and ranges before acting, and keep the decisions on the server: a [remote](../classes/remoteevent.md) carries data, not authority.

## Wrap the calls that can raise

[Set](../services/store.md) raises on a table holding an Instance, and require raises when a module returned nothing. A payload that arrived over a remote is exactly the kind that can carry one, so wrap the write and branch on the result:

```lua
local ok = pcall(function ()
    store:Set(player.UserId .. ":wins", payload)
end)

if not ok then
    warn("rejected a save from", player.Name)
end
```

## Measure before you tune

[Perf](../services/perf.md) writes the last frame's stage timings, and per script how many times it ran, its average cost, its worst run, and its total. Time spent waiting does not count. Call Report again after a change and compare the two outputs rather than guessing. The debug library is removed from the VM, so the report is the way in.

## Read the earliest red line

A test stops at the first error, and every error after it is suspect until that one is fixed. Both halves print into the same Output, so fix the earliest red line, run again, and let the next one surface.

## See also

- [Client and server](client-and-server.md): the two halves these habits sit on.
- [Instance](../globals/instance.md): signals, connections, and the shared methods.
- [task](../functions/task.md): yielding and scheduling.
- [The Luau standard library](../scripting/luau.md): the run budget and the removed libraries.
- [Perf](../services/perf.md): the report.
- [API Reference](../api/index.md)
