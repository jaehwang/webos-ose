# Getting Started with webOS OSE 

## Docker

    $ git clone https://github.com/webosose/build-webos.git
    $ cd docker
    $ cp ../build-webos/scripts/prerequisites.sh .
    $ docker build -t webososedev .
    $ cd ..
    $ docker run -it -v `pwd`/build-webos:/build -w /build webososedev

## USB WIFI Dongle for Raspberry PI 2

Create `build-webos/webos-local.conf`.

    MACHINE_EXTRA_RRECOMMENDS_append += "linux-firmware"
    MACHINE_EXTRA_RRECOMMENDS_append += "kernel-modules"

    IMAGE_INSTALL_append += "linux-firmware kernel-modules iw"

You can enable wifi using Setting app. `/etc/wpa_supplicant.conf` seems to have nothing with wifi.


## 기타

* I use Ubuntu 16.04 machine as a host.
* I use 4GB SD Card.

<!--
vim:nospell
-->
