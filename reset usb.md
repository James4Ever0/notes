---
title: reset usb
created: '2022-12-15T16:33:24.445Z'
modified: '2023-08-13T08:30:10.223Z'
---

# reset usb

the same for `/sys/bus/usb/drivers/*`.

----
in case kali failed to detect presence of hard disks, shall you pop up a dialog for us to decide whether to reset to usb or not.

## reset-usb.sh

```bash
#!/bin/bash
reset-ahci-controllers.sh
reset-xhci-controllers.sh
```

## reset-ahci-controllers.sh

```bash
#!/bin/bash

# this freaking works.

# Script to reset all local xHCI (USB) controllers
# Based on: http://billauer.co.il/blog/2013/02/usb-reset-ehci-uhci-linux/

if [[ ${EUID} != 0 ]]; then
	echo This must be run as root!
	exit 1
fi

for xhci in /sys/bus/pci/drivers/ahci; do
	if ! cd ${xhci}; then
		echo "Weird error. Failed to change directory to ${xhci}."
	exit 1
	fi
	echo "Resetting devices from ${xhci}..."
	for i in ????:??:??.?; do
		echo -n "${i}" > unbind
		echo -n "${i}" > bind
	done
done

```

## reset-xhci-controllers.sh

```bash
#!/bin/bash

# this freaking works.

# Script to reset all local xHCI (USB) controllers
# Based on: http://billauer.co.il/blog/2013/02/usb-reset-ehci-uhci-linux/

if [[ ${EUID} != 0 ]]; then
	echo This must be run as root!
	exit 1
fi

for xhci in /sys/bus/pci/drivers/?hci_hcd; do
	if ! cd ${xhci}; then
		echo "Weird error. Failed to change directory to ${xhci}."
	exit 1
	fi
	echo "Resetting devices from ${xhci}..."
	for i in ????:??:??.?; do
		echo -n "${i}" > unbind
		echo -n "${i}" > bind
	done
done

```
