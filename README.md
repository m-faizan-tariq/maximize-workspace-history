# MaximizeWorkspaceHistory

Like macOS — puts windows in a new workspace when maximized or full-screened and brings you back to the original workspace when unmaximized, unfull-screened, or the window gets closed.

Fork of `AmanCode22/MaximizeWorkspaceHistory` updated to support **GNOME Shell 50** (tested on Ubuntu 26.04 LTS) with app exclusion support.

[![screenshot](https://github.com/AmanCode22/MaximizeWorkspaceHistory/raw/master/screenshot.png)](https://github.com/AmanCode22/MaximizeWorkspaceHistory)

## Requirements

- Linux with **GNOME on Wayland** (tested on Ubuntu 26.04, GNOME Shell 50)
- GNOME Shell 45+

## Installation

### Download the packaged extension

Download the `.shell-extension.zip` from the [Releases](https://github.com/m-faizan-tariq/maximize-workspace-history/releases) page and install:

```bash
gnome-extensions install maximize-workspace-history@amancode22.github.com.shell-extension.zip --force
```

### Build from source

```bash
git clone https://github.com/m-faizan-tariq/maximize-workspace-history.git
cd maximize-workspace-history
gnome-extensions pack --force
gnome-extensions install maximize-workspace-history@amancode22.github.com.shell-extension.zip --force
```

### Post-install

| Session | Restart method |
|---------|---------------|
| **X11** | Press `Alt+F2`, type `r`, press Enter |
| **Wayland** | Log out and log back in |

After restart, enable the extension:

```bash
gnome-extensions enable maximize-workspace-history@amancode22.github.com
```

## Excluding apps

The extension skips windows whose **WM_CLASS** or **app ID** matches the `_excludedApps` list in `extension.js`. To exclude an app, add its identifier:

```javascript
this._excludedApps = ['app-name', 'app-name.desktop', 'wm-class-name'];
```

Current exclusions: `text-sniper`, `flameshot` (TextSniper for Linux).

## Files

| File | Purpose |
|------|---------|
| `extension.js` | Main extension logic |
| `metadata.json` | Extension metadata (GNOME 45-50) |
| `*.shell-extension.zip` | Packaged extension for installation |

## How it works

```
Window maximized ──> New workspace ──> Window unmaximized ──> Original workspace
                                                                      │
Window closed ────────────────────────────────────────────────────────┘
```

## Credits

- [AmanCode22/MaximizeWorkspaceHistory](https://github.com/AmanCode22/MaximizeWorkspaceHistory) — base fork with GNOME 45+ ESM support
- [raonetwo/MaximizeToWorkspace](https://github.com/raonetwo/MaximizeToWorkspace) — original extension
- `rliang` and `satran` — workspace history logic

## License

Apache-2.0
