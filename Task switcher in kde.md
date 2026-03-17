---
created: 2026-03-16T23:47:05+08:00
modified: 2026-03-17T18:09:15+08:00
---

# Task switcher in kde

Use tab search extension for chromium and Firefox, install and use standalone Firefox instead of snap version, use tmux for arranging and searching terminal, use terminal window instead of terminal tabs, detach important browser tabs as windows

Or use Mac with finda

---

You're in luck! KDE Plasma has a built-in tool called **KRunner** that can do exactly what you're looking for, and it can be enhanced to work even better across virtual desktops and with browser tabs.

## The Main Solution: KRunner

**KRunner** is the default application launcher and search tool in KDE Plasma (activated by default with `Alt+Space` or `Alt+F2`). It can search through your open windows by title and jump to them regardless of which virtual desktop they're on .

### Finding Browser Tabs

To search browser tabs specifically, you need the **Plasma Browser Integration**:

```bash
# Install the backend
sudo pacman -S plasma-browser-integration

# Then install the browser extension:
# - For Firefox: Search for "Plasma Integration" in add-ons
# - For Chromium: Install from Chrome Web Store
```

Once installed, make sure "Browser Tabs" is enabled in KRunner settings, and you'll be able to search your open browser tabs by title .

## Enhanced Window Title Search

By default, KRunner searches through applications, bookmarks, and various sources. If you want it to search **only by window titles**, you can create a custom shortcut:

### Option 1: Full Window List with Search (Recommended)

This shows all windows and lets you type to filter :

1. **Install xdotool**:
   ```bash
   sudo pacman -S xdotool
   ```

2. **Create the script** at `/usr/local/bin/krunner-search-by-windows.sh`:
   ```bash
   #!/bin/bash
   qdbus org.kde.krunner /App querySingleRunner windows "" 
   sleep 0.2
   xdotool type 'window '
   xdotool key "shift+BackSpace"
   ```

3. **Make it executable**:
   ```bash
   sudo chmod a+x /usr/local/bin/krunner-search-by-windows.sh
   ```

4. **Set up the keyboard shortcut**:
   - Go to System Settings → Shortcuts → Custom Shortcuts
   - Right-click → "New" → "Global Shortcut" → "Command/URL"
   - In "Trigger" tab: Set your desired key combination
   - In "Action" tab: Enter `/usr/local/bin/krunner-search-by-windows.sh`

### Option 2: Simpler D-Bus Approach

For a cleaner but slightly more limited approach, use a D-Bus command directly :

1. Go to System Settings → Shortcuts → Custom Shortcuts
2. Right-click → "New" → "Global Shortcut" → "D-Bus Command"
3. Configure:
   - **Remote application**: `org.kde.krunner`
   - **Remote Object**: `/App`
   - **Function**: `querySingleRunner`
   - **Arguments**: `windows ""`

## How It Works Across Virtual Desktops

Both methods above will show you **all windows from all virtual desktops** in the search results. When you select a window, KRunner will automatically switch to that virtual desktop and focus the window .

## Additional Tips

- **Meta Key Shortcut**: You can set the Meta (Windows) key to open KRunner:
  ```bash
  kwriteconfig5 --file kwinrc --group ModifierOnlyShortcuts --key Meta "org.kde.krunner,/App,,display"
  kwin_x11 --replace  # For X11
  # or
  kwin_wayland --replace  # For Wayland
  ```

- **Task Switcher Alternatives**: If you prefer a visual window switcher, you can explore alternative layouts in System Settings → Window Management → Task Switcher, with many options available on the [KDE Store](https://store.kde.org/) .

KRunner is incredibly powerful and should give you the exact workflow you're used to from Finda or Raycast!
