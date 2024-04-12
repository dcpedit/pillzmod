
<p align="center">
  <img src="assets/logo.jpg" width="300">
</p>

# Pillz Mod for the Kinesis Advantage/Contoured

![PCB](https://i.imgur.com/TwBOiEr.jpeg)
![PillzMod](https://i.imgur.com/PJ1Fk2n.jpg)

This project replaces my two previous forks ([kinesismod](https://github.com/dcpedit/kinesismod) and [kint](https://github.com/dcpedit/kint)) for adding Blackpill support to the Kinesis keyboard.  I've decided to merge all the features into a single PCB, add optional thumb cluster PCBs as part of the kit, and renamed the project to avoid confusion.  Below is a list of supported features.

* Supports Blackpill development board running QMK/Vial
* Supports Pill Bug wireless Bluetooth development board running ZMK
* Optional reversible thumb cluster PCB for left/right sides.  (Maintains original matrix wiring)
* 2u stabilizer support on thumb cluster

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
| Description | Qty | Notes |
| ---     | --- | ----- |
| Molex 39-53-2135 | 2 - 6  | [Link](https://octopart.com/61301011121-w%C3%BCrth+elektronik-18818159?r=sp)
| Header pins (1x20) | 2 | Should come with dev board
| Headers (1x20) | 2 | To socket your dev board
| 1.8mm LED | 4 | [Amazon](https://a.co/d/90uynIs)
| 10k resistor | 4 | Affects LED brightness. Smaller = brighter |
| USB-C panel mount | 1 | [AliExpress](https://www.aliexpress.us/item/3256806463941289.html?spm=a2g0o.order_list.order_list_main.43.18a31802pDYB6d&gatewayAdapt=glo2usa), [Amazon](https://a.co/d/cRoqHqx)

#### Blackpill
| Description | Qty | Notes |
| ----------- | --- | ----- |
| Blackpill (STM32F411) | 1 | [WeAct Store](https://www.aliexpress.com/store/1101545918?spm=a2g0o.order_list.order_list_main.2.18a31802pDYB6d)

#### -or- Pill Bug for wireless build

| Description | Qty | Notes |
| ----------- | --- | ----- |
| Pill Bug | 1 | [MechWild Store](https://mechwild.com/product/pillbug/)
| 3.7V battery | 1 | [2000mAh](https://a.co/d/dVUdHxi)
| Power button | 1 | Optional, [Amazon](https://a.co/d/i33uBM0)

### Instructions
<img src="https://i.imgur.com/CxrAwX4.jpeg" width="350">

_NOTE: If you're using a Pill Bug with a battery that's larger than 500mAh, then bridge the charge boost jumper labeled JP1 with some solder.  This will increases the max charge rate from 100mA to 500mA. Doing this for small batteries (<500mAh) may cause explosions._

All components go on the side with the silkscreen labels (rectangles) EXCEPT for the LEDs.  First solder the header pins onto your development board, and the header sockets onto the PCB.  Then solder in the LED resistors, but NOT the actual LEDs yet.  The resistors can be SMD or through hole.

For a Pill Bug with battery build, you can now solder the battery wires/connector to the board.  Make sure the positive wire goes into "BAT+", and the negative wire goes into "BAT-".  If you're using a power button, make sure to wire it inline along the BAT+ wire so that it essentially opens and closes the circuit.

Insert your Blackpill/Pill Bug development board into the sockets on the PCB.

For the Molex connectors, I find that it's more convient to desolder the ones on the original PCB so that I don't have to purchase new ones.  Solder the connectors onto the PCB.

Flip the PCB over and insert the LEDs on the side of the PCB with no other components.  Make sure the short leg goes into the square pad, and bend the legs so that they stay in place.  Screw the PCB back into the keyboard case, making sure the LEDs are lined up with the existing case holes.  You can also adjust the height of the LED to move them closer to the status window if you'd like.  Once you're satisfied with the position of the LEDs, you can then solder them in place while the PCB is still mounted.

Lastly, plug the USB-C panel mount cable to into the development board, and secure the other end to the hole in the case.

<img src="https://i.imgur.com/YmkMPXHh.jpeg" width="350">

<img src="https://i.imgur.com/bI6Lwymh.jpeg" width="350">

## Thumb cluster PCB build guide

The wiring for the thumb cluster (a.k.a. matrix wiring) has not been altered from original, so theoretically, they can be used in conjunction with any Kinesis PCB, including the stock one.

The PCB is also reversible, so you don't have to place separate orders for a "left" version and a "right" version.

### Components
| Description | Qty | Notes |
| ----------- | --- | ----- |
| 1N4148 diode | 12 | [Amazon](https://a.co/d/gsv8bGT)
| MX switch | 12 | Can desolder and reuse
| 2u screw-in stabilizer | 4 | [Link](https://divinikey.com/products/durock-v2-stabilizers-screw-in)
| Cable connector (1x10) | 2 | 2.54mm pitch
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


## Vial firmware for Blackpill

* `firmware/dcpedit_kint_bp_vial.bin`

Source: https://github.com/dcpedit/vial-qmk/tree/vial/keyboards/dcpedit/kint_bp

Remap keys: https://vial.rocks/

## ZMK firmware for Pill Bug

<img src="https://i.imgur.com/p7KiuxG.jpeg" width="350">

* `firmware/zmk_default.uf2` - Default keymap
* `firmware/zmk_custom.uf2` - Support for up to 6 layers
* `firmware/zmk_reset.uf2` - Resets PillBug board for BT connectivity issue on MacOS


Source: https://github.com/dcpedit/zmk/tree/kinesispb/app/boards/shields/kinesispb

## KiCad

All the PCBs were designed using KiCad, which is free and can be downloaded here: https://www.kicad.org/

For the thumb cluster PCB, I wasn't able to figure out how to have the left and right wiring co-exist without errors while sharing the same connector footprint.  My workaround was to first change the connector's reference designator to "J1", update the PCB from schematic, and wire up the left side.  Then I changed the reference designator to "J2", updated the PCB from schematic again, and wired up the right side.

If there are any KiCad experts out there that know of a more elegant solution, please let me know.