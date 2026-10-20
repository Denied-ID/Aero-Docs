# ScreenGui

A layer of interface that covers the screen.

A `ScreenGui` is the root of an interface tree. Frames, labels, and buttons only draw when they sit under one. A client copies `ScreenGui` objects from StarterGui into its PlayerGui, and that copy is what the player sees.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| Enabled | boolean | Whether the layer draws at all. |
| DisplayOrder | number | Draw order between layers. Higher values draw above lower ones. |
| IgnoreGuiInset | boolean | Whether the layer draws over the top bar inset. |
| ResetOnSpawn | boolean | Whether the layer is dropped and rebuilt when the character respawns. Default true. |

## Members

ScreenGui also has every interface member listed on [Frame](frame.md), including position, size, and the mouse events. Its own `Position` and `Size` are ignored by layout, because the layer always covers the viewport.

It has the shared Instance members too; see [Instance](../globals/instance.md).

## Example

```lua
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui

local screen = Instance.new("ScreenGui")
screen.Name = "Hud"
screen.DisplayOrder = 10
screen.IgnoreGuiInset = true
screen.ResetOnSpawn = false
screen.Parent = playerGui

local label = Instance.new("TextLabel", screen)
label.Size = UDim2.new(0, 200, 0, 30)
label.Position = UDim2.new(0, 16, 0, 16)
label.BackgroundTransparency = 1
label.Text = "Ready"
```

## See also

- [Frame](frame.md): the container to put inside a layer.
- [StarterGui](../services/startergui.md): the template each player receives.
- [UDim2](../globals/udim2.md): sizes and positions.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
