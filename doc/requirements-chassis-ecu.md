# Requirements for the Chassis Controller PCB

1. The controller must be designed as an expansion board for the STM32F407G-DISC1 development board.
2. The controller must be powered by an external power source with a voltage range of 6 V to 30 V.
3. The controller must have protection against incorrect polarity connection of the power supply.
4. Screw terminal blocks should be used for power connections.
5. The controller must measure the input voltage of the power supply.
6. The controller must have a buzzer.
7. The controller must have 4 groups of output signals for motor control modules. Connector type: JST PH.  
   Signals in each group:
   - PWM signal with a frequency up to 20 kHz. Logical level 5 V.
   - Forward (F) — logic output for controlling the movement direction. Logical level 5 V.
   - Reverse (R) — logic output for controlling the movement direction. Logical level 5 V.
   - GND.
8. The controller must have 4 groups of inputs for encoders. Connector type: JST PH.  
   Signals in each group:
   - +5 V — power for the encoder.
   - GND.
   - Phase A — signal from the encoder responsible for tracking position or rotation. Used for determining direction along with the Phase B signal.
   - Phase B — signal that works in conjunction with Phase A for precise determination of direction and the number of rotations. The alternating signals of phases A and B make it possible to determine both speed and direction of movement.
9. The controller must have 4 outputs for connecting marker LEDs. The current through each LED must be limited to 15 mA. Connector type: JST PH.
10. The controller must have an output for connecting 3 status LEDs (red, yellow, green). The current through each LED must be limited to 15 mA. Connector type: JST PH.
11. The controller must have a serial interface connector with TTL levels. Connector type: JST PH.
12. The controller must have 4 inputs for ultrasonic sensors such as the HC-SR04. Connector type: JST PH.  
    Signals for each sensor:
   - VCC — power supply (+5 V).
   - GND — common (ground) wire.
   - TRIG — input signal for starting the ultrasonic wave. The controller sends a short pulse (10 microseconds) to initiate the measurement.
   - ECHO — output signal indicating the return time of the reflected ultrasonic wave. The duration of this signal is proportional to the distance to the object.
13. The controller must have a connector for the GY-BNO080 (IMU) module.
14. The controller must have a connector for the HC-05 (Bluetooth) module.
15. The dimensions of the controller board must not exceed 110x190 mm. Preferably, but not necessarily, within 100x100 mm.
16. The number of PCB layers should not exceed 4, preferably 2.
17. The controller board must have 4 mounting holes with a diameter of 3.2 mm at the corners for attaching to the chassis.
18. All SMD components should be placed on the side of the STM32F407G-DISC1 connector.
19. All connectors for modules, signals, and power should be placed on the opposite side from the STM32F407G-DISC1 board.
20. The PCB must be designed using KiCad EDA (https://www.kicad.org/).
21. All board components must be available for order from https://www.lcsc.com/.
