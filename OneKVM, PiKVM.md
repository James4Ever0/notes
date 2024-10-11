---
title: OneKVM, PiKVM
created: 2024-09-08T14:57:25+00:00
modified: 2024-10-11T08:44:56+08:00
---

# OneKVM, PiKVM

OneCloud flashing reference:

https://files.mofeng.run/

https://one-kvm.mofeng.run/onecloud_install/

https://www.ecoo.top/update/soft_init/amlproject/USB_Burning_Tool_v2.1.3.exe

References:

https://one-kvm.mofeng.run

https://docs.pikvm.org/multiport

https://docs.pikvm.org/gpio

Alternative:

https://github.com/BigfootACA/webrtc-kvm

https://github.com/binnerhot/KVM-over-USB

CH9329 references:

https://blog.csdn.net/WCH_TechGroup/article/details/132202410

---

We select pin `NO` and `CC` for our programmable switch.

Top view of a USB relay:

```
  ______
 |      |   NO - Normally Open
 |SONGLE|   CC - Commonly Connected
 |      |   NC - Normally Closed
  ------     x - Selected pins
 |   |  |
 x   x
 NO  CC NC  
```

We then solder the other ends to the back of the button. Before soldering you can glue the wires close to the metal ends.

```
 ____________ Wire A
  |__ __ __|
     |  | Button
  |-- -- --|
 ------------ Wire B
```

To command a USB relay, we save the code as `usbrelay.c` and compile with `gcc -o usbrelay usbrelay.c`:

```c
#include <linux/types.h>
#include <linux/input.h>
#include <linux/hidraw.h>
 
#include <sys/types.h>
#include <sys/ioctl.h>
#include <sys/stat.h>
 
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdint.h>
#include <fcntl.h>
#include <errno.h>
 
int find_usbrelay()
{
	int found = 0;
	int fd = -1;
	int result;
	int id;
 
	char path[32];
	
	const struct hidraw_devinfo usb_relay_info = 
	{
		.bustype = BUS_USB,
		.vendor = 0x5131,
		.product = 0x2007
	};
 
	struct hidraw_devinfo t_info;
 
	for(id = 0; !found; id++)	
	{
		sprintf(path, "/dev/hidraw%d", id);
 
		fd = open(path, O_RDWR | O_NONBLOCK);
		if (fd < 0)
			break;
 
		result = ioctl(fd, HIDIOCGRAWINFO, &t_info);
		if (result < 0)
			break;
	
		if ((t_info.bustype == usb_relay_info.bustype)
		&& (t_info.vendor == usb_relay_info.vendor)
		&& (t_info.product == usb_relay_info.product))
		{
			found = 1;
			break;
		}
 
		close(fd);
		fd = -1;
	}
 
	if (fd >= 0)
		close(fd);
 
	return found ? id : -1;
}
 
int set_usbrelay_onoff(int id, int ch, int onoff)
{
	int fd = -1;
	uint8_t cmd[8];
 
	char path[32];
 
	do
	{
		sprintf(path, "/dev/hidraw%d", id);
 
		fd = open(path, O_RDWR | O_NONBLOCK);
		if (fd < 0)
			break;
 
		cmd[0] = 0xA0;
		cmd[1] = ch;    // 1, 2
		cmd[2] = onoff; // 0, 1
		cmd[3] = cmd[0] + cmd[1] + cmd[2];
 
		write(fd, cmd, 4);
 
	} while(0);
 
	if (fd >= 0)
		close(fd);
 
	return 0;
}
 
int main(int argc, char *argv[])
{
	int result;
	int id;
	int ch;
	int onoff;
	char path[32];
 
	do
	{
		if (argc != 3)
		{
			printf("Usage:\n"
			"\tusbrelay ch on|off\n");
			break;
		}
 
		ch = atoi(argv[1]);
		if (strcmp(argv[2], "on") == 0)
			onoff = 1;
		else if (strcmp(argv[2], "off") == 0)
			onoff = 0;
		else
			break;
 
		id = find_usbrelay();
		if (id < 0)
		{
			printf("usbrelay not found\n");
			break;
		}
 
		set_usbrelay_onoff(id, ch, onoff);
 
	} while(0);
 
	return 0;
}

```
Then run:

```bash
# toggle the switch remotely
./usbrelay 1 on
./usbrelay 1 off
```

---

USB connected video capture dongles tend to fail. We need to reset it often to prevent failures.

To restart the USB device, first figure out the USB identifiers by `lsusb`, then run the following Python code:

```python
# installable via: apt install python3-usb
import usb.core

from usb.core import find as finddev

devices = [
        (0x<idVendor>, 0x<idProduct>),
        ]
for idVendor, idProduct in devices:
    dev = finddev(idVendor=idVendor, idProduct=idProduct)
    dev.reset()

```

To reset the CH9239 device after remounting USB, do this:

```python
import os
import time
import traceback
import serial

assert os.getuid() == 0, "You must be root to run this script."

SERIAL_DEVICE = "/dev/<serial_device_path"

RESET_BYTES = [0x57, 0xAB,0x00,0x0F,0x00]
CHECKSUM_BYTE = sum(RESET_BYTES)%256
RESET_BYTES_WITH_CHECKSUM = [*RESET_BYTES, CHECKSUM_BYTE]

RESET_PACKET = bytes(RESET_BYTES_WITH_CHECKSUM)


def reset_once():
    # Define the serial port and baud rate
    ser = serial.Serial(SERIAL_DEVICE, baudrate=9600, timeout=1)


    # Check if the port is open
    if ser.is_open:
        print("Serial port is open.")

        # Data to be sent over the serial port
        data_to_send = RESET_PACKET
        # Send data over the serial port
        ser.write(data_to_send)

        print("Data sent:", data_to_send.hex())
        reply = ser.read(100)
        print("Data read:", reply.hex())

        # Close the serial port
        ser.close()
        print("Serial port is closed.")
    else:
        print("Failed to open serial port.")

def reset_multiple(times=2):
    for index in range(times):
        print(f"[*] Round #{index+1}")
        try:
            reset_once()
        except:
            traceback.print_exc()
            print("[-] Failed to reset")
        finally:
            time.sleep(2)

if __name__ == "__main__":
    reset_multiple()

```

To enable command execution by buttons on the web interface, write something like this under `/etc/kvmd/override.d/gpio.yaml`:

```yaml
kvmd:
    gpio:
        drivers:
            toggle_switch:
                type: cmd
                cmd: ["<absolute_path_of_binary>", "<arg1>", ...]
        scheme:
            toggle_switch:
                driver: toggle_switch
                pin: 0
                mode: output
                switch: false
        view:
            table:
                - ["toggle_switch|confirm|Switch KVM machine"]
```
