---
layout: article
title: Software developer kit
description: Get and setup nemo sdk
---

### Getting nemo sdk

Last nemo sdk you can dowload [here](http://img.nemomobile.net/2020.05/nemo_sdk-2020.05.i486.tar.bz2)

### Getting nemo build targets

* [aarch64](http://img.nemomobile.net/2020.05/nemo_target-2020.05.aarch64.tar.bz2)
* [armv7hl](http://img.nemomobile.net/2020.05/nemo_target-2020.05.armv7hl.tar.bz2)
* [x86](http://img.nemomobile.net/2020.05/nemo_target-2020.05.i486.tar.bz2)

### Install sdk

```bash
cd 
export MER_ROOT=$HOME/mer
mkdir -p $MER_ROOT/sdks/nemosdk
sudo tar --numeric-owner -pxjf ~/Downloads/nemo-sdk.tar.bz2 -C $MER_ROOT/sdks/nemosdk
```

Add into you ~/.bashrc `alias nemosdk='$HOME/mer/sdks/nemosdk/mer-sdk-chroot'`

Update to last packages versions
sudo zypper ref
sudo zypper up

### Install targets

```bash
cd
mkdir -p ~/mer/targets/nemo-$ARCH
sudo tar --numeric-owner -pxjf nemo-target_$ARCH.tar.bz2 -C ~/mer/targets/nemo-$ARCH
```

### Setup targets
Enter into nemo sdk `nemosdk` 

```bash
cd
sudo chown -R $USER ~/mer/targets/nemo-$ARCH
pushd ~/mer/targets/nemo-$ARCH
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
