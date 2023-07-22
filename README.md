# CAN Temperature and Humidity Sensor Project

## Description

This Arduino project allows you to monitor temperature and humidity values in multiple cages using a CAN (Controller Area Network) communication setup. The project consists of two parts: the CAN Master (Sender) and CAN Slave (Receiver). The CAN Master reads temperature and humidity values from a DHT11 sensor and sends them over the CAN bus to multiple slave nodes (cages). The CAN Slave nodes receive the data and display it for individual cages.

## Components Used

- Arduino board (compatible with SPI communication)
- DHT11 temperature and humidity sensor
- MCP2515 CAN controller module

## Libraries

The following libraries are required for this project:

- `SPI.h` for SPI communication.
- `mcp2515.h` for CAN communication. (Available at: https://github.com/autowp/arduino-mcp2515/)
- `DHT.h` for DHT sensor support.

## Wiring

### CAN Master (Sender)
- Connect the DHT11 sensor data pin to digital pin 26 on the Arduino.
- Connect the MCP2515 module to the Arduino as follows:
  - VCC -> 5V
  - GND -> GND
  - SCK -> SCK (Pin 13)
  - SO -> MISO (Pin 12)
  - SI -> MOSI (Pin 11)
  - CS -> Pin 5

### CAN Slave (Receiver)
- Connect the MCP2515 module to the Arduino as follows:
  - VCC -> 5V
  - GND -> GND
  - SCK -> SCK (Pin 13)
  - SO -> MISO (Pin 12)
  - SI -> MOSI (Pin 11)
  - CS -> Pin 5

## Setup

1. Install the required libraries:
   - `mcp2515.h`: Download the library from the given GitHub repository and add it to your Arduino libraries folder.
   - `DHT.h`: This library should be available in the Arduino IDE by default.

2. Upload the CAN Master (Sender) sketch to the Arduino board.

3. Upload the CAN Slave (Receiver) sketch to the Arduino board.

4. Ensure that the DHT11 sensor is connected correctly to the Arduino (CAN Master) and the MCP2515 module is wired appropriately (both CAN Master and CAN Slave).

5. Monitor the serial output of the CAN Slave to view the received data for each cage.

## Usage Notes

- The CAN bus should be properly terminated to ensure reliable communication between the master and slave nodes.
- The code assumes that each slave node (cage) sends data with a unique CAN ID from 1 to 100.
- Make sure to adjust the loop range (from 1 to 100) in the receiver code if using a different number of nodes.

## License

This project is licensed under the [MIT License](LICENSE).
