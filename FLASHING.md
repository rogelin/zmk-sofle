# Flashing Sofle Eyelash (ZMK / Nice!Nano)

This guide explains how to flash the GitHub Actions artifacts onto a Sofle Eyelash split wireless keyboard.

---

## Artifacts

Typical build artifacts:

| File | Purpose |
|------|--------|
| `eyelash_sofle_studio_left.uf2` | **Main firmware – LEFT (central)** |
| `nice_view-eyelash_sofle_right-zmk.uf2` | **Main firmware – RIGHT (peripheral)** |
| `settings_reset-eyelash_sofle_left-zmk.uf2` | **Settings reset – can be flashed to **either** half to clear Bluetooth pairings** |

> ⚠️ Use the **settings_reset** UF2 if you have connection problems or if the right half shows connected but no keys work.  
> It is labeled “left,” but it is safe to flash it to **either** side.

---

## Flashing Steps

### 1. Left Half
1. Connect the **left** half to your computer via USB-C.
2. Double-tap the Nice!Nano **reset** button – a drive named `NICENANO` will appear.
3. Drag `eyelash_sofle_studio_left.uf2` onto the drive and wait for it to reboot.

### 2. Right Half
1. Connect the **right** half via USB-C.
2. Double-tap reset to mount `NICENANO`.
3. (Optional but recommended if bonding issues)  
   Drag **`settings_reset-eyelash_sofle_left-zmk.uf2`** onto the drive and allow it to reboot.
4. Re-enter bootloader (double-tap reset again).
5. Drag `nice_view-eyelash_sofle_right-zmk.uf2` onto the drive and wait for it to reboot.

### 3. Pairing
1. Turn on both halves (battery switches on).
2. Pair the **left** half to your computer/phone as a normal Bluetooth keyboard.
3. The left half will automatically scan for and connect to the right half.  
   Keep them close together for the first bonding.

---

## Troubleshooting

| Symptom | Likely Cause | Fix |
|---------|--------------|----|
| Right shows connected but no keys register | Old bond data or wrong firmware | Flash **settings_reset** on the **right**, then reflash the right UF2. |
| Board not detected as NICENANO | Cable is charge-only or bootloader not entered | Use a data-capable cable and double-tap reset. |
| Only one UF2 produced | GitHub Action not building both shields | Ensure both `eyelash_sofle_left` and `eyelash_sofle_right` targets are listed in the build matrix. |

---

Once flashed and paired, the halves will automatically reconnect every time they are powered on.
