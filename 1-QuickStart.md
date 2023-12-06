##  Chapter 1) Quick Start Install 
## (Windows or Linux as Primary OS - If you would rather have a traditional macOS install then read Chapter 2 before starting)

1. Create a macOS bootable USB the Recommended way using a macOS installer downloaded from the AppStore on either a real mac, existing Hackintosh, or a virtual machine hackintosh, or alternatively by using this [Turorial](https://pureinfotech.com/create-macos-bootable-usb-windows/) [Not Recommended].
2. Once install disk is created mount EFI partition and copy one of the release OpenCore EFI folders to your Install Disk's EFI partition you just mounted. 
3. Boot into Windows or Linux and resize your partition and format as either NTFS or exFAT for you macOS install. In order to successfully install and run macOS with our EFI folders you must have at least an EFI partition of 200mb (300mb or greater recommended)
4. Boot from your usb, open Disk Utility and format the partition you just created as APFS and then install macOS on the partition you created just like on a real mac.
5. During first boot, after installing the OS, mount your EFI partition and copy over the OpenCore folder along with your BOOT folder found in the EFI folder on your install usb; you must copy/overwrite the same folders on the same partition located on your SSD.
6. Temporary: Move the "EFI/Microsoft" folder somewhere safe. I recommend the root of your EFI partition. If you leave the "Microsoft" folder in the EFI folder you will boot to Windows and not OpenCore.
7. Open your config.plist and generate a new serial number [Tutorial here](https://hackintosher.com/forums/thread/generate-your-own-hackintosh-serial-number-board-serial-number-uuid-mlb-rom-in-clover.306/)
8. Install any additional software and drivers if needed for your specific needs
9. Reboot and enjoy!
