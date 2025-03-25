# **PE100 用户手册**

[[English]](https://microphase-doc.readthedocs.io/en/latest/CARRIER_BOARD/PE100/PE100-Reference_Manual.html)

## 微信公众号：

![](./PE100-Reference_Manual.assets/Wechat.png)

<div style="page-break-after:always;"></div>

## ●1. 概述

使用 PE100，您可以快速测试、开发和评估微相科技的 5*6 XME 系列 SoM 的功能。它为 XME 系列 SoM 提供了多种接口，例如 HDMI TX、千兆以太网、SFP、PCIe 2.0 x1 等。

目前，它支持 XME0712、XME0715 和 XME0720。最推荐与 XME0715 一起使用。**在本文档除了特别说明到特定核心板型号的描述外，其它一律是以XME0715核心板来做说明。**

### ○板卡布局

![](./PE100-Reference_Manual.assets/pe100_LAYOUT.png)

### ○资源特性

- 1 个 PCIe x1

- 2 个千兆以太网，支持 10/100/1000M 网络传输速率，1 个位于 PS，1 个位于 PL

- 2 个 SFP

- 1 个 HDMI TX

- 1 个 USB UART

- 1 个 SD

- 2 个 40 针扩展端口

- 1 个 JTAG 调试端口

- 1 个系统复位键，2 个用户按键

- 4 个用户LED

    **注：因核心板不同，以上接口可能不完全支持，使用时请确认细节。**

### ○框图

![](./PE100-Reference_Manual.assets/BLOCKDIAGRAM.png)

### ○机械尺寸

![](./PE100-Reference_Manual.assets/MECH.png)

### ○核心板匹配说明

✔️：支持

❌：不支持

⚠️ : 使用需注意

⭐ : 不完全支持

| PE100    | XME0712-35T | XME0712-75T/100T/200T | XME0715  | XME0720  |
| -------- | ----------- | --------------------- | -------- | -------- |
| PCIE x1  | ✔️           | ✔️                     | ✔️        | ❌        |
| ETH0     | ❌           | ✔️                     | ✔️(PS 侧) | ✔️(PS 侧) |
| ETH1     | ✔️           | ✔️                     | ✔️        | ✔️        |
| HDMI TX  | ✔️           | ✔️                     | ✔️        | ✔️        |
| SFP x2   | ✔️           | ✔️                     | ✔️        | ❌        |
| USB-UART | ✔️           | ✔️                     | ✔️        | ✔️        |
| SD       | ❌           | ❌                     | ✔️(PS 侧) | ✔️(PS 侧) |
| GPIO1    | ✔️           | ✔️                     | ✔️        | ✔️        |
| GPIO2    | ⭐           | ✔️                     | ✔️        | ✔️        |

## ●2. 功能资源

### ○千兆以太网

底板提供 2 个千兆以太网接口。ETH0 的 PHY IC 集成在核心板上，ETH0通过MDI信号与核心板连接。有关 ETH0 PHY 的更多信息，请参考相应的核心板文档。

ETH1 的 PHY 是 Marvell Alaska 88E1512，通过 RGMII 接口与核心板连接。88E1512 是一个强大的 PHY，支持 RGMII 到 RJ45 和 SGMII 到 RJ45，具有 MDI/MDIX 和 10/100/1000 Mbps 自适应能力。

核心板与两个以太网 PHY 芯片的连接图。

![](./PE100-Reference_Manual.assets/ETH.png)

### ○USB Host

PE100 提供四个 USB Host接口。**对于 XME0712，不支持 USB Host。** USB 3320 集成在核心板上。底板通过一个 USB HUB 芯片 USB2514 扩展了四个 USB Host接口。USB 接口为 TYPE-A，可以连接不同的 USB Slave设备，例如 USB 鼠标、USB 键盘、USB WIFI 等。

USB Host电路设计的示意图如下所示：

![](./PE100-Reference_Manual.assets/3320.png)

USB 与 XME0715 的引脚连接分配表如下。

| 信号名称  | FPGA 引脚 | 引脚名称     | 说明                 |
| --------- | --------- | ------------ | -------------------- |
| OTG_NRST  | E18       | PS_MIO8_500  | OTG 复位，低电平有效 |
| OTG_CLK   | A14       | PS_MIO36_501 | ULPI 时钟输出        |
| OTG_DATA0 | C16       | PS_MIO32_501 | ULPI 双向数据 0      |
| OTG_DATA1 | G11       | PS_MIO33_501 | ULPI 双向数据 1      |
| OTG_DATA2 | B11       | PS_MIO34_501 | ULPI 双向数据 2      |
| OTG_DATA3 | F9        | PS_MIO35_501 | ULPI 双向数据 3      |
| OTG_DATA4 | A11       | PS_MIO28_501 | ULPI 双向数据 4      |
| OTG_DATA5 | B9        | PS_MIO37_501 | ULPI 双向数据 5      |
| OTG_DATA6 | F10       | PS_MIO38_501 | ULPI 双向数据 6      |
| OTG_DATA7 | C10       | PS_MIO39_501 | ULPI 双向数据 7      |
| OTG_DIR   | E15       | PS_MIO29_501 | 控制数据总线的方向   |
| OTG_NXT   | F14       | PS_MIO31_501 | OTG NXT 信号         |
| OTG_STP   | A12       | PS_MIO30_501 | OTG STP 信号         |

### ○USB UART

底板提供了一个 USB 转 UART 接口，芯片为 Silicon Labs CP2102。USB 接口为 Micro USB。

![](./PE100-Reference_Manual.assets/2102.png)

UART 与 XME0715 的引脚连接分配表如下。

| 信号名称 | FPGA 引脚 | 引脚名称     | 说明          |
| -------- | --------- | ------------ | ------------- |
| UART_RX  | B17       | PS_MIO14_500 | UART 接收信号 |
| UART_TX  | E17       | PS_MIO15_500 | UART 发送信号 |

### ○JTAG

PE100 提供了 IDC10 JTAG 接口。通过 JTAG 端口，用户可以下载 FPGA 程序、固化 FLASH 程序以及进行在线仿真。JTAG 电路包括二极管保护，以确保 FPGA 信号电压符合要求。然而，我们还是建议用户避免热插拔，以免损坏芯片。

![](./PE100-Reference_Manual.assets/JTAG.png)

### ○复位

我们提供了一个按键（K1），可以用作 FPGA 上运行的设计的“复位”信号。

### ○Micro SD

PE100 提供了一个 Micro SD 接口，供用户访问 SD 卡存储器。**对于 XME0712，不支持 SD。**

SDIO 信号与 ZYNQ 的 SDIO 连接。Bank 501 的 VCCIO 电压为 1.8V，而 SD 数据电压为 3.3V，因此使用 TXS02612 进行电平转换。

核心板与 SD 的连接图。

![](./PE100-Reference_Manual.assets/SD.png)

### ○SFP

PE100 提供了两个 SFP 接口，每个 SFP 使用一个收发器通道。用户可以使用 SFP 热插拔光模块进行光纤数据通信。

每个 SFP 接口包括以下信号：

- **收发器**：提供一个通道，数据传输速率高达 6.52 Gbps。
- **SMBUS (I2C)**：3.3V 信号，用于模块管理。
- **控制信号**：包括状态控制。
- **参考时钟**：底板的 125 MHz 差分时钟。

核心板与 SFP 的连接图。

![](./PE100-Reference_Manual.assets/SFP.png)

底板上 SFP 接口的物理图如下所示。

![](./PE100-Reference_Manual.assets/SFP_R.png)

SFP1 与 XME0715 的引脚连接分配表如下。

| 信号名称       | FPGA 引脚 | 说明                                        |
| -------------- | --------- | ------------------------------------------- |
| SFP1_RX_N      | AB9       | ZYNQ/FPGA 收发器接收数据                    |
| SFP1_RX_P      | AA9       | ZYNQ/FPGA 收发器接收数据                    |
| SFP1_TX_N      | AB5       | ZYNQ/FPGA 收发器发送数据                    |
| SFP1_TX_P      | AA5       | ZYNQ/FPGA 收发器发送数据                    |
| SFP1_PRSNTN    | R5        | 在位状态信号，上拉，低电平表示 SFP 模块在位 |
| SFP1_RXLOS     | R4        | Rx LOS，上拉，高电平表示 LOS 信号           |
| SFP1_SCL       | N3        | SMBUS (I2C) 时钟信号                        |
| SFP1_SDA       | N4        | SMBUS (I2C) 数据信号                        |
| SFP1_TXDISABLE | K5        | Tx_Disable，上拉，高电平时发送关闭          |
| SFP1_TXFAULT   | J5        | Tx_Fault，上拉，高电平表示故障信号          |

SFP2 与 XME0715 的引脚连接分配表如下。

| 信号名称       | FPGA 引脚 | 说明                                        |
| -------------- | --------- | ------------------------------------------- |
| SFP2_RX_N      | Y8        | ZYNQ/FPGA 收发器接收数据                    |
| SFP2_RX_P      | W8        | ZYNQ/FPGA 收发器接收数据                    |
| SFP2_TX_N      | Y4        | ZYNQ/FPGA 收发器发送数据                    |
| SFP2_TX_P      | W4        | ZYNQ/FPGA 收发器发送数据                    |
| SFP2_PRSNTN    | N8        | 在位状态信号，上拉，低电平表示 SFP 模块在位 |
| SFP2_RXLOS     | P8        | Rx LOS，上拉，高电平表示 LOS 信号           |
| SFP2_SCL       | P5        | SMBUS (I2C) 时钟信号                        |
| SFP2_SDA       | P6        | SMBUS (I2C) 数据信号                        |
| SFP2_TXDISABLE | L4        | Tx_Disable，上拉，高电平时发送关闭          |
| SFP2_TXFAULT   | L5        | Tx_Fault，上拉，高电平表示故障信号          |

### ○HDMI

一个 HDMI 视频输出接口可以实现 1080P 图像以及视频输出。

![](./PE100-Reference_Manual.assets/HDMI_B.png)

底板上 HDMI 接口的物理图如下所示。

![](./PE100-Reference_Manual.assets/HDMI.png)

### ○PCIe

PE100 底板是一个标准的 PCI-Express 卡，其机械尺寸符合标准 PCIe 卡的电气规格要求，它提供了一个标准的 PCIe x4 插槽卡，四个 TX 通道和 RX 通道连接到 PCIe 金手指插槽，单通道通信速率高达 5Gbps 带宽，满足 PCIe Gen2 的数据传输能力。PCIe 参考时钟由 PCIe ROOT 设备（通常是 PC）的 PCIe 插槽提供给开发板，参考时钟频率为 100MHz。

![](./PE100-Reference_Manual.assets/PCIe_B.png)

### ○LED

PE100 包括五个 LED，一个电源指示灯，一个 PS 侧的用户 LED 和三个 PL 侧的用户 LED。当 FPGA 的相应引脚处于低电平时，LED 会亮起。

| 位置 | 信号名称 | 引脚号 |
| ---- | -------- | ------ |
| D8   | PS_LED1  | G16    |
| D9   | PL_LED1  | B7     |
| D10  | PL_LED2  | B6     |
| D11  | PL_LED3  | M7     |

### ○按键

我们提供了两个按键供用户使用。按键按下时，FPGA 的相应引脚将处于低电平。

| 位置 | 信号名称 | 引脚号 |
| ---- | -------- | ------ |
| K2   | PS_KEY   | C19    |
| K3   | PL_KEY   | J1     |

### ○GPIO

底板提供了两个 IDC40 GPIO 扩展端口，JP1 和 JP2，可以连接到微相科技的模块或其他外设。**使用 IO 时，请确保连接的信号电压一致。**

**JP1:**  

| 引脚 | 信号名称  | 引脚号 | 引脚 | 信号名称  | 引脚号 |
| ---- | --------- | ------ | ---- | --------- | ------ |
| 1    | GPIO1_0P  | AA16   | 2    | GPIO1_0N  | AA17   |
| 3    | GPIO1_1P  | W17    | 4    | GPIO1_1N  | Y17    |
| 5    | GPIO1_2P  | AA19   | 6    | GPIO1_2N  | AA20   |
| 7    | GPIO1_3P  | V16    | 8    | GPIO1_3N  | W16    |
| 9    | GPIO1_4P  | AB18   | 10   | GPIO1_4N  | AB19   |
| 11   | VCC_5V    | -      | 12   | GND       | -      |
| 13   | GPIO1_5P  | U19    | 14   | GPIO1_5N  | V19    |
| 15   | GPIO1_6P  | AB21   | 16   | GPIO1_6N  | AB22   |
| 17   | GPIO1_7P  | V18    | 18   | GPIO1_7N  | W18    |
| 19   | GPIO1_8P  | U17    | 20   | GPIO1_8N  | U18    |
| 21   | GPIO1_9P  | Y18    | 22   | GPIO1_9N  | Y19    |
| 23   | GPIO1_10P | AB13   | 24   | GPIO1_10N | AB14   |
| 25   | GPIO1_11P | R17    | 26   | GPIO1_11N | T17    |
| 27   | GPIO1_12P | V13    | 28   | GPIO1_12N | V14    |
| 29   | VCC_3V3   | -      | 30   | GND       | -      |
| 31   | GPIO1_13P | AA14   | 32   | GPIO1_13N | AA15   |
| 33   | GPIO1_14P | U11    | 34   | GPIO1_14N | U12    |
| 35   | GPIO1_15P | AA12   | 36   | GPIO1_15N | AB12   |
| 37   | GPIO1_16P | Y12    | 38   | GPIO1_16N | Y13    |
| 39   | GPIO1_17P | V11    | 40   | GPIO1_17N | W11    |

**JP2**

| 引脚 | 信号名称  | 引脚号 | 引脚 | 信号名称  | 引脚号 |
| ---- | --------- | ------ | ---- | --------- | ------ |
| 1    | GPIO2_0P  | G8     | 2    | GPIO2_0N  | G7     |
| 3    | GPIO2_1P  | F5     | 4    | GPIO2_1N  | E5     |
| 5    | GPIO2_2P  | G6     | 6    | GPIO2_2N  | F6     |
| 7    | GPIO2_3P  | F7     | 8    | GPIO2_3N  | E7     |
| 9    | GPIO2_4P  | D7     | 10   | GPIO2_4N  | D6     |
| 11   | VCC_5V    | -      | 12   | GND       | -      |
| 13   | GPIO2_5P  | L6     | 14   | GPIO2_5N  | M6     |
| 15   | GPIO2_6P  | N1     | 16   | GPIO2_6N  | P1     |
| 17   | GPIO2_7P  | R3     | 18   | GPIO2_7N  | R2     |
| 19   | GPIO2_8P  | P3     | 20   | GPIO2_8N  | P2     |
| 21   | GPIO2_9P  | T2     | 22   | GPIO2_9N  | T1     |
| 23   | GPIO2_10P | P7     | 24   | GPIO2_10N | R7     |
| 25   | GPIO2_11P | K7     | 26   | GPIO2_11N | L7     |
| 27   | GPIO2_12P | J8     | 28   | GPIO2_12N | K8     |
| 29   | VCC_3V3   | -      | 30   | GND       | -      |
| 31   | GPIO2_13P | AA11   | 32   | GPIO2_13N | AB11   |
| 33   | GPIO2_14P | U13    | 34   | GPIO2_14N | U14    |
| 35   | GPIO2_15P | V15    | 36   | GPIO2_15N | W15    |
| 37   | GPIO2_16P | AB16   | 38   | GPIO2_16N | AB17   |
| 39   | GPIO2_17P | W12    | 40   | GPIO2_17N | W13    |

### ○电源

开发板需要 DC12V 电源。请使用指定的电源以避免损坏。开发板还支持从 PCIe 接口供电。电源结构如下。

![](./PE100-Reference_Manual.assets/Power_structure.png)

## ●3. 相关文档  

### ○PE100

- [PE100_R11 原理图](https://github.com/MicroPhase/fpga-docs/blob/master/schematic/PE100_R11.pdf) (PDF)
- [PE100_R11 尺寸](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/PE100/PE100_R11_Dimensions.pdf) (PDF)  
- [PE100_R11 板源文件](https://github.com/MicroPhase/fpga-docs/blob/master/others/PE100_R11_Board_source_file.brd) (Brd)  

### ○微相科技的 5*6 XME 系列 SoM
- [XME0712 用户手册](https://microphase-doc.readthedocs.io/en/latest/SoM/XME0712/XME0712-Reference_Manual.html)(HTML)
- [XME0715 用户手册](https://microphase-doc.readthedocs.io/en/latest/SoM/XME0715/XME0715-Reference_Manual.html)(HTML)
- [XME0720 用户手册](https://microphase-doc.readthedocs.io/en/latest/SoM/XME0720/XME0720-Reference_Manual.html)(HTML)