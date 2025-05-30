# recovery partition
veux/peux does not have dedicated `recovery` partition

The actual recovery resides in either `boot` or `vendor_boot` partition, depending on your current ROM.

Do not try to `fastboot boot recovery.img`, it will not work.

Do not try to install a custom recovery with one of these commands

```
fastboot flash boot boot.img
# or this one
fastboot flash vendor_boot boot.img
```

because you are not only replacing the recovery but also critical kernel components, and you will face:
- stuck in fastboot/bootloader mode
- bootloop
- broken drivers (modem, wi-fi, bluetooth...)

However, you can flash a valid combination of `boot` AND `vendor_boot` AND `dtbo` partitions, like this:
```
fastboot flash boot boot.img
fastboot flash vendor_boot vendor_boot.img
fastboot flash dtbo dtbo.img
```