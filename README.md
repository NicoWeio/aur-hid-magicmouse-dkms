# linux-hid-magicmouse

While the [Linux kernel](https://github.com/torvalds/linux) has a working driver for the *Magic Trackpad 2*,
it does not support “host click mode“,
which in turn means that the haptic feedback cannot be customized.

[https://github.com/nexustar/linux-hid-magicmouse](nexustar/linux-hid-magicmouse) solves this by allowing to pass parameters like so:
```shell
sudo modprobe -r hid_magicmouse && \
sudo modprobe hid-magicmouse host_click=on button_up_param=0x26300000 button_down_param=0x80100000
```

You can use the included install script, **or you can use this PKGBUILD**.

It works, but this is my first attempt at writing a PKGBUILD.
I did not submit it to the AUR yet.
