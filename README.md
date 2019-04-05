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

TODO

## Kexts

TODO

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
- [ ] 

## USB Ports

### EH01

*PR11* Hub:

* **HP11** Keep as unused
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
* **HP24** USB2 far right / Webcam
* **HP25** USB2 near right
* **HP26** Off
* **HP27** Off
* **HP28** Off

### XHC

*XHC* Hub:

* **HS01/SS01** USB2 far left
* **HS02/SS02** USB2 near left
* **HS03** Off
* **HS04** Off
* **HS05** Off
* **HS06** Off
* **HS07** Off
* **HS08** Off