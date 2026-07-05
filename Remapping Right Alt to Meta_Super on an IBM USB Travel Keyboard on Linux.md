---
created: 2026-07-05T11:27:44+08:00
modified: 2026-07-05T11:28:50+08:00
---

# Remapping Right Alt to Meta/Super on an IBM USB Travel Keyboard on Linux

## The Problem

The **IBM USB Travel Keyboard with Ultra Nav** (04b3:301e) is a classic piece of hardware, but on modern Linux desktops (KDE Plasma, GNOME, etc.), the **right Alt key** doesn't behave as a Meta/Super (Windows) key. Instead of opening the application launcher or triggering desktop shortcuts, it either does nothing useful or behaves as just another Alt modifier.

This blog walks through how to remap it using `udev`'s hardware database (`hwdb`) — no reboot required.

## Step 1: Find the Device

First, confirm your IBM keyboard is connected:

```
$ lsusb
Bus 005 Device 003: ID 04b3:301e IBM Corp. IBM USB Travel Keyboard with Ultra Nav
Bus 005 Device 002: ID 04b3:3016 IBM Corp. UltraNav Keyboard Hub
...
```

The device ID is `04b3:301e` (vendor `04b3`, product `301e`). The kernel exposes keyboard details under `/sys/`. We can find the right path by searching for "IBM" in the `name` files:

```
$ find /sys/ -iname '*name' -type f 2>/dev/null | while read f; do \
  content=$(cat "$f" 2>/dev/null); \
  if echo "$content" | grep -qi "IBM"; then echo "$f: $content"; fi; \
done

/sys/devices/pci0000:00/0000:00:08.1/0000:04:00.4/usb5/5-2/5-2.3/5-2.3:1.0/0003:04B3:301E.0007/input/input30/name: Lite-On Tech IBM USB Travel Keyboard with Ultra Nav
/sys/devices/pci0000:00/0000:00:08.1/0000:04:00.4/usb5/5-2/5-2.3/5-2.3:1.1/0003:04B3:301E.0008/input/input31/name: Lite-On Tech IBM USB Travel Keyboard with Ultra Nav Mouse
...
```

The keyboard input device is `input30`. Let's look at its modalias:

```
$ cat /sys/devices/pci0000:00/0000:00:08.1/0000:04:00.4/usb5/5-2/5-2.3/5-2.3:1.0/0003:04B3:301E.0007/input/input30/modalias

input:b0003v04B3p301Ee0100-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,sfw
```

The part **before the first dash** is the hardware match string for our hwdb entry: `input:b0003v04B3p301Ee0100`.

## Step 2: Find the Scan Code of Right Alt with evtest

We need to know what evdev scan code the right Alt key generates. Run `evtest` (requires root) and select the keyboard device (`event15` for the keyboard interface):

```
$ sudo evtest
...
/dev/input/event15:     Lite-On Tech IBM USB Travel Keyboard with Ultra Nav
...
Select the device event number [0-18]: 15
```

Press the right Alt key. The output looks like:

```
Event: time 1783221713.041636, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e6
Event: time 1783221713.041636, type 1 (EV_KEY), code 100 (KEY_RIGHTALT), value 1
Event: time 1783221713.105626, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e6
Event: time 1783221713.105626, type 1 (EV_KEY), code 100 (KEY_RIGHTALT), value 0
```

The scan code (`MSC_SCAN` value) is **`700e6`**. The kernel currently interprets it as `KEY_RIGHTALT` (code 100).

## Step 3: Find the Target Key Code

We want the right Alt key to behave as **Meta (Super/Windows key)**. From the Linux input-event-codes header:

```
$ grep -E 'KEY_LEFTMETA|KEY_RIGHTMETA|KEY_RIGHTALT' /usr/include/linux/input-event-codes.h

#define KEY_RIGHTALT     100
#define KEY_LEFTMETA     125
#define KEY_RIGHTMETA    126
```

We want to map it to `KEY_RIGHTMETA`, which has the numeric value **126**. Using the numeric value is more reliable than the symbolic name (some users report the symbolic name stops working after a while).

## Step 4: Create the hwdb File

Create `/etc/udev/hwdb.d/remap_liteon_ibmkb.hwdb`:

```
evdev:input:b0003v04B3p301Ee0100*
 KEYBOARD_KEY_700e6=126
```

Breaking this down:
- **Line 1**: The hardware match pattern — `evdev:` followed by the modalias prefix (up to the first `-`), with `*` glob to match any sub-variant.
- **Line 2**: `KEYBOARD_KEY_` followed by the scan code (`700e6`, from evtest), then `=` and the desired key code (`126` = `KEY_RIGHTMETA`).

## Step 5: Apply Without Reboot

Run these three commands to apply the remapping immediately:

```
$ sudo systemd-hwdb update
$ sudo udevadm control --reload-rules
$ sudo udevadm trigger
```

No reboot needed. Unplug and replug the keyboard, or just trigger the rules as above.

## Step 6: Verify

Run `evtest` again and press the right Alt key. It should now show `KEY_RIGHTMETA`:

