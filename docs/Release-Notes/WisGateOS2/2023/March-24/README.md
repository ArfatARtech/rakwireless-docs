---
release_date: 03/24/2023
version: "2.1.4"
release_note_description: Unified operative system for the WisGate Edge line that provides a feature-rich environment to access and configure the LoRaWAN gateway. The latest version of WisGateOS 2 is based on the latest version of the OpenWRT kernel for better security. WisGateOS 2 uses a simplified user interface that makes it easier to use and program. Integrated with WisDM, which allows the remote management of gateways and firmware. With extension functionality, the user can add extra features and functions to their gateways.
download_link: https://downloads.rakwireless.com/LoRa/WisGateOS2/WisGateOS2_2.1.4.zip
logo: /assets/images/release-notes/WisGateOS2.png

---

<rk-release-notes/>

---


## Added

| No. | Feature                                                         | Description                                                                                                                                                                                                                                                | Reference                                                                                                                                                           |
| --- | --------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | WisDM redirection in WisGateOS                                  | Quick link to the WisDM is added to the WebUI footer.                                                                                                                                                                                                      | -                                                                                                                                                                   |
| 2   | Pre-upgrade announcement                                        | Provides most important release notes for the new firmware before update from the WebUI.                                                                                                                                                                   | [WisGate OS 2 User Manual > Settings](https://docs.rakwireless.com/Product-Categories/Software-APIs-and-Libraries/WisGateOS-2/Overview/#firmware)                   |
| 3   | Add `enable automatic data recovery` for Packet Forwarder mode. | A feature that allows LoRa frames to be stored on the SD card (provided there is one in the slot). If the gateway loses connection to the LoRa Network Server, upon restoring the connection, the buffered messages will be forwarded, so no data is lost. | [WisGate OS 2 User Manual > LoRa](https://docs.rakwireless.com/Product-Categories/Software-APIs-and-Libraries/WisGateOS-2/Overview/#packet-forwarder-mode-settings) |

## Fixed

| Daily Build No. / Bug No. | Description                                                                                                                                                                                          |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -                         | Downlink is rejected by the forwarder sometimes.                                                                                                                                                     |
| -                         | The built-in NS will fall into a dead loop when the MQTT client's TLs version does not match the MQTT broker.                                                                                        |
| -                         | If using the AWS IoT MQTT client to get 64-byte uplink data, the client fails to get the data if the data is more than 64 bytes.                                                                     |
| -                         | Basics Station won‘t connect to Actility NS after the gateway is rebooted.                                                                                                                           |
| -                         | Default ping interval field setting is 10 minutes in MultiWAN.                                                                                                                                       |
| -                         | The RSSI value of FSK channel data displayed on the gateway exceeds the expected range.                                                                                                              |
| -                         | 4G default ping intervals were revised to reduce SIM data consumption.                                                                                                                               |
| -                         | In the AS923 band, after connecting to TTN, devices cannot join normally.                                                                                                                            |
| -                         | Support `-`, `_`, `,`, `!` in the WiFi WAN/LAN password.                                                                                                                                             |
| -                         | In the timestamp report to Chirpstack, the fineTimestampType is always `NONE`.                                                                                                                       |
| -                         | In some cases, the cellular connection cannot be established after a reboot.                                                                                                                         |
| -                         | After configuring the whitelist, the parameters do not take effect.                                                                                                                                  |
| -                         | Packet Filter, White List, and Network ID cannot be set to **0**.                                                                                                                                    |
| -                         | Basics Station cannot start successfully in some cases.                                                                                                                                              |
| -                         | Support config Json type(array/object) auto-detection for sx1302.                                                                                                                                    |
| -                         | Logic error causes Packet Forwarder to keep restarting.                                                                                                                                              |
| -                         | MAC commands for uplink are not displayed in the gateway packet capture.                                                                                                                             |
| -                         | After setting the SSL/TLS mode to a self-signed server and client certification and configuring the certificate, the process displays abnormal behavior.                                             |
| -                         | When the gateway has enabled the WisDM button, the `Upload.log` file is generated in `syslog`. In the case of poor network status, it will repeatedly try to upload to WisDM after the upload fails. |