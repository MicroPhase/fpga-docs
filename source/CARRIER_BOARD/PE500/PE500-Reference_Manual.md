- # **PE500 用户手册**

  ## 微信公众号:

  ![](./PE500-Reference_Manual.assets/Wechat.png)

  <div style="page-break-after:always;"></div>

  ## ●1. 概述

  使用PE500，您可以快速测试、开发和评估Microphase的6*8 XME系列SoM的功能。它为XME系列SoM提供了各种接口，如HDMI TX、Giga ETH、SFP、PCIe 2.0x8等。

  目前，它支持XME7035和XME7100。**以下内容基于XME7100，除非另有说明。**

  ### ○板卡布局

  ![](./PE500-Reference_Manual.assets/PE500_BL.png)

  ### ○主要特性

  - 1个PCIe x8接口
  
  - 2个千兆以太网接口，1个位于PS，1个位于PL，支持10/100/1000M网络传输速率
  
  - 4个SFP+接口
  
  - 1个M.2接口
  
  - 1个HDMI TX接口
  
  - 1个Micro-USB UART接口
  
  - 1个SD卡接口
  
  - 2个40针扩展端口
  
  - 1个JTAG调试端口
  
  - 4个USB2.0接口
  
  - 1个系统复位键，4个用户按键
  
  - 4个用户LED
  
    **注：因核心板不同，以上接口可能不完全支持，使用时请确认细节。**

  ### ○机械尺寸
  
  ![](./PE500-Reference_Manual.assets/500_mech.png)
  
  ### ○核心板匹配说明
  
  ✔️：支持  
  ❌：不支持  
  ⚠️ : 使用需注意  
  ⭐ : 不完全支持
  
  | PE500          | XME7035 | XME7100 |
  | -------------- | ------- | ------- |
  | PCIE 2.0       | ⭐       | ✔️       |
  | PS ETH         | ✔️       | ✔️       |
  | PL ETH         | ✔️       | ✔️       |
  | HDMI TX        | ✔️       | ✔️       |
  | 4*SFP+         | ✔️       | ✔️       |
  | M.2 Interface  | ❌       | ✔️       |
  | Micro-USB UART | ✔️       | ✔️       |
  | SD             | ✔️       | ✔️       |
  | 4*USB2.0       | ✔️       | ✔️       |
  | GPIO1          | ✔️       | ✔️       |
  | GPIO2          | ❌       | ✔️       |
  
  ## ●2. 功能资源
  
  ### ○千兆以太网
  
  底板提供2个千兆以太网接口。ETH0的PHY IC集成在核心板上，ETH0通过MDI信号与核心板连接。有关 ETH0 PHY 的更多信息，请参考相应的核心板文档。
  
  ETH1的PHY是Marvell Alaska 88E1512，通过RGMII接口与核心板连接。88E1512是一款强大的PHY，支持RGMII到RJ45和SGMII到RJ45，具有MDI/MDIX和10/100/1000 Mbps自动协商功能。
  
  核心板与两个以太网PHY芯片的连接图。
  
  ![](./PE500-Reference_Manual.assets/ETH.png)
  
  ### ○USB Host
  
  PE500提供四个USB Host。USB 3320集成在核心板上。底板通过一个 USB HUB 芯片 USB2514 扩展了四个 USB Host接口。USB 接口为 TYPE-A，可以连接不同的 USB Slave设备，例如 USB 鼠标、USB 键盘、USB WIFI 等。
  
  USB Host电路设计的示意图如下所示：
  
  ![](./PE500-Reference_Manual.assets/3320.png)
  
  USB与7100的引脚连接分配表如下。
  
  | 信号名称  | FPGA引脚 | 引脚名称     | 说明                |
  | --------- | -------- | ------------ | ------------------- |
  | OTG_NRST  | E18      | PS_MIO8_500  | OTG复位，低电平有效 |
  | OTG_CLK   | A14      | PS_MIO36_501 | ULPI时钟输出        |
  | OTG_DATA0 | C16      | PS_MIO32_501 | ULPI双向数据0       |
  | OTG_DATA1 | G11      | PS_MIO33_501 | ULPI双向数据1       |
  | OTG_DATA2 | B11      | PS_MIO34_501 | ULPI双向数据2       |
  | OTG_DATA3 | F9       | PS_MIO35_501 | ULPI双向数据3       |
  | OTG_DATA4 | A11      | PS_MIO28_501 | ULPI双向数据4       |
  | OTG_DATA5 | B9       | PS_MIO37_501 | ULPI双向数据5       |
  | OTG_DATA6 | F10      | PS_MIO38_501 | ULPI双向数据6       |
  | OTG_DATA7 | C10      | PS_MI039_501 | ULPI双向数据7       |
  | OTG_DIR   | E15      | PS_MIO29_501 | 控制数据总线方向    |
  | OTG_NXT   | F14      | PS_MIO31_501 | OTG NXT信号         |
  | OTG_STP   | A12      | PS_MI030_501 | OTG STP信号         |
  
  ### ○USB UART

  底板提供了一个USB转UART接口，芯片为Silicon Labs CP2102。USB接口为Micro USB。

  ![](./PE500-Reference_Manual.assets/2102.png)

  UART与XME7100的引脚连接分配表如下。

  | 信号名称 | FPGA引脚 | 引脚名称     | 说明         |
  | -------- | -------- | ------------ | ------------ |
  | UART_RX  | B22      | PS_MIO14_500 | UART接收信号 |
  | UART_TX  | C22      | PS_MIO15_500 | UART发送信号 |
  
  ### ○JTAG
  
  PE500 提供了 IDC10 JTAG 接口。通过 JTAG 端口，用户可以下载 FPGA 程序、固化 FLASH 程序以及进行在线仿真。JTAG 电路包括二极管保护，以确保 FPGA 信号电压符合要求。然而，我们还是建议用户避免热插拔，以免损坏芯片。
  
  ![](./PE500-Reference_Manual.assets/JTAG.png)
  
  ### ○复位
  
  我们提供了一个按键（K1），可以用作FPGA上运行的设计的“复位”信号。
  
  ### ○Micro SD
  
  PE500提供了一个Micro SD接口，供用户访问SD卡存储器。
  
  SDIO信号与ZYNQ的SDIO连接。Bank 501的VCCIO电压为1.8V，而SD数据电压为3.3V，因此使用TXS02612进行电平转换。
  
  核心板与SD的连接图。
  
  ![](./PE500-Reference_Manual.assets/SD.png)

  ### ○SFP+

  PE500提供四个SFP+接口，每个SFP+使用两个收发器通道。用户可以使用SFP+热插拔光模块进行光纤数据通信。

  每个SFP+接口包括以下信号：

  - **收发器**：提供一个通道，支持高达10 Gbps的数据传输。
  - **SMBUS (I2C)**：3.3V信号，用于模块管理。
  - **控制信号**：包括状态控制。
  - **参考时钟**：来自底板的125 MHz差分时钟。
  
  核心板与SFP的连接图。
  
  ![](./PE500-Reference_Manual.assets/SFP.png)
  
  SFP+与XME7100的引脚连接分配表如下。
  
  | FPGA引脚 | XME7100信号名称 | PE500信号名称  | 说明                                    |
  | -------- | --------------- | -------------- | --------------------------------------- |
  | AK2      | MGT109_TX3_P    | SFP0_TX_P      | ZYNQ/FPGA收发器发送数据                 |
  | AK1      | MGT109_TX3_N    | SFP0_TX_N      | ZYNQ/FPGA收发器发送数据                 |
  | AJ4      | MGT109_TX2_P    | SFP1_TX_P      | ZYNQ/FPGA收发器发送数据                 |
  | AJ3      | MGT109_TX2_N    | SFP1_TX_N      | ZYNQ/FPGA收发器发送数据                 |
  | AK6      | MGT109_TX1_P    | SFP2_TX_P      | ZYNQ/FPGA收发器发送数据                 |
  | AK5      | MGT109_TX1_N    | SFP2_TX_N      | ZYNQ/FPGA收发器发送数据                 |
  | AK10     | MGT109_TX0_P    | SFP3_TX_P      | ZYNQ/FPGA收发器接收数据                 |
  | AK9      | MGT109_TX0_N    | SFP3_TX_N      | ZYNQ/FPGA收发器接收数据                 |
  | AE8      | MGT109_RX3_P    | SFP0_RX_P      | ZYNQ/FPGA收发器接收数据                 |
  | AE7      | MGT109_RX3_N    | SFP0_RX_N      | ZYNQ/FPGA收发器接收数据                 |
  | AG8      | MGT109_RX2_P    | SFP1_RX_P      | ZYNQ/FPGA收发器接收数据                 |
  | AG7      | MGT109_RX2_N    | SFP1_RX_N      | ZYNQ/FPGA收发器接收数据                 |
  | AJ8      | MGT109_RX1_P    | SFP2_RX_P      | ZYNQ/FPGA收发器接收数据                 |
  | AJ7      | MGT109_RX1_N    | SFP2_RX_N      | ZYNQ/FPGA收发器接收数据                 |
  | AH10     | MGT109_RX0_P    | SFP3_RX_P      | ZYNQ/FPGA收发器接收数据                 |
  | AH9      | MGT109_RX0_N    | SFP3_RX_N      | ZYNQ/FPGA收发器接收数据                 |
  | AD16     | B10_L18_P       | SFP0_TXDISABLE | Tx_Disable，上拉，高电平时关闭发送      |
  | AF12     | B10_L7_N        | SFP0_RXLOS     | Rx LOS，上拉，高电平表示LOS信号         |
  | AH14     | B10_L8_P        | SFP1_TXDISABLE | Tx_Disable，上拉，高电平时关闭发送      |
  | AH13     | B10_L8_N        | SFP1_RXLOS     | Rx LOS，上拉，高电平表示LOS信号         |
  | AB15     | B10_L22_P       | SFP2_TXDISABLE | Tx_Disable，上拉，高电平时关闭发送      |
  | AB14     | B10_L22_N       | SFP2_RXLOS     | Rx LOS，上拉，高电平表示LOS信号         |
  | AG12     | B10_L10_P       | SFP3_TXDISABLE | Tx_Disable，上拉，高电平时关闭发送      |
  | AH12     | B10_L10_N       | SFP3_RXLOS     | Rx LOS，上拉，高电平表示LOS信号         |
  | AC13     | B10_L19_N       | SFP0_RS0       | 接收信号检测0，低电平表示检测到有效信号 |
  | AE12     | B10_L7_P        | SFP0_RS1       | 接收信号检测0，低电平表示检测到有效信号 |
  | AD14     | B10_L9_P        | SFP1_RS0       | 接收信号检测0，低电平表示检测到有效信号 |
  | AD13     | B10_L9_N        | SFP1_RS1       | 接收信号检测1，低电平表示检测到有效信号 |
  | AJ15     | B10_L5_P        | SFP1_SCL       | SMBUS (I2C) 时钟信号                    |
  | AK15     | B10_L5_N        | SFP1_SDA       | SMBUS (I2C) 数据信号                    |
  | AD15     | B10_L18_N       | SFP0_SCL       | SMBUS (I2C) 时钟信号                    |
  | AC14     | B10_L19_P       | SFP0_SDA       | SMBUS (I2C) 数据信号                    |
  | AJ14     | B10_L3_P        | SFP1_LED1      | SFP状态LED                              |
  | AJ13     | B10_L3_N        | SFP1_LED2      | SFP状态LED                              |
  | AB12     | B10_L21_P       | SFP0_LED1      | SFP状态LED                              |
  | AC12     | B10_L21_N       | SFP0_LED2      | SFP状态LED                              |
  
  ### ○HDMI
  
  一个 HDMI 视频输出接口可以实现 720P 图像以及视频输出。
  
  ![](./PE500-Reference_Manual.assets/HDMI.png)
  
  ### ○PCIe
  
  PE500底板是一个标准的PCI-Express卡。其机械尺寸符合PCIe卡电气规范。它设计为标准PCIe x8插槽卡，通过PCIe金手指支持八个TX和RX通道。每个通道的最大通信速率可达5 Gbps，满足PCIe Gen2数据传输要求。PCIe 参考时钟由 PCIe ROOT 设备（通常是 PC）的 PCIe 插槽提供给开发板，参考时钟频率为 100MHz。
  
  ![](./PE500-Reference_Manual.assets/1.png)

  ### ○LED

  PE500包括五个LED，一个电源指示灯和四个由PL控制的用户LED。当FPGA的相应引脚处于低电平时，LED点亮。

  | 位置 | 信号名称 | 引脚编号 |
  | ---- | -------- | -------- |
  | D8   | PL_LED1  | AB21     |
  | D11  | PL_LED2  | AB22     |
  | D10  | PL_LED3  | AG22     |
  | D9   | PL_LED4  | AH22     |

  ### ○按键

  我们提供了四个按键供用户使用。按下按键时，FPGA的相应引脚将处于低电平。

  | 位置 | 信号名称 | 引脚编号 |
  | ---- | -------- | -------- |
  | K5   | PL_KEY1  | AJ20     |
  | K4   | PL_KEY2  | AK20     |
  | K3   | PL_KEY3  | AK17     |
  | K2   | PL_KEY4  | AK18     |
  
  ### ○GPIO
  
  载板提供两个IDC40 GPIO扩展端口，JP1和JP2，允许连接Microphase技术模块或其他外设。**使用IO时，请确保连接信号的电压一致。**
  
  **JP1:**
  
  | 引脚 | 信号名称  | 引脚编号 | 引脚 | 信号名称  | 引脚编号 |
  | ---- | --------- | -------- | ---- | --------- | -------- |
  | 1    | GPIO1_0P  | AF15     | 2    | GPIO1_0N  | AG15     |
  | 3    | GPIO1_1P  | AF14     | 4    | GPIO1_1N  | AG14     |
  | 5    | GPIO1_2P  | AE13     | 6    | GPIO1_2N  | AF13     |
  | 7    | GPIO1_3P  | AB17     | 8    | GPIO1_3N  | AB16     |
  | 9    | GPIO1_4P  | AE16     | 10   | GPIO1_4N  | AE15     |
  | 11   | VCC_5V    | -        | 12   | GND       | -        |
  | 13   | GPIO1_5P  | AE18     | 14   | GPIO1_5N  | AE17     |
  | 15   | GPIO1_6P  | AC17     | 16   | GPIO1_6N  | AC16     |
  | 17   | GPIO1_7P  | AH19     | 18   | GPIO1_7N  | AJ19     |
  | 19   | GPIO1_8P  | Y22      | 20   | GPIO1_8N  | Y23      |
  | 21   | GPIO1_9P  | AD21     | 22   | GPIO1_9N  | AE21     |
  | 23   | GPIO1_10P | AF19     | 24   | GPIO1_10N | AG19     |
  | 25   | GPIO1_11P | AA22     | 26   | GPIO1_11N | AA23     |
  | 27   | GPIO1_12P | AE22     | 28   | GPIO1_12N | AF22     |
  | 29   | VCC_3V3   | -        | 30   | GND       | -        |
  | 31   | GPIO1_13P | AD23     | 32   | GPIO1_13N | AE23     |
  | 33   | GPIO1_14P | AC22     | 34   | GPIO1_14N | AC23     |
  | 35   | GPIO1_15P | AF23     | 36   | GPIO1_15N | AF24     |
  | 37   | GPIO1_16P | AC24     | 38   | GPIO1_16N | AD24     |
  | 39   | GPIO1_17P | AA24     | 40   | GPIO1_17N | AB24     |
  
  **JP2:**
  
  | 引脚 | 信号名称  | 引脚编号 | 引脚 | 信号名称  | 引脚编号 |
  | ---- | --------- | -------- | ---- | --------- | -------- |
  | 1    | GPIO2_0P  | R27      | 2    | GPIO2_0N  | T27      |
  | 3    | GPIO2_1P  | U25      | 4    | GPIO2_1N  | V26      |
  | 5    | GPIO2_2P  | T29      | 6    | GPIO2_2N  | U29      |
  | 7    | GPIO2_3P  | U22      | 8    | GPIO2_3N  | V22      |
  | 9    | GPIO2_4P  | P30      | 10   | GPIO2_4N  | R30      |
  | 11   | VCC_5V    | -        | 12   | GND       | -        |
  | 13   | GPIO2_5P  | N29      | 14   | GPIO2_5N  | P29      |
  | 15   | GPIO2_6P  | T30      | 16   | GPIO2_6N  | U30      |
  | 17   | GPIO2_7P  | R28      | 18   | GPIO2_7N  | T28      |
  | 19   | GPIO2_8P  | W25      | 20   | GPIO2_8N  | W26      |
  | 21   | GPIO2_9P  | U24      | 22   | GPIO2_9N  | V24      |
  | 23   | GPIO2_10P | R25      | 24   | GPIO2_10N | R26      |
  | 25   | GPIO2_11P | U26      | 26   | GPIO2_11N | U27      |
  | 27   | GPIO2_12P | P23      | 28   | GPIO2_12N | P24      |
  | 29   | VCC_3V3   | -        | 30   | GND       | -        |
  | 31   | GPIO2_13P | T22      | 32   | GPIO2_13N | T23      |
  | 33   | GPIO2_14P | N26      | 34   | GPIO2_14N | N27      |
  | 35   | GPIO2_15P | P25      | 36   | GPIO2_15N | P26      |
  | 37   | GPIO2_16P | R22      | 38   | GPIO2_16N | R23      |
  | 39   | GPIO2_17P | T24      | 40   | GPIO2_17N | T25      |
  
  ### ○电源
  
  开发板需要DC12V电源。请使用指定的电源以避免损坏。开发板还支持通过PCle接口供电。电源结构如下。
  
  ![](./PE500-Reference_Manual.assets/Power_structure.png)
  
  ## ●3. 相关文档
  
  ### ○PE500
  
  - [PE500_R10 原理图](https://github.com/MicroPhase/fpga-docs/blob/master/schematic/PE500_R10.pdf) (PDF)
  - [PE500_R10 尺寸图](https://github.com/MicroPhase/fpga-docs/blob/master/mechanical/PE500/PE500_R10_Dimensions.pdf) (PDF)  
  - [PE500_R10 板源文件](https://github.com/MicroPhase/fpga-docs/blob/master/others/PE500_R10_Board_source_file.brd) (Brd)  
  
  ### ○Microphase的6*8 XME系列SoM
  
  - [XME7035 参考手册](https://documentation-of-microphase-fpga-board.readthedocs.io/en/latest/SoM/XME7035/XME7035-Reference_Manual.html)(HTML)
  - [XME7100 参考手册](https://documentation-of-microphase-fpga-board.readthedocs.io/en/latest/SoM/XME7100/XME7100-Reference_Manual.html)(HTML)