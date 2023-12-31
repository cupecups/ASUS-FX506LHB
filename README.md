# ASUS-FX506LHB

![alt text](https://github.com/cupecups/ASUS-FX506LHB/blob/b3d6fec0622f0499607f3dc9bf840f458dbf7a57/output.png)

for macos bigsur and newer<br>
resize EFI partition for dual boot win/mac<br>
- create new partition on disk management "500MB"
- cmd = diskpart
- list disk
- sel vol "xx"
- list part
- create partition efi
- format quick fs = fat32
- assign letter = p
- list volume (see all volume)
- list partition (check new efi already system partition)
- exit
- bcdboot c:\windows /s p: /f UEFI

<br>
set bcd boot to opencore bootloader <br>
bcdedit /set {bootmgr} path \EFI\BOOT\BOOTX64.efi

- ### **Not Working**
    - dGPU *(nVidia GTX)*
    - WiFi & BT (cause MTK chipset)
    - HDMI Port (cause combination intel & Nvidia)
    - Continuity Features (need replace chipset BCM94352Z)
    - dGPU | dGPU doesn't have any drivers on any macOS OS.

 ---
    
</details>
<!-- BOOTABLE END -->
<!-- BIOS START -->
<details open>
<summary><h3>BIOS Settings</h3></summary>
 
- Make Sure you have [Latest BIOS v311 or newer]([https://www.asus.com/supportonly/FX504GE/HelpDesk_BIOS/](https://www.asus.com/supportonly/fx506lhb/helpdesk_bios/))
- After Updating the BIOS, you just need to **DISABLE** `VT-D`
- **prealocated gpu size** `64MB`,
- **ENABLE** `AHCI`,,
- **DISABLE** `Secure Boot`, and you are good to go.
---
 
</details>

<!-- BIOS END -->

<!-- POST-INSTALL START-->

<details open>
  <summary><h3>Post Installation</h3></summary>

ALC CODEC:
~~~
- layout-id=13/21/66/28/11
- with dualboot windows alc can stop working on mac the fix is add bootarg="alctcsel=1 alcdelay=10000" or remove realtex driver on windows
~~~
 
Open Terminal.app and run those commands:
~~~
sudo pmset autopoweroff 0
sudo pmset powernap 0
sudo pmset standby 0
sudo pmset proximitywake 0
sudo pmset tcpkeepalive 0
~~~
>These 5 commands help fixing possible Sleep/Wake Issues
  
~~~
  - sudo rm /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist
  - sudo rm /Library/Preferences/SystemConfiguration/preferences.plist
~~~
>These 2 commands help fixing possible iCloud Ban/iMessages Ban or WiFi/Ethernet Issues (Use only if you want or need)

---

</details>
<!-- POST-INSTALL END -->
