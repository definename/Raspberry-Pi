## Raspberry-Pi

[Raspberrypi_cookbook_ed2](https://github.com/simonmonk/raspberrypi_cookbook_ed2) source code

## Raspberry shop:

[Adafruit](https://www.adafruit.com/)

## Linux kernel

[kernelnewbies](https://kernelnewbies.org/)

## Raspberry documentation:
Getting [started](https://projects.raspberrypi.org/en/pathways/getting-started-with-raspberry-pi) with Raspberry Pi

Official [documentation](https://www.raspberrypi.org/documentation/)

[Os](https://www.raspberrypi.org/downloads/) for raspberry

For more details on the advanced capabilities of the [GPIO pins](https://pinout.xyz/) see gadgetoid's interactive pinout diagram.

`sudo raspi-config` - interface to control ssh, user passwd etc. 

## Build yocto with meta-raspberry layer

clone [yoctoproject](https://www.yoctoproject.org/software-overview/downloads/) sources

build `bitbake core-image-minimal`

clone [meta-raspberry](http://layers.openembedded.org/layerindex/branch/master/layer/meta-raspberrypi/) layer sources

modify build/conf/local.conf:
 - set machine type: `MACHINE = "raspberrypi3"`
 - add `rpi-sdimg` support with: `IMAGE_FSTYPES="tar.bz2 ext3 rpi-sdimg"`
 
build `bitbake core-image-base`

flash: `sudo dd if=core-image-base-raspberrypi3.rpi-sdimg of=/dev/mmcblk0 bs=1M conv=fsync`

NOTE: [meta-raspberrypi](https://meta-raspberrypi.readthedocs.io/en/latest/index.html) layer documentation

## Custom yocto layer for raspberry pi

[meta-olehk](https://github.com/definename/meta-olehk) layer

## Raspbian UART:

GPIO pin 6(GND),8(TX),10(RX)

- [uart howto](https://elinux.org/RPi_Serial_Connection)

HowTo
---
Garbage on UART console:

To the end of file: /boot/config.txt add:
```
dtoverlay=pi3-disable-bt
dtoverlay=pi3-miniuart-bt
```
restart board

[why1](https://openenergymonitor.org/forum-archive/node/12311.html), [why2](https://raspberrypi.stackexchange.com/questions/45007/garbage-on-raspberry-pi-console)
---
Unable to type on UART console:

Try to use non usb power supply

## RUN & PEN header

The `PEN` header is for Power enable. When this pin is connected to ground (e.g. `GPIO pin 14`), the Pi goes into its lowest possible power state. It is effectively just running the red LED at this point. Removing this ground connection causes the pull-up resistor on-board to pull this enable pin HIGH, giving the board power again. This could be attached to a low-power microcontroller if you needed a remote wake-up for instance.

The `RUN` header is similar, but for the CPU only. Connecting this to ground (e.g. `GPIO pin 14`) stops the CPU from running, but the Pi board still has power. This is what you could use as a “reset switch”.
