# Logitech Z906 Serial Control with ESPHome

This project was born from the idea of bringing the work of [nomis](https://github.com/nomis/z906-protocol) and others into the ESPHome ecosystem.  
I'm publishing my test hoping someone smarter than me can figure out what the problem is.

My ultimate goal is to replicate the original Logitech Z906 console as faithfully as possible using an ESP32, with the ultimate ambition of fully rebuilding the console (including LEDs, buttons, rotary encoder, etc.) on ESPHome. (if that makes sense)

## What works

- Power ON/OFF (with EEPROM save and power-up time reset)
- Input selection (TRS, RCA, Opticals)
- Volume control (up/down)
- Reading and decoding the full amplifier state (power, input, volume, effects, digital signal status)
- UART communication with buffer flush and timing management

## What does NOT work (yet)

Despite i get right rensponse from serial like: AA 0A 14 12 17 00 2B 02 00 03 03 01 00 03 01 0C 00 01 05 04 00 00 00 my audio is not working
- **Audio output does NOT work** when using ESPHome, even though the serial protocol and state reporting are correct.
- Pluggin back the the original console or [LewisSmallwood's C++ firmware](https://github.com/LewisSmallwood/Logitech-Z906-HTTP-API), audio works perfectly with the same cables and source (tested input 1,2,3,4 with pc and android smart tv).
- I can't understand what is the issue 

## Protocol

- Serial protocol based on the excellent documentation by [nomis](https://github.com/nomis/logitech-z906).
- Command structure and timing inspired by [zarpli](https://github.com/zarpli/logitech-z906) and [LewisSmallwood]([https://github.com/LewisSmallwood/Logitech-Z906-HTTP-API](https://github.com/LewisSmallwood/IoT-Logitech-Z906)) C++ implementations.

## How to use

1. Flash your ESP32/ESP8266 with ESPHome and this configuration (`z906.yaml`).
2. Connect the UART TX/RX pins to the Z906 amplifier serial port.
3. Use ESPHome web interface to control the amplifier.

## Extra: Z906 Serial Response Decoder

I have also created an **Excel file** to decode the amplifier's serial response:  
Just paste the response string, and the table will clearly show the meaning and value of each byte.

## Call for help

If you are smart enough to figure out why audio does not work (even if you don't have a Z906 for testing), I am available for any remote testing or debugging!  
Any contribution or insight is welcome. Feel free to clone the repository and open a pull request or issue on GitHub.
Any contribution, suggestion, or investigation is welcome!

## References

- [nomis/z906-protocol](https://github.com/nomis/z906-protocol) (serial protocol documentation)
- [zarpli/logitech-z906](https://github.com/zarpli/logitech-z906) (C++ implementation)
- [LewisSmallwood/Logitech-Z906-HTTP-API]([https://github.com/LewisSmallwood/Logitech-Z906-HTTP-API](https://github.com/LewisSmallwood/IoT-Logitech-Z906)) (C++/HTTP API)

---

**If you manage to get audio working with ESPHome, please share your solution!**
