With this you can program ATmega 168/328p microcontrollers from the [Arduino IDE](http://arduino.cc), without using the Arduino bootloader. It supports chips using external or internal clocks.

Skipping the Arduino bootloader means sketches start immediately after power-on, without any delay, and you have a litter extra flash memory available to your programs. Using the (optional) slower internal clock options means you can save on components, but also on power (since a slower chip draws less current).

Create a "hardware" folder inside your Arduino sketch folder if it doesn't already exist. Then place the "atmega/boards.txt" file there (including the "atmega" sub-folder) and restart the Arduino IDE. The new board options should then appear in the Arduino IDE's "Tools > Board" menu.

To program the microcontroller you will need an ISP programmer. An [Arduino as ISP](http://arduino.cc/en/Tutorial/ArduinoISP) works just fine.

Choose your ISP programmer in the "Tools > Programmer" menu. Then choose your ATmega from "Tools > Board", for example "ATmega168 (internal 8 MHz clock)".

To set the ATmega configuration fuses, use the "Tools > Burn Bootloader" menu item. This doesn't actually burn a bootloader onto the chip, it only sets the fuses.

To load programs into the microcontroller, use the "Upload" button as usual. The IDE will upload the code using the selected ISP programmer.
