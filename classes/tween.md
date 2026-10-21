# Tween

One animated property change.

A `Tween` is built by [TweenService](../services/tweenservice.md) and then played. It holds the target object, the timing, and the property values to move toward, and it reports when it finishes.

## Members

| Member | Type | What it does |
| --- | --- | --- |
| Instance | Instance or nil | The object being animated. Read-only. |
| TweenInfo | TweenInfo | The timing settings it was built with. Read-only. |
| PlaybackState | Enum.PlaybackState | Where the animation is now. Read-only. |
| Completed | event | Fires with the final PlaybackState. |

## Methods

`Play`, `Pause`, and `Cancel` come from the shared method list and only work on a Tween.

| Method | What it does |
| --- | --- |
| Play() | Starts the tween, or resumes it after a pause. |
| Pause() | Holds the tween where it is. |
| Cancel() | Stops the tween and leaves the property at its current value. |

## Example

```lua
local TweenService = game:GetService("TweenService")

local lamp = Instance.new("Part")
lamp.Name = "Lamp"
lamp.Anchored = true
lamp.Position = Vector3.new(0, 8, 0)
lamp.Parent = workspace

local tween = TweenService:Create(
    lamp,
    TweenInfo.new(0.8, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
    { Color = Color3.fromRGB(255, 90, 90) }
)

tween.Completed:Connect(function (state)
    print("finished", state.Name)
end)

tween:Play()
```

## See also

- [TweenService](../services/tweenservice.md): builds a tween.
- [TweenInfo](../globals/tweeninfo.md): the timing settings.
- [Enum](../globals/enum.md): the PlaybackState list.
- [API Reference](../api/index.md)
