# macOS on Dell XPS 13 9350

## Hardware Specifications `[VendorId:DeviceId:Revision]`

- **North Bridge**: Intel Skylake-U IMC
- **South Bridge**: Intel Sunrise Point-LP
- **CPU**: Intel Skylake Core i7-6560U @ 2.20GHz
  - **_Platform ID_**: 0x19260000, **_clock_**: 22x100MHz, **_voltage_**: 0.8v
- **Memory**: SK Hynix 8GB LPDDR3-SDRAM (1.2v)
  - **_Timings_**: 14-17-17-40 (CL-RCD-RP-RAS)
- **Storage**: Samsung PM951 NVMe 256Go `[0x144D:0xA802:01]`
- **Graphics**: Intel Iris Graphics 540
  - **_GPU Code Name_**: Skylake-U GT3e (SKL-U GT3e) `[0x8086:0x1926:0A]`
  - **_Max VRAM_**: 1536MB, **_dedicated memory_**: 128MB, **_framebuffer_**: 0x19260000, **_port_**: 3
- **Monitor**: Sharp LQ133Z1 (Dell RXN49) - 13.3" LCD QHD+ Touchscreen (3200x1800)
  - **_Monitor ID_**: SHP144A
  - **_Touch Layer_**: ELAN `[0x04F3:0x20D0:1112h]` (on USB 3.0 Root Hub @Port4)
- **Wireless Card**: Dell Wireless 1820A (DW1820A) - `Hardware Rev. CN-0VW3T3`
  - **_Wi-Fi_**: Broadcom Inc. BCM4350 802.11ac Wireless Network Adapter `[0x14E4:0x43A3:08]` (on `PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0)`)
  - **_Bluetooth_**: Broadcom Crop. Dell Wireless 1820A Bluetooth 4.1 LE `[0x0A5C:0x6412:0112h]` (on USB 3.0 Root Hub @Port3)
- **Sound**: Intel Sunrise Point-LP PCH `[0x8086:0x9D70:21]` (PCI Device)
  - Realtek ALC256 (ALC3246) `[0x10EC:0x0256:1000]`
  - Intel Skylake HDMI `[0x8086:0x2809:1000]`
- **Card Reader**: Realtek PCI-E Card Reader `[0x10EC:0x525A:01]` (PCI Device)
- **Webcam**: `[0x0C45:0x670C:5626h]` (on USB 3.0 Root Hub @Port 5)
- **USB**:
  - USB-A Right Port (On USB 3.0 Root Hub @Port1)
  - USB-A Left Port (On USB 3.0 Root Hub @Port2)
  - USB-C Left Port - Intel DSL6340 (Alpine Ridge 2C 2015)
    - USB 3.1 xHCI Controller `[0x8086:0x15B5:00]`
    - Thunderbolt 3 Bridge `[0x8086:0x1576:00]`
- **Sensor**: Dell SMI-B (ISA B2h)
- **BIOS**: v1.13.0
- **SMBIOS**: v2.8

## Features working status (v0.3 - macOS 10.15.7 Catalina)

| Feature | Status | Notes |
| ------------- | ------------- | ------------- |
| **Display** | ✅ Working | Display works and goes up to 1600x900@2x (2x retina). Brightness adjustment works. Intel 540 GPU Detected |
| **Touchscreen** | ✅ Working | macOS with touchscreen, here it is 😜 |
| **Keyboard** |  ✅ Working | PS2, `Alt` mapped as `⌘ Command`, `Windows` mapped as `⌥ Option` |
| **Trackpad** |  ✅ Working | PS2, Full gesture support |
| **Storage** | ✅ Working | Samsung PM951 NVMe 256Go |
| **Speakers** | ✅ Working ||
| **Headphones** | ✅ Working ||
| **Microphone** | ✅ Working ||
| **USB** | ✅ Working ||
| **SD Reader** | ✅ Working ||
| **Bluetooth** | ✅ Working ||
| **Handoff** | ✅ Working ||
| **Sidecar** | ✅ Working | 🔥 Heavy power consumption |
| **Apple Cloud Services** | ✅ Working | iMessage, Facetime, iCloud, AppStore |
| **WiFi 2.4 GHz** | ✅ Working ||
| **WiFi 5 GHz** | 🔶 Partially working | 5 Ghz Network connexion but sometimes drops |
| **Camera** | 🔶 Partially working | Tested with Facetime and PhotoBooth |
| **USB-C** | 🔶 Partially working | Charging and usb storage devices work, display not working. |

### EFI Drivers
Files with `efi` extension, that extends Clover features.  
Can be found in following folder: `/EFI/CLOVER/drivers`

