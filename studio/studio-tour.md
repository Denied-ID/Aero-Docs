# Studio Tour

Studio is where you build. One window, a 3D view in the middle, and panels around it for everything else.

## The panels

The viewport takes up the center. This is your place, rendered live. Click parts to select them and drag to move them. Scripts open as tabs over the viewport.

The Explorer sits on the right. It lists everything in the place as a tree. Right click anything for options.

Properties sits next to the Explorer. It shows the settings of whatever you selected. Change a number or a color and the viewport updates right away.

Output runs along the bottom. Script errors and printed messages show up here. Double click a line that mentions a script and Studio jumps straight to it.

The Insert palette hides on the left until you need it. Press Ctrl+I to open it, search for what you want, then drag it into the viewport or the Explorer.

## The toolbar

The top bar holds the tools you will use constantly.

Select, Move, Scale, and Rotate change how dragging behaves. Keys 1 through 4 switch between them fast.

Play starts a full test with everything running. Run starts a server only test with no player character. Pause freezes the test. Stop ends it and puts your place back exactly how it was. Step moves one frame at a time while paused.

Undo and Redo cover place edits, so you can experiment freely.

## Saving and files

File holds New, Open, Save, and Save As. A new place with no name is called Untitled until you save it.

Studio tracks unsaved changes and asks before you throw them away. It also saves a backup copy in the background and offers to recover your work if it ever closes unexpectedly. Recent places are listed under File so you can jump back in.

Place files use the .aepl extension. You never need to open one outside Studio.

Sometimes opening a file shows a Place Repaired message. It lists what Studio dropped or moved to load the file, then offers Save Now or Later. Saving can wait, but servers will not run the place until it is saved with the fixes.

## Copying and inserting

Cut, Copy, Paste Into, Duplicate, and Delete work the way you would expect. Duplicate makes a copy next to the original. Press F to frame the selected part in the viewport.

To add something new, open the Insert palette and pick what you need. Parts and models go into the world. Scripts open in the editor as soon as you add them. Interface objects land where they belong on screen.

## View and settings

View switches the viewport between Lit, Unlit, and Wireframe, and toggles a small diagnostics readout.

Edit holds Settings and Keyboard Shortcuts. Both apply the moment you change them. There is no restart step.

Under Help you will find About. Studio comes in a dark and a light theme, and you can rearrange the panels under View.

## Where to go next

Browse the [API Reference](../api/api.md) when you start adding behavior to your place.
