# Requirements for the Raspberry Pi Power Supply PCB

1. The board must be designed as a HAT (Hardware Attached on Top) module. The board must comply with all requirements except for the presence of EEPROM. Requirements: [https://github.com/raspberrypi/hats/blob/master/designguide.md](https://github.com/raspberrypi/hats/blob/master/designguide.md)
2. The board must be based on the AP64500SP DC-DC converter ([https://www.diodes.com/assets/Datasheets/AP64500.pdf](https://www.diodes.com/assets/Datasheets/AP64500.pdf)).
3. The board must provide an output voltage of 5.1 V and a current of 5 A.
4. Power should be supplied to the Raspberry Pi through the 40-pin connector. All GND pins must be connected together. Both +5 V pins must be used.
5. The board must have an additional +5 V output connector to allow it to be used separately for powering other devices.
6. Screw terminal blocks should be used for power input and the additional +5 V output.
7. The board must have protection against incorrect polarity connection of the power source.
8. The board must have additional protection against output voltage overvoltage.
9. The board must have a serial interface connector with TTL levels for connection to the chassis controller. Connector type: JST PH.
10. The board must have serial and I2C interface connectors for connecting a GPS sensor with a compass. Connector types: JST PH.
11. The board must have a green LED connected to +5 V to indicate power availability.
12. The PCB must be designed using KiCad EDA (https://www.kicad.org/).
13. All board components must be available for order from https://www.lcsc.com/.
