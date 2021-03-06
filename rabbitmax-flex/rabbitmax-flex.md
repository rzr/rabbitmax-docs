# RabbitMax Flex

**Open source Raspberry Pi HAT for Internet of Things (IoT)**

---

# DISCLAIMER

Raspberry Pi and the Raspberry Pi logo are registered trademarks of the Raspberry Pi Foundation. RabbitMax, the RabbitMax logo and combinations thereof, are registered trademarks of Leon Anavi. Other product names may be trademarks of others and the rights belong to their respective owners.

The information in this document is provided in connection with RabbitMax products. No license, express or implied
or otherwise, to any intellectual property right is granted by this document or in connection with the sale of RabbitMax products.

This work is licensed under the Creative Commons Attribution-ShareAlike 3.0 Unported License. To view a copy of
this license, visit http://www.creativecommons.org/licenses/by-sa/3.0/.

RabbitMax Flex hardware design is licensed under a Creative Commons Attribution-ShareAlike 3.0 Unported License.

The software examples are released under MIT and the rest of the software is available under GPLv3.

It is possible that the pictures in this manual differ from the latest revision of the board.

The product described in this document is subject to continuous development and improvements. All particulars of the product and its use contained in this document are given by RabbitMax in good faith. However all warranties implied or expressed including but not limited to implied warranties of merchantability or fitness for purpose are excluded. This document is intended only to assist the reader in the use of the product. RabbitMax shall not be liable for any loss or damage arising from the use of any information in this document or any error or omission in such information or any incorrect use of the product.

This evaluation board/kit is intended for use for engineering development, demonstration, or evaluation purposes only and is not considered by RabbitMax to be a finished end-product fit for general consumer use. People handling the product must have electronics training and observe good engineering practice standards. As such, the goods being provided are not intended to be complete in terms of required design-, marketing-, and/or manufacturing-related protective considerations, including product safety and environmental measures typically found in end products that incorporate such semiconductor components or circuit boards.

There is no warranty for the design materials and the components used to create RabbitMax Flex. There are considered suitable only for RabbitMax Flex.

---

# CHAPTER 1: Overview

## Introduction

RabbitMax Flex is an open source hardware Raspberry Pi HAT for Internet of Things (IoT). RabbitMax Flex was started as a hobby project by Leon Anavi in 2016. It is suitable for do it yourself (DIY) weather station, automated desk assistant or rapid prototyping of Internet of Things (IoT).

