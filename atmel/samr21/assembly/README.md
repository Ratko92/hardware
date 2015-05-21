These are the assembly instructions and firmware files for setting up a
[Thingsquare](http://thingsquare.com) system based on the
Atmel wireless [SAM R21](http://www.atmel.com/tools/atsamr21-xpro.aspx)
System-on-a-Chip.

## Hardware

Hardware needed to build a Thingsquare system:

* At least two [SAM R21 Xplained Pro evaluation boards](http://www.atmel.com/tools/atsamr21-xpro.aspx)
* Micro USB cables (one per SAM R21 device)
* One [Atmel Ethernet1 Xplained PRO extension board](http://www.atmel.com/tools/ETHERNET1_XPRO.aspx)
* An Ethernet cable
* A WiFi router with an Ethernet port connected to the Internet
* A PC for uploading the Thingsquare firmware to the chips

## Software and firmware

Software needed to be installed and firmware needed to be downloaded
to build a Thingsquare system:

* [Atmel Studio 6.2 or later](http://www.atmel.com/tools/ATMELSTUDIO.aspx)
* The Thingsquare SAMR21 firmware `client.hex` from the [firmware directory](../firmware/)
* The Thingsquare SAMR21 Ethernet router firmware `gateway.hex` from the [firmware directory](../firmware/)

## Upload the firmware to the wireless nodes

* Download the Thingsquare SAMR21 firmware `client.hex`from the [firmware directory](../firmware/)
* Start Atmel Studio
* Connect a SAM R21 board to your PC (using the connector labeled "EDBG USB")
* Verify that Atmel Studio discovers the board (it should show up automatically)
* Press Ctrl+Shift+P to enter Programming mode
* Select EDBG under "Tool" and click "Apply"
* Drag the slider to approx 2 MHz and click "Set"
* Select "Memories" in the menu on the left
* Enter the path to the downloaded firmware in the "Flash" field and click program (with the options "Erase" and "Verify" set)
* Repeat for all the nodes except the router node (see below)

Screen captures below:
![Atmel Studio 2 screenshot](program-2.png?raw=true)
![Atmel Studio 2 screenshot](program-3.png?raw=true)


## The router node
![Connected router node](r21_eth.jpg?raw=true)
The router node is a regular SAM R21 board with an Ethernet connector
board that runs the Thingsquare router firmware.
* Attach the Ethernet extension board to the EXT1 header on the R21 board
* Program the node using Atmel studio as above with the Thingsquare SAMR21 Ethernet router firmware `gateway.hex`
from the [firmware directory](../firmware/)


## Power up the wireless nodes
![Assembled wireless nodes](r21_kit.jpg?raw=true)
* Connect the Ethernet cable to the extension board on the router node and to the Internet
* Connect USB power cables to the connectors labeled "EDBG USB" and to
  a power source - *note* make sure to connect to the EDBG USB
  connector and not the Target USB connector.
* The nodes should all display a green steady light from the "Power"
  LED
* The Ethernet router should blink its LED until it has successfully
  connected to the Ethernet
* The wireless nodes should blink its LED until it has successfully
  connected to the wireless network and to the Thingsquare backend

## Open the app
Download the Thingsquare app from Google Play or the Apple app store and open it.

Tap the _Devices_ button to see the list of nearby devices. If the SAMR21 boards are not in the list, tap the _Scan_ button to scan for new devices.

## Troubleshooting

If you don't see the devices in the list even after scanning, make sure the LEDs have stopped blinking. If the LEDs are blinking, this means that the devices have not yet connected to the backend.

If the devices still do not show up in the app after scanning, make sure you are connected to the same WiFi as the SAMR21 Ethernet gateway.

## Connect to GPIOs

Two GPIO pins of the SAMR21 board can be controlled from the smartphone app: PA13 and PA28. They can be found on the EXT1 extension header. Connect an LED between either of the pins and the ground pin. You should now be able to control the LEDs from the app.
