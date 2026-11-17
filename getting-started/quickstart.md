# Quickstart

Install Aero, build a small place, and play it. Each step links to the full guide.

## 1. Install Studio

Download Aero Setup and install the Client and Studio. Sign in with your Aero account when the installer asks, and pick where Aero lives.

The full guide is [Installation](installation.md).

## 2. Take the tour

Open Studio and meet the panels. The Explorer is on the right, Properties sits beside it, Output runs along the bottom, and the Insert palette opens on the left with Ctrl+I.

The full guide is [Studio tour](studio-tour.md).

## 3. Build your first place

Start a new place and drag in a few parts. Then add two scripts. The server script goes in ServerScriptService.

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function (player)
    print("Welcome", player.Name)
end)

print("server started")
```

The client script goes in StarterPlayer.

```lua
local Players = game:GetService("Players")

print("client ready for", Players.LocalPlayer.Name)
```

The full guide is [Your first place](../tutorials/first-place.md).

## 4. Play it

Press F5. Output shows both halves. The server script writes `server started`, and the client script writes `client ready for` with a player name. Press Shift+F5 to stop.

The full guide is [Testing your place](../tutorials/testing-your-place.md).

## See also

- [Client and server](../guides/client-and-server.md) (why the two scripts ran on two halves)
- [Troubleshooting](../guides/troubleshooting.md) (Output errors, crash dialogs, and fixes)
- [API Reference](../api/index.md) (everything scripts can reach)