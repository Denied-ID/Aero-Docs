# CoreGui

The engine's own interface.

`CoreGui` holds the interface the engine draws itself: the topbar, the chat window, the health display, the player list, the name tags over characters, and the menu. Its contents are built by the engine, not authored by scripts.

## Members

CoreGui has no properties, events, or methods beyond the shared Instance members. See [Instance](../globals/instance.md).

The player list, the health display, and chat can be switched off through [StarterGui](startergui.md)`:`SetCoreGuiEnabled` from a LocalScript:

```lua
local StarterGui = game:GetService("StarterGui")
StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Chat, false)
```

## See also

- [StarterGui](startergui.md): the switch for these elements.
- [ScreenGui](../classes/screengui.md): interface you author yourself.
- [API Reference](../api/index.md)
