# API Reference

Every name Luau scripts can use, in one list. Classes are objects you add, services are always there, functions do things, and globals are values and roots.

Member tables are being filled in page by page. Names follow the live bindings.

## Guides

| Guide | About |
| --- | --- |
| [Installation](../getting-started/installation.md) | Install Studio and open your first place. |
| [Studio tour](../studio/studio-tour.md) | Panels, toolbar, saving, and playtesting. |
| [Troubleshooting](../getting-started/troubleshooting.md) | Output errors, crash dialogs, and fixes. |

## Classes

| Symbol | About |
| --- | --- |
| [Folder](../classes/folder.md) | Keeps the Explorer organized. Holds anything. |
| [Frame](../classes/frame.md) | A box that holds other interface objects. |
| [Humanoid](../classes/humanoid.md) | Makes a model walk, jump, and take damage. |
| [ImageLabel](../classes/imagelabel.md) | A picture on the screen. |
| [InputObject](../classes/inputobject.md) | Describes one input, like a key press. |
| [LocalScript](../classes/localscript.md) | Luau code that runs on each player machine. |
| [MeshPart](../classes/meshpart.md) | A part that uses a custom mesh shape. |
| [Model](../classes/model.md) | A group of parts that move as one. |
| [ModuleScript](../classes/modulescript.md) | A library of shared Luau functions. |
| [Part](../classes/part.md) | A solid block. The basic building piece. |
| [Player](../classes/player.md) | One person in the game. |
| [PointLight](../classes/pointlight.md) | Light that shines in all directions from one point. |
| [RemoteEvent](../classes/remoteevent.md) | Sends one way messages between client and server. |
| [RemoteFunction](../classes/remotefunction.md) | Asks the other side a question and waits for the answer. |
| [ScreenGui](../classes/screengui.md) | A screen interface. Holds buttons and labels. |
| [Script](../classes/script.md) | Luau code that runs on the server. |
| [ScrollingFrame](../classes/scrollingframe.md) | A box with a scroll bar. |
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
| [CoreGui](../services/coregui.md) | Built in interface elements like chat and the health bar. |
| [Lighting](../services/lighting.md) | Sun, sky, and atmosphere for the place. |
| [Players](../services/players.md) | Everyone in the game. Handles spawning characters. |
| [ReplicatedStorage](../services/replicatedstorage.md) | A shared folder that both server and client scripts can see. |
| [RunService](../services/runservice.md) | Tells scripts what is running: editing, Play, or Run. |
| [ServerScriptService](../services/serverscriptservice.md) | A safe place to keep server scripts. |
| [SoundService](../services/soundservice.md) | Global sound settings for the place. |
| [StarterGui](../services/startergui.md) | Interface objects kept here are copied to each player. |
| [StarterPack](../services/starterpack.md) | Tools kept here are copied to each player. |
| [StarterPlayer](../services/starterplayer.md) | Settings for how characters spawn. |
| [TweenService](../services/tweenservice.md) | Animates properties smoothly over time. |
| [UserInputService](../services/userinputservice.md) | Keyboard, mouse, and gamepad input on the client. |
| [Workspace](../services/workspace.md) | The place world. Everything you see lives under it. |

## Functions

| Symbol | About |
| --- | --- |
| [print](../functions/print.md) | Writes a line to the Output panel. |
| [require](../functions/require.md) | Loads a ModuleScript and returns what it returned. |
| [task](../functions/task.md) | Pausing and scheduling for scripts. |
| [warn](../functions/warn.md) | Writes a warning line to the Output panel. |

## Globals

| Symbol | About |
| --- | --- |
| [BrickColor](../globals/brickcolor.md) | A named color from the classic palette. |
| [CFrame](../globals/cframe.md) | A position plus a rotation in 3D. |
| [Color3](../globals/color3.md) | A color mixed from red, green, and blue. |
| [Enum](../globals/enum.md) | Named lists of options. |
| [game](../globals/game.md) | The place itself. Start here with GetService. |
| [Instance](../globals/instance.md) | The base of every object, with Instance.new to create them. |
| [Random](../globals/random.md) | Random numbers with its own seed. |
| [TweenInfo](../globals/tweeninfo.md) | Timing settings for an animation. |
| [UDim](../globals/udim.md) | A length that scales with its parent, plus pixels. |
| [UDim2](../globals/udim2.md) | A screen position and size that survives resizing. |
| [Vector2](../globals/vector2.md) | A point on a flat surface, like a screen. |
| [Vector3](../globals/vector3.md) | A point or direction in 3D space. |
| [workspace](../globals/workspace.md) | Shortcut for the Workspace service. |
