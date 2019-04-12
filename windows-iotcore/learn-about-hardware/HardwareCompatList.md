---
title: 硬件兼容性列表
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解有关外围接口和 Windows 10 IoT Core 最佳支持的协议。
keywords: windows iot、 外围设备、 协议、 兼容性、 总线、 硬件
ms.openlocfilehash: 819414db94d01e826fbcf721c911fff9d02f6c94
ms.sourcegitcommit: b79c2b74968e552bee664ecc886725754d183657
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512103"
---
# <a name="hardware-compatibility-list"></a>硬件兼容性列表

Windows 10 IoT 核心版支持各种外设接口和协议，包括对诸如 I2C、UART、USB 等常见总线的支持。 本页面列出已知受支持的外设，并且是目前最新的 RTM 版本。 特定条目可能仅适用于预览版，并将这些条目作出说明。 我们鼓励您参与到 GitHub 上的此列表 ！

> [!IMPORTANT]
> 此列表并不详尽。 此页面上并未列出许多与 Windows 10 IoT 核心版兼容的其他外设。 如果看不到列出，但类符合与已在 Windows 10 IoT Core 支持的设备，那么它将起作用。 


是否在查找有关受支持的硬件平台的信息？ 单击[此处](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards)有关与 Windows 兼容的开发板的列表。

## <a name="usb-devices"></a>USB 设备

