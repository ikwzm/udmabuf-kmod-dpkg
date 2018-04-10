udmabuf(User space mappable DMA Buffer) debian package
======================================================

Overview
------------------------------------------------------------------------------------

### Introduction

This is a repository for making udmabuf debian package.

Udmabuf is a Linux device driver that allocates contiguous memory blocks in the kernel space as DMA buffers and makes them available from the user space.

For details of udmabuf, please refer to following URL.

  * https://github.com/ikwzm/udmabuf

Build and Install in self
------------------------------------------------------------------------------------

### Download repository

```console
shell$ git clone git://github.com/ikwzm/udmabuf-debpkg
shell$ cd udmabuf-debpkg
```

### Checkout v1.1.0

```console
shell$ git checkout v1.1.0
shell$ git submodule init
shell$ git submodule update
```

### Build

```console
shell$ make

```


# Build Debian Package

## Parameters

  * kernel_release : Kernel Release Name     , default=$(shell uname -r)
  * arch           : Architecture Name       , default=$(shell uname -m | sed -e s/arm.*/arm/ -e s/aarch64.*/arm64/)
  * deb_arch       : Debian Architecture Name, default=$(shell dpkg --print-architecture)
  * kernel_src_dir : Kernel Source Directory , default=/lib/modules/$(kernel_release)/build

## Cross Compile for armv7

```console
shell$ sudo debian/rules arch=arm deb_arch=armhf kernel_release=4.14.21-armv7-fpga kernel_src_dir=/usr/src/linux-4.14.21-armv7-fpga binary
shell$ file ../udmabuf-4.14.21-armv7-fpga_1.1.0-1_armhf.deb
../udmabuf-4.14.21-armv7-fpga_1.1.0-1_armhf.deb: Debian binary package (format 2.0)
```

## Self Compile

```console
shell$ sudo debian/rules binary
```

