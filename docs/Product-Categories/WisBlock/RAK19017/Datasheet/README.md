---
rak_desc: Provides comprehensive information about your RAK19017 to help you use it. This information includes technical specifications, characteristics, and requirements, and it also discusses the device components.
rak_img: /assets/images/wisblock/rak19017/RAK19017.png
tags:
  - datasheet
  - wisblock
  - RAK19017
prev: ../Overview/
next: false
---

# RAK19017 WisBlock PoE Power Slot Module Datasheet

## Overview

### Description

RAK19017 is a WisBlock POE Power Slot Module that has an Ethernet connector with POE capability (power supply only, no Ethernet connection capability) and a reset button. It is compatible with the WisBlock Base board with Power Slot.

RAK19017 WisBlock POE module is a power board that is designed based on Ag99005 MT from Silver. The Ag9905MT Power-over-Ethernet (PoE) modules are designed to extract power from a conventional twisted pair Category 5 Ethernet cable, conforming to the IEEE 802.3af PoE standard. The Ag9905MT signature and control circuit provides the PoE compatibility signature required by the Power Sourcing Equipment (PSE) before applying up to 9&nbsp;W power to the port. The Ag9905 MT provides a Class 0 signature. The DC/DC converter operates over a wide input voltage range and provides a regulated output. The DC/DC converter also has built-in short-circuit output protection.

### Features

- POE Power Module (power supply only, no Ethernet connection capability)
- 36&nbsp;V to 57&nbsp;V Input voltage range
- Short-circuit protection and Over temperature protection
- Compact size, the minimum size is: 30 x 50&nbsp;mm

## Specifications

### Overview


<rk-img
  src="/assets/images/wisblock/rak19017/datasheet/top-bottom-view.png"
  width="90%"
  caption="RAK19017 WisBlock Power Module top and bottom view"
/>


#### Mounting

The RAK19017 module can be mounted on the power slot of the WisBlock Base board. **Figure 2** shows the mounting mechanism of the RAK19017 on a WisBlock Base module with a power slot, such as the RAK19010.

:::warning ⚠️ WARNING

RAK19017 **only** supports WisBlock Base boards with Power Slot. It is not compatible with other WisBlock Base boards.

:::

<rk-img
  src="/assets/images/wisblock/rak19017/datasheet/mounting-mechanism.png"
  width="60%"
  caption="RAK19017 mounting mechanism on a WisBlock Base board with Power Slot"
/>

### Hardware

The hardware specification is categorized into six parts. It discusses the interfacing, pinouts, and their corresponding functions and diagrams of the module. It also covers the electrical, mechanical, and environmental characteristics that include the tabular data of the functionalities and standard values of the RAK19017 WisBlock PoE Power Slot Module.

#### Interfaces

RAK19017 WisBlock PoE Power Slot Module provides the following interfaces:

* PoE Ethernet Connector (with two LEDs controllable by WisBlock Core)
* Reset button

::: tip 📝 NOTE
RAK19017 doesn't have a USB connector. So when RAK19017 is used together with WisBlock Base board with power slot, it is not possible to program the core (unless via SWD pins using external tools like Jlink and RAKDAP1). If you want to program the WisBlock Core via USB, you need the RAK5804. Then you can use the USB connector of RAK5804 to program the WisBlock Core.
:::

<br>

<rk-img
  src="/assets/images/wisblock/rak19017/datasheet/label.png"
  width="55%"
  caption="RAK19017 part labels"
/>

##### RESET Push Button

The Reset Push Button shown in [**Figure 3**](#interfaces) is connected to the MCU module. When pushed, it resets the MCU.

##### LEDs

The two LEDs in the Ethernet connector can be controlled by the WisBlock Core.

- **Green LED** - Controlled by MCU of WisBlock Core defined by the user via `PIN_LED1`.
- **Yellow LED** -  Controlled by MCU of WisBlock Core defined by the user via `PIN_LED2`.

#### Pin Definition

The RAK19017 module has a 40-pin WisConnector that is compatible with the WisBlock Power Slot. The pin order of the connector and the pinout definition is shown in **Figure 4**.

::: tip 📝 NOTE
VBAT, 3V3, RESET, LED1, LED2, and GND have connected to WisBlock 40-pin connector.
:::

<rk-img
  src="/assets/images/wisblock/rak19017/datasheet/pinout.png"
  width="65%"
  caption="RAK19017 pinout diagram"
/>


#### Electrical Characteristics

##### Absolute Maximum Ratings

The Absolute Maximum Ratings of the device are shown in the table below. The stress ratings are the functional operation of the device.

:::warning ⚠️WARNING
1. If the stress rating goes above what is listed, it may cause permanent damage to the device.
2. Exposure to maximum rating conditions may affect the device reliability.
:::

| **Ratings**                   | Maximum Value | Unit |
| ----------------------------- | ------------- | ---- |
| Power In Voltage (**VCC-IN**) | 36 to 57      | V    |

#### Mechanical Characteristic

##### Board Dimensions

The mechanical dimensions of the RAK19017 module are shown in **Figure 5**.

<rk-img
  src="/assets/images/wisblock/rak19017/datasheet/mechanical-dimensions.png"
  width="100%"
  caption="RAK19017 mechanical dimensions"
/>

##### WisConnector PCB Layout

<rk-img
  src="/assets/images/wisblock/rak19017/datasheet/wisconnector-pcb.png"
  width="90%"
  caption="WisConnector PCB footprint and recommendations"
/>

#### Environmental Characteristics

The table below lists the operation and storage temperature requirements of RAK19017:

| **Parameter**                 | **Minimum** | **Typical** | **Maximum** |
| ----------------------------- | :---------: | :---------: | :---------: |
| Operational temperature range | –35&nbsp;ºC | +25&nbsp;ºC | +75&nbsp;ºC |
| Extended temperature range    | –40&nbsp;ºC | +25&nbsp;ºC | +80&nbsp;ºC |
| Storage temperature range     | –40&nbsp;ºC | +25&nbsp;ºC | +80&nbsp;ºC |

#### Schematic Diagram

**Figure 7** shows the schematic of the WisBlock PoE Power Slot Module.

<rk-img
  src="/assets/images/wisblock/rak19017/datasheet/schematic.png"
  width="100%"
  caption="RAK19017 schematic"
/>