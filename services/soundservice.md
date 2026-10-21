# SoundService

Settings for music and ambience.

`SoundService` holds the two global audio settings the engine reads.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| MusicVolume | number | Music volume. Not clamped. |
| AmbientReverb | string | The reverb preset name. Default `NoReverb`, and any string is accepted. |

## A note on audio

The settings are stored and readable, but the engine does not mix audio. Changing them makes nothing audible.

## Members

SoundService has no methods of its own. It also has the shared Instance members; see [Instance](../globals/instance.md).

## Example

```lua
local SoundService = game:GetService("SoundService")

print(SoundService.AmbientReverb)    -- NoReverb
SoundService.MusicVolume = 0.6
SoundService.AmbientReverb = "Hall"
```

## See also

- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/index.md)
