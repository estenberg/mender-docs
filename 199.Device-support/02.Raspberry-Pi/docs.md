---
title: Raspberry Pi series
taxonomy:
    category: docs
---

## Device description

The Raspberry Pi is a series of popular single board computers
based on Broadcom SoCs.

![Raspberry Pi 3 Model B](Raspberry-Pi-3-Flat-Top.jpg?lightbox&resize=400,200)


Vendor page: [https://www.raspberrypi.org](https://www.raspberrypi.org?target=_blank).


## Mender device support levels


| Device            | MACHINE variable | Mender support level |
|-------------------|------------------|----------------------|
| [Raspberry Pi Zero](https://www.raspberrypi.org/products/raspberry-pi-zero?target=_blank)      | raspberrypi0  | community |
| [Raspberry Pi 1](https://www.raspberrypi.org/products/raspberry-pi-1-model-b?target=_blank)    | raspberrypi   | community |
| [Raspberry Pi 2](https://www.raspberrypi.org/products/raspberry-pi-2-model-b?target=_blank)    | raspberrypi2  | community |
| [Raspberry Pi 3](https://www.raspberrypi.org/products/raspberry-pi-3-model-b?target=_blank)    | raspberrypi3  | reference |


## Configuring the build

### Prerequisites

A Yocto Project build environment with

* the Mender layers already added, and
* Mender's `local.conf` settings

as described in [Building a Mender Yocto Project image](../../artifacts/building-mender-yocto-image).


### Adding device-specific meta layers

Please make sure you are standing in the directory where `poky` resides, i.e. the top level of the Yocto Project build tree, and run this command:

```bash
git clone -b master git://git.yoctoproject.org/meta-raspberrypi
```

Next, initialize the build environment:

```bash
source oe-init-build-env
```

Then add the Raspberry Pi layer and the Mender integration layer:

```bash
bitbake-layers add-layer ../meta-raspberrypi
bitbake-layers add-layer ../meta-mender/meta-mender-raspberrypi
```

### Updating local.conf

In addition to the [generic Mender build configuration](../../artifacts/building-mender-yocto-image#configuring-the-build),
add this Raspberry Pi specific configuration to your `conf/local.conf`:

```bash
# These layers support the following MACHINE settings:
# raspberrypi0, raspberrypi, raspberrypi2, raspberrypi3
MACHINE = "raspberrypi3"
RPI_USE_U_BOOT = "1"

# These are simply to align with how the "stock" RPi machines are
# configured.
MENDER_PARTITION_ALIGNMENT_KB = "4096"
MENDER_BOOT_PART_SIZE_MB = "40"

# rpi-base.inc removes these as they are normally installed on to the
# vfat boot partition. To be able to update the Linux kernel Mender
# uses an image that resides on the root file system and below line
# ensures that they are installed to /boot
IMAGE_INSTALL_append = " kernel-image kernel-devicetree"

# Mender will build an image called `sdimg` which shall be used instead
# of the `rpi-sdimg`.
IMAGE_FSTYPES_remove += " rpi-sdimg"
```

That is it!
You can now continue the general steps for
[building the image](../../artifacts/building-mender-yocto-image#building-the-image).
