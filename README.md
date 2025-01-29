# M2SmartHome

![M2SH Photo](images/M2SH-photo.jpeg)

## Overview

Setting up a smart home hub, such as running Home Assistant, often requires hardware with sufficient performance and connectivity options. Many existing solutions, like Raspberry Pi, may be insufficient for advanced automation tasks due to a low-power CPU or a slow microSD card on which the OS is installed. A good alternative could be an x86 mini PC, but these often lack expansion ports.  

M2SmartHome is an add-on card that operates on PCIe x1 and can be installed in any M.2 2280 Key M-equipped device. By integrating multiple essential components into a single device, it eliminates the need for external adapters and additional hardware.  

The device is equipped with onboard eMMC memory, an SD card reader, WiFi 802.11n 2.4GHz radio (RTL8188), and a Thread radio (EFR32) from Silicon Labs. Once installed in an M.2 slot, it provides both storage for the operating system and enhanced connectivity, making it an ideal choice for smart home setups.

![Render 1](images/M2SmartHome_cc9c86150_render_1.png)
![Render 2](images/M2SmartHome_cc9c86150_render_2.png)

## Features

- **Form Factor**: M.2 2280 Key M
- **Interface**: M.2 edge conenctor PCIe x1 
- **Storage**: Onboard eMMC, SD card reader
- **Wireless Connectivity**:
  - **WiFi**: 802.11n 2.4GHz (Realtek RTL8188)
  - **Thread Radio**: EFR32MG21 (Silicon Labs)


## Block diagram

On the diagram below siplified system architecture has been presented. PCIe x1 interface from host device is connected to PCIe bridge. To four USB 2.0 ports all crucial components are connected: eMMC memory controller, micro SD card controller, USB to UART bridge with Thread / ZigBee RF SOC and WiFi network card. 

![Block diagram](images/M2SmartHome_block_diagram.png)


### PCie to USB bridge
As a PCIe bridge choosen the `PI7C9X440SLBFDE` sold by Diodes Inc. (oryginally manufactured by Pericom). `7C9X440SLBFDE` is a PCIe-to-USB 2.0 host controller with a single x1 PCIe 1.1 interface, compliant with the PCIe Base Specification 1.1, supporting programmable driver current, de-emphasis levels, and advanced power management (L0, L0s, L1, L2, L2/L3Ready, L3, D0, D3Hot, D3Cold). It features four USB 2.0 ports with EHCI (480 Mbps) and OHCI (12 Mbps, 1.5 Mbps) controllers for high-, full-, and low-speed transactions. An EEPROM connected via I²C has been added to enable optional features and configurable settings.


[TODO] - add schematic

This part of the schematic has been highlighted in green on the board:
![board-3d-pcie-bridge](images/board-3d-pcie-bridge.png)

### eMMC memory with controller

The USB2244 is connected to a Pericom PCIe-to-USB bridge, acting as a USB 2.0-to-eMMC controller for Kingston’s EMMC16G-MW28-01E10, with a Microchip 24AA04T-I/OT EEPROM for optional configuration. The eMMC is powered directly from the M.2 3.3V rail, eliminating the need for an LDO. The eMMC interface uses D0–D8, CMD, and CLK lines, with 49.9kΩ pull-ups on CMD and data lines. The EEPROM is connected via I²C (SCL, SDA) with 4.7kΩ pull-ups, storing configuration settings for the USB controller. This setup provides high-speed eMMC access over USB in an M.2 form factor.

![M2SmartHome-emmc](images/M2SmartHome-emmc.svg)

![board-3d-eMMC](images/board-3d-eMMC.png)

### micro SD card reader and controller

The USB2244 controller interfaces with a Hirose HRS_DM3AT-SF-PEJM5 push-in microSD card slot for USB-to-microSD storage access, with a Microchip 24AA04T-I/OT EEPROM for configuration storage. The microSD card is powered by the internal 3.3V regulator of the USB2244. The SD interface utilizes CLK, CMD, and D0–D3 lines, with 49.9kΩ pull-ups on CMD and data lines for stable operation. The EEPROM is connected via I²C (SCL, SDA) with 4.7kΩ pull-ups, allowing the USB2244 to load stored device settings at startup.

![M2SmartHome-sd-card](images/M2SmartHome-sd-card.svg)

![board-3d-uSD](images/board-3d-uSD.png)

### Thread radio

The Silicon Labs EFR32MG21B020F1024IM32-B is a 802.15.4 Thread radio SoC, providing wireless connectivity, while the Silicon Labs CP2102N-A02-GQFN20 acts as a USB-to-UART bridge for communication with a host system. The EFR32MG21 is powered from the M.2 3.3V rail, with its radio interface using an external antenna for Thread communication. The CP2102N is connected via USB 2.0 (D+, D-) to the host via PCIe USB bridge. 

![M2SmartHome-thread-or-zigbee](images/M2SmartHome-thread-or-zigbee.svg)

![board-3d-thread](images/board-3d-thread.png)

### WiFi radio

The Realtek RTL8188FTV-VC-CG is a WiFi 802.11b/g/n 2.4GHz radio SoC, providing wireless connectivity. It is powered from the M.2 3.3V rail and interfaces with the host system via a USB 2.0 connection. The RF section is connected to an external antenna. 

![M2SmartHome-wifi](images/M2SmartHome-wifi.svg)

![board-3d-wifi](images/board-3d-wifi.png)

## Board design

Board dimensions
Board renders

![Render 3](images/M2SmartHome_cc9c86150_render_3.png)
![Render 4](images/M2SmartHome_cc9c86150_render_4.png)

##Manufacturing

Board has been manufactured 

Add stackup
Add impedance 
Board photos

## Board bring up 

Photos inside PC
Describe what works what not

### PCie USB bridge


### eMMC memory

### uSD reader

### Thread radio

### WiFi radio




### Firmware

reguirements:
- USB devices not detachable
- custom description






## Repository Structure

This repository contains the following directories:

- `hardware-electronics` - Kicad 8 project (schematic, board and libraries) 