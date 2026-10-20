# ImageLabel

A picture on the screen.

An `ImageLabel` draws an image inside the bounds of a [Frame](frame.md). It has every Frame member and four settings of its own.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| Image | string | Path to the image file, relative to the working directory. |
| ImageColor3 | Color3 | Tints the image. White leaves it unchanged. |
| ImageTransparency | number | 0 is solid, 1 is invisible. |
| ScaleType | number | 0 stretches the image to the frame, 1 fits it inside. |

Images are file paths, not asset ids.

## Members

ImageLabel has every [Frame](frame.md) member, plus the shared Instance members in [Instance](../globals/instance.md). It has no methods of its own.

## Example

```lua
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui

local screen = Instance.new("ScreenGui")
screen.Name = "Hud"
screen.Parent = playerGui

local icon = Instance.new("ImageLabel", screen)
icon.Size = UDim2.new(0, 64, 0, 64)
icon.Position = UDim2.new(0, 16, 0, 16)
icon.BackgroundTransparency = 1
icon.Image = "content/ui/coin.png"
icon.ScaleType = 1
icon.ImageColor3 = Color3.fromRGB(255, 220, 90)
```

## See also

- [Frame](frame.md): the members this class starts from.
- [TextLabel](textlabel.md): text instead of a picture.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
