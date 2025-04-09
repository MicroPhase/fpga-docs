# **XME0726 用户手册**

[[English]](https://microphase-doc.readthedocs.io/en/latest/SoM/XME0726/XME0726-Reference_Manual.html)

## 开发环境：

  赛灵思Vivado 2018.3

<https://www.xilinx.com>

## 微信公众号：

![](./assets/vx.png)

<div style="page-break-after:always;"></div>

## ●1. 概述

XME0726 是微相科技基于 Xilinx Zynq-SoC（XC7Z010 或 XC7Z020）开发的系统模块。

它集成了 1GB DDR3 RAM、32MB SPI 闪存、千兆以太网 PHY 收发器以及大量通过高速连接器扩展的可配置 I/O。模块尺寸仅为 4.5 x 3.5cm，小巧灵活，适用于广泛的应用场景。

核心板在 PL 侧扩展了 120 个单端 IO（可配置为 60 对差分 IO），IO 电压可调；PS 侧有 32 个 IO 和一个千兆以太网 PHY，FPGA 引脚到连接器的走线经过等长差分处理，单端阻抗为 50 欧姆，差分阻抗为 100 欧姆。这对于高速信号传输应用场景非常重要。

### ○板卡布局

![](./assets/layout.png)

<div style="page-break-after:always;"></div>

### ○资源特性

- Xilinx Zynq™ XC7Z010-1CLG400C（仅 7010 版本），  
  Xilinx Zynq™ XC7Z020-2CLG400C（仅 7020 版本）。  
- DDR3：PS 1GB DDR3 RAM。  
- 闪存：256Mbit QSPI 闪存。  
- LED：1 个电源 LED，1个FPGA 配置状态指示灯；  
  &ensp;&ensp;&ensp;&ensp;&ensp;1 个 PS 用户 LED。  
- MIO：32 个 MIO，8 个 IO 为 3.3V，24 个 IO 为 1.8V。  
- PL GPIO：120 个，电压可调，60 对 LVDS。  
- 千兆以太网：10/100/1000M 自适应  
- USB 主机：USB2.0 PHY（USB3320）  
- 时钟：1 个 33.33MHz 有源晶振为 PS 系统提供稳定时钟。  
- 连接器：2 * 120pin 高速 B2B 连接器  

### ○系统框图

![](./assets/block_diagram.png)

### ○机械尺寸

![](./assets/XME0726_MECH.png)

## ●2. 硬件资源

### ○FPGA

- 667 MHz dual-core Cortex-A9 processor  
- DDR3L me  mory controller with 8 DMA channels and 4   

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

该模块使用两个 16 位 DDR3 内存芯片，单个芯片容量为 512MB，两个芯片容量为 1GB。

| 信号名称      | 引脚号 | 信号名称       | 引脚号 |
| ------------- | ------ | -------------- | ------ |
| PS_DDR3_A0    | N2     | PS_DDR3_D9     | E3     |
| PS_DDR3_A1    | K2     | PS_DDR3_D10    | G3     |
| PS_DDR3_A2    | M3     | PS_DDR3_D11    | H3     |
| PS_DDR3_A3    | K3     | PS_DDR3_D12    | J3     |
| PS_DDR3_A4    | M4     | PS_DDR3_D13    | H2     |
| PS_DDR3_A5    | L1     | PS_DDR3_D14    | H1     |
| PS_DDR3_A6    | L4     | PS_DDR3_D15    | J1     |
| PS_DDR3_A7    | K4     | PS_DDR3_D16    | P1     |
| PS_DDR3_A8    | K1     | PS_DDR3_D17    | P3     |
| PS_DDR3_A9    | J4     | PS_DDR3_D18    | R3     |
| PS_DDR3_A10   | F5     | PS_DDR3_D19    | R1     |
| PS_DDR3_A11   | G4     | PS_DDR3_D20    | T4     |
| PS_DDR3_A12   | E4     | PS_DDR3_D21    | U4     |
| PS_DDR3_A13   | D4     | PS_DDR3_D22    | U2     |
| PS_DDR3_A14   | F4     | PS_DDR3_D23    | U3     |
| PS_DDR3_BA0   | L5     | PS_DDR3_D24    | V1     |
| PS_DDR3_BA1   | R4     | PS_DDR3_D25    | Y3     |
| PS_DDR3_BA2   | J5     | PS_DDR3_D26    | W1     |
| PS_DDR3_NCAS  | P5     | PS_DDR3_D27    | Y4     |
| PS_DDR3_CKE   | N3     | PS_DDR3_D28    | Y2     |
| PS_DDR3_CLK_N | M2     | PS_DDR3_D29    | W3     |
| PS_DDR3_CLK_P | L2     | PS_DDR3_D30    | V2     |
| PS_DDR3_NCS   | N1     | PS_DDR3_D31    | V3     |
| PS_DDR3_DM0   | A1     | PS_DDR3_DQS_N0 | B2     |
| PS_DDR3_DM1   | F1     | PS_DDR3_DQS_N1 | F2     |
| PS_DDR3_DM2   | T1     | PS_DDR3_DQS_N2 | T2     |
| PS_DDR3_DM3   | Y1     | PS_DDR3_DQS_N3 | W4     |
| PS_DDR3_D0    | C3     | PS_DDR3_DQS_P0 | C2     |
| PS_DDR3_D1    | B3     | PS_DDR3_DQS_P1 | G2     |
| PS_DDR3_D2    | A2     | PS_DDR3_DQS_P2 | R2     |
| PS_DDR3_D3    | A4     | PS_DDR3_DQS_P3 | W5     |
| PS_DDR3_D4    | D3     | PS_DDR3_NRST   | B4     |
| PS_DDR3_D5    | D1     | PS_DDR3_ODT    | N5     |
| PS_DDR3_D6    | C1     | PS_DDR3_NRAS   | P4     |
| PS_DDR3_D7    | E1     | PS_DDR3_NWE    | M5     |
| PS_DDR3_D8    | E2     |                | ****   |

### ○千兆以太网

RTL8211F 芯片支持 10/100/1000M 网络传输速率，并通过 RGMII 接口与 Zynq7000 PS 系统的 MAC 层进行通信。它支持 MDI/MDX 自适应、多种速率自适应、主/从模式自适应，并支持通过 MDIO 总线进行 PHY 寄存器管理。

### ○JTAG

XME0726 的 JTAG 信号链路连接到扩展连接器。

|   信号   | JM3 引脚号 | 说明         |
| :------: | :--------: | ------------ |
| FPGA_TCK |   Pin103   | 输入（3.3V） |
| FPGA_TDI |   Pin99    | 输入（3.3V） |
| FPGA_TDO |   Pin101   | 输出（3.3V） |
| FPGA_TMS |   Pin105   | 输出（3.3V） |

### ○启动配置

通过配置MODE1(JM3 PIN108)、MODE01(JM3 PIN106)来设置 ZYNQ 启动模式，核心模块 ZYNQ 配置原理图如下所示。

![](./assets/BOOT.png)

| 模式 | MODE1（JM3 PIN108） | MODE0（JM3 PIN106） |
| :--: | :-----------------: | :-----------------: |
| JTAG |     连接到 GND      |     连接到 GND      |
| QSPI |         NC          |     连接到 GND      |
|  SD  |         NC          |         NC          |

### ○Quad-SPI 

板载 256M Quad-SPI 闪存 W25Q256FVEI 用于存储初始 FPGA 配置和用户应用程序及数据。

| 位置 |    型号     | 容量  |  厂商   |
| :--: | :---------: | :---: | :-----: |
|  U7  | W25Q256FVEI | 256MB | Winbond |

### ○时钟

XME0726 核心板为 PS 系统提供 33.3MHz 有源时钟。

PL 部分的时钟可以由 PS 部分的 PLL 生成，或者用户可以通过将外部时钟源连接到模块的专用时钟引脚来将其用作 PL 部分的时钟输入。

| 位置 |  信号名称   |   频率    | 引脚号 |
| :--: | :---------: | :-------: | :----: |
|  Y2  | PS_CLK_33d3 | 33.333MHz |   E7   |

### ○电源

**请注意，XME0726 的电源输入为 +5V。我们建议使用 5V/2A 电源。**

模块上电顺序为：1.0V -> 1.8V -> 1.5V -> 3.3V。3.3V 输出将最后上电，同时提供系统电源状态PG信号。

### ○LED

XME0726 板提供三个 LED，电源指示灯、FPGA 配置状态指示灯和 PS 控制的用户 LED。

LED 信号如下表所述。

| LED  | FPGA 引脚 | 说明                                      |
| :--: | :-------: | ----------------------------------------- |
|  D5  |    \-     | 电源 LED                                  |
|  D2  |    R11    | FPGA 配置状态 LED，FPGA 成功配置 LED 点亮 |
|  D3  |    E6     | 当 Bank500 MIO0 输出为高电平时 LED 点亮   |

### ○扩展端口

XME0726 使用两组连接器 JM1 和 JM3 用于 拓展FPGA IO 和以太网接口信号。

2 x AXK5A2137YG，120Pin，0.5mm 间距

| 核心板连接器型号 | 底板连接器型号 |  制造商   | 配对高度 |
| :--------------: | :------------: | :-------: | :------: |
|   AXK5A2137YG    |  AXK6A2337YG   | Panasonic |   3mm    |

FPGA Bank、IO 数量与 B2B 连接器表

| FPGA Bank | B2B 连接器 | IO 数量 | 电压 |              说明               |
| :-------: | :--------: | :-----: | :--: | :-----------------------------: |
|  Bank500  |    JM1     |    8    | 3.3V |             8个MIO              |
|  BANK501  |    JM1     |   24    | 1.8V |             24个MIO             |
|  Bank35   |    JM1     |   48    | 可调 | 48 个单端，可配对为 24 对差分对 |
|  Bank12   |    JM3     |   48    | 可调 | 48 个单端，可配对为 24 对差分对 |
|  Bank13   |    JM3     |   24    | 可调 | 24 个单端，可配对为 12 对差分对 |

说明：

1. Bank35 IO 电平取决于 JM1 Pin29&30 电压输入，输入范围 1.2V~3.3V。
2. Bank34 IO 电平取决于 JM3 Pin29&30 电压输入，输入范围 1.2V~3.3V。
3. Bank13 IO 电平取决于 JM3 Pin89&90 电压输入，输入范围 1.2V~3.3V。
4. MIO8-MIO15（JM1 Pin111-Pin118）、JTAG、RESET（JM1 Pin99~Pin108）电平为 3.3V。
5. MIO28-MIO51（JM1 Pin81-Pin108）电平为 1.8V。
6. 请参阅 《[XME0726_Pinout_Table](https://github.com/MicroPhase/fpga-docs/blob/master/others/XME0726_Pinout_Table.pdf)》 获取 XME0726 的详细引脚定义。

## ●3. 相关文档  
### ○XME0726
- [XME0726_R10 原理图](https://github.com/MicroPhase/fpga-docs/blob/master/schematic/XME0726_R10.pdf) (PDF)
- [XME0726_R10 尺寸](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/XME0726/XME0726_R10_Dimensions.pdf) (PDF) 
- [XME0726_R10 尺寸源文件](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/XME0726/XME0726_R10_Dimensions_source_file.dxf) (DXF) 
### ○Dev_XME0726 
- Dev_XME0726 用户手册（HTML）- 待添加
- [Dev_XME0726_R10 原理图](https://github.com/MicroPhase/fpga-docs/blob/master/schematic/Dev_XME0726_R10.pdf) (PDF)
- [Dev_XME0726_R10 尺寸](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/XME0726/Dev_XME0726_R10_Dimensions.pdf) (PDF)
- [Dev_XME0726_R10 板源文件](https://github.com/MicroPhase/fpga-docs/blob/master/others/Dev_XME0726_R10_Board_source_file.BRD) (Brd)
