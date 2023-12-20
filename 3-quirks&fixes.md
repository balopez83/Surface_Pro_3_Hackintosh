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

4. In order to get macOS Hibernation working you are required to change your hibernatemode and make other power management adjustments. Please open Terminal and enter the following commands.
```
sudo pmset -a hibernatemode 25;
sudo pmset autopoweroff 0
sudo pmset powernap 0
sudo pmset standby 0
sudo pmset proximitywake 0
sudo pmset tcpkeepalive 0
```

5. You can enable an onscreen keyboard for touch screen only use of macOS using Accessability options. Enabling Sticky Keys is another useful way to make typing easier on the screen. Another interesting onscreen keybpard application comes from Irradiated Software and its called [Key Up](https://www.irradiatedsoftware.com/labs/).

6. If you are having issues with iMessage, FaceTime, or other iServices after an EFI or software update you can try the following to restore iMessage services.
   1. If you haven't yet, sign out of all iCloud services.
   2. Open a Finder window and click on your User Name then in a blank area right click and select
   3. Show View Options and from the resulting window select Show Library Folder.
   4. Open the newly revealed Library folder and select Caches
   5. From the Caches folder delete all files and folders beginning with :
     ```
     com.apple.iCloudHelper
     com.apple.imfoundation.IMRemoteURLConnectionAgent
     com.apple.Message
     ```
   6. In Finder navigate to Username/Library/Preferences and delete all files and folders beginning with
     ```
     com.apple.iChat.
     com.apple.icloud.
     com.apple.ids.service
     com.apple.imagent.
     com.apple.imessage.
     com.apple.imservice.
     ```
   7. Empty the Trash and Restart.
