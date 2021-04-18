---
layout: post
permalink: /installing-glacier/
title: "Installing Glacier"
---

Glacier can be installed on any device running SailfishOS.
This can be either the [SailfishOS emulator](https://releases.sailfishos.org/sdk/emulators/) or any armv7hl or i486 device running the latest SailfishOS.

You can also use [the VirtualBox image](#virtualbox-image)

## On SailfishOS 2.1.x.x and later

First, as a precautionary measure, change the _Default USB_ mode to _Developer mode_.
Allow _Remote connection_ from _Developer tools_ and set the password used for remote connections.
Also make sure to backup Jolla's Lipstick, just in case:

```
$ pkcon download /home/nemo/ lipstick-jolla-home-qt5
```

Now add the latest Glacier repoistory (note: this is the master branch of lipstick-glacier-home-qt5).
For the emulator and i486 devices:

```
# ssu ar nemo-devel-ux http://repo.merproject.org/obs/home:/neochapay:/nemo-ux/sailfish_latest_i486/
```

For armv7hl devices:

```
# ssu ar nemo-devel-ux http://repo.merproject.org/obs/home:/neochapay:/nemo-ux/sailfish_latest_armv7hl/
```

Then refresh the packages:

```
# pkcon refresh
```

Next, install the Glacier package:

```
# pkcon install lipstick-glacier-home-qt5
```

If Lipstick doesn't restart automatically, restart it manually:

```
# systemctl --user restart lipstick
```

You can install some extra example Glacier components:

```
# pkcon install qt5-qtquickcontrols-nemo-examples
```

### In case of panic
If something goes wrong and the display stays black after restarting Lipstick, you'll need to reinstall Jolla's Lipstick.

Connect your device to a computer using an USB connection and SSH into it (`192.168.2.15` is the default address. If you have changed it, replace it for the correct one):

```
$ ssh nemo@192.168.2.15
```

Then install the backup of `lipstick-jolla-home` made earlier:

```
# pkcon install-local lipstick-jolla-home-qt5-*
```

## Uninstalling
If for some reason you want to install Glacier, run the following commands:

```
# ssu dr nemo-devel-ux
# pkcon remove lipstick-glacier-home-qt5
# pkcon install lipstick-jolla-home-qt5
```

# VirtualBox image

First download [the SailfishOS Software Development Kit](https://sailfishos.org/wiki/Application_SDK).

The SDK has been verified on the following systems:
* Ubuntu 14.04, 32 & 64-bit
* Windows 8, 32 & 64-bit
* macOS 10.9.2

It should work fine on other Linux distributions as well, but this has not been tested.

Pre-requisites:
* A host machine running a Linux, Windows or macOS operating system
* VirtualBox version 4.1.18 or higher. Use the version that comes with your distribution
* About 5GB of free disk space
* 4GB or more RAM

Download the ready-made SailfishOS with Glacier UX VirtualBox image: [https://cloud.disroot.org/s/NneoSnjJWbKqXHn](https://cloud.disroot.org/s/NneoSnjJWbKqXHn)

Extract the tar file, for example to `~/SailfishOS/emulator`.

Open VirtualBox and select `SailfishOS Emulator`.
Open the settings of the selected virtual machine and select "Storage".
Change "sailfishos.vdi" to the extracted virtual machine image "SFOSGlacier.vdi".

To get the latest Nemo Mobile packages follow the installation instructions on the top of this page.
