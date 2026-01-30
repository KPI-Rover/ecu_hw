# KPI Rover Chassis Controller (ECU) Requirements Specification

This document defines the functional, electrical, and mechanical requirements for the KPI Rover Chassis Controller (ECU). It serves as a comprehensive specification for the design, development, and verification of the controller hardware and its interfaces.

## General Requirements

#### REQ.1 Power requirements:  
 1. The controller must be powered by an external power source with a voltage range of `6V to 30V`. 
 2. The controller should have protection against reverse polarity connection of the power source.
 3. Screw terminal blocks should be used for power connections.


#### REQ.4 Input voltage measurement
The controller should measure the input voltage by MCU.  

Implementation details: `MCU`: `POWER_SUPPLY_ADC`

#### REQ.5 Motors control
The controller should have 4 groups of output signals for motor control.  
Connector type: `JST PH`  
Pinout:
1. `PWM` with a frequency up to 20 kHz. Logic level 5V.
2. `Forward` (F) — logic output for direction control. Logic level 5V.
3. `Reverse` (R) — logic output for direction control. Logic level 5V.
4. `GND`

Implementation details: `PCA9685PW`

#### REQ.6 Encoders
The controller should have 4 groups of inputs for encoders.  
Connector type: `JST PH`  
Pinout:
1. `+3.3V` — encoder power source.
2. `GND`
3. `Phase A`
4. `Phase B`

Implementation details: `MCU`: `ENCx_A` and `ENCx_B`

#### REQ.7 External status LEDs
The controller should have an output for connecting 3 external status LEDs (red, yellow, green).
The current through each LED should be limited to 15 mA.  
Connector type: `JST PH`  
Pinout:
1. `GND`
2. `R` - Red led
3. `Y` - Yellow led
4. `G` - Green led

Implementation details: `PCA9685PW`

#### REQ.8 Ultrasonic sensors
The controller should have 2 inputs for HC-SR04 ultrasonic sensors.  
Connector type: `JST PH`  
Pinout:
1. `+5V`
2. `GND`
3. `TRIG`
4. `ECHO`

Implementation details: `MCU`: `USSx_TRIG` and `USSx_ECHO` 

#### REQ.9 Serial interfaces
The controller should have 2 serial interface connectors at TTL level (3.3V).  
Connector type: `JST PH`  
Pinout:
1. `GND`
2. `TX`
3. `RX`

Implementation details: `MCU`: `USARTx_TX` and `USARTx_RX`

#### REQ.10 External I2C interface
The controller should have connector to connect external I2C devices.  
Connector type: `JST PH`  
Pinout:
1. `SDA`
2. `SCL`
3. `3.3V`
4. `GND`

Implementation details: `MCU`: `EXT_I2C_SCL` and `EXT_I2C_SDA`

#### REQ.11 Servos
The controller should have 6 servo connectors.  
Connector type: `JST PH`  
Pinout:
1. `+5V`
2. `PWM`
3. `GND`

Implementation details: All `PWM` signals should be connected to `PCA9685PW`

#### REQ.12 Enable/Disable servos power
The controller should provide a way to enable/disable power of all servos by MCU.  

Implementation details: `MCU`: `SERVO_PWR`

#### REQ.13 CAN Interface
The controller should have connector for the CAN interface. 
The CAN driver `SN65HVD230` should be used.   
The termination resistor should be between the CAN High and CAN Low signals.  
Also, there should be a jumper to connect or disconnect the termination resistor.
Connector type: `JST PH`  
Pinout:
1. `GND`
2. `CAN High`
3. `CAN Low`

Implementation details: `MCU`: `CAN1_TX` `CAN1_RX`


#### REQ.16 Buzzer
The controller should have an onboard buzzer controlled by the MCU.

Implementation details: `PCA9685PW`

#### REQ.17 Onboard status LEDs
The controller should have four onboard status blue LEDs controlled by the MCU. The current through each LED should be limited to 5 mA.

Implementation details: `MCU`: `STATUS_LED_x`

#### REQ.18 IMU
The controller should have an onboard `MPU-6050` (IMU) module connected to the MCU.

Implementation details: `MCU`: `IMU_I2C_SCL`, `IMU_I2C_SDA`

#### REQ.19 DIP Switch
The controller should have an onboard 4-bit DIP switch connected to the MCU.

Implementation details: `MCU`: `DIPx`

#### REQ.20 MCU
The controller must be developed based on the STM32F407VGTx MCU.

#### REQ.21 Flashing connector
The controller must have an onboard connector for firmware flashing.  
Connector type: `JST PH`  
Pinout:
1. `+3.3V`
2. `SWCLK`
3. `GND`
4. `SWDIO`
5. `NRST`
6. `SWO`

#### REQ.22 Output power connector +5V
The controller must have an onboard connector to provide +5V power to external devices.
Connector type: `JST PH`  
Pinout:
1. `+5V`
2. `GND`

#### REQ.23 Output power connector +3.3V
The controller must have an onboard connector to provide +3.3V power to external devices.
Connector type: `JST PH`  
Pinout:
1. `+3.3V`
2. `GND`

## Mechanical Requirements

#### REQ.200 Dimensions
The dimensions of the controller board should not exceed 100x100 mm.

#### REQ.201 Layers
The number of PCB layers should be 2.
All unused PCB areas on both sides must be filled with a GND shield.

#### REQ.202 Mounting
The controller board should have 4 holes with a diameter of 3.2 mm at the corners for mounting to the chassis.

#### REQ.203 Components location
All SMD components must be placed on the `bottom` side.  
Except:  
- SMD connectors  
- 4 status LEDs  
- Buzzer if SMD
All connectors must be placed on the `top` side.

#### REQ.204 IDE
The printed circuit board should be designed using KiCad EDA ([https://www.kicad.org/](https://www.kicad.org/)).

#### REQ.205 Schematic documentation
The schematic must be created as a multipage KiCAD document, and each page must use the A3 page format.

#### REQ.206 Components ordering
All components should be available for order on the website: [https://www.lcsc.com/](https://www.lcsc.com/).  
Each KiCAD Schematic component should have the field 'LCSC Part'.
