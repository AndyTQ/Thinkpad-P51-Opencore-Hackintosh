# Thinkpad-P51-Opencore-Hackintosh
- 2022.4.25 Update #2: Fix VoodooRMI (for trackpad & trackpoint). Now trackpad and trackpoint are much smoother to use. Added Bluetooth Support via Bluetoothfixup.kext
- 2022.4.22 Update #1: Initial Upload
- Current tested macOS version: **Monterey 12.3.1**
- Current tested OpenCore version: **0.8.0**
- Deeply appreciate the guide from https://github.com/midi1996/P50-opencore-hackintosh/ and Dortania, and the posts on /r/Hackintosh Reddit!
- **The EFI folder is modified to fit the specs below. It may not work on your machine, and make sure that you forllow Dortania's hackintosh guide if you wanna make your own EFI folder.**
- **Disclaimer: Use this configuration on your own risk as I am not responsibile for damaging anyone's system.**

## Platform Specifications
https://psref.lenovo.com/syspool/Sys/PDF/ThinkPad/ThinkPad_P51/ThinkPad_P51_Spec.PDF

## Tested Specs

- CPU: i7-7700HQ (4 cores, 8 threads)
- GPU: HD630 (Max VRAM: 2GB)
- RAM: 32GB DDR4 (4 * 8GB @ 2400Hz)
- Motherboard/Laptop Make and Model: Lenovo Thinkpad P51 20HH 
- Display: 2560 x 1440 @ 165Hz, scaled to 1600 x 900 @ HiDPI & 144Hz (panel#: N156KME-GNA). Originally the machine comes with a 4K screen. I swapped the screen out and replaced with one that has high refresh-rate. 
- Audio Codec: ALC298 (ALC3268)
- Ethernet Card: Intel I219-V
- Wifi/BT Card: BCM94352Z
- Touchpad and touch display devices: Symaptics touchpad
- BIOS revision: 1.57

## List of hardwares and their compatibilities
| Category | Element | Compatibility | Notes |
| ------------- | ------------- | ------------- | ------------- | 
| CPU | i7-7700HQ | Working✅ | Power management works correctly.
| GPU | HD630 | Working✅ | Need additional config in EFI\OC\config.plist. (more on that in the future)
| | NVIDIA M1200 | Nope ❌ | Will never work as there are no driver support since MacOS 10.14. |
| MEMORY | 1x16GB | Working✅ | |
| DISPLAY | 1440P @ 144Hz, scaled to "looks like" 1600x900 | Working✅ | Can't get to 165Hz due to limited pixelclock for HD630 (even with maximum pixelclock override). Requires a combination of `SwitchResX` and `RDM`. Requires additional config in EFI\OC\config.plist. (more on that in the future) But 165 and 144Hz are kinda difficult to distinguish tho.|
| STORAGE | Samsung 970 Evo 1TB | Working✅| |
| ETHERNET | Intel I219-V | Working✅ | |
| WLAN | BCM94360CS2 | Working✅ |  |
| BLUETOOTH | BCM94360CS2 | Working✅ | Need BluetoothFixup.kext for Monterey+. Airdrop can only receive but cannot send somehow. |
| CAMERA | Internal | Working✅ | Requires custom USBMap.kext. See https://github.com/corpnewt/USBMap |
| AUDIO | ALC3268 | Working✅ | AppleALC.kect + Layout #3 as per https://dortania.github.io/OpenCore-Post-Install/universal/audio.html#finding-your-layout-id|
| PORTS | 4xUSB3.1 Gen 1 (3.0) |  Working✅ | Requires custom USBMap.kext. See https://github.com/corpnewt/USBMap|
| KEYBOARD | Non backlit keyboard | Working✅ | I don't have a backlit keyboard (used to have one but that got damaged by a bottle of water. the newly replaced one doesn't have backlight.) |
| Trackpad | Synaptics | Working✅| Used the VoodooRMI kext, which is ported fromm the Linux RMI driver. More responsive than using VoodooPS2Controller.kext! |
| Trackpoint | Synaptics | Working✅| Used the VoodooRMI kext, which is ported fromm the Linux RMI driver. More responsive and less buggy than using VoodooPS2Controller.kext! |
| Video Output| HDMI 1.4b and mini DP1.2a, or eGPU via TB3 | Partially working (will never fully work) ⚠️ | Since Nvidia is disabled, **HDMI and DP don't work** as they are directly connected to nvidia GPU. It's impossible to get video output directly via TB3 either. However, it is still possible to get external monitor by using an eGPU with AMD GPU, and use the method mentioned in https://github.com/AsahiKou/ThinkPadP51-Hackintosh-Catalina/issues/1. You will need to plug the eGPU to TB port BEFORE booting and add the `agdpmod=pikera` boot flag for some AMD GPUs. Keep in mind that this method would be very expensive.
| SD READER | Realtek RTS525A | In Progress ⚠️ | There are newer drivers now available and I will try them out. |
| Dock | | Untested ❓| Theoretically possible as per https://github.com/MirkoCovizzi/thinkpad-p51-hackintosh |
| 1xUSB C (Thunderbolt) | | Partially working ⚠️| Impossible to hot plug. You need to plug in before booting to make it work. Theoretically possible for eGPU output since it worked in 10.15 as per https://github.com/AsahiKou/ThinkPadP51-Hackintosh-Catalina/issues/1. Untested for other TB3 devices.|
| FP READER | Internal | Nope  ❌| Disabled via custom usb mapping. I don't use them anyway |
| COLOR CALIBRATOR | Internal | Nope  ❌ | Disabled via custom usb mapping. I don't use them anyway |
| EXPRESS CARD | Internal | Nope  ❌ | Will never work; disabled in UEFI setup. I don't use them anyway | 
