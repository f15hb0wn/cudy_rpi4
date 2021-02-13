# Cudy WU700 AC650 USB WIFI ADAPTER

This are the drivers for Cudy WIFI adapter (rtl8811CU) which was unfortunately shipped with the wrong drivers (88x2BU).
This repository was forked from whitebatman2's [one](https://github.com/whitebatman2/rtl8821CU) and some modification were added here and there to have it work on new kernels (kernel 5.4 confirm operation).

Modifications are from cilynx's RTS88x2BU [driver](https://github.com/cilynx/rtl88x2bu) which was installed due to incorrect assumption of the correct RTL driver, all thanks to him.

Use following commands in source directory:
```
make
sudo make install
sudo modprobe 8821cu

```
