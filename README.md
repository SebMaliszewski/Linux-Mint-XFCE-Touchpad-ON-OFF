# Linux-Mint XFCE Touchpad ON/OFF

Toggle the laptop touchpad on Linux Mint (XFCE). One command turns it off or back on, with a desktop notification. Bind it to a panel launcher or a keyboard shortcut.

When the touchpad is disabled, X floats the device and prefixes its name with `∼ `. The script always resolves the device by id from a `Touchpad` line, so the toggle still finds it after it has been turned off.

## Requirements

- Linux Mint with the XFCE desktop (X11 session)
- `xinput`
- `notify-send` (desktop notifications; the toggle still works if this is missing)

```bash
sudo apt install xinput libnotify-bin
```

## Script

### `touchpad-toggle`

Finds the touchpad with `xinput list`, reads `Device Enabled`, and runs `xinput disable` or `xinput enable`.

Usage:

```bash
./touchpad-toggle
```

## Installation

Copy the script to a directory in your `PATH`, and the launcher to the applications menu:

```bash
mkdir -p ~/.local/bin ~/.local/share/applications
cp touchpad-toggle ~/.local/bin/
chmod +x ~/.local/bin/touchpad-toggle
cp touchpad-toggle.desktop ~/.local/share/applications/
update-desktop-database ~/.local/share/applications/ 2>/dev/null || true
```

`~/.local/bin` must be on `PATH` so the panel and the menu can run `touchpad-toggle`.

### Panel

Right-click the XFCE panel → Panel → Add New Items → Launcher, then add **Touchpad on/off**.

### Keyboard shortcut

Settings → Keyboard → Application Shortcuts → Add, command `touchpad-toggle`.

Example binding: `Ctrl+Super+T`.

## License

Open Source
