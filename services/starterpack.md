# StarterPack

The contents every player's backpack starts with.

Children of `StarterPack` are copied into each player's Backpack when their character spawns. A script inside one of them is skipped where it sits and runs from the copy the player receives.

## Members

StarterPack has no properties, events, or methods beyond the shared Instance members. See [Instance](../globals/instance.md).

## Example

```lua
-- A Script in StarterPack
print(script.Parent.Name)     -- Backpack, in the player's copy
```

The script above prints `Backpack`, not `StarterPack`, because the copy under the player is the one that runs.

## See also

- [StarterGui](startergui.md): the same idea for interface.
- [Player](../classes/player.md): where the Backpack appears.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
