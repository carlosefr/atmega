About
=====

With these configuration files you can program ATmega 168/328p microcontrollers from the [Arduino IDE](http://arduino.cc), without using the Arduino bootloader. It supports chips using external or internal clocks.

Skipping the Arduino bootloader means sketches start immediately after power-on, without any delay, and you have a little extra flash memory available to your programs. Using the (optional) slower internal clock options means you can save on components, but also on power (since a slower chip draws less current).

Install
=======

Create an `hardware` folder inside your Arduino sketch folder if it doesn't already exist. Then place the contents of this repository in a sub-folder called `atmega`. You should end up with an `hardware/atmega/avr` folder containing the actual configuration files. Restart the Arduino IDE and the new board options should appear in the "Tools > Board" menu.

Programming
===========

To program the microcontroller you will need an ISP programmer. An [Arduino as ISP](http://arduino.cc/en/Tutorial/ArduinoISP) works just fine.

Choose your ISP programmer in the "Tools > Programmer" menu. Then choose your ATmega microcontroller from "Tools > Board" (eg. "ATmega168") and your choice of clock frequency from "Tools -> Clock" (eg. "1 MHz (internal)").

To set the ATmega configuration fuses, use the "Tools > Burn Bootloader" menu item. This doesn't actually burn a bootloader onto the chip, it only sets the fuses for the chosen clock frequency.

To load programs into the microcontroller, use the "Upload" button as usual. The IDE will upload the code using the selected ISP programmer.

Arduino IDE Versions
====================

These files are meant for Arduino IDE 1.6 or later. Get the "ide-1.0.x" release from the "releases" section on GitHub if you're using Arduino 1.0.
