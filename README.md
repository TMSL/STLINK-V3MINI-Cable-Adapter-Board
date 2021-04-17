# STLINK-V3MINI-Cable-Adapter-Board
PCB files for an STLINK-V3MINI Adapter / breakout board that provides 0.100" (2.54mm) connections from the STMicrolectronics defined "STDC14" (7x2 0.050") connector cable. The adapter has been designed to support 1x12 headers to allow it to be plugged into a solderless breadboard or connected to the target using separate leads.

This adapter / breakout board was created to make it easier use the STDC14 cable that is provided with the MINI with boards that have 0.100" pin connections. It supports the following STLINK-V3MINI features:
* Device FLASH programming
* Serial Wire Debugging (SWD)
* A Virtual Comm Port (VCP) over USB
* Serial Wire Viewer (SWV)

<!-- comment: ![alt text](/Adapter3DImage.png?raw=true) -->
<p align="left">
  <img src="/Adapter3DImage.png?raw=true" width="350" alt="board image" title="STLINK-V3MINI Adapter">
</p>

Two 1x12 single row header positions are provided for connecting to the target board. The signals on both are identical. One or both may be populated as desired. For example, one header connector may be soldered on the top of the board to enable connecting to the target board with patch wires while another header connector may be simultaneously soldered on the bottom to facilitate plugging the adapter into a solderless breadboard. Dual-row headers or sockets may also be used, or cable wires directly soldered to the board, and so on... Your choice.

## Background
The STLINK-V3MINI is a very small and low cost FLASH programmer and in-circuit debug board for STM8 and STM32 microcontrollers that includes Serial Wire Viewer (SWV) and Virtual Comm Port (VCP) support, among other additional features. However, the STLINK-V3MINI STDC14 connector is an unusual size. The 0.050 (1.27mm) pitch and is not easily used with STM32 "maker" boards such as the Blue Pill, Black Pill, Maple Mini, and other boards that typically use 0.100" pin headers, it also doesn't match match the 10-pin cable standard defined for ARM JTAG.

## What's good about the STLINK-V3MINI :+1:
The board provides a number of features that put it a level up from the STLINK-V2.1 and two steps above the cheap STLINK-V2 clones.
<p align="left">
  <img src="https://user-images.githubusercontent.com/27512953/115096574-9f716500-9eda-11eb-98d0-d14632c64c95.jpg" width="350" alt="board image" title="STLINK-V3MINI Adapter">
</p>

* Low Cost compared to official STMicroelectronics STLINK-V2 and STLINK-V3SET products
* Very small (maybe too small?) Just 15mm x 30mm
* Delivered with 1.27 mm pitch STDC14 to STDC14 flat cable
* LEDs for communication and power
* Includes STDC14 signals protection
* Self-powered through Micro-B USB connector (Note: does not provide power supply to the target application)
* USB 2.0 high-speed compatible interface
* Can be upgraded or reprogrammed through Direct firmware update (DFU) (Potentially opening up the board to custom uses).
* JTAG / serial wire debugging (SWD) specific features:
  *  3 V to 3.6 V application voltage support and 5 V tolerant inputs
  *  SWD and serial wire viewer (SWV) communication support
* Virtual COM port (VCP) specific features:
  * 3 V to 3.6 V application voltage support on the UART interface and 5 V tolerant inputs
  * VCP frequency up to 15 MHz
* Provides interesting options for "bridging" I2C, GPIO, USART, SPI, and CAN between host USB and the board under test
  * Note: those additional features and connections are not provided on the adapter board. You'd need to connect directly to the castellated pads on the module 

## What's not so good about the STLINK-V3MINI :-1:
The board appears to have been designed first as a module (The STLINK-V3MODS) that was intended to be soldered onto the target or some other intermediate board taking the least amount of space possible while providing access to all of the MINI's features. The STDC14 connector fits into the overall design almost as an afterthought.
* The Size
** The STDC14 connector allows the STLINK-V3MINI to be used as a separate test board for its most used features, but a separate debug board having the smallest size is not a benefit compared to ease of connectivity.
* The STDC14 Connector
** While the STDC14 pins include the 10-pin ARM JTAG signals as a subset, unfortunately you cannot directly plug a 0.050" (1.27mm) 10-pin IDC ribbon cable directly into the MINI because of mechanical interference. (The design intent was better than the implementation).
** The 2x7 0.50" sockets and headers are much harder for hobbyists to find in small quantities online than the 2x5 versions. If you're designing a new board it may be best to avoid directly supporting STM's STDC14 connector and stick with more standard and commonly available connectors.
** The components for making the IDC ribbon cables are also harder to find, along with the ribbon cable material itself. Be gentle with the cable because if you bust it, getting a replacement will probably cost more than buying another board.
* No mounting holes
** Not a huge issue if it's hanging off the end of a USB cable using the 14-conductor flat ribbon cable
** Impedes using it from being installed on the target as a mezzanine card using the STDC14 connector, except temporarily - in which case you might as well use the cable.
** The module itself is solidly built and does not need to be handled very delicately. The mechanical weak points are in the STDC14 connector and the ribbon cable used to connect to the target board.

# Making Your Own Copy of the Adapter Board
The .ZIP file contains all the Gerber and Drill files needed to upload the design to a PCB fabrication service, such as JLCPCB. You should only need download the file from here and upload it to the service. It's a simple TWO LAYER board and should not require any special specifications or changes from the service's default configurations for two layer board manufacturing other than verifying that the DIMENSIONS ARE IN MM and selecting other options you may wish, such as board color or whether lead or lead-free solder tinning finish is used.

0.100" (2.54mm) pin headers are easy to find from many online sources. Finding the 2x7 0.050" (1.27mm) connector is more difficult. I wound up ordering my 1.27mm Pitch 2x7 Pin 14 Pin Straight Male Shrouded through-hole connectors from eBay. When ordering, check to make sure that there is a centered key slot. Alternatively, you can use generic 1.27mm pin header strips but since there is no shroud or key slot you need to be careful to avoid plugging in the cable the wrong way.

