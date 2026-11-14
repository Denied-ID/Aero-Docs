# StarterPlayer

Client-side content that runs where it sits.

`StarterPlayer` holds the scripts that should run on each client. Unlike StarterGui and StarterPack, its contents are not copied. A LocalScript placed here runs where it sits, on the client. It also holds the defaults a new character spawns with.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| WalkSpeed | number | Humanoid WalkSpeed for new characters. Default 16. |
| JumpPower | number | Humanoid JumpPower for new characters. Default 50. |
| UseJumpHeight | boolean | Whether spawning characters use JumpHeight instead of JumpPower. Default true. |
| JumpHeight | number | Jump height in studs when UseJumpHeight is true. Default 7. |
| MaxHealth | number | Humanoid MaxHealth for new characters. Default 100. |
| AutoRotate | boolean | Whether new characters turn toward their movement. Default true. |
| RespawnDelay | number | Seconds before a dead character respawns. Default 3. |
| CharacterCollision | boolean | Whether characters collide with each other. Default true. |
| CameraMinZoomDistance | number | Closest the orbit camera zooms in on a character. Default 2. |
| CameraMaxZoomDistance | number | Farthest the orbit camera zooms out from a character. Default 20. |
| CameraFieldOfView | number | Horizontal field of view of the game camera, in degrees. Default 85. |

All eleven are saved with the place and scriptable.

## Example

```lua
-- LocalScript in StarterPlayer
local Players = game:GetService("Players")

print("client ready for", Players.LocalPlayer.Name)
```

## See also

- [LocalScript](../classes/localscript.md): the class that runs here.
- [StarterGui](startergui.md): interface copied into each player.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/index.md)
