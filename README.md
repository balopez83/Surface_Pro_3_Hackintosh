# Surface_Pro_3_Hackintosh
OpenCore based Hackintosh on Surface Pro 3 (May work with some modification on Surface Pro 1/2 and early Surface Books)

Full support for macOS version 10.14.X and above.

If you see anything that could be added or changed don't hesitate to make a pull request.


## *** NOTICE ***
### Do not update kexts labeled as "custom" manually, instead wait for an update. Kexts have been modified to support the Surface and generic kexts may break support.
### Upon first installation you must go to Settings and disable "Force Touch" in the trackpad settings for the Surface Trackpad to function properly
### Due to quirks in the Surface Pro 1/2/3 firmware, dual booting with Windows is problematic. Please see instructions in Chapter 5 [COMING SOON] detailing how to dual boot with Windows.
### Secure boot: In order to boot with secure boot on a key must be registered otherwise secure boot must be turned on. Please see instructions in Chapter 10 [COMING SOON] to register the secure boot key and boot with secure boot turned on


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
### [Chapter 9) Internal WiFi/Bluetooth Workaround for macOS support (COMING SOON)]
### [Chapter 10) Secure Boot ON with OpenCore using Grub (COMING SOON)]

## What works 

- macOS 10.14.X and above
- Graphics Acceleration: (occasional artifacts/glitches at high resolutions)
- Native Brightness Adjustments
- Native Audio Adjustments
- Fan
- USB
- Battery
- TypeCover Trackpad: w/gestures
- TypeCover Keyboard
- TypeCover Hotplug
- Audio
- WiFi: USB nano cards supported with the Realtek chipset
- iServices: Requires custom SMBIOS settings in OpenCore config.plist file. See the OpenCore Dortania Post-Install guide.
- USB Installer (no wifi support)
- SDcard
- Secure Boot: ON (see Chapter 5)
- Dual Boot: (see Chapter 5)



## What doesn't work or hasn't yet been tested

- WiFi: (Marvell Avastar - Unsupported)
- Bluetooth: (Marvell Avastar - Unsupported)
- Audio: Audio Jack & Audio over mDP (not yet tested)
- TouchScreen / Surface Pen
- Power Management: (Partially supported but not completed)
- Sleep / Wake: (Partially supported but not completed)
- TypeCover: close to sleep/open to wake
- mDP
- Accelerometer: (Will likely never work as macOS has never supported rotation natively with an Accelerometer)
- Recovery
- FileVault: (Not Yet Tested)
- DRM: (Not Yet Tested)


## Credits
Special thanks to the massive Hackintosh community for all your work that makes these guides and Surface Pro Hackintosh possible. Additional thanks goes to @acidanthera and [@Xiashangning](https://github.com/Xiashangning/BigSurface) for their tireless work on the software & kexts that make hackintoshing possible. <br>
