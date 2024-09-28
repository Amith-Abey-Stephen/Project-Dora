# Project Dora

**Project Dora** is an IoT-based distance monitoring system that utilizes an ultrasonic sensor and two ESP modules for data collection and transmission. This project is designed to measure the distance from a sensor, send the data wirelessly, and display it on a web interface.

## Project Overview
The setup consists of:
1. **Ultrasonic Sensor**: An HC-SR04 sensor is used for distance measurement.
2. **ESP Module 1**: Captures data from the sensor and transmits it to the second ESP module.
3. **ESP Module 2**: Receives data and sends it to a web server for real-time visualization.

This project aims to showcase basic IoT principles like sensor integration, ESP communication, and web-based monitoring.

## Prerequisites
- Arduino IDE installed
- ESP8266 or ESP32 libraries
- Two ESP boards
- HC-SR04 Ultrasonic Sensor
- Basic knowledge of microcontrollers and IoT setup

## Hardware Requirements
- 2x ESP8266/ESP32
- 1x Ultrasonic Sensor (HC-SR04)
- Jumper wires
- Breadboard

## Circuit Diagram
Connect the ultrasonic sensor to ESP1 as follows:
- **VCC** → 3.3V on ESP
- **GND** → GND
- **Trig Pin** → D1 (GPIO 5)
- **Echo Pin** → D2 (GPIO 4)

### ESP to ESP Communication
The two ESP modules should be configured to communicate wirelessly. ESP1 (connected to the sensor) acts as a transmitter, while ESP2 is the receiver.

## Software Setup
1. Clone the repository:  
   `git clone https://github.com/Amith-Abey-Stephen/Project-Dora`
2. Open `distance_sensor.ino` in the Arduino IDE.
3. Configure the Wi-Fi credentials in the code (`ssid` and `password`).
4. Upload the code to both ESP modules.


## Code Explanation
### Ultrasonic Sensor Code
1. Initialization: The sensor is initialized with the trigger and echo pins.
2. Distance Calculation: `digitalWrite()` sends a pulse from the `Trig` pin, and `pulseIn()` captures the time taken for the pulse to return to the `Echo` pin.
3. Distance Formula:
`Distance (cm) =   (Pulse Time × 0.034) / 2`
where 0.034 cm/µs is the speed of sound.

4. Data Transmission: The calculated distance is sent to the second ESP using Serial.write().

### Receiver Code
The second ESP reads the data and forwards it to a simple web server for real-time display.

## Web Visualization
The repository includes a basic HTML page (index.html) that captures and displays the data sent from the ESP modules. To host it, you can use any web server, such as Apache or Node.js.

## How to Run
1. Power on both ESP modules.
2. Open the serial monitor to check the communication.
3. Navigate to the IP address shown on the second ESP’s serial output to view the real-time data on a web page.
