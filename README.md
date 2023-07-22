# CAN-PROJECT
# Temperature and Humidity Sensor with CAN Communication

This Arduino project reads temperature and humidity values from a DHT11 sensor and sends them over the CAN bus using an MCP2515 module. It also calculates the heat index based on the sensor readings and includes it in the CAN message.

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

- Connect the DHT11 sensor data pin to digital pin 26 on the Arduino.
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

2. Upload the sketch to your Arduino board.

3. Ensure that the DHT11 sensor is connected correctly to the Arduino and the MCP2515 module is wired appropriately.

4. Monitor the serial output to check the temperature, humidity, and heat index readings, as well as the CAN messages being sent.

## Notes

- The DHT sensor readings may take a few seconds to stabilize. Please be patient while the values are being updated.
- The MCP2515 module requires the CAN bus to be terminated correctly for proper communication. Ensure that you have appropriate termination resistors if required.

## License

This project is licensed under the [MIT License](LICENSE).



CAN Slave (Receiver) - Temperature and Humidity Sensor

This Arduino project serves as the CAN slave (receiver) that receives temperature and humidity values from the CAN master and displays them for individual cages. The code is designed to handle up to 100 cages, each identified by a unique CAN ID.

Components Used
Arduino board (compatible with SPI communication)
MCP2515 CAN controller module
Libraries
The following library is required for this project:

SPI.h for SPI communication.
mcp2515.h for CAN communication. (Available at: https://github.com/autowp/arduino-mcp2515/)
Wiring
Connect the MCP2515 module to the Arduino as follows:
VCC -> 5V
GND -> GND
SCK -> SCK (Pin 13)
SO -> MISO (Pin 12)
SI -> MOSI (Pin 11)
CS -> Pin 5
Setup
Install the required library:

mcp2515.h: Download the library from the given GitHub repository and add it to your Arduino libraries folder.
Upload the CAN slave (receiver) sketch to your Arduino board.

Ensure that the MCP2515 module is wired appropriately.
Monitor the serial output to view the received data for each cage.

Usage Notes
The CAN bus should be properly terminated to ensure reliable communication with the master node.
The code assumes that the master node sends data to each cage with a unique CAN ID from 1 to 100.
Make sure the CAN master (sender) is running and sending data to the slave node(s).
License
This project is licensed under the MIT License.
