# M2SmartHome

![M2SH Photo](images/M2SH-photo.jpeg)

## Overview

Setting up a smart home hub, such as running Home Assistant, often requires hardware with sufficient performance and connectivity options. Many existing solutions, like Raspberry Pi, may be insufficient for advanced automation tasks due to a low-power CPU or a slow microSD card on which the OS is installed. A good alternative could be an x86 mini PC, but these often lack expansion ports.  

M2SmartHome is an add-on card that operates on PCIe x1 and can be installed in any M.2 2280 Key M-equipped device. By integrating multiple essential components into a single device, it eliminates the need for external adapters and additional hardware.  

The device is equipped with onboard eMMC memory, an SD card reader, WiFi 802.11n 2.4GHz radio (RTL8188), and a Thread radio (EFR32) from Silicon Labs. Once installed in an M.2 slot, it provides both storage for the operating system and enhanced connectivity, making it an ideal choice for smart home setups.


## Features

- **Form Factor**: M.2 2280
- **Interface**: M.2 edge conenctor PCIe x1 
- **Storage**: Onboard eMMC, SD card reader
- **Wireless Connectivity**:
  - **WiFi**: 802.11n 2.4GHz (Realtek RTL8188)
  - **Thread Radio**: EFR32MG21 (Silicon Labs)


## Block diagram

![Block diagram](images/M2SmartHome_block_diagram.png)


### PCie to USB bridge

Diodes Inc. (Pericom) PI7C9X440SLBFDE PCIe 1.0 x1 4x USB 2.0 bridge



![board-3d-pcie-bridge](images/board-3d-pcie-bridge.png)

### eMMC memory with controller

Kingston EMMC16G-MW28-01E10 eMMC flash memory
Microchip USB2244 controller
Microchip 24AA04T-I/OT serial EEPROM for storing device configuration to be loaded during startup

![M2SmartHome-emmc](images/M2SmartHome-emmc.svg)

![board-3d-eMMC](images/board-3d-eMMC.png)

### micro SD card reader and controller

Hirose HRS_DM3AT-SF-PEJM5 push-in micro SD card slot
Microchip USB2244 controller
Microchip 24AA04T-I/OT serial EEPROM for storing device configuration to be loaded during startup

![M2SmartHome-sd-card](images/M2SmartHome-sd-card.svg)

![board-3d-uSD](images/board-3d-uSD.png)

### Thread radio

Silicon Labs EFR32MG21B020F1024IM32-B 802.15.4 thread radio SOC
Silicon Labs CP2102N-A02-GQFN20 USB UART

![M2SmartHome-thread-or-zigbee](images/M2SmartHome-thread-or-zigbee.svg)

![board-3d-thread](images/board-3d-thread.png)

### WiFi radio

Realtek RTL8188FTV-VC-CG wifi radio SOC

![M2SmartHome-wifi](images/M2SmartHome-wifi.svg)

![board-3d-wifi](images/board-3d-wifi.png)

## Board design

Highlight certain regions
Board dimensions
Board renders

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