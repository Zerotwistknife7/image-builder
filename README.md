# image-builder

## Building the adsb image based on buster:

```
git clone https://github.com/Zerotwistknife7/image-builder.git
cd image-builder
wget https://downloads.raspberrypi.org/raspios_oldstable_lite_armhf/images/raspios_oldstable_lite_armhf-2021-12-02/2021-12-02-raspios-buster-armhf-lite.zip
unzip 2021-12-02-raspios-buster-armhf-lite.zip
 ./create-image.sh 2021-12-02-raspios-buster-armhf-lite.img buster.img
```

## Building the adsb image base on bullseye

```
wget https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2022-04-07/2022-04-04-raspios-bullseye-armhf-lite.img.xz
unxz 2022-04-04-raspios-bullseye-armhf-lite.img.xz
./create-image.sh 2022-04-04-raspios-bullseye-armhf-lite.img bullseye.img
```

## tracking down disk writes

```
stdbuf -oL -eL inotifywait -r -m /etc /adsb /opt /root /home /usr /lib /boot /var 2>&1 | stdbuf -oL grep -v -e OPEN -e NOWRITE -e ACCESS -e /var/tmp -e /var/cache/fontconfig -e /var/lib/systemd/timers -e /var/log | ts >> /tmp/inot
```
