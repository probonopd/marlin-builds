# marlin-builds

Builds Marlin 2.x firmware for various 3D printers with customizations. The directory structure in `customization/configuration/` matches the directory structure in [Marlin Configurations](https://github.com/MarlinFirmware/Configurations/tree/import-2.1.x/config/examples) but instead of storing whole configurations, we are doing incremental configuration changes using `opt_enable`, `opt_disable`, and `opt_set`. This way we will benefit from changes in upstream configurations.

This contains my customizations. You may want to clone this repository and do your own, since my customizations may not be suitable for your machines.

## Flashing Ender-2 with USBASP

Ender-2

My Ender-2 has no USB socket on its PCB, hence I need to flash it using an USBASP. Yours may be different.

* Connect USBASP to 6-pin header, DO NOT connect VCC from the USBASP to the printer. Have the printer powered by its PSU
* Backup the original firmware with `sudo avrdude -p atmega1284p -c usbasp -F -U flash:r:factory.hex:i`.
* Flash this firmware with `sudo avrdude -p m1284p -c usbasp -F -U flash:w:'/home/me/Downloads/Marlin.ino.hex':i`. A bootloader is not needed!
