# **PE100 Reference Manual**

## Revision History

| Revision | Time  | Description   |
| :------- | :---- | :------------ |
| Rev. 1.0 | 2024. | First Release |
|          |       |               |

## CopyRight Notice:

Copyright ©2015 by MicroPhase Technologies (Shanghai) Co. Ltd. All rights are reserved.

## WeChat Public Number:

![image-20240808164018087](G:\MARKDOWN_DOC\DEV\XME0724\XME0724_Reference Manual_ES1_240908.assets\image-20240808163724633.png)

<div style="page-break-after:always;"></div>


## ●1. Overview

​	Using PE100, you can quickly test, developed and evaluated the function of the Microphase's 5*6 XME serious SoM. It provide various of interface for XME serious SoM, such as HDMI TX, Giga ETH, SFP ,PCIe 2.0 x1 and so on.

​	For now, it support XME0715 and XME0720. The most recommend is to use with XME0715.The following is based on the XME0715 unless noted.

### ○Board Layout

![pe100_LAYOUT](G:\MARKDOWN_DOC\BASEDBOARD\PE100\PE100_Reference Manual_Rev1.0_241016.assets\pe100_LAYOUT.png)

### ○Key Features

- 1 PCIe x1
- 2 Giga ETH supports 10/100/1000M network transfer rate,1 for PS, 1 for PL
- 2 SFP
- 1 HDMI TX
- 1 USB UART
- 1 SD
- 2 40 pin Extension ports
- 1 JTAG debug port
- 1 system reset key, 2 user's key
- 4 user's LED

### ○Block diagram

![](G:\MARKDOWN_DOC\BASEDBOARD\PE100\PE100_Reference Manual_Rev1.0_241016.assets\BLOCKDIAGRAM.png)

### ○Mechanical Spec

![](G:\MARKDOWN_DOC\BASEDBOARD\PE100\PE100_Reference Manual_Rev1.0_241016.assets\Allegro.png)

### ○Core Board Matching Description

✔️：Support

❌：Not support

⚠️ :  Pay attention when using

⭐ :  Not fully supported

| PE100    | XME0712 | XME0715-35T | XME0715-75T/100T/200T | XME0720    |
| -------- | ------- | ----------- | --------------------- | ---------- |
| PCIE x1  | ✔️       | ✔️           | ✔️                     | ❌          |
| ETH0     | ❌       | ✔️(PS side)  | ✔️                     | ✔️(PS side) |
| ETH1     | ✔️       | ✔️           | ✔️                     | ✔️          |
| HDMI TX  | ✔️       | ✔️           | ✔️                     | ✔️          |
| SFP x2   | ✔️       | ✔️           | ✔️                     | ❌          |
| USB-UART | ✔️       | ✔️           | ✔️                     | ✔️          |
| SD       | ❌       | ✔️(PS side)  | ✔️(PS side)            | ✔️(PS side) |
| GPIO1    | ✔️       | ✔️           | ✔️                     | ✔️          |
| GPIO2    | ✔️       | ⭐           | ✔️                     | ✔️          |

## ●2. Function Resources

### ○Giga ETH

​	The baseboard provided 2 Gigabit Ethernet interfaces. The phy IC of ETH0 is integrated in the core board. It's connected with core board according to the signs of MDI. More information of the ETH0 PHY, please reference the  corresponding core board document.

​	The phy of ETH1 is Marvell Alaska 88E1512. The ETH PHY IC connected with core board according to the RGMII interface. The function of 88E1512 is powerful. It support RGMII to RJ45, SGMII to RJ45 and so on. Supports MDI/MDIX self-adaptation and 10/100/1000M self-adaptation.

​	Diagram of connecting the core board and two Ethernet phy chips.

![image-20241018143117373](G:\MARKDOWN_DOC\BASEDBOARD\PE100\PE100_Reference Manual_Rev1.0_241016.assets\image-20241018143117373.png)

The pin connection assignment table for ETH0 and XME0715 is as follows.

|      |      |      |      |
| ---- | ---- | ---- | ---- |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |

The pin connection assignment table for ETH1 and XME0715 is as follows.

|      |      |      |
| ---- | ---- | ---- |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |
|      |      |      |

### ○USB HOST

​	PE100 provide four USB Host interfaces. **For XME0712,USB Host is not support.** The  USB 3320 is  integrated in the core board. The based board expansion four USB Host according to the USB HUB IC USB2514. The interface of USB host is TYPE-A, it can connected with different USB Slave peripheral, such as USB mouse, USB keyboard, USB WIFI and so on.

​	Diagram of connecting the core board and two Ethernet phy chips.

​	![image-20241018151127056](G:\MARKDOWN_DOC\BASEDBOARD\PE100\PE100_Reference Manual_Rev1.0_241016.assets\image-20241018151127056.png)

The pin connection assignment table for USB and XME0715 is as follows.

|      |      |      |      |
| ---- | ---- | ---- | ---- |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |

### ○USB UART

​	The base board provide a USB to UART interface, the chip is Silicon Labs CP2102. The USB is Micro USB.

![image-20241018160356753](G:\MARKDOWN_DOC\BASEDBOARD\PE100\PE100_Reference Manual_Rev1.0_241016.assets\image-20241018160356753.png)

The pin connection assignment table for UART and XME0715 is as follows.

|      |      |      |
| ---- | ---- | ---- |
|      |      |      |
|      |      |      |

### ○SD

​	PE100 provide a Micro SD interface for users to access the SD card memory. **For XME0712,SD is not support.** 

​	The SDIO sign connected with ZYNQ's SDIO. The VCCIO voltage of Bank 501 is 1.8V while the SD data voltage is 3.3V, thus using TXS02612 to conversion level.

Diagram of connecting the core board and SD.