# Kits

A kit is a named build that lives in the place, and copies of one kit can stay linked.

## Methods

| Method | What it does |
| --- | --- |
| Build(name) | Clones the kit called `name` into the Workspace and returns the copy, or `nil` when no kit carries that name. |

## Linking copies

Kit copies that share the same `KitId` stay in sync while you edit: move a brick in one and it moves in all of them, add a brick and it appears in all of them. The most recent edit wins.

The kit's own name, position, and parent belong to each copy and never sync, so every copy can sit where it needs to sit. Set `KitId` to an empty string to break one copy away; copies made with Clone or copy and paste keep the link.

Syncing happens while you edit. During play, scripts change their own copies and nothing propagates.

## Saving builds

A saved kit is one `.aekit` file holding the kit and everything inside it. Studio keeps two libraries: a folder named after the place, beside its `.aepl` file, and a global folder at `%LOCALAPPDATA%\Aero\Kits` shared by every place. A place called `Harbor.aepl` keeps its kits in `Harbor.kits\`.

Open the Kit Tray from View > Kit Tray to see both libraries. Double-click a kit to insert it, or use Import Kit... to read a `.aekit` from anywhere. Every insert keeps the file's `KitId`, so two copies of the same saved kit start out linked. When the place already holds a kit with that id, the tray inserts the copy already in the place instead of the file.

Right-click a kit in the Explorer for these actions:

| Action | What it does |
| --- | --- |
| Cast as Kit | Turns a Model or Folder into a kit with a fresh `KitId`, moving its contents inside. |
| Break from Kit | Clears `KitId` on one copy, so it stops following the others. |
| Save as Kit... | Writes the kit to this place's library. |
| Save to Global Kits... | Writes the kit to the global library. |
| Export Kit to File... | Writes a `.aekit` to a folder you pick, for handing the build to someone else. |

Saving a kit that has no `KitId` yet gives it one, so the file has an identity to follow. A place that has never been saved has no folder of its own, so Save as Kit writes to the global library instead.

## How library files follow edits

Saving the place rewrites each kit file beside it from the copy in the place that shares its `KitId`. Global files only change when you pick Save to Global Kits. If you delete a kit from the place, its file stays in the library.

A library file holds one version, not a history. When several copies of a kit are linked, the copy the save finds first decides the file's contents.

## Example

```lua
local kits = game:GetService("Kits")

for i = 1, 3 do
    kits:Build("Watchtower")
end
```

## See also

- [API Reference](../api/api.md)
