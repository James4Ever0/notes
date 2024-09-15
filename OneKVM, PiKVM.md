---
title: 'OneKVM, PiKVM'
created: '2024-09-08T14:57:25.399Z'
modified: '2024-09-15T06:34:35.815Z'
---

# OneKVM, PiKVM

To 


Top view of a USB relay:

```
 _____
|     |
|     |
|     |
 -----
|  |  |
x  x
   

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
