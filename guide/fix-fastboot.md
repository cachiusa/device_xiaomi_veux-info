# Fix stuck in bootloader mode (screen showing `FASTBOOT`) (veux only)

You need a PC to fix this. Make sure it has [the latest](https://developer.android.com/tools/releases/platform-tools) `fastboot` and `adb` installed

Your bootloader must be unlocked. If it is locked, you're done for.

Try each of these, from top to bottom:

## 1 - Run `fastboot reboot`
If this didn't fix, try (2)

## 2 - Reset active slot
1. Get your current slot
```
fastboot getvar active-slot
```
2. Run this command. Replace `<active-slot>` with your current slot name
```
fastboot set_active <active-slot>
fastboot reboot
```
If this didn't fix, try (3)

## 3 - Install Lineage Recovery
1. Download [LineageOS Recovery](https://sourceforge.net/projects/recovery-veux/files/lineage-recovery-20250112-veux.zip/download) & extract the package.
2. Flash the provided boot.img AND vendor_boot.img AND dtbo.img
```
fastboot flash dtbo dtbo.img
fastboot flash boot boot.img
fastboot flash vendor_boot vendor_boot.img
fastboot reboot recovery
```
3. Re-flash your current ROM (do not format data)
4. Reboot system now

If this didn't fix, try (4)

## 4 - Restore to MIUI/HyperOS
1. Download latest [MIUI/HyperOS](https://xmfirmwareupdater.com/hyperos/veux/) (fastboot variant) & extract the package.
2. Run `flash_all.bat` or `flash_all.sh` (do not run the `lock` script)
    - YOU WILL LOSE ALL DATA

## If (4) didn't work
Congratulations, your phone is bricked.