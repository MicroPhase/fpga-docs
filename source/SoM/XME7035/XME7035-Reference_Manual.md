# **XME7035 Reference Manual**

## Revision History

| Revision | Time       | Description   |
| :------- | :--------- | :------------ |
| Rev. 1.0 | 2024.10.22 | First Release |
|          |            |               |

## CopyRight Notice:

Copyright ©2024 by MicroPhase Technologies (Shanghai) Co. Ltd. All rights are reserved.

## Development Environment:

Vivado 2021.1 is from Xilinx website

<https://www.xilinx.com>

## WeChat Public Number:

![](./assets/vx.png)


## ●1. Overview

XME7035 is a industrial-grade system module based on Xilinx Zynq-SoC from Microphase Technology. With customizable variants available upon request, customised requirements may be subject to minimum order quantities,  please contact our sales team for more information: sales@microphase.cn.  
It integrates 4 DDR3 SDRAM chips, with two forming a 32-bit data bus and 8Gbit capacity. The read/write data clock frequency between the PS(Processing System) and the DDR3 is up to 533MHz, and the read/write data clock frequency between the PL(Programmable Logic) and the DDR3 is up to 800MHz, which can satisfy the system's demand for high-bandwidth data processing. At the same time, a REALTEK RTL8211F Gigabit Ethernet PHY chip is integrated on the core board, which can be easily used by users to realised Ethernet related applications.  
The core board features 138 single-ended IOs (configurable as 69 differential pairs), adjustable IO voltages, 8 GTX high-speed RX/TX pairs, and equal-length differential alignments with 50-ohm single-ended and 100-ohm differential impedance.

### ○Board Layout

![](./assets/layout.png)

### ○Key Features

- Xilinx Zynq™ XC7Z035-FFG676 Soc  
- DDR3: PS 8Gbit DDR3 RAM, 32Bit;  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;PL 8Gbit DDR3 RAM, 32Bit  
- Flash: Flash: 256Mbit QSPI Flash, 8GB eMMC Flash.  
- LED: 1 Power LED, 1 FPGA Done LED;  
&ensp;&ensp;&ensp;&ensp;&ensp;2 users LED,1 PS control, 1 PL control.  
- GTX: 8
- MIO: 21 MIOs, 3 IO at 3.3V, 18 IOs at 1.8V  
- PL GPIO: 138, Adjustable Voltage, 46 for HP BANK, 92 for HR BANK,  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;Can be configured as 69 differential pairs  
- Connectors: 3 x 120pin High Speed B2B Connectors  

### ○Block diagram

![](./assets/XME7035_DIAGRAM-01.png)

### ○Mechanical Spec  

![](./assets/mech.png)

## ●2. Function Resources  

### ○FPGA  

- Up to 1GHz MHz dual-core Cortex-A9 processor

- DDR3L memory controller with 8 DMA channels and 4

- High Performance AXI3 Slave ports

- High-bandwidth peripheral controllers: 1G Ethernet, USB 2.0, SDIO

- Low-bandwidth peripheral controllers: SPI, UART, CAN, I2C

- Programmable from JTAG, Quad-SPI flash, and microSD card

- Programmable logic equivalent to Kintex-7 FPGA

  LUTs: 171,900

  DSP Slices: 900

  Logic Cells: 275K

  Flip-Flops: 343,800

  Total Block RAM: 17.6Mb

- Analog Mixed Signal (AMS) / XADC: 2x 12 bit, MSPS ADCs with up to 17 Differential Inputs

- Security: AES & SHA 256b Decryption & Authentication for Secure Programmable Logic Configs  

### ○DDR3  

The PS of the module uses two 16-bit DDR3 memory chips, with a capacity of 512MB for a single chip and 1GB for two chips.

