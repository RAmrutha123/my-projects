# 🌱 Soil Moisture Sensor Project

This project is an IoT-based Soil Moisture Monitoring System built using an Arduino Uno and a Soil Moisture Sensor. The system measures the water content in the soil and provides output to indicate whether the soil is *dry or sufficiently moist. Such a project is highly useful in *smart farming and irrigation management.

---

## 📌 Features
- Reads soil moisture levels using a sensor.
- Displays output in percentage via Serial Monitor.
- Turns ON/OFF output signal (LED/Relay) based on soil condition.
- Helps in efficient water usage and crop management.

---

## 🛠 Components Used
- Arduino Uno
- Soil Moisture Sensor
- Jumper Wires
- LED (or Relay Module for pump control)

---

## 💻 Code
The Arduino code reads sensor data and maps the values to percentage levels:
- Dry soil → Output indicates low moisture.
- Wet soil → Output indicates sufficient moisture.

```cpp
int sensor_pin = A0;
int output_value;

void setup() {
  pinMode(3, OUTPUT);
  Serial.begin(9600);
  Serial.println("Reading from the Moisture sensor…");
  delay(2000);
}

void loop() {
  output_value = analogRead(sensor_pin);
  output_value = map(output_value, 550, 10, 0, 100);
  Serial.print("DRY:");
  Serial.print(output_value);
  Serial.println("%");

  if (output_value < 0) {
    delay(1000);
    digitalWrite(3, LOW);
  } else {
    delay(1000);
    digitalWrite(3, HIGH);
  }
  delay(1000);
}
