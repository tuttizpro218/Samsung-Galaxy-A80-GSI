
# ✅ How to Install a GSI on Samsung Galaxy A80 (SM-A805F)
### ⚙️ No Fastboot | With Odin, TWRP, and GSI | Verified Working

---

## 📦 Requirements

- **TWRP** (touchscreen fixed version) `.tar` [Download](https://github.com/tuttizpro218/Samsung-Galaxy-A80-GSI/releases/tag/Main)
- **GSI ROM** (`LineageOS-23.0-20251027-GAPPS-EXT4-GSI.img`) [LIST](https://github.com/TrebleDroid/treble_experimentations/wiki/Generic-System-Image-%28GSI%29-list) [I used this](https://github.com/MisterZtr/LineageOS_gsi/releases/tag/v2025.10.27-lineage23.0)
- **vbmeta.img** (from GSI or patched manually) [Download](https://github.com/tuttizpro218/Samsung-Galaxy-A80-GSI/releases/tag/Main)
- **Odin4** [Download](https://github.com/Adrilaw/OdinV4/releases)
- **ADB + Platform Tools** (Linux/Windows)

---

## 🛠️ Step-by-Step Instructions

This tutorial is only for LINUX USERS!

### 1️⃣ Flash TWRP+VBMETA via Odin4
- Boot your phone to **Download Mode** (Powered off state)
- **Hold Volume Down + Up and plug the usb cable into the phone, then press Volume Up again**
- **(WARNING!!!! YOU NEED TO ENABLE OEM UNLOCK AND USB DEBUGGING!!!!!!)**
- Open Terminal, navigate your terminal to odin4

```sh
(sudo chmod +x odin4 this gives you premission to use the program)
./odin4 -a recovery.tar (!! YOU NEED TO PAY ATTENTION TO THIS CUZ ON LINUX THERE IS NO UNCHECK AUTO REBOOT!!, after the flash was finished, instantly hold Volume Up + Power, it's should boot into twrp)
```
- After your phone restarted **Hold Volume Down + Up, then press Volume Up again**
- Then flash the vbmeta.tar in the same way.

```sh
./odin4 -a vbmeta.tar (!! YOU NEED TO PAY ATTENTION TO THIS CUZ ON LINUX THERE IS NO UNCHECK AUTO REBOOT!!, after the flash was finished, instantly hold Volume Up + Power, it's should boot into twrp)
```

---

### 2️⃣ Flash the GSI via ADB Terminal
From TWRP → Advanced → Terminal  

or via `adb shell`:

```sh
adb shell "dd of=/dev/block/sda23 bs=4096" < LineageOS-23.0-20251027-GAPPS-EXT4-GSI.img

```
- If you are not sure about this part you can find the correct parttion like this:

```sh
mount | grep system
```

- Mine looks like this:
```sh
a71naxx:/ # mount | grep system
/dev/block/sda23 on /system_root type ext4 (ro,seclabel,relatime,block_validity,delalloc,barrier,user_xattr,acl,i_version)
a71naxx:/
```
---

###  3️⃣ Wipe Partitions via TWRP
From TWRP → Wipe → Format Data
- Type yes Format
- Swipe to Factory Reset

---

## 🔁 Boot System

If everything flashed correctly:

- From TWRP → Reboot → System
- First boot can take several minutes

---

## 🧨 Troubleshooting

- Try a different GSI variant (A/B or VNDK level) if bootloops
- Or restore stock firmware via Odin (Frija, SamFW, or SamMobile)

---

> Authored by @tuttizpro218 and @ChatGPT4-o — Simplified for fellow Galaxy A80 tweakers.
