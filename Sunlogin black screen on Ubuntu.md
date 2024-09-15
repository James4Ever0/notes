---
title: Sunlogin black screen on Ubuntu
created: '2024-09-15T04:57:24.412Z'
modified: '2024-09-15T05:13:20.466Z'
---

# Sunlogin black screen on Ubuntu

First make sure only one user is using Sunlogin.

Next, switch to `lightdm` instead of `gdm3`:

```bash
sudo apt install -y lightdm
sudo dpkg-reconfigure lightdm
```

To check whether the current session is running on Xorg or Wayland on Ubuntu, you can use the following command in the terminal:

```bash
echo $XDG_SESSION_TYPE
```

When you run this command, it will display either "x11" if you are using Xorg or "wayland" if you are using the Wayland display server. This environment variable indicates the type of session you are currently using.

If it is "wayland", switch to Xorg instead of Wayland:

1. Open a terminal window by pressing `Ctrl+Alt+T`.
2. Edit the LightDM configuration file by running the following command:

```bash
sudo nano /etc/lightdm/lightdm.conf
```

3. Add the following lines at the end of the file to force the system to use Xorg:

```plaintext
[Seat:*]
xserver-command=X -core
```

4. Save the changes by pressing `Ctrl+O`, then press `Enter` to confirm. Exit the editor by pressing `Ctrl+X`.



