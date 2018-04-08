# webOS OSE

## Docker를 이용한 Build 

Ubuntu 16.04 환경에서 빌드 시도했더니 mesa가 llvm과 궁합이 안 맞는지 에러가 났다. 그래서 Docker로 Ubuntu 14.04 빌드 환경을 만들어 본다.
    
    $ git clone https://github.com/webosose/build-webos.git
    $ cd docker
    $ cp ../build-webos/scripts/prerequisites.sh .
    $ docker build -t webososedev .
    $ cd ..
    $ docker run -it -v `pwd`/build-webos:/build -w /build webososedev

## USB WIFI 사용하기

RPI2의 wifi dongle을 위해 `webos-local.conf`를 만들었다.

    MACHINE_EXTRA_RRECOMMENDS_append += "linux-firmware"
    MACHINE_EXTRA_RRECOMMENDS_append += "kernel-modules"

    IMAGE_INSTALL_append += "linux-firmware kernel-modules iw"

Setting 앱을 이용하면 wifi를 쓸 수 있다. 하지만 wpa supplicant의 설정을 어떻게 하는 지 모르겠다.

<!--
vim:nospell
-->
