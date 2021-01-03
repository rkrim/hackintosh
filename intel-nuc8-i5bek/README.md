# macOS on Intel NUC8i5BEK Bean Canyon

## Hardware Specifications

  ```
  HardwareId: [VendorId:DeviceId:Revision]
  DevicePath: PciRoot(Bus)/Pci(Device, Function)
  ```

- **North Bridge**: Intel Coffee Lake-U IMC
- **South Bridge**: Intel Cannon Point-LP
- **CPU**: Intel Coffee Lake Core i5-8259U @ [2.3GHz, 3.7GHz] (QuadCore)  
  [Intel Product Specifications](https://ark.intel.com/content/www/us/en/ark/products/135935/intel-core-i5-8259u-processor-6m-cache-up-to-3-80-ghz.html)
  - **_Clock_**: 23x100MHz, **_voltage_**: 0.8v
- **Memory**: 32Go, 2x Crucial 16Go DDR4-2666 SODIMM (CT16G4SFRA266)
  - **_Timings_**: 19-19-19-43 (CL-RCD-RP-RAS), **_voltage_**: 1.2v
- **Storage**: Crucial P2 M.2 2280 SSD CT1000P2SSD8 1To
  - **_Controller_**: Phison PS5013-E13T (PCIe 3.0 x4, NVMe 1.3)
  - **_HardwareId_**:  `[0xC0A9:0x540A:01]`
  - **_DevicePath_**: `PciRoot(0x0)/Pci(0x1D,0x0)/Pci(0x0,0x0)`
- **Graphics**: Intel Iris Plus Graphics 655
  - **_GPU Code Name_**: Intel Coffee Lake-U GT3e 28W (CFL-U GT3)
  - **_GPU Architecture_**: Intel Gen9.5, **_Execution Units_**: 48EU, **_GPU Clock_**: [300MHz, 1.05GHz]
  - **_HardwareId_**: `[0x8086:0x3EA5:R01]` - Sub `[0x8086:0x2074]`
  - **_DevicePath_**: `PciRoot(0x0)/Pci(0x2,0x0)`
  - **_Framebuffer_**: 0x3EA50009, **_Type_**: mobile, **_Connectors_**: 3, **_TOTAL STOLEN Memory_**: 58MB
  - **_AAPL,ig-platform-id_**: 0900A53E, **_device-id_**: A53E0000  
  [Intel iGPU Patching](https://dortania.github.io/OpenCore-Post-Install/gpu-patching/intel-patching/)
- **Monitor**: LG Ultra HD - 27" 4K (3840x2160)
  - **_MonitorId_**: GSM5B09
  - **_HardwareId_**: `[0x1E6D:0x5B09]`
- **Ethernet**: Intel Ethernet Connection (6) I219-V Gigabit Network Device
  - **_DeviceName_**: Ethernet Connection (6) I219-V
  - **_DevicePath_**: `PciRoot(0x0)/Pci(0x1F,0x6)`
  - **_HardwareId_**: `[0x8086:0x15BE:30]` - Sub `[0x8086:0x2074:30]`
- **_Wi-Fi_**: Intel Wireless-AC 9560 160MHz
  - **_DeviceName_**: Cannon Point-LP CNVi \[Wireless-AC\]
  - **_HardwareId_**: `[0x8086:0x9DF0:30]` - Sub `[0x8086:0x0034]`
  - **_DevicePath_**: `PciRoot(0x0)/Pci(0x14,0x3)`
- **_Bluetooth_**: Intel Wireless Bluetooth
    - **_DeviceName_**: Bluetooth 9460/9560 Jefferson Peak (JfP)
    - **_HardwareId_**: `[0x8087:0x0AAA:0002]`
    - **_DevicePath_**: `Port_#0010.Hub_#0001`
- **Card Reader**: Realtek RTS522A PCI Express Card Reader
  - **_HardwareId_**: `[0x10EC:0x522A:01]` - Sub `[0x8086:0x2074]`
  - **_DevicePath_**: `PciRoot(0x0)/Pci(0x1D,0x6)/Pci(0x0,0x0)`
- **Sound**:
  - Realtek ALC235 (ALC235)
    - **_HardwareId_**: `[0x10EC:0x0235:1000]` - Sub `[0x8086:0x2074]`
    - **_DevicePath_**: HD Audio Bus Driver
  - Intel Kaby Lake HDMI
    - **_DeviceName_**: Intel Cannon Point-LP PCH - cAVS (Audio, Voice, Speech) \[D0\]
    - **_HardwareId_**: `[0x8086:0x9DC8:30]` - Sub `[0x8086:0x2074]`
    - **_DevicePath_**: `PciRoot(0x0)/Pci(0x1F,0x3)`
- **USB**:
  - JHL6340 Thunderbolt 3 Bridge (C step) [Alpine Ridge 2C 2016]
    - **_HardwareId_**: `[0x8086:0x15DB]`
    - **_DevicePath_**: `PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0)`
    - **_DevicePath_**: `PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0)/Pci(0x0,0x0)`
    - **_DevicePath_**: `PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0)/Pci(0x1,0x0)`
    - **_DevicePath_**: `PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0)/Pci(0x2,0x0)`
  - JHL6340 Thunderbolt 3 USB 3.1 Controller (C step) [Alpine Ridge 2C 2016]
    - **_HardwareId_**: `[0x8086:0x9DED]`
    - **_DevicePath_**: `PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0)/Pci(0x2,0x0)/Pci(0x0,0x0)`
- **USB Hardware mapping**:
  - Internal:
    - Name: `HS10`, Port: `0x0A`
  - Front:
    - Right USB-A (Yellow): Name: `HS01`, Port: `0x01` | Name: `SS01`, Port: `0x0D`
    - Left USB-A (Blue): Name: `HS02`, Port: `0x02` | Name: `SS02`, Port: `0x0E`
  - Rear:
    - Bottom USB-A (Blue): Name: `HS03`, Port: `0x03` | Name: `SS03`, Port: `0x0F`
    - Top USB-A (Blue): Name: `HS04`, Port: `0x04` | Name: `SS04`, Port: `0x10`
    - Right USB-C (Thunbderbolt): Name: `UB21`, Port: `0x01` | Name: `UB31`, Port: `0x03`
- **BIOS**: BECFL357.86A.0085.2020.1007.1917
- **SMBIOS**: v3.2
