With this you can program ATmega 168/328p microcontrollers from the [Arduino IDE](http://arduino.cc), without using the Arduino bootloader. It supports chips using external or internal clocks.

Skipping the Arduino bootloader means sketches start immediately after power-on, without any delay. Using the slower internal clock options means you can save on components, but also on power.

Create a "hardware" folder inside your Arduino sketch folder if it doesn't already exist. Then place the "atmega/boards.txt" file there (including the "atmega" sub-folder) and restart the Arduino IDE. The new board options should then appear in the Arduino IDE's "Tools/Board" menu.

To program the microcontrollers you will need an ISP programmer. An [Arduino as ISP](http://arduino.cc/en/Tutorial/ArduinoISP) works just fine.