| Signal Name   | PIN Number | Signal Name    | PIN Number |
| ------------- | ---------- | -------------- | ---------- |
| PS_DDR3_A0    | K22        | PS_DDR3_D9     | L23        |
| PS_DDR3_A1    | K20        | PS_DDR3_D10    | M26        |
| PS_DDR3_A2    | N21        | PS_DDR3_D11    | K23        |
| PS_DDR3_A3    | L22        | PS_DDR3_D12    | M25        |
| PS_DDR3_A4    | M20        | PS_DDR3_D13    | N24        |
| PS_DDR3_A5    | N22        | PS_DDR3_D14    | M24        |
| PS_DDR3_A6    | L20        | PS_DDR3_D15    | N23        |
| PS_DDR3_A7    | J21        | PS_DDR3_D16    | R26        |
| PS_DDR3_A8    | T20        | PS_DDR3_D17    | P24        |
| PS_DDR3_A9    | U20        | PS_DDR3_D18    | N26        |
| PS_DDR3_A10   | M22        | PS_DDR3_D19    | P23        |
| PS_DDR3_A11   | H21        | PS_DDR3_D20    | T24        |
| PS_DDR3_A12   | P20        | PS_DDR3_D21    | T25        |
| PS_DDR3_A13   | J20        | PS_DDR3_D22    | T23        |
| PS_DDR3_A14   | R20        | PS_DDR3_D23    | R23        |
| PS_DDR3_BA0   | U22        | PS_DDR3_D24    | V24        |
| PS_DDR3_BA1   | T22        | PS_DDR3_D25    | U26        |
| PS_DDR3_BA2   | R22        | PS_DDR3_D26    | U24        |
| PS_DDR3_NCAS  | Y23        | PS_DDR3_D27    | U25        |
| PS_DDR3_CKE   | U21        | PS_DDR3_D28    | W26        |
| PS_DDR3_CLK_N | P21        | PS_DDR3_D29    | Y25        |
| PS_DDR3_CLK_P | R21        | PS_DDR3_D30    | Y26        |
| PS_DDR3_NCS   | Y21        | PS_DDR3_D31    | W23        |
| PS_DDR3_DM0   | G24        | PS_DDR3_DQS_N0 | G25        |
| PS_DDR3_DM1   | K25        | PS_DDR3_DQS_N1 | L25        |
| PS_DDR3_DM2   | P26        | PS_DDR3_DQS_N2 | R25        |
| PS_DDR3_DM3   | V26        | PS_DDR3_DQS_N3 | W25        |
| PS_DDR3_D0    | J26        | PS_DDR3_DQS_P0 | H24        |
| PS_DDR3_D1    | F25        | PS_DDR3_DQS_P1 | L24        |
| PS_DDR3_D2    | J25        | PS_DDR3_DQS_P2 | P25        |
| PS_DDR3_D3    | G26        | PS_DDR3_DQS_P3 | W24        |
| PS_DDR3_D4    | H26        | PS_DDR3_NRST   | H22        |
| PS_DDR3_D5    | H23        | PS_DDR3_ODT    | Y22        |
| PS_DDR3_D6    | J24        | PS_DDR3_NRAS   | V23        |
| PS_DDR3_D7    | J23        | PS_DDR3_nWE    | V22        |
| PS_DDR3_D8    | K26        |                |            |

The PL of the module uses two 16-bit DDR3 memory chips, with a capacity of 512MB for a single chip and 1GB for two chips.  

