
<p align="center">
  <img src="assets/logo.png" width="300">
</p>

# Pillz Mod for the Kinesis Advantage/Contoured

![PCB](https://i.imgur.com/TwBOiEr.jpeg)
![PillzMod](https://i.imgur.com/PJ1Fk2n.jpg)

This project replaces my two previous forks ([kinesismod](https://github.com/dcpedit/kinesismod) and [kint](https://github.com/dcpedit/kint)) for adding Blackpill support to the Kinesis keyboard.  I've decided to merge all the features into a single PCB, add optional thumb cluster PCBs as part of the kit, and renamed the project to avoid confusion.  Below is a list of supported features.

* Supports Blackpill development board running QMK/Vial
* Supports Pill Bug wireless Bluetooth development board running ZMK
* Optional reversible thumb cluster PCB for left/right sides.  (Maintains original matrix wiring)
* 2u stabilizer support on thumb cluster

## "Pro" PCB Features
* Supports devlopment board with Pro-Micro footprint (Elite-C, Elite-Pi, Nice!Nano)

Credit goes to the following people for doing all the initial development on replacment PCBs for the Kinesis:
 * Aaron Silman's [kinesismod project](https://gitlab.com/Silman/kinesismod.git) ([blog](https://silman.io/project/kinesis_mod/))
 * Michael Stapelberg's [KinT project](https://github.com/kinx-project/kint) ([blog](https://michael.stapelberg.ch/posts/2020-07-09-kint-kinesis-keyboard-controller/))
 * Dmitry Nosachev's [Kin80 project](https://github.com/DmNosachev/kin80)

## Ordering PCBs from JLCPCB

The files needed for https://jlcpcb.com are located in the production folders:
* `pcb/production`
* `thumb-pcb/production`

Once uploaded, you place the order with the selected default options.  You can optionally change the solder mask color, which changes the final color of your PCB.

## Main PCB build guide
### Components
| Position | Description | Qty | Notes |
| -------- | ----------- | --- | ----- |
| J1-J4    | Molex 39-53-2135 | 2 - 6  | [Link](https://octopart.com/39-53-2135-molex-7670149?r=sp)
| J3-J4    | Molex 39-53-2134 | 0 - 2  | Contoured only, [Link](https://octopart.com/search?q=Molex+39-53-2134)
| U1       | Header pins (1x20) | 2 | Should come with dev board
| U1       | Headers (1x20) | 2 | To socket your dev board
| D1-D4    | 1.8mm LED | 4 | [Amazon](https://a.co/d/90uynIs)
| R1-R4    | 10k resistor | 4 | Affects LED brightness. Smaller = brighter |
|          | USB-C panel mount | 1 | [AliExpress](https://www.aliexpress.us/item/3256806463941289.html?spm=a2g0o.order_list.order_list_main.43.18a31802pDYB6d&gatewayAdapt=glo2usa), [Amazon](https://a.co/d/cRoqHqx)

### Blackpill Components
| Position | Description | Qty | Notes |
| -------- | ----------- | --- | ----- |
| U1       | Blackpill (STM32F411) | 1 | [WeAct Store](https://www.aliexpress.com/store/1101545918?spm=a2g0o.order_list.order_list_main.2.18a31802pDYB6d)

#### -or- Pill Bug for wireless build

| Description | Qty | Notes |
| ----------- | --- | ----- |
| Pill Bug | 1 | [MechWild Store](https://mechwild.com/product/pillbug/)
| 3.7V battery | 1 | [2000mAh](https://a.co/d/dVUdHxi)
| Power button | 1 | Optional, [10mm](https://a.co/d/i33uBM0) or [19mm](https://a.co/d/fYN6ZX5)

### Additional "Pro" Components

| Position | Description | Qty | Notes |
| -------- | ----------- | --- | ----- |
| U1       | Elite-C/Elite-Pi | 1 |
|          | 3.7V battery | 1 | [2000mAh](https://a.co/d/dVUdHxi)
| U2       | 74HC595      | 1 | [Amazon](https://a.co/d/eLX9kOY)
| U2       | 16-pin IC socket | 1 | [Amazon](https://a.co/d/5EaFAHo)
| D6-D8    | 1n4148 Diode | 3 | [Link](https://www.mouser.com/ProductDetail/512-1N4148TR)
| BZ1      | Piezo Buzzer | 1 | [Link](https://www.digikey.com/en/products/detail/tdk-corporation/PS1240P02BT/935924)
| SW1      | Reset button | 1 | [Link](https://www.mouser.com/ProductDetail/642-MJTP1230A)
| R5-R19   | 10k Resistor | 15| AVR/Elite-C Only [Link](https://www.mouser.com/ProductDetail/YAGEO/MFR-12FTF52-10K?qs=oAGoVhmvjhzLlUYKKBtdYQ%3D%3D), [Link](https://mou.sr/3xgqcNf)


#### -or- Nice!Nano for wireless build

| Description | Qty | Notes |
| ----------- | --- | ----- |
| Nice!Nano    | 1 | [Website](https://nicekeyboards.com/nice-nano/)
| 3.7V battery | 1 | [2000mAh](https://a.co/d/dVUdHxi)
| Power button | 1 | Optional, [10mm](https://a.co/d/i33uBM0) or [19mm](https://a.co/d/fYN6ZX5)

### Instructions

<img src="https://i.imgur.com/CxrAwX4.jpeg" width="350">

_NOTE: If you're using a battery that's larger than 500mAh, then bridge the charge boost jumper labeled JP1 with some solder.  This will increases the max charge rate from 100mA to 500mA. Doing this for small batteries (<500mAh) may cause explosions._

All components go on the side with the silkscreen labels (rectangles) EXCEPT for the LEDs.  First solder the header pins onto your development board, and the header sockets onto the PCB.  I prefer to use Mill-Max 310 series sockets because the pins are thin.  Then solder in the LED resistors, but NOT the actual LEDs yet.  The resistors can be SMD or through hole.

For a wireless build, you can now solder the battery wires/connector to the board.  Make sure the positive wire goes into "BAT+", and the negative wire goes into "BAT-".  If you're using a power button, make sure to wire it inline along the BAT+ wire so that it essentially opens and closes the circuit.

Insert your development board into the sockets on the PCB.

For the Molex connectors, I find that it's more convient to desolder the ones on the original PCB so that I don't have to purchase new ones.  Solder the connectors onto the PCB.

Flip the PCB over and insert the LEDs on the side of the PCB with no other components.  Make sure the short leg goes into the square pad, and bend the legs so that they stay in place.  Screw the PCB back into the keyboard case, making sure the LEDs are lined up with the existing case holes.  You can also adjust the height of the LED to move them closer to the status window if you'd like.  Once you're satisfied with the position of the LEDs, you can then solder them in place while the PCB is still mounted.

Lastly, plug the USB-C panel mount cable to into the development board, and secure the other end to the hole in the case.

<img src="https://i.imgur.com/YmkMPXHh.jpeg" width="350">

<img src="https://i.imgur.com/bI6Lwymh.jpeg" width="350">


### "Pro" Additional Instructions

The components required for this build and their position will depend on the development board you're using.  For example, pull-down resistors R5-R19 are only needed for AVR chips (Pro-Micro, Elite-C) since they don't support internal pull-downs for the row inputs.  Use the image below as a guide.

<img src="https://i.imgur.com/sp7KOUK.png" width="350">

The Elite-C has an extra B0 pin that is broken out into the J10 pins.  You can use this to drive other components if you choose (ie. RGB strip, Solenoid)

* Pin 1 (square pad) - VCC
* Pin 2 - B0
* Pin 3 - GND

The J9 pins are for foot pedals and have the following assignment:

* Pin 1 (square pad) - Col6
* Pin 2 - Row0
* Pin 3 - Row1
* Pin 4 - Row2

Diodes D6-D8 are connected to the rows, so no additional diodes are needed in the pedals/switches.

<img src="https://i.imgur.com/vDt3BZc.jpeg" width="350">

### "Pro" Nice!Nano Additional Instructions

Mill-Max 310 sockets are recommended for socketing the Nice!Nano because thin pins are required for connecting the extra 3 pins in the middle.

The Nice!Nano is one pin short of supporting all 4 status lights on the Advantage.  If you want to utilize the unused numpad status LED as a power indicator, go ahead and short JP1 with some solder.

<img src="https://i.imgur.com/5jWpRJg.jpeg" width="350">

## Thumb cluster PCB build guide

The wiring for the thumb cluster (a.k.a. matrix wiring) has not been altered from original, so theoretically, they can be used in conjunction with any Kinesis PCB, including the stock one.

The PCB is also reversible, so you don't have to place separate orders for a "left" version and a "right" version.

### Components

| Description | Qty | Notes |
| ----------- | --- | ----- |
| 1N4148 SOD-123 diode | 12 | [Amazon](https://a.co/d/gsv8bGT)
| MX switch | 12 | Can desolder and reuse
| 2u screw-in stabilizer | 4 | [Link](https://divinikey.com/products/durock-v2-stabilizers-screw-in)
| Cable connector (1x10) | 4 | 2.54mm pitch (eg KF2510)
| Ribbon cable | 2 | >= 50mm length

### Instructions

<img src="https://i.imgur.com/fso7a7l.jpeg" width="350">

You will need two PCBs for the thumb cluster, but since they're reversible, you will need to read the silkscreen to see if it's the left or right cluster.

First step is to solder all the 1N4148 diodes.  Orientation matters, so make sure the line on the diode faces same direction as the thicker white line on the PCB.  Place a dab of solder on ONE of the two diode pads.  Drop the diode into position (double checking the orientation), hold the diode in place with tweezers, and melt the solder you just added to the pad so that diode is held in place.  Now add solder to the opposite pad, thus holding the other diode leg in place.  Repeat for all the other diodes.

The connector for the ribbon cable can now be soldered onto the PCB, and will be on the same side as the diodes.  The pin pitch is 2.54mm, so any compatible connector/cable will work here.

Install the 2u stabilizers onto the PCB.

Now solder in your MX switches.  If you're reusing the original switches, desolder them from the original PCB, and remove the diode from inside the switch housing.  Using a switch opener will make this task much easier.

<img src="https://i.imgur.com/ROcCSb1.jpeg" width="350">


Mount the thumb clusters onto the keyboard and connect the ribbon cables.

<img src="https://i.imgur.com/2i21le3.jpeg" width="350">


## QMK firmware for "Pro"

* `firmware/pro_qmk_avr_default.bin`
* `firmware/pro_qmk_rp2040_default.uf2`

QMK source: https://github.com/dcpedit/qmk_firmware/tree/pillzmod/keyboards/dcpedit/pillzmod

## Vial firmware for Blackpill

* `firmware/dcpedit_kint_bp_vial_6layers.bin`

Source: https://github.com/dcpedit/vial-qmk/tree/pillzmod/keyboards/dcpedit/pillzmod

### Flashing firmware under Linux
The file firmware/dcpedit_kint_bp_vial_6layers.bin (or other) can simply be flashed to the Blackpill using the dfu-util. The dfu-util tool requires root privileges if settings are not accessible by the user.

Connect Blackpill to your Linux PC via USB C cable and start unit in DFU mode by holding bootp button and pressing reset button. Wait a second and release the bootp button.

Check the DFU devices by running
```
dfu-util -l
```
The Blackpill device should be visible.

Write the firmware to the device with
```
dfu-util -d 0483:df11 -a 0 -s 0x08000000 -D [PATH TO kint]/firmware/dcpedit_kint_bp_vial_6layers.bin
```

Blackpill source: https://github.com/dcpedit/vial-qmk/tree/vial/keyboards/dcpedit/kint_bp

Remap keys: https://vial.rocks/

## Vial firmware for "Pro"

Coming soon

## ZMK firmware for Pill Bug

<img src="https://i.imgur.com/p7KiuxG.jpeg" width="350">

* `firmware/zmk_default.uf2` - Default keymap
* `firmware/zmk_custom.uf2` - Support for up to 6 layers
* `firmware/zmk_reset.uf2` - Resets PillBug board for BT connectivity issue on MacOS      

Source: https://github.com/dcpedit/zmk/tree/kinesispb/app/boards/shields/kinesispb

## ZMK firmware for "Pro" Nice!Nano

* `firmware/pro_zmk.uf2` - Default keymap

Source: https://github.com/dcpedit/zmk/tree/pillzmod/app/boards/shields/pillzmod_pro

### Bluetoobh with ZMK

The ZMK firmware has mappings for performing system tasks. By default there are 4 Bluetooth pairings saved to the keyboard but they do not switch automatically when adding new devices. So after you add the first device, you need to tell they keyboard to use Bluetooth slot 2 and so forth.
The keys to switch between are accessed by a different keyboard layer. This layer is opened by holding down the "Program" key at the very top right of the Kinesis and, while holding it, then clicking another key as follows:

* **Clear all saved Bluetooth profiles:** Program + F9
* **Bluetooth profile 1:** Program + F1
* **Bluetooth profile 2:** Program + F2
* **Bluetooth profile 3:** Program + F3
* **Bluetooth profile 4:** Program + F4
* **Enter bootloader mode (to upload UF2 files):** Program + - (the dash key just below program)

Source: https://github.com/dcpedit/zmk/tree/kinesispb/app/boards/shields/kinesispb

If you want to do a ZMK firmware build using GitHub actions, take a look at the following repository from keepitsimplejim:

https://github.com/keepitsimplejim/zmk-config-pillzmod-kinesis-adv

## KiCad

All the PCBs were designed using KiCad, which is free and can be downloaded here: https://www.kicad.org/

For the thumb cluster PCB, I wasn't able to figure out how to have the left and right wiring co-exist without errors while sharing the same connector footprint.  My workaround was to first change the connector's reference designator to "J1", update the PCB from schematic, and wire up the left side.  Then I changed the reference designator to "J2", updated the PCB from schematic again, and wired up the right side.

If there are any KiCad experts out there that know of a more elegant solution, please let me know.

The production JLCPCB files are all generated with Fabrication Toolkit: https://github.com/bennymeg/Fabrication-Toolkit
