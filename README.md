##\*uino-mx250

The \*uino-mx250 was designed for my son Mathew. As a mostly though-hole design, it should be easy to assemble even for a beginner.  The only surface mount component is the micro USB connector. Personally I much prefer micro USB over the full sized or mini connector. Unfortunately I was unable to find a through-hole micro USB.  Having the one surface mounted component was a compromise I was willing to take.

The board uses the PIC32MX250F128B which is available in a 28 pin through-hole package and includes an on-board USB peripheral.  The PIC32MX250F128B is supported by [chipKIT Core](http://chipkit.net/wiki/index.php?title=ChipKIT_core) for the [Arduino](https://www.arduino.cc/) development environment.  Select the chipKIT DP32.

###Important Note

PCB have been ordered from SeeedStudio FusionPCB service. There is no working sample yet.

###Licensing

This work is licensed under a Creative Commons Attribution-ShareAlike 3.0 Unported License, CC BY-SA.

You are free to copy, distribute and transmit the work. You must attribute the work in the manner specified by the author or licensor (but not in any way that suggests that they endorse you or your use of the work). you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.  

Please refer to [http://creativecommons.org/licenses/by-sa/3.0/] for the license.

###Credit

The \*uino-mx250 is derived from previous work done by:

- The [chipKIT DP32](https://reference.digilentinc.com/chipkit_dp32/refmanual)
- The [HelvePic32](http://www.mathias-wilhelm.de/arduino/embedded-boards/helvepic32)

###Details

Aside from teaching my son how to solder, the motivation for the \*uino-mx250 was to create a through-hole chipKIT board that can make use of existing shields.  The \*uino-mx250 is intended to operate at 3.3V as this is the operating voltage of the PIC32MX250F128B.

Mostly due to the use of the USB peripheral, the PIC32MX250F128B has less available I/O than the ATmega328P. Some compromises and choices were necessary to map the PIC32MX250F128B I/O to the shield pins.  In particular analog pins A1, A2, A3, A4 and A5 are directly connected to digital pins D12, D10, D11, D9 and D8.  This is important to remember!

PIC32MX250F128B I/O is mapped to shield pins to preserve the special functions of the digital pins.  Thanks to PIC32 mappable peripheral pins I2C, SPI, serial and PWM functions are were they should be. Still, some compromises were necessary, either D3 or D11 can use OC2 for PWM, but not both at the same time.

###Pin Mapping

```
        PIC32MX250F128B                                     Peripheral
D0      SOSCO/RPA4/T1CK/CTED9/PMA1/RA4                      RX1         RxD
D1      TDI/RPB7/CTED3/PMD5/INT0/RB7                        TX1         TxD
D2      PGED3/RPB5/PMD7/RB5
D3      TCK/RPB8/SCL1/CTED10/PMD4/RB8                       OC2         PWM
D4      TDO/RPB9/SDA1/CTED4/PMD3/RB9
D5      SOSCI/RPB4/RB4                                      OC1         PWM
D6      AN11/RPB13/CTPLS/PMRD/RB13                          OC4/5       PWM
D7      AN9/C3INA/RPB15/SCK2/CTED6/PMCS1/RB15

D8  A5  AN5/C1INA/C2INC/RTCC/RPB3/SCL2/RB3 
D9  A4  AN4/C1INB/C2IND/RPB2/SDA2/CTED13/RB2                OC4/5       PWM
D10 A2  PGED1/AN2/C1IND/C2INB/C3IND/RPB0/RB0                OC3         PWM
D11 A3  PGEC1/AN3/C1INC/C2INA/RPB1/CTED12/RB1               OC2 DO1     PWM MOSI
D12 A1  PGEC3/VREF-/CVREF-/AN1/RPA1/CTED2/PMD6/RA1          DI          MISO
D13     CVREFOUT/AN10/C3INB/RPB14/SCK1/CTED5/PMWR/RB14      SCK1        SCK

A0      PGED3/VREF+/CVREF+/AN0/C3INC/RPA0/CTED1/PMD7/RA0
A1 D12  PGEC3/VREF-/CVREF-/AN1/RPA1/CTED2/PMD6/RA1
A2 D10  PGED1/AN2/C1IND/C2INB/C3IND/RPB0/RB0
A3 D11  PGEC1/AN3/C1INC/C2INA/RPB1/CTED12/RB1
A4 D9   AN4/C1INB/C2IND/RPB2/SDA2/CTED13/RB2                SDA2        SDA
A5 D8   AN5/C1INA/C2INC/RTCC/RPB3/SCL2/RB3                  SCL2        SCL

```

