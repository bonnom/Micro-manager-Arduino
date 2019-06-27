## Micro-manager-Arduino
This repo contains a rewritten arduino "firmware" for micro-manger that is usable for newer arduino's
This is a work in progress but it is already usable for blanking, patterns and one DAC channel.

# Working Arduino boards:
* ItsyBitsy M4 
  - This sketch is written for this board. Please note that Pin 8 is not available!
* Teensy 3.2, 3.5 and 3.6
  - The sketch has to be partly rewritten for the DAC
# Not working boards:
  - Any esp8266 board
  - Any esp32 board

# Functions not implemented
Some functions are yet to be implemented:
* Currently the ADC does not work!
* Only one DAC channel is implemented!
* 
