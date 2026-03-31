When the correct combination of switches is flipped, the corresponding LED lights up, creating a magic effect.
<img width="599" height="370" alt="image" src="https://github.com/user-attachments/assets/0b11f867-06ff-42f8-8d7c-1f80909c8027" />


## Components
ESP32 development board
4 Toggle switches
4 LEDs
4 Resistors (220Ω or suitable for LEDs)
Jumper wires
Breadboard or project box

Connect each toggle switch to a digital input on the ESP32.
Connect each LED to a digital output pin on the ESP32 with a resistor in series.
Ensure common GND between ESP32, switches, and LEDs.
<img width="599" height="370" alt="image" src="https://github.com/user-attachments/assets/20bb6a0f-8a91-4c98-a567-d7709039ffe5" />


Note: The color coding in the picture is just for reference – you can choose any colors.

## Code:

```cpp
const int switchPins[4] = {12, 13, 14, 15};
const int ledPins[4]    = {16, 17, 18, 19};

void setup() {
  for (int i = 0; i < 4; i++) {
    pinMode(switchPins[i], INPUT_PULLUP);
    pinMode(ledPins[i], OUTPUT);
    digitalWrite(ledPins[i], LOW);
  }
}

void loop() {
  for (int i = 0; i < 4; i++) {
    bool isPressed = (digitalRead(switchPins[i]) == LOW);
    digitalWrite(ledPins[i], isPressed ? HIGH : LOW);
  }
}