| Signal Name   | PIN Number | Signal Name    | PIN Number |
| ------------- | ---------- | -------------- | ---------- |
| PL_DDR3_A0    | E5         | PL_DDR3_D9     | J1         |
| PL_DDR3_A1    | A8         | PL_DDR3_D10    | H1         |
| PL_DDR3_A2    | E6         | PL_DDR3_D11    | H3         |
| PL_DDR3_A3    | B6         | PL_DDR3_D12    | H4         |
| PL_DDR3_A4    | A7         | PL_DDR3_D13    | G1         |
| PL_DDR3_A5    | A3         | PL_DDR3_D14    | L3         |
| PL_DDR3_A6    | B7         | PL_DDR3_D15    | H2         |
| PL_DDR3_A7    | B4         | PL_DDR3_D16    | M4         |
| PL_DDR3_A8    | A9         | PL_DDR3_D17    | L4         |
| PL_DDR3_A9    | E8         | PL_DDR3_D18    | N4         |
| PL_DDR3_A10   | D9         | PL_DDR3_D19    | L5         |
| PL_DDR3_A11   | A10        | PL_DDR3_D20    | M2         |
| PL_DDR3_A12   | C2         | PL_DDR3_D21    | L2         |
| PL_DDR3_A13   | B10        | PL_DDR3_D22    | M6         |
| PL_DDR3_A14   | D8         | PL_DDR3_D23    | M5         |
| PL_DDR3_BA0   | B1         | PL_DDR3_D24    | J5         |
| PL_DDR3_BA1   | C6         | PL_DDR3_D25    | J6         |
| PL_DDR3_BA2   | F5         | PL_DDR3_D26    | N6         |
| PL_DDR3_NCAS  | C9         | PL_DDR3_D27    | M7         |
| PL_DDR3_CKE   | F9         | PL_DDR3_D28    | K6         |
| PL_DDR3_CLK_N | F7         | PL_DDR3_D29    | N7         |
| PL_DDR3_CLK_P | G7         | PL_DDR3_D30    | K8         |
| PL_DDR3_NCS   | A4         | PL_DDR3_D31    | K5         |
| PL_DDR3_DM0   | E2         | PL_DDR3_DQS_N0 | F2         |
| PL_DDR3_DM1   | J4         | PL_DDR3_DQS_N1 | K1         |
| PL_DDR3_DM2   | N1         | PL_DDR3_DQS_N2 | N2         |
| PL_DDR3_DM3   | K7         | PL_DDR3_DQS_N3 | L8         |
| PL_DDR3_D0    | E1         | PL_DDR3_DQS_P0 | G2         |
| PL_DDR3_D1    | G4         | PL_DDR3_DQS_P1 | K2         |
| PL_DDR3_D2    | F4         | PL_DDR3_DQS_P2 | N3         |
| PL_DDR3_D3    | F3         | PL_DDR3_DQS_P3 | M8         |
| PL_DDR3_D4    | D4         | PL_DDR3_NRST   | B5         |
| PL_DDR3_D5    | C1         | PL_DDR3_ODT    | A5         |
| PL_DDR3_D6    | D1         | PL_DDR3_NRAS   | B9         |
| PL_DDR3_D7    | D3         | PL_DDR3_NWE    | B2         |
| PL_DDR3_D8    | K3         |                |            |

### ○Giga ETH  

The RTL8211F chip supports 10/100/1000M network transfer rate and communicates with the MAC layer of the Zynq7000 PS system via the RGMII interface. It supports MDI/MDX adaptation, multiple speed adaptation, master/slave adaptation and MDIO bus support for PHY register management.  

### ○eMMC  

The module features an 8GB eMMC interface (PS_SDIO0) that can be utilised for system files or other data file storage. It can also be employed as a secondary boot device in conjunction with the QSPI flash for system boot. The interface is PS BANK501 MIO[46-51].  

| Signal Name | Pin Number |
| ----------- | ---------- |
| MMC_CLK     | B21        |
| MMC_CMD     | B19        |
| MMC_DATA0   | E17        |
| MMC_DATA1   | A18        |
| MMC_DATA2   | B22        |
| MMC_DATA3   | B20        |

### ○JTAG  

The JTAG signal link of the XME7035 is connected to the expansion connector.

| Signal   | JM1 Pin Number | Explain       |
| -------- | -------------- | ------------- |
| FPGA_TCK | Pin23          | Input (3.3V)  |
| FPGA_TDI | Pin25          | Input (3.3V)  |
| FPGA_TDO | Pin27          | Output (3.3V) |
| FPGA_TMS | Pin29          | Output (3.3V) |

### ○Boot Config  

ZYNQ startup mode by configuring the core module pins PIN119 (MODE0), PIN120 (MODE1),the core module ZYNQ configuration schematic is shown below.  

![](./assets/boot.png)

| Mode | MODE1(JM1 PIN19)  | MODE0(JM1 PIN17)  |
| ---- | ----------------- | ----------------- |
| JTAG | Connection to GND | Connection to GND |
| QSPI | NC                | Connection to GND |
| SD   | NC                | NC                |

### ○Quad-SPI Flash  

On-board 256M Quad-SPI Flash memory W25Q256FVEI is used to store initial FPGA configuration and user’s application as well as data.  

| Position | Model       | Capacity | Factory |
| -------- | ----------- | -------- | ------- |
| U4       | W25Q256FVEI | 256 Byte | Winbond |

### ○Clock  

The XME7035 core board provides a 33.3Mhz active clock for the PS system and a 200Mhz active clock for the PL system.  

| Position | Signal Name | Frequency | Pin Number |
| -------- | ----------- | --------- | ---------- |
| U2       | PS_CLK_33d3 | 33.333Mhz | B24        |
| U6       | SYS_CLK_P   | 200Mhz    | C8         |
| U6       | SYS_CLK_N   | 200Mhz    | C7         |

