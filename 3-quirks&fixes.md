## Chapter 3) Quirks & Fixes

### After installing macOS you may find several things that need to be resolved in order to have a true mac experience. Please use the following quirks & fixes to fix remaining issues.

1. If you are missing OpenCore from your boot options boot your computer and press both the 'FN' AND 'F1' keys to load the boot list. Select the option to start the UEFI Shell. Once the shell loads type the following:
```
bcfg boot add 0 FS0:\EFI\OC\OpenCore.efi "OC"
```
Where "0" after add is where you assign boot order. "0" would be the first position. "OC" is the name of the boot option. You may name your boot option anything you want. "FS0" is the drive and partition where your OpenCore EFI files are located. If you are installing macOS to anything other than the built in SSD in the 1st partition EFI (standard configurtion) you will need to determine the correct path of your OpenCore Files. If you need more information regarding how to edit your UEFI boot options you can go [here](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface).


2. You can enable HiDPI mode which adds more resolution options to the list of available display resolutions.

Enter the following command in terminal post-installation then reboot:

```
sudo defaults write /Library/Preferences/com.apple.windowserver.plist DisplayResolutionEnabled -bool true
```


3. macOS sets "Force Click and Haptic Feedback" enabled which causes unexpected behavior when clicking on the trackpad. You will need to turn off this function in order to have a trackpad that operates as expected. You can turn it off by going to:
``` 
System Preferences > Trackpad > Uncheck Force Click and Haptic Feedback
```


