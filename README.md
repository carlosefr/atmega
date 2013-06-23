Raw ATmega support for the Arduino IDE
======================================

With this you can program ATmega 168/328p microcontrollers from the Arduino IDE, without using the Arduino bootloader. It supports chips using external (16MHz) or internal (1/8 MHz) clocks.

Skipping the Arduino bootloader means sketches start immediately after power-on, without any delay. Using the slower internal clocks not only saves components, but also power.

Create a "hardware" folder inside your Arduino sketch folder if it doesn't already exist. Then place the "atmega/boards.txt" file there and restart the Arduino IDE. The new board options should then appear in the Arduino IDE's "Tools/Board" menu.
