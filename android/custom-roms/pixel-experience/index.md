---
author:
    name: Paradox
    avatar: /paradox.jpg
    email: s.samarthkulkarni@gmail.com
    link: https://github.com/ParadoxInfinite/
date: 2022-10-19T01:40
title: PixelExperience
categories: [custom-roms, android, guides, raphael]
description: Installation guide for PixelExperience 12.1+ on raphael/raphaelin
image: https://descargas.ams3.digitaloceanspaces.com/images/710/ux9-ux10-theme-pixel-experience-android-10-11_android_409_1.png
---
# PixelExperience

![|450](https://gizblog.it/wp-content/uploads/2019/02/pixel-experience-banner-1024x576.jpg)

<br/>
Installing PE (12.1 and above) on Redmi K20 Pro/Xiaomi Mi 9T Pro (raphael/raphaelin)
<br/><br/>

## Downloads
- **ROM**:<br/>Download links for raphael can be found here: [PixelExperience site](https://download.pixelexperience.org/raphael)

- **Latest firmware**:<br/>Download respective latest firmware from here:<br/>
    +++ Indian Model [!badge variant="dark" text="raphaelin"]
    [Redmi K20 Pro India Latest Firmware](https://xiaomifirmwareupdater.com/firmware/raphaelin)
    +++ Global Model [!badge variant="dark" text="raphael"]
    [Mi 9T Pro / Redmi K20 Pro Latest Firmware](https://xiaomifirmwareupdater.com/firmware/raphael) (Pick your region accordingly)
    +++

- **Recovery**:<br/>
    !!!warning Important Note
    From Android 12.1 onwards, PE will be switching over to FBEv2 and F2FS filesystem. This means, generic TWRP/OrangeFox recoveries won't work for flashing the ROM.
    
    **However**, you might TWRP initially to get the required OFox flashed. Get the latest TWRP from [here](https://dl.twrp.me/raphael/).
    !!!
    Download OrangeFox from either of the options:<br/>
    +++ Android File Host
    [Android File Host](https://androidfilehost.com/?fid=15664248565197208249) - by Pranav Talmale
    +++ Direct Download
    [!file Direct download](https://github.com/ParadoxInfinite/paradocs/releases/download/ofox-recovery-fbev2/Ofox-R11.1_1-FBEv2.zip)
    +++

## Instructions

!!!danger Disclaimer
**Make a NAND backup**, and only continue if you know what you are doing. I am not responsible for anything that happens to you/your device.
!!!

!!! ADB and fastboot
Assuming ADB and fastboot are installed. Following commands are in linux format, might have to make some changes for Windows/Mac, YMMV.
!!!

### Getting to fastboot/recovery
>>>Connect your phone to PC with USB debugging enabled.
>>>In a terminal, run: `adb reboot bootloader` and this will bring you to the fastboot menu.
>>>Now run: `fastboot boot twrp-3.7.0_9-0-raphael.img` (the twrp file name will be the file you downloaded from [Downloads](#downloads))
>>>Once in TWRP, (if your storage isn't mounted, mount it and then) transfer your `Ofox-R11.1_1-FBEv2.zip` file onto your storage.
>>>Flash the OFox recovery and the phone will auto reboot to OFox recovery.
>>>

### Flashing firmware (Optional, but recommended)
Transfer the firmware file you downloaded onto the storage and flash it.

### Format/Wipe before install
>>>Click on the trash/garbage bin at the bottom of OFox to get to the Wipe menu.
>>>In the `Wipe tab`, select/tick **only** `Cache` and `Data` options and Wipe them.
>>>Now in the `Format Data` tab, type 'yes' and format.
>>>

### Flash PixelExperience
>>>Transfer the PixelExperience zip file onto your storage.
>>>Flash the PixelExperience zip.
>>>(Optional, **NOT Recommended**) You can flash a DFE zip to remain decrypted, but I would strongly advice against it, unless you have the need to be decrypted and understand the risks of it.
>>>Reboot to System and you should now be booting PixelExperience successfully.
>>>

!!!info
Incase you get stuck even after these steps, do checkout the [Telegram group](https://t.me/peraphaelofficial) for raphael PE and seek help there. Be nice and respectful when asking for help.
!!!

Enjoy the ROM, cheers!

![|350](/imgs/congration.jpg)