# Raspberry-Pi

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

# Raspbian uart:

- [uart howto](https://elinux.org/RPi_Serial_Connection)

Garbage on UART console:

- To the end of file: /boot/config.txt add:
```
dtoverlay=pi3-disable-bt
dtoverlay=pi3-miniuart-bt
```
- restart

[Info1](https://openenergymonitor.org/forum-archive/node/12311.html)

[Info2](https://raspberrypi.stackexchange.com/questions/45007/garbage-on-raspberry-pi-console)

Unable to type on UART console:

- Try to use non usb power supply

# Yocto (zeus 3.0.2):

- [yocto](https://www.yoctoproject.org/)
- [meta-raspberrypi](https://meta-raspberrypi.readthedocs.io/en/latest/index.html)

---

clone [yocto](https://www.yoctoproject.org/software-overview/downloads/)

build `bitbake core-image-minimal`

add [meta-raspberry](http://layers.openembedded.org/layerindex/branch/master/layer/meta-raspberrypi/) layer

modify build/conf/local.conf:
 - set machine type: `MACHINE = "raspberrypi3"`
 - add `rpi-sdimg` support with: `IMAGE_FSTYPES="tar.bz2 ext3 rpi-sdimg"`
 
build `bitbake core-image-base`

flash: `sudo dd if=core-image-base-raspberrypi3.rpi-sdimg of=/dev/mmcblk0 bs=1M conv=fsync`

--- 

rpi machine: 
```
MACHINE = "raspberrypi3"
```

rpi sd image to flash with dd:
```
IMAGE_FSTYPES += "rpi-sdimg"
```

i2c:
```
ENABLE_I2C = "1"
IMAGE_INSTALL_append = " i2c-tools"
```

uart:
```
ENABLE_UART = "1"
```

uart manually:
- add to config.txt: `enable_uart=1`
- add to cmdline.txt: `console=serial0,115200 console=tty1`

vim:
```
IMAGE_INSTALL_append = " vim"
```

---
