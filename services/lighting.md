# Lighting

Sun, sky, and atmosphere for the place.

`Lighting` owns the time of day, the ambient light, and the shadow settings. One instance of it exists in every place, and changing it updates the world immediately.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| ClockTime | number | Time of day in hours, from 0 to 24. Default 14. |
| TimeOfDay | string | The same time as `HH:MM:SS`. Writing accepts `H:M` or `H:M:S`. |
| DayOfYear | number | Day of the year from 1 to 365. Default 80, about the spring equinox. |
| GeographicLatitude | number | Latitude in degrees, from -90 to 90. Default 41.733299. |
| Brightness | number | Overall light intensity. Clamped to 0 and up. Default 1. |
| Ambient | Color3 | The ambient light at night. Not clamped. |
| OutdoorAmbient | Color3 | The ambient light during the day. Not clamped. |
| ColorShift_Top | Color3 | Tint added to surfaces facing up. Clamped from 0 to 1 per channel. |
| ColorShift_Bottom | Color3 | Tint added to surfaces facing down. Clamped from 0 to 1 per channel. |
| ShadowSoftness | number | How soft shadow edges are, from 0 to 1. Default 0.5. |
| Technology | Enum.LightingTechnology | Which lighting model renders the place. `Compatibility` keeps the older flat lighting. `Dynamic` uses the new warm, directional look. Default `Dynamic`. |
| GlobalShadows | boolean | Whether the sun and moon cast shadows. Default true. |

`ClockTime` and `TimeOfDay` are two views of one value. Setting either updates the other.

`Ambient` and `OutdoorAmbient` are blended by how high the sun is. At night the world takes `Ambient`; during the day it takes `OutdoorAmbient`, and twilight mixes the two.

The ambient light is directional. Surfaces facing up get a sky-tinted share of it, surfaces facing down fall toward a darker ground tone, and vertical surfaces sit between the two.

`Technology` picks the model behind that behavior. `Compatibility` renders the older flat lighting, where the ambient term never varies by surface orientation, and `Dynamic` is the directional look described here. Places saved before this property existed open as `Dynamic`.

An invalid `TimeOfDay` string is ignored, and the clock keeps its previous time. No error is raised, so a typo shows up as a time that never changes.

## Methods

| Method | Returns | What it does |
| --- | --- | --- |
| GetSunDirection() | Vector3 | The direction sunlight comes from. |
| GetMoonDirection() | Vector3 | The direction moonlight comes from. |

## Example

```lua
local Lighting = game:GetService("Lighting")

Lighting.ClockTime = 18.5
Lighting.Brightness = 1.5
Lighting.Ambient = Color3.fromRGB(70, 70, 90)
Lighting.OutdoorAmbient = Color3.fromRGB(110, 110, 130)
Lighting.ShadowSoftness = 0.7

print(Lighting.TimeOfDay)                -- 18:30:00
print(Lighting:GetSunDirection())
```

## See also

- [PointLight](../classes/pointlight.md): a local light source.
- [Color3](../globals/color3.md): the color type used here.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/index.md)
