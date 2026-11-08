# CoreGui

The engine's own interface.

`CoreGui` holds the interface the engine draws itself: the topbar, the chat window, the health display, the player list, the name tags over characters, and the menu. Its contents are built by the engine, not authored by scripts.

CoreGui is read-only. Scripts can read it and clone it, but creating, deleting, reparenting, or changing properties under it raises an error. Studio shows it read-only too. The client also refuses to apply replicated changes under CoreGui, so a server cannot push interface changes into another player's client.

## Members

The service itself carries two chat settings, and nothing else beyond the shared [Instance](../globals/instance.md) members:

| Member | Type | What it does |
| --- | --- | --- |
| ChatHistoryLength | number | How many lines the chat log keeps before the oldest drop off. Default 100. |
| ChatAutoFade | boolean | Whether the quiet chat window fades out on its own. When false it stays up until switched off. Default true. |
| ChatWindowWidth | number | Chat window width in pixels, between 240 and 600. Default 384. |
| ChatWindowCorner | number | Which corner the chat hugs: 0 top-left, 1 top-right, 2 bottom-left, 3 bottom-right. Default 0. |

These two are runtime settings: they are not saved with the place.

The player list, the health display, chat, and the connection meter can be switched off through [StarterGui](startergui.md)`:`SetCoreGuiEnabled` from a LocalScript:

```lua
local StarterGui = game:GetService("StarterGui")
StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Chat, false)
```

## See also

- [StarterGui](startergui.md): the switch for these elements.
- [ScreenGui](../classes/screengui.md): interface you author yourself.
- [API Reference](../api/index.md)
