# TinyWATCH S3 Pre Built Alpha Firmware
This is the latest development version of the TinyWATCH S3 firmware - This wil eventually be available via a web flashing tool, but for now to put updates on your TinyWATCH, you'll need to flash it with `esptool`. 

Change `{port}` to reference the serial port presented by TinyWATCH on your OS. On macOS it might look like `/dev/cu.usbmodem83401` 

You should really erase the flash before putting on new firmware, but this is optional.
```
esptool.py --chip esp32s3 --port {port} erase_flash
```

Flash the firmware on your TinyWATCH

```
esptool.py --chip esp32s3 --port {port} write_flash -z 0x0000 bootloader.bin 0x8000 partitions.bin 0xe000 ota.bin 0x10000 firmware.bin
```

Each OS has `esptool` installed differently. On Windows you might need to call `esptool.exe` etc. Please adjust your command above to suit your OS.

### Change list
Dec 15, 2023
- Fixed IMU interrupt not being set for step counting
