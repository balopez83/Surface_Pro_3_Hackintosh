# Surface Pro 3 Hackintosh With Touch Working
OpenCore based Hackintosh on Surface Pro 3

Full support for macOS version 10.14.X through 14.X.X. macOS Ventura and up supported and requires OpenCore Legacy Patcher to regain graphics support.

If you see anything that could be added or changed don't hesitate to let me know.

![Screenshot 2023-03-07 at 2 19 15 PM](https://user-images.githubusercontent.com/53441362/223567083-c2dafb00-a842-4ea7-81fe-e90056486810.png)


## *** NOTICE ***
- ## macOS Ventura and up is now mostly supported. Graphics Acceleration is only supported using OpenCore legacy patcher. It is recommended that you download OCLP first and upgrade to Ventura from Monterey.
- ### Do not manually update kexts labeled as "custom"; instead wait for an update. Custom kexts have been modified to support the Surface Pro 3 and generic kexts WILL break support (e.g. TouchScreen & Keyboard support)
- ### Upon first installation you must go to Settings and disable "Force Touch" in the trackpad settings for the Surface Trackpad to function properly
- ### Due to quirks in the Surface Pro 3 firmware, dual booting with Windows is problematic.
- ### Secure boot: In order to boot with secure boot on a key must be registered otherwise secure boot must be turned off. Please see instructions in Chapter 9 to register the secure boot key and boot with secure boot turned on
- ### Touch works however you will need to tap the screen several times in a row until it registers (approx 10 times). Once registered it will work as expected until the next boot when you will have to do this again. 


## Surface Pro 3 Specifications:

| Model: | i3 | i5 | i7 |
|-|-|-|-|
|CPU| i3-4020Y Single Core 1.5 Ghz| i5-4300U Dual Core 1.9-2.9 Ghz| i7-4650U Dual Core 1.7-3.3 Ghz |
|Display| 12" ClearType HD 2160x1440 | same | same |
|GPU| HD 4200 | HD 4400 | HD 5000 |
|RAM| 4 GB | 4/8 GB | 8 GB |
|SSD| 64/128 GB SATA | 128/256 GB SATA | 128/256/512 GB SATA |
|WiFi| Marvell Avastar b/g/n/ac | same | same |
|Batt| 42 W/h | same | same |
|Ports| 1x USB 3.0, 1x mDP, 1x 3.5 Audio Jack | same | same |
|   | 1x Type Cover Port, 1x Surface Dock Port | same | same |



## Instruction Guides

### [Chapter 1) Quick Start Install](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/1-QuickStart.md)
### [Chapter 2) BootCamp Install](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/2-BootCamp.md)
### [Chapter 3) Quirks & Fixes](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/3-quirks%26fixes.md)
### [Chapter 4) Additional Drivers](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/4-drivers.md)
### [Chapter 5) Booting Other OS's with OpenCore](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/5-OtherOS%26OC.md)
### [Chapter 6) Other Operating Systems](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/6-OtherOS.md)
### [Chapter 7) Other OS Quirks & Fixes](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/7-OtherOSquirks%26fixes.md)
### [Chapter 8) Windows 11 Upgrade and/or Clean Install](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/8-Windows-11.md)
### [Chapter 9) Secure Boot ON with OpenCore using Grub](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/9-SecureBootOn.md)
### [Chapter 10) Haswell Legacy Support (macOS Ventura only)](https://github.com/balopez83/Surface_Pro_3_Hackintosh/blob/main/10-HaswellLegacySupport.md)

## What works 

- macOS 10.14.X through 14.X.X (Ventura and newer req's special modifications)
- Graphics Acceleration
- Native Brightness Adjustments
- Native Audio Adjustments
- Fan
- USB
- Battery (Battery status & management works in all OS's)
- A/C Detection
- TypeCover Trackpad: w/gestures
- TypeCover Keyboard
- TypeCover Hotplug
- Audio / Headphones / Microphone
- WiFi: USB nano cards supported with the Realtek chipset
- iServices: Requires custom SMBIOS settings in OpenCore config.plist file. See the OpenCore Dortania Post-Install guide.
- USB Installer (no wifi support)
- SDcard
- Secure Boot: ON (see Chapter 9)
- Dual Boot: (see Chapter 5)
- Windows Boot From OpenCore Supported
- TouchScreen (Works in macOS, Recovery, Installer)
- Surface Pen
- Recovery
- FileVault
- Power Management
- mDP
- Dock MDP/HDMI
- Dock USB
- Dock Ethernet
- Deep Sleep (macOS style Hibernation; See Quirks & Fixes for required power setting changes)

## Partially Working/In-Progress (Working ONLY After Warm Boot From Windows/Linux)

- Power Button (Sleep/Wake)
- Volume Down
- Volume Up
- Windows Button (Disabled Pending Assigning A Useful Task For The Button)


## Current Issues Being Worked On

- TypeCover Sleep/Wake Trigger


## Won't Ever Work

- WiFi: (Marvell Avastar - Unsupported)
- Accelerometer: (Unsupported)
- Bluetooth: (Marvell Avastar - Unsupported)
- DRM: (Unsupported on iGPU)


## Credits
Special thanks to the massive Hackintosh community for all your work that makes these guides and Surface Pro Hackintosh possible. Additional thanks goes to @acidanthera and [@Xiashangning](https://github.com/Xiashangning/BigSurface) for their tireless work on the software & kexts that make hackintoshing possible. Custom VoodooI2C.kext utilizes code with permission from Xiashangning's BigSurface kext to enable Surface Keyboard support. <br>