- **ApfsDriverLoader.efi** ✅:  
Enables support of APFS file system from Container for macOS High Sierra and Later.
- **HFSPlus.efi** ✅:  
Enables support of HFS+ file system.  
Required to see macOS installer on usb drives.
- **AptioMemoryFix.efi** ✅:  
Fix certain AMI APTIO UEFI Firmware issues relevant to booting macOS.
- **FSInject.efi** ✅:  
Enables File System injection of kexts (into kernelcache).
- **NTFS.efi** ⌥:  
Enables support of NTFS file system.
- **AudioDXE.efi** ⌥:  
HDA Driver to play start up sound at boot time.

### Kexts
Kexts is a concatenation of `Kernel` and `Extension`, those are macOS level drivers.
Can be found in following folder: `/EFI/CLOVER/kexts`

- **Lilu.kext**:  
Kernel extension bringing a platform for arbitrary kext, library, and program patching throughout the system for macOS.
- **NoTouchID.kext**:  
***Lilu plugin*** for disabling TouchID support.
- **WhateverGreen.kext**:  
***Lilu plugin*** providing patches to select GPUs on macOS.
- **AirportBrcmFixup.kext**:  
***Lilu plugin*** Enabling non-native Airport Broadcom Wi-Fi cards.
- **BrcmBluetoothInjector.kext**:  
A set of kernel extensions that enables Bluetooth card to work using RAMUSB.  
Needs (`BrcmFirmwareData.kext, BrcmPatchRAM3.kext`)
- **AppleALC.kext**:  
Enables native macOS HD audio for not officially supported codecs without any filesystem modifications.
- **VerbStub.kext**:  
Hackintosh combojack support for alc256/alc255. ***Need to execute installer on post-install***
- **UVC2FaceTimeHD.kext**:  
Enables Facetime Camera.
- **VirtualSMC.kext**:
Advanced Apple SMC emulator in the kernel. Requires Lilu for full functioning.
  - **SMCDellSensors.kext**: Enables Dell Sensors
  - **SMCBatteryManager.kext**: Enables Battery monitoring
- **NVMeFix.kext**:  
Set of patches for the Apple NVMe storage driver, IONVMeFamily. Improve compatibility with non-Apple SSDs.
- **IOElectrify.kext**:  
Enables always-on power to Intel Thunderbolt hardware.
- **Sinetek-rtsx.kext**:  
Enables SD Card Reader
- **VoodooPS2Controller.kext**:  
Add support for PS2 Controllers such as keyboard, mouse and trackpad.
This enables the use of any from one to four finger gestures defined by Apple.
- **VoodooI2C.kext**:  
Add support for I2C bus devices such as ELAN Touchscreen.  
Needs (`VoodooI2CHID.kext`)

## Post Install and important notes
- Apple logo on boot instead of logs:  
Remove `-v` and `debug=0x10` from NVRAM arguments
- Apple Service:  
To enable Apple services like iMesage, generate ***SMBIOS Info*** with tools like [`Clover Configurator`](https://mackie100projects.altervista.org/download-clover-configurator/) or [`GenSMBIOS`](https://github.com/corpnewt/GenSMBIOS).  
Most important infos are **`Type, Serial, Board Serial, SmUUID`**.
- Headphones:  
Headphones are supported with [ComboJack](https://github.com/hackintosh-stuff/ComboJack), to enable full support run `ComboJack_Installer/install.sh` in terminal and reboot.
- Updating `VoodooI2C` requires disabling the embedded `VoodooInput.kext` plugin to avoid collision with `VoodooPS2Controller`'s own plugins.

## Similar Projects & Community
- [Github: syscl - XPS9350-macOS](https://github.com/syscl/XPS9350-macOS)
- [Github: hackintosh-stuff - XPS9350-macOS](https://github.com/hackintosh-stuff/XPS9350-macOS)
- [Github: the-darkvoid - XPS9360-macOS](https://github.com/the-darkvoid/XPS9360-macOS)
- [Github: jsassu20 - macOS Full Support of Dell DW1820a Broadcom BCM94350Zae](https://github.com/jsassu20/Dell-DW1820a-Broadcom-BCM94350Zae-macOS-Full-Support)
- [tonymacx86: Guide - Dell xps 13 9350 - Catalina](https://www.tonymacx86.com/threads/guide-dell-xps-13-9350-catalina.296796/)
- [tonymacx86: Guide - Dell xps 13 9350 - Catalina 10.15.5 - Clover](https://www.tonymacx86.com/threads/guide-xps-13-9350-catalina-10-15-5-clover-hotpatch-simple-clean-ish.299997/)
