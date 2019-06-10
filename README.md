Samsung Remote Control Keytable
=====================================
IR Keytable of Samsung Remote Control for `ir-keytable`

What is it ?
-----------
This repository contains IR keytable of "No-Smart-TV" Samsung Remote Control for `ir-keytable` command. 
This keytable has been tested on LibreElec 9.0.2.
It is not compatible on previous major versions of LibreElec (< 9.0), due to LIRC implementation.

However, this keytable would be compatible on every Linux-based system, with `ir-keytable` command installed.

How to
----------
1. First, run `ir-keytable` to find out which protocols your IR receiver driver supports - look at the Supported protocols: line. eg:
```
LibreELEC:~ # ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event1) with:
        Driver gpio-rc-recv, table rc-rc6-mce
        Supported protocols: lirc rc-5 rc-5-sz jvc sony nec sanyo mce_kbd rc-6 sharp xmp
        Enabled protocols: lirc nec rc-6
        Name: gpio_ir_recv
        bus: 25, vendor/product: 0001:0001, version: 0x0100
        Repeat delay = 500 ms, repeat period = 125 ms
```
2. Secondly, check if `nec` protocol is supported by your IR receiver (mandatory for "No-Smart-TV" Samsung Remote Control). If not, your receiver won't decode IR signal from remote.
3. Copy `my_samsung` keytable file to `/storage/.config/rc_keymaps/`
4. Load this keytable via `ir-keytable -c -w /storage/.config/rc_keymaps/my_samsung`. eg:
```
LibreELEC:~ # ir-keytable -c -w /storage/.config/rc_keymaps/my_samsung
Read justboom table
Old keytable cleared
Wrote 33 keycode(s) to driver
Protocols changed to nec
```
5. Once loaded, you should control your Kodi by pressing some buttons on your remote.
6. If testing succeeds, make it permanent via a `/storage/.config/rc_maps.cfg` file like this:
```
* * my_samsung
```
7. Then reboot and you should have a working remote in Kodi.

Testing systems
----------
- LibreElec 9.0.2

Link
----------
[Infrared Remotes LibreElec Documentation ](https://wiki.libreelec.tv/infrared_remotes)
