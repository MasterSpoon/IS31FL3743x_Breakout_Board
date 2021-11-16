
# IS31FL3743x Breakout Board

This ia a Dev board for the LUMISSIL Microsystems IS31FL3743A & IS31FL3743B LED drivers with the main difference being the A variant is I2C-1MHz and the B variant SPI-12MHz.

[IS31FL3743A datasheet](https://www.lumissil.com/assets/pdf/core/IS31FL3743A_DS.pdf)
[IS31FL3743B datasheet](https://www.lumissil.com/assets/pdf/core/IS31FL3743B_DS.pdf)

The are both 18 x 11 matrix drivers capable of supporting up to 198 LEDs / 66 RGB LEDs.
With an average current on each LED of 3.03mA they are suitable for SMD LEDs.
Eg. [Foshan NationStar Optoelectronics FM-B2020RGBA-HG ](https://lcsc.com/product-detail/Light-Emitting-Diodes-LED_Foshan-NationStar-Optoelectronics-FM-B2020RGBA-HG_C108793.html )

Parts list

| Part | Package | Location | Notes |
|------|---------|----------|-------|
| ISSI Driver | UQFN-40(5x5) | U1 | IS31FL3743A or IS31FL3743B |
| 100nF Capacitor | 0603 | C1 & C2 | LED driver Capacitors |
| 1uF Capacitor | 0603 | C3 & C4 | LED driver Capacitors |
| 20ohm Resistor | 0805 | R1-R18 | Series Resistors for CS1-CS18 respectively |
| 10K Resistor | 0805 | R19 | ISET Resistor |
| 2K Resistor | 0805 | R20 & R21 | I2C pull up Resistors |

General Notes
- In default configuration the breakout board is setup for the IS31FL3743A driver however if easily changed to suit the IS31FL3743B driver. 
- CSx Resistors have been listed as 20ohm, if using for RGB change the Resistors to 51ohm for the CSx channels that will be used for Red.
- SDB Pin is pulled high through the solder jumper, if wanting to control through MCU cut the jumper trace and solder a wire to the pad above the S Pin on the SDB solder jumper.

IS31FL3743A Notes
- I2C Pullup Resistors are connected to VCC, if using an MCU that is not 5V tollerant will need to omit R20 & R21 and provide pullup Resistors elsewhere.
- I2C address default has ADDR1 & ADDR2 Pulled to GND. Solder jumpers can be used to change if required.
    - GN1VC Sets ADDR1 between GND and VCC, 514 sets ADDR1 between Pin 5(SCL) & Pin 4(SDA).
    - GN2VC Sets ADDR1 between GND and VCC.
    - **WARNING** Before setting any solder jumpers first cut the jumper trace for the ADDR Pin first.
    - Note : Not all address combinations have been made available through solder jumpers. 

IS31FL3743B Notes
- Omit R20 & R21 Resistors as these are for I2C Pullups and will pull MOSI & SCL Pins high.
- Cut the solder bridge traces for GN1VC & GN2VC to avoid the CS and MISO Pins being pulled to GND.
- Silkscreen is based on IS31FL3743A driver. Differences for IS31FL3743B are

| Silkscreen | Function |
|------------|----------|
| SDA | MOSI |
| SCL | SCK |
| A1 | CS |
| A2 | MISO |
