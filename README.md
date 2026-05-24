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
| **Audio** | Realtek ALC292 | Working (layout-id 59) |
| **Wi-Fi/BT** | Intel Dual Band Wireless-AC 7265 | Working (via AirportItlwm & IntelBTHandshake) |
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

## Pre-Installation (BIOS Settings)

Before booting the macOS installer, you must configure your ThinkPad X250 BIOS settings properly. 

Restart your laptop, press **F1** to enter BIOS, and set the following options:

### Security
- **Security Chip:** Disabled
- **Memory Protection -> Execution Prevention:** Enabled
- **Secure Boot:** Disabled

### Startup
- **UEFI/Legacy Boot:** UEFI Only
- **CSM Support:** Enabled

### Config
- **Serial ATA (SATA) -> Controller Mode:** AHCI
- **CPU -> Intel Virtualization Technology:** Enabled
- **CPU -> Intel VT-d:** Disabled (or keep enabled if `DisableIoMapper` quirk is on)

---

## Installation Process

Follow these steps to deploy this EFI configuration:

1. **Format USB Drive:** Format your 16GB+ USB flash drive as GUID Partition Table (GPT).
2. **Create macOS Installer:** Go to the official [Olarila Vanilla Images Archive](https://olarila.com/) to download the macOS Monterey `.raw` image. Once downloaded, flash it to your USB drive using one of these tools:
   * **Method A (BalenaEtcher):** Open BalenaEtcher, click *Flash from file* to select your Olarila macOS image, click *Select target* to choose your USB drive, and then click *Flash!*.
   * **Method B (Win32 Disk Imager):** Open Win32 Disk Imager, click the folder icon to select your Olarila `.raw` file (make sure to change the file type filter to `*.*` to see it), select your USB drive letter under *Device*, and click *Write*.
3. **Mount EFI Partition:** Use a tool like MiniTool Partition Wizard (on Windows) or MountEFI (on macOS) to mount the hidden EFI partition of your flashed USB drive.
4. **Copy EFI Folder:** Extract and copy the **EFI** folder (containing `BOOT` and `OC`) from this repository into the root directory of your USB's EFI partition.
5. **Boot Installer:** Insert the USB into your ThinkPad X250, press **F12** during boot, select your USB drive, and choose *Install macOS Monterey*.
6. **Post-Install:** Once macOS is installed on your SSD, mount your SSD's EFI partition and copy this EFI folder there so you can boot without the USB drive.

## Post-Installation Notes

1. **SMBIOS Generation:** You **must** generate your own unique Serial Number, UUID, and MLB using GenSMBIOS before using this EFI.
2. **Kexts:** All essential kexts (VirtualSMC, Lilu, WhateverGreen, AppleALC) are included.

## 💾 Download EFI

You can download the full, pre-configured EFI folder for Lenovo ThinkPad X250 from the link below:

👉 **[Download EFI via Google Drive](https://drive.google.com/file/d/1008cHBuX7N5xM4R2Jk5PmqnkRa9n-kNJ/view?usp=drive_link)**

*Note: This EFI is updated to OpenCore v1.0.4 and optimized for macOS Monterey 12.7.6.*

## 🏅 Credits & Acknowledgments

Special thanks to the amazing open-source community and developers:

- **Apple** for macOS.
- **Acidanthera** for OpenCore Bootloader and essential kexts (Lilu, WhateverGreen, AppleALC, VirtualSMC).
- **Dortania** for the comprehensive OpenCore Install Guide.
- **Sniki** for the inspirational ThinkPad Hackintosh repository layout.
- **RehabMan** for legacy ACPI patches and contributions to the ThinkPad community.
