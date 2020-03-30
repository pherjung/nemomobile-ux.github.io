---
layout: article
title: Software developer kit
description: Get and setup nemo sdk
---

### Getting nemo sdk

Last nemo sdk you can dowload [here](https://yadi.sk/d/8GKbU0XbWW5_qw)

### Getting nemo build targets

* [aarch64](https://yadi.sk/d/nLqyIfFigcsfTA)
* [armv7hl](https://yadi.sk/d/hgKlglpnLugNvQ)
* [x86](https://yadi.sk/d/hwV22opW6fklAA)

### Install sdk

```bash
cd 
mkdir -p nemo/sdk
sudo tar --numeric-owner -pxjf nemo-sdk.tar.bz2 -C nemo/sdk
```

Add into you ~/.bashrc `alias nemosdk='$HOME/nemo/sdk/mer-sdk-chroot'`

### Install targets

```bash
cd
mkdir -p nemo/targets/nemo-$ARCH
sudo tar --numeric-owner -pxjf nemo-target_$ARCH -C nemo/targets/nemo-$ARCH
```

### Setup targets
Enter into nemo sdk `nemosdk` 

```bash
cd
sudo chown -R $USER nemo/targets/nemo-$ARCH
pushd nemo/targets/nemo-$ARCH
grep :$(id -u): /etc/passwd >> etc/passwd
grep :$(id -g): /etc/group >> etc/group

#For armv7hl
sb2-init -d -L "--sysroot=/" -C "--sysroot=/" -c /usr/bin/qemu-arm-dynamic -m sdk-build -n -N -t / nemo-$ARCH /opt/cross/bin/$ARCH-meego-linux-gnueabi-gcc

#For aarch64
sb2-init -d -L "--sysroot=/" -C "--sysroot=/" -c /usr/bin/qemu-aarch64-dynamic -m sdk-build -n -N -t / nemo-$ARCH /opt/cross/bin/$ARCH-meego-linux-gnueabi-gcc

#rebuild rpm db and ret last updates
sb2 -t nemo-$ARCH -m sdk-install -R rpm --rebuilddb
sb2 -t nemo-$ARCH -m sdk-install -R zypper ref --force
```

### Test sdk
Enter into nemo sdk `nemosdk` 

```bash
mkdir -p $HOME/nemo/tmp
pushd $HOME/nemo/tmp

cat > main.c << EOF
#include <stdlib.h>
#include <stdio.h>
int main(void) {
printf("Scratchbox, works!\n");
return EXIT_SUCCESS;
}
EOF

sb2 -t nemo-$ARCH gcc main.c -o test
sb2 -t nemo-$ARCH ./test

popd
```

### Build packages
Enter into nemo sdk `nemosdk` 

```bash
cd path_to_sources
mb2 build
```
