# task

Pausing and scheduling for scripts.

The `task` library starts code on its own thread and controls when that thread runs. Every thread it creates belongs to the script that scheduled it, so `script` still points at the right instance and errors still report against it.

## Members

| Member | Call | What it does |
| --- | --- | --- |
| wait | `task.wait(seconds?)` | Pauses the current thread and returns the time that actually passed, in seconds. |
| spawn | `task.spawn(fn, ...)` | Starts `fn` right away on a new thread and returns that thread. |
| delay | `task.delay(seconds, fn, ...)` | Starts `fn` after `seconds`. The duration is required. |
| defer | `task.defer(fn, ...)` | Runs `fn` when the current step ends. |

## Waiting

`task.wait()` with no argument waits one frame, which is 1/60 of a second. A negative duration counts as zero, so it waits for the next frame instead of skipping ahead.

The return value is how long the wait really took, not the duration you asked for:

```lua
local elapsed = task.wait(2)
print(elapsed)    -- 2.01, or whatever the frame timing allowed
```

A zero wait still resumes on a later frame. Code never resumes in the middle of the step that yielded it.

## Scheduling

`task.spawn` runs the function before it returns, on a separate thread. The caller keeps going immediately after.

`task.delay` creates the thread at the call, but the function body does not start until the delay has passed. Arguments are captured at the call.

`task.defer` is for work that should happen after the current step. It is the safe choice when a function would be too early to run inside the step that scheduled it.

```lua
task.spawn(function ()
    print("runs first")
end)

task.defer(function ()
    print("runs when this step ends")
end)

print("runs second")
```

## See also

- [RunService](../services/runservice.md): signals that fire every step.
- [script](../classes/script.md): the instance a scheduled thread belongs to.
- [API Reference](../api/api.md)
