---
title: Installation
category: Getting Started
order: 2
label: draft
---
# Installation

## Installation from scratch

* Download the latest release of the firmware for your RG35XX console from the [releases page](https://github.com/rg35xx-cfw/rg35xx-cfw.github.io/releases)
* Download [Balena Etcher](https://www.balena.io/etcher/) for your operative system
* Install and run Balena Etcher
* Open the firmware file and select your USB drive as your target device. Note that you will need a minimum of 8GB but we recommend a minimum of 16GB.
* Click on Flash! and wait for the image to be created.
* Insert the SDCARD into your RG35XX and power it on
* The first time batocera boots it will enlarge the second partition to all the available storage. Once that's finished, batocera will continue with its normal boot sequence. You should see the batocera logo in a bit, followed with EmulationStation (the main batocera interface) starting
* Note that the first boot takes a bit more than a minute to finish, after that first boot the system should boot in aobut 35s

## Updating and existing installation without flashing

You can update the batocera system by flashing a new installation image, or you can update an existing image by following this procedure:
* Download the ``boot.tar.xz`` for the latest release from the [releases page](https://github.com/rg35xx-cfw/rg35xx-cfw.github.io/releases)
* Insert the USB with your existing batocera installation on your PC/Mac/Linux
* Mount the first partition called BATOCERA
* Extract all the contents of the ``boot.tar.xz`` file and copy the contents to the BOOT partition
* Eject the USB
* Insert the USB on your console and boot

