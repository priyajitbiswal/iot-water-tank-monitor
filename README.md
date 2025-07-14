SEM-2 IoT Group Project

# 💧 Water Level Monitoring System with ESP8266, Ultrasonic Sensor & Blynk

This project monitors the water level in a tank using an ultrasonic sensor and displays the level on an I2C LCD. It also connects to the **Blynk IoT platform** for real-time remote monitoring and motor control. The system uses an **ESP8266 NodeMCU**, visual indicators (LEDs), a **relay module** for motor control, and sends updates to the user’s phone via the **Blynk app**.

## 🔧 Features

* Real-time **water level measurement** using ultrasonic sensor
* **LCD display** showing water level status (Very Low, Low, Medium, High, Full)
* **LED indicators** for intuitive water level feedback
* **Blynk mobile app integration** to:

  * Monitor water level remotely (via virtual pin V0)
  * Control water pump relay (via virtual pin V1)
* **Automatic relay control** via app interface
* WiFi connectivity using **ESP8266 (NodeMCU)**

## 📦 Components Used

* ESP8266 NodeMCU
* HC-SR04 Ultrasonic Sensor
* 16x2 I2C LCD Display
* 5 LEDs (for water level indication)
* Relay Module (for motor control)
* Blynk App (Cloud and mobile interface)
* Jumper wires and a water tank setup

## 🧠 Working Principle

1. The ultrasonic sensor measures the distance from the sensor to the water surface.
2. Based on the measured distance, the system determines the water level and:

   * Updates the LCD with a level label (Very Low → Full)
   * Lights up corresponding LEDs
   * Sends the water level to the Blynk app via virtual pin V0
3. Through the Blynk app, the user can turn the motor ON/OFF using virtual pin V1.
4. When the button is pressed:

   * The relay is triggered to start/stop the water pump
   * The LCD reflects the motor status (ON/OFF)

## 🖼️ LCD & LED Indicators

| Water Level | LEDs ON    | LCD Display |
| ----------- | ---------- | ----------- |
| Very Low    | LED1       | Very Low    |
| Low         | LED1, LED2 | Low         |
| Medium      | LED1–LED3  | Medium      |
| High        | LED1–LED4  | High        |
| Full        | LED1–LED5  | Full        |

## 📲 Blynk App Setup

1. Create a new project in Blynk (use **ESP8266** as hardware).
2. Use the following virtual pins:

   * `V0`: Water Level (Display)
   * `V1`: Motor ON/OFF (Button widget)
3. Enter your **Auth Token** in the code.
4. Connect your mobile to the same network initially.

## 🔧 Setup Instructions

1. Connect all components as per the pin definitions in the code.
2. Upload the code to NodeMCU using Arduino IDE.
3. Power on the device.
4. Open the Blynk app and start the project.
5. The LCD will display the current water level.
6. Use the app to turn the pump ON/OFF.

## 🛠️ Pin Configuration

| Component       | NodeMCU Pin |
| --------------- | ----------- |
| Ultrasonic Trig | D7          |
| Ultrasonic Echo | D8          |
| LED1            | D0          |
| LED2            | D3          |
| LED3            | D4          |
| LED4            | D5          |
| LED5            | D6          |
| Relay           | D9 (GPIO3)  |

## 🧾 Configuration Parameters

```cpp
#define BLYNK_TEMPLATE_ID "TMPL3j5LYkfHk"
#define BLYNK_TEMPLATE_NAME "water level sensing"

char auth[] = "your-auth-token";
char ssid[] = "your-SSID";
char pass[] = "your-WIFI-password";

int MaxLevel = 13; // Max water level in cm
```

Adjust `MaxLevel` according to your tank’s max capacity.

## 📷 Sample Output

* LCD: `WLevel: Medium`
* Blynk: `Water Level = 8cm`
* Motor: ON/OFF based on button in app

## ✅ Future Improvements

* Add automatic motor ON/OFF based on water level
* Send push notifications for low water alert
* Integrate with voice assistants like Alexa or Google Assistant

