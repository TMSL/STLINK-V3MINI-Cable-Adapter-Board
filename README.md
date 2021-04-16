# STLINK-V3MINI-Cable-Adapter-Board
PCB files for an STLINK-V3MINI Adapter / breakout board that provides 0.100" (2.54mm) connections from the STMicrolectronics defined "STDC14" (7x2 0.050") connector cable.

This adapter / breakout board was created to make it easier use the STDC14 cable that is provided with the MINI with boards that have 0.100" pin connections. It supports:
* FLASH programming
* Serial Wire Debugging (SWD)
* A Virtual Comm Port (VCP) over USB
* Serial Wire Viewer (SWV)

## Background
The STLINK-V3MINI is a very small and low cost FLASH programmer and in-circuit debug board for STM8 and STM32 microcontrollers that includes Serial Wire Viewer (SWV) and Virtual Comm Port (VCP) support, among other additional features. However, the STLINK-V3MINI STDC14 connector is an unusual size. The 0.050 (1.27mm) pitch and is not easily used with STM32 "maker" boards such as the Blue Pill, Black Pill, Maple Mini, and other boards that typically use 0.100" pin headers, it also doesn't match match the 10-pin cable standard defined for ARM JTAG.

## What's good about the STLINK-V3 MINI
* low cost compared to official STMicroelectronics STLINK-V2 and STLINK-V3SET products
* very small (maybe too small?)
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

* Provides interesting options for "bridging" I2C, GPIO, USART, and CAN between host USB and the board under test
  * Note: those additional features and connections are not provided on the adapter board. You'd need to connect directly to the castellated pads on the module 

## Additional Commentary
While the STDC14 pins include the 10-pin ARM JTAG signals as a subset, unfortunately you cannot directly plug a 0.050" 10-pin IDC ribbon cable directly into the MINI because of mechanical interference. (The design intent was better than the implementation). Additionally, the 2x7 0.50" sockets and headers are much harder for hobbyists to find in small quanties online than the 2x5 versions. If you're designing a new board it may be best to avoid directly supporting STM's STDC14 connector and stick with more standard and commonly available connectors.

# Making Your Own Board
The .ZIP file contains all the Gerber and Drill files needed to upload the design to a PCB fabrication service, such as JLCPCB. You should only need download the file from here and upload it to the service. It's a simple TWO LAYER board and should not require any special specifications or changes from the service's default configurations for two layer board manufacturing other than indicating that the DIMENSIONS ARE IN MM.

0.100" (2.54mm) pin headers are easy to find from many online sources. Finding the 2x7 0.050" (1.27mm) connector is more difficult. I wound up ordering my 1.27mm Pitch 2x7 Pin 14 Pin Straight Male Shrouded through-hole connectors from eBay. When ordering, check to make sure that there is a centered key slot. Alternatively, you can use generic 1.27mm pin header strips but since there is no shroud or key slot you need to be careful to avoid plugging in the cable the wrong way.

