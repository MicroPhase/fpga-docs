# **XME0724CB 用户手册**

[[English]](https://microphase-doc.readthedocs.io/en/latest/DEV_BOARD/XME0724CB/XME0724CB-Reference_Manual.html)

## 开发环境：

Vivado 2018.3 可从 Xilinx 官网下载

<https://www.xilinx.com>

## 微信公众号：

![](./XME0724CB-Reference_Manual.assets/VX.png)

## ●1. 概述

XME0724CB 为评估 XME0724 核心板而设计的专用底板。底板为 ZYNQ PS 部分搭载了千兆网口， 1 个 USB Host 接口， USB UART 接口， TF 卡接口， CAN 接口； ZYNQ PL 部分全部以 GPIO 扩展口引出。支持 Linux，资料提供包括完整全套资料，外扩接口驱动， BSP 源码包，开发工具等。为开发者提供了完善的软件开发环境，缩短产品 ZYNQ SoC XC7Z010/020 开发周期，实现产品快速上市。

### ○板卡布局

![](./XME0724CB-Reference_Manual.assets/0724CB_B_LAYOUT.png)

### ○资源特性

- 按键：2 个用户按键，1 个 PS 控制，1 个 PL 控制。
  
- GPIO：2 个 40 针扩展端口（2.54mm 间距），每个端口提供 36 个 PL IO  
&ensp;&ensp;&ensp; &ensp;&ensp;1 个 30 针扩展端口（2.54mm 间距），提供 20 个 PL IO 和 4 个 PS IO。  
&ensp;&ensp;&ensp; &ensp;&ensp;所有 PL IO 电压可调。

- JTAG：1 个 10 针 JTAG 接口。

- ETH：1 个千兆以太网接口
- USB Host：1 个 Type-A USB Host 接口
- SD 卡：1 个 SD 卡接口
- USB UART：1 个 TYPE-C USB UART 接口
- CAN：2 个 CAN 接口

### ○系统框图

![](./XME0724CB-Reference_Manual.assets/0724CB_BLOCK_DIAGRAM.png)

### ○机械尺寸

![](./XME0724CB-Reference_Manual.assets/XME0724CB_R21_4C_Mechanical.jpg)

## ●2. 硬件资源

### ○千兆以太网

以太网 PHY 集成在 XME0724 核心板上，提供 MDI 接口，RJ45 接口连接到 XME0724CB 底板上。

![image-20241127165940491](./XME0724CB-Reference_Manual.assets/ETH.png)

### ○USB Host

XME0724CB 上有一个 USB2.0 HOST 端口。USB 端口为扁型 USB 接口（USB Type A），可用于连接不同的 USB 从设备，如 USB 鼠标、USB 键盘、USB WIFI、USB 摄像头等外设。

![](./XME0724CB-Reference_Manual.assets/Host.png)

### ○USB UART

USB 转 UART 使用 CH340E，连接到 PS Bank500 MIO14、MIO15，用于提供 PC 和 ZYNQ 之间的串行通信。

![](./XME0724CB-Reference_Manual.assets/UART.png)

### ○JTAG

XME0724CB 提供 IDC10 JTAG 接口，用户可以将 USB 下载器连接到 JTAG 端口以下载或仿真 ZYNQ 的程序，请避免带电插拔，以免损坏芯片。

![](./XME0724CB-Reference_Manual.assets/JTAG.png)

### ○启动配置

XME0724CB 提供三种启动模式：SD 卡启动、QSPI 启动和 JTAG 启动。用户可以通过拨动 SW1 拨码开关来改变模式引脚的电压以更改启动模式。

![image-20241205145328751](./XME0724CB-Reference_Manual.assets/image-20241205145328751.png)

### ○复位

我们提供了一个按键（K1），可用作 FPGA 上运行的设计的“复位”信号。

### ○Micro SD

板卡提供了一个 Micro SD 卡接口，允许用户访问 SD 卡存储器。它还提供了 ZYNQ 芯片的引导加载程序、Linux 操作系统内核、文件系统和其他用户数据文件的存储。

SDIO 信号连接到 ZYNQ 的 PS BANK501（MIO40-MIO45）的 IO 信号。BANK501 的 VCCIO 电压为 1.8V，而 SD 卡的数据电平为 3.3V，因此需要连接一个电平转换芯片 TXS02612。

![](./XME0724CB-Reference_Manual.assets/SD_BD.png)

### ○按键

我们提供了两个按键供用户使用。按键按下时对应管脚为低电平。

| 位置 |    信号名称    | 引脚号 |  说明   |
| :--: | :------------: | :----: | :-----: |
|  K2  |     PS_KEY     |   B5   | PS 按键 |
|  K3  | B35_L12_N_MRCC |  K18   | PL 按键 |

### ○CAN

基板上提供了两个 TI SN65HVD230 CAN 收发器，它们连接到 PS Bank500 MIO10-MIO13。核心板与 CAN 芯片的连接如下表所示：

| CAN 信号 | SoM 引脚 | ZYNQ 引脚名称 | ZYNQ 引脚号 |
| -------- | -------- | ------------- | ----------- |
| CAN0_RX  | Pin_146  | PS_MIO10_500  | E9          |
| CAN0_TX  | Pin_147  | PS_MIO11_500  | C6          |
| CAN1_TX  | Pin_148  | PS_MIO12_500  | D9          |
| CAN1_RX  | Pin_149  | PS_MIO13_500  | E8          |

CAN 信号连接到 J12 扩展端口，可以通过跳线在 CAN 信号线上添加 60.4 欧姆的终端电阻。对于 CAN0，终端电阻可以添加在 Pin1 和 Pin2 之间；对于 CAN1，终端电阻可以添加在 Pin9 和 Pin10 之间。

| 说明      | 引脚 | 引脚 | 说明  |
| --------- | ---- | ---- | ----- |
| CAN0 终端 | 1    | 2    | CANL0 |
| CANH0     | 3    | 4    | CANL0 |
| GND       | 5    | 6    | GND   |
| CANH1     | 7    | 8    | CANL1 |
| CAN1 终端 | 9    | 10   | CANL1 |

### ○GPIO

基板提供了 3 个扩展 IO 端口，2 个 40 针扩展端口 JP1 和 JP2，一个 30 针扩展端口 JP3，供用户扩展更多外设和接口，接口默认未焊接，用户可以根据需要自行焊接双排针或母座。

40 针扩展端口提供 1 路 5V 电源、1 路 3.3V 电源、2 路地和 36 路 IO 端口，而 30 针扩展端口提供 1 路 5V 电源、1 路 3.3V 电源、2 路地和 24 路 IO 端口。使用时请注意 IO 的电压，确保连接的信号电压一致，如果不一致，需要添加外部电平转换芯片，错误使用会烧毁 ZYNQ 主芯片。

**JP1**

| 引脚 | 信号名称  | 引脚号 | 引脚 | 信号名称  | 引脚号 |
| :--: | :-------: | :----: | :--: | :-------: | :----: |
|  1   | GPIO1_0P  |  U18   |  2   | GPIO1_0N  |  U19   |
|  3   | GPIO1_1P  |  T20   |  4   | GPIO1_1N  |  U20   |
|  5   | GPIO1_2P  |  V20   |  6   | GPIO1_2N  |  W20   |
|  7   | GPIO1_3P  |  W18   |  8   | GPIO1_3N  |  W19   |
|  9   | GPIO1_4P  |  Y18   |  10  | GPIO1_4N  |  Y19   |
|  11  |  VCC_5V   |   -    |  12  |    GND    |   -    |
|  13  | GPIO1_5P  |  V17   |  14  | GPIO1_5N  |  V18   |
|  15  | GPIO1_6P  |  Y16   |  16  | GPIO1_6N  |  Y17   |
|  17  | GPIO1_7P  |  T16   |  18  | GPIO1_7N  |  U17   |
|  19  | GPIO1_8P  |  V16   |  20  | GPIO1_8N  |  W16   |
|  21  | GPIO1_9P  |  U14   |  22  | GPIO1_9N  |  U15   |
|  23  | GPIO1_10P |  V15   |  24  | GPIO1_10N |  W15   |
|  25  | GPIO1_11P |  W14   |  26  | GPIO1_11N |  Y14   |
|  27  | GPIO1_12P |  T14   |  28  | GPIO1_12N |  T15   |
|  29  |  VCC_3V3  |   -    |  30  |    GND    |   -    |
|  31  | GPIO1_13P |  P14   |  32  | GPIO1_13N |  R14   |
|  33  | GPIO1_14P |  V12   |  34  | GPIO1_14N |  W13   |
|  35  | GPIO1_15P |  U13   |  36  | GPIO1_15N |  V13   |
|  37  | GPIO1_16P |  T12   |  38  | GPIO1_16N |  U12   |
|  39  | GPIO1_17P |  T11   |  40  | GPIO1_17N |  T10   |

**JP2**



| 引脚 | 信号名称  | 引脚号 | 引脚 | 信号名称  | 引脚号 |
| :--: | :-------: | :----: | :--: | :-------: | :----: |
|  1   | GPIO2_0P  |  J18   |  2   | GPIO2_0N  |  H18   |
|  3   | GPIO2_1P  |  E17   |  4   | GPIO2_1N  |  D18   |
|  5   | GPIO2_2P  |  E18   |  6   | GPIO2_2N  |  E19   |
|  7   | GPIO2_3P  |  C20   |  8   | GPIO2_3N  |  B20   |
|  9   | GPIO2_4P  |  K14   |  10  | GPIO2_4N  |  J14   |
|  11  |  VCC_5V   |   -    |  12  |    GND    |   -    |
|  13  | GPIO2_5P  |  B19   |  14  | GPIO2_5N  |  A20   |
|  15  | GPIO2_6P  |  H15   |  16  | GPIO2_6N  |  G15   |
|  17  | GPIO2_7P  |  F16   |  18  | GPIO2_7N  |  F17   |
|  19  | GPIO2_8P  |  D19   |  20  | GPIO2_8N  |  D20   |
|  21  | GPIO2_9P  |  L16   |  22  | GPIO2_9N  |  L17   |
|  23  | GPIO2_10P |  F19   |  24  | GPIO2_10N |  F20   |
|  25  | GPIO2_11P |  G17   |  26  | GPIO2_11N |  G18   |
|  27  | GPIO2_12P |  G19   |  28  | GPIO2_12N |  G20   |
|  29  |  VCC_3V3  |   -    |  30  |    GND    |   -    |
|  31  | GPIO2_13P |  K19   |  32  | GPIO2_13N |  J19   |
|  33  | GPIO2_14P |  M17   |  34  | GPIO2_14N |  M18   |
|  35  | GPIO2_15P |  L19   |  36  | GPIO2_15N |  L20   |
|  37  | GPIO2_16P |  M19   |  38  | GPIO2_16N |  M20   |
|  39  | GPIO2_17P |  H16   |  40  | GPIO2_17N |  H17   |

**JP3**

| 引脚 | 信号名称 | 引脚号 | 引脚 | 信号名称 | 引脚号 |
| ---- | -------- | ------ | ---- | -------- | ------ |
| 1    | GPIO3_0P | J20    | 2    | GPIO3_0N | H20    |
| 3    | GPIO3_1P | K16    | 4    | GPIO3_1N | J16    |
| 5    | GPIO3_2P | L14    | 6    | GPIO3_2N | L15    |
| 7    | GPIO3_3P | N15    | 8    | GPIO3_3N | N16    |
| 9    | GPIO3_4P | N18    | 10   | GPIO3_4N | P19    |
| 11   | -        | -      | 12   | -        | -      |
| 13   | GPIO3_5P | N20    | 14   | GPIO3_5N | P20    |
| 15   | GPIO3_6P | P15    | 16   | GPIO3_6N | P16    |
| 17   | GPIO3_7P | R16    | 18   | GPIO3_7N | R17    |
| 19   | GPIO3_8P | N17    | 20   | GPIO3_8N | P18    |
| 21   | GPIO3_9P | T17    | 22   | GPIO3_9N | R18    |
| 23   | -        | -      | 24   | -        | -      |
| 25   | -        | -      | 26   | -        | -      |
| 27   | -        | -      | 28   | -        | -      |
| 29   | VCC_3V3  | -      | 30   | GND      | -      |

### ○电源

板卡使用 USB 提供的 +5V 电源。下图显示了 USB 可用于提供电源。

![](./XME0724CB-Reference_Manual.assets/UART.png)

## ●3. 相关文档

### ○XME0724

- [XME0724 用户手册](https://fpga-docs.microphase.cn/zh-cn/latest/SoM/XME0724/XME0724-Reference_Manual.html)(HTML)

- [XME0724_R30 原理图](https://swnatyr2ph.feishu.cn/file/JYtybEyWooePwTxUEAUcTfqvndb) (PDF)
- [XME0724_R30 尺寸](https://swnatyr2ph.feishu.cn/file/MfFQbcd7mo0FpAxEpNhcsMGcnYe) (PDF)  
- [XME0724_R30 尺寸源文件](https://swnatyr2ph.feishu.cn/file/EOf2bN3Vbo2krnxNALScAfBWnEd) (DXF)  

### ○XME0724CB

- [XME0724CB_R21 原理图](https://swnatyr2ph.feishu.cn/file/RTkTb8JuXo0QBAxfMYEckDqbnlb)(PDF)
- [XME0724CB_R21 尺寸](https://swnatyr2ph.feishu.cn/file/VMQ4bcZNvojPVWxrjJBc6RgIn4g)(PDF)
- [XME0724CB_R21 板卡源文件](https://swnatyr2ph.feishu.cn/file/FoCXbJ2IKo3Y6UxgFPDcF4vSndf)(Brd)

### ○XME0724CB-NET

- XME0724CB-NET 用户手册(HTML)-待添加
- [XME0724CB-NET_R30 原理图](https://swnatyr2ph.feishu.cn/file/SP7lbSA1ooeMTTxbMJ3cKlJInbg)(PDF)
- [XME0724CB-NET_R30 尺寸](https://swnatyr2ph.feishu.cn/file/VMQ4bcZNvojPVWxrjJBc6RgIn4g)(PDF)
