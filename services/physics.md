# Physics

What scripts do to the simulated world.

## Methods

| Method | What it does |
| --- | --- |
| Explode(center, radius, power, options?) | Detonates a blast at `center`. Returns a table of hits, one per pushed body, each with `Instance`, `Distance`, `Direction`, and `DeltaVelocity`. |

Call it from a Script. A LocalScript raises an error instead, because a client cannot change the simulation.

`center` is a Vector3 in studs. `radius` is the blast's reach in studs. `power` is the speed, in studs per second, that a 1x1x1 brick gains at the epicenter. Bigger bodies get pushed proportionally less, so a wall barely lifts while loose bricks fly. Everything past `radius` is untouched.

`options` is a table, and every field has a default:

| Field | Default | What it does |
| --- | --- | --- |
| Falloff | Enum.BlastFalloff.Quadratic | How fast the push fades toward the edge of the radius. |
| UpwardBias | 0.25 | How much the push tilts upward, 0 to 1. High values throw debris into the air. |
| RespectWalls | true | When true, anchored geometry between the blast and a body blocks it. |
| Visual | true | Whether clients draw the fireball and the light flash. |
| VisualColor | warm orange | The Color3 of the explosion sphere. |
| FilterDescendantsInstances | empty | Instances to skip, with everything under them. |

`Falloff` takes an `Enum.BlastFalloff`:

| Item | What it does |
| --- | --- |
| Constant | Full push at every distance inside the radius. |
| Linear | Fades evenly from the epicenter to the edge. |
| Quadratic | The default: the fade steepens near the edge, so most of the push stays near the center. |
| Sharp | Nearly everything at the center, almost nothing past half the radius. |

A raw number works too: it is the exponent on the fade curve, so `1.5` sits between Linear and Quadratic.

The return value is a table of hits, one per pushed body. Each hit has `Instance`, `Distance` (studs from the epicenter to the body's surface), `Direction` (the unit vector of the push), and `DeltaVelocity` (the speed change the body received, in studs per second). Use it for damage, sounds, and scorch marks without running a second query.

## Characters

A blast that reaches a character does not write on the character directly. The server sends the fling to the player whose character it is, their game applies it, and everyone else sees the flight through the normal pose stream. The character flies on the push, slides to a stop, stays down for up to a second and a half depending on how hard it was hit, then gets up. Faster blasts hold characters down longer.

Fast debris does the same on contact: a loose brick thrown hard enough at a character knocks that character over, anywhere in the game, not just from a blast.

## Contacts

Parts report touches as events, so scripts can react to collisions without polling positions. Connect to a part's [Touched](../classes/part.md) event from a server script:

```lua
local pad = workspace.SpeedPad

pad.Touched:Connect(function(other)
    print(other.Name, "reached the pad")
end)
```

The event fires once when contact begins, with the other part as the argument, and again only after the parts separate and meet again. The server detects the contact and the event replays on clients, so the same handler works in a Script or a LocalScript.

## Example

```lua
local Physics = game:GetService("Physics")

local hits = Physics:Explode(barrel.Position, 12, 400)
for _, hit in hits do
    print(hit.Instance.Name, "pushed", hit.Distance, "studs from the blast")
end
```

## See also

- [API Reference](../api/index.md)
