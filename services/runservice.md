?# RunService

The engine's clock: signals for each step and queries about where the script is running.

`RunService` is how a script does something every frame, and how it asks whether it is on the server or a client.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| TimeScale | number | Multiplies the simulation step. 0.1-4, default 1. Saved with the place. |
| Paused | boolean | Stops the simulation step and script scheduling together. |
| UptimeSeconds | number | Read-only seconds since the world started. |
| FrameCount | number | Read-only frames since the world started. |

## Events

| Event | Callback arguments | When it fires |
| --- | --- | --- |
| PreSimulation | deltaTime | First of the frame's script signals. State you change here is what the rest of the frame reads. |
| Stepped | time, deltaTime | Second. `time` is the world clock in seconds since the place started; `deltaTime` is this frame's step. |
| Heartbeat | deltaTime | The main once-per-frame tick for game logic. |
| PostSimulation | deltaTime | Last of the four, so reads here see every change made this frame. |
| RenderStepped | deltaTime | On a client, just before the frame is drawn. |

The first four run in that order once per frame, after the physics steps. `RenderStepped` fires on a client only.

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| IsServer() | boolean | True on a server: the playtest server in Studio or a dedicated server. |
| IsClient() | boolean | True on a client: the playtest client in Studio or the Aero Client. |
| IsStudio() | boolean | True inside Studio: while editing and during a playtest. |
| BindToRenderStep(name, priority, callback) | nothing | Calls `callback(deltaTime)` before each rendered frame. |
| UnbindFromRenderStep(name) | nothing | Removes the binding with that name. |

`BindToRenderStep` is client-only, like `RenderStepped`. Binding the same name again replaces the earlier callback. The priority argument is accepted and has no effect.

While you edit a place, IsStudio is true and IsServer and IsClient are false.

## Example

```lua
local RunService = game:GetService("RunService")

print(RunService:IsServer(), RunService:IsClient())

RunService.Heartbeat:Connect(function (deltaTime)
    -- Runs once per step on both sides.
end)

if RunService:IsClient() then
    RunService:BindToRenderStep("Hud", Enum.RenderPriority.Last.Value, function (deltaTime)
        -- Runs before the camera moves this frame.
    end)
end
```

## See also

- [task](../functions/task.md): scheduling without a per-frame signal.
- [TweenService](tweenservice.md): animation that runs off the same clock.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/index.md)