```
Event: time 1783221714.177625, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e6
Event: time 1783221714.177625, type 1 (EV_KEY), code 126 (KEY_RIGHTMETA), value 1
Event: time 1783221714.241812, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e6
Event: time 1783221714.241812, type 1 (EV_KEY), code 126 (KEY_RIGHTMETA), value 0
```

Now right Alt opens your application launcher and works as a Super/Meta key in shortcuts.

## Summary of Commands

| Step | Command | Purpose |
|------|---------|---------|
| 1 | `lsusb` | Find the USB vendor/product ID |
| 2 | `find /sys/ -iname '*name' -type f ...` | Locate the sysfs path for the keyboard |
| 3 | `cat .../input/XXX/modalias` | Get the hwdb modalias string |
| 4 | `sudo evtest` | Find the scan code of the key to remap |
| 5 | Edit `/etc/udev/hwdb.d/remap_*.hwdb` | Write the remapping rule |
| 6 | `sudo systemd-hwdb update` | Update the hardware database |
| 7 | `sudo udevadm control --reload-rules` | Reload udev rules |
| 8 | `sudo udevadm trigger` | Re-trigger device events |
| 9 | `sudo evtest` | Verify the key now emits the correct code |

## Why hwdb and Not xmodmap or setxkbmap?

- **xmodmap** is X11-only and doesn't work reliably for Alt-to-Meta remapping (the KDE forum thread confirms this).
- **setxkbmap** options are often overridden by desktop environments.
- **hwdb** works at the evdev layer, before X11 or Wayland even sees the key event. It's compositor-agnostic and survives application focus changes.
## Alternative: Using xremap (Untested / Unverified)

[xremap](https://github.com/xremap/xremap) is a Rust-based key remapper for Linux that supports both X11 and Wayland, with app-specific and device-specific remapping. Unlike hwdb, it runs as a userspace daemon and can handle more complex mappings (key sequences, hold-vs-tap behavior, application-specific overrides).

Based on the project's README, the approach would be:

### Installation

xremap can be installed via `cargo` or downloaded from the [releases page](https://github.com/xremap/xremap/releases). The feature flag depends on your desktop environment:

```bash
# For KDE-Plasma Wayland
cargo install xremap --features kde

# For GNOME Wayland
cargo install xremap --features gnome

# For X11
cargo install xremap --features x11

# For wlroots-based compositors (Sway, Wayfire, etc.)
cargo install xremap --features wlroots
```

### Configuration

Create a config file, e.g. `~/.config/xremap/config.yml`:

```yaml
modmap:
  - name: IBM Keyboard Right Alt to Meta
    device:
      only: "Lite-On Tech IBM USB Travel Keyboard with Ultra Nav"
    remap:
      KEY_RIGHTALT: KEY_RIGHTMETA
```

Key points from the README:
- **`modmap`** is used for key-to-key remapping (like xmodmap). Use this for remapping a physical key to a modifier.
- **`device.only`** restricts the remapping to just this keyboard, so other keyboards are unaffected. The device name can be a full path like `/dev/input/event15`, a device name substring, or a vendor/product ID like `ids:0x04b3:0x301e`.
- Key names are case-insensitive with the `KEY_` prefix optional: `KEY_RIGHTALT`, `RIGHTALT`, and `RightAlt` are all equivalent.

### Running xremap

**With sudo** (simplest):

```bash
sudo xremap config.yml
```

**Without sudo** — requires setting up a `uinput` udev rule so the user has write access to `/dev/uinput`. The README mentions this is possible but doesn't detail the exact steps.

**As a systemd service** — xremap can be run as a system service using the `--features socket` variant, enabling it to start at boot and persist across sessions.

### Caveats

- This approach is **untested** for this specific IBM keyboard. The hwdb method above is confirmed working.
- xremap has been responsive to device remapping. If the `device.only` filter doesn't match, you can identify the correct device name/ID by running `xremap --list-devices` or checking the startup logs.
- For device-specific matching, the README also supports vendor/product IDs in the format `ids:0x04b3:0x301e`, which may be more reliable than matching on device name.
- Since xremap runs as a daemon, it needs to be started at login (or as a system service) for the remapping to persist across reboots.
- Unlike hwdb, xremap operates on the processed key event stream, not at the evdev hardware layer. This gives it more flexibility (app-specific remapping, key sequences) but also means it must be running for the remapping to work.

### When to Use xremap Instead of hwdb

- You need **app-specific remapping** (e.g., right Alt is Meta everywhere except in a terminal).
- You want **hold-vs-tap behavior** (tap for Alt, hold for Meta).
- You need **key sequences** (e.g., Alt+Space → Ctrl+Alt+T).
- You prefer a **declarative YAML config** over editing hwdb files.
- You want to **avoid editing system files** under `/etc/`.

## References

- [KDE Discuss: Mapping right-Alt to Meta (Windows/Super) key](https://discuss.kde.org/t/mapping-right-alt-to-meta-windows-super-key/7627/2)
- [xremap - key remapper for Linux](https://github.com/xremap/xremap)
- [Linux input-event-codes.h](https://github.com/torvalds/linux/blob/master/include/uapi/linux/input-event-codes.h)
-
