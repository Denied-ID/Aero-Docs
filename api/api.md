# API Overview

Everything you can use in Luau lives in the place tree. This section documents each class one page at a time. Many pages are still drafts. The lists below are complete and the details are catching up.

## Services

Services are always there. Ask for one by name:

```lua
local lighting = game:GetService("Lighting")
```

Workspace, Players, Lighting, ReplicatedStorage, ServerScriptService, StarterGui, StarterPack, StarterPlayer, SoundService, UserInputService, TweenService, RunService, CoreGui.

## Objects

Objects are things you add. Pick them from the Insert palette in Studio.

Parts and building: Part, MeshPart, Model, Folder.

Scripts: Script, LocalScript, ModuleScript.

Players and characters: Player, Humanoid.

Talking between client and server: RemoteEvent, RemoteFunction.

Interface: ScreenGui, Frame, TextLabel, TextButton, TextBox, ImageLabel, ScrollingFrame, UICorner, UIStroke, UIGradient.

Lights: PointLight, SpotLight, SurfaceLight.

Helpers: Tween, InputObject.

## Value types

Small values you pass around in scripts: Vector3, Vector2, CFrame, Color3, UDim2, BrickColor, Enum, Random, TweenInfo, and the task library. Each one gets its own page soon.