RabbitMax Flex is designed with the free and open source electronics design automation suite [KiCAD](http://kicad-pcb.org/). No soldering is required. You can assemble RabbitMax Flex to your Raspberry Pi with your bare hands.

RabbitMax is fully compatible with the Raspbian GNU/Linux distribution and open source sample applications are provided. RabbitMax Flex also supports its own RabbitMax IoT GNU/Linux distribution which is based on the Yocto Project and Openembedded and features open source daemon for communicating with other Internet of Things (IoT) through the lightweight machine-to-machine connectivity protocol MQTT.

## Features

RabbitMax Flex Raspberry Pi HAT includes:

* Relay
* IR LED
* IR photo sensor
* Piezo buzzer
* Button
* RGB LED
* Slot for modular LCD character display
* Slots for up to 5 plug and play I2C sensors

## Supported Raspberry Pi Versions and Models

RabbitMax Flex is compatible with the following Raspberry Pi version and models:

* Raspberry Pi 3 
* Raspberry Pi 2 
* Raspberry Pi 0
* Raspberry Pi Model B+
* Raspberry Pi Model A+

RabbitMax Flex is **NOT** compatible with the earlier 26-pin models of Raspberry Pi 1 Model B & A's.

## Target Market

RabbitMax Flex is a Raspberry Pi HAT suitable for existing Raspberry Pi customers interested in home automation, software development and Internet of Things. The board is appropriate for embedded programming enthusiasts, GNU/Linux gadget fans, students as well as web and/or mobile app developers. The main usage of the board is embedded software development without the urge of understanding perfectly the hardware.

## Board Version

Revision 1.1 of RabbitMax Flex was used while writing this document. It is possible that it is outdated so it is always recommended to check the latest sources from the GitHub page of the board.

# CHAPTER 2: Getting Started

## Electrostatic Warning

RabbitMax Flex is shipped in a protective antistatic bag. The HAT as well as the Raspberry Pi must **NOT** be exposed to high electrostatic potentials. A grounding strap or similar protective device should be worn when handling the board. Avoid touching the component pins or any other metallic element.

## Requirements

In order to setup RabbitMax Flex the following items are required:

* Compatible Raspberry Pi
* microSD card with compatible image
* USB power supply

Additionally you may attach USB mouse, keyboard, HDMI monitor or addition peripheral devices to your Raspberry Pi.

## Supported Peripherals

### Sensors

#### Temperature Sensor

The official temperature sensor for RabbitMax Flex is BMP180. This is I2C sensor capable of measuring both temperature and barometric pressure.

Using 4 Dupont jumper wires connect BMP180 to one of the 5 I2C slots on RabbitMax Flex as follows:

| BMP180   | RabbitMax Flex |
| -------- |:-------------- |
| VIN      | 3.3V           |
| GND      | GND            |
| SCL      | SCL            |
| SDA      | SDA            |

#### Humidity Sensor

The official humidity temperature for RabbitMax Flex is HTU21 (SHT21). This is I2C sensor capable of measuring both humidity and temperature.

Using 4 Dupont jumper wires connect HTU21 to one of the 5 I2C slots on RabbitMax Flex as follows:

| HTU21    | RabbitMax Flex |
| -------- |:-------------- |
| VIN      | 3.3V           |
| GND      | GND            |
| SCL      | SCL            |
| SDA      | SDA            |

#### Light Sensor

The official light I2C sensor for RabbitMax Flex is BH1750.

Using 4 Dupont jumper wires connect BH1750 to one of the 5 I2C slots on RabbitMax Flex as follows:

| BH1750   | RabbitMax Flex |
| -------- |:-------------- |
| VCC      | 3.3V           |
| GND      | GND            |
| SCL      | SCL            |
| SDA      | SDA            |

### LCD Display Modules

RabbitMax Flex supports monochrome 1602 character LDC alphanumeric display screen with 16 characters on two rows. Plug the display in the 16 female header pins above the logo of RabbitMax Flex. Use a screwdriver to adjust the brightness of the backlight of the display through the potentiometer.

## Assembly

You can assemble RabbitMax Flex and mount it on your Raspberry Pi with your bare hands following the steps below:

* Ensure that you Raspberry Pi is compatible with RabbitMax Flex.
* Power off your Raspberry Pi.
* Gently mount RabbitMax Flex on the 40 pin header of your Raspberry Pi.
* Add sensors and LCD display module to your RabbitMax Flex.
* Optionally, you may also assemble two brass M2.5 standoffs to keep your Pi HAT snug on your Raspberry Pi while also keeping the two boards separated, in particular the HDMI port.
* Optionally, adjust the LED backlight of the LCD display module using a screwdriver.
* That's all, now you are ready to go!

## Powering RabbitMax Flex

RabbitMax Flex is Raspberry Pi HAT therefore it is powered through Raspberry Pi. It is recommended to use the [official Raspberry Pi Power Supply](https://www.raspberrypi.org/products/universal-power-supply/) or another 2.5A USB power supply from reputable retailer.

---

# CHAPTER 3: Software

## Installation

In order to work correctly, RabbitMax Flex HAT requires an up-to-date kernel, I2C to be enabled, and a few libraries to get started. After booting microSD card with Raspbian, open a terminal and execute the following commands:

* Ensure your APT package list is up-to-date:

```
sudo apt-get update
```

* Upgrade packages

```
sudo apt-get upgrade
```

* Install additional applications, libraries and other tools needed by RabbitMax Flex

```
sudo apt-get install -y git i2c-tools lirc
```

### Enable I2C

### Enable infrared (IR)

## Examples

Sample applications written in Python and the C programming language are provided for RabbitMax Raspberry Pi HAT under MIT license in GitHub. All examples have been tested on Raspbian.

Open a terminal and execute the follow the steps by step instructions to install all dependencies and to get the source code:

* Install dependencies:

```
sudo apt-get update
sudo apt-get install -y git git-core vim python-dev python-rpi.gpio
```

* Install the GPIO interface library for Raspberry Pi called [wiringPi](http://wiringpi.com/):

```
cd ~
git clone git://git.drogon.net/wiringPi
cd wiringPi
./build
```

* Download the example for RabbitMax Flex Raspberry Pi HAT

```
cd ~
git clone https://github.com/RabbitMax/rabbitmax-examples.git
cd rabbitmax-examples
```

### Relay

### Piezo Buzzer

### Button

### RGB LED

### LCD Display Module

### Sensors

#### Temperature Sensor (BMP180)

#### Humidity Sensor (HTU21D)

#### Light Sensor (BH1750)

## LIRC

## Device Tree Overlays

Device Tree (DT) in Linux is a description of the hardware in a system. The DT overlay adds a number of optional elements. 

The EEPROM of RabbitMax Flex contains DT overlay with description of the peripheral devices on the HAT. After adding RabbitMax to your Raspberry Pi and booting it you  should have some new filesystem nodes at */proc/device-tree/hat*:

```
pi@raspberrypi:~ $ ls -l /proc/device-tree/hat/
total 0
-r--r--r-- 1 root root  4 Sep 18 23:29 name
-r--r--r-- 1 root root 15 Sep 18 23:27 product
-r--r--r-- 1 root root  7 Sep 18 23:27 product_id
-r--r--r-- 1 root root  7 Sep 18 23:27 product_ver
-r--r--r-- 1 root root 37 Sep 18 23:29 uuid
-r--r--r-- 1 root root 24 Sep 18 23:27 vendor
```

The information provided in these filesystem nodes helps you to identify RabbitMax Flex vendor, version, product name, etc. For example:

```
pi@raspberrypi:~ $ cat /proc/device-tree/hat/product
RabbitMax Flex

pi@raspberrypi:~ $ cat /proc/device-tree/hat/vendor
RabbitMax by Leon Anavi
```

More information about device trees, overlays and parameters are available at [the official Raspberry Pi documentation](https://www.raspberrypi.org/documentation/configuration/device-tree.md).


## Debugging

---

# CHAPTER 4: RabbitMax IoT GNU/Linux Distribution

---

# CHAPTER 5: Schematics

## Pinout

The components of RabbitMax Flex utilize the following pins on Raspberry Pi:

| Component    | Pins                            |
| ------------ |:------------------------------- |
| I2C          | 3, 5                            |
| EEPROM       | 27, 28                          |
| Relay        | 29                              |
| Button       | 23                              |
| Piezo buzzer | 31                              |
| RGB LED      | 33 (blue), 35 (green), 37 (red) |
| LCD display  | 7, 13, 15, 19, 21, 40           |
| IR LED       | 11                              |
| IR receiver  | 12                              |

## I2C

The sensors that can be connected to RabbitMax Flex communicate with a host microcontroller via a communications standard called **I2C** (Inter-Integrated-Circut). I2C uses two wires, labelled SDA (Serial Data) and SCL (Serial Clock). To function properly, I2C requires a pullup resistor on each of those lines therefore RabbitMax Flex includes two 4.7kohm resistors labelled as R9 and R10. If for one reason or another you need to disable the I2C pullup resistors remove R9 and R10.

## LCD Module

1602 LCD character display module can be attached to RabbitMax Flex. The HAT supports modules with 16 characters on 2 rows which are compatible with the Hitachi HD44780 LCD controller. The LCD module requires 8 data lines to provide data to bits 0-7  but it can be also set to a 4 bit mode which allows sending data in two chunks. Each chuck is 4 bits. The 4 bit mode is convenient as it reduces the number of used GPIO pins on Raspberry Pi. RabbitMax Flex uses the following wiring for the connector for 1602 LCD modules:

| LCD  | Function             | Raspberry Pi Pin |
| ---- |:-------------------- |:---------------- |
| 1    | GND                  | 6
| 2    | 5V                   | 2
| 3    | Contrast             | 6
| 4    | RS                   | 7
| 5    | RW                   | 6
| 6    | E                    | 40
| 7    | Data 0               | 13
| 8    | Data 1               | 15
| 9    | Data 2               | 19
| 10   | Data 3               | 21
| 11   | Data 4               | -
| 12   | Data 5               | -
| 13   | Data 6               | -
| 14   | Data 7               | -
| 15   | 5V via potentiometer | 2
| 16   | GND                  | 6

LED backlight of the LCD display module can be manually adjusted through the potentiometer POT1 using a screwdriver.

---

# CHAPTER 6: Frequently Asked Questions (FAQ)

#### May I use RabbitMax Flex with other operating systems?

Yes, you can use RabbitMax Flex with other GNU/Linux distributions and even other operating systems but some porting efforts might be required.

#### May I use other I2C sensors with RabbitMax Flex?

Yes, you can use other I2C sensors with RabbitMax Flex but you should take care for their drivers and software support.

#### May I use non-I2C sensors with RabbitMax Flex?

No.

#### Is RabbitMax Flex software free and open source?

Yes, the official RabbitMax Flex software is free and open source. The examples are available under MIT license and the rest is available under GPLv3. Please contact us if you are working on a commercial product and you would like to use the software under alternative commercial license.

---

# CHAPTER 7: Revision History

## Document Revision

| Date             | Changes                | Modified pages  |
| ---------------- |:----------------------:| :---------------|
| 14 September 2016| Initial manual release | All             |

## RabbitMax Flex HAT Revision

| Revision| Notable changes                                              |
| ------- |:-------------------------------------------------------------|
| 1.0     | First prototype                                              |
| 1.1     | Piezo buzzer and button changed, potentiometer added         |

## See Also

For more information please visit [rabbitmax.com](http://rabbitmax.com/) and our [GitHub repositories](https://github.com/RabbitMax). If you have any questions or enquiries please contact us through [Facebook](https://www.facebook.com/RabbitMax-1632492473734364/), [Twitter](https://twitter.com/rabbitmaxcom) or [email](mailto:info@rabbitmax.com).

---
