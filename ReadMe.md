
# ✅ How to Install a GSI on Samsung Galaxy A80 (SM-A805F)
### ⚙️ No Fastboot | With Odin, TWRP, and GSI | Verified Working
### ⚙️ ATTENTION FLASH ATTEMPT WAS THIS: Google GSI (Beta 1) (DO NOT ATTEMPT)

---

## 📦 Requirements

- **TWRP** (touchscreen fixed version) `.tar` [Zip](https://drive.google.com/file/d/1F5k4Kf-Mur5cgJOaHGBoIhAz5V4a6P_f/view)
- **GSI ROM** (`system.img`) [LIST](https://github.com/TrebleDroid/treble_experimentations/wiki/Generic-System-Image-%28GSI%29-list)
- **vbmeta.img** (from GSI or patched manually)
- **Odin3** (on Windows)
- **ADB + Platform Tools** (Linux/Windows)
- **USB cable + PC (Linux & Windows access)**

---

## 🛠️ Step-by-Step Instructions

### 1️⃣ Flash TWRP via Odin

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

---

### 2️⃣ Wipe Partitions via TWRP

From TWRP UI:

- Go to **Wipe → Advanced Wipe**
- Select:
  - ✅ Dalvik / ART Cache
  - ✅ Cache
- Swipe to Wipe
  
---

### 3️⃣ Reformat `/data` via Shell

From TWRP → Advanced → Terminal  
or via `adb shell`:

```sh
umount /data
umount /dev/block/by-name/userdata
mke2fs -t ext4 /dev/block/by-name/userdata
```

---

### 4️⃣ Flash the GSI

Back in TWRP:

- Go to **Install**
- Tap “Install Image”
- Choose `system.img`
- Select **System Image** → Swipe to flash

---

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
