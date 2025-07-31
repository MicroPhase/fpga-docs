# **Z7-Nano 用户手册**

[[English]](https://fpga-docs.microphase.cn/en/latest/DEV_BOARD/Z7-NANO/Z7-NANO_Reference_Manual.html)

## 开发环境

赛灵思Vivado 2018.3 

<https://www.xilinx.com>

## 微信公众号

![](./Z7-NANO_Reference_Manual.assets/Wechat17.png)

<div style="page-break-after:always;"></div>

## ●1. 概述

Z7 Nano 是一款基于 Xilinx Zynq-7000 SoC（XC7Z010 或 XC7Z020）的开发板，配备高达 4Gb 的 DDR3/L SDRAM、128MB SPI 闪存、千兆以太网 PHY 收发器、USB PHY 收发器以及简单的 供电方式。该开发板提供商业版（XC7Z010、XC7Z020）和工业版（XC7Z020），可根据需求提供定制版本，定制需求可能需要满足最低订购量，请联系我们的销售团队获取更多信息：<sales@microphase.cn>。

### ○板卡布局

![](./Z7-NANO_Reference_Manual.assets/Z7NANO_BOARD_LAYOUT.png)

### ○资源特性

- Xilinx Zynq™ XC7Z010-1CLG400C（仅限 7010 版本），  
  Xilinx Zynq™ XC7Z020-2CLG400C（仅限 7020 版本）

- DDR3：1 个 4Gbit DDR3（MT41J256M16HA-125:K 或等效型号）。  

- 按键：1 个用户按键，由 PL 控制。  

- LED：2 个用户 LED，1 个 PS 控制，1 个 PL 控制。  

- GPIO：2 个 40 针扩展端口（2.54mm 间距），72 个 3.3V 电压的 IO。  

- USB JTAG：1 个板载 JTAG 电路，可通过 USB 电缆调试和下载 ZYNQ 系统。  

- HDMI：1 个 HDMI 视频输出接口，可实现 1080P 视频图像。  

- PHY ETH：2 个 10/100/1000M 以太网 RJ45 接口，可用于以太网数据交换或其他应用。  
  &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;1 个 PS 控制，1 个 PL 控制。  

- USB Host：1 个 USB Host。  

- SD 卡：1 个 SD 卡，用于存储操作系统镜像和文件系统。  

- USB UART：1 个 USB UART 接口，用于与 PC 进行串行通信。  

- 时钟：1 个 33.33MHz 有源晶振，为 PS 系统提供稳定时钟。  
  &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;1 个 50MHz 有源晶振，为 PL 逻辑提供额外时钟。  

### ○系统框图

![](./Z7-NANO_Reference_Manual.assets/Z7_NANO-BLOCK_DIAGRAM.png)

### ○**机械尺寸**

![](./Z7-NANO_Reference_Manual.assets/Z7NANO_MECH.jpg)

## ●2. 硬件资源

### ○FPGA

- 667 MHz dual-core Cortex-A9 processor  

- DDR3L memory controller with 8 DMA channels and 4   

- High-Performance AXI3 Slave ports  

- High-bandwidth peripheral controllers: 1G Ethernet, USB 2.0, SDIO  

- Low-bandwidth peripheral controllers: SPI, UART, CAN, I2C  

- Programmable from JTAG, Quad-SPI flash, and microSD card  

- Programmable logic equivalent to Artix-7 FPGA  

  LUTs: 17,600 (7010)  
  	   &ensp;&ensp;&ensp;&ensp;&ensp;53,200(7020)  
  DSP Slices: 80 (7010)   
      	&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;220 (7020)  
  Logic Cells: 28K (7010)  
  		  &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;85K(7020)  
  Flip-Flops: 35,200 (7010)   
      	 &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;106,400 (7020)  
  Total Block RAM: 2.1Mb (7010)   
  &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;4.9Mb (7020)  

- Analog Mixed Signal (AMS) / XADC:  2x 12 bit, MSPS ADCs with up to 17 Differential Inputs  

- Security: AES & SHA 256b Decryption & Authentication for Secure Programmable Logic Config

### ○DDR3

板载 1 个 16bit 512M DDR3/L SDRAM 芯片。

| 位置 |    型号     |     容量     | 制造商 |
| :--: | :---------: | :----------: | :----: |
|  U4  | MT41K256M16 | 256M x 16bit |  美光  |

| 信号名称      | 引脚编号 | 信号名称       | 引脚编号 |
| ------------- | -------- | -------------- | -------- |
| PS_DDR3_A0    | N2       | PS_DDR3_D0     | C3       |
| PS_DDR3_A1    | K2       | PS_DDR3_D1     | B3       |
| PS_DDR3_A2    | M3       | PS_DDR3_D2     | A2       |
| PS_DDR3_A3    | K3       | PS_DDR3_D3     | A4       |
| PS_DDR3_A4    | M4       | PS_DDR3_D4     | D3       |
| PS_DDR3_A5    | L1       | PS_DDR3_D5     | D1       |
| PS_DDR3_A6    | L4       | PS_DDR3_D6     | C1       |
| PS_DDR3_A7    | K4       | PS_DDR3_D7     | E1       |
| PS_DDR3_A8    | K1       | PS_DDR3_D8     | E2       |
| PS_DDR3_A9    | J4       | PS_DDR3_D9     | E3       |
| PS_DDR3_A10   | F5       | PS_DDR3_D10    | G3       |
| PS_DDR3_A11   | G4       | PS_DDR3_D11    | H3       |
| PS_DDR3_A12   | E4       | PS_DDR3_D12    | J3       |
| PS_DDR3_A13   | D4       | PS_DDR3_D13    | H2       |
| PS_DDR3_A14   | F4       | PS_DDR3_D14    | H1       |
| PS_DDR3_BA0   | L5       | PS_DDR3_D15    | J1       |
| PS_DDR3_BA1   | R4       | PS_DDR3_DQS_N0 | B2       |
| PS_DDR3_BA2   | J5       | PS_DDR3_DQS_N1 | F2       |
| PS_DDR3_NCAS  | P5       | PS_DDR3_DQS_P0 | C2       |
| PS_DDR3_CKE   | N3       | PS_DDR3_DQS_P1 | G2       |
| PS_DDR3_CLK_N | M2       | PS_DDR3_NRST   | B4       |
| PS_DDR3_CLK_P | L2       | PS_DDR3_ODT    | N5       |
| PS_DDR3_NCS   | N1       | PS_DDR3_NRAS   | P4       |
| PS_DDR3_DM0   | A1       | PS_DDR3_NWE    | M5       |
| PS_DDR3_DM1   | F1       |                |          |

### ○千兆以太网

RTL8211F芯片支持10/100/1000M网络传输速率，并通过RGMII接口与Zynq7000 PS的MAC层通信。它支持MDI/MDX自适应、多种速率自适应、主/从自适应以及MDIO总线支持，用于PHY寄存器管理。

### ○USB Host

板载 USB 2.0 收发器为 USB3320C-EZK，支持 ULPI 标准接口。它与 ZYNQ 的总线接口连接，以实现高速 USB2.0 Host 模式数据通信。

![](./Z7-NANO_Reference_Manual.assets/USB_HOST.png)

### ○USB UART

提供了一个 USB 转 UART 芯片 CH340，用于用户连接到主机 PC。

| 信号名称 |   引脚名称   | 引脚编号 |     说明      |
| :------: | :----------: | :------: | :-----------: |
| UART_TX  | PS_MIO15_500 |    C8    | UART 数据输出 |
| UART_RX  | PS_MIO14_500 |    C5    | UART 数据输入 |

### ○USB JTAG

我们在板上集成了 JTAG 下载和调试电路，使用户能够通过 USB 线开发和调试 ZYNQ。

### ○启动配置

Z7-Nano 的启动设置包括 JTAG、QSPI 和 SD 模式，这些模式由 J1 的 MODE 输入信号控制。用户可以通过跳线帽更改模式。启动模式配置如下表所示。

![](./Z7-NANO_Reference_Manual.assets/BOOTMODE.png)

### ○Quad-SPI 闪存

板载 128M Quad-SPI 闪存 W25Q128JVSIQ，用于存储 FPGA 初始配置、用户应用程序和数据。

| 位置 |     型号     |   容量    | 制造商 |
| :--: | :----------: | :-------: | :----: |
|  U2  | W25Q128JVSIQ | 128M 字节 |  华邦  |

### ○时钟

一个 33.33 MHz 有源晶振为 PS 系统提供稳定时钟，另一个 50 MHz 有源晶振为 PL 逻辑提供额外时钟。

| 位置 |  信号名称   |   频率    | 引脚编号 |
| :--: | :---------: | :-------: | :------: |
|  Y1  | PS_CLK_33d3 | 33.333MHz |    E7    |
|  U3  | PL_CLK_50M  |   50MHz   |   N18    |

### ○复位

我们提供了一个按键（K1），可用作 FPGA 上运行的设计的“复位”信号。

### ○Micro SD

板卡提供了一个 Micro SD 卡接口，允许用户访问 SD 卡存储器。它还提供了 ZYNQ 芯片的引导加载程序、Linux 操作系统内核、文件系统和其他用户数据文件的存储。

### ○HDMI

一个 HDMI 视频输出接口，可实现 1080P 视频图像。

### ○LED

我们提供了两个 LED 供用户使用。当 FPGA 的相应引脚处于低电平时，LED 会亮起。

| 位置 | 信号名称  | 引脚编号 |  说明   |
| :--: | :-------: | :------: | :-----: |
|  D4  |  PS_LED1  |    E6    | PS LED1 |
|  D3  | GPIO1_17N |   R14    | PL LED1 |

### ○按键

我们提供了一个按键供用户使用。按下按键时，对应引脚将处于低电平。

| 位置 | 信号名称  | 引脚编号 |  说明   |
| :--: | :-------: | :------: | :-----: |
|  K2  | GPIO1_17P |   P14    | PL KEY1 |

### ○GPIO

该设备配备了最多 72 个用户 IO 引脚，可用于各种自定义应用。所有用户 IO 都经过长度匹配，可用作差分对。  

**JP1:**  

| 引脚 | 信号名称  | 引脚编号 | 引脚 | 信号名称  | 引脚编号 |
| :--: | :-------: | :------: | :--: | :-------: | :------: |
|  1   | GPIO1_0P  |   N17    |  2   | GPIO1_0N  |   P18    |
|  3   | GPIO1_1P  |   R16    |  4   | GPIO1_1N  |   R17    |
|  5   | GPIO1_2P  |   T17    |  6   | GPIO1_2N  |   R18    |
|  7   | GPIO1_3P  |   T16    |  8   | GPIO1_3N  |   U17    |
|  9   | GPIO1_4P  |   W18    |  10  | GPIO1_4N  |   W19    |
|  11  |  VCC_5V   |          |  12  |    GND    |          |
|  13  | GPIO1_5P  |   Y18    |  14  | GPIO1_5N  |   Y19    |
|  15  | GPIO1_6P  |   Y16    |  16  | GPIO1_6N  |   Y17    |
|  17  | GPIO1_7P  |   V17    |  18  | GPIO1_7N  |   V18    |
|  19  | GPIO1_8P  |   V16    |  20  | GPIO1_8N  |   W16    |
|  21  | GPIO1_9P  |   V15    |  22  | GPIO1_9N  |   W15    |
|  23  | GPIO1_10P |   U14    |  24  | GPIO1_10N |   U15    |
|  25  | GPIO1_11P |   U13    |  26  | GPIO1_11N |   V13    |
|  27  | GPIO1_12P |   T12    |  28  | GPIO1_12N |   U12    |
|  29  |  VCC_3V3  |          |  30  |    GND    |          |
|  31  | GPIO1_13P |   W14    |  32  | GPIO1_13N |   Y14    |
|  33  | GPIO1_14P |   V12    |  34  | GPIO1_14N |   W13    |
|  35  | GPIO1_15P |   T14    |  36  | GPIO1_15N |   T15    |
|  37  | GPIO1_16P |   T11    |  38  | GPIO1_16N |   T10    |
|  39  | GPIO1_17P |   P14    |  40  | GPIO1_17N |   R14    |

**JP2:**  

| 引脚 | 信号名称  | 引脚编号 | 引脚 | 信号名称  | 引脚编号 |
| :--: | :-------: | :------: | :--: | :-------: | :------: |
|  1   | GPIO2_0P  |   H15    |  2   | GPIO2_0N  |   G15    |
|  3   | GPIO2_1P  |   F16    |  4   | GPIO2_1N  |   F17    |
|  5   | GPIO2_2P  |   E17    |  6   | GPIO2_2N  |   D18    |
|  7   | GPIO2_3P  |   E18    |  8   | GPIO2_3N  |   E19    |
|  9   | GPIO2_4P  |   G17    |  10  | GPIO2_4N  |   G18    |
|  11  |  VCC_5V   |          |  12  |    GND    |          |
|  13  | GPIO2_5P  |   H16    |  14  | GPIO2_5N  |   H17    |
|  15  | GPIO2_6P  |   B19    |  16  | GPIO2_6N  |   A20    |
|  17  | GPIO2_7P  |   C20    |  18  | GPIO2_7N  |   B20    |
|  19  | GPIO2_8P  |   D19    |  20  | GPIO2_8N  |   D20    |
|  21  | GPIO2_9P  |   J18    |  22  | GPIO2_9N  |   H18    |
|  23  | GPIO2_10P |   F19    |  24  | GPIO2_10N |   F20    |
|  25  | GPIO2_11P |   G19    |  26  | GPIO2_11N |   G20    |
|  27  | GPIO2_12P |   J20    |  28  | GPIO2_12N |   H20    |
|  29  |  VCC_3V3  |          |  30  |    GND    |          |
|  31  | GPIO2_13P |   K16    |  32  | GPIO2_13N |   J16    |
|  33  | GPIO2_14P |   K19    |  34  | GPIO2_14N |   J19    |
|  35  | GPIO2_15P |   L16    |  36  | GPIO2_15N |   L17    |
|  37  | GPIO2_16P |   M19    |  38  | GPIO2_16N |   M20    |
|  39  | GPIO2_17P |   L19    |  40  | GPIO2_17N |   L20    |

## ●3.相关文档

- [Z7-NANO_R21_Schematic](https://swnatyr2ph.feishu.cn/file/IiZKbjNpJonjHPx8bZfcs4knn1g)(PDF)
- [Z7-NANO_R20_Dimensions](https://swnatyr2ph.feishu.cn/file/SYtxb0NBPo8P9Wxwc2OcRDtdnXb)(PDF)
- [Z7-NANO_R20_Dimensions source file](https://swnatyr2ph.feishu.cn/file/LsOnbJD3LoSD3uxNIXKcnt3cneh) (DXF) 
