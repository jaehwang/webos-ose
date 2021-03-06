# Getting Started with webOS OSE 

I have a Raspberry Pi 2 and a Ubuntu 16.04 workstation. Since [webOS Open Source Edition](http://webosose.org/) officially supports Raspberry Pi 3 and Ubuntu 14.04, I find a way that suits my environment.

## Build with Docker Ubuntu 14.04

Before building Docker image, change `git` command arguments in [`docker/Dockerfile`](docker/Dockerfile) to use your personal information.

    $ git clone git@github.com:jaehwang/webos-ose.git
    $ cd webos-ose
    $ git clone https://github.com/webosose/build-webos.git
    $ cp build-webos/scripts/prerequisites.sh docker/
    $ sudo docker build --build-arg UID=$UID -t webososedev docker
    $ sudo docker run -it -v `pwd`/build-webos:/build -w /build webososedev

In the `webososedev`, to build webOS OSE, follow the instructions in [webOS OSE web page](http://webosose.org/discover/setting/building-webos-ose/).

    $ ./mcf raspberrypi3
    $ make webos-image

## USB WIFI Dongle for Raspberry PI 2

To use a wifi dongle, create `build-webos/webos-local.conf` file and build.

    IMAGE_INSTALL_append += "kernel-modules"

You can enable wifi using [Setting app](http://webosose.org/discover/setting/setting-up-networking/). `/etc/wpa_supplicant.conf` seems to have nothing to do with wifi. :/

## Flashing the Image

Follow the instructions in [this page](http://webosose.org/discover/setting/flashing-webos-ose/). I use `dd` command as follows:

    $ sudo dd bs=4M if=build-webos/BUILD/deploy/images/raspberrypi3/webos-image-raspberrypi3.rootfs.rpi-sdimg of=/dev/sdX status=progress conv=fsync

I expanded the partition that webOS is running on to use the full size of the SD card. I used `GParted` on my unbuntu 16.04 workstation.

## Etc.

* I use a Ubuntu 16.04 machine as a host.
* I use a USB wifi dongle with Realtek 8192cu.
* I use a 4GB micro SD Card.

<!--
vim:nospell
-->
