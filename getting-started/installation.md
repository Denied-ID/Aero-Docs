# Installation

Aero is a standalone creator-first multiplayer gaming platform. You make places in Studio, add behavior with Luau scripts, and test it all with Play. One download covers everything: Aero Setup installs the Aero Client and Aero Studio, and each app updates itself when you start it.

## What you need

A 64-bit Windows 10 or 11 PC. The install is per-user, inside your own profile, so it never asks for administrator rights and there is nothing else to install alongside it.

## Installing with Aero Setup

1. On the Downloads page, press **Download for Windows**. When you press that button, it downloads a setup executable to your device.
2. Run it and choose **Sign in with Aero**. Your browser should open so you can approve access there. Aero uses OAuth to authenticate the installer to your account, which is very secure.

The installer will never save your credentials, let alone see it. In case you ever want to revoke permissions from its authentication, you can do so via your account's [Privacy Settings](https://aeroengine.org/settings#privacy) at any time.

3. After that, you can select what you want to install. If you want to build games, choose **Aero Studio**. If you want to play games, choose **Aero Client**.
4. Now you can choose where Aero gets installed to. Aero gets installed to `%localappdata%/Aero` by default.
5. Now choose **Install**! When it finishes, the last page allows you to launch what you just installed.

## Starting your apps

Open **Aero Client** or **Aero Studio** from the Start Menu. Each shortcut checks that app for updates first and applies them before starting, with a progress window only while something is actually downloading. If the server reports that everything is up-to-date, the app starts without issue.

Your apps show their build as **Build #** with the source commit next to it. The Client menu footer shows it, and Studio shows it in Help > About.

## Staying up to date

Launching an app through its shortcut goes through the Aero Launcher, which automatically connects to Aero's servers to check for any available updates. If a newer build is available for that app, it automatically downloads said build, and then proceeds to launch. If an update is ever interrupted, relaunching picks up from where it left off.

The Downloads page also lists per-component zips for manual use. Those need a signed-in account to download, though the installer is the best way to get Aero executables seamlessly.

## Changing or removing Aero

Run `AeroSetup.exe` again with Aero already installed and it opens a maintenance page instead of the installer.

**Modify installation** walks the same screens to change components or locations, and **Uninstall Aero** removes the apps, the shortcuts, and the saved OAuth sign-in. Your `.aepl` place files stay wherever you saved them and are never modified.

You can also uninstall from Windows Settings, where the entry is listed as **Aero Launcher**.

## If something goes wrong

Start with [Troubleshooting](../guides/troubleshooting.md). Installer and updater problems have their own rows there, alongside the script errors and crashes.

## Where to go next

Read the [Studio Tour](studio-tour.md) to learn the editor, then browse the [API Reference](../api/index.md) when you start scripting.
