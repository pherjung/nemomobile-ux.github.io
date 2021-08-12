---
layout: post
title: Software developer kit
description: Get and setup nemo sdk
---

## Getting Nemo sdk

Install [nemomobile into Virtualbox](/installation/). Install `manjaro-arm-tools` and `base-devel` packages

```
pacman -Syyu
pacman -S manjaro-arm-tools base-devel
```

## Build packages

Start with Nemo packaging repository [packaging repository](https://github.com/nemomobile-ux/nemo-packaging) or with [manjaro-arm packages](https://gitlab.manjaro.org/manjaro-arm/packages/community/nemo-ux).
The build procedure is given by scripts in `PKGBUILD` file. 

### x86_64 build:

```bash
cd ./glacier-browser-git # enter the package directory
makepkg # build package
pacman -U glacier-browser*pkg* # install package
```

### aarch64 build:

```
buildarmpkg -k -p glacier-browser-git # skip -k when want clean chroot
```

The command expects working repository in chroot configuration:
```
/var/lib/manjaro-arm-tools/pkg/aarch64/etc/pacman.conf
```

To add new package into repository copy the file into directory and run repo-add:
```
repo-add -q "nemomobile.db.tar.xz" "*.pkg.tar.*"
```

## Building rootfs

The rootfs images are based on packages it self and recipe how to bake them together.
There is a list of packages to use, list of services to enable, and other configuration. This
is specific for device and desktop environment. This is in arm-profiles repository. The
buildarmimg downloads upstream repository into `/usr/share/manjaro-arm-tools/profiles/arm-profiles`.
It should be replaced by nemomobile branch from  [https://github.com/nemomobile-ux/arm-profiles/tree/nemomobile](arm-profiles)..

The rootfs image could be build as follows:

```
sudo buildarmimg -d pinephone -e nemomobile -k https://img.nemomobile.net/manjaro/10.2021/devel/aarch64/nemomobile.db
```
