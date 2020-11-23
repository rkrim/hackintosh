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
  - **_Wi-Fi_**: Broadcom Inc. BCM4350 802.11ac Wireless Network Adapter `[0x14E4:0x43A3:08]` (PCI Device)
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

## Features working status (v0.2 - macOS 10.15.7 Catalina)

| Feature | Status | Notes |
| ------------- | ------------- | ------------- |
| **Display** | ✅ Working | Display works and goes up to 1600x900@2x (2x retina). Brightness adjustment works. Intel 540 GPU Detected |
| **Touchscreen** | ✅ Working | macOS with touchscreen, here it is 😜 |
| **Keyboard** |  ✅ Working | PS2, `Alt` mapped as `⌘ Command`, `Windows` mapped as `⌥ Option` |
| **Trackpad** |  ✅ Working | PS2, Full gesture support |
| **Storage** | ✅ Working | Samsung PM951 NVMe 256Go |
| **Speakers** | ✅ Working ||
| **Microphone** | ✅ Working ||
| **USB** | ✅ Working ||
| **Bluetooth** | ✅ Working ||
| **Handoff** | ✅ Working ||
| **Apple Cloud Services** | ✅ Working | iMessage, Facetime, iCloud, AppStore |
| **WiFi 2.4 GHz** | ✅ Working ||
| **WiFi 5 GHz** | 🔶 Partially working | 5 Ghz Network connexion but sometimes drops |
| **Camera** | 🔶 Partially working | Tested with Facetime and PhotoBooth |
| **USB-C** | 🔶 Partially working | Charging and usb storage devices work, display not working. |
| **Headphones** | ❌ Not working | Headphones detected but no sound or crappy |
| **SD Reader** | ❌ Not working ||

### EFI Drivers
Files with `efi` extension, that extends Clover features.  
Can be found in following folder: `/EFI/CLOVER/drivers`

- **NvmExpressDxe.efi**:  
Enables support of NVM Express Devices.
- **ApfsDriverLoader.efi**:  
Enables support of APFS file system from Container for macOS High Sierra and Later.
- **HFSPlus.efi**:  
Enables support of HFS+ file system.  
Required to see macOS installer on usb drives.
- **AptioMemoryFix.efi**:  
Fix certain AMI APTIO UEFI Firmware issues relevant to booting macOS.
- **FSInject.efi**:  
Enables File System injection of kexts (into kernelcache).
- **DataHubDxe.efi**:  
Driver responsible to preload the DataHub with status information copied in from PEI HOBs.  
Needed by some BIOSes
- **PartitionDxe.efi**:  
Enables support of non usual partition maps such as hybrid GPT/MBR or Apple Partition Map.  
Required to boot recovery on OS X 10.7 through 10.9.
- **AudioDXE.efi**:  
HDA Driver to play start up sound at boot time.

### Kexts
Kexts is a concatenation of `Kernel` and `Extension`, those are macOS level drivers.
Can be found in following folder: `/EFI/CLOVER/kexts`
