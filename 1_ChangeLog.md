---
title: Introduction
category: General
order: 4
label: WIP
permalink: 
---

2023/04/27 - Batocera 37-dev for RG35XX Beta v0.8
* Moved completely away from X11 graphics. Thanks to the excellent work by @JohnnyOnFlame we now have a GPU fbdev based SDL2 version that performs significantly better
* As part of this change the tearing issues with refresh have now been solved as he fixed the VSYNC issues
* Rebased all the changes to be in sync with the latest batocera v37 development branch, so there are several standalone emulators and cores updated
* Replaced pico8 core retro8 with fake8
* General performance improvements
* Solved the audio volume issue. Audio volume should now be consistent across the system, also the audio slide overlay is visible in EmulationStation frontend
* System charging algorithm has been disabled in this build since it led to more confusion than convenience. However, if you want the system to enter into charging after shutdown delete the file boot/firstBoot from the first partition (BATOCERA)

2023/04/20 - Batocera 36 for RG35XX Beta v0.7
* First full batocera beta release (no longer lite)
* Added initial charging logic, it's now *finally* possible to charge the device while being powered off:
  * When the system is powered off but connected to the power it no longer powered off but enters the charging mode.
  * This also happens If your device is powered off but you connected it to power
  * When the system is in charging mode, press power button briefly to boot
* Fixed led status (broken in v0.6)
* Updated external roms folder mount points to allow compatibility with non-batocera structure roms folders. It’s now possible to reuse OFW or GarlicOS sdcard roms and bios folders (Thanks @XQuader for the patch).
* Fixed internet connection status message (no longer showing ``Status Not Connected`` after a successful connection)
* Fixed DeSmume and melonDS NDS cores
* Added support for Space Cadet Pinball port
* Added eDuke32 port
* Added libretro-ecwolf 
* Added mame (current) libretto core
* Added od-commander file browser
* Enabled scraper content download for all platforms (thanks batocera @nadenislamarre)
* Earphones detection/audio switching is working (probably fixed in v0.6 but not tested before)
* Consolidated build system to use batocera standard image 
* Rootfs has not changed to squashfs format. This is due to space savings and to allow updates
* ADB can now be enabled by switching the kernel. Mount the first partition of the SDCARD on your PC, make a copy of uImage, and copy adb_uImage to uImage. After the system reboots adb will be available.
* Fixed direct launch into retroarch. Add an empty file to the first partition of the SDCARD named ``startRA``. The configuration may be missing, so you may need to the ``retroarch.cfg`` below to the ``/userdata/system/.config/retroarch/retroarch.cfg`` (via network or mounting the second partition of the SDCARD)

2023/04/12 - Batocera Lite for RG35XX Test Release Alpha 0.6
* Updated bootloader and uboot for latest board revisions compatibility 
* By default the installation has the 2600mAh battery curve, but there's also a 2100mAh battery curve in the first partition
  * If you have a 2100mAh battery, insert the sdcard on your computer, move the file ``kernel.dtb`` to ``2600mAh-gpu.dtb``, and copy the file ``2100mAh-gpu.dtb`` to ``kernel.dtb``
* Updated the kernel to include overclock/underclock support. 
  * By default the frequency is set to 1008 MHz (same as previous releases) but it's possible to choose 5 levels of under/overclock: Powersave (240 MHz), Low (720 MHz), None (1008 MHz), High (1200 MHz), Turbo (1392 MHz) and Extreme (1488 MHz). 
  * To change the clock frequency, open batocera ``Settings -> System Settings -> Overclock`` and select the desired frequency. 
  * When you exit the menu batocera will indicate that you need to reboot for the changes to be applied, but you can ignore that message. The selected frequency will be applied and saved in the configuration for the next boot.

2023/04/11 - Batocera Lite for RG35XX Test Release Alpha 0.5
* Fixed menu hotkeys not working on retroarch, it's now possible to access the menu by selecting ``MENU`` + ``B``
* Fixed GL shaders, selecting the shaders in batocera EmulationStation options should work (e.g. ``GAME RENDERING & SHADERS -> SHADER SET -> ZFAST``
* Virtual memory has been enabled again, this should help to avoid some crashes in some games

2023/04/10 - Batocera Lite for RG35XX Test Release Alpha 0.4
* Build is now based on full batocera build
* EmulationStation menus to select core should now work:
    * To change it for a full system: Select a system and press ``SELECT``, ``ADVANCED SYSTEM OPTIONS``, ``EMULATOR`` and set the emulator of your choice
    * For a specific rom, select the rom, then press and keep pressed ``B``, then ``ADVANCED GAME OPTIONS``, ``EMULATOR`` and set the emulator of your choice
* Note that many core options are now changed in the ``ADVANCED SYSTEM``/``GAME OPTIONS``
* Added multiple ports, all ports should have working controls now (SDLPoP, devolutionx, Cannonball, Sonic1, Sonic2, SonicCD, etc.)
* Added additional standalone emulators: GSPlus, Hatari, Amiberry Drastic, flycast, OpenBOR, PPSSPP, Mupen64, vice etc.)
* Updated input driver for compatibility with revisions 6C or lower. Thanks to Dark-Seraph for the gpio driver.
* USB Ethernet (ASIX based chipsets) and USB Wireless (RTL8192, RTL8188 based chipsets) should now work. Note that usb needs to be plugged after the system boots, and in some cases you need to insert the USB C to USB A adapter first, then connect the Ethernet or Wifi adapter.


2023/03/24 - Batocera Lite for RG35XX Test Release Alpha 0.3
* SDCard structure now based on regular batocera structure (1st partition contains the system, second partition is for content).
  * Future system updates can be added by just replacing the some files in the first partition, no need to reflash the SDCARD.
* SDCard auto expand: during the first boot the sdcard will expand the second partition to fill the whole sdcard. After that happens batocera populates the required folders for roms, etc.
* Added virtual memory. It should be possible to run some N64 games now. Note that launching those titles may fail at first, just try again.
* Fixed motor running all the time in some models (#2) 
* Fixed led status during charging, power on, low battery 
* Fixed power off: Note that only work when the console is not connected to the power (See #8 )
* Added initial governor support (currently only set on performance, additional work will be tracked in #10)
* Controls are now configured as a joystick, so it's possible to navigate the keyboard like interface in Retroarch and EmulationStation search/text entry, etc.
* External USB controllers work, some may need configuration. Note that at this point batocera control mappings are ignored, so you need to configure secondary controls in retroarch.

2023/03/16 - Batocera Lite for RG35XX Test Release Alpha 0.2
* First batocera lite build
* Power button now works (although it may restart in some cases)
* Volume controls work
* Brightness controls work with MENU + Volume +/Volume -
* It's possible to switch to RetroArch boot (instead of emulationstation) by adding a file named startRA at the top of the second sdcard. Remove the file to boot again into EmulationStation.

2023/03/13 - RetroArch (GPU enabled for RG35XX Test Release Alpha 0.1 
* First Test Alpha release