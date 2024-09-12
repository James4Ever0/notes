---
created: 2024-09-12T15:42:03+08:00
modified: 2024-09-12T15:42:42+08:00
---

# Disable wayland on Ubuntu

To change the default display server from Wayland to X11 in Ubuntu 22.04 using the terminal, you can follow these steps:

1. **Open a Terminal**:
   - You can open a terminal by pressing `Ctrl + Alt + T` or by searching for "Terminal" in the application menu.

2. **Edit the GDM Configuration**:
   - Run the following command to edit the GDM (GNOME Display Manager) configuration file:
     ```bash
     sudo nano /etc/gdm3/custom.conf
     ```

3. **Uncomment the WaylandEnable=false Line**:
   - In the text editor that opens, find the line that says `#WaylandEnable=false` and remove the `#` at the beginning of the line to uncomment it. This line disables the Wayland display server.
     ```plaintext
     WaylandEnable=false
     ```

4. **Save and Close the File**:
   - Press `Ctrl + O` to save the file, then press `Enter`. Press `Ctrl + X` to exit the text editor.

5. **Restart GDM**:
   - To apply the changes, restart the GNOME Display Manager (GDM) by running:
     ```bash
     sudo systemctl restart gdm
     ```

6. **Log Out and Log Back In**:
   - After restarting GDM, you can log out of your current session and log back in. When you log back in, you should be using the X11 display server instead of Wayland.

By following these steps in the terminal, you can switch the default display server from Wayland to X11 in Ubuntu 22.04. This change will persist across reboots until you modify the GDM configuration again.
