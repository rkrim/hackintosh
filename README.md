This is a guide to install macOS on my hardware

## 1. Know the hardware

- Dell XPS 13 9350 - [Specifications](https://github.com/rkrim/hackintosh/tree/master/dell-xps13-9350)

## 2. Download macOS Installer

- From MacAppStore if already using macOS
  - [macOS Big Sur](https://apps.apple.com/fr/app/macos-big-sur/id1526878132), latest known version: 11.0.1.
  - [macOS Catalina](https://apps.apple.com/fr/app/macos-catalina/id1466841314), latest known version: 10.15.7.

## 3. Create a bootable macOS usb installer

### a. Create the installer

Make sure that the USB disk is formated in HFS+ (Mac OS Extended) and has GUID Partition Map scheme.

Use the 'createinstallmedia' command in Terminal.
Follow instructions on Apple documentation about [how to create a bootable installer for macOS](https://support.apple.com/en-us/HT201372).

Here is an extract for Big Sur and Catalina

```
NOTE: Make sure to replace 'MyVolume' with the right USB volume name in the below commands.

## macOS Big Sur
sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume

## macOS Catalina
sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

### b. Bootloader

At this step, we have a bootable macOS USB Installer that can be used to install macOS on Apple Computers.

To make it bootable on other computers, we need to mount the EFI partition of the USB disk and add a bootloader and by the way, also add required firmware drivers, kexts, patches and other needed stuff.

There is a lot of bootloader projects out there, the most popular one are Clover and OpenCore.
When you can, always choose OpenCore as it has a better and more secure approach ([Why OpenCore](https://dortania.github.io/OpenCore-Install-Guide/why-oc.html)).

This step is computer specific, so go to the right section on the right hardware directry.

## Modify BIOS/UEFI Settings

Depending on computers, some components and/or settings can prevent macOS from booting.

Those components needs to be turned off and settings needs to be changed at least until the install successfully finishes.

## Install macOS

Install macOS like on a regular Apple computer.

## Post Install

- Copy bootloader and all other files in EFI folder from usb disk to the disk where macOS was installed.
- From now on you can unplug the installer usb disk.
- When possible, undo changes made in BIOS and/or UEFI
- Reboot.

## Tools

- [Clover](https://github.com/CloverHackyColor/CloverBootloader/releases)
- [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases)
- [MountEFI](https://github.com/corpnewt/MountEFI)
- [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/)
- [OpenCore Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/)
- [ProperTree](https://github.com/corpnewt/ProperTree)
- [Hackintool](https://github.com/headkaze/Hackintool/releases)

## Community and Documentation

- [Hackintosh Gitbook](https://hackintosh.gitbook.io/)
- [OpenCore Install Guide (dortania)](https://dortania.github.io/OpenCore-Install-Guide/)
- [AMD Vanilla OpenCore](https://github.com/AMD-OSX/AMD_Vanilla)
- [Hackintosh](https://hackintosh.com/)
- [General Framebuffer Patching Guide](https://www.tonymacx86.com/threads/guide-general-framebuffer-patching-guide-hdmi-black-screen-problem.269149/)
- [An iDiot's Guide To Lilu and its Plug-ins](https://www.tonymacx86.com/threads/an-idiots-guide-to-lilu-and-its-plug-ins.260063/)