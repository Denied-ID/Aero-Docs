# CoreGui

The engine's own interface.

`CoreGui` holds the interface the engine draws itself: the player list, the health display, the backpack, chat, and the emotes menu. Its contents are built by the engine, not authored by scripts.

## Members

CoreGui has no properties, events, or methods beyond the shared Instance members. See [Instance](../globals/instance.md).

To show or hide the parts of it, call [StarterGui](startergui.md)`:`SetCoreGuiEnabled` from a LocalScript:

```lua
local StarterGui = game:GetService("StarterGui")
StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Chat, false)
```

## See also

- [StarterGui](startergui.md): the switch for these elements.
- [ScreenGui](../classes/screengui.md): interface you author yourself.
- [API Reference](../api/api.md)
