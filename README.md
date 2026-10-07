# OSK Fix

A GNOME Shell extension that forces the native on-screen keyboard (OSK) to appear in applications that don't normally trigger it.

Native Wayland apps work out of the box; the keyboard is forced in apps that don't request it (Vivaldi, Chromium, Electron).

> Tested on GNOME 50 and 51.
> **XWayland applications are not supported yet.**

## Installation

### Drag and drop (recommended)

1. Download the release zip and extract it.
2. Drag the `osk-fix@houssemko.github.io` folder into `~/.local/share/gnome-shell/extensions/`.
3. Log out and back in, then enable it with `gnome-extensions enable osk-fix@houssemko.github.io` (or Extensions app → OSK Fix → on).

- **Release 1.10:** [osk-fix@houssemko.github.io.v1.10.shell-extension.zip](https://github.com/Linuxuser67/GNOME-OSK-fix/releases/download/1.10/osk-fix%40houssemko.github.io.v1.10.shell-extension.zip)

### One-line install

```bash
curl -sSL https://raw.githubusercontent.com/Linuxuser67/GNOME-OSK-fix/main/install.sh | bash
```

### Manual

```bash
git clone https://github.com/Linuxuser67/GNOME-OSK-fix.git
cd GNOME-OSK-fix
mkdir -p ~/.local/share/gnome-shell/extensions/osk-fix@houssemko.github.io/schemas
cp extension.js metadata.json README.md LICENSE \
   ~/.local/share/gnome-shell/extensions/osk-fix@houssemko.github.io/
cp schemas/org.gnome.shell.extensions.osk-fix.gschema.xml \
   ~/.local/share/gnome-shell/extensions/osk-fix@houssemko.github.io/schemas/
glib-compile-schemas ~/.local/share/gnome-shell/extensions/osk-fix@houssemko.github.io/schemas/
gnome-extensions enable osk-fix@houssemko.github.io
```

> **Note:** log out and back in after enabling (Wayland cannot restart GNOME Shell in-place).

## Activation

The extension is active only while *Settings → Accessibility → Screen Keyboard* is ON. Toggling it takes effect immediately — no reload needed.

## Troubleshooting

- If the journal reports a missing `gschemas.compiled`, compile the extension schemas:
  `glib-compile-schemas ~/.local/share/gnome-shell/extensions/osk-fix@houssemko.github.io/schemas/`
- To trace open/learn decisions, set `OSK_FIX_DEBUG=1` for the GNOME Shell process before login, then inspect:
  `journalctl --user -b | grep osk-fix`

## License

GPL-2.0-or-later — see [LICENSE](LICENSE) for details