---
title: 硬件兼容性列表
ms.date: 08/02/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解最支持的外围设备接口Windows 10 IoT 核心版协议。
keywords: windows iot， 外围设备， 协议， 兼容性， 总线， 硬件
ms.openlocfilehash: 2ced320d7c4a944bae3f19914e4ed6d3774ab2ff
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229644"
---
# <a name="hardware-compatibility-list"></a>硬件兼容性列表

Windows 10 IoT 核心版支持各种外围设备接口和协议，包括对 I2C、UART、USB 等常见总线的支持。 此页列出了已知的受支持外围设备，并且自最新 RTM 版本起是最新的。 特定条目仅适用于预览体验成员版本，因此会进行说明。 我们鼓励你参与此列表GitHub！

> [!IMPORTANT]
> 此列表并未囊括所有方式。 此页上未列出的许多其他外围设备与 Windows 10 IoT 核心版。 如果设备未列出，但类符合设备中已支持Windows 10 IoT 核心版，则它将正常工作。


查找有关支持的硬件平台的信息？ 有关与 Windows 兼容的开发板列表，请查看[So Boards C](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards)和自定义Windows。

## <a name="usb-devices"></a>USB 设备

### <a name="wifi-adapters"></a>WiFi 适配器
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|---------------|------------------------------|
> | 官方 Raspberry Pi WiFi 适配器 | ARM32、x64、x86 | 官方 Raspberry Pi WiFi 适配器提供尽可能小尺寸的最佳 WiFi 性能。 | | &#10004;  |
> | Airlink Wireless N 150 微型 USB 适配器 | x64、x86 | Airlink 101 AWL5077 Golden 150Mbps 无线微型 USB 适配器，具有 WPA2、WPA 和 WEP 增强的无线安全性 | | &#10004;  
> | Panda PAU06 | x64、x86 |  具有高增益天线的 Panda 300Mbps 无线 N USB 适配器 | |  &#10004;  
> | TP-LINK TL_WN725N |  ARM32、x64、x86 | TP-LINK TL-WN725N 无线 N Nano USB 适配器 150 Mbps `(USB/VID_0BDA&PID_8179)` |  | &#10004;  
> | NET-DYN USB WiFi 适配器 | MBM | WiFi USB 适配器 NET-DYN | |  &#10004;  
> | Realtek 8191 USB 无线 WiFi | ARM32、x64、x86 | Realtek 8191 300Mbps 802.11n/g/b/ USB 无线 WiFi LAN 网卡适配器 | | &#10004;  
> | Realtek 8192 USB 无线 WiFi | ARM32、x64、x86 | Realtek Single-Chip IEEE 802.11b/g/n 2T2R WLAN 控制器和 USB 2.0 接口 | | &#10004; |
> | Realtek 8188EU USB 无线 WiFi | ARM32、Mx64、x86BM | Realtek RTL8188EU 无线 LAN 802.11n/g/b USB 2.0 网络适配器 | | &#10004; |
> | Realtek 8192EU USB 无线 WiFi | ARM32、x64、x86 | Realtek RTL8192EU 无线 LAN 802.11n/g/b USB 2.0 网络适配器 | | &#10004; |
> | CanaKit USB 无线 WiFi | x64、x86 | 芯片组 Ralink 5370 | | &#10004;
> | D-Link DWA-172 | ARM32 | 无线 AC600 Dual-Band High-Gain USB 适配器 | [数据表](ftp://ftp.dlink.de/dwa/dwa-172/documentation/DWA-172_ds_en_Datasheet.pdf) |

### <a name="ethernet-adapters"></a>以太网适配器
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|---------------|------------------------------|
> | ASIX AX88772 USB 2.0 快速以太网适配器 | ARM32、x64、x86 | 这是一种高性能且集成性高的 ASIC，嵌入式 28 KB SRAM 用于数据包缓冲。  | | &#10004;  |


### <a name="bluetooth-dongles"></a>蓝牙北岛
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|--------|------------------------------|
> | CSR Mini USB 蓝牙 V 4.0 适配器 | ARM32、x64、x86 | 2 类蓝牙 4.0 智能就绪适配器、低功耗、双电源 |  | &#10004;
> | OR进行 BTA-403 mini 蓝牙 4.0 USB 适配器 | ARM32、x64、x86 | 低能耗蓝牙 4.0 适配器 USB Micro Adapter Dongle |  | &#10004;
> | CSR Mini USB 蓝牙 V 4.0 适配器 | x64、x86 | 2 类蓝牙 4.0 智能就绪适配器、低功耗、双电源 |  | &#10004;|

### <a name="cameras"></a>相机
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Microsoft Lifecam 3000 USB 相机 | ARM32、x64、x86 | USB 网络摄像头 | [家庭安全摄像头Project](https://developer.microsoft.com/en-us/windows/iot/samples/webcamapp)|&#10004;|
> | Microsoft Lifecam HD-5000 | ARM32、x64、x86 | Microsoft LifeCam HD-5000 720p HD 网络摄像头 | | &#10004; |
> | Microsoft® LifeCam Studio™ | ARM32 | Microsoft® LifeCam Studio™ (模型：1425) 1080p HD 网络摄像头 | | |
> | Logitech 网络摄像头 C210 | ARM32、x64、x86 | USB 网络摄像头，1.3mp 照片 |  |&#10004; |

### <a name="audio"></a>音频
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证 |
> |----------------|-------------------|-------------|--------|------------------------------|
> | 配置 USB 外部立体声声音适配器，型号 AU-EMAC1 | ARM32、x64、x86 | 将 USB 转换为 3.5mm 音频和麦克风信号 | | &#10004;

### <a name="miscellaneous"></a>杂项
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Aeon Labs Z-Wave Z-Stick 系列 2 USB Dongle DSA02203-ZWUS | ARM32 | 系列 2 Z-Wave USB Z-Stick 控制器 |  | &#10004; |
> | [Board Electronics 7"LCD 容量触摸屏显示器](https://www.chalk-elec.com/?page_id=1280#!/7-black-frame-universal-HDMI-LCD-with-capacitive-multi-touch/p/21750201/category=3094861) | ARM32 | | [正在更新固件](https://www.chalk-elec.com/?p=1826) | &#10004; |
> | Vodafone (）) K5150 | ARM32、x64、x86 | Vodafone (（) K5150 150Mbps 4G ISP FDD USB 移动宽带调制解调器） |  | &#10004;  |
> | Vodafone (）) K5160 | ARM32、x64、x86 | Vodafone () K5160 150Mbps GSM/EDGE/3G/HSPA+/GSM-CAT4 USB 移动宽带调制解调器 |  | |
> | Sierra Wireless Beam (AirCard 340U)  | x64、x86 |    Sierra Wireless Beam (AirCard 340U) 4G USB USB 移动宽带调制解调器 |  |&#10004; |
> | Microsoft Xbox 360 控制器 | ARM32 | 适用于 Microsoft 合作伙伴的符合 HID 的 USB 游戏Xbox 360 | [机器人工具包](https://microsoft.hackster.io/en-US/windowsiot/robot-kit-6dd474) |  &#10004; |
> | [MyTeletouch](http://www.myteletouch.com/) | ARM、x32 | 符合 HID 的 USB 无线鼠标、键盘和游戏板 |  | &#10004; |

## <a name="other-hardware-peripherals"></a>其他硬件外围设备

### <a name="nfcrfidproximity"></a>NFC/NFC/NFC/邻近感应
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证 |
> |----------------|-------------------|-------------|--------|------------------------------|
> | NXP OM5577 演示板 | ARM32 | NXP PN7120 NFC 芯片的演示板。 | [ProximityDevice 文档](https://docs.microsoft.com/uwp/api/Windows.Networking.Proximity.ProximityDevice) | &#10004; |
> | NXP PN547/PN548/PN7120 | ARM32、x64、x86 | 支持的 NXP NFC 芯片。 | | &#10004; |

### <a name="pi-hats"></a>Pi Hats
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit 16 通道 PWM](https://www.adafruit.com/product/2327#description-anchor) | ARM32 | 添加了控制最多 16 个浆果的功能，无需额外的 Raspberry Pi 处理开销。 能够以 12 位精度执行高达 1.6KHz 的 PWM。 | [Adafruit 教程 C# IoT 示例](https://github.com/golaat/Adafruit.Pwm) | |
> | [Dexter Industries GrovePi](https://www.dexterindustries.com/shop/grovepi-board/) | ARM32 | 可以连接数百个不同的传感器，而无需进行安装，因此可以编程它们，以监视、控制和自动执行你生命中的设备。 | [GrovePi 示例](https://github.com/DexterInd/GrovePi/) | |
> | Dexter Industries GoPiGo | ARM、x32 | GoPiGo 是 Raspberry Pi 的一款智能且完整的机器人，它使 Pi 成为完全可操作机器人。 GoPiGo 是 Dexter 行业开发的 Raspberry Pi 的移动机器人平台。 | [GoPiGo 示例](https://github.com/DexterInd/GoPiGo/tree/master/Software/CSharp) | |
> | [SeeedStudio Grove Base Hat for Raspberry PI](https://www.seeedstudio.com/Grove-Base-Hat-for-Raspberry-Pi.html) |ARM| Grove Base Hat for RPI 为 Raspbery PI 平台上的 Seeedstudio Grove System 提供支持。| [库和示例](https://github.com/KiwiBryn/GroveBaseHatWindows10IoTCore) | |
> | [SeeedStudio Grove Base Hat for Raspberry PI Zero](https://www.seeedstudio.com/Grove-Base-Hat-for-Raspberry-Pi-Zero-p-3187.html) |ARM| Grove Base Hat for RPI Zero 为 Raspbery PI 平台上的 Seeedstudio Grove System 提供支持。| [库和示例](https://github.com/KiwiBryn/GroveBaseHatWindows10IoTCore) | |

### <a name="semtech-sx127x-based-lora-pi-hats"></a>[基于 Semtech SX127X 的 LoRa® Pi Hats](https://www.semtech.com/products/wireless-rf/lora-transceivers)
Semtech 的 LoRa®超长范围 (100M 到 10KM) 分布范围通信技术具有高干扰性，并提供低成本解决方案，用于将电池/太阳能设备连接到传统网络基础结构。

> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit LoRa Radio 单选机 433MHz](https://www.adafruit.com/product/4075) | ARM32 | 433MHz LoRa 连接、3 个按钮和 OLED 显示器。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Adafruit LoRa Radio 为 868/915MHz](https://www.adafruit.com/product/4074) | ARM32 | 868/915MHz LoRa 连接、3 个按钮和 OLED 显示器。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Dragino LoRa GPS Hat for RaspberryPI 433/868/915MHz](http://www.dragino.com/products/lora/item/106-lora-gps-hat.html) | ARM32 | 433/868/915MHz LoRa 连接选项和 GPS。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [适用于 RPI 915MHz 的 Elecrow LoRa RFM95 IoT 板](https://www.elecrow.com/lora-rfm95-iot-board-for-rpi.html) | ARM32 | 915MHz LoRa 连接和 Grove 套接字。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Raspberry Pi Zero 和 PI3 电子技巧 Lora/LoraWan 防护](https://www.tindie.com/products/electronictrik/loralorawan-shield-for-raspberry-pi-zero-and-pi3/) | ARM32 | 868/915MHz LoRa 连接和可选的 OLED 显示。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [适用于 Raspberry Pi 的 M2M 1 通道 LoRaWan 网关防护](https://www.tindie.com/products/m2m/1-channel-lorawan-gateway-shield-for-raspberry-pi/) | ARM32 | 868/915/923MHz LoRa 连接选项。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [uputronics Raspberry Pi+ LoRa (TM) 扩展板](https://store.uputronics.com/index.php?route=product/product&path=61&product_id=68) | ARM32 | 433/868/915MHz LoRa 连接选项。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [uputronics Raspberry PiZero LoRa (TM) 扩展板](https://store.uputronics.com/index.php?route=product/product&path=61&product_id=99) | ARM32 | 双 433/868/915MHz LoRa 连接选项。 | [库和示例](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |


### <a name="nordic-semiconductor-nrf24l01-wireless-pi-hats"></a>[中国国家/地区 nRF24L01 无线 Pi Hats](https://www.nordicsemi.com/Products/Low-power-short-range-wireless/nRF24-series)
全球 2.5GHz ISM 带区、250Kbps、1Mbps 和 2Mbps 数据速率。 低功率模块 10 米范围，高功率模块最多 1KM。

> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Ceech Raspberry Pi nRF24l01+ Shield](https://www.tindie.com/products/ceech/new-raspberry-pi-to-nrf24l01-shield/) |ARM| Raspberry Pi 的 Raspberry Pi NRF24l01+ Shield 加载项支持单个 NRF24l01+ 模块以及一个磁头和原型制作区域。| [库](https://github.com/techfooninja/Radios.RF24)， [示例应用程序](https://github.com/KiwiBryn/nRF24L01Windows10IoTCoreDuinoDemo)， [需要修改](https://blog.devmobile.co.nz/2017/07/31/nrf24-windows-10-iot-core-hardware/) | |
> | [管理Rf2-Dual nRF24L01 pHat](https://www.tindie.com/products/boros/borosrf2-dual-nrf24l01-phathat-rtc-for-pis/) |ARM| 管理器 RF2 最多支持两个 NRF24L01+ 无线电和可选的 RTC。| [库](https://github.com/techfooninja/Radios.RF24)， [示例应用程序](https://github.com/KiwiBryn/nRF24L01Windows10IoTCoreDuinoDemo) | |


### <a name="port-expanders"></a>端口扩展器
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|--------|------------------------------|
> | MCP23008 8 位 I/O 端口扩展器 | ARM32、x64、x86 | I2C 接口芯片，GPIO 端口扩展器。 8 个端口，18-PDIP 包 | [SPI 端口 Explander 示例](https://www.hackster.io/4803/i2c-port-expander-sample-0a6d4f) | &#10004; |
> | MCP23S17 16 位 I/O 端口扩展器 | ARM32、x64、x86 | I2C 接口芯片，GPIO 端口扩展器。 16 个端口，28-SPDIP 包 | [Interactive Interactive Interactive Sample](https://www.hackster.io/windowsiot/build-2014-piano-3b449c) | &#10004; |

### <a name="storage-media"></a>存储媒体
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Samsung 32GB EVO 类 10 Micro SDHC](https://www.amazon.com/gp/product/B00IVPU786) | AARM32、x64、x86 | 对于可以刷用闪存的设备，建议Windows 10 IoT 核心版 SD 卡。 | | &#10004;|
> | [SanDisk Ultra Micro SDHC 16GB](https://www.amazon.com/SanDisk-Ultra-Micro-SDHC-16GB/dp/9966573445) | ARM32、x64、x86 | 对于可以刷用闪存的设备，建议Windows 10 IoT 核心版 SD 卡。 | | &#10004; |

### <a name="sensors"></a>传感器
> | 部件名称/否。 | 兼容的体系结构 | 说明 | 相关链接 | Microsoft 验证  |
> |----------------|-------------------|-------------|--------|------------------------------|
> | DHT11 基本温度湿度传感器 | ARM32、x64、x86 | 一个基本的超低成本数字温度和湿度传感器。 它使用容量湿度传感器和热度器测量周围的空气，并发出数据引脚上的数字信号 (不需要模拟输入) 。  | [GpioOneWireSample (DHT11) ](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire)| &#10004; |
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
