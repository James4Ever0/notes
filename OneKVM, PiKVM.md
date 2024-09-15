---
title: 'OneKVM, PiKVM'
created: '2024-09-08T14:57:25.399Z'
modified: '2024-09-15T05:59:51.737Z'
---

# OneKVM, PiKVM

USB connected video capture dongles tend to fail. We need to reset it often to prevent failures.

To restart the USB device, first figure out the USB identifiers by `lsusb`, then run the following Python code:

```python
# installable via: apt install python3-usb

```

To reset the CH9239 device after remounting USB, do this:

```python

```

To enable command execution by buttons on the web interface, write something like this under ``:

```yaml
```
