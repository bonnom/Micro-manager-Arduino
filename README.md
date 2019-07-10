This repo contains a more universal arduino firmware that works on some 32-bit arduino boards. It is a work in progress and the firmware isn't thoroughly tested yet. 

# Micro-manager-Arduino
The original micro-manager arduino firmware is specifically written for the Arduino uno and won't work on the newer and faster 32-bit arduinos. This project aims to rewrite the original firmware to get compatibility with the newer arduino compatible boards. The original firmware and guide can be found on the micro-manager website [link](https://micro-manager.org/wiki/Arduino).

Please keep in mind that most 32-bit arduinos boards gets damaged when 5V is applied on the input pins. 
Voltage level conversion must be needed when using 5V input on not 5V tolerant boards.

Also the digital output is 3.3V, most devices that work with 5V input also work fine with 3.3V input but this is not guaranteed.

## Advantages of 32 Bit-boards
* Baudrate increased to 500 000, nearly 9 times the transferspeed between Arduino and Micro-Manager (there are some exceptions).
* Some 32-bit Arduinos have a buildin DAC. This is only 3.3V out, amplification might be needed.
* Easier to change preferred pins

## Working Arduino boards:
* ESP32
  - Baudrate: 115200
  - DAC1 on pin 25 and DAC2 on pin 26
  - ADC not implemented
  - KEEP IN MIND: NOT 5V TOLERANT!!
  
* ItsyBitsy M4 
  - The ADC does not work at the moment because of DAC implementation
  - Channel 8 has become channel 7
  - KEEP IN MIND: NOT 5V TOLERANT!!
  
* Teensy 3.1 & 3.2
  - Seems to work fine, but more testing is needed
  - All currently used pins in the sketch are 5V tolerant, for non-5V tolerant pins see [link](https://www.pjrc.com/teensy/teensy31.html)
  - Only one DAC pin A14
  - All other pins are the same as the original UNO firmware
  - Handy: [Pinout](https://www.pjrc.com/teensy/card7a_rev1.png)

* Teensy 3.5
  - Not yet tested
  - All currently used pins in the sketch are 5V tolerant
  - DAC1 on pin 21 and DAC2 on pin 22

* Teensy 3.6
  - Teensy 3.6: NOT 5V TOLERANT!!

  
  
## Not working boards:
  - Esp8266 board
  - Arduino Due
  - Sipeed Maix boards

## To be tested:
 - Teensy LC
 - ESP32
 - A SAMD21 board
 - Teensy 3.5 (Very likely Works)

## Functions not implemented
Some functions are yet to be implemented:
