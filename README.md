# 🌿 IoT-Based Irrigation System

This project is an **IoT-based irrigation system** that automates the watering of plants based on soil moisture levels. It utilizes an **ESP32** microcontroller, a **DHT22 sensor** for temperature and humidity monitoring, and a **soil moisture sensor** to control a sprinkler system. The data is logged to **ThingSpeak** for remote monitoring and analysis.


---

## Features

- **Automated Sprinkler Control**: The system automatically turns the sprinkler on or off based on the soil moisture level.
- **Temperature and Humidity Monitoring**: Real-time monitoring using the DHT22 sensor.
- **ThingSpeak Integration**: Logs soil moisture, temperature, humidity, and sprinkler status to ThingSpeak.

## Hardware Components

- **ESP32** (for WiFi connectivity and control)
- **DHT22 Sensor** (for measuring temperature and humidity)
- **Soil Moisture Sensor**
- **Relay** (to control the sprinkler system)
- **Sprinkler** (for watering the plants)

## Pin Configuration

- **DHT22 Sensor**: GPIO 15
- **Soil Moisture Sensor**: GPIO 34 (Analog Input)
- **Sprinkler Control**: GPIO 5 (Digital Output)

## Prerequisites

- **Arduino IDE** or **PlatformIO** for coding and uploading firmware to ESP32
- Libraries:
  - `WiFi.h`
  - `ThingSpeak.h`
  - `DHTesp.h`

## Installation and Setup

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/iot-irrigation-system.git
   cd iot-irrigation-system
   ```

2. Install the necessary libraries in the Arduino IDE or PlatformIO:
   - **WiFi.h** (included with ESP32)
   - **ThingSpeak.h**
   - **DHTesp.h**

3. Set up your WiFi credentials and ThingSpeak channel details in the code:

   ```cpp
   char* WIFI_NAME = "your_wifi_name";
   char* WIFI_PASSWORD = "your_wifi_password";
   
   int myChannelNumber = your_channel_number;  // ThingSpeak Channel ID
   char* myApiKey = "your_api_key";            // ThingSpeak API Key
   ```

4. Upload the code to your ESP32 using the Arduino IDE or PlatformIO.

## How It Works

- The system reads the soil moisture level and checks whether it is below the predefined threshold.
- If the soil moisture percentage is below the low threshold, the system activates the sprinkler and continues to monitor moisture until it reaches the high threshold.
- The temperature and humidity values from the DHT22 sensor are also monitored and displayed.
- All data (soil moisture, temperature, humidity, and sprinkler status) is sent to the ThingSpeak channel every 15 seconds.


## Code Snippet

Here is a key portion of the code for controlling the sprinkler:

```cpp
if (soilMoisturePercentage < MOISTURE_THRESHOLD_LOW) {
    SPRINKLER_ACTIVATION_STATUS = true;
    digitalWrite(SPRINKLER_CONTROL_PIN, HIGH); // Turn on sprinkler
} else {
    SPRINKLER_ACTIVATION_STATUS = false;
    digitalWrite(SPRINKLER_CONTROL_PIN, LOW);  // Turn off sprinkler
}
```
