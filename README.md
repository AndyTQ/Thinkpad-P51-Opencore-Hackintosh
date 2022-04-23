# This read me file is work in progress
# Thinkpad-P51-Opencore-Hackintosh

Last updated: 2022.4.22

**Disclaimer
This guide is only for educational purpose. By following this guide, you agree to take full responsibility for any damage to your system and any other things that comes out from the guide.**

## Platform Specifications
https://psref.lenovo.com/syspool/Sys/PDF/ThinkPad/ThinkPad_P51/ThinkPad_P51_Spec.PDF

## Tested Hardware
| Category | Element | Compatibility | Notes |
| ------------- | ------------- | ------------- | ------------- | 
| CPU | i7-7700HQ | Working✅ | Power management works correctly.
| GPU | HD630 | Working✅ | See additional comment #1. Need additional config in EFI\OC\config.plist.
| | NVIDIA M1200 | Nope ❌ | Will never work as there are no driver support since MacOS 10.14. |
| MEMORY | 1x16GB | Working✅ | |
| DISPLAY | 1440P @ 165 | Working✅ | Requires a combination of `SwitchResX` and `RDM`. See additional comment #2.|
| STORAGE | Samsung 970 Evo 1TB | Working✅| |
| ETHERNET | Intel I219-V | Working✅ | |
| WLAN | BCM94352Z | Working✅ |  |
| CAMERA | | Working✅ | Requires custom USBMap.kext. See https://github.com/corpnewt/USBMap |
| AUDIO | ALC3268 | Working✅ | AppleALC.kect + Layout #3 as per https://dortania.github.io/OpenCore-Post-Install/universal/audio.html#finding-your-layout-id|
| PORTS | 4xUSB3.1 Gen 1 (3.0) |  Working✅ | Requires custom USBMap.kext. See https://github.com/corpnewt/USBMap|
| KEYBOARD | Non backlit keyboard | Working✅ | I don't have a backlit keyboard (used to have one but that got damaged by a bottle of water. the newly replaced one doesn't have backlight.) |
| ULTRANAV | Trackpoint | Partially working ⚠️ | Thr |
| | Touchpad | Partially working ⚠️  | See if it is possible to add more gestures |
| | Dock | Untested ⚠️| Theoretically possible as per https://github.com/MirkoCovizzi/thinkpad-p51-hackintosh |
| | 1xUSB C (Thunderbolt) | Untested ⚠️ | Theoretically possible for eGPU output since it worked in 10.15 as per https://github.com/AsahiKou/ThinkPadP51-Hackintosh-Catalina/issues/1. Untested for other TB3 devices.|
| BLUETOOTH | BCM94352Z | Nope, but work in progress ❌| There are some issues with Broadcome-related kexts in Monterey, but it is theoretically possible to coninue using BCM94352Z via BlueToolFixup. See https://github.com/acidanthera/BrcmPatchRAM |
| FP READER | | Nope  ❌| Disabled via custom usb mapping |
| COLOR CALIBRATOR | | Nope  ❌ | Disabled via custom usb mapping |
| EXPRESS CARD | - | Nope  ❌ | Will never work; disabled in UEFI setup. |
| SD READER | Realtek RTS525A | Nope ❌ | There are drivers in progress, but they are to be not stable as per https://github.com/midi1996/P50-opencore-hackintosh |
| | HDMI and DP | Nope ❌ | Since Nvidia is disabled, these ports connected to it can't work. To get external monitor, you might need an eGPU with AMD GPU, and using the method mentioned in https://github.com/AsahiKou/ThinkPadP51-Hackintosh-Catalina/issues/1. You will need to plug the eGPU to TB port BEFORE booting and add the `agdpmod=pikera` boot flag.

