##  Chapter 1) Quick Start Install 
## (Windows or Linux as Primary OS - If you would rather have a traditional macOS install then read Chapter 2 before starting)

1. Create a macOS bootable USB the Recommended way using a macOS installer downloaded from the AppStore on either a real mac, existing Hackintosh, or a virtual machine hackintosh, or alternatively by using this [Turorial 1](https://www.reddit.com/r/hackintosh/comments/jrrhox/how_to_make_a_full_offline_installer_for_macos_on/) or [Turorial 2](https://pureinfotech.com/create-macos-bootable-usb-windows/) [Not Recommended]. Web Installers are not supported due to inconsistencies with USB Ethernet devices and no macOS support of the Marvel Avastart WiFi built into the Surface computers.
2. Once install disk is created mount EFI partition and copy one of the release OpenCore EFI folders to your Install Disk's EFI partition you just mounted. 
3. Boot into Windows or Linux and resize your partition and format as either NTFS or exFAT for you macOS install. In order to successfully install and run macOS with our EFI folders you must have at least an EFI partition of 200mb (300mb or greater recommended)
4. Boot from your usb, open Disk Utility and format the partition you just created as APFS and then install macOS on the partition you created just like on a real mac.
5. During first boot, after installing the OS, mount your EFI partition and copy over the OpenCore folder along with your BOOT folder found in the EFI folder on your install usb; you must copy/overwrite the same folders on the same partition located on your SSD.
6. Temporary: Move the "EFI/Microsoft" folder somewhere safe. I recommend the root of your EFI partition. If you leave the "Microsoft" folder in the EFI folder you will boot to Windows and not OpenCore.
7. Open your config.plist and generate a new serial number [Tutorial here](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/)
8. Install any additional software and drivers if needed for your specific needs
9. Reboot and enjoy!
