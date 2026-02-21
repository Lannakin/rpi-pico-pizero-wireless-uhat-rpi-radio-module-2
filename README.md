# **wireless-uhat-tht-rpi-radio-module-2 - Design Notes**

## **CREDITS FOR FONTS**

[WebPlus_ToshibaSat_8x14 and WebPlus_ToshibaSat_9x16 by VileR](https://**int10h**.org/oldschool-pc-fonts/)
[scientifica © 2020 Akshay Oppiliappan (nerdy@peppe.rs)](https://github.com/oppiliappan/scientifica)

---

## **Overview**

This project is to adapt the Raspberry Pi Radio Module 2 (RM2) [(p/n RMC20452)](https://pip-assets.raspberrypi.com/categories/1216-raspberry-pi-radio-module-2/documents/RP-008943-DS-4-Radio%20Module%202%20Datasheet.pdf)
to the μHat specification, minus the EEPROM chip, as the RM2 is not compatible
with anything except the Raspberry Pi microcontrollers (RPIMCU).  The main
reason I am doing this is because I have an RP2350B A4 revision chip, which is
part of a Waveshare RP2350-PiZero board.  I wish I knew what the hell their
tables in the `40Pin OUT` section meant for sure.  Oh well, thank y'all for making
the schematic public.

**It should be noted that I am doing this as part of a hobby, and I am not any
kind of engineer.**

## **Schematic Notes**

- I've attempted to have PCB traces cross at 90° angles to help prevent / reduce
interference.

- I need to calculate how wide the traces and vias should be.

- I read or heard somewhere that it can be a good idea to basically have a
power rail border the board to prevent interference but I don't think I have
ever seen anyone do that.

## **Layout Considerations**

- Bottom layer is ground plane.

- Top layer is also a ground plane

- Top layer maybe should not be a ground plane.  I will look at the STMicro
Nucleo board design files and filch their secrets if they include the PCB design
files.

- The RM2 antenna has a big keep-out area.  I have positioned it roughly over
where the antenna on the Raspberry Pi Zero 2 W is located.  I hope it blocks the
HDMI / DVI connector, just to spite everyone.

  • Shit.  I just noticed the RP2350-PiZero has the stupid debug connector right
  under there.  22.3 mm from (top view) left edge of board to outside of DIO
  debug header insulation, 12.5 mm  from bottom edge of board to outside top of
  debug header insulation.

* The RM2 is now over the USB ports I guess

## **Component Notes**
<!-- Click on designators like R1, C5, U3 to highlight on PCB -->
- The RM2 is based on the CYW43439 and is made to share pins when used by the
RPIMCUs.

- Added LEDs for RM2 GPIO control.

- Considering adding a slot for debug port present on the RP2XX0-PiZero

## **Power Distribution**

Measuring traces on the W5500-EVB-Pico board as a reference.  Thanks Altium for
the online gerber viewer with a ruler.

| NET               | TRACE WIDTH       | CLEARANCE  |
|-------------------|-------------------|------------|
| 3V3DVC            | 0.8-0.9 mm        | 0.3 mm     |
| 5VDC VBUS VSYS    | 0.5 mm            | 0.3 mm     |
| GPIO              | 0.2 mm            | 0.2-0.3 mm |
| W5500             | 0.3 mm            | 0.2-0.3 mm |

## **References**

### DESIGN

[Pimoroni Pico Plus 2 W](https://cdn-shop.adafruit.com/product-files/6243/Pimoroni_Pico_Plus_2_W_Schematic.pdf)
[Raspberry Pi Pico 2 W](https://datasheets.raspberrypi.com/picow/pico-2-w-schematic.pdf)
[W5500-EVB-Pico](https://github.com/Wiznet/Hardware-Files-of-WIZnet/tree/master/02_iEthernet/W5500)
[Waveshare RP2350B-Plus-W](https://files.waveshare.com/wiki/RP2350B-Plus-W/RP2350B-Plus-W.pdf)

### PARTS

[Infineon CYW43439](https://www.mouser.com/datasheet/2/196/Infineon_CYW43439_DataSheet_v03_00_EN-3074791.pdf)
[RMC20452 aka Raspberry Pi Radio Module 2](https://pip-assets.raspberrypi.com/categories/1216-raspberry-pi-radio-module-2/documents/RP-008943-DS-4-Radio%20Module%202%20Datasheet.pdf)

---

### KiNotes - PCBtools.xyz
