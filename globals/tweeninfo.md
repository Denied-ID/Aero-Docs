# TweenInfo

Timing settings for an animation.

`TweenInfo` describes how a [TweenService](../services/tweenservice.md) animation should run: how long it lasts, how it eases, how many times it repeats, and how long it waits first.

## Creating one

```lua
TweenInfo.new(time, easingStyle, easingDirection, repeatCount, reverses, delayTime)
```

Every argument is optional.

| Argument | Type | Default | What it means |
| --- | --- | --- | --- |
| time | number | 1 | How long one run lasts, in seconds. |
| easingStyle | Enum.EasingStyle | Quad | The shape of the speed curve. |
| easingDirection | Enum.EasingDirection | Out | Which end of the curve the easing applies to. |
| repeatCount | number | 0 | How many extra runs follow the first. 0 plays once, and a negative number repeats forever. |
| reverses | boolean | false | Whether each repeat plays backward. |
| delayTime | number | 0 | Seconds to wait before the first run. |

The two easing arguments accept an enum item, a plain number, or the item's name as a string:

```lua
TweenInfo.new(2, Enum.EasingStyle.Bounce)
TweenInfo.new(2, "Bounce")
TweenInfo.new(2, 6)
```

All three forms above mean the same thing.

A value that does not fit is quietly replaced by the default instead of raising an error. That covers an unknown style name, an enum item from a different enum, and a non-boolean value for `reverses`, such as `1` or `"true"`.

## Members

| Member | Type | What it is |
| --- | --- | --- |
| Time | number | The duration in seconds. |
| EasingStyle | Enum.EasingStyle | The easing shape. |
| EasingDirection | Enum.EasingDirection | The easing direction. |
| RepeatCount | number | Extra runs after the first. Negative repeats forever. |
| Reverses | boolean | Whether repeats alternate direction. |
| DelayTime | number | Seconds before the first run. |

All members are read-only. Assigning to one raises an error from the VM rather than a message from the binding.

## Example

```lua
local info = TweenInfo.new(
    0.4,                        -- seconds
    Enum.EasingStyle.Quad,
    Enum.EasingDirection.Out,
    0,                          -- play once
    false,
    0.1                         -- wait a tenth of a second
)

print(info.Time)                -- 0.4
print(info.RepeatCount)         -- 0
print(info.EasingStyle.Name)    -- Quad
```

## See also

- [TweenService](../services/tweenservice.md): where a TweenInfo is used.
- [Tween](../classes/tween.md): the animation object it configures.
- [Enum](enum.md): the easing lists.
- [API Reference](../api/index.md)
