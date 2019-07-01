This repo contains a more universal arduino firmware that works on some 32-bit arduino boards. It is a work in progress and the firmware isn't thoroughly tested yet. 

# Micro-manager-Arduino
The original micro-manager arduino firmware is specifically written for the Arduino uno and won't work on the newer and faster 32-bit arduinos. This project aims to rewrite the original firmware to get compatibility with the newer arduino compatible boards. The original firmware and guide can be found on the micro-manager website [link](https://micro-manager.org/wiki/Arduino).

Please keep in mind that the 32-bit boards in general don't have a 5V output and that most of them don't have 5V tolerant inputs. 
A lot of devices should be triggered just fine with the arduinos 3.3V output but it is not guaranteed.
Voltage level conversion must be needed when using 5V input on not 5V tolerant boards.

## Working Arduino boards:
* Teensy 3.2 & 3.1
  - Works sometimes, need more testing
  - All currently used pins in the sketch are 5V tolerant, for non-5V tolerant pins see [link](https://www.pjrc.com/teensy/teensy31.html)
  - DAC pin A14
  - All other pins are the same as the original UNO firmware
  - Handy: [Pinout](https://www.pjrc.com/teensy/card7a_rev1.png)
  
* ItsyBitsy M4 
  - The ADC does not work at the moment because of DAC implementation
  - KEEP IN MIND: NOT 5V TOLERANT!!
  
* Teensy 3.6
  - Teensy 3.6: NOT 5V TOLERANT!!
  
## Not working boards:
  - Any esp8266 board
  - Any esp32 board
  - Arduino Due

## To be tested:
 - Teensy LC
 - A SAMD21 board
 - Teensy 3.5 (Very likely Works)

## Functions not implemented
Some functions are yet to be implemented:
* Only one DAC channel is implemented!
