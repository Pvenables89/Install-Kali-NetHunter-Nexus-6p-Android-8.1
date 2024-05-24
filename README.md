# Install-Kali-NetHunter-Nexus-6p-Android-8.1


Installing Kali Nethunter in Nexus 6P (Angler)

"Original Author: Saulo S. Ortiz"    Date: 20180511

updated by: https://github.com/Pvenables89

Updated: 24-05-2024



Websites used in this step:

	https://github.com/ortizimo/Install-NetHunter-to-Nexus-6p-Angler/blob/master/instructions.txt 
 # I USED THIS LINK AS IT HAD GREAT INSTRUCTIONS, JUST OUTDATED AND I FOUND SOME STEPS UNNECESSARY



*NOTE 1: As of this writing, Kali Nethunter is compatible with image 7.1.1 Nougat #SEVRAL ATTEMPTS NETHUNTER ZIP FAILS


IMPORTANT!

YOU'LL NEED TO UNLOCK THE BOOTLOADER FIRST...CHECK STEP #1 DOCUMENT FOR:

	a. SYSTEM SETUP...SECTION #1.0
 
	b. UNLOCK THE BOOTLOADER...SECTION #1.1
 

5. Connect phone to computer

6. Set phone to Developer Mode:
	a. Go to Settings
	b. Go to System
	c. Go to About phone
	d. Tap Build number 7 times
		(Your in Developer Mode!!!!)

7. Tap back, then tap {} Developer options

8. Enable:
	a. Stay awake
	b. OEM unlocking
	c. USB debugging

9. Exit {} Developer mode then exit Settings

10. While in c:\adb press and hold Shift key + Right click

11. From menu select Open command window from here

12a. In cmd prompt type: adb devices
	(serial number is displayed...if not, close cmd prompt and try again)
	(may need to put it into Bootloader manually then connect to the computer to get drivers to recognize phone)

