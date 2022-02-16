---
rak_desc: Provides comprehensive information about your RAK12019 to help you use it. This information includes technical specifications, characteristics, and requirements, and it also discusses the device components.
rak_img: /assets/images/wisblock/rak12019/overview/RAK12019_home.png
tags:
  - datasheet
  - wisblock
  - RAK12019
prev: ../Quickstart/
next: false
---

# RAK12019 WisBlock UV Sensor Datasheet

## Overview

### Description

The RAK12019 is an Ambient Light sensor (ALS) or Ultraviolet Light Sensor (UVS), which is part of the RAKwireless WisBlock sensor series. The measured ambient light intensity and ultraviolet index are interfaced via the I2C bus making it immune to electrical noises, unlike its analog output counterpart. This module utilizes the LTR-390UV-01 sensor from Lite-On.


### Features

 - Ambient Light Sensor (ALS) or Ultraviolet Light Sensor (UVS)
 - I2C interface capable of Standard mode @100&nbsp;kHz or Fast mode @400kHz communication 1.8&nbsp;V logic compatible
 - Very low power consumption with sleep mode capability
 - 13 to 20 bits effective resolution
 - Wide dynamic range of 1:18,000,000 with linear response
 - Close to human eye spectral response
 - Automatic rejection for 50&nbsp;Hz/60&nbsp;Hz lighting flicker
 - Operating voltage ranges: 1.7&nbsp;V to 3.6&nbsp;V
 - Operating temperature ranges: -40 to +85&nbsp;ºC
 - Built-in temperature compensation circuit
 - Programmable interrupt function for ALS, UVS with upper and lower thresholds
 - RoHS and Halogen-free compliant 
 - Module Size: 10&nbsp;mm x 10&nbsp;mm

## Specifications

### Overview 

#### Mounting

The RAK12019 WisBlock UV Sensor can be mounted to the IO slot of the WisBlock Base board. **Figure 1** shows the mounting mechanism of the RAK12019 on a WisBlock Base board, such as the [RAK5005-O](https://store.rakwireless.com/products/rak5005-o-base-board).

<rk-img
  src="/assets/images/wisblock/rak12019/datasheet/mounting.png"
  width="60%"
  caption="RAK12019 WisBlock UV Sensor Mounting"
/>


### Hardware

The hardware specification is categorized into four parts. It shows the pinouts and their corresponding functions and diagrams. It also covers the electrical and mechanical parameters that include the tabular data of the functionalities and standard values of the RAK12019 WisBlock UV Sensor.

#### Pin Definition

The RAK12019 WisBlock UV Sensor comprises a standard WisIO connector. The WisIO connector allows the RAK12019 module to be mounted to a WisBlock baseboard, such as RAK5005-O. The pin order of the connector and the pinout definition is shown in **Figure 2**.

::: tip 📝 NOTE
- **I2C** related pin, **INT** pin, **3V3_S** and **GND** are connected to WisIO connector
:::

 <rk-img
  src="/assets/images/wisblock/rak12019/datasheet/RAK12019_Pinouts.svg"
  width="60%"
  caption="RAK12019 WisBlock UV Sensor Pinout"
/>
  

#### Electrical Characteristics

##### Power Supply Ratings

| Symbol     | Description                     | Condition                                               | Min. | Nom. | Max. | Unit |
| ---------- | ------------------------------- | ------------------------------------------------------- | ---- | ---- | ---- | ---- |
| 3V3_S      | LTR-390UV-01 Operating  Voltage | Input voltage must within this range                    | 2.5  | 3.3  | 3.6  | V    |
| Isd        | Shut down current               | VDD is 2.8 V                                            | -    | 1    | -    | uA   |
| ALS        | ALS Active Mode Current         | VMax. duty cycle, Vdd=2.8V, Gain 3x                     | -    | 110  | -    | uA   |
| UVS        | UVS Active Mode Current         | Max. duty cycle, Vdd=2.8V                               | -    | 100  | -    | uA   |
| WakeupTime | Wakeup Time from Standby        | From Standby to Active mode where measurement can start | -    | 5    | 10   | ms   |

#### Mechanical Characteristics

##### Board Dimensions

**Figure 3** shows the dimensions and the mechanical drawing of the RAK12019 module.

 <rk-img
  src="/assets/images/wisblock/rak12019/datasheet/mechanical-drawing.png"
  width="60%"
  caption="RAK12019 WisBlock UV Sensor Dimensions"
/>


##### WisConnector PCB Layout

<rk-img
  src="/assets/images/wisblock/rak12019/datasheet/pcb-layout.png"
  width="100%"
  caption="WisConnector PCB Footprint and Recommendations"
/>


#### Schematic Diagram

<rk-img
  src="/assets/images/wisblock/rak12019/datasheet/schematic.png"
  width="100%"
  caption="RAK12019 WisBlock UV Sensor Schematic Diagram"
/>




