# Fix stuck in bootloader mode (screen showing `FASTBOOT`) (veux only)

You need a PC to fix this. Make sure it has [the latest](https://developer.android.com/tools/releases/platform-tools) `fastboot` and `adb` installed

Your bootloader must be unlocked. If it is locked, you're done for.

Try each of these, from top to bottom:

## 1 - Run `fastboot reboot`
## 2 - If (1) didn't work
1. Get your current slot: `fastboot getvar active-slot`
2. Reset to that slot. If your current slot is `b`, replace `a` with `b`
```
fastboot set_active a
```
3.  `fastboot reboot`
## 3 - If (2) didn't work
1. Download [LineageOS Recovery](https://sourceforge.net/projects/recovery-veux/files/lineage-recovery-20250112-veux.zip/download) & extract the package.
2. Flash the provided boot.img AND vendor_boot.img AND dtbo.img
```
fastboot flash dtbo_a dtbo.img
fastboot flash dtbo_b dtbo.img
fastboot flash boot_a boot.img
fastboot flash boot_b boot.img
fastboot flash vendor_boot_a vendor_boot.img
fastboot flash vendor_boot_b vendor_boot.img
```
3. `fastboot reboot recovery`
4. Re-flash your current ROM (do not format data)
5. Reboot system now
## 4 - If (3) didn't work
1. Download latest [MIUI/HyperOS](https://xmfirmwareupdater.com/hyperos/veux/) (fastboot variant) & extract the package.
2. Run `flash_all.bat` or `flash_all.sh` (do not run the `lock` script)
	- YOU WILL LOSE ALL DATA
## 5 - If (4) didn't work
Congratulations, your phone is bricked.