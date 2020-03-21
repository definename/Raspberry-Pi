# Raspberry-Pi

[Raspberrypi_cookbook_ed2](https://github.com/simonmonk/raspberrypi_cookbook_ed2) source code

## Raspberry shop:

[Adafruit](https://www.adafruit.com/)

## Raspberry documentation:
Getting [started](https://projects.raspberrypi.org/en/pathways/getting-started-with-raspberry-pi) with Raspberry Pi

Official [documentation](https://www.raspberrypi.org/documentation/)

[Os](https://www.raspberrypi.org/downloads/) for raspberry

For more details on the advanced capabilities of the [GPIO pins](https://pinout.xyz/) see gadgetoid's interactive pinout diagram.

`sudo raspi-config` ssh, user passwd etc.

## RPI serial connection



## RPI 3B+ UART:

[HowTo](https://elinux.org/RPi_Serial_Connection)

## Error garbage on UART console:

- To the end of file: /boot/config.txt add:
```
dtoverlay=pi3-disable-bt
dtoverlay=pi3-miniuart-bt
```
- Reboot target

[Garbage1](https://openenergymonitor.org/forum-archive/node/12311.html)

[Garbage2](https://raspberrypi.stackexchange.com/questions/45007/garbage-on-raspberry-pi-console)

## Error not able to type on UART console
