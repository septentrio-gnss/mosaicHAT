# mosaicHAT

<img src="doc_resources/mosaicHAT_logo_withText.png" width="60%">

mosaicHAT: A GNSS HAT for Raspberry PI </br>
Maintainer: Septentrio <githubuser AT septentrio DOT com> </br>
Author: Jamal Sa'd <jamalhazem127 AT gmail DOT com> </br>
External website: https://github.com/septentrio-gnss/mosaicHAT </br>
License: <a href="https://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution Share-Alike License.</a> and <a href="https://www.oshwa.org/definition/">Open Source HW</a>


Table of contents
=================
<!--ts-->
   * [Introduction to mosaicHAT](#introduction-to-mosaichat)
      * [What is mosaicHAT?](#what-is-mosaichat)
      * [A HAT for Raspberry Pi?](#a-hat-for-raspberry-pi)
      * [What is Septentrio's mosaic-X5 or mosaic-Sx?](#what-is-the-mosaic-x5-or-mosaic-sx?)
      * [Who is Septentrio?](#who-is-septentrio)
      * [Is the project Open Source?](#is-the-project-open-source)
      * [Disclaimer](#disclaimer)
   * [mosaicHAT user documentation](#mosaichat-user-documentation)
      * [main interfaces of mosaicHAT]
<!--te-->

## Introduction to mosaicHAT
### What is mosaicHAT?
The mosaicHAT is an Open Source GPS/GNSS HW PCB HAT which integrates <a href="https://www.septentrio.com/en/products/gnss-receivers/rover-base-receivers/receivers-module/mosaic">Septentrio's mosaic-X5</a> GNSS module (and other Septentrio pin compatible modules such as <a href="https://www.septentrio.com/en/products/correction-services/precise-point-positioning-services-land/secorx-s/mosaic-sx">Septentrio's mosaic-Sx</a>) with basic communications and which can be stacked into a Raspberry Pi system. 

The goal of the design is to allow easy HW prototyping using the mosaic-X5 GNSS module taking the advantage of the computer ecosystem provided by the Raspberry Pi environment. The board however can also be used standalone since it can be powered either via USB or via power pins. 
This project and design can be used either produced with your local electronics assembly house or can also be used as an starting point for your own HW integrations.

### A HAT for Raspberry Pi?
HAT stands for “Hardware attached on top”. It is a new hardware specification for add-one modules for the new Raspberry Pi model B+. HATs have several advantages compared to older add-on modules for the Raspberry Pi.
#### No soldering, just plug it onto the Raspbery Pi
With our older HiFiBerry boards you had to solder an 8-pin header onto the Raspberry Pi. While this is not a problem for experienced hackers, not everybody owns a solder station and can do this.
#### Robust mechanical design
With 4 mounting holes the connection between the Raspberry Pi and the add-on board is very robust. 

### What is the's mosaic-X5 or mosaic-Sx?
#### mosaic-X5
<a href="https://www.septentrio.com/en/products/gnss-receivers/rover-base-receivers/receivers-module/mosaic">Septentrio's mosaic-X5</a>, a multi-band, multi-constellation GNSS receiver in a low power surface mount module with a wide array of interfaces, designed for mass market applications like robotics and autonomous systems, capable of tracking all Global Navigation Satellite System (GNSS) constellations supporting current and future signals. With unique built-in AIM+ technology for interference mitigation, Septentrio is offering a performance benchmark in mass market GNSS positioning building blocks.

#### mosaic-Sx
<a href="https://www.septentrio.com/en/products/correction-services/precise-point-positioning-services-land/secorx-s/mosaic-sx">Septentrio's mosaic-Sx</a> module offers a unique approach to GNSS positioning. It provides convenient always-on high-accuracy positioning right out of the box. No need for any additional correction service selection, subscription and maintenance. This is made possible by an integration of a PPP-RTK sub-decimeter correction service into Septentrio’s latest core GNSS technology. With all-in-view satellite tracking and unmatched anti-jamming technology mosaic-Sx offers a perfect combination of convenience and performance in a very small size factor.

### Who is Septentrio?
Septentrio designs, manufactures and sells high-precision, multi-frequency, multi-constellation GPS/GNSS equipment for use in demanding applications. Septentrio products are used in a wide variety of industries including marine, construction, precision agriculture, logistics, machine control, rail, automotive, survey and mapping, geographic information systems (GIS), unmanned aerial vehicles (UAVs) and scientific. Septentrio receivers deliver consistently accurate and precise GNSS positioning scalable to centimeter-level and designed to perform solidly in the most challenging environments. Septentrio receivers are available as OEM boards, housed receivers and smart antennas.

The technology offers high accuracy and reliability thanks to GNSS+ algorithms as well as <a href="https://www.septentrio.com/en/advanced-interference-monitoring-mitigation-aim">Septentrio's Advanced Interference Monitoring and Mitigation (AIM+)</a> which protects against RF interference (jamming) and spoofing.

For more information about Septentrio products go to http:\\www.septentrio.com

### Is the project open source?
Yes, as it allows easy adaptations and thus enables the robotics and autonomous community to create their own spin off projects.
As such this can be also a starting reference point for integrators when in need of GNSS integration.

With open source it means that the following is provided:
-Editable source files
-Modifications and spinn off projects allowed
-You are allowed to sell your version. No -NC limitations.
-May require attribution
-We encourage you to stand on our shoulders and even make money at it! 

More info about licensing can be found here: 
<a href="https://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution Share-Alike License.</a> and <a href="https://www.oshwa.org/definition/">Open Source HW</a>

### Disclaimer
This project is provided as is and while the general interfaces have been tested, the project has not been fully validated nor by the author nor by Septentrio. 
We recommend you to contact Septentrio should you have questions on how to integrate Septentrio's GNSS modules.

Their support email address is <support AT septentrio DOT com> </br>

## mosaicHAT user documentation
### general interfaces of mosaicHAT
The board exposes the following interfaces:
<img src="doc_resources/mosaicHAT_features.png" width="80%">

### Connecting to Raspberry Pi

#### Preparing Raspberry Pi

To enable communication between mosaicHAT and Raspberry Pi (RPi), you should make sure needed communication permissions are set. We've tested mosaicHAT with both Raspbian OS and Ubuntu OS on RPi and found the following points needed.

##### Raspbian OS
- To enable RPi serial communication, go to terminal and run:

  `sudo raspi-config`

- Select **Interfacing Options**, then from the menu select **Serial**. You will get the question:

  *Would you like a login shell to be accessible over serial?*

  Select **No**. Another prompt will ask:

  *Would you like the serial port hardware to be enabled?*

  Select **Yes**.

- Finally, exit the config and reboot RPi for changes to take effect.

##### Ubuntu OS

- To enable RPi's UART, go to `/boot/config.txt` and set `enable_uart=1` at the end of the file. This could be done directly on SD card or using:
 
  `sudo nano /boot/config.txt` 

- You will also need to disable UART console login. To do so on RPi 4, use:

  `sudo nano /boot/firmware/nobtcmd.txt` 

  And delete `console=ttyAMA0,115200` from the file. For different RPi versions, the cmd configuration file could be `/boot/cmdline.txt`.

- TCP/IP over USB may not be enabled by default. To enable TCP/IP over USB, go to:

  `sudo nano /etc/network/interfaces`

  And add:
  ```
  allow-hotplug usb0

  iface usb0 inet dhcp
  ```
-  Reboot RPi for changes to take effect.

#### USB Communication


Connecting RPi, as well as any other PC, to mosaic via USB provides:
- Septentrio's web interface
- Two USB serial ports
- Multiple TCP/IP ports

#### Serial Communication

#### General Purpose LEDs

#### FTDI

#### Input Reset

#### PPSO

#### Events


## mosaicHAT Design documentation
This section is intended for people who want to understand more about the design of the mosaicHAT
### Design Overview
mosaicHAT is a 4-Layer Printed Circuit Board (PCB) designed to stack on top of Raspberry Pi. Both Top and Back layers are used for power and signals. The first inner layer is a GND plane whereas the second inner layer functions as a 3.3V power plane with a slight use of other connections.

Other than the female Raspberry Pi connecter, all components are placed on the Top layer. All components are Surface Mount Devices (SMD) except for connectors.

mosaicHAT was designed using [KiCAD](https://kicad-pcb.org), an open source suite for Electric Design Automation. KiCAD provides a beautiful 3D viewer besides its design capabilities.

Following is the schematic plan, for higher quality check [PDF plan](mosaicHAT_schematic.pdf).

<img src="doc_resources/schematic_big.PNG" width="60%">


A top 3D view of mosaicHAT showing main components.

<img src="doc_resources/3dplan.PNG" width="60%">

The following sections provide more details on mosaicHAT design.

### mosaic Pinout

// to add later

### Power Sources

mosaicHAT could be powered by three options; Raspberry Pi, Micro USB and external power pin headers. mosaic module itself runs on 3.3V, thus a voltage regulator is used (LD1117AS33TR). According to its datasheet, the regulator's maximum input is 15V. Raspberry Pi and Micro USB already provide 5V. User should be careful when connecting higher voltage to external power pin headers. Though 5V is preferable, user can input up to 15V only if both VANT and FTDI PWR SRC jumpers are connected to 3.3V. Pin headers of 5V in the jumpers are connected directly to the input source as it's presumed to be 5V.

Schottky diodes (MBRX120LF-TP) are used to insure one-way current direction. Decoupling capacirors (100nF and 10uF) are used according to regulator’s datasheet. Following is the power part of schematic.

<img src="doc_resources/regulator_sch.PNG" width="60%">

<img src="doc_resources/power_brd.png" width="60%">

In the figure above:

1. Regulator's circuit.

2. Raspberrpi power source (5V pins).

3. External power source headers.

4. Micro USB power source.

### Antennas

mosaic is a dual-antenna module. It can perfectly function with one antenna, however, connecting a second antenna increases accuracy and enables heading sensing.

Following is the antennas part in schematic.

<img src="doc_resources/ant_sch.PNG" width="60%">
 
#### First Antenna
The first antenna SMA connector is directly connected to ANT1 pad. ANT1 is ESD-protected within the module and carries DC voltage. The DC voltage of ANT1 is supplied from mosaic's VANT pad. mosaicHAT's user could choose between 3.3V and 5V supply to VANT using 2.00 mm header jumpers.

The nominal input impedance of the RF line is 50 Ohms. Thus, antenna trace should have a characteristic impedance (Zo) of 50 Ohms. Line impedance could be measured by different tools, such as the freeware [Saturn PCB toolkit](https://saturnpcb.com/pcb_toolkit).

<img src="doc_resources/line_impdence.PNG" width="60%">

Right characteristic impedance (45-55 Ohms) could be reached by adjusting the width of RF line (Conductor Width) having PCB specifications fixed. Frequency is set to 1575 MHz as the GPS L1 Frequency. Conductor Hight is the thickness of the dielectric material between Top layer and the next copper layer which depends on manufacturing service and board specifications, in mosaicHAT's case it's 0.36 mm.

Having right characteristic impedance insures reduced reflections in the opposite direction thus higher quality of signals. For uniform lines, characteristic impedance is not dependent on trace length.

It is also important to stich vias every few millimetres around the RF line for good ground coherence. Stitching GND vias help to protect line from interference.

<img src="doc_resources/stiching_vias.PNG" width="60%">

For more details on antennas and interference please refer to mosaic's [Hardware Manual](HWManual.pdf).

Following is the first antenna part of board layout. The center of SMA connector is copper freed to prevent undesired capacitance due to high copper density.

<img src="doc_resources/ant1layout.PNG" width="60%">

// ask about the freq

// check about capacitance

#### Second Antenna

The second antenna is similar to first antenna except that ANT2 pad in mosaic is not internally ESD-protected and does not carry DC voltage by itself. Wherefore, both protection and DC biasing are needed.

For ESD protection, TVS diode (SESD0402X1BN-0010-098) is used. TVS diode protects the module against sudden removal of the antenna. As any stubs branching out of the RF line could cause undesired reflections, TVS diode shoud be placed exactly on top of the RF trace.

Biasing inductors are used to supply the ANT2 with DC voltage from ANT1 trace. Two inductors, one for each RF line, are used to avoid stubs and provide single tracks for RF signals. The inductor value is best to be around 33 nH with self resonant frequency of 1.4 GHz. A 100 nF bypass capacitor has been placed between inductors to filter out any AC noise.


<img src="doc_resources/ant_board.png" width="60%">

In the figure above:

1. ANT1 RF trace.

2. DC biasing circuit.

3. ANT2 RF trace.

4. VANT source jumper 2.00 mm headers.

5. TVS diode.

// highlight SMA connectors

### Raspberry Pi Serial

Serial communication with Raspberry Pi is conducted by connecting COM1 of mosaic to Raspberry Pi UART pins: TX (GPIO 14) and RX (GPIO 15). GPIO 14 is pin 8 on the GPIO header whereas GPIO 15 is pin 10. Raspberry Pi's TX is connected to mosiac's RX1 while RX is connected to mosaic's TX1.

According to the hardware manual, non-zero voltage should not be driven to mosaic's input pads while in standby mode.

<img src="doc_resources/drive_nonzero.PNG" width="100%">

Thus, MosaicRX1 signal has been tri-stated by MODULE_RDY using tri-state buffer (SN74LVC1G126DRLR). 


<img src="doc_resources/serial_sch.PNG" width="80%">

// rename buffer in schematic

### Reset Input

### Micro USB

To use mosaic as a USB device, the following pins of the module should be connected to a USB connector.

<img src="doc_resources/usb_hwmanual.PNG" width="60%">

A common mode filter with ESD protection for USB 2.0 (ECMF02-2AMX6) is used with USB_DEV_P (D+) and USB_DEV_N (D-) for protection. The filter suppresses the noise of electromagnetic interference (EMI) on high speed differential USB lines.  

<img src="doc_resources/microusb.PNG" width="60%">

As USB uses a differential pair, differential pair impedance (Zdifferential) should be tuned to avoid reflections. Zdifferential needs to be around 90 Ohms. Zdifferential could be calculated using Saturn's PCB toolkit. For mosaicHAT USB, traces width was set to 0.35 mm with 0.15 mm spacing.

<img src="doc_resources/diff_impedence.PNG" width="60%">

Following board figure shows USB parts highlighted. GND vias were stitched around the USB connector and lines to insure good ground coherence. 

<img src="doc_resources/psdboard_usb.png" width="60%">


1. Micro USB connector (Molex 1050170001).

2. Common mode filter.

3. USB D+/D- lines.

4. USB_V.

### Events and PPSO

mosaic offers two event inputs which could be used to time tag external events. Both input pads of mosaic, EVENTA and EVENTB, use 1.8V level. For better integration with external applications, a level shifter (SN74AVC4T245PWR) is used to transform signals into 3.3V level.

Pulse Per Second Output (PPSO) is a mosaic clock output. Polarity, frequency and pulse width of PPSO could be configured by **setPPSParameters** command. As PPSO uses 1.8V level as well, same level shifter is used to get 3.3V level signals.

Both EVENTS and PPSO 3.3V levels are connected to 2.54 mm pin headers.

<img src="doc_resources/levelshifter_sch.PNG" width="60%">

Port A tracks 1.8V while port B tracks 3.3V level. Direction could be set for two channels, each provides two connections. (1DIR) is set to low for mosaic input direction while (2DIR) is set to high for output direction. Both (O̅E̅) pins are set to low to enable low impedance state. VCCB is connected to +3.3V while VCCA is connected to +1.8V, which is supplied by 1V8_OUT pin of mosaic. Bypass capacitors are used on power supplies according to datasheet.
 
<img src="doc_resources/psdboard_events.png" width="60%">

1. EVENTS, PPSO and 1V8_OUT vias, connected to level shifter via Back layer.

2. Level shifter.

3. 3.3V level pin headers.


### FTDI

Second serial connection to mosaic (COM2) is exposed through 2.54 mm pin headers. The FTDI connection could be used to communicate with other devices through serial (e.g. HC-06 Bluetooth module).

If the device needs mosaicHAT's power, like HC-06, VCC pin of FTDI could be used. 5V or 3.3V could be provided by moving The FTDI PWR SRC jumpers.

<img src="doc_resources/ftdi_sch.PNG" width="80%">

### LEDs

mosaicHAT comes with five blue indicator LEDs.

<img src="doc_resources/leds_sch.PNG" width="40%">

<img src="doc_resources/psdboard_leds.png" width="60%">

1. Raspberry Pi's (GPIO 6) which is pin 31 in header, connected to GL1 LED. 

2. Raspberry Pi's (GPIO 26) which is pin 37 in header, connected to GL2 LED. 

3. PPSO 3.3V level, connected to PPS LED.  

4. Trace to mosaic's GPLED pin, connected to PVT LED.  

5. Indicator LEDs, PWR LED is directly connected to 3.3V power plane. 

PPSO clock could be tuned using **setPPSParameters** command. While GPLED default mode is *PVTLED*, it could be configured to work in different modes (*PVTLED*, *DIFFCORLED* and *TRACKLED*) using **setLEDMode** command. Refer to the Hardware Manual for blinking behaviour of each mode. Both General LEDs (GL1 and GL2) could be directly controlled by Raspberry Pi for customized user applications.

### Clock Frequency Reference 

mosaic module embeds an internal Temperature Compensated Crystal Oscillator (TCXO) for frequency reference. The module can either use its internal TCXO frequency reference or an external frequency reference. In Mosiachat's case, internal reference is used. Following are  Hardware Manual instructions for using internal TCXO.

<img src="doc_resources/ref_hwmanual.PNG" width="60%">

Layout connections for REF and 2V8.

<img src="doc_resources/REF_2V8_lyo.png" width="60%">



