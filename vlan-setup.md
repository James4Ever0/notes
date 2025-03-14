## router

on fortios, just use the web interface to configure vlan per physical interface.

on ssg5, create a vlan within a bgroup using `set interface bgroupx.y <vlan_params>`

## client

on windows, one use the device manager to configure the vlan id, or use vendor-specific tools to create a new network interface per vlan id.


---

on linux, one use `vconfig` or `ip` to configure a new vlan interface.

to make a vlan connection persistent, in networkmanager, one can run `nmcli con mod <ifname> connection.autostart yes`

