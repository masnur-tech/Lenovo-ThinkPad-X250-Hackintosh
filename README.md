Personal portfolio and technical configuration documentation.
# Lenovo-ThinkPad-X250-Hackintosh

<img width="698" height="463" alt="Screen Shot 2026-05-24 at 23 47 04" src="https://github.com/user-attachments/assets/d1fa160e-7774-4b97-b746-7fda2f94b01f" />

OpenCore configuration for Lenovo ThinkPad X250 running macOS Monterey 12.7.6.

## Hardware Specifications

| Component | Specification | Status |
| :--- | :--- | :--- |
| **CPU** | Intel Core i5-4300U (Haswell) | Working |
| **RAM** | 8 GB DDR3 | Working |
| **Storage** | 128 GB SSD | Working |
| **Graphics** | Intel HD Graphics 4400 | Working (with patch) |
| **Audio** | Realtek ALC292 | Working (layout-id 28) |
| **Wi-Fi/BT** | Supported Card | Working |
| **SMBIOS** | MacBookPro11,4 | Configured |
| **Bootloader**| OpenCore v1.0.4 | Active |

## What is Working

- [x] UEFI booting via OpenCore
- [x] Intel HD Graphics 4400 QE/CI Acceleration
- [x] Audio and headphone jack
- [x] Internal microphone
- [x] Battery Management and Indicator
- [x] Wi-Fi and Bluetooth
- [x] Trackpad, Trackpoint, and Keyboard shortcuts
- [x] USB Ports
- [x] Sleep and Wake

## Configuration Details

- **Bootloader Version:** OpenCore 1.0.4
- **Target OS:** macOS Monterey 12.7.6
- **SMBIOS Target:** MacBookPro11,4

## Post-Installation Notes

1. **SMBIOS Generation:** You **must** generate your own unique Serial Number, UUID, and MLB using GenSMBIOS before using this EFI.
2. **Kexts:** All essential kexts (VirtualSMC, Lilu, WhateverGreen, AppleALC) are included.
