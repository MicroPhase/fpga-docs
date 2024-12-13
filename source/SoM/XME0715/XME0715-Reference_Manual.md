# **XME0715 Reference Manual**

## Revision History

| Revision | Time       | Description   |
| :------- | :--------- | :------------ |
| Rev. 1.0 | 2024.12.09 | First Release |
|          |            |               |

## CopyRight Notice:

Copyright ©2024 by MicroPhase Technologies (Shanghai) Co. Ltd. All rights are reserved.

## Development Environment:

Vivado 2018.3 is from Xilinx website

<https://www.xilinx.com>

## WeChat Public Number:

![](./XME0715-Reference_Manual.assets/VX.png)

<div style="page-break-after:always;"></div>


## ●1. Overview

​	XME0715 is a industrial-grade system module based on Xilinx Zynq-SoC  from Microphase Technology.  
​	It integrates 1GB DDR3 RAM, 32MB SPI flash, 8GB eMMC flash, Gigabit Ethernet PHY transceiver, USB PHY transceiver, and a large number of configurable I/Os expandable via high-speed connectors. With a size of only 5 x 6cm, the module is small and flexible enough to be used in a wide range of applications.

### ○Board Layout

![](./XME0715-Reference_Manual.assets/0715_BL.png)

### ○Key Features

- Xilinx XC7Z015-2CLG485I  
- DDR3: 1GB DDR3 RAM 
- Flash: 256Mbit QSPI Flash, 8GB eMMC Flash.  
- LED: 1 Power LED, 1 FPGA Done LED;  
  &ensp;&ensp;&ensp;&ensp;&ensp;2 user's LED, 1 PS(Processing System ) control, 1 PL(Programmable Logic) control.  
- PL GPIO: 142, 96 GPIOs are Adjustable Voltage,  
  &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;Can be configured as 71 differential pairs  
- Giga ETH: 10/100/1000M Adaptive.  
- USB Host: USB2.0 PHY(USB3320)  
- CLOCK: 1 33.33Mhz active crystal oscillator provides a stable clock for the PS system.  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; 1 50Mhz active crystal oscillator provides additional clocks for the PL logic.     

### ○Block diagram
![XME0715_Block-01](./XME0715-Reference_Manual.assets/XME0715_Block-01.png)

### ○Mechanical Spec
![](./XME0715-Reference_Manual.assets/0715MS.png)

## ●2. Function Resources

### ○FPGA

- 766 MHz dual-core Cortex-A9 processor

- DDR3L memory controller with 8 DMA channels and 4 

- High Performance AXI3 Slave ports

- High-bandwidth peripheral controllers: 1G Ethernet, USB 2.0, SDIO

- Low-bandwidth peripheral controllers: SPI, UART, CAN, I2C

- Programmable from JTAG, Quad-SPI flash, and microSD card

- Programmable logic equivalent to Artix-7 FPGA  
  LUTs: 46,200  
  DSP Slices: 160   
  Logic Cells: 74K   
  Flip-Flops: 92,400  
  Total Block RAM: 3.3Mb 
  
- Analog Mixed Signal (AMS) / XADC:  2x 12 bit, MSPS ADCs with up to 17 Differential Inputs

- Security: AES & SHA 256b Decryption & Authentication for Secure Programmable Logic Config

### ○DDR3

The module uses two 16-bit DDR3 memory chips to form a 32-bit bit-width, 1GB capacity.

