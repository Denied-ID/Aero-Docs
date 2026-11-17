# Installation

Aero is a creator-first platform for multiplayer places. One download installs the Client and Studio, and each app updates itself when you start it.

You make places in Studio, add behavior with Luau scripts, and test it all with Play.

## What you need

A 64-bit Windows 10 or 11 PC. The install is per-user, inside your own profile, so it never asks for administrator rights and there is nothing else to install alongside it.

## Installing with Aero Setup

1. On the Downloads page, press **Download for Windows**. That downloads a setup executable to your device.
2. Run it and choose **Sign in with Aero**. Your browser opens so you can approve access there. Aero uses OAuth to authenticate the installer to your account.
3. Choose what to install. Pick **Aero Studio** to build games, or **Aero Client** to play them.
4. Choose where Aero goes. The default is `%localappdata%/Aero`.
5. Choose **Install**. When it finishes, the last page lets you launch what you just installed.

The installer never saves your credentials, and never sees them. To revoke its access later, use your account's [Privacy Settings](https://aeroengine.org/settings#privacy).

## Starting your apps

Open **Aero Client** or **Aero Studio** from the Start Menu. Each shortcut checks that app for updates first and applies them before starting, with a progress window only while something is downloading. If the server reports that everything is up to date, the app starts straight away.

Your apps show their build as **Build #** with the source commit next to it. The Client menu footer shows it, and Studio shows it in Help > About.

## Staying up to date

Launching an app through its shortcut goes through the Aero Launcher, which connects to Aero's servers to check for updates. If a newer build is available for that app, it downloads the build and then launches it. If an update is interrupted, relaunching picks up from where it left off.

The Downloads page also lists per-component zips for manual use. Those need a signed-in account to download, though the installer remains the easiest way to get Aero executables.

## Changing or removing Aero

Run `AeroSetup.exe` again with Aero already installed and it opens a maintenance page instead of the installer.

**Modify installation** walks the same screens to change components or locations. **Uninstall Aero** removes the apps, the shortcuts, and the saved OAuth sign-in. Your `.aepl` place files stay wherever you saved them and are never modified.

You can also uninstall from Windows Settings, where the entry is listed as **Aero Launcher**.

## If something goes wrong

Start with [Troubleshooting](../guides/troubleshooting.md). Installer and updater problems have their own rows there, alongside the script errors and crashes.

## See also

- [Studio tour](studio-tour.md) (the editor, panel by panel)
- [Quickstart](quickstart.md) (build and play a place in four steps)
- [Troubleshooting](../guides/troubleshooting.md) (installer and updater failures)
- [API Reference](../api/index.md)
