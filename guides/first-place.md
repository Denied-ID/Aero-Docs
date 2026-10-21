# Your first place

Build a small place, script both halves of it, and play it. Every menu and key here is in the [Studio Tour](studio-tour.md), and every name in the scripts is in the [API reference](../api/index.md).

## Start the place

Open Studio and choose File > New. A new place opens with a flat baseplate.

## Put parts down

Press Ctrl+I to open the Insert palette, pick Part, and drag it into the viewport. Add two or three this way.

Select a part (the Select tool is key 1) and change it in the Properties panel: give it a color and a size. Try the Move (2), Scale (3), and Rotate (4) tools on it. Drag in the viewport to move the part, or set values directly in the Properties panel.

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

- [Client and server](client-and-server.md): why the two scripts ran on two halves.
- [Testing your place](testing-your-place.md): what Play actually started.
- [API Reference](../api/index.md): everything scripts can reach.
