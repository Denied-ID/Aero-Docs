# Your first place

Build a small place, script both halves of it, and play it.

## Start the place

Open Studio and choose File > New. A new place opens with a flat baseplate.

## Put parts down

Press Ctrl+I to open the Insert palette, pick Part, and drag it into the viewport. Add two or three this way.

Four toolbar tools change what a drag does, and keys 1 through 4 switch between them. Each one draws its handles in the part's own axes:

| Tool | Key | The handles it draws |
| --- | --- | --- |
| Select | 1 | None. Clicking picks a part. |
| Move | 2 | An arrow on each axis. |
| Scale | 3 | A handle on each axis. |
| Rotate | 4 | A ring around each axis, through the part's center. |

Select a part, then change it in the Properties panel: give it a color and a size. Dragging in the viewport is one way; typing the values directly is the other.

## Add the server script

In the Explorer, click ServerScriptService, then drag a Script onto it from the Insert palette. The editor opens. Type:

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function (player)
    print("Welcome", player.Name)
end)

print("server started")
```

## Add the client script

Click StarterPlayer in the Explorer and drag a LocalScript onto it:

```lua
local Players = game:GetService("Players")

print("client ready for", Players.LocalPlayer.Name)
```

## Play it

Press F5. The character appears on the baseplate, and Output along the bottom shows `server started` from the server script and `client ready for` with a name from the client script. Walk with W, A, S, and D, and hold Space to jump.

Press Shift+F5 to end the test. The place returns exactly as it was, so changes made during a test do not stay. Build in edit mode, test with Play, and edit again.

## Where to go next

- [Client and server](../guides/client-and-server.md): why the two scripts ran on two halves.
- [Testing your place](testing-your-place.md): the server and client behind Play.
- [API Reference](../api/index.md): everything scripts can reach.
