
# ✅ How to Install a GSI on Samsung Galaxy A80 (SM-A805F)
### ⚙️ No Fastboot | With Odin, TWRP, and GSI | Verified Working

---

## 📦 Requirements

- **TWRP** (touchscreen fixed version) `.tar` [Download](https://github.com/tuttizpro218/Samsung-Galaxy-A80-GSI/releases/tag/Main)
- **GSI ROM** (`LineageOS-23.0-20251027-GAPPS-EXT4-GSI.img`) [LIST](https://github.com/TrebleDroid/treble_experimentations/wiki/Generic-System-Image-%28GSI%29-list) [I used this](https://github.com/MisterZtr/LineageOS_gsi/releases/tag/v2025.10.27-lineage23.0)
- **vbmeta.img** (from GSI or patched manually)
- **Odin3** (on Windows)
- **ADB + Platform Tools** (Linux/Windows)
- **USB cable + PC (Linux & Windows access)**

---

## 🛠️ Step-by-Step Instructions

### 1️⃣ Flash TWRP via [Odin3 |Windows only](https://odindownload.com)

- Boot your phone to **Download Mode** (Powered off state)
- **Hold Volume Down + Up and plug the usb cable into the phone, then press Volume Up again**
- **(WARNING!!!! YOU NEED TO ENABLE OEM UNLOCK AND USB DEBUGGING!!!!!!)**
- Open **Odin3**
- Load the **recovery.tar** into the **AP** slot
- **Uncheck "Auto Reboot"** in Options
- Click **Start**
- When done, manually boot to TWRP:  
  → Press & hold **Vol down + Power** while unplugging USB
  → After the screen went black  Press & hold **Vol Up + Power** and release the buttons if you se the SAMSUNG Logo
- TWRP should boot with working touchscreen
- Next step is Wipe Partitions via ADB or TWRP Terminal
- After this Flash `vbmeta.img` via Odin

### 1️⃣ Flash TWRP via [Odin4 |Linux only!|](https://github.com/Adrilaw/OdinV4) 
- Boot your phone to **Download Mode** (Powered off state)
- **Hold Volume Down + Up and plug the usb cable into the phone, then press Volume Up again**
- **(WARNING!!!! YOU NEED TO ENABLE OEM UNLOCK AND USB DEBUGGING!!!!!!)**
- Open Terminal, navigate your terminal to odin4

```sh
(sudo chmod +x odin4 this gives you premission to use the program)
./odin4 -a recovery.tar (!! YOU NEED TO PAY ATTENTION TO THIS CUZ ON LINUX THERE IS NO UNCHECK AUTO REBOOT!!, after the flash was finished, instantly hold Volume Up + Power, it's should boot into twrp)
```

---

### 2️⃣ Wipe Partitions via ADB or TWRP Terminal
From TWRP → Advanced → Terminal  

or via `adb shell`:

```sh
umount /data
umount /dev/block/by-name/userdata
umount /cache
rm -rf /data/dalvik-cache
rm -rf /cache/dalvik-cache
rm -rf /cache/*
mke2fs -t ext4 /dev/block/by-name/userdata
mke2fs -t ext4 /dev/block/by-name/cache
```

---

### 4️⃣ Flash the GSI via ADB Terminal
From TWRP → Advanced → Terminal  

or via `adb shell`:

```sh
adb shell "dd of=/dev/block/sda23 bs=4096" < LineageOS-23.0-20251027-GAPPS-EXT4-GSI.img

```

### 5️⃣ Flash `vbmeta.img` via Odin

- Back to Download Mode

- Transfer to Windows
- Load `vbmeta.tar` into **AP** in Odin
- **Uncheck Auto Reboot**
- Click **Start**
- After "PASS", manually reboot to **TWRP** again  
  (Vol Up + Power)

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
