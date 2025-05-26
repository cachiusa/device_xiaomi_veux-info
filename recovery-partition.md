# recovery partition
veux/peux does not have dedicated `recovery` partition. The actual recovery resides in either `boot` or `vendor_boot` partition, depending on your current ROM.

Do not try to `fastboot boot recovery.img`, it will not work.

Do not try to install a custom recovery with `fastboot flash`, unless you flash a valid combination of `boot` AND `vendor_boot` AND `dtbo` partitions.