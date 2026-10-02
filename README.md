# ESP32-C3 DevBoard

Simple but fancy ESP32-C3 development board. Small enough to fit on a breadboard, big enough to hand-solder without a microscope and a prayer.

<img width="532" height="400" alt="ESP32-C3-image" src="https://github.com/user-attachments/assets/35fa4479-342d-4feb-80ff-5be2e7f56d39" />


## MAIN FEATURES :

- **ESP32-C3** – 32-bit RISC-V core, Wi-Fi + Bluetooth LE. Tiny chip, big ambitions.
- **Onboard CH340C USB-to-serial** – plug it in and start flashing, no external programmer and no spaghetti of jumper wires.
- **WS2812B-2020 RGB LED on IO8** – because every respectable dev board needs at least one LED that can blink in 16 million colors while your code doesn't work.
- **Breadboard compatible** – leaves room for actual wires on both sides. Revolutionary, I know.
- **0805 (and bigger) components** – hand-solder friendly. If you lose one on the floor, you can still find it. Usually.


## IMPORTANT INFORMATIONS ! 

1. **Install the CH340C driver before you plug the board in.** Windows and macOS don't always ship with it, and "my board is dead" is in 90% of cases "my driver is missing". Official drivers: https://www.wch-ic.com/downloads/CH341SER_EXE.html (Windows) / https://www.wch-ic.com/downloads/CH34XSER_MAC_ZIP.html (macOS). Linux has it built in, as Linux likes to remind everyone.

2. **The RGB LED is on IO8.** IO8 is also one of the ESP32-C3 strapping pins, so if you hang something of your own on it, make sure you don't pull it LOW during boot, otherwise the chip will sulk and refuse to enter download mode.

3. **In Arduino IDE** select *ESP32C3 Dev Module* from the ESP32 board package. To light up the LED, use the Adafruit NeoPixel or FastLED library with `DATA_PIN 8` and `NUM_LEDS 1`. One LED. Don't get greedy.

## Quick test 

```cpp
#include <Adafruit_NeoPixel.h>

Adafruit_NeoPixel led(1, 8, NEO_GRB + NEO_KHZ800);

void setup() {
  led.begin();
  led.setBrightness(40); // it's a 2020 LED, not a lighthouse
}

void loop() {
  led.setPixelColor(0, led.Color(255, 0, 0)); led.show(); delay(500);
  led.setPixelColor(0, led.Color(0, 255, 0)); led.show(); delay(500);
  led.setPixelColor(0, led.Color(0, 0, 255)); led.show(); delay(500);
}
```

If it blinks red, green, blue: congratulations, you are now an embedded developer. Put it on your CV.

## Repository content 

- **GERBER, BOM, PNP** – everything you need to order the PCB (and assembly, if you're not in the mood for soldering) from JLCPCB or your favorite fab.
- **SCHEMATIC** – the schematic in PDF, for reading over coffee.
- **Images** – photos for admiring over a second coffee.

## If you want to edit the PCB

**Project can also be found here:** https://oshwlab.com/mariusmym/esp32-c3_devboard

## License 

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

This project is licensed under [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/).

See the [LICENSE](LICENSE) file for the full legal text, which is much less fun to read than this README.

## Donate 

If you'd like to say thanks or buy me a coffee, a **[PayPal donation](https://www.paypal.com/donate/?hosted_button_id=KHR7DYJP2Z8QJ)** is always appreciated!

Have fun and enjoy it ! 😊
