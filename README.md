# Mosaichat
## 1. Mosaichat Design
### 1.1 Design Overview
Mosaichat is a 4-Layer Printed Circuit Board (PCB) designed to stack on top of Raspberry Pi. Both Top and Back layers are used for power and signals. The first inner layer is a GND plane whereas the second inner layer functions as a 3.3V power plane with a slight use of other connections.

Other than the female Raspberry Pi connecter, all components are placed on the Top layer. All components are Surface Mount Devices (SMD) except for connectors.

Mosaichat was designed using KiCAD, an open source suite for Electric Design Automation. KiCAD provides a beautiful 3D viewer besides its design capabilities.

Following is the schematic plan, for higher quility check [PDF plan](schematic.pdf).

![Mosaichat Schematic](schematic_big.PNG)

A top 3D view of Mosaichat with main components marked
![Mosaichat 3D](3dplan.PNG)
