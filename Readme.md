# Edge2Cloud

**Edge2Cloud** is a real-time embedded telemetry system that collects fan speed data using an STM32 microcontroller and securely transmits it to Azure Cloud via a UART–MQTT bridge. The system demonstrates a complete pipeline from low-level sensor acquisition to encrypted cloud communication.

## 🔧 Project Structure

This project is organized into the following submodules:

### 1. `stm32-firmware/`
> **Submodule**  
Firmware for the STM32 microcontroller that reads fan speed using FreeRTOS and transmits the data via UART in a cyclic loop.

- Platform: STM32
- OS: FreeRTOS
- Output: UART messages (fan RPM, temperature, humidity)

### 2. `uart-mqtt-bridge/`
> **Submodule**  
A lightweight Python-based bridge that listens to UART messages from the STM32 and publishes them to Azure Cloud using MQTT over TLS.

- Platform: PC/Raspberry Pi
- Protocols: UART in, MQTT out
- Security: TLS encryption

## 🛠️ How It Works

1. STM32 captures fan telemetry and sends structured UART messages
2. The UART–MQTT bridge reads messages, wraps them into MQTT payloads, and publishes to Azure IoT Hub
3. All communication to the cloud is encrypted via TLS for secure data transfer

## 🚀 Getting Started

### Clone with Submodules

```bash
git clone --recurse-submodules https://github.com/yourusername/Edge2Cloud.git
