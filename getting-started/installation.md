# Installation

Aero is a standalone creator-first multiplayer gaming platform. You make places in Studio, add behavior with Luau scripts, and test it all with Play. One download covers everything: Aero Setup installs the Aero Client and Aero Studio, and each app updates itself when you start it.

## What you need

A 64-bit Windows 10 or 11 PC. The install is per-user, inside your own profile, so it never asks for administrator rights and there is nothing else to install alongside it.

## Installing with Aero Setup

1. On the Downloads page, pick **Download for Windows**. That saves a single file, like `AeroSetup-0.0.1.6.exe`. The number is the build. It goes up with every release.
2. Run it and choose **Sign in with Aero**. Your browser opens so you can approve access there; the installer never sees your password.
3. Pick which pieces to keep: the Client, Studio, or both. You can change this later.
4. Pick where Aero lives. The default is a folder inside your local app data, and anything already there is left alone.
5. Choose **Install**. When it finishes, the last page offers to launch what you just installed.

## Starting your apps

Open **Aero Client** or **Aero Studio** from the Start Menu. Each shortcut checks that app for updates first and applies them before starting, with a progress window only while something is actually downloading. When everything is current, the app just starts. There is no separate launcher window to go through.

Your apps show their build as **Build N** with the source commit next to it. The Client menu footer shows it, and Studio shows it in Help > About. Studio's product line says alpha, like `0.0.1.6-alpha`. The Client and Server also print it for a `--version` flag. Quote that line in a bug report.

## Staying up to date

There is nothing to do by hand. Launching an app brings it current, and the updater itself updates the same way: if a newer one is available, it downloads, restarts once, and carries on with your launch. If an update is ever interrupted, relaunching picks up from a clean state.

The Downloads page also lists per-component zips for manual use. Those need a signed-in account; the installer is the normal path.

## Changing or removing Aero

Run `AeroSetup.exe` again with Aero already installed and it opens a maintenance page instead of the installer: **Modify installation** walks the same screens to change components or locations, and **Uninstall Aero** removes the apps, the shortcuts, and the saved sign-in. Your `.aepl` place files live wherever you saved them and are never touched.

You can also uninstall from Windows Settings, where the entry is listed as **Aero Launcher**.

## If something goes wrong

Start with [Troubleshooting](troubleshooting.md). Installer and update problems have their own rows there, alongside the script errors and crashes.

## Where to go next

Read the [Studio Tour](../studio/studio-tour.md) to learn the editor, then browse the [API Reference](../api/api.md) when you start scripting.
