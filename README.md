This repo contains a more universal Micro-Manager arduino firmware for the original Arduino device adapter (NOT Arduino32bitBoards). The firmware is written for some newer arduino boards. It is a work in progress and the firmware isn't thoroughly tested yet. 

There is an other github that has firmware for the newer Arduino32bitBoards device adapter: https://github.com/bonnom/Arduino32BitBoards


For questions, go to the "Issue section" and ask over there!

# Micro-manager-Arduino
The original micro-manager arduino firmware is specifically written for the Arduino uno and won't work on the newer and faster arduinos. This project aims to rewrite the original firmware to get compatibility with the newer arduino compatible boards. The original firmware and guide can be found on the micro-manager website [link](https://micro-manager.org/wiki/Arduino).

This GitHub repo contains two types of firmwares, one is a normal one. This firmware works exactly like the original firmware.
There is also firmware that has DAC_Blanking in the name. This firmware replaced the first (or two) channels with the DAC channels. This allows the DAC channels to be used as a Shutter.

Please keep in mind that many newer Arduino boards gets damaged when 5V is applied on the input pins. 
Voltage level conversion must be needed when using 5V input on not 5V tolerant boards. Also the digital output is 3.3V, most devices that work with 5V input also work fine with 3.3V input but this is not guaranteed.

The Teensy 3.5 is currently the recommended board.

## Contents
  - [Advantages of the sketches provided in this repo](#advantages-of-the-sketches-provided-in-this-repo)
  - [Arduino boards information](#arduino-boards-information) contains settings and pinouts
  - [Installation](#installation)
  - [Drivers](#drivers)
  - [Known bugs](#bugs)
  
## Advantages of the sketches provided in this repo
* Works on newer and faster boards, pin registers don't have to be used
* Easier to adapt since pin registers aren't used
  * This allows PWM + blanking
  * DAC + blanking
  * Possibility to choose different pins
* No need for external DAC with most boards


## Arduino boards information:
### Default pinout (Not DAC-Blanking)
These are the defaults pinouts unless stated otherwise
- Trigger: Pin 5 (not for ItsyBitsy M4)
- Channel 1: Pin 8 (Pin 7: ItsyBitsy M4)
- Channel 2: Pin 9
- Channel 3: Pin 10
- Channel 4: Pin 11
- Channel 5: Pin 12
- Channel 6: Pin 13

### Default pinout DAC-Blanking firmware
- Trigger: Pin 5 (not for ItsyBitsy M4)
- Channel 1: (Depends on Board, see below)
- Channel 2: (Depends on Board, see below)
- Channel 3: Pin 10
- Channel 4: Pin 11
- Channel 5: Pin 12
- Channel 6: Pin 13

### Adafruit
* ItsyBitsy M4
  - Baudrate: 500,000
  - Trigger: Pin 2
  - DAC 1: Pin A0
  - DAC 2: Pin A1
  - The ADC does not work at the moment because of DAC implementation!
  - KEEP IN MIND: NOT 5V TOLERANT!!

* Adafruit SAMD (Works on M4 Feather, M4 express, etc.)
  - Baudrate: 500,000
  - DAC 1: Pin A0
  - DAC 2: Pin A1
  - The ADC does not work at the moment because of DAC implementation!
  - KEEP IN MIND: NOT 5V TOLERANT!!
  
### ESP32
  - Baudrate: 115200
  - DAC1 on pin 25 and DAC2 on pin 26
  - ADC not implemented
  - Able to set PWM frequency and Resolution
  - Low Price boards available       
  - KEEP IN MIND: NOT 5V TOLERANT!!
  
 
### Teensy 3.x Boards
#### All 3.x boards
 - Baudrate: 500,000
 - Able to set PWM frequency and Resolution, for more information [link](https://www.pjrc.com/teensy/td_pulse.html)
 - At least one DAC
 - handy: Pinouts page [https://www.pjrc.com/teensy/pinout.html]
 
* Teensy 3.1 & 3.2
  - Seems to work fine, but more testing is needed
  - All currently used pins in the sketch are 5V tolerant
  - Only one DAC on pin A14
  - All other pins are the same as the original UNO firmware

* Teensy 3.5 (Recommended)
  - Not yet tested
  - All currently used pins in the firmware are 5V tolerant
  - DAC1 on pin 21 and DAC2 on pin 22
  - Able to set PWM frequency and Resolution

* Teensy 3.6
  - Uses same sketch as teensy 3.5
  - Faster than teensy 3.5
  - KEEP IN MIND: NOT 5V TOLERANT!!
  
## Not working boards:
  - Arduino Due
  - Sipeed Maix boards
  

## Installation
This page is an overview of the installation links for Arduino and the respective boards

### Arduino (Required)
Arduino offers two solutions, an online editor and a local Integrated development environment (IDE) program.
It is recommended to use the local IDE software.
The page for the software can be found [here](https://www.arduino.cc/en/Main/Software)

### Adafruit
Adafruit makes two programming environments to use on their 32-bit boards. One is circuit python and Arduino. Circuitpython currently doesn't work with micro-manager.
Guide for installing the Adafruit Feather M4 board can be found [here](https://learn.adafruit.com/adafruit-feather-m4-express-atsamd51/setup)

### Esp32
ESP32 arduino core installation link can be found [here](https://github.com/espressif/arduino-esp32/blob/master/docs/arduino-ide/boards_manager.md)
Also when using an windows version older than Windows 10 driver installation might be needed. There are two types of usb to serial chips used with each their own driver. If you are not sure what IC is used just install both drivers.

These two are the most common type of drivers:
* [SiLabs cp210x](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)
* [CH340] (https://cdn.sparkfun.com/assets/learn_tutorials/8/4/4/CH341SER.EXE)

### Teensy boards
Teensy requires its own installation software that can be downloaded [here](https://www.pjrc.com/teensy/td_download.html)

## Drivers
On windows 10 the Arduino-compatible board drivers are automatically installed, but this is not the case for windows 7 and below.

There are two ways to install the Arduino-compatible board drivers, the first is to install the Arduino IDE and than to install the board under boards-manager. The second way is to install the standalone driver packages. The standalone drivers are listed below.

### Adafruit Serial Drivers:
* Most general driver package
* Includes drivers for FTDI
* Includes SiLabs CP210x drivers

[Adafruit Drivers](https://github.com/adafruit/Adafruit_Windows_Drivers/releases/latest)

[Source Drivers](https://learn.adafruit.com/adafruit-arduino-ide-setup/windows-driver-installation)

### CH340G:
* Used on a lot of Arduino-compatible boards from China

[Windows Drivers](https://cdn.sparkfun.com/assets/learn_tutorials/8/4/4/CH341SER.EXE)

[Source Drivers](https://www.sparkfun.com/products/14050)

### FTDI Drivers
* Used on a lot of arduino-compatible boards (also included in the Adafruit Serial Driver package)
(Drivers)[https://www.ftdichip.com/Drivers/VCP.htm]

### SiLabs Drivers
* Used on a lot of arduino-compatible boards (also included in the Adafruit Serial Driver package)

(Drivers) [https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers]

### Teensy Serial Drivers:
[Windows Serial Installer](https://www.pjrc.com/teensy/serial_install.exe)

[Source Drivers](https://www.pjrc.com/teensy/td_download.html)

## Bugs
When a bug isn't listed here, please report it under 'Issues' above.

* Using different exposure times in multi-dimensional acquisition can lead to problems. It is not yet known if this is caused by Arduino or the Andor camera

* The Arduino will behave slow and sporadic under multi-dimensional acquisition if not a channel has been selected first under 'Configuration settings' in the main micro-manager window.
