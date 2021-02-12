# Cudy WU700 AC650 USB WIFI ADAPTER

This are the drivers for Cudy WIFI adapter (rtl8811CU) which was unfortunately shipped with the wrong drivers (88x2BU).
This repository was forked from whitebatman2's [one](https://github.com/whitebatman2/rtl8821CU) and some modification were added here and there to have it work on new kernels (kernel 5.4 confirm operation).

Modifications are from cilynx's RTS88x2BU [driver](https://github.com/cilynx/rtl88x2bu) which was installed due to incorrect assumption of the correct RTL driver, all thanks to him.

Here are the original instructions:

## Build and install with DKMS

DKMS is a system which will automatically recompile and install a kernel module when a new kernel gets installed or updated. To make use of DKMS, install the dkms package, which on Debian (based) systems is done like this:

    apt-get install dkms

To make use of the DKMS feature with this project, do the following:

    DRV_NAME=rtl8821CU
    DRV_VERSION=5.2.5.3
    sudo mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
    git archive master | sudo tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
    sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
    sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
    sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}

If you later on want to remove it again, do the following:

    DRV_NAME=rtl8821CU
    DRV_VERSION=5.2.5.3
    sudo dkms remove ${DRV_NAME}/${DRV_VERSION} --all

## Build and install without DKMS
Use following commands in source directory:
```
make
sudo make install
sudo modprobe 8821cu
```
## Raspberry Pi
To build this driver on Raspberry Pi you need to set correct platform in Makefile.
Change
```
CONFIG_PLATFORM_I386_PC = y
CONFIG_PLATFORM_ARM_RPI = n
CONFIG_PLATFORM_ARM_RPI3 = n
```
to
```
CONFIG_PLATFORM_I386_PC = n
CONFIG_PLATFORM_ARM_RPI = y
CONFIG_PLATFORM_ARM_RPI3 = n
```
For the Raspberry Pi 3 you need to change it to
```
CONFIG_PLATFORM_I386_PC = n
CONFIG_PLATFORM_ARM_RPI = n
CONFIG_PLATFORM_ARM_RPI3 = y
```
