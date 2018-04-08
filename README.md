# Getting Started with webOS OSE 

## Docker for Build

    $ git clone https://github.com/webosose/build-webos.git
    $ cd docker
    $ cp ../build-webos/scripts/prerequisites.sh .
    $ docker build -t webososedev .
    $ cd ..
    $ docker run -it -v `pwd`/build-webos:/build -w /build webososedev

In the `webososedev`, to build webOS OSE, follow the instructions in [webOS OSE web page](http://webosose.org/discover/setting/building-webos-ose/).

    $ ./mcf raspberrypi3
    $ make webos-image

## USB WIFI Dongle for Raspberry PI 2

To use a wifi dongle, create `build-webos/webos-local.conf` and build again.

    MACHINE_EXTRA_RRECOMMENDS_append += "linux-firmware"
    MACHINE_EXTRA_RRECOMMENDS_append += "kernel-modules"

    IMAGE_INSTALL_append += "linux-firmware kernel-modules iw"

You can enable wifi using Setting app. `/etc/wpa_supplicant.conf` seems to have nothing todo with wifi.

## Flashing the Image

Follow the instructions in [this page](http://webosose.org/discover/setting/flashing-webos-ose/). I use `dd` command as follows:

    $ sudo dd bs=4M if=build-webos/BUILD/deploy/images/raspberrypi3/webos-image-raspberrypi3.rootfs.rpi-sdimg of=/dev/sdX status=progress conv=fsync

## Etc.

* I use a Ubuntu 16.04 machine as a host.
* I use 4GB SD Card.

<!--
vim:nospell
-->
