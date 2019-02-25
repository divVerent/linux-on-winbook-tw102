# Getting Linux to run on a Winbook TW102

I've recently obtained a small Windows 10 tablet, namely the
[Winbook TW102](https://www.microcenter.com/product/496688/winbook-tw102-101-2-in-1-laptop-computer---black),
together with its recommended keyboard. Together this makes a nice 10"
tablet that you can actually run Linux on.

I wanted to run Linux on it, and got it to mostly work, including
the following hardware:

* Intel graphics, including OpenGL and Vulkan
* Display backlight
* Keyboard
* Sound (needed non-free firmware)
* WiFi (needed non-free firmware)
* Touchscreen (needed "hard to obtain" non-free firmware)
* Bluetooth (needed non-free firmware)

For now I have _not_ gotten the following to work:

* Camera

# What You Need

You'll need the following things available:

* Another machine running desktop Linux (any distro should do)
* An USB flash drive you're OK to reformat with at least 4GB of storage
* If you did not get the keyboard that attaches to the device, any
  external USB keyboard and a USB hub

# Booting Linux

So first, you need to boot a Linux image on it via USB.

Unfortunately, this device runs a 32bit UEFI and you'll probably want
to install a 64bit Linux distribution. Only few distributions actually
support this combination; Debian has a "multiarch" netinstall ISO that
will do, however from that I couldn't get WiFi to connect.

Also, it clearly should be something somewhat lightweight, given you
only have 2GB RAM in the device.

So I went with [Lubuntu 18.04 LTS](https://lubuntu.me/bionic-released/) and [isorespin.sh](https://github.com/kenorb-contrib/isorespin).

To create a bootable flash drive, just run `isorespin.sh`, point it at
the ISO, and tell it to apply changes for Atom devices. While at it,
you also should edit the kernel parameters to append `fbcon=rotate:1`
so you get readable boot messages without tilting your head.

# Installing Linux

So before you install anything, you should test that any hardware you
really require will work off your live image. With the aforementioned ISO,
WiFi worked immediately (albeit slow), so I went ahead.

To better try things out, open a terminal and type
`xrandr --output DSI-1 --rotate right`.
This will switch the screen to landscape mode, so you can see what you're
doing when typing.

# Setting up Intel Graphics

The GPU should already work fine out of the box; recommended improvements are:

## Default to Landscape Orientation

## Fix Tearing

## Enable Vulkan

# Setting up Sound

# Fixing WiFi Speed

To get better WiFi speed, upgrade your kernel to at least
`4.20`, e.g. by downloading a newer kernel package from
[kernel-ppa](https://kernel.ubuntu.com/~kernel-ppa/mainline/).

Beware: starting at `4.20.1`, the MicroSD card slot stops working -
haven't tracked down the cause and possible fixes yet.

# Setting up the Touch Screen

# Setting up Bluetooth
