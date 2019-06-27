This repo contains a more universal arduino firmware that works on some 32-bit arduino boards. It is a work in progress and not everything works.

# Micro-manager-Arduino
The original micro-manager arduino firmware is specifically written for the Arduino uno and won't work on the newer and faster 32-bit arduinos. This project aims to rewrite the original firmware to get compatibility with the newer arduino compatible boards. The original firmware and guide can be found on the micro-manager website [link](https://micro-manager.org/wiki/Arduino)

## Working Arduino boards:
* ItsyBitsy M4 
  - This sketch is written for this board. Please note that Pin 8 is not available!
* Teensy 3.2, 3.5 and 3.6
  - The sketch has to be partly rewritten for the DAC
## Not working boards:
  - Any esp8266 board
  - Any esp32 board

## Functions not implemented
Some functions are yet to be implemented:
* Currently the ADC does not work!
* Only one DAC channel is implemented!
