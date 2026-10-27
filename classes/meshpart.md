# MeshPart

A part whose shape comes from a mesh file.

A `MeshPart` takes everything a [Part](part.md) has and swaps the box shape for a glTF mesh. Its size still controls placement and collision; the mesh controls what you see.

## Properties

| Property | Type | What it does |
| --- | --- | --- |
| MeshId | string | Path to the mesh. It must end in `.gltf` or `.glb`, and values longer than 512 bytes are dropped. Setting it clears any mesh data already embedded in the part. Assigning a mesh resizes the part to the mesh's own dimensions. |
| DoubleSided | boolean | Draws back faces as well as front faces. |

Both properties belong to MeshPart alone. A plain Part raises an error if you write them.

`MeshId` is forgiving in a way that hides mistakes: a value with the wrong extension is cleared instead of rejected, so the part quietly renders as a box. A file that cannot be opened has the same result, and the block shape stays until a mesh loads.

## Members

MeshPart has every [Part](part.md) member, plus the shared Instance members in [Instance](../globals/instance.md).

A MeshPart is not a subclass of Part for `IsA`, so `IsA("Part")` is false even though all the Part properties work.

## Example

```lua
local rock = Instance.new("MeshPart")
rock.Name = "Rock"
rock.MeshId = "content/meshes/rock.glb"
rock.DoubleSided = false
rock.Size = Vector3.new(6, 4, 6)
rock.Position = Vector3.new(0, 2, 0)
rock.Parent = workspace
```

## See also

- [Part](part.md): the box-shaped version.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/index.md)
