---
title: FAQ
category: General
order: 3
label: WIP
permalink: 
---

> Q: I want to add my own roms to the SDCARD but my Windows/Mac computer can't see the roms partition

A: By default batocera formats the second partition with Linux EXT4 file format. That format is typically
not readable/mountable under Windows/Mac. To solve that you need to use one of the following approaches:
 * Use Paragon EXTFS for Windows/Mac. This tool is not free but it's highly recommended since it allows seamless 
 access to EXT2/3/4
 * Use DiskGenius on Windows. Not recommended. DiskGenius performs badly and tends to corrupt the partition and its content
 * Format the second partition as FAT32:
   * Insert the SDCARD on your PC/MAC
   * On Windows, open the partition tool and erase/format the second partition (SHARE) as FAT32
   * On Mac, unfortunately you will need use the command line to completely reformat the partition. Open Disk Utility and note the 
   disk number and partition of your usb (e.g. disk4s2). Open a terminal and reformat the partition with the following command:
   ```sudo diskutil eraseVolume ms-dos SHARE /dev/disk4s2```
   * Eject the SDCARD from your computer and insert it again on the RG35XX
   * Power the device on
   * Batocera will re-populate the partition with the correct contents. After the system boots you can power it off and insert the sdcard
   on your computer to add your bios/roms or any other content.

---

> Q: Can I use a second SDCARD for my roms/bios content?

A: Yes! if you have a new or empty SDCARD you can insert the SDCARD on the second slot of the RG35XX and follow these steps:
  * Boot batocera and go to ``Settings -> System Settings -> Storage Device`` and change it from ``INTERNAL`` to your second card, e.g. ``SHARE - 25.6G``. 
  * Exit the settings menu and the system will indicate you need to reboot to get the changes applied. 
  * Go to the menu ``Settings -> Quit -> Restart System`` to reboot. The system will reboot and the second card will be now used for batocera and the folder structure (roms, bios, etc.) will be created. 
  * You can now shutdown the console, insert the card on your computer, and copy your bios & roms content.

---

> Q> I have Garlic with my roms/bios on the second SDCARD. Is it possible to reuse that card for Batocera?

A: By default batocera expects a different name for the roms folders and its location, but thanks to @XQuader there's a script that creates the compatible configuration for batocera based on the Garlic structure. You can read more about it on [this Reddit post](https://www.reddit.com/r/RG35XX/comments/12zxs8t/how_to_get_garlicos_roms_folders_working_in/)

---

> Q: The installation seems to be running, I can see it's expanding the partition but it's taking too long

A: Expanding and booting the first time with a 64GB SDCARD takes about 1 to 1:30 minutes. If your SDCARD is larger it may take much longer, however if it goes beyond 5 minutes chances are that something didn't go well. Just press reset and the system will continue. If that's the case the partition may have not been expanded. For that you will need to manually expand the card on your PC/Mac/Linux.

---

> Q: I've installed/updated to the latest version and I don't have audio, or my controls don't respond, or something else is not working as expected:

A: If you have updated from an older version you may need to copy the ``batocera.conf`` from the releases page to your SDCARD:
  * If you use one single SDCARD, mount the second partition on your PC/Mac/Linux (``SHARE``) and copy the file to ``system/batocera.conf``
  * If you use two SDCARDs, mount the second SDCARD on your PC/Mac/Linux and copy the file to ``system/batocera.conf``

---

> Q: Do I have to flash every release or can I update?

A: For most of the releases you can update:
  * Download the boot.tar.xz file from the releases page
  * Extract its content
  * Mount your batocera SDCARD on your PC/Mac/Linux computer
  * Delete the file ``boot/batocera`` (you can make a backup of this file on your computer in case you want to revert to the previous version)
  * Copy the contents of the extracted boot.tar.xz to the SDCARD

---

> Q: I am trying to run NDS roms but when trying to launch them the console returns to emulationstaion. Is it possible to use Drastic?

A: Currently Drastic is the best emulator for NDS roms. However it's not working to launch roms directly from the NDS roms menu. See [this issue in Github](https://github.com/rg35xx-cfw/rg35xx-cfw.github.io/issues/25#issuecomment-1526845570) to see how to add drastic to launch from the ports menu. Once the script is added to roms/ports, you can launch the standalone drastic emulator, and then navigate to ``/userdata/roms/nds`` to find your roms. Note that roms need to be uncompressed in .nds format.
Both desmume and melonds run but the performance is not very good compared with Drastic.

