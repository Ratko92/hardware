These are the assembly instructions for a [Thingsquare](http://thingsquare.com/) system based on the Texas Instruments
CC2538 wireless System-on-a-Chip.

A TI CC2538-based Thingsquare IoT cloud system consists of a number of
wireless nodes and one Ethernet router.

![A small Thingsquare system](kit.jpg?raw=true)

## Hardware

Hardware needed to build a Thingsquare system:

* At least one [Texas Instruments CC2538 development
  kit](http://www.ti.com/tool/cc2538dk)
* One [Olimex ENCH28J60-H ethernet
  board](http://www.olimex.com/Products/Modules/Ethernet/ENC28J60-H/)
* Six [female-to-female Dupont jumper
  cables](http://www.adafruit.com/products/266)
* An Ethernet cable
* A WiFi router, connected to the Internet
* A laptop, used for uploading the Thingsquare firmware to the chips

## Software and firmware

Software needed to be installed and firmware needed to be downloaded
to build a Thingsquare system:

* [TI Flash Programmer 2](http://www.ti.com/tool/flash-programmer)
* The Thingsquare CC2538dk firmware `client.bin` from the [firmware
  download page](../firmware/)
* The Thingsquare Ethernet router firmware `gateway.bin` from the [firmware download page](../firmware/)

# The Wireless Nodes

The wireless nodes consist of SmartRF06 boards with
CC2538em boards mounted on top of them.

![The wireless nodes](kit-nodes.jpg?raw=true)

## Assemble the wireless nodes

![An assembled wireless node](build01.jpg?raw=true)

* Attach the CC2538em board to the SmartRF06 board
* Connect the SmartRF06 board to the laptop via a USB cable
* Make sure the SmartRF06 POWER switch is in the ON position

## Upload the firmware to the wireless nodes

![Flash programmer 2 screenshot](flashing-node.png?raw=true)

* Download the Thingsqure CC2538dk firmware `client.bin` from the [firmware
  download page](../firmware/)
* On the laptop, run the [TI Flash Programmer
  2](http://www.ti.com/tool/flash-programmer) to upload the firmware
  to the board. Use the following settings:
  * Adress at 0x - 00200000
  * Erase/All
  * Program/entire source file
  * Verify/Readback

## Turn on the wireless nodes

* The LEDs should start blinking
* Nothing will be displayed on the LCD screen
* The LEDs will stop blinking once the device has successfully connected to the Thingsquare backend
* Build the Ethernet router per below

# The Ethernet Router

The Ethernet router is built from a CC2538 development board and
an Olimex Ethernet module, connected via Dupont cables.

![The Ethernet router board](build03.jpg?raw=true)

## Disconnect the jumpers

![Disconnect the jumpers](jumpers.jpg?raw=true)

* Make sure the SmartRF06 board is powered off and that
  no USB cable is connected

* Disconnect the jumpers on pin header 404

## Connect the cables to the Olimex board

![Connect the Olimex board](build06.jpg?raw=true)

* Connect four Dupont cables to pins 1, 2, 3, 7.
* Connect two Dupont cables to pins 9 (GND) and 10 (PWR).

## Connect the four first cables to the SmartRF board

![Connect four cables](build04.jpg?raw=true)

* Olimex 1 &ndash; SmartRF 1.16_SCK
* Olimex 2 &ndash; SmartRF 1.18_MOSI
* Olimex 3 &ndash; SmartRF 1.20_MISO
* Olimex 7 &ndash; SmartRF 2.10

## Connect the final two cables to the SmartRF board

![Connect the final cables](build05.jpg?raw=true)

* See picture as the pins on the SmartRF board are not marked.
* Olimex 9 &ndash; GND (black)
* Olimex 10 &ndash; PWR (red)

## Upload the router firmware

![Upload router firmware](flashing-router.png?raw=true)

* Connect the SmartRF06 board to the laptop via a USB
  cable
* Download the CC2538dk Ethernet router firmware `gateway.bin` from the [firmware
  download page](../firmware/)
* On the laptop, run the [TI Flash Programmer
  2](http://www.ti.com/tool/flash-programmer) to upload the firmware
  to the board. Use the following settings:
  * Adress at 0x - 00200000
  * Erase/All
  * Program/entire source file
  * Verify/Readback

## Connect to the Internet

![Connect the Ethernet](ethernet-connect.jpg?raw=true)

* Connect the Ethernet cable to the Ethernet module and
  the LAN port of your WiFi router
* Turn on the Ethernet board by setting the POWER switch to on
* The red LED should blink while the Ethernet router
  is looking for its IP address
* When the red LED has stopped blinking, the wireless
  nodes should be able to connect to the cloud.
* The LCD display of the Ethernet board should not display anything

# Open the app
Download the Thingsquare app from Google Play or the Apple app store and open it.

Tap the _Devices_ button to see the list of nearby devices. If the CC2538dk boards are not in the list, tap the _Scan_ button to scan for new devices.

## Troubleshooting

If you don't see the devices in the list even after scanning, make sure the LEDs have stopped blinking. If the LEDs are blinking, this means that the devices have not yet connected to the backend.

If the devices still do not show up in the app after scanning, make sure you are connected to the same WiFi as the Ethernet gateway.



