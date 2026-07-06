# Honor MagicBook X14 Hackintosh - macOS Tahoe (v26)

This repository contains the OpenCore EFI configuration required to run macOS Tahoe (v26) on the **Honor MagicBook X14** laptop. Fully optimized for daily tasks with Comet Lake hardware.

---

## 💻 Hardware Specifications

| Component | Detail |
| :--- | :--- |
| **Device** | Honor MagicBook X14 |
| **CPU** | Intel Core i5-10210U @ 1.60GHz (Comet Lake) |
| **iGPU** | Intel UHD Graphics 620 |
| **RAM** | 8 GB DDR4 |
| **Storage** | 512 GB NVMe SSD |
| **Audio** | Realtek ALC / Intel High Definition Audio |
| **Wi-Fi & BT** | Intel Wireless-AC 9560 (160MHz) |

---

## 🛠️ Status (What's Working / What's Not)

### ✅ Working
* **Graphics Acceleration** (Intel UHD 620 with full QE/CI)
* **Wi-Fi & Internet** 
* **Bluetooth**
* **Battery Management** (Percentage status and charging cycle display)
* **USB Ports** (Mapped correctly)
* **Keyboard & Trackpad** (Multi-touch gestures support)
* **Audio** (Speakers and Microphone Array)

### ⚠️ Known Issues & Workarounds
* **Webcam:** Currently not working.
* **Sleep Mode:** Sleep/Wake mechanism is unstable. The laptop occasionally struggles to wake up properly.
* **Slow Boot:** During the initial boot, a black screen may persist for about 2-3 minutes before the Apple logo or login screen appears. Please be patient, it will eventually boot.

---

## ⚙️ BIOS Settings

Before proceeding with the installation, you **must** configure your BIOS settings properly to avoid kernel panics.

* **Secure Boot:** `Disabled`
* **SATA Mode:** `AHCI`

---

## 🔧 Essential Tools (Highly Recommended)

To manage, update, or customize this EFI, using these specific tools is strongly advised:
1. **OCAuxiliaryTools (OCAT):** The absolute best tool for keeping OpenCore, Kexts, and your `config.plist` up to date without breaking the structure.
2. **USBMap / USBMapper:** Essential for maintaining clean USB port mapping, ensuring better battery life, and preventing sleep issues on your specific laptop layout.

---

## 🚀 Installation Steps & Pre-Installation Hint

### 💡 Pre-Installation Optimization (Crucial)
To prevent installation loops and ensure a smooth setup process, **it is highly recommended to temporarily disable the Wi-Fi and Bluetooth kexts in the EFI (`config.plist`) before booting the installer.** Do not connect to any network during the initial macOS setup phases. Once you reach the desktop successfully, you can re-enable them.

### Step-by-Step:
1. **Prepare the USB installer:** Create a vanilla macOS Tahoe bootable USB drive.
2. **Clone the EFI:** Download this repository, rename the folder to `EFI` and place it into the root of your USB drive's EFI partition.
3. **Disable Networking Kexts:** Use OCAuxiliaryTools to open `config.plist`, go to the Kernel section, and temporarily disable the Intel Wi-Fi and Bluetooth kexts for the first install.
4. **Configure GenSMBIOS:** Generate a unique serial number, Board Serial, and SmUUID using `MacBookPro16,4` (Comet Lake) SMBIOS profile. Inject these into the `config.plist`.
5. **Boot:** Plug the USB into your MagicBook X14, boot into the boot manager, select the OpenCore drive, and start the installation.
   * *Reminder: Remember that you might face a 2-3 minute black screen on boots. Do not force shutdown your laptop.*
