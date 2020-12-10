# Hackintosh on z390 - Intel CoffeeLake

## Introduction
Since macOS Big Sur was released in the end of 2020, my old mac-mini was not able to do the upgrade. Then I sold it and I bought the following configuration (see Hardware configuration section).
I've followed many tutorials in order to prepare an USB stick to install macOS Big Sur on my new configuration but I'm facing the following issues...

## Issues
- Thursday 10th of december 2020: Infinite loop with OpenCore: '1. Install macOS Big Sur (external)' then many things appear on the screen, then it reboots, then '1. Install macOS Big Sur (external)', etc.
- Solved: Tuesday 8th of december 2020: Boot is blocked, system saying 'SMCBatteryManager bmgr: @ failed to find batteries or adapters'. This issue was solved by removing SMC things I previously ticked using [OC.Gen-X](https://github.com/Pavo-IM/OC-Gen-X).

## Hardware (Desktop) configuration 
- Motherboard Gigabyte Z390 AORUS PRO
- CPU Intel Core i7-9700K (Coffee-Lake)
- SSD Samsung V-Nand SSD 970 EVO Plus NVMe M.2 500GB
- DDR 4 Viper by Patriot 32GB (2 x 16GB) PC4-24000 3000MHz
- Wireless Network Adapter Fenvi FV-T919 (with Blutooth) compatible with macOS 
- USB stick Sandisk USB 3.0 32GB (16GB should be enough but I had a 32GB one)

## Tools

### Tools Links

#### Official websites 
- [OC.Gen-X](https://github.com/Pavo-IM/OC-Gen-X)
- [MountEFI](https://github.com/corpnewt/MountEFI)
- [ProperTree](https://github.com/corpnewt/ProperTree)
- [OpenCore page for Coffee Lake Desktop](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#starting-point)
- [OpenCore Sanity Checker](https://opencore.slowgeek.com/)
- [ACPI files](https://dortania.github.io/Getting-Started-With-ACPI/ssdt-platform.html#desktop)

#### Versions I used
- [OC.Gen-X](https://github.com/amarnaud2/hackintosh/tree/main/tools/OC.Gen-X.app.zip)
- [MountEFI](https://github.com/amarnaud2/hackintosh/tree/main/tools/MountEFI-update.zip)
- [ProperTree](https://github.com/amarnaud2/hackintosh/tree/main/tools/ProperTree-master.zip)
- [ACPI files](https://github.com/amarnaud2/hackintosh/tree/main/tools/SSDT.zip)

### Procedure
1. Create an USB installer for mac OS Big Sur using a Macbook Pro with Big Sur
2. Generate EFI base with [OC.Gen-X](https://github.com/Pavo-IM/OC-Gen-X) on desktop
3. Download ACPI Files compiled (.aml) and unzip the downloaded archives
4. Mount the EFI partition (from USB key)
5. Erase existing EFI folder on USB key
6. Copy my generated EFI (step 2) on the USB key EFI partition
7. Copy ACPI (.aml) files in /usb_key/EFI/OC/ACPI
8. Launch ProperTree
9. Open /usb_key/EFI/OC/config.plist file
10. Inject ACPI files by using 'File' > 'OC Snapshot' in ProperTree 
11. Choose /usb_key/EFI/OC folder and validate 
12. Clean snapshot by using 'File' > 'OC Clean Snapshot' in ProperTree and validate
13. Check values according [OpenCore page for Coffee Lake Desktop](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#starting-point) and update if necessary
14. When file seems okay, then save it using 'File' > 'Save' in ProperTree and then quit ProperTree
15. Check /usb_key/EFI/OC/config.plist file with [OpenCore Sanity Checker](https://opencore.slowgeek.com/). My generated report is [here](https://github.com/amarnaud2/hackintosh/blob/main/OpenCore-config.plist-Sanity-Checker.pdf)
16. When it's done, completely eject the USB key and unplug it
17. Turn on target computer and check BIOS settings give [Open Core Intel BIOS settings section](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#intel-bios-settings)
18. Plug the USB key on the target machine and reboot

## My current generated EFI
[ACPI files](https://github.com/amarnaud2/hackintosh/efi-aorus-z390/EFI)