### ○Power  

**Please note that the power input of XME7035 is +5V. We recommend using a 5V/2A power supply.**  

The module requires a 5V input, and it automatically follows a cascading power-up sequence:1.0V -> 1.8V -> 1.5V -> 3.3V. The 3.3V output will be powered up last, and at the same time, it will provide the PG signal of system power status.  

### ○LED  

The XME7035 board provides four LEDs, the power indicator, the FPGA configuration status light, the PL-controlled user LED, and the PS user-controlled LED.  
The LED signals are described in the following table.    

| LED  | ZYNQ Pin | Note                                                         |
| ---- | -------- | ------------------------------------------------------------ |
| D4   | --       | Power LED                                                    |
| D1   | W9       | FPGA configuration status LED, lit after successful FPGA configuration |
| D2   | G14      | LED on when FPGA E26 (MIO0) output is low                    |
| D3   | H16      | LED on when FPGA H16 output is low                           |

### ○Expansion Ports  

The XME7035 uses three sets of connectors, JM1, JM3 and JM4, for the FPGA IO signals and Ethernet interface.  
3 x AXK5A2137YG, 120Pin, 0.5mm Pitch    

| Core Board Connector Models | Based Board Connector Models | Manufacturers | Mated height |
| --------------------------- | ---------------------------- | ------------- | ------------ |
| AXK5A2137YG                 | AXK6A2337YG                  | Panasonic     | 3mm          |

FPGA Bank, Number of IOs vs. B2B Connector Table   

| FPGA Bank | B2B Connector | IO Number | Voltage    | Explain                                                |
| --------- | ------------- | --------- | ---------- | ------------------------------------------------------ |
| Bank500   | JM1           | 3         | 3.3V       |                                                        |
| BANK501   | JM1           | 18        | 1.8V       |                                                        |
| Bank35    | JM1           | 44        | Adjustable | 44 single-ended, can be mated to 22 differential pairs |
| Bank12    | JM3           | 44        | Adjustable | 44 single-ended, can be mated to 22 differential pairs |
| Bank13    | JM3           | 44        | Adjustable | 44 single-ended, can be mated to 22 differential pairs |
| BANK111   | JM4           | 20        | -          | 2 pairs of CLK, 4 pairs of TX and RX                   |
| BANK112   | JM4           | 20        | -          | 2 pairs of CLK, 4 pairs of TX and RX                   |

Description:  

1. Bank35 IO level depends on JM1 Pin29&30 voltage input, input range 1.2V-1.8V.
2. Bank12 IO level depends on JM3 Pin29&30 voltage input, input range 1.2V-3.3V.
3. Bank13 IO level depends on JM3 Pin89&90 voltage input, input range 1.2V-3.3V.
4. MIO8,MIO14 and MIO15 (JM1 Pin20,55,57), JTAG,RESET (JM1 Pin18, Pin23-Pin29) level is 3.3V.
5. MIO28~MIO45 (JM1 Pin24,26,28···-Pin108) level is 1.8V.
6. Please refer to the ‘[XME7035_Pinout Table](https://github.com/MicroPhase/fpga-docs/blob/master/others/XME7035_Pinout_Table.pdf)’ for detailed pin definitions of the XME7035.  

## ●3. Related Documents  

### ○XME7035  

- [XME7035_R12 Schematic](https://github.com/MicroPhase/fpga-docs/blob/master/schematic/XME7035_R12.pdf) (PDF)
- [XME7035_R12 Dimensions](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/XME7035/XME7035_R12_Dimensions.pdf) (PDF)  
- [XME7035_R12 Dimensions source file](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/XME7035/XME7035_R12_Dimensions_source_file.dxf) (DXF)  

### ○PE500   
- PE500 Reference_Manual(HTML)-To be added
- [PE500_R10 Schematic](https://github.com/MicroPhase/fpga-docs/blob/master/schematic/PE500_R10.pdf)(PDF)
- [PE500_R10 Dimensions](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/XME7035/PE500_R10_Dimensions.pdf)(PDF)
- [PE500_R10 Board source file](https://github.com/MicroPhase/fpga-docs/blob/master/others/PE500_R10_Board_source_file.brd)(Brd)