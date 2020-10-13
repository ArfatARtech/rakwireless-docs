---
prev: ../../Overview/
tags:
  - RAK4200 Breakout Board
---

# Quick Start Guide

## Prerequisites

### What do you need?

Before going through the step in the installation guide of the RAK4200 WisDuo LPWAN Module, make sure to prepare the necessary items listed below:

#### Hardware Tools

1. RAK4200 WisDuo LPWAN Module
2. Windows PC
3. USB to TTL adapter


#### Software Tools

- [RAK4200 Specification Manual](https://downloads.rakwireless.com/LoRa/RAK4200/Hardware-Specification/RAK4200_Module_Specifications_V1.4.pdf)
- [RAK Serial Port Tool](https://downloads.rakwireless.com/en/LoRa/Tools/RAK_SERIAL_PORT_TOOL_V1.2.1.zip)
- [RAK Device Firmware Upgrade (DFU) Tool](https://downloads.rakwireless.com/LoRa/Tools/RAK_Device_Firmware_Upgrade_tool/)
- [RAK4200 Firmware](https://downloads.rakwireless.com/en/LoRa/RAK4200/Firmware/)


#### Definition of Terms

##### List of Acronyms

| Acronym | Meaning                       |
| ------- | ----------------------------- |
| ABP     | Activation By Personalization |
| BLE     | Bluetooth Low Energy          |
| DFU     | Device Firmware Upgrade       |
| EUI     | Extender Unique Identifier    |
| JTAG    | Joint Test Action Group       |
| LoRa    | Long Range                    |
| OTAA    | Over The Air Activation       |
| TTN     | The Things Network            |

## Product Configuration

### Connecting to the RAK4200 Console

During the configuration of the module through the AT commands, it is possible to read the console outputs. You can connect to the console of the RAK4200 module: through the UART interface.

#### Connect to the RAK4200

In this document, a RAK4200 module is used for demonstration. Use a USB to TTL module to connect to the module. In case the RAK4200 is mounted on an evaluation board or on a customized PCB then use the appropriate interface to connect to the Serial port.

1. Connect the RAK4200 to the serial port of a general-purpose (e.g.: USB port) using a USB to TTL adapter, as shown in the figure.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/module-connection.png"
  width="70%"
  caption="RAK4200 module connection"
/>

2. Any serial communication tool will work, but it is recommended to use the RAK Serial Port Tool that can be downloaded from [here](https://downloads.rakwireless.com/en/LoRa/Tools/RAK_SERIAL_PORT_TOOL_V1.2.1.zip).

3. Configure the serial communication tool by selecting the proper port of the computer UART port and configure the link as: 115200 bauds, 8 bits, no parity bit, and 1 stop bit.

4. The RAK4200 console output can now be read in the RAK Serial Port Tool as shown in figure below.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/serial-port-tool.png"
  width="50%"
  caption="RAK serial port tool connected to RAK4200"
/>

#### Configure RAK4200

In order to connect the RAK4200 module to a LoRa-P2P connection or a LoRaWAN network, the module must be configured and LoRa parameters must be set by sending AT commands through the UART interface.

Connect the RAK4200 module to the computer as described in the previous section. Using the Serial communication tool then is possible to send commands to the RAK4200, e.g.: sending the `at+version` will return and display the current firmware version as shown in the figure below. For more supported commands, refer to [AT Commands for RAK4200](../AT-Command-Manual/).

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/at-version-command-response.png"
  width="50%"
  caption="at+version command response"
/>


### Connecting to The Things Network (TTN)

This section shows how to connect the RAK4200 module to The Things Network (TTN™) platform.
As described in the TTN’s website:
"The engine of The Things Network is our technology - a robust yet flexible and enterprise-ready LoRaWAN network server stack. Our stack caters to the needs of demanding LoRaWAN deployments, from covering the essentials to advanced security configurations and device life cycle management. Backed by SLAs to meet your availability requirements, facilitated by our team of support engineers"

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK4200-ttn.png"
  width="80%"
  caption="RAK4200 in the context of the TTN"
/>

As shown in figure above, the RAK4200 module is one of the devices located on the left side. In the context of an IoT solution, the objective is to deploy devices to sense the relevant process variables and transmit the data to the backend servers located in the cloud. The data will be processed and integrated as part of a larger solution that, ultimately, could generate efficiency, traceability, predictability capacity among others.

The RAK4200 module can be part of this ecosystem, and the objective of this section is to demonstrate how simple is to send data to TTN using LoRaWAN. Users must be aware that to achieve this, the RAK4200 must be located inside of coverage of a LoRaWAN gateway.

In summary, these are the requirements:

- Have an account on the TTN website.
- Have access to a LoRaWAN gateway subscribed to the TTN. (The frequency band set for the RAK4200 needs to be consistent with the frequency band of the gateway.)
  [Add gateway configuration TTN network server document link]()
- The "serial port tool" provided by RAKWireless.
- The RAK4200 module.

::: tip 📝 NOTE
The frequency band used in this example is EU868 which is supported by the high-frequency version of the RAK4200 module.
:::

The steps for sending data to the TTN platform from a RAK4200 module can be summarized as:

- Sign up to TTN platform and login to the TTN’s platform.
- Create a new Application.
- Register a new device in the platform
- Configure the Join Mode
   - OTAA mode on the platform
   - OTAA mode on the RAK4200 module
   - ABP mode on the platform
   - ABP mode on the RAK4200 module
   - Send data from the module and receive it at the platform

In the following sections, it will be explained in detail each of these steps. The user must choose to use ABP or OTAA mode to register the device to the network server.

#### Registering the RAK4200 to TTN

To register the RAK4200 to TTN execute the following steps:

##### Login to the Things Network platform

Access to the URL: [TTN](https://www.thethingsnetwork.org/), login into the platform, please go to the “Console” section (by clicking on the Console icon located at the top-right corner of the page). You should see an interface similar to figure below.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console.png"
  width="100%"
  caption="TTN’s Console"
/>

##### Create a new Application

Choose the “APPLICATIONS” option.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console-application-section.png"
  width="100%"
  caption="TTN’s Console, Application section"
/>

Click on “add application”:

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console-new-application.png"
  width="100%"
  caption="TTN’s Console, new application form"
/>

Fill in the correct contents in the “Add application form”.

- Application ID: should be in lower case, and it must be the unique ID on TTN network.
- Description: A human-readable description of the new app
- Application EUI: Is automatically generated by TTN
- Handler registration: Select the handler you want to register this application to.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-completed-add-application.png"
  width="100%"
  caption="TTN's Add Application Form"
/>

To finish, click on the “Add application” button at the bottom of this page, the following page will appear:

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console-new-application-created.png"
  width="100%"
  caption="TTN’s Console, a new application created"
/>

##### Register a new device in the platform

In the “Application details” page, find the “DEVICES” section by the middle of this page

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-devices-1.png"
  width="100%"
  caption="TTN's DEVICES section at the Application details page"
/>

Click on “register device”, a “register device form” will appear.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console-5.png"
  width="100%"
  caption="TTN’s Console, new Device form."
/>

In this form, the device ID must be unique for the application and must be completed with a lower case, alphanumeric characters. The rest of the parameters in the form are very important for the LoRaWAN protocol:

- Device EUI
- Application Key
- Application EUI

The TTN platform can generate these parameters randomly by leaving those fields empty or the user can enter already existing values.

Press the “Register” button at the bottom of this page to finish the process. The registration results will appear summarized as in figure below.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console-6.png"
  width="100%"
  caption="TTN’s Console, the results of creating a new Device."
/>

#### LoRaWAN Join Mode

The LoRaWAN specification defines that to join in a LoRaWAN network, each end-device has to be personalized and activated. Activation can be done either via Over-The-Air-Activation (OTAA) or via Activation-By-Personalization (ABP). In OTAA the end-device previously personalized is activated when is deployed or reset. In ABP, personalization and activation are done as a single step.

##### Join in OTAA mode

###### Configure the OTAA mode on the TTN platform

As shown in figure below, the default activation mode in TTN is the OTAA mode. Therefore, no further actions are required on the platform side.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console-6.png"
  width="100%"
  caption="TTN’s Console, the results of creating a new Device."
/>

Three parameters from TTN setup are used to configure the RAK4200: “Device EUI”, “Application EUI” and “App Key”.

###### Configure the OTAA mode on the RAK4200 module

RAK4200 complies with LoRaWAN 1.0.2, by default the LoRa join mode is OTAA and the LoRa Class is Class A.

To setup the RAK4200 module to join the TNN using OTAA start by connecting the RAK4200 module to the Computer and open the RAK Serial Port Tool, wait for the communication to start. It is recommended to test the serial communication by sending an AT command as “at+get_config=lora:status” or “at+version”.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool.png"
  width="50%"
  caption="RAK Serial Port Tool connected to a RAK4200"
/>

As an example, the following parameters will be configured in RAK4200:

- LoRa join mode: OTAA
- LoRa class: Class A
- LoRa region: EU868
- Device EUI: 5e9d1e0857cf25f1 (from TTN registration)
- Application EUI: 5e9d1e0857cf25f1 (from TTN registration)
- Application Key: f921d50cd7d02ee3c5e6142154f274b2 (from TTN registration)

1. Set the LoRa join mode to OTAA

Type command: 
```
at+set_config=lora:join_mode:0
```

2. Set the LoRa Class to Class A

Type command: 

```
at+set_confing=lora:class:0
```

3. Set the frequency/region

RAK4200 Supported frequency plan includes:

- IN865 (India)
- EU868 (Europe)
- US915(United States)
- AU915(Australia)
- KR920(Korea)
- AS923(Asia)

**Example**: For Europe Type command:
```
at+set_config=lora:region:EU868
```
::: tip 📝 NOTE
Remember that the device frequency shall be in the same band as the Gateway.
:::

4. Set the Device EUI

Get the Device EUI number from TNN register

Type command:
```
at+set_config=lora:dev_eui:5e9d1e0857cf25f1`
```
5. Set the Application EUI

Get the Application EUI number from the TNN register.

Type command:
```
at+set*config=lora:app* eui:5e9d1e0857cf25f1
```

6. Set the Application Key

Get the Application Key from the TNN register.

Type command: 
```
at+set_config=lora:app_key:f921d50cd7d02ee3c5e6142154f274b2
```

7. Saving RAK4200 parameters

Reset the RAK4200 for saving the parameters.

The figure below summarizes the set of commands sent over the console for setting the OTAA mode on the RAK4200

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK4200-lora-param.png"
  width="50%"
  caption="RAK4200 LoRa parameters configuration over the RAK Serial Port Tool"
/>

8. Command the RAK4200 to join in OTAA mode

Type command:
```
at+join
```

* After 5 or 6 seconds, if the request was successfully received by a LoRa gateway, then “OK Join Success” messages will be shown in the console (see figure below).

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK4200-example-1.png"
  width="50%"
  caption="RAK4200 example of sending data to the TTN, in this case, the string 123456890 over port 2"
/>

9. Send data from RAK4200 to TTN

Example: To send the string 123456789 over LoRa port 2, type command: 
```
at+send=lora:2:1234567890
```

* The data will appear in the TTN’s web (see figure below).

<rk-img
src="/assets/images/wisduo/rak4200-module/quickstart/ttn-website-showing.png"
width="100%"
caption="TTN’s website showing the data received from RAK4200"
/>

##### Join in ABP Mode

###### Configure the ABP mode on the platform

As shown previously, the default activation mode in TTN is the OTAA mode. Therefore, no further actions are required on the platform side.

Three parameters from TTN setup are used to configure the RAK4200: “Device EUI”, “Application EUI” and “App Key”.

For joining TTN in ABP mode first it is needed to switch the activation method as ABP. This is done on the TTN’s website under the “Device Settings” page, as shown in figure below.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console-7.png"
  width="100%"
  caption="TTN Console, change the activation mode to ABP"
/>

As for the OTAA mode, three TTN’s parameters will be used to configure the RAK4200 for ABP mode: “Device Address”, “Network Session Key” and “App Session Key”(see figure below). These fields can be left empty in the form and TTN will complete them with random values, in other cases the user can complete them with specific values.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console-8.png"
  width="100%"
  caption="TTN Console, ABP mode’s parameters"
/>

After completing the mode change the device parameters will be summarized as in figure below.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-console-9.png"
  width="100%"
  caption="TTN Console, ABP mode configuration finalized"
/>

###### Configure the ABP mode on the RAK4200 module

RAK4200 complies with LoRaWAN 1.0.2, by default the LoRa join mode is OTAA and the LoRa Class is Class A.

To set up the RAK4200 module to join the TNN using ABP start by connecting the RAK4200 module to the Computer and open the RAK Serial Port Tool, wait for the communication to start. It is recommended to test the serial communication by sending an AT command as `at+get_config=lora:status` or `at+version`.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool-2.png"
  width="50%"
  caption="RAK Serial Port Tool connected to a RAK4200"
/>

As an example, the following parameters will be configured in RAK4200:

- LoRa join mode: ABP
- LoRa class: Class A
- LoRa region: EU868
- Device address: 26011af9 (from TTN registration)
- Network Session Key: c280cb8d1df688bc18601a97025c5488 (from TTN registration)
- Application Session Key: 4d42ec5caf97f03d833cdaf5003f69e1 (from TTN registration)

1. Set LoRa join mode to ABP

Type command: 
```
at+set_config=lora:join_mode:1
```

2. Set the LoRa Class to Class A

Type command: 
```
at+set_confing=lora:class:0
```

3. Set the Frequency/Region

RAK4200 Supported frequency plan includes:

- IN865 (India)
- EU868 (Europe)
- US915(United States)
- AU915(Australia)
- KR920(Korea)
- AS923(Asia)

**Example**: For Europe Type command:
```
at+set_config=lora:region:EU868
```
::: tip 📝 NOTE
Remember that the device frequency shall be in the same band as the Gateway.
:::
4. Set the Device Address

Get the Device Address from TNN register,

**Exammple**: To set the LoRa Device Address to “**26011af9**”, type command:
```
at+set_config=lora:dev_addr:26011af9
```

5. Set the Network Session Key

Get the Network Session Key from the TTN register.

**Example**: To set the LoRa Network Session Key to “**c280cb8d1df688bc18601a97025c5488**”, type command:
```
at+set_config=lora:nwks_key:c280cb8d1df688bc18601a97025c5488
```

6. Set the Application Key

Get the Application Key from the TTN register. 

**Example**: To set the Application Key to “**4d42ec5caf97f03d833cdaf5003f69e1**”, type command: 
```
at+set_config=lora:apps_key: 4d42ec5caf97f03d833cdaf5003f69e1
```

7. Saving RAK4200 parameters

Reset the RAK4200 for saving the parameters.

Figure 21, and Figure 14 summarizes the set of commands sent over the console for setting the OTAA mode on the RAK4200

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK4200-lora-param2.png"
  width="50%"
  caption="RAK4200 LoRa parameters configuration over the Serial Port Tool"
/>

8. Command the RAK4200 to join in ABP mode

Type command: 
```
at+join
```

::: tip 📝 NOTE
The ABP mode in LoRaWAN doesn’t require to join a network before sending a LoRaWAN package. But in order to keep the consistency of the internal states of the firmware of the RAK4200 module, it is still required to send at+join command in the ABP mode.
:::

Almost immediately after sending the command the “OK Join Success” should be replied in the console as shown in Figure 22.

9. Send data from RAK4200 to ChirpStack

**Example**: To send the string 123456789 over LoRa port 2, type command:
```
at+send=lora:2:1234567890
```

* The data will appear in the TTN’s web (see Figure 23)

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool-3.png"
  width="50%"
  caption="RAK Serial Port Tool, sending a message in ABP mode"
/>

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/ttn-website.png"
  width="100%"
  caption="TTN’s website with received data from RAK4200"
/>

### Connecting with ChirpStack

This section shows how to connect the RAK4200 module to the ChirpStack platform. As described in the ChripsStack’s website:

“The ChirpStack open-source LoRaWAN Network Server stack provides open-source components for LoRaWAN networks. Together they form a ready-to-use solution including a user-friendly web-interface for device management and APIs for integration.

The modular architecture makes it possible to integrate within existing infrastructures. All components are licensed under the MIT license and can be used for commercial purposes.”

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK4200-module.png"
  width="70%"
  caption="RAK4200 module in the context of the ChirpStack platform"
/>

The architecture of the ChirpStack platform is shown in Figure 24. Similar to the case of TTN, the RAK4200 module is located in the periphery and will transmit the data to the backend servers through a LoRa gateway. More information about this architecture can be found [here](https://www.chirpstack.io/).

In this document, it is assumed that users are using a RAK LoRa gateway, such as RAK7243. The gateway must be configured and registered previously to Chirpstack deployment. More information about that can be found [here](https://downloads.rakwireless.com/en/LoRa/).

::: tip 📝 NOTE
The frequency band used in this example is EU868 which is supported by the high-frequency version of RAK4200.
:::

And these are the steps to send data to the ChirpStack platform from a RAK4200 module:

- Request an account to RAK and login to the RAK’s ChirpStack platform.
- Create a new Application.
- Register a new device on the platform:
- Configure the Join Mode:
  - OTAA mode on the platform
  - OTAA mode on the RAK4200 module
  - ABP mode on the platform
  - ABP mode on the RAK4200 module
  - Send data from the module and receive it at the platform

The following section gives the details of each of these aforementioned steps. As usual, the user must choose to use ABP or OTAA mode to register the device to the network server.

#### Registering the RAK4200 to ChirpStack

##### Sign up to Chirpstack.io and login to the platform.

Request an account in the forum of RAK, then access to server assigned for your region with your username and password.

##### Create a new Application

Go to the Application section as shown in Figure 25

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/application-section.png"
  width="100%"
  caption="Application section of the RAK’s ChirpStack LoRaServer"
/>

By default, a new Application should be created, although it is possible to reuse the existing ones. For this setup, let’s create a new Application by clicking on the “CREATE” button, and fill the required parameters as shown in Figure 26 and Figure 27.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/creating-a-new-application.png"
  width="100%"
  caption="Creating a new Application on the RAK’s ChirpStack LoRaServer"
/>

For this setup, create an Application named “rak_node_test”.

ChirpStack LoRaServer supports multiple system configurations, with only one by default.
**Service profile** field is to select the system profile.
**Payload codec** is the parsing method for selecting load data. Such as parsing LPP format data.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/filling-parameters.png"
  width="100%"
  caption="Filling parameters of an Application on the RAK’s ChirpStack LoRaServer"
/>

##### Register a new device in the platform

Choose the Application created in the previous step, then select the DEVICES tab as shown in Figure 28, Figure 29.

“CREATE APPLICATION”.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/list-of-applications.png"
  width="100%"
  caption="List of applications created on the RAK’s ChirpStack LoRaServer"
/>

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/device-tab-app.png"
  width="100%"
  caption="Device tab of an Application on the RAK’s ChirpStack LoRaServer"
/>

Once inside of the DEVICE tab, create a new device (LoRa node) by clicking on the “+ CREATE” button.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/add-new-device.png"
  width="100%"
  caption="Add a new device at Device tab of an Application on the RAK’s ChirpStack LoRaServer"
/>

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/new-device-reg.png"
  width="100%"
  caption="New device registration form on the RAK’s ChirpStack LoRaServer"
/>

Fill the parameters requested as appears in Figure 31:

- **Device name and Device description**: These are just descriptive texts.
- **Device EUI**: This interface allows you to generate a Device EUI automatically by clicking the icon highlighted in red in Figure 32. Users can also add a specific Device EUI directly in the form.
- **Device Profile**: To join in OTAA mode, select “DeviceProfile_OTAA”. To join in ABP mode and CN470 frequency, select “DeviceProfile_ABP_CN470”. To join in ABP mode, select “DeviceProfile_ABP”. Note, ChirpStack doesn’t support AS923 in ABP mode.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/generate-new-device.png"
  width="100%"
  caption="Generate a new Device EUI in the device registration form"
/>

#### LoRaWAN Join Mode

The LoRaWAN specification defines that to join in a LoRaWAN network, each end-device has to be personalized and activated. Activation can be done either via Over-The-Air-Activation (OTAA) or via Activation-By-Personalization (ABP). In OTAA the end-device previously personalized is activated when is deployed or reset. In ABP, personalization and activation are done as a single step.

##### Join in OTAA Mode

###### Configure the OTAA mode on the platform

If you have selected “DeviceProfile_OTAA” as shown in Figure 33, then after the device is created, an Application Key must be also created for this device.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/choosing-otaa-mode.png"
  width="100%"
  caption="Choosing OTAA mode in the device registration form"
/>

A previously created Application Key can be entered here or a new one can be generated automatically by clicking the icon highlighted in red in Figure 34:

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/app-key-for-otaa.png"
  width="100%"
  caption="Application Key for the OTAA mode in the device registration form"
/>

Once the Application Key is added in the form, the process can be finalized by clicking on the “SET DEVICE-KEYS” button.

As shown in Figure 35, a new device should be listed in the DEVICES tab. The most important parameters, such as the Device EUI is shown in the summary.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/new-created-device.png"
  width="100%"
  caption="New crated device listed in the DEVICES tab"
/>

To end the process, it is a good practice to review that the Application Key is properly associated with this device. The Application Key can be verified in the KEYS(OTAA) tab as shown in Figure 36.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/app-key-associated.png"
  width="100%"
  caption="Application Key associated with the new device."
/>

::: tip 📝 NOTE
Standard OTAA mode requires the Device EUI, Application Key and the Application EUI, but in the ChirpStack’s implementation, only Device EUI and the Application Key are mandatory. The Application EUI is not required and is not recorded in the Application tab. Nevertheless, the Application EUI is a mandatory parameter in the RAK4200 module’s firmware, in order to resolve this mismatch, users can reuse the Device EUI as the Application EUI during the configuration in the side of the node.
:::

###### Configure the OTAA mode on the RAK4200 module

RAK4200 complies with LoRaWAN 1.0.2, by default the LoRa join mode is OTAA and the LoRa Class is Class A.
To set up the RAK4200 module to join ChirpStack using OTAA start by connecting the RAK4200 module to the Computer (as in Figure 1) and open the RAK Serial Port Tool, wait for the communication to start. It is recommended to test the serial communication by sending an AT command as `at+get_config=lora:status` or `at+version`.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool-4.png"
  width="50%"
  caption="RAK Serial Port Tool connected to a RAK4200"
/>

As an example, the following parameters will be configured in RAK4200:

- LoRa join mode: OTAA
- LoRa class: Class A
- LoRa region: EU868
- Device EUI: 5e9d1e0857cf25f1 (from ChirpStack registration)
- Application EUI: 5e9d1e0857cf25f1 (from ChirpStack registration)
- Application Key: f921d50cd7d02ee3c5e6142154f274b2 (from ChirpStack registration)

1. Set the LoRa join mode to OTAA

Type command: 
```
at+set_config=lora:join_mode:0
```

2. Set the LoRa Class to Class A

Type command: 
```
at+set_confing=lora:class:0
```

3. Set the frequency/region

RAK4200 Supported frequency plan includes:

- IN865 (India)
- EU868 (Europe)
- US915(United States)
- AU915(Australia)
- KR920(Korea)
- AS923(Asia)

**Example**: For Europe Type command: 
```
at+set_config=lora:region:EU868
```

4. Set the Device EUI

Get the Device EUI number from ChirpStack register

Type command: 

```
at+set_config=lora:dev_eui: 5e9d1e0857cf25f1
```

5. Set the Application EUI

Get the Application EUI number from the ChirpStack register.

Type command: 
```
at+set_config=lora:app_eui: 5e9d1e0857cf25f1
```

::: tip 📝 NOTE
Remember, the Application EUI parameter was not required in the ChirpStack platform, therefore it possible to use the same id as the Device EUI. Otherwise, the firmware will complain.
:::

6. Set the Application Key

Get the Application Key from the TNN register.

Type command: 
```
at+set_config=lora:app_key:f921d50cd7d02ee3c5e6142154f274b2
```

7. Saving RAK4200 parameters

Reset the RAK4200 for saving the parameters.

Figure 38 summarizes the set of commands sent over the console for setting the OTAA mode on the RAK4200

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK4200-lora-param3.png"
  width="50%"
  caption="RAK4200 LoRa parameters configuration over the Serial Port Tool"
/>

8. Command the RAK4200 to join in OTAA mode

Type command: 
```
at+join
```

* After 5 or 6 seconds, if the request was successfully received by a LoRa gateway, then “OK Join Success” messages will be shown in the console (see Figure 39).

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool-5.png"
  width="50%"
  caption="RAK Serial Port Tool, join the network"
/>

The JoinRequest and JoinAccept messages are also displayed on the ChirpStack platform, specifically in the LoRaWAN FRAMES section, as shown in Figure 40

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/chirpstack-console.png"
  width="100%"
  caption="ChirpStack Console, checking LoRaWAN join requests"
/>

9. Send data from RAK4200 to ChirpStack

**Example**: To send the string 123456789 over LoRa port 2, type command:
```
at+send=lora:2:1234567890
```
* The data will appear in the ChirpStack web (see Figure 41).

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool-6.png"
  width="50%"
  caption="RAK Serial Port Tool, send a LoRaWAN message."
/>

On the ChirpStack platform, the messages shall appear in the LORAWAN FRAMES tab as shown in Figure 42. Note, by convention, messages sent from nodes to gateways are considered as Uplink. While message send by gateways to nodes are considered as a Downlinks.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/chirpstack-console1.png"
  width="100%"
  caption="ChirpStack Console, checking LoRaWAN messages received."
/>

##### Join in ABP Mode

###### Configure the ABP mode on the platform

During the registration of a new device, if“DeviceProfile_ABP” is selected, as shown in Figure 43, then the ChirpStack platform will assume that this device will join the LoRaWAN network using the ABP mode.

::: tip 📝 NOTE
Check Disable counting frame verification to prevent the node-side counting frame counting from starting from zero after the node is powered on during the test, and the server cannot synchronize the node-side counting and causing the transmission to fail.
:::

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/chirpstack-console2.png"
  width="100%"
  caption="ChirpStack Console, configuring a device in ABP mode"
/>

After selecting the ABP mode, the following parameters appear in the Activation tab (See Figure 44):

- Device address
- Network Session Key
- Application Session Key

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/chirpstack-console3.png"
  width="100%"
  caption="ChirpStack Console, parameters required for the ABP mode"
/>

The parameters can be generated as random numbers by the platform or can be set with user values. Once these parameters are filled properly, the process is completed by clicking on the “ACTIVATE DEVICE” button.

###### Configure the ABP mode on the RAK4200 module

RAK4200 complies with LoRaWAN 1.0.2, by default the LoRa join mode is OTAA and the LoRa Class is Class A.
To set up the RAK4200 module to join ChirpStack using ABP start by connecting the RAK4200 module to the Computer (as in Figure 1) and open the RAK Serial Port Tool, wait for the communication to start. It is recommended to test the serial communication by sending an AT command as `at+get_config=lora:status` or `at+version`.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool-7.png"
  width="50%"
  caption="RAK Serial Port Tool connected to a RAK4200"
/>

As an example, the following parameters will be configured in RAK4200:

- LoRa join mode: ABP
- LoRa class: Class A
- LoRa region: EU868
- Device address: 26011af9 (from ChirpStack registration)
- Network Session Key: c280cb8d1df688bc18601a97025c5488(from ChirpStack registration)
- Application Session Key: 4d42ec5caf97f03d833cdaf5003f69e1(from ChirpStack registration)

1. Set the LoRa join mode to ABP

Type command: 
```
at+set_config=lora:join_mode:1
```

2. Set the LoRa Class to Class A

Type command: 
```
at+set_confing=lora:class:0
```

3. Set the frequency/region:

RAK4200 Supported frequency plan includes:

- IN865 (India)
- EU868 (Europe)
- US915(United States)
- AU915(Australia)
- KR920(Korea)
- AS923(Asia)

**Example**: For Europe Type command:
```
at+set_config=lora:region:EU868
```

4. Set the Device Address

Get the Device Address from ChirpStack register.

**Example**: To set the LoRa Device Address to “**26011af9**”, type command
```
at+set_config=lora:dev_addr:26011af9
```

5. Set the Network Session Key

Get the Network Session Key from the ChirpStack register.

**Example**: To set the LoRa Network Session Key to “**c280cb8d1df688bc18601a97025c5488**”, type command: 
```
at+set_config=lora:nwks_key:c280cb8d1df688bc18601a97025c5488
```

6. Set the Application Key

Get the Network Session Key from the ChirpStack register. 

**Example**: To set the LoRa Network Session Key to “**4d42ec5caf97f03d833cdaf5003f69e1**”, type command:
```
at+set_config=lora:apps_key: 4d42ec5caf97f03d833cdaf5003f69e1
```

7. Saving RAK4200 parameters

Reset the RAK4200 for saving the parameters.

Figure 46 summarizes the set of commands sent over the console for setting the ABP mode on the RAK4200

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK4200-lora-param4.png"
  width="50%"
  caption="RAK4200 LoRa parameters configuration over the Serial Port Tool"
/>

8. Command the RAK4200 to join in ABP mode

Type command: 
```
at+join
```

Once all the parameters required to join to a LoRaWAN network in OTAA mode have been configured. After the RAK4200 returns, you can send the join command: 
```
at+join
```

Almost immediately after sending the command the “OK Join Success” should be replied in the console as shown in Figure 47.

::: tip 📝 NOTE
The ABP mode in LoRaWAN doesn’t require to join a network before sending a LoRaWAN package to the air. But, in order to keep the consistency of the internal states of the firmware of the RAK4200 module, it is still required to send at+join command in the ABP mode.
:::

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool-8.png"
  width="50%"
  caption="RAK Serial Port Tool, sending a message in ABP mode."
/>

9. Send data from RAK4200 to ChirpStack

**Example**: To send the string 123456789 over LoRa port 2, type command: 
```
at+send=lora:2:1234567890
```
* The console will feedback with an “OK” message (see Figure 47). The sent data shall be displayed in ChirpStack web.

### LoRa P2P Mode

This section will show how to set and link two RAK4200 units to work in LoRa P2P mode.
The two RAK4200 units shall be set to operate at the same frequency, e.g: EU868.

As shown in the previous sections, the setup of the RAK4200 units is done by connecting them with a general-purpose computer through the UART port. The setup of each RAK4200 can be done separately, but testing the LoRa P2P mode will require having both units connected simultaneously to a UART port (this could be one computer with 2 ports or 2 computers with one UART port each).

To set the RAK4200 to work in LoRa P2P mode, open the RAK Serial port tool and send the command as in Figure 48: `at+set_config=lora:work_mode:1`

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK4200-setting.png"
  width="50%"
  caption="RAK4200 setting to LoRa P2P mode"
/>

Configure the LoRa P2P parameters for both units. The command for setting the parameters has the format.
`at+set_config=lorap2p:XXX:Y:Z:A:B:C`

From Table 6 the parameters are:

- XXX: Frequency in Hz.
- Y: Spreading factor, [6, 7, 8, 9, 10, 11, 12].
- Z: Bandwidth, [0: 125 kHz,1: 250 kHz,2: 500kHz]
- A: Coding Rate, [1: 4/5, 2: 4/6, 3: 4/7, 4: 4/8]
- B: Preamble Length, 5~65535.
- C: Power in dBm, 5~20.

For this example, the LoRa parameters are:

- Link frequency: 869525000 Hz
- Spreading factor:7
- Bandwidth: 125 kHz
- Coding Rate:4/5
- Preamble Length: 5
- Power: 5 dBm

Which is translated into the following RAK4200 AT command and that is sent to both units as shown in Figure 49:
`at+set_config=lorap2p:869525000:7:0:1:5:5`

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/setting-both-units.png"
  width="50%"
  caption="Setting both RAK4200 units with the LoRa P2P parameters"
/>

Next, set the transmission mode of the module. In this example, Unit 1 is set to sender mode, and unit 2 is set to receiver mode by AT command. See Figure 50.

Unit 1(Sender): `at+set_config=lorap2p:transfer_mode:2`
Unit 2(Receiver): `at+set_config=lorap2p:transfer_mode:1`

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool-9.png"
  width="100%"
  caption="Set the module in the sender (left) and in the receiver (right) mode"
/>

Now, to send a message with the string “123456890” from Unit1 to Unit2, use the command on Unit 1
`at+send=lorap2p:1234567890`

The message will be automatically received by Unit 2 (see Figure 51).

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/RAK-serial-port-tool-10.png"
  width="100%"
  caption="Sending a message from RAK unit 1(left) to RAK unit 2 (right)"
/>

## Miscellaneous

### Firmware Update

Before to start working with the RAK4200, it is recommended to keep the RAK4200 module updated to the latest version of the firmware.

Get the latest pre-compiled firmware version [here](https://downloads.rakwireless.com/en/LoRa/RAK4200/Firmware/).

In the following sections, two (2) options for flashing new firmware in a RAK4200 module are shown: **Upgrade through DAPLink** and **Upgrade through UART1**.

#### Firmware Upgrade Through DAPLink

Refer to the [RAKDAP1 Flash and Debug Tool](/Product-Categories/Accessories/RAKDAP1-Flash-and-Debug-Tool/Overview/#rakdap1-flash-and-debug-tool) guide in the Accesories Category.

#### Firmware Upgrade Through UART1

##### Minimum Hardware and Software Requirements

|               |                                           |
| ------------- | ----------------------------------------- |
| Computer      | A Windows/Ubuntu/Mac computer             |
| Firmware File | Bin firmware downloaded from the website. |
| Others        | A USB to TTL module.                      |

##### Firmware Upgrade Procedure

Follow this procedure in order to upgrade the firmware in Device Firmware Upgrade (DFU) mode through the UART1 interface.

1. Download the latest application firmware of the RAK4200 module from [here](https://downloads.rakwireless.com/en/LoRa/RAK4200/Firmware/).
2. Download the RAK Device Firmware Upgrade (DFU) tool. In this folder are the different DFU tools depending on your machine's OS.
    - [RAK Device Firmware Upgrade (DFU) Tool](https://downloads.rakwireless.com/LoRa/Tools/RAK_Device_Firmware_Upgrade_tool/)
3. Connect the RAK4200 module with a computer through USB to TTL adapter as shown in Figure 1.
4. Open the RAK Device Firmware Upgrade (DFU) tool. Select the serial port and baud rate of the module and click the "Select Port" button.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/device-firmware-tool.png"
  width="70%"
  caption="Device Firmware Upgrade Tool"
/>

5. Select the application firmware file of the module with the suffix ". bin".

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/select-firmware.png"
  width="70%"
  caption="Select firmware"
/>

6. Click the "upgrade" button to upgrade the device. After the upgrade is complete, the RAK4200 module is now ready to work with the new firmware.

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/firmware-upgrading.png"
  width="70%"
  caption="Firmware upgrading"
/>

<rk-img
  src="/assets/images/wisduo/rak4200-module/quickstart/upgrade-success.png"
  width="70%"
  caption="Upgrade successful"
/>
