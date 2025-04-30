# **XME7100 用户手册**

[[English]](https://microphase-doc.readthedocs.io/en/latest/SoM/XME7100/XME7100-Reference_Manual.html)

## 开发环境：

赛灵思Vivado 2021.1

<https://www.xilinx.com>

## 微信公众号：

![](./XME7100-Reference_Manual.assets/vx.png)

## ●1. 概述

XME7100 是微相科技基于 Xilinx Zynq-SoC 的工业级系统模块。可根据需求定制，定制需求可能需要满足最小订单量，请联系我们的销售团队获取更多信息：<sales@microphase.cn>。  
该模块集成了 4 个 DDR3 SDRAM 芯片，其中两个形成一个 32 位数据总线，容量为 8Gbit。PS（处理系统）与 DDR3 之间的数据读写时钟频率最高可达 533MHz，PL（可编程逻辑）与 DDR3 之间的数据读写时钟频率最高可达 800MHz，能够满足系统对高带宽数据处理的需求。同时，核心板上集成了 REALTEK RTL8211F 千兆以太网 PHY 芯片，用户可以轻松实现以太网相关应用。  
核心板引出了 230 个单端 IO（可配置为 115 对差分对），184个单端IO 电压可调，8 对 GTX 高速 RX/TX 对，FPGA 引脚到连接器的走线经过等长差分处理，单端阻抗为 50 欧姆，差分阻抗为 100 欧姆。

### ○板卡布局

![](./XME7100-Reference_Manual.assets/layout.jpg)

### ○资源特性

- Xilinx Zynq™ XC7Z100-2FFG900I Soc  
- DDR3：PS 8Gbit DDR3 RAM，32 位；  
  &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;PL 8Gbit DDR3 RAM，32 位  
- 闪存：512Mbit QSPI 闪存，8GB eMMC 闪存。  
- LED：1 个电源 LED，1个FPGA 配置状态指示灯 
- GTX：16  
- MIO：21 个 MIO，3 个 IO 为 3.3V，18 个 IO 为 1.8V  
- PL GPIO：230 个，可配置为 115 对差分对 ，其中184个单端IO 电压可调，46 个 HP BANK IO，184 个HR BANK IO  
  &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; 
- 连接器：4 x 120pin 高速 B2B 连接器  

### ○机械规格

![](./XME7100-Reference_Manual.assets/7100_MECH.png)

## ●2. 功能资源

### ○FPGA

- Up to 1GHz MHz dual-core Cortex-A9 processor

- DDR3L memory controller with 8 DMA channels and 4

- High Performance AXI3 Slave ports

- High-bandwidth peripheral controllers: 1G Ethernet, USB 2.0, SDIO

- Low-bandwidth peripheral controllers: SPI, UART, CAN, I2C

- Programmable from JTAG, Quad-SPI flash, and microSD card

- Programmable logic equivalent to Kintex-7 FPGA

  LUTs: 277,400

  DSP Slices: 2,020

  Logic Cells: 444K

  Flip-Flops: 554,800

  Total Block RAM: 26.5Mb

- Analog Mixed Signal (AMS) / XADC: 2x 12 bit, MSPS ADCs with up to 17 Differential Inputs

- Security: AES & SHA 256b Decryption & Authentication for Secure Programmable Logic Configs  

### ○DDR3

模块的 PS 使用两个 16 位 DDR3 内存芯片，单个芯片容量为 512MB，两个芯片容量为 1GB。

| 信号名称      | 引脚号 | 信号名称       | 引脚号 |
| ------------- | ------ | -------------- | ------ |
| PS_DDR3_A0    | L25    | PS_DDR3_D9     | A27    |
| PS_DDR3_A1    | K26    | PS_DDR3_D10    | A30    |
| PS_DDR3_A2    | L27    | PS_DDR3_D11    | A28    |
| PS_DDR3_A3    | G25    | PS_DDR3_D12    | C28    |
| PS_DDR3_A4    | J26    | PS_DDR3_D13    | D30    |
| PS_DDR3_A5    | G24    | PS_DDR3_D14    | D28    |
| PS_DDR3_A6    | H26    | PS_DDR3_D15    | D29    |
| PS_DDR3_A7    | K22    | PS_DDR3_D16    | H27    |
| PS_DDR3_A8    | F27    | PS_DDR3_D17    | G27    |
| PS_DDR3_A9    | J23    | PS_DDR3_D18    | H28    |
| PS_DDR3_A10   | G26    | PS_DDR3_D19    | E28    |
| PS_DDR3_A11   | H24    | PS_DDR3_D20    | E30    |
| PS_DDR3_A12   | K23    | PS_DDR3_D21    | F28    |
| PS_DDR3_A13   | H23    | PS_DDR3_D22    | G30    |
| PS_DDR3_A14   | J24    | PS_DDR3_D23    | F30    |
| PS_DDR3_BA0   | M27    | PS_DDR3_D24    | J29    |
| PS_DDR3_BA1   | M26    | PS_DDR3_D25    | K27    |
| PS_DDR3_BA2   | M25    | PS_DDR3_D26    | J30    |
| PS_DDR3_NCAS  | M24    | PS_DDR3_D27    | J28    |
| PS_DDR3_CKE   | M22    | PS_DDR3_D28    | K30    |
| PS_DDR3_CLK_N | J25    | PS_DDR3_D29    | M29    |
| PS_DDR3_CLK_P | K25    | PS_DDR3_D30    | L30    |
| PS_DDR3_NCS   | N22    | PS_DDR3_D31    | M30    |
| PS_DDR3_DM0   | C27    | PS_DDR3_DQS_N0 | B26    |
| PS_DDR3_DM1   | B30    | PS_DDR3_DQS_N1 | B29    |
| PS_DDR3_DM2   | H29    | PS_DDR3_DQS_N2 | F29    |
| PS_DDR3_DM3   | K28    | PS_DDR3_DQS_N3 | L29    |
| PS_DDR3_D0    | A25    | PS_DDR3_DQS_P0 | C26    |
| PS_DDR3_D1    | E25    | PS_DDR3_DQS_P1 | C29    |
| PS_DDR3_D2    | B27    | PS_DDR3_DQS_P2 | G29    |
| PS_DDR3_D3    | D25    | PS_DDR3_DQS_P3 | L28    |
| PS_DDR3_D4    | B25    | PS_DDR3_NRST   | F25    |
| PS_DDR3_D5    | E26    | PS_DDR3_ODT    | L23    |
| PS_DDR3_D6    | D26    | PS_DDR3_NRAS   | N24    |
| PS_DDR3_D7    | E27    | PS_DDR3_NWE    | N23    |
| PS_DDR3_D8    | A29    |                |        |

模块的 PL 使用两个 16 位 DDR3 内存芯片，单个芯片容量为 512MB，两个芯片容量为 1GB。  

| 信号名称      | 引脚号 | 信号名称       | 引脚号 |
| ------------- | ------ | -------------- | ------ |
| PL_DDR3_A0    | L10    | PL_DDR3_D9     | F2     |
| PL_DDR3_A1    | E8     | PL_DDR3_D10    | H4     |
| PL_DDR3_A2    | J10    | PL_DDR3_D11    | G6     |
| PL_DDR3_A3    | K10    | PL_DDR3_D12    | H3     |
| PL_DDR3_A4    | F8     | PL_DDR3_D13    | G2     |
| PL_DDR3_A5    | J11    | PL_DDR3_D14    | H6     |
| PL_DDR3_A6    | E10    | PL_DDR3_D15    | G1     |
| PL_DDR3_A7    | L12    | PL_DDR3_D16    | E2     |
| PL_DDR3_A8    | E11    | PL_DDR3_D17    | F4     |
| PL_DDR3_A9    | K11    | PL_DDR3_D18    | D4     |
| PL_DDR3_A10   | E7     | PL_DDR3_D19    | F5     |
| PL_DDR3_A11   | G11    | PL_DDR3_D20    | E3     |
| PL_DDR3_A12   | J8     | PL_DDR3_D21    | F3     |
| PL_DDR3_A13   | H12    | PL_DDR3_D22    | D3     |
| PL_DDR3_A14   | D11    | PL_DDR3_D23    | E5     |
| PL_DDR3_BA0   | J9     | PL_DDR3_D24    | C1     |
| PL_DDR3_BA1   | H8     | PL_DDR3_D25    | B1     |
| PL_DDR3_BA2   | L9     | PL_DDR3_D26    | B4     |
| PL_DDR3_NCAS  | G7     | PL_DDR3_D27    | A3     |
| PL_DDR3_CKE   | F7     | PL_DDR3_D28    | C2     |
| PL_DDR3_CLK_N | D8     | PL_DDR3_D29    | B5     |
| PL_DDR3_CLK_P | D9     | PL_DDR3_D30    | C4     |
| PL_DDR3_NCS   | K8     | PL_DDR3_D31    | B2     |
| PL_DDR3_DM0   | K5     | PL_DDR3_DQS_N0 | K2     |
| PL_DDR3_DM1   | G5     | PL_DDR3_DQS_N1 | H1     |
| PL_DDR3_DM2   | E1     | PL_DDR3_DQS_N2 | D5     |
| PL_DDR3_DM3   | A2     | PL_DDR3_DQS_N3 | A4     |
| PL_DDR3_D0    | J3     | PL_DDR3_DQS_P0 | K3     |
| PL_DDR3_D1    | K6     | PL_DDR3_DQS_P1 | J1     |
| PL_DDR3_D2    | J5     | PL_DDR3_DQS_P2 | E6     |
| PL_DDR3_D3    | L1     | PL_DDR3_DQS_P3 | A5     |
| PL_DDR3_D4    | K1     | PL_DDR3_NRST   | H11    |
| PL_DDR3_D5    | L3     | PL_DDR3_ODT    | H7     |
| PL_DDR3_D6    | J4     | PL_DDR3_NRAS   | D6     |
| PL_DDR3_D7    | L2     | PL_DDR3_NWE    | L8     |
| PL_DDR3_D8    | H2     |                |        |

### ○千兆以太网

88E1512 芯片支持 10/100/1000M 网络传输速率，并通过 RGMII 接口与 Zynq7000 PS 系统的 MAC 层通信。它具有 MDI/MDX 交叉、多种速度的自适应协商和主/从配置。此外，它还支持 MDIO 总线用于 PHY 寄存器管理，并通过 IEEE 802.3az 节能以太网（EEE）提供先进的能效。88E1512 针对低功耗进行了优化，并为高速网络应用提供了强大的性能。

### ○eMMC

该模块具有 8GB eMMC 接口（PS_SDIO1），可用于系统文件或其他数据文件的存储。它还可以与 QSPI 闪存一起用作系统启动的辅助启动设备。接口信号连接到 PS BANK501 MIO[46-51]。  

| 信号名称  | 引脚号 / 引脚名称  |
| --------- | ------------------ |
| MMC_DATA0 | F20 / PS_MIO46_501 |
| MMC_CMD   | A18 / PS_MIO47_501 |
| MMC_CLK   | C19 / PS_MIO48_501 |
| MMC_DATA1 | D18 / PS_MIO49_501 |
| MMC_DATA2 | A19 / PS_MIO50_501 |
| MMC_DATA3 | F19 / PS_MIO51_501 |

### ○JTAG

XME7100 的 JTAG 信号链路连接到扩展连接器。

| 信号     | JM1 引脚号 | 说明         |
| -------- | ---------- | ------------ |
| FPGA_TCK | Pin23      | 输入（3.3V） |
| FPGA_TDI | Pin25      | 输入（3.3V） |
| FPGA_TDO | Pin27      | 输出（3.3V） |
| FPGA_TMS | Pin29      | 输出（3.3V） |

### ○启动配置

通过配置MODE1(JM1 PIN19), MODE0(JM1 PIN17)来设置 ZYNQ 启动模式，核心模块 ZYNQ 配置原理图如下所示。  

![](./XME7100-Reference_Manual.assets/boot.png)

| 模式 | MODE1（JM1 PIN19） | MODE0（JM1 PIN17） |
| ---- | ------------------ | ------------------ |
| JTAG | 连接到 GND         | 连接到 GND         |
| QSPI | NC                 | 连接到 GND         |
| SD   | NC                 | NC                 |

### ○Quad-SPI 闪存

板载 256M Quad-SPI 闪存 W25Q256FVEI 用于存储初始 FPGA 配置和用户应用程序及数据。  

| 位置 | 型号        | 容量  | 厂商    |
| ---- | ----------- | ----- | ------- |
| U4   | W25Q256FVEI | 256MB | Winbond |
| U5   | W25Q256FVEI | 256MB | Winbond |

### ○时钟

XME7100 核心板为 PS 系统提供 33.3MHz 有源时钟，为 PL 系统提供 200MHz 有源时钟，并为本地时钟提供 50MHz 有源时钟。  

| 位置 | 信号名称    | 频率      | 引脚号 |
| ---- | ----------- | --------- | ------ |
| U2   | PS_CLK_33d3 | 33.333MHz | B24    |
| U6   | SYS_CLK_P   | 200MHz    | C8     |
| U6   | SYS_CLK_N   | 200MHz    | C7     |
| U7   | CLK_50M     | 50MHz     | AD18   |

### ○电源

**请注意，XME7100 的电源输入为 +5V。建议使用 5V/2A 电源。**  

模块需要 5V 输入，并自动遵循级联上电顺序：1.0V -> 1.8V -> 1.5V -> 3.3V。3.3V 输出将最后上电，同时提供系统电源状态的 PG 信号。  

### ○LED

XME7100 板提供两个 LED，电源指示灯和 FPGA 配置状态灯。

| LED  | ZYNQ 引脚 | 说明                                   |
| ---- | --------- | -------------------------------------- |
| D4   | --        | 电源 LED                               |
| D1   | AA9       | FPGA 配置状态 LED，FPGA 成功配置后点亮 |

### ○扩展端口

XME7100 使用四组连接器 JM1、JM2、JM3 和 JM4 用于 FPGA IO 信号和以太网接口。  
4 x AXK5A2137YG，120Pin，0.5mm 间距  

[对应的底板连接器可以点击这里购买。](https://detail.tmall.com/item.htm?abbucket=3&id=693447746846&rn=fbc10a648fa73d95f20fd791b43bc157&skuId=4940866028771&spm=a1z10.3-b-s.w4011-24631307581.22.366d63e3FKGIZa)  

| 核心板连接器型号 | 底板连接器型号 | 制造商    | 配对高度 |
| ---------------- | -------------- | --------- | -------- |
| AXK5A2137YG      | AXK6A2337YG    | Panasonic | 3mm      |

FPGA Bank、IO 数量与 B2B 连接器表   

| FPGA Bank | B2B 连接器 | IO 数量 | 电压 | 说明                            |
| --------- | ---------- | ------- | ---- | ------------------------------- |
| Bank500   | JM1        | 3       | 3.3V |                                 |
| BANK501   | JM1        | 18      | 1.8V |                                 |
| Bank35    | JM1        | 46      | 可调 | 46 个单端，可配对为 23 对差分对 |
| Bank12    | JM2        | 46      | 可调 | 46 个单端，可配对为 23 对差分对 |
| Bank13    | JM2        | 46      | 可调 | 46 个单端，可配对为 23 对差分对 |
| Bank10    | JM3        | 46      | 可调 | 46 个单端，可配对为 23 对差分对 |
| Bank11    | JM3        | 46      | 可调 | 46 个单端，可配对为 23 对差分对 |
| BANK109   | JM4        | 20      | -    | 2 对 CLK，4 对 TX 和 RX         |
| BANK110   | JM4        | 20      | -    | 2 对 CLK，4 对 TX 和 RX         |
| BANK111   | JM4        | 20      | -    | 2 对 CLK，4 对 TX 和 RX         |
| BANK112   | JM4        | 20      | -    | 2 对 CLK，4 对 TX 和 RX         |

说明：  

1. Bank35 IO 电平取决于 JM1 Pin117&119 电压输入，输入范围 1.2V-1.8V。
2. Bank12 IO 电平取决于 JM2 Pin117&119 电压输入，输入范围 1.2V-3.3V。
3. Bank13 IO 电平取决于 JM2 Pin57&59 电压输入，输入范围 1.2V-3.3V。
4. Bank10 IO 电平取决于 JM3 Pin117&119 电压输入，输入范围 1.2V-3.3V。
5. Bank11 IO 电平取决于 JM3 Pin57&59 电压输入，输入范围 1.2V-3.3V。
6. MIO8、MIO14 和 MIO15（JM1 Pin20、55、57），JTAG、RESET（JM1 Pin18、Pin23-Pin29）电平为 3.3V。
7. MIO28~MIO45（JM1 Pin24、26、28···-Pin108）电平为 1.8V。
8. 请参阅 < [XME7100_Pinout Table](https://swnatyr2ph.feishu.cn/file/LQhlb3Llbo5ZIMx7pHqcVZxFnkc)> 获取 XME7100 的详细引脚定义。  

## ●3. 相关文档  

### ○XME7100  

- [XME7100_R11 原理图](https://swnatyr2ph.feishu.cn/file/Elc1bp2PHoTfDex55yGcusNanDd) (PDF)
- [XME7100_R11 尺寸](https://swnatyr2ph.feishu.cn/file/MyvDbpjIgoHkCpxJCaKcezClnnf) (PDF)  
- [XME7100_R11 尺寸源文件](https://swnatyr2ph.feishu.cn/file/UaaGbiuygoekg6xOBfAcnhmhnPg) (DXF)  

### ○PE500    
- [PE500 用户手册](https://microphase-doc.readthedocs.io/zh-cn/latest/CARRIER_BOARD/PE500/PE500-Reference_Manual.html)(HTML)
- [PE500_R10 原理图](https://swnatyr2ph.feishu.cn/file/Hqe3byQrYoHNccxbiAcc8xDJnRh)(PDF)
- [PE500_R10 尺寸](https://swnatyr2ph.feishu.cn/file/OS7obS91jo4SvaxxvLdca6Dfnsd)(PDF)
- [PE500_R10 板源文件](https://swnatyr2ph.feishu.cn/file/CUElb07ThouSh9xCOhUc6PwMnEb)(Brd)