### <a name="wifi-adapters"></a>WiFi 适配器
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | 官方 Raspberry Pi WLAN 硬件保护装置 | ARM32，x64、 x86 | 官方 Raspberry Pi WiFi 硬件保护装置提供其随之而来的大小的最佳可能 WiFi 性能。 | | &#10004;  |
> | Airlink 无线 N 150 微型 USB 适配器 | x64、 x86 | Airlink 101 黄金 AWL5077 150 mbps 无线迷你 USB 适配器 WPA2、 WPA，与 WEP 增强的无线安全 | | &#10004;  
> | Panda PAU06 | x64、 x86 |  附带高增益天线的 Panda 300Mbps 无线 N USB 适配器 | |  &#10004;  
> | TP-LINK TL_WN725N |  ARM32，x64、 x86 | TP 链接 TL WN725N 无线 N Nano USB 适配器 150 Mbps `(USB/VID_0BDA&PID_8179)` |  | &#10004;  
> | NET DYN USB WiFi 适配器 | MBM | WiFi USB 适配器 NET DYN | |  &#10004;  
> | Realtek 8191 USB 无线 WiFi | ARM32，x64、 x86 | Realtek 8191 300 mbps 802.11n/g/b/ USB 无线 WiFi LAN 网络卡适配器 | | &#10004;  
> | Realtek 8192 USB 无线 WiFi | ARM32，x64、 x86 | 附带 USB 2.0 接口的 Realtek 单芯片 IEEE 802.11b/g/n 2T2R WLAN 控制器 | | &#10004; |
> | Realtek 8188EU USB 无线 WiFi | ARM32，Mx64，x86BM | Realtek RTL8188EU 无线 LAN 802.11n/g/b USB 2.0 网络适配器 | | &#10004; |
> | Realtek 8192EU USB 无线 WiFi | ARM32，x64、 x86 | Realtek RTL8192EU 无线 LAN 802.11n/g/b USB 2.0 网络适配器 | | &#10004; |
> | CanaKit USB 无线 WiFi | x64、 x86 | Chipset Ralink 5370 | | &#10004;
> | D-Link DWA-172 | ARM32 | 无线 AC600 双外高增益 USB 适配器 | [数据表](ftp://ftp.dlink.de/dwa/dwa-172/documentation/DWA-172_ds_en_Datasheet.pdf) |

### <a name="ethernet-adapters"></a>以太网适配器
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | ASIX AX88772 USB 2.0 快速以太网适配器 | ARM32，x64、 x86 | 这是高性能和高数据包缓冲与嵌入 28 KB SRAM 集成 ASIC。  | | &#10004;  |


### <a name="bluetooth-dongles"></a>蓝牙连接器
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | CSR 微型 USB 蓝牙 V 4.0 适配器 | ARM32，x64、 x86 | 2 级蓝牙 4.0 智能准备适配器、低功耗、双电源 |  | &#10004; 
> | ORICO BTA-403 微型蓝牙 4.0 USB 硬件保护装置 | ARM32，x64、 x86 | 低耗电蓝牙 4.0 适配器 USB 微适配器硬件保护装置 |  | &#10004; 
> | CSR 微型 USB 蓝牙 V 4.0 适配器 | x64、 x86 | 2 级蓝牙 4.0 智能准备适配器、低功耗、双电源 |  | &#10004;|

### <a name="cameras"></a>相机
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Microsoft Lifecam 3000 USB 相机 | ARM32，x64、 x86 | USB 网络摄像头 | [家庭安全照相机项目](https://developer.microsoft.com/en-us/windows/iot/samples/webcamapp)|&#10004;|
> | Microsoft Lifecam HD-5000 | ARM32，x64、 x86 | Microsoft LifeCam HD-5000 720p 高清网络摄像头 | | &#10004; |
> | Microsoft® LifeCam Studio™ | ARM32 | Microsoft® LifeCam Studio™（型号：1425）1080p 高清网络摄像头 | | |
> | Logitech 网络摄像头 C210 | ARM32，x64、 x86 | USB 网络摄像头，1.3mp 照片 |  |&#10004; |

### <a name="audio"></a>Audio
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证 |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Sabrent USB 外部立体声音响适配器，型号 AU-EMAC1 | ARM32，x64、 x86 | 将 USB 转换为 3.5mm 音频和麦克风信号 | | &#10004; 

### <a name="miscellaneous"></a>其他
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Aeon Labs Z-Wave Z-Stick 系列 2 USB 硬件保护装置 DSA02203-ZWUS | ARM32 | 系列 2 Z-Wave USB Z-Stick 控制器 |  | &#10004; |
> | [黑板上电子设备 7"LCD 电容式触摸屏显示](https://www.chalk-elec.com/?page_id=1280#!/7-black-frame-universal-HDMI-LCD-with-capacitive-multi-touch/p/21750201/category=3094861) | ARM32 | | [更新固件](https://www.chalk-elec.com/?p=1826) | &#10004; |
> | Vodafone (Huawei) K5150 | ARM32，x64、 x86 | Vodafone (Huawei) K5150 150Mbps 4G LTE FDD USB 移动宽带调制解调器 |  | &#10004;  |
> | Vodafone （华为） K5160 | ARM32，x64、 x86 | Vodafone （华为） K5160 150 mbps GSM/边缘/3g/HSPA + LTE CAT4 USB 移动宽带调制解调器 |  | |
> | Sierra 无线波束 (AirCard 340U) | x64、 x86 |    Sierra 无线波束 (AirCard 340U) 4G LTE USB 移动宽带调制解调器 |  |&#10004; |
> | Microsoft Xbox 360 控制器 | ARM32 | Microsoft Xbox 360 的符合 HID 标准的 USB 游戏板 | [机器人工具包](https://microsoft.hackster.io/en-US/windowsiot/robot-kit-6dd474) |  &#10004; |
> | [MyTeletouch](http://www.myteletouch.com/) | ARM x32 | 符合 HID 标准的 USB 无线鼠标、键盘和游戏板 |  | &#10004; |

## <a name="other-hardware-peripherals"></a>其他外围硬件设备

### <a name="storage-media"></a>存储媒体
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Samsung 32GB EVO Class 10 Micro SDHC](https://www.amazon.com/gp/product/B00IVPU786) | AARM32，x64、 x86 | 设备可以有 Windows 10 IoT 核心版已刷新建议的 SD 卡。 | | &#10004;|
> | [SanDisk Ultra Micro SDHC 16GB](https://www.amazon.com/SanDisk-Ultra-Micro-SDHC-16GB/dp/9966573445) | ARM32，x64、 x86 | 设备可以有 Windows 10 IoT 核心版已刷新建议的 SD 卡。 | | &#10004; |

### <a name="pi-hats"></a>Pi 尖角符号
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit 16-Channel PWM](https://www.adafruit.com/product/2327#description-anchor) | ARM32 | 在不增加其他 Raspberry Pi 处理开销的情况下，添加可以控制最多 16 个伺服的功能。 能够执行最多 1.6KHz 的 PWM，且精度达到 12 位。 | [Adafruit 教程C#IoT 示例](https://github.com/golaat/Adafruit.Pwm) | |
> | [Dexter 行业 GrovePi](https://www.dexterindustries.com/shop/grovepi-board/) | ARM32 | 可以连接数百个不同的传感器，而焊接，因此可以将其用于监视，编程控制，并在您的生活中实现自动化的设备。 | [GrovePi 示例](https://github.com/DexterInd/GrovePi/) | |
> | Dexter 行业 GoPiGo | ARM x32 | GoPiGo 是针对 Raspberry Pi 将 Pi 变成完全正常运行机器人很不一般吧和完整的机器人。 GoPiGo 是用于开发的 Dexter 行业在 Raspberry Pi 的移动机器人平台。 | [GoPiGo 示例](https://github.com/DexterInd/GoPiGo/tree/master/Software/CSharp) | |

### <a name="sensors"></a>传感器
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | DHT11 基本温度-湿度传感器 | ARM32，x64、 x86 | 超低成本的基本数字温度和湿度传感器。 它使用容量湿度传感器和热敏电阻来测量周围空气，并在数据引脚上显示数字信号（无需模拟输入引脚）。  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire)| &#10004; |
> | DHT22 温度-湿度传感器 | ARM32，x64、 x86 | 超低成本的基本数字温度和湿度传感器。 它使用容量湿度传感器和热敏电阻来测量周围空气，并在数据引脚上显示数字信号（无需模拟输入引脚）。  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire) | &#10004; |
> | SparkFun 三轴加速计突围 - ADXL345 | ARM32，x64、 x86 | 小型，精简，低电源、 3 轴 MEMS 加速感应器使用 ±16 g 最高分辨率 （13 位） 上的度量值。 数字输出数据的格式设置为 16 位的二进制补码，并可通过 SPI（3 线或 4 线）或 I2C 数字接口访问。 |[加速计示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer) | &#10004; |
> | Adafruit BMP280 温度和气压传感器 | ARM32 | 测量温度、气压的 Bosch 环境传感器 | |   &#10004; |
> | [Adafruit TCS34725 色彩传感器](http://www.adafruit.com/products/1334) | ARM x32 | 使用红外线 （ir） 筛选器和白色 LED-TCS34725 RGB 颜色传感器 | | &#10004; |
> | Rohm BH1750FVI 环境光线传感器 | ARM32 | 小 I2C 传感器环境光线度量 | [I2C 示例](https://github.com/mickut/Win10-IoT-Sensors) | |
> | 博世 BMP180 温度和大气传感器 | ARM x32 | 博世环境传感器与 tempreature，大气压力 | [I2C 示例](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Dorji DSTH01 相对湿度传感器 | ARM32 | I2C 相对湿度传感器 | [I2C 示例](https://github.com/mickut/Win10-IoT-Sensors)| |
> | Honeywell HMC5883L 数字 3 轴指南针/磁力仪 | ARM32 | 小型数字指南针使用和磁场度量值的 3 轴磁力仪 | [I2C 示例](https://github.com/mickut/Win10-IoT-Sensors) | |


### <a name="port-expanders"></a>端口扩展器
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | MCP23008 8 位 I/O 端口扩展器 | ARM32，x64、 x86 | I2C 接口芯片，GPIO 端口扩展器。 8 个端口，18 PDIP 程序包 | [SPI 端口 Explander 示例](https://www.hackster.io/4803/i2c-port-expander-sample-0a6d4f) | &#10004; |
> | MCP23S17 16 位 I/O 端口扩展器 | ARM32，x64、 x86 | I2C 接口芯片，GPIO 端口扩展器。 16 个端口，28 SPDIP 的程序包 | [交互式钢琴示例](https://www.hackster.io/windowsiot/build-2014-piano-3b449c) | &#10004; |

### <a name="nfcrfidproximity"></a>NFC/RFID/Proximity
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证 |
> |----------------|-------------------|-------------|--------|------------------------------|
> | NXP OM5577 演示板 | ARM32 | NXP PN7120 NFC 芯片的演示板。 | [ProximityDevice 文档](https://docs.microsoft.com/uwp/api/Windows.Networking.Proximity.ProximityDevice) | &#10004; |
> | NXP PN547/PN548/PN7120 | ARM32，x64、 x86 | 支持 NXP NFC 芯片。 | | &#10004; |

### <a name="miscellaneous"></a>其他
> | 部件名称/编号 | 兼容的体系结构 | 描述 | 相关链接 | Microsoft 验证 | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | 官方 Pi 显示 | ARM32 | 7"800x480 触摸显示。 | [在 raspberry Pi 7"触摸屏](https://www.raspberrypi.org/products/raspberry-pi-touch-display/) | &#10004; |
> | 单色 1.3"128x64 OLED 图形显示 |ARM，x 32、 x64、 x86 | 1.3"斜向的高对比度黑白 OLED 显示。 128x64 单个白色 OLED 像素，每个 OLED 均由控制器芯片打开或关闭。 | [SPI 屏幕示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SPIDisplay) | &#10004; |
> | SN74HC595N 移位寄存器 IC | ARM32，x64、 x86 | IC 8 位移位寄存器 16 DIP | [移位寄存器示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/ShiftRegister) | &#10004; |
> | 微芯片技术 ADC MCP3002-I/P | AARM32，x64、 x86 | MCP3002 10 位模拟到数字转换器。 |  [电位计传感器示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | 微芯片技术 ADC MCP3208-CI/P | ARM32，x64、 x86 | MCP3208 12 位模拟到数字转换器。 | [电位计传感器示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | ADS1115 | ARM，x 32、 x64、 x86 | 极小型、 低功耗、 16 位 ADC | [ADC 总线提供程序](https://github.com/ms-iot/BusProviders/tree/develop/ADC) | &#10004; |
> | TTL 模块串行转换器的 CP2102 USB 2.0 | ARM32，x64、 x86 | TTL 模块串行转换器的 CP2102 USB 2.0 | [串行端口示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SerialUART) | &#10004; |
> | PCA9685 | ARM32，x64、 x86 | 16 通道、 12 位 PWM Fm + I2C 总线 LED 控制器。 | [PWM 总线提供程序](https://github.com/ms-iot/BusProviders/tree/develop/PWM) | &#10004; |


