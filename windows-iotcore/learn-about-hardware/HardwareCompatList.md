---
title: 硬件兼容性列表
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Windows 10 IoT Core 最支持的外围接口和协议。
keywords: windows iot，外围设备，协议，兼容性，总线，硬件
ms.openlocfilehash: 058f5aad2f0d233466f3d0e8615d1e0112f0ee48
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655823"
---
# <a name="hardware-compatibility-list"></a>硬件兼容性列表

Windows 10 IoT Core 支持各种外设接口和协议，其中包括支持 I2C、UART、USB 等常见总线。 本页列出了已知受支持的外围设备，最新版本的 RTM 版本是最新版本。 特定条目仅适用于内部版本，并将进行记录。 我们鼓励你在 GitHub 上参与此列表！

> [!IMPORTANT]
> 此列表并未囊括所有方式。 此页面上未列出与 Windows 10 IoT Core 兼容的其他许多外设。 如果设备未列出，但符合 Windows 10 IoT Core 中已支持的功能，则它将起作用。 


正在寻找有关支持的硬件平台的信息？ 有关与 Windows 兼容的开发板的列表，请查看 [soc 和自定义板](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards) 。

## <a name="usb-devices"></a>USB 设备

### <a name="wifi-adapters"></a>WiFi 适配器
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | 官方 Raspberry Pi WiFi 转换器 | ARM32、x64、x86 | 官方 Raspberry Pi WiFi 转换器为其 diminutive 大小提供最佳的 WiFi 性能。 | | &#10004;  |
> | Airlink 无线 N 150 微型 USB 适配器 | x64、x86 | Airlink 101 AWL5077 黄金150Mbps 无线迷你 u 适配器与 WPA2、WPA 和 WEP 增强型无线安全性 | | &#10004;  
> | Panda PAU06 | x64、x86 |  带有高增益天线的 Panda 300Mbps 无线 N USB 适配器 | |  &#10004;  
> | TP-链接 TL_WN725N |  ARM32、x64、x86 | TP-LINK TL-WN725N 无线 N Nano USB 适配器 150 Mbps `(USB/VID_0BDA&PID_8179)` |  | &#10004;  
> | DYN USB WiFi 适配器 | MBM | WiFi USB 适配器网络-DYN | |  &#10004;  
> | Realtek 8191 USB 无线 WiFi | ARM32、x64、x86 | Realtek 8191 300Mbps 802.11 n/g/b/USB 无线 WiFi LAN 网卡适配器 | | &#10004;  
> | Realtek 8192 USB 无线 WiFi | ARM32、x64、x86 | Realtek 单芯片 IEEE 802.11 b/g/n 2T2R WLAN 控制器与 USB 2.0 接口 | | &#10004; |
> | Realtek 8188EU USB 无线 WiFi | ARM32、Mx64、x86BM | Realtek RTL8188EU 无线 LAN 802.11 n/g/b USB 2.0 网络适配器 | | &#10004; |
> | Realtek 8192EU USB 无线 WiFi | ARM32、x64、x86 | Realtek RTL8192EU 无线 LAN 802.11 n/g/b USB 2.0 网络适配器 | | &#10004; |
> | CanaKit USB 无线 WiFi | x64、x86 | 芯片组 Ralink 5370 | | &#10004;
> | D-link DWA-172 | ARM32 | 无线 AC600 双频高增益 USB 适配器 | [数据表](ftp://ftp.dlink.de/dwa/dwa-172/documentation/DWA-172_ds_en_Datasheet.pdf) |

### <a name="ethernet-adapters"></a>以太网适配器
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | .ASIX AX88772 USB 2.0 快速以太网适配器 | ARM32、x64、x86 | 这是一种高性能和高度集成的 ASIC，其中嵌入了 28 KB SRAM 用于数据包缓冲。  | | &#10004;  |


### <a name="bluetooth-dongles"></a>蓝牙连接器
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | CSR 迷你 u 蓝牙 V 4.0 适配器 | ARM32、x64、x86 | 2类蓝牙4.0 智能就绪适配器，低能耗，双电源 |  | &#10004; 
> | ORICO BTA-403 微型蓝牙 4.0 USB 转换器 | ARM32、x64、x86 | 低能耗蓝牙4.0 适配器 USB 微适配器转换器 |  | &#10004; 
> | CSR 迷你 u 蓝牙 V 4.0 适配器 | x64、x86 | 2类蓝牙4.0 智能就绪适配器，低能耗，双电源 |  | &#10004;|

### <a name="cameras"></a>摄像头
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Microsoft Lifecam 3000 USB 摄像机 | ARM32、x64、x86 | USB 网络摄像机 | [Home Security 相机项目](https://developer.microsoft.com/en-us/windows/iot/samples/webcamapp)|&#10004;|
> | Microsoft Lifecam HD-5000 | ARM32、x64、x86 | Microsoft LifeCam HD-5000 720p HD 网络摄像头 | | &#10004; |
> | Microsoft® LifeCam Studio™ | ARM32 | Microsoft® LifeCam Studio™ (模型： 1425) 1080p HD 网络摄像机 | | |
> | Logitech 网络摄像机 C210 | ARM32、x64、x86 | USB 网络摄像机，1.3 mp 照片 |  |&#10004; |

### <a name="audio"></a>音频
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证 |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Sabrent USB 外部立体声声音适配器，模型 AU-EMAC1 | ARM32、x64、x86 | 将 USB 转换为 3.5 mm 音频和麦克风信号 | | &#10004; 

### <a name="miscellaneous"></a>杂项
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Aeon Labs Z-波形 Z-摇杆系列 2 USB 转换器 DSA02203-ZWUS | ARM32 | 序列 2 Z 波 USB Z 棒控制器 |  | &#10004; |
> | [Chalkboard 电子 7 "LCD 电容式触摸屏显示](https://www.chalk-elec.com/?page_id=1280#!/7-black-frame-universal-HDMI-LCD-with-capacitive-multi-touch/p/21750201/category=3094861) | ARM32 | | [正在更新固件](https://www.chalk-elec.com/?p=1826) | &#10004; |
> | Vodafone (Huawei) K5150 | ARM32、x64、x86 | Vodafone (Huawei) K5150 150Mbps 4G LTE FDD USB 移动宽带调制解调器 |  | &#10004;  |
> | Vodafone (Huawei) K5160 | ARM32、x64、x86 | Vodafone (Huawei) K5160 150Mbps GSM/EDGE/3G/HSPA +/LTE-CAT4 USB 移动宽带调制解调器 |  | |
> | 塞拉利昂无线横梁 (AirCard 340U)  | x64、x86 |    塞拉利昂无线横梁 (AirCard 340U) 4G LTE USB 移动宽带调制解调器 |  |&#10004; |
> | Microsoft Xbox 360 控制器 | ARM32 | 适用于 Microsoft Xbox 360 的符合 HID 标准的 USB 游戏板 | [机器人工具包](https://microsoft.hackster.io/en-US/windowsiot/robot-kit-6dd474) |  &#10004; |
> | [MyTeletouch](http://www.myteletouch.com/) | ARM，x32 | 符合 HID 标准的 USB 无线鼠标、键盘和游戏板 |  | &#10004; |

## <a name="other-hardware-peripherals"></a>其他硬件外设

### <a name="nfcrfidproximity"></a>NFC/RFID/邻近性
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证 |
> |----------------|-------------------|-------------|--------|------------------------------|
> | NXP OM5577 演示板 | ARM32 | NXP PN7120 NFC 芯片的演示板。 | [ProximityDevice 文档](https://docs.microsoft.com/uwp/api/Windows.Networking.Proximity.ProximityDevice) | &#10004; |
> | NXP PN547/PN548/PN7120 | ARM32、x64、x86 | 支持的 NXP NFC 芯片。 | | &#10004; |

### <a name="pi-hats"></a>Pi 帽子
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit 16 通道 PWM](https://www.adafruit.com/product/2327#description-anchor) | ARM32 | 添加了一种功能，用于控制多达16个伺服，无附加的 Raspberry Pi 处理开销。 可以执行最多为 1.6 KHz、12位精度的 PWM。 | [Adafruit 教程 c # IoT 示例](https://github.com/golaat/Adafruit.Pwm) | |
> | [Dexter 工业 GrovePi](https://www.dexterindustries.com/shop/grovepi-board/) | ARM32 | 无需焊接即可连接数百个不同的传感器，因此你可以对其进行编程，以便在生活中监视、控制和自动化设备。 | [GrovePi 示例](https://github.com/DexterInd/GrovePi/) | |
> | Dexter 工业 GoPiGo | ARM，x32 | GoPiGo 是 Raspberry Pi 的不知和完整机器人，可将 Pi 变成完全操作的机器人。 GoPiGo 是一个移动机器人平台，适用于 Dexter 行业开发的 Raspberry Pi。 | [GoPiGo 示例](https://github.com/DexterInd/GoPiGo/tree/master/Software/CSharp) | |
> | [Raspberry PI 的 SeeedStudio Grove 基本 Hat](https://www.seeedstudio.com/Grove-Base-Hat-for-Raspberry-Pi.html) |ARM| RPI 的 Grove 基本 Hat 在 Raspbery PI 平台上提供对 Seeedstudio Grove 系统的支持。| [库和示例](https://github.com/KiwiBryn/GroveBaseHatWindows10IoTCore) | |
> | [SeeedStudio Grove for Raspberry PI Zero](https://www.seeedstudio.com/Grove-Base-Hat-for-Raspberry-Pi-Zero-p-3187.html) |ARM| RPI 0 的 Grove 基本 Hat 为 Raspbery PI 平台上的 Seeedstudio Grove 系统提供支持。| [库和示例](https://github.com/KiwiBryn/GroveBaseHatWindows10IoTCore) | |

### <a name="semtech-sx127x-based-lora-pi-hats"></a>[基于 Semtech SX127X 的 LoRa® Pi 帽子](https://www.semtech.com/products/wireless-rf/lora-transceivers)
Semtech 的 LoRa®超长范围 (100M 到 10KM) 传播频谱通信技术具有高干扰抗干扰性，并为将备有电池的设备连接到传统的网络基础结构提供了低成本的解决方案。

> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit LoRa 收音机 Bonnet 433MHz](https://www.adafruit.com/product/4075) | ARM32 | 433MHz LoRa 连接，3个按钮和一个 OLED 显示。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Adafruit LoRa 收音机 Bonnet 868/915MHz](https://www.adafruit.com/product/4074) | ARM32 | 868/915MHz LoRa 连接，3个按钮和一个 OLED 显示器。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Dragino LoRa GPS Hat for Config-raspberrypi.json 433/868/915MHz](http://www.dragino.com/products/lora/item/106-lora-gps-hat.html) | ARM32 | 433/868/915MHz LoRa 连接选项和 GPS。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [RPI 915MHz 的 Elecrow LoRa RFM95 IoT 板](https://www.elecrow.com/lora-rfm95-iot-board-for-rpi.html) | ARM32 | 915MHz LoRa 连接和 Grove 套接字。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [电子技巧 Lora/LoraWan 盾牌 Raspberry Pi Zero and PI3](https://www.tindie.com/products/electronictrik/loralorawan-shield-for-raspberry-pi-zero-and-pi3/) | ARM32 | 868/915MHz LoRa 连接性和可选 OLED 显示。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [M2M 1 通道 LoRaWan Gateway 盾牌 for Raspberry Pi](https://www.tindie.com/products/m2m/1-channel-lorawan-gateway-shield-for-raspberry-pi/) | ARM32 | 868/915/923MHz LoRa 连接选项。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [uputronics Raspberry Pi + LoRa (TM) 扩展板](https://store.uputronics.com/index.php?route=product/product&path=61&product_id=68) | ARM32 | 433/868/915MHz LoRa 连接选项。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [uputronics Raspberry PiZero LoRa (TM) 扩展板](https://store.uputronics.com/index.php?route=product/product&path=61&product_id=99) | ARM32 | 双 433/868/915MHz LoRa 连接选项。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |


### <a name="nordic-semiconductor-nrf24l01-wireless-pi-hats"></a>[北欧半导体 nRF24L01 无线 Pi 帽子](https://www.nordicsemi.com/Products/Low-power-short-range-wireless/nRF24-series)
全球 2.5 GHz ISM 波段、250Kbps、1Mbps 和2Mbps 数据速率。 低能耗模块10的计量范围，高能耗模块1KM。

> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Ceech Raspberry Pi nRF24l01 + 盾牌](https://www.tindie.com/products/ceech/new-raspberry-pi-to-nrf24l01-shield/) |ARM| Raspberry Pi 的 Raspberry Pi NRF24l01 + 盾牌外接程序支持单个 NRF24l01 + 模块和一个蜂鸣器和原型设计区域。| [库](https://github.com/techfooninja/Radios.RF24)， [示例应用程序](https://github.com/KiwiBryn/nRF24L01Windows10IoTCoreDuinoDemo)， [必需修改](https://blog.devmobile.co.nz/2017/07/31/nrf24-windows-10-iot-core-hardware/) | |
> | [Boros Rf2-双重 nRF24L01 pHat](https://www.tindie.com/products/boros/borosrf2-dual-nrf24l01-phathat-rtc-for-pis/) |ARM| Boros RF2 最多支持两个 NRF24L01 + 无线电和一个可选 RTC。| [库](https://github.com/techfooninja/Radios.RF24)， [示例应用程序](https://github.com/KiwiBryn/nRF24L01Windows10IoTCoreDuinoDemo) | |


### <a name="port-expanders"></a>端口扩展器
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | MCP23008 8 位 i/o 端口扩展器 | ARM32、x64、x86 | I2C Interface 芯片，GPIO 端口扩展器。 8个端口，18个 PDIP 包 | [SPI 端口 Explander 示例](https://www.hackster.io/4803/i2c-port-expander-sample-0a6d4f) | &#10004; |
> | MCP23S17 16 位 i/o 端口扩展器 | ARM32、x64、x86 | I2C Interface 芯片，GPIO 端口扩展器。 16个端口，28-SPDIP 包 | [交互式钢琴示例](https://www.hackster.io/windowsiot/build-2014-piano-3b449c) | &#10004; |

### <a name="storage-media"></a>存储媒体
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Samsung 32GB EVO Class 10 微 SDHC](https://www.amazon.com/gp/product/B00IVPU786) | AARM32、x64、x86 | 建议的 SD 卡，适用于可使 Windows 10 IoT Core 闪存的设备。 | | &#10004;|
> | [SanDisk 超高微 SDHC](https://www.amazon.com/SanDisk-Ultra-Micro-SDHC-16GB/dp/9966573445) | ARM32、x64、x86 | 建议的 SD 卡，适用于可使 Windows 10 IoT Core 闪存的设备。 | | &#10004; |

### <a name="sensors"></a>传感器
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | DHT11 基本温度-湿度传感器 | ARM32、x64、x86 | 一种基本的超低成本数字温度和湿度传感器。 它使用容量湿度传感器和 thermistor 测量周围的空气，并创建数据 pin 上的数字信号， (无需) 模拟输入插针。  | [GpioOneWireSample (DHT11) ](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire)| &#10004; |
> | DHT22 温度-湿度传感器 | ARM32、x64、x86 | 一种基本的超低成本数字温度和湿度传感器。 它使用容量湿度传感器和 thermistor 测量周围的空气，并创建数据 pin 上的数字信号， (无需) 模拟输入插针。  | [GpioOneWireSample (DHT11) ](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire) | &#10004; |
> | SparkFun 三轴加速感应-ADXL345 | ARM32、x64、x86 | 高分辨率的小型、窄、低电源、3轴 MEMS 加速感应 (13 位) 度量，最高支持± 16 g。 数字输出数据的格式为16位2补码，可通过 SPI (3 或 4-无线) 或 I2C 数字接口进行访问。 |[加速感应示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer) | &#10004; |
> | Adafruit BMP280 温度和大气传感器 | ARM32 | 温度、大气压力 Bosch 环境传感器 | |   &#10004; |
> | [Adafruit TCS34725 彩色传感器](http://www.adafruit.com/products/1334) | ARM，x32 | 带有 IR 筛选器和白色 LED 的 RGB 彩色传感器-TCS34725 | | &#10004; |
> | Rohm BH1750FVI 环境光线传感器 | ARM32 | 用于环境轻型度量的小型 I2C 传感器 | [I2C 示例](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Bosch BMP180 温度和大气传感器 | ARM，x32 | Bosch 环境传感器与 tempreature、大气压力 | [I2C 示例](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Dorji DSTH01 相对湿度传感器 | ARM32 | I2C 相对湿度传感器 | [I2C 示例](https://github.com/mickut/Win10-IoT-Sensors)| |
> | Honeywell HMC5883L 数字 3-axis/磁力仪 | ARM32 | 用于数字罗盘使用和磁场度量的小型3轴磁力仪 | [I2C 示例](https://github.com/mickut/Win10-IoT-Sensors) | |

### <a name="touchpanel-solutions"></a>触摸屏解决方案
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证 | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Keith & Koep i-平移 M7 CoverLens | ARM32 | 7.0 英寸触摸计算机，适用于使用 Qualcomm Snapdragon 410E CPU、解析800x480px、亮度 850cd/qm、USB 2.0、SD 卡、POE | [i-平移 M7 信息](https://keith-koep.com/en/products/products-hmi/i-pan-m7-coverlens-arm-touch-panel-computer-technical-data/) | &#10004; |


### <a name="miscellaneous"></a>杂项
> | 部分名称/否。 | 兼容体系结构 | 说明 | 相关链接 | Microsoft 验证 | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | 官方 Pi 显示 | ARM32 | 7 "处理触摸显示。 | [Raspberry Pi 7 "触摸屏幕](https://www.raspberrypi.org/products/raspberry-pi-touch-display/) | &#10004; |
> | 单色 1.3 "128x64 OLED 显示 |ARM，x32，x64，x86 | 1.3 "对角，高对比度 B/W OLED 显示"。 128x64 单个白色 OLED 像素，控制器芯片会打开或关闭每个像素。 | [SPI 显示示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SPIDisplay) | &#10004; |
> | SN74HC595N 移位注册 IC | ARM32、x64、x86 | IC 8 位移位寄存器 16-DIP | [轮班注册示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/ShiftRegister) | &#10004; |
> | 微芯片技术 ADC MCP3002-I/P | AARM32、x64、x86 | MCP3002 10bit 模拟到数字转换器。 |  [Potentiometer 传感器示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | 微芯片技术 ADC MCP3208-CI/P | ARM32、x64、x86 | MCP3208 12bit 模拟到数字转换器。 | [Potentiometer 传感器示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | ADS1115 | ARM，x32，x64，x86 | 超小型、低功耗、16位 ADC | [ADC 总线提供程序](https://github.com/ms-iot/BusProviders/tree/develop/ADC) | &#10004; |
> | CP2102 USB 2.0 到 TTL 模块串行转换器 | ARM32、x64、x86 | CP2102 USB 2.0 到 TTL 模块串行转换器 | [串行端口示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SerialUART) | &#10004; |
> | PCA9685 | ARM32、x64、x86 | 16通道，12位 PWM Fm + I2C 总线 LED 控制器。 | [PWM 总线提供程序](https://github.com/ms-iot/BusProviders/tree/develop/PWM) | &#10004; |


