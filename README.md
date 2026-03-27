# Matebook-D15-2020-Hackintosh

Huawei Matebook D15 2020 (BOHK-WAX9X) Hackintosh EFI 💻

### This repository contains an OpenCore-based EFI folder for Honor MagicBook 15 / Huawei MateBook D15 (AMD Ryzen 3500U). This configuration is optimized for daily use but has specific nuances due to the AMD mobile platform.

## 💻 Hardware Specs

CPU: AMD Ryzen 5 3500U (with Radeon Vega 8 Graphics)

GPU: AMD Radeon Vega 8 (NootedRed)

Audio: Realtek ALC (Speaker, Mic & Jack working)

Keyboard/Trackpad: I2C HID (Full Gestures)

## 📡 Networking & Continuity (Intel AX210)

I replaced the stock Realtek card with an Intel AX210. While Wi-Fi and Bluetooth are stable, Apple's Continuity features work only partially:

[x] Universal Clipboard: Copy on iPhone, paste on Mac (and vice versa) works perfectly.

[x] Handoff: Switching Safari/Chrome tabs or apps from iPhone to Mac works.

[x] Location Services: Fully working (Maps, Find My, Night Shift).

[ ] AirDrop: Devices are visible, but file transfer fails.

[ ] Instant Hotspot: Does not activate automatically from the Wi-Fi menu; you must enable it manually on the iPhone.

[ ] Continuity Camera & Mic: iPhone is detected by the system, but video/audio stream does not work.

[ ] Continuity Sketch/Markup: Taking a photo or scanning a document from iPhone into Notes/Finder is not working.

# 💾 Storage & NVMe 
The stock Samsung PM981 SSD is natively incompatible with macOS. This EFI includes a [workaround](https://github.com/tylernguyen/x1c6-hackintosh/issues/43):

Integrated Fixes: Features NVMeFix.kext and a SSDT-NVMe to stabilize the controller.

BIOS ID Customization: Depending on your firmware, you may need to update the Hardware ID / ACPI Path in the provided SSDT-NVMe.aml to match your specific system.

Recommendation: Swapping to a compatible SSD (e.g., WD Blue/Black) is still highly recommended to avoid Kernel Panics.

## ✅ What's Working

Graphics Acceleration.

Audio: Internal speakers, Microphone, and 3.5mm Jack are fully functional.

Input: Keyboard and Trackpad (all multi-touch gestures work).

Battery: Proper status reporting and percentage.

USB Ports: All ports mapped correctly.

## ⚠️ Known Issues & Fixes
Wallpapers: Use static images only. Dynamic wallpapers on Sonoma and higher will crash the system (NootedRed issue).

Sleep/Wake: 100% stable on macOS Ventura. On Sonoma/Sequoia, occasional crashes may occur during deep sleep.

Webcam: Detected as a USB device but does not output video.

Fingerprint Sensor: Will never work on macOS.

iCloud Sync Issue:
On macOS Sonoma (and likely Sequoia/Tahoe), the system crashes during iCloud synchronization, I gonna try fix it asap.

You can sign in to your Apple ID, but enabling iCloud Drive or Photos sync will lead to a system freeze or kernel panic.
For full iCloud stability, macOS Ventura is recommended.

## 🛠 Installation Instructions
1. Generate Serial Numbers

IMPORTANT: This EFI does not contain a serial number. To use iCloud/iMessage, you MUST generate your own:

The used SMBios was MacbookPro16,3. Heres how to do it: https://www.youtube.com/watch?v=8MsueH5EouQ.

2. BIOS Settings
Disable: Secure Boot, Fast Boot, TPM.
