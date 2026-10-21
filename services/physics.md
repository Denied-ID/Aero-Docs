# Physics

What scripts do to the simulated world.

## Methods

| Method | What it does |
| --- | --- |
| Explode(center, radius, power, options?) | Detonates a blast at `center`. Returns the number of bodies it pushed, then a table describing each one. |

Call it from a Script. A LocalScript raises an error instead, because a client cannot change the simulation.

`center` is a Vector3 in studs. `radius` is the blast's reach in studs. `power` is the speed, in studs per second, that a 1x1x1 brick gains at the epicenter. Bigger bodies get pushed proportionally less, so a wall barely lifts while loose bricks fly. Everything past `radius` is untouched.

`options` is a table, and every field has a default:

| Field | Default | What it does |
| --- | --- | --- |
| Falloff | 2 | How fast the push fades with distance. 1 fades linearly, 2 quadratically. |
| UpwardBias | 0.25 | How much the push tilts upward, 0 to 1. High values throw debris into the air. |
| RespectWalls | true | When true, anchored geometry between the blast and a body blocks it. |
| Visual | true | Whether clients draw the fireball and the light flash. |
| VisualColor | warm orange | The Color3 of the fireball and the flash. |
| FilterDescendantsInstances | empty | Instances to skip, with everything under them. |

The second return value is a table of hits. Each hit has `Instance`, `Distance` (studs from the epicenter to the body's surface), `Direction` (the unit vector of the push), and `DeltaVelocity` (the speed change the body received, in studs per second). Use it for damage, sounds, and scorch marks without running a second query.

## Characters

A blast that reaches a character does not write on the character directly. The server sends the fling to the player whose character it is, their game applies it, and everyone else sees the flight through the normal pose stream. The character flies on the push, slides to a stop, stays down for up to a second and a half depending on how hard it was hit, then gets up. Faster blasts hold characters down longer.

Fast debris does the same on contact: a loose brick thrown hard enough at a character knocks that character over, anywhere in the game, not just from a blast.

## Example

```lua
local Physics = game:GetService("Physics")

local count, hits = Physics:Explode(barrel.Position, 12, 400)

for _, hit in hits do
    print(hit.Instance.Name, "pushed", hit.Distance, "studs from the blast")
end
```

## See also

- [API Reference](../api/index.md)
