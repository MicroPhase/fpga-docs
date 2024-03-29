# Z7-Nano
## 1. verview

Z7 Nano is a Commercial-grade SoM (System on Module) based on Xilinx Zynq-7000 SoC (XC7Z010 or XC7Z020) with up to 4Gb of DDR3/L SDRAM, 128MB of SPI flash memory, Gigabit Ethernet PHY transceiver, a USB PHY transceiver and a simple way to support power.

It’s not only suitable for the software verification but also of the software staff, but also

suitable for the hardware design of the hardware developer, according to the cooperation of software and hardware to help you speed up the development process of the project.



### 1.1 Key Features

- Xilinx Zynq™ XC7Z010-1CLG484C (7010 Version Only), 
  Xilinx Zynq™ XC7Z020-1CLG484C (7020 Version Only)
- DDR3: 1 4Gbit, DDR3 (MT41J256M16HA-125:K or equivalent)
- KEY: 1 users key, which is controlled by PL.
- LED: 2 users LED, 1 PS control, 1 PL control.
- GPIO: 2 40 pin expansion ports (2.54mm pitch), 72 IOs of 3.3V voltage.
- USB JTAG: 1 on board JTAG circuit, can debug and download the ZYNQ system through a USB cable.
- HDMI: 1 HDMI video output interface, can realize 1080P video image
- PHY ETH: 2 10/100/1000M Ethernet RJ45 interface, which can be used for Ethernet data exchange or other application.1 PS control, 1 PL control.
- USB Host: 1 USB Host.
- SD Card: 1 SD Card is provided to store the operating system image and file system.
- USB UART:1 USB UART interface, using for serial communication with PC. 
  CLOCK: 1 33.33Mhz active crystal oscillator provides a stable clock for the PS system. 1 50Mhz active crystal oscillator provides additional clocks for the PL logic.

### 1.2 Components layout

![image-20240218172910048](z7-nano.assets/image-20240218172910048.png)

### 1.3 Purchasing Options

| Name                | Number |
| ------------------- | ------ |
| SD Card Reader      | 1      |
| 16GB Micro SD       | 1      |
| Type-C Cable        | 1      |
| 2*20P Header        | 2      |
| Organic Glass Cover | 1      |



## 2. Interface

### 2.1 Power

The board is use the +5V supply from USB. The Figure 2-1 shows the USB can use to provide power.

![image-20240218172921092](z7-nano.assets/image-20240218172921092.png)



### 2.2 Boot Config

By default, Z7Nano- supports JTAG, QSPI and SD modes, which is controlled by the MODE input signal from the J1. User can change mode through the jumper cap. The startup mode is configured as shown in blow.

![image-20240218172928170](z7-nano.assets/image-20240218172928170.png)

| Jumper cap position                                          | Mode |
| ------------------------------------------------------------ | ---- |
| ![image-20240218172936012](z7-nano.assets/image-20240218172936012.png) | SD   |
| ![image-20240218172942722](z7-nano.assets/image-20240218172942722.png) | QSPI |
| ![image-20240218172947842](z7-nano.assets/image-20240218172947842.png) | JTAG |

### 2.3 On-board Peripherals

- DDR3/L Memory
  One on-board 16bit 512M DDR3/L SDRAM chips. 

| Position | Model       | Capacity     | Factory |
| -------- | ----------- | ------------ | ------- |
| U4       | MT41K256M16 | 256M x 16bit | Micron  |

- Quad-SPI Flash

  On-board 128M Quad-SPI Flash memory W25Q128JVSIQ is used to store initial FPGA configuration and user’s application as well as data.

| Position | Model        | Capacity  | Factory |
| -------- | ------------ | --------- | ------- |
| U2       | W25Q128JVSIQ | 128M Byte | Winbond |

- Oscillators/Clocks
  One 33.33Mhz active crystal oscillator provides a stable clock for the PS system. The other one 50Mhz active crystal oscillator provides additional clocks for the PL logic.

| Position | Signal Name | Frequency | Pin Number |
| -------- | ----------- | --------- | ---------- |
| Y1       | PS_CLK_33d3 | 33.333Mhz | E7         |
| U3       | PL_CLK_50M  | 50Mhz     | N18        |

- USB JTAG
  We integrated the JTAG download and debug circuit on the board that user can develop and debug ZYNQ through a USB cable.

- USB-UART
  A USB to UART chip CH340 is provide. According to it, user can connect the module to the host PC. 

| Signal Name | Pin Name     | Pin Number | Explain          |
| ----------- | ------------ | ---------- | ---------------- |
| UART_TX     | PS_MIO15_500 | C5         | UART data output |
| UART_RX     | PS_MIO14_500 | C8         | UART data output |

- USB Host
  The USB2.0 transceiver on-board is USB3320C-EZK, which is supports the ULPI standard interface. It connected with ZYNQ’s bus interface to enable high-speed USB2.0 Host mode data communications.

![image-20240218172957747](z7-nano.assets/image-20240218172957747.png)



- Reset
  Z7 Nano provided a key(K1) to be used as a “Reset” signal , Z7 Nano use the key to reset the board。

|                                                              | Signal Name | Pin Number |
| ------------------------------------------------------------ | ----------- | ---------- |
| ![image-20240218173005385](z7-nano.assets/image-20240218173005385.png) | SYS_RESET_N | C7         |

