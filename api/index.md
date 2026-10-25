# API Reference

Everything Luau scripts can access. New to Aero? Start with [Get started](../getting-started/index.md).

## Classes

| Symbol | About |
| --- | --- |
| [Folder](../classes/folder.md) | A container that keeps the Explorer organized and can hold anything. |
| [Frame](../classes/frame.md) | A box that holds other interface objects. |
| [Humanoid](../classes/humanoid.md) | Makes a model walk, jump, and take damage. |
| [ImageLabel](../classes/imagelabel.md) | A picture on the screen. |
| [InputObject](../classes/inputobject.md) | What one input event carries. |
| [Kit](../classes/kit.md) | A named build that lives in the place. Copies sharing a `KitId` stay in sync while you edit. |
| [LocalScript](../classes/localscript.md) | Luau code that runs on each player's machine. |
| [MeshPart](../classes/meshpart.md) | A part whose shape comes from a mesh file. |
| [Model](../classes/model.md) | A group of parts you can name and handle as one. |
| [ModuleScript](../classes/modulescript.md) | Luau code that runs only when another script requires it. |
| [Part](../classes/part.md) | A solid object which is used as a basic building piece. |
| [Player](../classes/player.md) | One person in the game. |
| [PointLight](../classes/pointlight.md) | A light that shines in every direction from a point. |
| [RemoteEvent](../classes/remoteevent.md) | Sends values between the server and clients. |
| [RemoteFunction](../classes/remotefunction.md) | Calls the server from a client and waits for the answer. |
| [ScreenGui](../classes/screengui.md) | A layer of interface that covers the screen. |
| [Script](../classes/script.md) | Luau code that runs on the server. |
| [ScrollingFrame](../classes/scrollingframe.md) | A frame with a scrollable canvas inside it. |
| [SpotLight](../classes/spotlight.md) | A cone of light. |
| [SurfaceLight](../classes/surfacelight.md) | A cone of light from one face of a part. |
| [TextBox](../classes/textbox.md) | A field the player can type into. |
| [TextButton](../classes/textbutton.md) | A button with a text label on it. |
| [TextLabel](../classes/textlabel.md) | A line of text on the screen. |
| [Tween](../classes/tween.md) | One animated property change. |
| [UICorner](../classes/uicorner.md) | Rounds the corners of the interface object it sits in. |
| [UIGradient](../classes/uigradient.md) | Blends two colors across the interface object it sits in. |
| [UIStroke](../classes/uistroke.md) | Draws an outline around the interface object it sits in. |

## Services

| Symbol | About |
| --- | --- |
| [CoreGui](../services/coregui.md) | The engine's own interface. |
| [Kits](../services/kits.md) | A kit is a named build that lives in the place, and copies of one kit can stay linked. |
| [Lighting](../services/lighting.md) | Sun, sky, and atmosphere for the place. |
| [Perf](../services/perf.md) | Frame timings and per-script cost, written to the Output on demand. |
| [Players](../services/players.md) | Everyone connected, and the signals for joining and leaving. |
| [Physics](../services/physics.md) | What scripts do to the simulated world. |
| [ReplicatedStorage](../services/replicatedstorage.md) | Content both sides need. |
| [RunService](../services/runservice.md) | The engine's clock: signals for each step and queries about where the script is running. |
| [ServerScriptService](../services/serverscriptservice.md) | Server-only content. |
| [SoundService](../services/soundservice.md) | Settings for music and ambience. |
| [StarterGui](../services/startergui.md) | The interface every player starts with. |
| [StarterPack](../services/starterpack.md) | The contents every player's backpack starts with. |
| [StarterPlayer](../services/starterplayer.md) | Client-side content that runs where it sits. |
| [Store](../services/store.md) | Saves values with the place, on the server. |
| [TweenService](../services/tweenservice.md) | Animates properties smoothly over time. |
| [UserInputService](../services/userinputservice.md) | Keyboard and mouse input on the client. |
| [Workspace](../services/workspace.md) | The place world. |

## Functions

| Symbol | About |
| --- | --- |
| [print](../functions/print.md) | Writes a line to the Output panel. |
| [require](../functions/require.md) | Loads a ModuleScript and returns what it returned. |
| [task](../functions/task.md) | Pausing and scheduling for scripts. |
| [typeof](../functions/typeof.md) | Names the type of a value. |
| [warn](../functions/warn.md) | Writes a warning line to the Output panel. |

## Globals

| Symbol | About |
| --- | --- |
| [BrickColor](../globals/brickcolor.md) | A named color from the classic palette. |
| [CFrame](../globals/cframe.md) | A position plus a rotation in 3D. |
| [Color3](../globals/color3.md) | A color mixed from red, green, and blue. |
| [Enum](../globals/enum.md) | Named lists of options. |
| [game](../globals/game.md) | The root of the instance tree, and the way to reach every service. |
| [Instance](../globals/instance.md) | The base of every object, with Instance.new to create them. |
| [Random](../globals/random.md) | Random numbers with its own seed. |
| [TweenInfo](../globals/tweeninfo.md) | Timing settings for an animation. |
| [UDim](../globals/udim.md) | A length that scales with its parent, plus pixels. |
| [UDim2](../globals/udim2.md) | A screen position and size that survives resizing. |
| [Vector2](../globals/vector2.md) | A point on a flat surface, like a screen. |
| [Vector3](../globals/vector3.md) | A point or direction in 3D space. |
| [workspace](../globals/workspace.md) | Shortcut for the Workspace service. |

## Scripting

| Page | About |
| --- | --- |
| [The Luau standard library](../scripting/luau.md) | What the VM provides, on top of the engine's own API. |