| Signal Name   | PIN Number | Signal Name    | PIN Number |
| ------------- | ---------- | -------------- | ---------- |
| PS_DDR3_A0    | M19        | PS_DDR3_D9     | G22        |
| PS_DDR3_A1    | M18        | PS_DDR3_D10    | L22        |
| PS_DDR3_A2    | K19        | PS_DDR3_D11    | L21        |
| PS_DDR3_A3    | L19        | PS_DDR3_D12    | L20        |
| PS_DDR3_A4    | K17        | PS_DDR3_D13    | K22        |
| PS_DDR3_A5    | K18        | PS_DDR3_D14    | J22        |
| PS_DDR3_A6    | J16        | PS_DDR3_D15    | K20        |
| PS_DDR3_A7    | J17        | PS_DDR3_D16    | M22        |
| PS_DDR3_A8    | J18        | PS_DDR3_D17    | T20        |
| PS_DDR3_A9    | H18        | PS_DDR3_D18    | N20        |
| PS_DDR3_A10   | J20        | PS_DDR3_D19    | T22        |
| PS_DDR3_A11   | G18        | PS_DDR3_D20    | R20        |
| PS_DDR3_A12   | H19        | PS_DDR3_D21    | T21        |
| PS_DDR3_A13   | F19        | PS_DDR3_D22    | M21        |
| PS_DDR3_A14   | G19        | PS_DDR3_D23    | R22        |
| PS_DDR3_BA0   | L16        | PS_DDR3_D24    | Y20        |
| PS_DDR3_BA1   | L17        | PS_DDR3_D25    | U22        |
| PS_DDR3_BA2   | M17        | PS_DDR3_D26    | AA22       |
| PS_DDR3_NCAS  | P20        | PS_DDR3_D27    | U21        |
| PS_DDR3_CKE   | T19        | PS_DDR3_D28    | W22        |
| PS_DDR3_CLK_N | N18        | PS_DDR3_D29    | W20        |
| PS_DDR3_CLK_P | N19        | PS_DDR3_D30    | V20        |
| PS_DDR3_NCS   | P17        | PS_DDR3_D31    | Y22        |
| PS_DDR3_DM0   | B22        | PS_DDR3_DQS_N0 | D21        |
| PS_DDR3_DM1   | H20        | PS_DDR3_DQS_N1 | J21        |
| PS_DDR3_DM2   | P22        | PS_DDR3_DQS_N2 | P21        |
| PS_DDR3_DM3   | AA21       | PS_DDR3_DQS_N3 | W21        |
| PS_DDR3_D0    | D22        | PS_DDR3_DQS_P0 | C21        |
| PS_DDR3_D1    | C20        | PS_DDR3_DQS_P1 | H21        |
| PS_DDR3_D2    | B21        | PS_DDR3_DQS_P2 | N21        |
| PS_DDR3_D3    | D20        | PS_DDR3_DQS_P3 | V21        |
| PS_DDR3_D4    | E20        | PS_DDR3_NRST   | F20        |
| PS_DDR3_D5    | E22        | PS_DDR3_ODT    | P18        |
| PS_DDR3_D6    | F21        | PS_DDR3_NRAS   | R18        |
| PS_DDR3_D7    | F22        | PS_DDR3_NWE    | R19        |
| PS_DDR3_D8    | G21        |                |            |

### ○Giga ETH

The RTL8211F chip supports 10/100/1000M network transfer rate and communicates with the MAC layer of the Zynq7000 PS system via the RGMII interface. It supports MDI/MDX adaptation, multiple speed adaptation, master/slave adaptation and MDIO bus support for PHY register management.

### ○USB Host

The USB2.0 transceiver on-board is the USB3320C-EZK, which supports the ULPI standard interface. It's connected with ZYNQ's bus interface to enable high-speed USB2.0 Host mode data communications.

### ○USB UART

A USB to UART chip, the CH340, is provided for user connection to the host PC.

| Signal Name |   Pin Name   | Pin Number |     Explain      |
| :---------: | :----------: | :--------: | :--------------: |
|   UART_TX   | PS_MIO15_500 |     C5     | UART data output |
|   UART_RX   | PS_MIO14_500 |     C8     | UART data output |

### ○eMMC

The module includes an 8GB eMMC interface (PS_SDIO1) for system files or data storage. It can also serve as a secondary boot device alongside the QSPI flash. The interface is PS BANK501 MIO[46-51].

| Signal Name  | Pin Name  | Pin Number |
| ------------ | --------- | ---------- |
| PS_MIO48_501 | MMC_CLK   | D12        |
| PS_MIO47_501 | MMC_CMD   | B13        |
| PS_MIO46_501 | MMC_DATA0 | D11        |
| PS_MIO49_501 | MMC_DATA1 | C9         |
| PS_MIO50_501 | MMC_DATA2 | D10        |
| PS_MIO51_501 | MMC_DATA3 | C13        |

### ○JTAG

The JTAG signal link of the XME0726 is connected to the expansion connector.

|  Signal  | JM3 Pin Number | Explain                                           |
| :------: | :------------: | ------------------------------------------------- |
| VCC_3V3  |       13       | **Module voltage output**, JTAG reference voltage |
| FPGA_TDI |       21       | Input (3.3V)                                      |
| FPGA_TDO |       17       | Output (3.3V)                                     |
| FPGA_TCK |       15       | Input (3.3V)                                      |
| FPGA_TMS |       23       | Input (3.3V)                                      |
|   GND    |       19       | Connect to the GND signal on the module           |

### ○Boot Config

Configure the ZYNQ startup mode using core module pins PIN119 (MODE0) and PIN120 (MODE1). The ZYNQ configuration schematic is shown below.