- Micro SD
  The board provide a Micro SD card interface to make user can access the SD card memory, BOOT programs for storing ZYNQ chips, Linux operating system kernels, file systems, and other user date files.



- Ethernet
  The RTL8211F chip supports 10/100/1000 M network transfer rate and communicates with the Zynq7000 PS system's MAC layer through the RGMII interface. It supports MDI/MDX adaptation, various speed adaptations, Master/Slave adaptation, and MDIO bus support for PHY register management.

- HDMI
  One HDMI video input and output interface, can realize 1080P video image.
- LEDs
  We provide two LEDs for user to use.

| Position | Signal Name | Pin Number | Explain |
| -------- | ----------- | ---------- | ------- |
| D4       | PS_LED1     | E6         | PS LED1 |
| D3       | GPIO1_17N   | R14        | PL LED1 |

- Keys
  We provide a key for user to use.

| Position | Signal Name | Pin Number | Explain |
| -------- | ----------- | ---------- | ------- |
| K2       | GPIO1_17P   | P14        | PL KEY1 |

- GPIOs
  This device is equipped with a maximum of 72 user IO pins that can be used for various custom applications. All user IOs are length matched and can be used as differential pairs.

| JP1  |             |            |      |             |            |
| ---- | ----------- | ---------- | ---- | ----------- | ---------- |
| Pin  | Signal Name | Pin Number | Pin  | Signal Name | Pin Number |
| 1    | GPIO1_0P    | N17        | 2    | GPIO1_0N    | P18        |
| 3    | GPIO1_1P    | R16        | 4    | GPIO1_1N    | R17        |
| 5    | GPIO1_2P    | T16        | 6    | GPIO1_2N    | U17        |
| 7    | GPIO1_3P    | W18        | 8    | GPIO1_3N    | W19        |
| 9    | GPIO1_4P    | Y18        | 10   | GPIO1_4N    | Y19        |
| 11   | VCC_5V      | -          | 12   | GND         | -          |
| 13   | GPIO1_5P    | Y16        | 14   | GPIO1_5N    | Y17        |
| 15   | GPIO1_6P    | V17        | 16   | GPIO1_6N    | V18        |
| 17   | GPIO1_7P    | W14        | 18   | GPIO1_7N    | Y14        |
| 19   | GPIO1_8P    | V16        | 20   | GPIO1_8N    | W16        |
| 21   | GPIO1_9P    | T17        | 22   | GPIO1_9N    | R18        |
| 23   | GPIO1_10P   | V12        | 24   | GPIO1_10N   | W13        |
| 25   | GPIO1_11P   | T14        | 26   | GPIO1_11N   | T15        |
| 27   | GPIO1_12P   | T11        | 28   | GPIO1_12N   | T10        |
| 29   | VCC_3V3     | -          | 30   | GND         | -          |
| 31   | GPIO1_13P   | V15        | 32   | GPIO1_13N   | W15        |
| 33   | GPIO1_14P   | P14        | 34   | GPIO1_14N   | R14        |
| 35   | GPIO1_15P   | U14        | 36   | GPIO1_15N   | U15        |
| 37   | GPIO1_16P   | U13        | 38   | GPIO1_16N   | V13        |
| 39   | GPIO1_17P   | T12        | 40   | GPIO1_17N   | U12        |

| JP2  |             |            |      |             |            |
| ---- | ----------- | ---------- | ---- | ----------- | ---------- |
| Pin  | Signal Name | Pin Number | Pin  | Signal Name | Pin Number |
| 1    | GPIO2_0P    | L16        | 2    | GPIO2_0N    | L17        |
| 3    | GPIO2_1P    | H15        | 4    | GPIO2_1N    | G15        |
| 5    | GPIO2_2P    | F16        | 6    | GPIO2_2N    | F17        |
| 7    | GPIO2_3P    | E18        | 8    | GPIO2_3N    | E19        |
| 9    | GPIO2_4P    | B19        | 10   | GPIO2_4N    | A20        |
| 11   | VCC_5V      | -          | 12   | GND         | -          |
| 13   | GPIO2_5P    | D19        | 14   | GPIO2_5N    | D20        |
| 15   | GPIO2_6P    | E17        | 16   | GPIO2_6N    | D18        |
| 17   | GPIO2_7P    | H16        | 18   | GPIO2_7N    | H17        |
| 19   | GPIO2_8P    | G19        | 20   | GPIO2_8N    | G20        |
| 21   | GPIO2_9P    | J18        | 22   | GPIO2_9N    | H18        |
| 23   | GPIO2_10P   | K16        | 24   | GPIO2_10N   | J16        |
| 25   | GPIO2_11P   | C20        | 26   | GPIO2_11N   | B20        |
| 27   | GPIO2_12P   | G17        | 28   | GPIO2_12N   | G18        |
| 29   | VCC_3V3     | -          | 30   | GND         | -          |
| 31   | GPIO2_13P   | L19        | 32   | GPIO2_13N   | L20        |
| 33   | GPIO2_14P   | F19        | 34   | GPIO2_14N   | F20        |
| 35   | GPIO2_15P   | M19        | 36   | GPIO2_15N   | M20        |
| 37   | GPIO2_16P   | K19        | 38   | GPIO2_16N   | J19        |
| 39   | GPIO2_17P   | J20        | 40   | GPIO2_17N   | H20        |