# Status Tray

A GNOME Shell extension that brings back the system tray for applications using StatusNotifierItem (AppIndicator/SNI) protocol.

<!-- SCREENSHOT_PLACEHOLDER: Main screenshot showing Status Tray in action with several tray icons visible in the GNOME panel. Recommended size: 800x100px or similar showing just the panel area. Filename suggestion: screenshot-panel.png -->   

## Features

- **Zero Configuration** - Works out of the box, no external daemon required
- **Automatic Discovery** - Finds and displays all tray icons automatically
- **Native Menus** - Full support for application context menus via DBusMenu
- **Dual Icon Modes** - Choose between symbolic (monochrome) or original (colored) icons
- **Highly Customizable** - Per-app icon overrides, effects, and ordering
- **Drag & Drop Reordering** - Arrange tray icons in your preferred order
- **Live Updates** - All changes apply instantly without restart

## Compatibility

| GNOME Version | Status |
|---------------|--------|
| GNOME 45 | Supported |
| GNOME 46 | Supported |
| GNOME 47 | Supported |
| GNOME 48 | Supported |
| GNOME 49 | Supported |

### Tested Applications

- Nextcloud
- Discord
- Slack
- Bitwarden
- Dropbox
- Telegram
- Steam
- And many more...

## Installation

### From extensions.gnome.org (Recommended)

<!-- TODO: Add link once published -->
Visit the [Status Tray extension page](https://extensions.gnome.org/) and click "Install".

### Manual Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/keithvassallomt/status-tray.git
   cd status-tray
   ```

2. Run the install script:
   ```bash
   ./install.sh
   ```

3. Restart GNOME Shell:
   - **X11**: Press `Alt+F2`, type `r`, press Enter
   - **Wayland**: Log out and log back in

4. Enable the extension:
   ```bash
   gnome-extensions enable status-tray@keithvassallo.com
   ```

## Usage

Once installed and enabled, Status Tray automatically appears in your GNOME panel whenever an application registers a tray icon. Simply:

1. **Click** on a tray icon to open its menu
2. **Select** menu items to interact with the application

<!-- SCREENSHOT_PLACEHOLDER: Screenshot showing an open tray menu (e.g., Nextcloud or Discord menu). Recommended size: 400x300px. Filename suggestion: screenshot-menu.png -->

## Configuration

Access settings through GNOME Extensions app or by running:

```bash
gnome-extensions prefs status-tray@keithvassallo.com
```

<!-- SCREENSHOT_PLACEHOLDER: Screenshot of the preferences window showing the main settings view with app list. Recommended size: 600x500px. Filename suggestion: screenshot-prefs.png -->

### Icon Mode

Choose how tray icons are displayed:

| Mode | Description |
|------|-------------|
| **Symbolic** | Monochrome icons that match your shell theme (default) |
| **Original** | Full-color icons as provided by applications |

<!-- SCREENSHOT_PLACEHOLDER: Side-by-side comparison showing the same icons in symbolic vs original mode. Recommended size: 400x100px. Filename suggestion: screenshot-icon-modes.png -->

### App Management

- **Enable/Disable Apps** - Toggle visibility for individual applications
- **Drag & Drop** - Reorder apps by dragging the handle on the left

### Custom Icons

Override any app's icon with a system icon or custom image:

1. Click the icon picker button next to an app
2. Search for a system icon or click "Choose File..." for a custom image
3. Click "Apply" to save

<!-- SCREENSHOT_PLACEHOLDER: Screenshot of the icon picker dialog showing the icon grid and search. Recommended size: 500x400px. Filename suggestion: screenshot-icon-picker.png -->

### Icon Effects

Fine-tune how icons appear in symbolic mode:

- **Desaturation** - Control grayscale conversion (0% = color, 100% = grayscale)
- **Brightness** - Adjust icon brightness
- **Contrast** - Adjust icon contrast
- **Tint** - Apply a custom color tint

<!-- SCREENSHOT_PLACEHOLDER: Screenshot of the icon effect dialog showing the sliders and preview. Recommended size: 400x350px. Filename suggestion: screenshot-effects.png -->

## How It Works

Status Tray implements the StatusNotifierItem (SNI) protocol, the modern replacement for the legacy XEmbed system tray. It provides its own `org.kde.StatusNotifierWatcher` D-Bus service, allowing applications to register tray icons directly with the extension.

### Key Technical Features

- **Self-contained** - No dependency on external daemons like `snixembed` or AppIndicator libraries
- **DBusMenu Integration** - Fetches dynamic menus directly from applications
- **Electron Support** - Handles Electron/Chromium apps that use custom icon paths
- **Flatpak Compatible** - Gracefully handles sandboxed applications

## Troubleshooting

### Icons not appearing

1. Ensure the extension is enabled:
   ```bash
   gnome-extensions list --enabled | grep status-tray
   ```

2. Check if the app is disabled in settings

3. Restart the application after enabling the extension

### Menu not opening

Some applications may take a moment to initialize their menus. If clicking has no effect:

1. Wait a few seconds and try again
2. Check application logs for errors

### Icons look wrong

1. Try switching between Symbolic and Original icon modes
2. Use the icon override feature to set a custom icon
3. Adjust icon effects for better visibility

### Viewing Logs

```bash
journalctl -f -o cat /usr/bin/gnome-shell 2>&1 | grep -i status-tray
```

## Contributing

Contributions are welcome! Please see the [developer documentation](docs/status-tray.md) for technical details.

### Development Setup

1. Clone and install in development mode:
   ```bash
   git clone https://github.com/keithvassallomt/status-tray.git
   cd status-tray
   ./install.sh --dev
   ```

2. Make your changes

3. Restart GNOME Shell to test

4. Submit a pull request

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- The GNOME Shell team for the excellent extension API
- The KDE team for the StatusNotifierItem specification
- The AppIndicator project for pioneering modern system tray support

---

<p align="center">
  Made with care for the GNOME community
</p>
