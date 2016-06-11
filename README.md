About
=====

With these configuration files you can program ATmega 8/168/168p/328/328p microcontrollers from the [Arduino IDE](http://arduino.cc), without using the Arduino bootloader. It supports chips using external or internal clocks.

Skipping the Arduino bootloader means sketches start immediately after power-on, without any delay, and you have a little extra flash memory available to your programs. Using the (optional) slower internal clock options means you can save on components, but also on power (since a slower chip draws less current).

Install
=======

Add https://raw.githubusercontent.com/carlosefr/atmega/master/package_carlosefr_atmega_index.json in the Arduino IDE Preferences under `File > Preferences` for the setting `Additional Boards Manager URLs`

And then install via `Tools > Board > Boards Manager`.

Programming
===========

To program the microcontroller you will need an ISP programmer. An [Arduino as ISP](http://arduino.cc/en/Tutorial/ArduinoISP) works just fine:

![Arduino as ISP](http://arduino.cc/en/uploads/Tutorial/SimpleBreadboardAVR.png)

Choose your ISP programmer in the `Tools > Programmer` menu. Then choose your ATmega microcontroller from `Tools > Board` and your choice of clock source and clock frequency from `Tools > Clock`.

To set the ATmega configuration fuses, use the `Tools > Burn Bootloader` menu item. This doesn't actually burn an Arduino bootloader onto the chip, it only sets the fuses for the chosen clock settings.

To load programs into the microcontroller, use the `Sketch > Upload with Programmer` menu entry. The IDE will upload the code using the selected ISP programmer.

Pin Mapping
===========

The ATmega168(p) and ATmega328(p) have identical pin configurations. Check [this diagram](http://arduino.cc/en/Hacking/PinMapping168) for their correspondence to Arduino pin numbering:

![ATmega168/168p/328/328p](http://arduino.cc/en/uploads/Hacking/Atmega168PinMap2.png)

Arduino IDE Versions
====================

These configuration files are meant for Arduino IDE 1.6 or later. If you're still using version 1.0 of the IDE, you'll need to get the [ide-1.0.x](https://github.com/carlosefr/atmega/releases/tag/ide-1.0.x) release instead (Does not include 8/168p/328).

Tips and Caveats
================

If you're using an ATmega chip that already has the Arduino bootloader inside or has otherwise been configured to require an external clock source, you may get an `avrdude: Yikes! Invalid device signature.` error. In this case, connect an appropriate external clock source to it (most likely 16 MHz) and try again. Once the ATmega has been configured to use its internal clock source, you can remove the external one and the error shouldn't happen again.

The core `delay()` function is not very precise for clock rates other than external 8 and 16MHz. The internal clock is not so bad but external 12 and 20MHz drift very noticeably. If this is a problem for you code, beware.
