About
=====

With these configuration files you can program ATmega 8/168/168p/328/328p microcontrollers from the [Arduino IDE](http://arduino.cc), without using the Arduino bootloader. It supports chips using external or internal clocks.

Skipping the Arduino bootloader means sketches start immediately after power-on, without any delay, and you have a little extra flash memory available to your programs. Using the (optional) slower internal clock options means you can save on components, but also on power (since a slower chip draws less current).

Install
=======

Go to the **Preferences** window and add the folloing URL to the `Additional Boards Manager URLs` list:

  * `https://raw.githubusercontent.com/carlosefr/atmega/master/package_carlosefr_atmega_index.json`

The chip definitions are now available to be installed from the **Boards Manager**. Search for `Barebones ATmega Chips` in `Tools > Boards > Boards Manager`, select it and click `Install`.

![ATmega](https://raw.githubusercontent.com/carlosefr/atmega/master/atmega_addon.png)

Programming
===========

To program the microcontroller you will need an ISP programmer. An [Arduino as ISP](http://arduino.cc/en/Tutorial/ArduinoISP) works just fine:

![Arduino as ISP](http://arduino.cc/en/uploads/Tutorial/SimpleBreadboardAVR.png)

Choose your ISP programmer in the `Tools > Programmer` menu. Then choose your ATmega microcontroller family from `Tools > Board`, the specific chip you have from `Tools > Processor` and your choice of clock frequency and source from `Tools > Clock`.

To set the ATmega configuration fuses, use the `Tools > Burn Bootloader` menu item. This doesn't actually burn an Arduino bootloader onto the chip, it only sets the chip configuration for the chosen clock settings.

To load programs into the microcontroller, use the `Upload` button as usual. You can also use the `Sketch > Upload with Programmer` menu entry. Both will make the IDE upload the code using the selected ISP programmer.

Pin Mapping
===========

The ATmega168/328 families have identical pin configurations. Check [this diagram](http://arduino.cc/en/Hacking/PinMapping168) for their correspondence to Arduino pin numbering:

![ATmega168/168p/328/328p](https://raw.githubusercontent.com/carlosefr/atmega/master/atmega328p.png)

The pin layout for the ATmega8 is also identical to these, but additional functions may be missing (eg. PWM on the left-side pins).

Arduino IDE Versions
====================

These configuration files are meant for Arduino IDE 1.6 or later. If you're still using version 1.0 of the IDE, you'll need to get the [ide-1.0.x](https://github.com/carlosefr/atmega/releases/tag/ide-1.0.x) release instead (only the ATmega168 and 328p are supported).

Tips and Caveats
================

If you're using an ATmega chip that already has the Arduino bootloader inside or has otherwise been configured to require an external clock source, you may get an `avrdude: Yikes! Invalid device signature.` error. In this case, connect an appropriate external clock source to it (most likely 16 MHz) and try again. Once the ATmega has been configured to use its internal clock source, you can remove the external one and the error shouldn't happen again.

The core `delay()` function is not very precise for clock rates other than external 8 and 16MHz. The internal clock is not so bad but external 12 and 20MHz drift very noticeably. If this is a problem for you code, beware.

The ATmega168p and ATmega328 chip variants supported by this addon were never used in Arduino boards, if you're wondering.
