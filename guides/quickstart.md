# Quickstart

Install Aero, build a small place, and play it. Each step links to the full guide.

## 1. Install Studio

Download Aero Setup and install the Client and Studio. Sign in with your Aero account when the installer asks, and pick where Aero lives.

Full guide: [Installation](installation.md).

## 2. Take the tour

Open Studio and meet the panels: the Explorer on the right, Properties beside it, Output along the bottom, and the Insert palette on the left with Ctrl+I.

Full guide: [Studio Tour](studio-tour.md).

## 3. Build your first place

Start a new place and drag in a few parts. Then add two scripts. The server script goes in ServerScriptService:

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function (player)
    print("Welcome", player.Name)
end)

print("server started")
```

The client script goes in StarterPlayer:

```lua
local Players = game:GetService("Players")

print("client ready for", Players.LocalPlayer.Name)
```

Full guide: [Your first place](first-place.md).

## 4. Play it

Press F5. Output shows both halves: `server started` from the server script, and `client ready for` with a player name from the client script. Press Shift+F5 to stop.

Full guide: [Testing your place](testing-your-place.md).

## Where to go next

- [Client and server](client-and-server.md): why the two scripts ran on two halves.
- [Troubleshooting](troubleshooting.md): Output errors, crash dialogs, and fixes.
- [API Reference](../api/index.md): everything scripts can reach.
