---
layout: post
permalink: /installation/
title: "Installation"
---

Glacier UI is the next interface for Nemo Mobile.
It is a new UI, created and built by the community, and made with the latest technologies like Qt 5 and Wayland.
For developing use [libglacierapp](#) and [qtquickcontrols-nemo](/qtquickcontrols-nemo/)

# Try it

## On a phone

* Download latest image from [img.nemomobile.net](https://img.nemomobile.net/) (for example [Manjaro-ARM-nemomobile-pinephone-0.3.img.xz](https://img.nemomobile.net/2021.05/Manjaro-ARM-nemomobile-pinephone-0.3.img.xz))
* Copy image on the &micro;SD card
```
xz -dc "Manjaro-ARM-nemomobile-pinephone-0.3.img.xz" | dd if=/dev/stdin of=/dev/mmcblk0 status=progress conv=fsync bs=4M
```



## Virtualbox

* Install standard [Manjaro Linux](https://manjaro.org/).
* Add repository nemomobile repository into `/etc/pacman.conf`. It must be first in the list.
```
[nemomobile]
SigLevel = Optional
Server = https://img.nemomobile.net/manjaro/10.2021/devel/x86_64/
```
* Install Nemomobile packages
```
pacman -S --noconfirm $(pacman -Slq nemomobile)
```
* Run `lipstick` or logout, choose Nemomobile, and logging in.

## I have a problem!

If you have some problems we welcome you to our IRC (#nemo on Freenode), [Matrix](https://matrix.to/#/#nemomobile:matrix.org) or [Telegram group](https://t.me/NemoMobile).
You can also post issues on [our issue tracker](https://github.com/nemomobile-ux/glacier-home/issues)

On an issue you'll have to include the following information:

* Device
* Version of OS or component
* A description of the problem
* Links to log
