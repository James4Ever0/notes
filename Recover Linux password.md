---
created: 2026-06-12T14:13:02+08:00
modified: 2026-06-12T14:13:12+08:00
---

# Recover Linux password

I'll explain how to edit the GRUB boot menu to reset your Linux password.

This method works because you're instructing the system to boot directly into a shell as the root user, bypassing the normal login process entirely.

📝 Step-by-Step Instructions

1. Reboot and Access the GRUB Menu

First, restart your computer. When the system starts booting, quickly access the GRUB menu:

· Legacy BIOS/Legacy Boot: Hold down the Left Shift key.
· UEFI System / Virtual Machine: Tap the Esc key repeatedly. If this doesn't work, you can also try pressing and holding the Shift key.

If you see the login screen, you have missed the timing. Simply restart and try again.

2. Edit the Boot Parameters

Once you're on the GRUB menu (a screen showing a list of operating systems or kernel versions), use the arrow keys to select your default boot entry and press the e key to edit it. Now, find the line that starts with linux (it could also be named linux16 or linuxefi). Use the arrow keys to scroll and move the cursor to the end of this line. You will need to make two important changes:

· Change ro to rw: Find where the line says ro (which stands for "read-only") and replace it with rw ("read-write"). This will give you the necessary permissions to change the password.
· Add the boot parameter: Add a space and then type init=/bin/bash at the very end of the line. This will tell the system to launch a root shell (bash) instead of the usual graphical interface.

After editing, your line should look something like this:
linux /vmlinuz-... root=/dev/sda... rw init=/bin/bash
(Note: Your specific numbers and codes will be different.)

3. Boot and Reset the Password

Press Ctrl+X or F10 to boot your system with these temporary changes. Instead of a normal login screen, you should be dropped into a # root command prompt. Now, you can reset the password for the user account you normally log in with. For example, to reset the password for a user named john, run:

```bash
passwd john
```

Important: If you receive an error like "Authentication token manipulation error", the root filesystem is not writable. If this happens, run the following command to manually remount it with write permissions, and then try the passwd command again:

```bash
mount -o remount,rw /
```

4. Final Steps

After successfully resetting your password, you need to reboot the system. The reboot command might not work from this minimal environment, so use the following command instead:

```bash
exec /sbin/init
```

Your system will now start up normally, and you can log in with your new password.

⚠️ Important Considerations & Troubleshooting

· This is a Security Feature, Not a Bug: This method is a standard recovery mechanism for Linux, not a vulnerability. Its existence is why physical security for servers and workstations is absolutely critical.
· Security Barriers (This method may not work if...)
  · GRUB is password-protected: If the bootloader itself is locked with a password, you won't be able to edit the boot entry.
  · Full Disk Encryption (LUKS) is used: If your hard drive is fully encrypted, the system cannot access the files to boot or change the password.
· Additional Notes for Some Systems
  · SELinux (Fedora, Rocky Linux, AlmaLinux): If your system uses SELinux (common in Fedora, CentOS/RHEL families), after the reboot, you may be unable to log in with your newly set password. To fix this, you will need to perform an automatic SELinux relabel. Reboot again, edit the same linux line, and this time, add autorelabel=1 at the end of the line before booting. This will fix file permissions and your new password should work afterwards.
  · File System Corruption: While rare, forcing a reboot after manually remounting the drive can, in theory, lead to file system inconsistencies. It's always a good idea to ensure you have a recent backup before using this type of recovery method.
