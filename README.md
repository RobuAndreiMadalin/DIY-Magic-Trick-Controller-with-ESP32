When the correct combination of switches is flipped, the corresponding LED lights up, creating a magic effect.

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

Note: The color coding in the picture is just for reference – you can choose any colors.

## Code:
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

