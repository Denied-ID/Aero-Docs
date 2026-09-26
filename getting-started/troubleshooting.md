# Troubleshooting

When something breaks, the reason is written down somewhere. There are two places to look: the Output panel inside Studio, and the crash dialog with its logs folder. This page covers both, then the problems people hit most.

## The Output panel

Everything your scripts print, plus every script error, lands in Output along the bottom of Studio. Errors show in red and warnings in amber. A compile error names the script and the message. A runtime error names the script too.

Double click a line that mentions a script and Studio jumps straight to that line in the editor.

If the viewport freezes during a test, read the red lines. The test stops at the first error, so fix the earliest one and run again. You can filter the panel to show only warnings and errors while you look.

## The crash dialog

A hard native crash is not a script error, so it does not go to Output. The app closes with a dialog instead. It names the error, saves a log and a crash dump, and offers to open the logs folder. Attach both files to a bug report.

Two dialogs you may see:

- A DirectX error naming device creation. The engine found no graphics device it could use, not even software rendering. Update your graphics drivers and Windows first, then report it with the logs if it persists.
- An unhandled exception with an address and a code. That is a native crash. There is nothing to fix on your side, so send the log and the dump.

## Common problems

| What you see | What it means | What to do |
| --- | --- | --- |
| Viewport freezes after pressing Play | A script threw during the test | Read the red lines in Output, fix the earliest error, Stop and Play again |
| Script runs but does nothing, with no error | It may be running where you cannot see it | Check Play versus Run: Run starts server scripts only, with no player character |
| Place opens with a Place Repaired message | Studio dropped unsupported items or moved items so the file could load | Read what it lists, then pick Save Now or Later. Servers will not run the place until it is saved with the fixes |
| Insert refused with Cannot create here | That parent cannot hold that object | Pick another spot in the Explorer and try again |
| Test runs very slowly on an old machine | The engine likely fell back to software rendering | Update your drivers, or use another newer system or change graphics cards if possible |
| Client closes with a DirectX error dialog | No graphics path worked at all | Update drivers and Windows, then report it with the logs folder contents if the issue persists |

## Where to go next

Back to [Installation](installation.md) if you are still setting up, or the [Studio Tour](../studio/studio-tour.md) to keep learning the editor.
