---
layout: post
permalink: /glacier-home/
title: "Glacier Home"
---

Glacier UI is the next interface for Nemo Mobile.
It is a new UI, created and built by the community, and made with the latest technologies like Qt 5 and Wayland.
For developing use [libglacierapp](#) and [qtquickcontrols-nemo](/qtquickcontrols-nemo/)

# Try it

## On a phone

Before experimenting with the Glacier UX you should enable the developer mode and follow the [installation instructions](#).

*Please, note: Glacier UX is in alpha stage, so any contributions (including testing) are welcome! :)*

## Virtualbox


To build a Glacier image, use Sailfish SDK and [this](https://gist.github.com/neochapay/59d7ac23691f97b683104c93aff23266) (nemo-clean.ks) file.

First we must update mic in the SDK:

```
SDK# sudo su
SDK# zypper ar -G http://repo.merproject.org/obs/mer:/core/latest_i486/ mer-up
SDK# zypper ar -G http://repo.merproject.org/obs/home:/neochapay:/mer:/tools/latest_i486/ mer-tools
SDK# zypper ref
SDK# zypper in mic
```

Build command is 

```
SDK# cd $ANDROID_ROOT
SDK# export PORT_ARCH=aarch64 #replace to you arch
SDK# sudo mic create fs --arch=$PORT_ARCH --tokenmap=ARCH:$PORT_ARCH --record-pkgs=name,url --outdir=nemo-test --pack-to=nemo_test-$PORT_ARCH.tar.bz2
nemo_clean.ks
```

## I have a problem!

If you have some problems we welcome you to our IRC (#nemo on Freenode), [Matrix](https://matrix.to/#/#nemomobile:matrix.org) or [Telegram group]((https://t.me/NemoMobile).
You can also post issues on [our issue tracker](https://github.com/nemomobile-ux/glacier-home/issues)

On an issue you'll have to include the following information:

* Device
* Version Nemo/SailfishOS
* A description of the problem
* Links to log


## References

* [Qwazix's blog -- Design](http://play.qwazix.com/grog/)
* [Nemo Mobile IRC logs](http://play.qwazix.com/grog/)
* [Nemo UX git](https://github.com/nemomobile-ux)
* [Nemo git](https://github.com/nemomobile)