12b. Manual Bootloader mode
	a. Turn off phone...wait 2 seconds
	b. Press and hold Volume Down button + Power button
		(you're in Bootloader mode)

13. Close cmd prompt

14. Go to c:\adb where image folder is and double click flash-all.bat file
	(flash-all.sh is for Linux)
	(flash-base.sh is for Mac)

15. Wait for it to flash (downgrade)...this will take up to 10 minutes
	(phone reboots)

16. Setup phone as if was new

17. Go to Settings and scroll to About phone to confirm 7.1.1



********************************************************
Installing Kali Nethunter in Nexus 6P (Angler) - Step #1
Updated: 20180512
********************************************************
Websites used in this step:
	https://developer.android.com/studio
	https://adb.clockworkmod.com/
	https://rootmygalaxy.net/downgrade-android-oreo-android-nougat/
	https://www.androidcentral.com/how-unlock-nexus-6p-bootloader

*NOTE 1: If you have any android version above 7.1.1 STOP and go to Step#0 to Downgrade to Nougat
**NOTE: All required files are included in the zip...steps reflect what I did in the process

--------------------------------------------------------------
Section #1.0: Initial Setup
--------------------------------------------------------------
1. Download latest OracleVirtualbox (free) or VMWare Workstation

2. Install VM software and create a Windows 7 VM to prevent damage/infection to main system
	a. Have 2GB ram...4GB recommended
	b. 128MB video with 3D and 2D if possible
	c. NAT to host or Bridge if router is not using ACL or if MAC was added to pool

3. Log into Win7VM and install Mozilla Firefox

4. Download and install:
	a. adb-setup-1.4.3
	b. UniversalAdbDriverSetup

5. Set phone to Developer Mode:
	a. Go to Settings
	b. Go to About phone
	c. Tap Build number 7 times
		(Your in Developer Mode!!!!)

6. Tap back,then tap {} Developer options

7a. Enable:
	a. Stay awake
	b. OEM unlocking
	c. USB debugging
	d. Select USB Configuration (MTP)...usually set by default

7b. Disable:
	a. Automatic system updates
	b. Verify apps over USB

8. Exit {} Developer mode

9. Scroll up and tap Display

10. Change Sleep to 5 minutes

11. Exit to main screen

--------------------------------------------------------------
Section #1.1: Unlock Bootloader
--------------------------------------------------------------
1. Go into c:\adb folder

2. Hold down Shift and Right click

3. Select Open command line window from here
	(cmd prompt opens)

4. Connect phone to computer...(may or maynot display/be required...only saw it under 8.1.0)
	(Accept RSA key fingerprint prompt)

5. Type:
	a.adb devices
		(you may not get serial number from phone if phone was already connected)

	b. adb reboot bootload
		(phone reboots into bootloader mode)

6. Check Device is LOCKED
		(if UNLOCKED, then go to #9 below)

7. Type: fastboot devices
	(you'll see a serial number and the word fastboot)

8. Type: fastboot flashing unlocked
	(THIS WILL RESET THE PHONE TO FACTORY MODE...YOU WILL LOSE ALL DATA!!!)

9. Setup phone as it was new then go to Step #2 folder


********************************************************
Installing Kali Nethunter in Nexus 6P (Angler) - Step #2
Updated: 20180512
********************************************************
Websites used in this step:
	https://android.gadgethacks.com/how-to/root-android-oreo-nexus-5x-6p-0176736/
	https://download.chainfire.eu/1122/SuperSU/SR3-SuperSU-v2.82-SR3-20170813133244.zip
	https://www.reddit.com/r/zenfone2/comments/3f0t7z/trying_to_flash_twrpsuccessful_but_cant_boot_into/
	https:/www.youtube.com/wawtch?v=5ucIwt9cPiE
	https://dl.twrp.me/angler/twrp-3.2.1-0-angler.img.html

*NOTE: All required files are included in the zip...steps reflect what I did in the process

--------------------------------------------------------------
Step #2.1: Root the Phone
--------------------------------------------------------------
1. Reboot phone

2. Add the phone MAC address to your router
	(may need to add more IPs in pool if using ACL)

On phone:

3. Download Root Checker from Play Store

4. Download SuperSu from (chainfire.eu) website above
	(goes into the Downloads folder)

In computer:

5. Download and copy twrp-3.2.1-0-angler.img to c:\adb

6. Connect phone to computer

7. Open c:\adb then hold down Shift and Right click

8. Select Open command window from here

9a. Type: adb devices
	(serial number is displayed..if not then try again
		(or do Bootloader manually)

9b. Manual Bootloader mode:
	a. Turn off phone...wait 2 seconds
	b. Press Volume Down button + Power button
	c. Go to step #11

10. Type: adb reboot bootloader to put phone in Bootloader mode

11. Type: fastboot devices
	(serial number is displayed)

12. Type: fastboot flash recovery twrp-3.2.1-0-angler.img

13. On the phone, scroll using the volume buttons to Recovery mode

14. Press power button to select it
	(after some seconds phone boots up to TWRP)

15. Swipe to enter TWRP

16. Tap on Install

17. Go to the Downloads folder

18. Tap on SuperSu .zip file then swipe to confirm flash
	(SuperSu installs)

19. Tap on Wipe chache/dalvik and swipe to wipe cache

20. Tap on Reboot and swipe to accept
	(leave defaults...phone reboots...may reboot twice...don't touch it)

21. Go to App Drawer and check for SuperSu icon...move it to the main screen

22. Run Root Checker to verify if phone is rooted...congrats!


********************************************************
Installing Kali Nethunter in Nexus 6P (Angler) - Step #3
Updated: 20190721
********************************************************
Websites used in this step:
	https://build.nethunter.com/nightly/
	https://forum.xda-developers.com/nexus-6p/general/kernel-kali-nethunter-huawei-nexus-6p-t3539084
	https://github.com/offensive-security/kali-nethunter/issues/706
	https://github.com/offensive-security/kali-nethunter/wiki
	https://github.com/offensive-security/kali-nethunter/wiki#60-kali-nethunter-attacks-and-features
	https://github.com/offensive-security/kali-nethunter

*NOTE: All required files are included in the zip...steps reflect what I did in the process

--------------------------------------------------------------
Section #3.1: Installing Kali Nethunter
--------------------------------------------------------------
7. Using your phone, download the latest 2 files from (build.nethunter.com):
    a. nethunter-generic-arm64-kalifs-full-rolling-[VERSION].zip (Kali FS)
    b. kernel-nethunter-angler-nougat-[VERSION].zip (Kernel)

IMPORTANT!
YOU NEED TO MAKE SURE YOU DOWNLOAD THE CORRECT 2 FILES ABOVE OR YOU'LL BRICK YOUR PHONE!!!!

8. Reboot to Bootloader, then select Recovery mode
	(you're in TWRP)

9. Tap Install, then go to the Downloads folder

10. Select nethunter-generic...and install it
	(it may take 25 minutes to complete!)
	(do not reboot after its done!)

11. Select kernel-nethunter...and install it

12. Swipe to wipe cache, then tap Reboot

13. Check App Drawer for new programs

--------------------------------------------------------------
Section #3.2: Nethunter Setup
--------------------------------------------------------------
1. Move all new icons from App Drawer to the main screen
2. Run Nethunter and allow everything
3. Grant root to Nethunt when SuperSU asks

--------------------------------------------------------------
Section #3.3: Fix NetHunter Terminal Crash
--------------------------------------------------------------
1. If NetHunter Terminal crashes then...
	a. Download and run Termux
	b. type: su
	c. type bootkali
	d. Run NetHunter Terminal

*During that session NetHunter terminal will run until you reboot...then you have to do these steps again

2. May have something to do with BusyBox installed over the BusyBox that comes with NetHunter
	a. Install everything to /system/xbin
	b. Check the box of everything unchecked

--------------------------------------------------------------
Section #3.4: Additional steps:
--------------------------------------------------------------
1. Do a recovery backup of the current state using TWRP

2. Install FX File Explorer from Play Store
	(To move your recovery file to the computer)

3. Go to Settings > Apps and DISABLE and FORCE STOP all applications you don't want
	(go to Google in Apps then scroll down to Modify system settings and checge to NO)

4. Install the following in the Nexus:
Program			         Author
---------------------------------------------
a. Root Checker ---------------- joeykrim
b. Reboot (no ads) ------------- AppClick MKS
c. FX File Explorer (no ads) --- NextApp Inc
d. System App Remover (root) --- Jumobile
e. Blank Widget ---------------- Chislon Chow
f. Termux ---------------------- Fredrik Fornwall
g. BusyBox --------------------- Stephen (Stericson)
h. Device Control -------------- Alexander Martinz




QUICK GUIDE (WINDOWS 10)

 install android-sdk
install android-platform-tools
Download https://dl.google.com/dl/android/aosp/angler-opm7.181205.001-factory-b75ce068.zip
OPEN PLATFORM TOOLS CREATE A NEW FOLDER "ANY-NAME" AND COPY Download https://dl.google.com/dl/android/aosp/angler-opm7.181205.001-factory-b75ce068.zip INSIDE NOW EXTRACT ALL
 RENAME "flash-all.sh" TO "flash-all.bat" (for windows)

Go to c:\adb where image folder is and double click flash-all.bat file
	(flash-all.sh is for Linux)
	(flash-base.sh is for Mac)

15. Wait for it to flash (downgrade)...this will take up to 10 minutes
	(phone reboots)

Warning: skip copying bootloader image avb footer (bootloader partition size: 0, bootloader image size: 3639296).
Sending 'bootloader' (3554 KB)                     OKAY [  0.390s]
Writing 'bootloader'                               OKAY [  0.193s]
Finished. Total time: 1.242s
Rebooting into bootloader                          OKAY [  0.008s]
Finished. Total time: 0.017s
< waiting for any device >
Warning: skip copying radio image avb footer (radio partition size: 0, radio image size: 49897472).
Sending 'radio' (48728 KB)                         OKAY [  3.789s]
Writing 'radio'                                    OKAY [  2.161s]
Finished. Total time: 6.800s
Rebooting into bootloader                          OKAY [  0.006s]
Finished. Total time: 0.018s
--------------------------------------------
Bootloader Version...: angler-03.84
Baseband Version.....: angler-03.88
Serial Number........: CVH7N16408000100
--------------------------------------------
extracting android-info.txt (0 MB) to RAM...
Checking 'product'                                 OKAY [  0.003s]
Checking 'version-bootloader'                      OKAY [  0.012s]
Checking 'version-baseband'                        OKAY [  0.013s]
archive does not contain 'fastboot-info.txt'
extracting boot.img (11 MB) to disk... took 3.331s
archive does not contain 'init_boot.img'
archive does not contain 'dtbo.img'
archive does not contain 'dt.img'
archive does not contain 'pvmfw.img'
extracting recovery.img (18 MB) to disk... took 8.395s
archive does not contain 'vbmeta.img'
archive does not contain 'vbmeta_system.img'
archive does not contain 'vbmeta_vendor.img'
archive does not contain 'vendor_boot.img'
archive does not contain 'vendor_kernel_boot.img'
archive does not contain 'odm.img'
archive does not contain 'odm_dlkm.img'
archive does not contain 'product.img'
extracting system.img (1912 MB) to disk... took 113.749s
archive does not contain 'system_dlkm.img'
archive does not contain 'system_ext.img'
extracting vendor.img (188 MB) to disk... took 11.347s
archive does not contain 'vendor_dlkm.img'
archive does not contain 'super_empty.img'
archive does not contain 'super_empty.img'
extracting boot.img (11 MB) to disk... took 2.152s
archive does not contain 'boot.sig'
archive does not contain 'super_empty.img'
Warning: skip copying boot image avb footer (boot partition size: 0, boot image size: 12383462).
Sending 'boot' (12093 KB)                          OKAY [  0.597s]
Writing 'boot'                                     OKAY [  0.181s]
archive does not contain 'super_empty.img'
extracting recovery.img (18 MB) to disk... took 3.259s
archive does not contain 'recovery.sig'
archive does not contain 'super_empty.img'
Warning: skip copying recovery image avb footer (recovery partition size: 0, recovery image size: 19420394).
Sending 'recovery' (18965 KB)                      OKAY [  0.520s]
Writing 'recovery'                                 OKAY [  0.271s]
archive does not contain 'super_empty.img'
archive does not contain 'super_empty.img'
extracting system.img (1912 MB) to disk... took 145.096s
archive does not contain 'system.sig'
Sending sparse 'system' 1/5 (482756 KB)            OKAY [ 22.787s]
Writing 'system'                                   OKAY [  7.385s]
Sending sparse 'system' 2/5 (475402 KB)            OKAY [ 22.607s]
Writing 'system'                                   OKAY [  6.622s]
Sending sparse 'system' 3/5 (474990 KB)            OKAY [ 39.184s]
Writing 'system'                                   OKAY [  8.389s]
Sending sparse 'system' 4/5 (476568 KB)            OKAY [ 28.288s]
Writing 'system'                                   OKAY [  6.982s]
Sending sparse 'system' 5/5 (49108 KB)             OKAY [  2.465s]
Writing 'system'                                   OKAY [  0.671s]
archive does not contain 'super_empty.img'
extracting vendor.img (188 MB) to disk... took 14.222s
archive does not contain 'vendor.sig'
archive does not contain 'super_empty.img'
Warning: skip copying vendor image avb footer due to sparse image.
Sending 'vendor' (192577 KB)                       OKAY [  8.091s]
Writing 'vendor'                                   OKAY [  3.510s]
Erasing 'userdata'                                 OKAY [  2.331s]
mke2fs 1.46.6 (1-Feb-2023)
Creating filesystem with 14328190 4k blocks and 3588096 inodes
Filesystem UUID: c0edc0de-1993-11ef-97ea-25cb3e9e2799
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424

Allocating group tables: done
Writing inode tables: done
Creating journal (65536 blocks): done
Writing superblocks and filesystem accounting information: done

adb reboot bootloader

Download https://dl.twrp.me/angler/twrp-3.5.1_9-0-angler.img.html



16. Setup phone as if was new

adb reboot bootloader

Download https://dl.twrp.me/angler/twrp-3.5.1_9-0-angler.img.html

now copy Download https://dl.twrp.me/angler/twrp-3.5.1_9-0-angler.img.html into platform tools main folder 

in address bar type cmd 

in terminal type:

fastboot flash recovery twrp-3.5.1_9-0-angler.img







fastboot reboot

In Android Browser Download the Magisk Manager App: https://tweakdroid.com/downloadlinks/magisk-manager-app/