![](./XME0715-Reference_Manual.assets/BOOT.png)

### ○Quad-SPI Flash

On-board 256M Quad-SPI Flash memory W25Q256FVEI is used to store initial FPGA configuration and user’s application as well as data.

| Position |    Model    | Capacity | Factory |
| :------: | :---------: | :------: | :-----: |
|    U4    | W25Q256FVEI | 256 Byte | Winbond |

### ○Clock

The XME0715 core board provides a 33.3Mhz active clock for the PS system and a 50Mhz active clock for the PL system. 

| Position | Signal Name | Frequency | Pin Number/Pin Name |
| :------: | :---------: | :-------: | :-----------------: |
|    U2    | PS_CLK_33d3 | 33.333Mhz |     PS_CLK_500      |
|    U6    | PL_CLK_50M  |   50Mhz   |         Y14         |

### ○Power

**Please note that the power input of XME0715 is +5V. We recommend using a 5V/2A power supply.** 

The module powers up in a cascading sequence: 1.0V- > 1.8V -> 1.5V- > 3.3V. The 3.3V output will be powered up last, and at the same time, it will provide the PG signal of system power status.

### ○LED

The XME0715 board includes four LEDs: a power indicator, an FPGA configuration status light, a PL-controlled user LED, and a PS-controlled user LED.  
The LED signals are described in the following table.  

| LED  | FPGA Pin/<br />FPGA Name | Note                                                         |
| :--: | ------------------------ | ------------------------------------------------------------ |
|  D4  | --                       | Power LED                                                    |
|  D1  | T10                      | FPGA configuration status LED, lit after successful FPGA configuration |
|  D2  | G14/PS_MIO0_500          | LED on when FPGA PS_MIO0_500 output is low                   |
|  D3  | T16                      | LED on when FPGA T16 output is low                           |

### ○Expansion Ports

The XME0715 uses three sets of connectors, JM1, JM2 and JM3, for the FPGA IO signals and Ethernet interface.  
3 x AXK600337YG, 100Pin, 0.5mm Pitch 

| Core Board Connector Models | Based Board Connector Models | Manufacturers | Mated height |
| --------------------------- | ---------------------------- | ------------- | ------------ |
| AXK600337YG                 | AXK500137YG                  | Panasonic     | 3mm          |

Description:  
1. Bank34 IO level depends on JM1 Pin11,13 voltage input, input range 1.2V-3.3V.
2. Bank35 IO level depends on JM2 Pin91,93 voltage input, input range 1.2V-3.3V.
3. SD Signal (JM3 Pin73,75,77-Pin85) voltage is 1.8V.
4. MIO9-MIO13, UART, JTAG, RESET level is 3.3V.
5. Please refer to the ‘[XME0715_Pinout_Table_R20](https://github.com/MicroPhase/fpga-docs/blob/master/others/XME0715_Pinout_Table_R20.xlsx)’ for detailed pin definitions of the XME0715 and its carrier board.

## ●3. Related Documents  

### ○XME0715
- [XME0715_R20 Schematic](https://github.com/MicroPhase/fpga-docs/blob/master/schematic/XME0715_R20.pdf) (PDF)
- [XME0715_R20 Dimensions](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/XME0715/XME0715_R20_Dimensions.pdf) (PDF)  
- [XME0715_R20 Dimensions source file](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/XME0715/XME0715_R20_Dimensions_source_file.dxf) (DXF)  
### ○PE100
- [PE100 Reference Manual](https://documentation-of-microphase-fpga-board.readthedocs.io/en/latest/CARRIER_BOARD/PE100/PE100-Reference_Manual.html)(HTML)
- [PE100_R11 Schematic](https://github.com/MicroPhase/fpga-docs/blob/master/schematic/PE100_R11.pdf) (PDF)
- [PE100_R11 Dimensions](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/PE100/PE100_R11_Dimensions.pdf) (PDF)  
- [PE100_R11 Board source file](https://github.com/MicroPhase/fpga-docs/blob/master/others/PE100_R11_Board_source_file.brd) (Brd) 
### ○PE300
- PE300 Reference Manual(HTML)-To be added
- [PE300_R11 Schematic](https://github.com/MicroPhase/fpga-docs/blob/master/schematic/PE300_R11.pdf)(PDF)
- [PE300_R11 Dimensions](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/PE300/PE300_R11_Dimensions.pdf) (PDF)  
- [PE300_R11 Board source file](https://github.com/MicroPhase/fpga-docs/blob/master/others/PE300_R11_Board_source_file.brd) (Brd) 