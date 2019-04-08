# Clover configuration for MSI GE70 2PC
MSI GE70 2PC Hackintosh configuration for macOS Mojave

## Hardware

* CPU: Intel i5-4200H Haswell
* GPU: Intel HD4600
  * ID: 0x416
* Chipset: Intel HM86 Lynx Point
* Memory 16GB
* Audio: Realtek ALC892
* Network: Qualcomm Atheros Killer E220x
* WiFi: Qualcomm Atheros AR9285 PSIe (only 2.4Gz)
* SSD: Intel 530 series 240Gb

## Applied DSDT Patches

DSDT Patches from RehabMan [repo](http://raw.githubusercontent.com/RehabMan/Laptop-DSDT-Patch/master):

* Remove _DSM methods
* Fix _WAK Arg0 v2
* HPET Fix
* SMBUS Fix
* IRQ Fix
* RTC Fix
* OS Check Fix Windows 8
* Fix Mutex with non-zero SyncLevel
* Fix PNOT/PPNT
* 7-8 Series USB
* USB PRW 0x0D
* Haswell-LPC
* Brightness fix
* Insert DTGP

SSDT Patches:

* SSDT-UIAC-ALL: See `SSDT-UIAC-ALL.dsl` source and compiled `/EFI/CLOVER/ACPI/patched/SSDT-UIAC-ALL.aml`.
The patch enables usable USB2 and USB3 ports includes internal Web Cam.
Also the patch disables SteelSeries backlight port to prevent a lot of error messages in the system log.
Kext `USBInjectAll.kext` must be installed.

## Kexts

* ACPIBatteryManager.kext - battery.
* Lilu.kext - kext patcher. Requires various plugins:
  * WhateverGreen.kext - Intel integrated video driver.
  * VirtualSMC.kext - Advanced SMC emulation.
  * AppleALC.kext - Native macOS HD audio for not officially supported codecs.
  * NoVPAJpeg.kext - Workarounds Quicklook issues on 10.14 when using macmodels with IGPU on CPUs without IGPU. Can be used as an alternative to MacPro6,1 model. Possible not required for correct work on this laptop.
* ApplePS2SmartTouchPad.kext - keyboard and Elan/Synaptics touchpad driver.
* AtherosE2200Ethernet.kext - network card driver.
* CodecCommander.kext - fix sound after sleep.
* corecapture.kext and IO80211Family.kext - Qualcomm Atheros AR928x driver. Remove both if you have another card.
* USBInjectAll.kext - disable unused USB ports.

## What is working

* GPU Acceleration (for success work and avoiding 8 apples required UEFI+CSM settings in BIOS)
* Battery indicator
* Backlight (fn+Up/Down and fn+F3/F5)
* Sound (tested only build-in speakers and microphone). CodecCommander.kext used to keep sound working after sleep.
* Touchpad with gestures
* Sleep
* SSD Trim is disabled for APFS otherwise you will have long boot and lot of warnings during boot
* Wi-Fi
* Network must working but not tested
* USB ports
* Web camera

## Partially working

* ???

## TODO

- [x] Web Camera sometimes working. Need to finalize USB configuration.
- [ ] Check and fix if Intel SpeedStep working and configured correctly

## USB Ports

### EH01

*PR11* Hub:

* **HP11** Keep as unused (whole EH01 can be disabled but I'm lazy)
* **HP12** Off
* **HP13** Off
* **HP14** Off - MSI EPF USB - SteelSeries keyboard backlight. Must be disabled.
* **HP15** Off
* **HP16** Off
* **HP17** Off
* **HP18** Off


### EH02

*PR21* Hub:

* **HP21** Off
* **HP22** USB2 far right
* **HP23** Off
* **HP24** USB2 Webcam
* **HP25** USB2 near right
* **HP26** Off
* **HP27** Off
* **HP28** Off

### XHC

*XHC* Hub:

* **HS01/SS01** USB2/USB3 far left
* **HS02/SS02** USB2/USB3 near left
* **HS03** Off
* **HS04** Off
* **HS05** Off
* **HS06** Off
* **HS07** Off
* **HS08** Off
