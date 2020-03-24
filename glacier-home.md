---
layout: article
permalink: /glacier-home/
title: "Glacier Home"
---

Glacier UI is the next interface for Nemo mobile. It is a new UI, created and built 
by the community, and made with latest technologies like Qt 5 and Wayland. For developing use [libglacierapp](#) and [qtquickcontrols-nemo](/qtquickcontrols-nemo/)

# Try it

## On phone

Before experimenting with Glacier UX you should install developer mode and follow the [installing instructions](#).

*Please, note: Glacier UX is in alpha stage, so any contributions (including testing) are welcome! :)*

## Virtualbox


For build glacier image use Sailfish SDK and [this](https://gist.github.com/neochapay/59d7ac23691f97b683104c93aff23266 nemo-clean.ks) file. 

In first we must update mic in sdk

```SDK# sudo su```
```SDK# zypper ar -G http://repo.merproject.org/obs/mer:/core/latest_i486/ mer-up```
```SDK# zypper ar -G http://repo.merproject.org/obs/home:/neochapay:/mer:/tools/latest_i486/ mer-tools```
```SDK# zypper ref```
```SDK# zypper in mic```

Build command is 

```SDK# cd $ANDROID_ROOT```
```SDK# export PORT_ARCH=aarch64 #replace to you arch```
```SDK# sudo mic create fs --arch=$PORT_ARCH --tokenmap=ARCH:$PORT_ARCH --record-pkgs=name,url --outdir=nemo-test --pack-to=nemo_test-$PORT_ARCH.tar.bz2``` ```nemo_clean.ks```

## I have a problem!

if you have some problem welcome to irc or telegram groups. Or you can post issue in [git](https://github.com/nemomobile-ux/glacier-home/issues)

In issue you must post

* Device
* Version Nemo/SailfishOS
* Description of problems
* Links to log


## References

* [Qwazix's blog -- Design](http://play.qwazix.com/grog/)
* [Nemo Mobile IRC logs](http://play.qwazix.com/grog/)
* [Nemo UX git](https://github.com/nemomobile-ux)
* [Nemo git](https://github.com/nemomobile)
