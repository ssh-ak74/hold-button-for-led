#  Hold Button for LED

A simple ESP32 project where an LED stays **ON only while the push button is being held down**.

Built as a basic introduction to **digital inputs, digital outputs, and pull-up resistors**.

##  Features

*  Push-button input
*  LED output
*  Uses the ESP32's internal pull-up resistor
*  LED turns ON while the button is held
*  LED turns OFF when the button is released
*  Built with PlatformIO
*  MIT licensed

##  Wiring

### LED

| Component       | ESP32                        |
| --------------- | ---------------------------- |
| LED anode (+)   | GPIO 25 through 1kΩ resistor |
| LED cathode (-) | GND                          |

### Push Button

| Button        | ESP32   |
| ------------- | ------- |
| One side      | GPIO 27 |
| Opposite side | GND     |

The button uses `INPUT_PULLUP`, so no external pull-up resistor is required.

> **Note:** 4-pin tactile buttons have two pairs of internally connected pins. Make sure GPIO 27 and GND are connected to **opposite sides** of the button.

##  How It Works

The ESP32 continuously checks the state of GPIO 27.

```text
Button released → GPIO 27 = HIGH → LED OFF
Button pressed  → GPIO 27 = LOW  → LED ON
```

The LED is controlled using GPIO 25.

##  Code

```cpp
#define LED_PIN 25
#define BUTTON_PIN 27

void setup() {
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUTTON_PIN, INPUT_PULLUP);
}

void loop() {
  if (digitalRead(BUTTON_PIN) == LOW) {
    digitalWrite(LED_PIN, HIGH);
  } else {
    digitalWrite(LED_PIN, LOW);
  }
}
```

##  Hardware

* ESP32 development board
* 1× LED
* 1× 1kΩ resistor
* 1× 4-pin tactile push button
* Breadboard
* Jumper wires

##  Getting Started

1. Connect the components according to the wiring above.
2. Clone this repository.
3. Open it with PlatformIO.
4. Connect your ESP32.
5. Upload the program.
6. Hold the button to turn the LED on.

## 📁 Project Structure

```text
hold-button-for-led/
├── src/
│   └── main.cpp
├── platformio.ini
├── LICENSE
└── README.md
```

##  License

This project is licensed under the **MIT License**.

See [`LICENSE`](LICENSE) for details.

---
