# API Reference

Everything Luau scripts can access. New to Aero? Start with the [guides](../guides/index.md).

## Classes

| Symbol | About |
| --- | --- |
| [Folder](../classes/folder.md) | A container that keeps the Explorer organized. |
| [Frame](../classes/frame.md) | A box that holds other interface objects. |
| [Humanoid](../classes/humanoid.md) | Moves a character: walking, jumping, and dying. |
| [ImageLabel](../classes/imagelabel.md) | A picture on the screen. |
| [InputObject](../classes/inputobject.md) | Describes one input, like a key press. |
| [Kit](../classes/kit.md) | A named build; linked copies stay in sync while you edit. |
| [LocalScript](../classes/localscript.md) | Luau code that runs on each player's machine. |
| [MeshPart](../classes/meshpart.md) | A part that uses a custom mesh shape. |
| [Model](../classes/model.md) | A group of parts you can handle as one. |
| [ModuleScript](../classes/modulescript.md) | Luau code that runs only when required. |
| [Part](../classes/part.md) | A solid block, and the basic building piece. |
| [Player](../classes/player.md) | One person in the game. |
| [PointLight](../classes/pointlight.md) | Light that shines in all directions from one point. |
| [RemoteEvent](../classes/remoteevent.md) | Sends messages between the server and clients. |
| [RemoteFunction](../classes/remotefunction.md) | Asks the server a question and waits for the answer. |
| [ScreenGui](../classes/screengui.md) | A screen interface. Holds buttons and labels. |
| [Script](../classes/script.md) | Luau code that runs on the server. |
| [ScrollingFrame](../classes/scrollingframe.md) | A frame with a scrollable canvas inside it. |
| [SpotLight](../classes/spotlight.md) | Light that shines in one direction, like a flashlight. |
| [SurfaceLight](../classes/surfacelight.md) | Light that shines off one face of a part. |
| [TextBox](../classes/textbox.md) | A box players can type into. |
| [TextButton](../classes/textbutton.md) | A button with text that players can press. |
| [TextLabel](../classes/textlabel.md) | Text on the screen. |
| [Tween](../classes/tween.md) | One animation played through TweenService. |
| [UICorner](../classes/uicorner.md) | Rounds the corners of interface objects. |
| [UIGradient](../classes/uigradient.md) | Blends colors across interface objects. |
| [UIStroke](../classes/uistroke.md) | Draws an outline around interface objects. |

## Services

| Symbol | About |
| --- | --- |
| [CoreGui](../services/coregui.md) | The engine's own interface, such as chat and the player list. |
| [Kits](../services/kits.md) | Named builds that live in the place; copies can stay linked. |
| [Lighting](../services/lighting.md) | Sun, sky, and atmosphere for the place. |
| [Perf](../services/perf.md) | Frame timings and per-script cost, written to the Output. |
| [Players](../services/players.md) | Everyone connected, with the signals for joining and leaving. |
| [Physics](../services/physics.md) | What scripts do to the simulated world, like blasts. |
| [ReplicatedStorage](../services/replicatedstorage.md) | A shared folder that both server and client scripts can see. |
| [RunService](../services/runservice.md) | The engine's clock, and where the script is running. |
| [ServerScriptService](../services/serverscriptservice.md) | Server-only content, kept off clients. |
| [SoundService](../services/soundservice.md) | Global sound settings for the place. |
| [StarterGui](../services/startergui.md) | Interface objects kept here are copied to each player. |
| [StarterPack](../services/starterpack.md) | Contents kept here are copied to each player's backpack. |
| [StarterPlayer](../services/starterplayer.md) | Client scripts that run in place on each player's client. |
| [Store](../services/store.md) | Saves values with the place, on the server. |
| [TweenService](../services/tweenservice.md) | Animates properties smoothly over time. |
| [UserInputService](../services/userinputservice.md) | Keyboard and mouse input on the client. |
| [Workspace](../services/workspace.md) | The place world, and its ray query. |

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
| [The Luau standard library](../scripting/luau.md) | What the VM provides beyond the engine's API. |
