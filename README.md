AntiAliasedClock
======
**Teensy 4.x analog clock with three different views.**
**For displays with ILI9341 controller and 240x320px resolution.**
**The special feature is the drawing of the hands with antialiasing and the flickerfree and smooth movement of the hands.**

Copyright (C) 2021 by DIYLAB <https://www.diylab.de>

![](screenshots/thumb_watchface1.jpg) ![](screenshots/thumb_watchface2.jpg) ![](screenshots/thumb_watchface3.jpg)

The idea itself comes from Bodmer's repository and his wonderful [TFT_eSPI](https://github.com/Bodmer/TFT_eSPI) library - thanks for the suggestion!
The colleague presented an '[Anti-aliased_Clock_v3](https://github.com/Bodmer/TFT_eSPI/tree/2.4.0-Beta/examples/Anti-aliased/Anti-aliased_Clock_v3)' which I liked immediately.

I ported this clock demo to the Teensy 4.x and use the [ILI9341_T4](https://github.com/vindar/ILI9341_T4)  and Arvind's [TGX library](https://github.com/vindar/tgx). It also allows me to draw with antialiasing, flicker-free through vSync and use RGB32 colors and alpha channels.

The clock uses the internal RTC of the Teensy and if you connect a [battery externally](https://www.pjrc.com/store/teensy40.html), the time is not lost either!

![](screenshots/teensy40_vbat_coin_cell.jpg)

The time is set automatically by flashing the firmware.
You can create and use a clock face yourself in a very easy way, the source code is simple and documented. Use the [ImageConverter](http://www.rinkydinkelectronics.com/t_imageconverter565.php) from Rinky-Dink electronics to convert your own pictures to the needed format.

After setting the time, the clock runs freely and is automatically resynchronized with a deviation of +/- one second to the RTC.

### Watch the video

[![Watch the video](https://img.youtube.com/vi/NFdBhmQNh7A/0.jpg)](https://youtu.be/NFdBhmQNh7A)

### These components are required as a minimum

* Teensy 4.0 or Teensy 4.1
* One TFT displays with ILI9341 controller and a resolution of 320x240 px

### Display recommendations

* [3.2inch SPI Module ILI9341 SKU:MSP3218](http://www.lcdwiki.com/3.2inch_SPI_Module_ILI9341_SKU:MSP3218)
* [2.8inch SPI Module ILI9341 SKU:MSP2807](http://www.lcdwiki.com/2.8inch_SPI_Module_ILI9341_SKU:MSP2807)
* [2.4inch SPI Module ILI9341 SKU:MSP2402](http://www.lcdwiki.com/2.4inch_SPI_Module_ILI9341_SKU:MSP2402)
* [2.2inch SPI Module ILI9341 SKU:MSP2202](http://www.lcdwiki.com/2.2inch_SPI_Module_ILI9341_SKU:MSP2202)

Many other displays are also possible if they have the required connectors, have the ILI9341 controller and a resolution of 320x240 px.

### Displays connection diagram

| Display      | Teensy                                                       |
| -------------- | ------------------------------------------------------------ |
| VCC            | **3.3V** (from Teensy, better 3.3V from separate LDO) ¹      |
| GND            | **GND** (on top, between Vin and 3.3V)                       |
| CS             | **9**                                                        |
| RESET          | **6**                                                        |
| DC/RS          | **10**                                                       |
| SDI (**MOSI**) | **11**                                                       |
| SCK            | **13**                                                       |
| LED            | any available pin will do or connect to +3.3V through a small resistor 50 to 100 Ohm |
| SDO (**MISO**) | **12**                                                       |

¹ Recommended: close the jumper **J1** on the display.

### Used libraries

1. Arvind's optimized ILI9341 screen driver library for Teensy 4/4.1, with vsync and differential updates: <https://github.com/vindar/ILI9341_T4>
2. TGX - a tiny/teensy graphics library: <https://github.com/vindar/tgx>
3. TimeLib.h from Paul Stoffregen (included in Teensyduino)

### Used development software

* Arduino IDE 1.8.15 (always needed)
* Teensyduino, Version 1.54 (always needed, versions below 1.54 will not work)
* [optional: Microsoft Visual Studio Community 2019 + Visual Micro - Release 21.06.06.17]