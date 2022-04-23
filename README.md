# This read me file is work in progress
# Thinkpad-P51-Opencore-Hackintosh

Last updated: 2022.4.22

**Disclaimer:
This guide is only for educational purpose. By following this guide, you agree to take full responsibility for any damage to your system and any other things that comes out from the guide.**

## Platform Specifications
https://psref.lenovo.com/syspool/Sys/PDF/ThinkPad/ThinkPad_P51/ThinkPad_P51_Spec.PDF

## Tested Specs

- CPU: i7-7700HQ
- GPU: HD630
- RAM: 32GB DDR4 (4 * 8GB)
- Motherboard/Laptop Make and Model: Lenovo Thinkpad P51 20HH 
- Display: 2K @ 165Hz (panel#: N156KME-GNA). Originally the machine comes with a 4K screen.
- Audio Codec: ALC298 (ALC3268)
- Ethernet Card: Intel I219-V
- Wifi/BT Card: BCM94352Z
- Touchpad and touch display devices: Symaptics touchpad
- BIOS revision: 1.57

## List of hardwares and their compatibilities
| Category | Element | Compatibility | Notes |
| ------------- | ------------- | ------------- | ------------- | 
| CPU | i7-7700HQ | Working✅ | Power management works correctly.
| GPU | HD630 | Working✅ | See additional comment #1. Need additional config in EFI\OC\config.plist.
| | NVIDIA M1200 | Nope ❌ | Will never work as there are no driver support since MacOS 10.14. |
| MEMORY | 1x16GB | Working✅ | |
| DISPLAY | 1440P @ 144Hz, scaled to "looks like" 1600x900 | Working✅ | Can't get to 165Hz due to limited pixelclock for HD630 (even with maximum pixelclock override). Requires a combination of `SwitchResX` and `RDM`. See additional comment #2.|
| STORAGE | Samsung 970 Evo 1TB | Working✅| |
| ETHERNET | Intel I219-V | Working✅ | |
| WLAN | BCM94352Z | Working✅ |  |
| CAMERA | Internal | Working✅ | Requires custom USBMap.kext. See https://github.com/corpnewt/USBMap |
| AUDIO | ALC3268 | Working✅ | AppleALC.kect + Layout #3 as per https://dortania.github.io/OpenCore-Post-Install/universal/audio.html#finding-your-layout-id|
| PORTS | 4xUSB3.1 Gen 1 (3.0) |  Working✅ | Requires custom USBMap.kext. See https://github.com/corpnewt/USBMap|
| KEYBOARD | Non backlit keyboard | Working✅ | I don't have a backlit keyboard (used to have one but that got damaged by a bottle of water. the newly replaced one doesn't have backlight.) |
| Trackpoint | Synaptics | Partially working ⚠️ | Thr |
| Touchpad | Synaptics | Partially working ⚠️  | See if it is possible to add more gestures |
| Dock | | Untested ⚠️| Theoretically possible as per https://github.com/MirkoCovizzi/thinkpad-p51-hackintosh |
| 1xUSB C (Thunderbolt) | | Untested ⚠️ | Theoretically possible for eGPU output since it worked in 10.15 as per https://github.com/AsahiKou/ThinkPadP51-Hackintosh-Catalina/issues/1. Untested for other TB3 devices.|
| BLUETOOTH | BCM94352Z | Nope, but work in progress ❌| There seem to be some issues with Broadcome-related kexts in Monterey, e.g., `BrcmBluetoothInjector.kext` causes freeze during installation process. But it is theoretically possible to coninue using BCM94352Z via BlueToolFixup. See https://github.com/acidanthera/BrcmPatchRAM |
| FP READER | Internal | Nope  ❌| Disabled via custom usb mapping |
| COLOR CALIBRATOR | Internal | Nope  ❌ | Disabled via custom usb mapping |
| EXPRESS CARD | Internal | Nope  ❌ | Will never work; disabled in UEFI setup. |
| SD READER | Realtek RTS525A | Nope ❌ | There are drivers in progress, but they are to be not stable as per https://github.com/midi1996/P50-opencore-hackintosh |
| Video Output| HDMI 1.4b and mini DP1.2a | Nope ❌ | Since Nvidia is disabled, these ports connected to it can't work. To get external monitor, you might need an eGPU with AMD GPU, and using the method mentioned in https://github.com/AsahiKou/ThinkPadP51-Hackintosh-Catalina/issues/1. You will need to plug the eGPU to TB port BEFORE booting and add the `agdpmod=pikera` boot flag.

