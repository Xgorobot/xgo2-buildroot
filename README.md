# XGO2 lite/mini Buildroot-based software

![XGO2 mini/lite software](./res/catdog.jpg)

[![xgo2 mini/lite](https://github.com/e-yes/xgo2-buildroot/actions/workflows/xgo2-buildroot.yml/badge.svg)](https://github.com/e-yes/xgo2-buildroot/actions/workflows/xgo2-buildroot.yml)

## Build

Clone the source code

```sh
mkdir xgo2 && cd xgo2
git clone git://git.busybox.net/buildroot
git clone https://github.com/e-yes/xgo2-buildroot.git
cd buildroot
make BR2_EXTERNAL=../xgo2-buildroot/ xgo2_defconfig
make -j # you can specify how many CPU cores it can use for build
```

## Install

```sh
unzip image_xgo2.zip && gunzip sdcard.img.gz
sudo dd if=output/images/sdcard.img of=/dev/mmcblk0 status=progress
```

## Usage

- Create hotspot named "XGO2" with password "LuwuDynamics".
- Insert SD-card to the robot and power it up:)
- Use ssh client to connect to it, username is "pi" and the password is the same. You can use `ipython` to play with it.
```
› ssh pi@192.168.214.65
(pi@192.168.214.65) Password: 
$ sudo su
$ ipython
Python 3.11.5 (main, Sep 22 2023, 23:40:52) [GCC 12.3.0]
Type 'copyright', 'credits' or 'license' for more information
IPython 8.8.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: from xgolib import XGO

In [2]: dog = XGO("xgomini")

In [3]: dog.action(11) # I like this one:)
```
- If you wonder what is IP-address of the dog, use `arp-scan --localnet` to discover it:
```
# arp-scan --localnet
Interface: wlan0, type: EN10MB, MAC: 30:24:32:b7:d6:62, IPv4: 192.168.214.117
Starting arp-scan 1.9.7 with 256 hosts (https://github.com/royhills/arp-scan)
192.168.214.65	e4:5f:01:e5:3c:dc	(Unknown) <--- HERE! Your mileage may vary!!!
192.168.214.65	e4:5f:01:e5:3c:dc	(Unknown) (DUP: 2)
192.168.214.163	56:8f:45:0a:d9:f0	(Unknown: locally administered)

```

## Contributing

PRs accepted.

## License

[![License: WTFPL](https://img.shields.io/badge/License-WTFPL-brightgreen.svg)](http://www.wtfpl.net/about/)
