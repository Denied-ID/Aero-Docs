# TweenService

Animates properties smoothly over time.

`TweenService` builds [Tween](../classes/tween.md) objects. You describe the target, the timing, and the properties to change, then play the tween and let the engine move the values.

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| Create(target, info, properties) | Tween | Builds a tween but does not start it. |

`target` is the instance to animate, `info` is a [TweenInfo](../globals/tweeninfo.md), and `properties` is a table of property names and the values to reach.

## What can be tweened

Only three kinds of target animate: a [Part](../classes/part.md), a [Humanoid](../classes/humanoid.md), and the [SoundService](soundservice.md). `Create` accepts any instance, so a tween on a Frame or a Model runs, fires `Completed`, and moves nothing.

On those targets, four value types are interpolated:

| Value type | Example |
| --- | --- |
| number | `Transparency = 1` |
| Vector3 | `Position = Vector3.new(0, 10, 0)` |
| Color3 | `Color = Color3.fromRGB(255, 80, 80)` |
| CFrame | `CFrame = CFrame.new(0, 5, 0)` |

Any other value type is skipped without an error, so a property set to a boolean or an Instance simply does not move. Check that a tween changed something rather than assuming it did.

## Example

```lua
local TweenService = game:GetService("TweenService")

local door = workspace:FindFirstChild("Door")
local info = TweenInfo.new(1.2, Enum.EasingStyle.Quad, Enum.EasingDirection.InOut)

local close = TweenService:Create(door, info, {
    CFrame = door.CFrame * CFrame.new(0, 0, -4),
})

close.Completed:Connect(function (state)
    print("door finished", state.Name)
end)

close:Play()
```

## See also

- [Tween](../classes/tween.md): the object this service builds.
- [TweenInfo](../globals/tweeninfo.md): duration, easing, and repeats.
- [RunService](runservice.md): the clock the tween runs on.
- [API Reference](../api/index.md)
