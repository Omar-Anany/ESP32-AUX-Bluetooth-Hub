# ESP32-AUX-Bluetooth-Hub
## Overview

This project is focused on designing and developing a smart Bluetooth audio receiver and automatic audio switching system using an ESP32 microcontroller and external I2S DAC hardware.

The primary objective of this system is to allow seamless integration between a physical AUX audio input and Bluetooth audio streaming while maintaining uninterrupted analog audio passthrough behavior when Bluetooth is inactive.

The ESP32 continuously operates in standby Bluetooth mode and is always prepared to establish an audio connection with trusted devices. When no active Bluetooth connection is present, the system routes the physical AUX input directly through an analog audio switching stage, allowing external audio sources to pass through with no interruption.

Once a valid Bluetooth connection is established, the ESP32 receives Bluetooth A2DP audio, converts the digital stream through an external PCM5102 I2S DAC and redirects the output path through the audio switching circuitry.

---

# Core System Goals

* Receive Bluetooth A2DP audio using ESP32
* Output stereo analog audio through external I2S DAC
* Maintain uninterrupted AUX passthrough while Bluetooth is inactive
* Automatically switch between AUX and Bluetooth audio paths
* Implement trusted device security and controlled pairing behavior
* Develop a fully integrated custom PCB implementation
* Create modular firmware architecture for future expansion

---

# Security and Pairing Logic

The Bluetooth subsystem is intentionally designed around controlled access behavior rather than unrestricted public pairing.

The ESP32 continuously advertises as a Bluetooth audio receiver and remains available for reconnection from previously authenticated devices. Trusted devices stored within system memory are allowed to reconnect automatically at any time.

Unknown or foreign Bluetooth devices are rejected by default.

To authorize a new device, a physical external pairing button must be pressed by the user. This temporarily enables pairing mode and allows the next connecting device to become registered within the trusted device list.

Any unauthorized connection attempts occurring outside of active pairing mode are immediately disconnected.

This behavior creates a controlled and user managed pairing environment while preserving the convenience of automatic reconnection for approved devices.

---

# Current Hardware

## Main Processing

* ESP32-WROOM-32D

## Audio Hardware

* Adafruit PCM5102 I2S DAC
* TS5A23157 Analog Audio Switch
* 3.5mm AUX Input/Output

## Planned Features

* Custom PCB implementation
* Multi-device trusted storage
* Status LED indicators
* Physical pairing control
* WiFi configuration interface
* OTA firmware updates

---

# Current Development Status

* ESP32 environment configured
* Bluetooth A2DP communication functional
* I2S DAC communication in progress
* Audio switching architecture finalized
* Security and pairing logic under development
* PCB architecture planning started
