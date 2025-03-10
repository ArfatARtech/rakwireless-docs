---
rak_desc: Provides comprehensive information about your RAK4631-R to help you use it. This information includes technical specifications, characteristics, and requirements, and it also discusses the device components.
rak_img: /assets/images/wisblock/rak4631-r/RAK4631-R.png
prev: ../DFU/
next: false
tags:
  - datasheet
  - wisblock
  - RAK4631-R
certifications:
  - [CE, https://downloads.rakwireless.com/LoRa/RAK4630/Certification/RAK4630_RAK4631_CE_Certification.zip]
  - [FCC, https://downloads.rakwireless.com/LoRa/RAK4630/Certification/RAK4630_RAK4631_FCC_Certification.zip]
  - [KCC, https://downloads.rakwireless.com/LoRa/RAK4630/Certification/RAK4630_RAK4631_KC_Certification.pdf]
  - [RCM, https://downloads.rakwireless.com/LoRa/RAK4630/Certification/RAK4630_RCM_Certification.pdf]
  - [REACH, https://downloads.rakwireless.com/LoRa/RAK4630/Certification/RAK4630_RAK4631_REACH_Report.pdf]
  - [RoHS, https://downloads.rakwireless.com/LoRa/RAK4630/Certification/RAK4630_RAK4631_RoHS_Report.pdf]
---

# RAK4631-R WisBlock LPWAN Module Datasheet


## Overview

### Description

The RAK4631-R WisBlock Core module is a RAK4630 stamp module with an expansion PCB and connectors compatible with WisBlock Base. It allows an easy way to access the pins of the RAK4630 module to simplify development and testing processes.

The module itself comprises a RAK4630 as its main component. The RAK4630 is a combination of an nRF52840 MCU and an SX1262 LoRa chip. It features ultra-low power consumption of 2.0&nbsp;uA during sleep mode, high LoRa output power up to 22&nbsp;dBm during a transmission mode, and the BLE interface with output power up to 4&nbsp;dBm.

Also, it complies with LoRaWAN 1.0.3 protocols and supports LoRa point-to-point communication. The RF communication characteristic of the module (LoRa + BLE) makes it suitable for a variety of applications in the IoT field, such as home automation, sensor networks, building automation, personal area networks applications (health/fitness sensors, and monitors, etc.).


### Features

- TCXO crystal for LoRa chip
- I/O ports: UART/I2C/GPIO/USB
- SPI pins and optional NFC interface are accessible using WisBlock IO module
- Temperature range: -40&nbsp;°C to +85&nbsp;°C
- Supply voltage: 2.0 ~ 3.6&nbsp;V
- Low-Power Wireless Systems with 7.8&nbsp;KHz to 500&nbsp;KHz Bandwidth
- Ultra-Low Power Consumption 2.0&nbsp;uA in sleep mode
- LoRa PA Boost mode with 22&nbsp;dBm output power
- BLE5.0 (Tx power -20 to +4&nbsp;dBm in 4&nbsp;dB steps)
- Serial Wire Debug (SWD) interface
- Module size: 20 x 30&nbsp;mm
- Chipset: Nordic nRF52840, Semtech SX1262
## Specifications

### Overview

The overview covers the RAK4631-R board overview and the mounting mechanics of the board into the baseboard.

#### Board Overview

<rk-img
  src="/assets/images/wisblock/rak4631/datasheet/rak4631overview.png"
  width="65%"
  caption="RAK4631-R Overview"
/>

<rk-img
  src="/assets/images/wisblock/rak4631/datasheet/rak4630-rak4631.png"
  width="30%"
  caption="RAK4630 in RAK4631-R WisBlock Core"
/>



#### Mounting Sketch

The RAK4631-R module is designed to work with Wisblock Base Boards. **Figure 3** shows how a RAK4631-R module should be mounted on top of the WisBlock RAK5005-O Base Board.

<rk-img
  src="/assets/images/wisblock/rak4631/datasheet/mounting-sketch.png"
  width="50%"
  caption="RAK4631-R Mounting Sketch"
/>

### Hardware

The hardware specification is categorized into three parts. It covers the RF, electrical, and mechanical parameters that include the tabular data of the functionalities and standard values of the RAK4631-R WisBlock LPWAN Module.

#### Chipset
| Vendor          | Part number        |
| --------------- | ------------------ |
| Nordic, Semtech | nRF52840, SX1262   |

#### RF Characteristics

The RAK4631-R module supports the LoRaWAN bands shown in the table below. When buying a RAK4631-R module, pay attention to specifying the correct core module RAK4630 H/L for your region, in which H stands for high-frequency regions and L for low-frequency regions.

:::tip 📝 NOTE
Detailed information about the RAK4631-R BLE and LoRa antenna can be found on the [antenna datasheet](https://downloads.rakwireless.com/LoRa/WisBlock/Accessories/).
:::

| Region        | Frequency (MHz)  | Core Module |
| ------------- | ---------------- | ----------- |
| India         | IN865            | RAK4630(H)  |
| Europe        | EU868            | RAK4630(H)  |
| Europe        | EU433            | RAK4630(L)  |
| North America | US915            | RAK4630(H)  |
| Canada        | US915            | RAK4630(H)  |
| Australia     | AU915            | RAK4630(H)  |
| Korea         | KR920            | RAK4630(H)  |
| Asia          | AS923            | RAK4630(H)  |
| China         | CN470 <br> CN779 | RAK4630(L)  |

#### Electrical Characteristics

##### Power Consumption

| **Item**                     | **Power Consumption** | **Condition**                 |
| ---------------------------- | --------------------- | ----------------------------- |
| Tx mode LoRa @20&nbsp;dBm    | 12&nbsp;5mA           | LoRa @ PA_BOOST&BT sleep      |
| Tx mode LoRa @17&nbsp;dBm    | 92&nbsp;mA            | LoRa @ PA_BOOST&BT sleep      |
| Tx mode BT@4&nbsp;dBm        | 9&nbsp;mA             | BT Tx mode & Lora sleep       |
| Rx mode LoRa @37.5&nbsp;kbps | 17&nbsp;mA            | LoRa @ Receive mode &BT sleep |
| Rx mode BT@2&nbsp;Mbps       | 11.5&nbsp;mA          | BT Rx mode & Lora sleep       |
| Sleep mode                   | 2.0&nbsp;uA           | LoRa&BT sleep                 |


##### Absolute Maximum Ratings

| **Symbol** | **Description**               | **Min.** | **Nom.** | **Max.** | **Unit** |
| ---------- | ----------------------------- | -------- | -------- | -------- | -------- |
| VBAT_SX    | LoRa chip supply voltage      | -0.5     | -        | 3.9      | V        |
| VBAT_SX_IO | LoRa chip supply for I/O pins | -0.5     | -        | 3.9      | V        |
| VDD_NRF    | MCU power supply              | -0.3     | -        | 3.9      | V        |
| VBUS       | USB supply voltage            | -0.3     | -        | 5.8      | V        |
| VBAT_NRF   | MCU high voltage power supply | -0.3     | -        | 5.8      | V        |


##### Recommended Operating Conditions

| **Symbol** | **Description**                    | **Min.** | **Nom.** | **Max.** | **Unit** |
| ---------- | ---------------------------------- | -------- | -------- | -------- | -------- |
| VBAT_SX    | SX1262 supply voltage              | 2.0      | 3.3      | 3.7      | V        |
| VBAT_SX_IO | SX1262 supply for I/O pins         | 2.0      | 3.3      | 3.7      | V        |
| VDD_NRF    | NRF52840 power supply              | 2.0      | 3.3      | 3.6      | V        |
| VBUS       | VBUS USB supply voltage            | 4.35     | 5.0      | 5.5      | V        |
| VBAT_NRF   | NRF52840 high voltage power supply | 2.5      | -        | 5.5      | V        |

##### Schematic Diagram

<rk-img
  src="/assets/images/wisblock/rak4631/datasheet/schematic.png"
  width="100%"
  caption="RAK4631-R Schematic Diagram"
/>

- **WisConnector**: The breakout module allows the RAK4630 stamp module pinout to be transferred by the board-to-board WisConnector.

- **WisConnector Pin Order**: The pin order of the WisConnector is located in the bottom layer of the module.

- **Core Module**: The breakout module itself has a RAK4630 at its core, and it shows the core module pin and connection information. By default, the NFC function is disabled to conserve the low power characteristic.

- **SWD Interface**: The breakout module exposes an SWD debug interface. Additionally, the RST pin is used for resetting the core module RAK4630.

- **Power Up Automatic Reset**: The breakout module has a power-up automatic reset circuit, and the schematic shows the automatic reset mechanism. This module also can be reset through the WisBlock Base reset pin.

##### Setup of the SX1262

Information to write custom firmware for the RAK4630.  This shows the internal connection between the RAK4630 and required information when initializing the SX1262 LoRa Transceiver.

| nRF52840 GPIO	| SX1262 pin | function                          |
| ------------- | ---------- | --------------------------------- |
| P1.10         | NSS        | SPI NSS                           |
| P1.11         | SCK        | SPI CLK                           |
| P1.12         | MOSI       | SPI MOSI                          |
| P1.13         | MISO       | SPI MISO                          |
| P1.14         | BUSY       | BUSY signal                       |
| P1.15         | DIO1       | DIO1 event interrupt              |
| P1.06         | NRESET     | NRESET manual reset of the SX1262 |

Important for successful SX1262 initialization:
- Setup DIO2 to control the antenna switch
- Setup DIO3 to control the TCXO power supply
- Setup the SX1262 to use it's DCDC regulator and not the LDO
- RAK4630 schematics show GPIO P1.07 connected to the antenna switch, but it should not be initialized, as DIO2 will do the control of the antenna switch

#### Mechanical Characteristics

##### Board Dimensions

<rk-img
  src="/assets/images/wisblock/rak4631/datasheet/board-dimensions.jpg"
  width="35%"
  caption="Mechanical Dimensions"
/>

##### WisConnector PCB Layout

<rk-img
  src="/assets/images/wisblock/rak4631/datasheet/FxxS1003K6M.png"
  width="100%"
  caption="WisConnector PCB footprint and recommendations"
/>



## Certification

<rk-certifications :params="$page.frontmatter.certifications" />

