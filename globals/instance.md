# Instance

The base of every object, with Instance.new to create them.

Every object in a place is an Instance: parts, scripts, folders, interface objects, and the services themselves. Each one has a class name, a name, a place in the tree, and the members its class adds on top of the ones listed here.

## Creating one

| Call | Returns |
| --- | --- |
| `Instance.new(className)` | A new object of that class, with no parent. |
| `Instance.new(className, parent)` | The same, already parented. |

The class name must be one the engine can build on demand:

| Group | Names |
| --- | --- |
| Parts and models | Part, MeshPart, Model, Folder, Kit |
| Scripts | Script, LocalScript, ModuleScript |
| Players and input | Player, InputObject |
| Networking | RemoteEvent, RemoteFunction |
| Characters | Humanoid |
| Interface | ScreenGui, Frame, TextLabel, TextButton, TextBox, ScrollingFrame, ImageLabel, UICorner, UIStroke, UIGradient |
| Lights | PointLight, SpotLight, SurfaceLight |
| Animation | Tween |

An unknown name raises `NotAClass is not a valid class name`. Workspace and the services are already created for the place, so `Instance.new("Workspace")` raises the same error.

## Members every Instance has

| Member | Type | What it does |
| --- | --- | --- |
| Name | string | The name shown in the Explorer, used by child lookup and by `FindFirstChild`. |
| ClassName | string | The class name, read-only. |
| Parent | Instance or nil | Where the object sits. Setting it moves the object and everything under it. |

Reading a member that is not a property, event, or method with an object's name returns its direct child with that exact name, case-sensitive:

```lua
local door = workspace.Door          -- same as workspace:FindFirstChild("Door")
```

A property, event, or method always wins over a child with the same name.

Setting `Parent` to `nil` removes the object from the tree. Moving an object into its own descendant raises an error, and so does parenting anything other than a service directly under `game`.

## Events

Every class has these:

| Event | Callback arguments | When it fires |
| --- | --- | --- |
| ChildAdded | child | A child was parented in. |
| ChildRemoved | child | A child was parented out. |
| DescendantAdded | descendant | Anything below this object was added. |
| DescendantRemoving | descendant | Anything below this object is about to leave. |
| AncestryChanged | child, parent | This object or a descendant changed parent. `parent` is nil when it left the tree. |
| Changed | propertyName | A property was written. One write can fire more than one name, such as `CFrame`, `Position`, and `Orientation` for one position change. |
| Destroying | none | The object is about to be destroyed. |

## Signals

`Connect` runs a function every time the signal fires. `Once` runs it once and then disconnects. `Wait` pauses the script until the signal fires and returns the arguments the signal sends.

```lua
local connection = part.ChildAdded:Connect(function (child)
    print("added", child.Name)
end)

connection:Disconnect()
```

| Signal member | Returns | What it does |
| --- | --- | --- |
| Connect(fn) | Connection | Calls `fn` each time the signal fires. |
| Once(fn) | Connection | Calls `fn` once, then disconnects. |
| Wait() | the signal's arguments | Yields until the signal fires. |

| Connection member | Type | What it does |
| --- | --- | --- |
| Connected | boolean | True until the connection is disconnected. |
| Disconnect() | nothing | Stops the callback. Calling it twice is safe. |

`Connect`, `Once`, `Wait`, and `Disconnect` also have lowercase aliases. A connection to an instance drops when that instance is destroyed.

## Methods

Every instance sees every method. A method only works on the class it belongs to, and calling it on the wrong one raises an error such as `GetPlayers is only available on Players`.

| Method | Works on | What it does |
| --- | --- | --- |
| FindFirstChild(name, recursive?) | any | Returns the first child with that name, or a descendant when `recursive` is truthy. |
| FindFirstChildOfClass(className) | any | Returns the first direct child of that class. |
| FindFirstChildWhichIsA(className, recursive?) | any | Like `FindFirstChildOfClass`, but accepts a base class name. |
| FindFirstAncestor(name) | any | Walks up the tree to the first ancestor with that name. |
| FindFirstAncestorOfClass(className) | any | Walks up to the first ancestor of that class. |
| WaitForChild(name, timeout?) | any | Yields until a child with that name exists. Returns nil if the timeout passes first. Without a timeout it waits forever. |
| GetChildren() | any | A new array of direct children. |
| GetDescendants() | any | A new array of everything below this object. |
| GetFullName() | any | The path, such as `Workspace.Door.Hinge`. |
| IsA(className) | any | Whether the class is that name or derives from it. |
| IsDescendantOf(ancestor) | any | Whether this object sits anywhere below another. |
| IsAncestorOf(descendant) | any | The reverse of `IsDescendantOf`. |
| Destroy() | any | Removes the object and everything under it, and disconnects their signals. |
| Clone() | any | A deep copy with no parent, or nil for classes that cannot be built on demand. |
| ClearAllChildren() | any | Destroys every direct child. |
| GetService(name) | game | Returns a service. See [game](../globals/game.md). |
| IsServer() | RunService | True on the server. |
| IsClient() | RunService | True on a client. |
| IsStudio() | RunService | True when the place is running inside Studio. |
| BindToRenderStep(name, priority, fn) | RunService | Calls `fn` each rendered frame on the client. Binding the same name again replaces it. |
| UnbindFromRenderStep(name) | RunService | Removes a binding made with that name. |
| Build(name) | Kits | Clones the named Kit into Workspace. |
| GetPlayers() | Players | An array of the players in the game. |
| SetCoreGuiEnabled(type, enabled) | StarterGui | Shows or hides one of the engine's own interface elements. |
| GetCoreGuiEnabled(type) | StarterGui | Whether that element is enabled. |
| FireServer(...) | RemoteEvent | Sends values from a client to the server. |
| FireClient(player, ...) | RemoteEvent | Sends values from the server to one player. |
| FireAllClients(...) | RemoteEvent | Sends values from the server to every player. |
| InvokeServer(...) | RemoteFunction | Calls the server and waits for its return values. |
| Raycast(origin, direction, maxDistance?, params?) | Workspace | Returns the first thing hit along a ray. |
| GetMouseLocation() | UserInputService | The mouse position in pixels. |
| GetMouseDelta() | UserInputService | How far the mouse moved. |
| IsKeyDown(keyCode) | UserInputService | Whether a key is held. |
| IsMouseButtonPressed(button) | UserInputService | Whether a mouse button is held. |
| Create(instance, info, properties) | TweenService | Builds a tween. |
| Play() | Tween | Starts or resumes the tween. |
| Pause() | Tween | Holds the tween where it is. |
| Cancel() | Tween | Stops the tween and leaves the property where it stopped. |
| GetSunDirection() | Lighting | The direction the sun shines from. |
| GetMoonDirection() | Lighting | The direction the moon shines from. |
| Get(key) | Store | Reads a saved value, on the server. |
| Set(key, value) | Store | Writes a saved value, on the server. |
| Report() | Perf | Writes timing lines to the Output. |

## Example

```lua
local folder = Instance.new("Folder")
folder.Name = "Loot"
folder.Parent = workspace

local part = Instance.new("Part", folder)
part.Position = Vector3.new(0, 5, 0)

part.ChildAdded:Connect(function (child)
    print("added", child.Name)
end)

print(part:GetFullName())    -- Workspace.Loot.Part
```

## See also

- [game](../globals/game.md): the root of the tree.
- [Vector3](../globals/vector3.md): positions and directions.
- [API Reference](../api/api.md)
