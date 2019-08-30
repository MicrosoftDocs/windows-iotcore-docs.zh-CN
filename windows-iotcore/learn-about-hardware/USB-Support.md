---
title: 适用于 Windows 10 IoT Core 的 USB 支持和双重角色概述
author: saraclay
ms.author: saclayt
ms.date: 10/11/2017
ms.topic: article
description: 了解什么是 USB 支持和双角色, 以及如何为 Windows 10 IoT Core 设备自定义此功能。
keywords: windows iot, USB 支持, 双角色, USB
ms.openlocfilehash: be1ba523975a0a39414537242ca3b14b680d9799
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167596"
---
# <a name="overview-of-usb-support-and-dual-role"></a>USB 支持和双重角色概述

通用串行总线 (USB) 提供可扩展的热插拔即插即用串行接口, 可确保外围设备 (例如键盘、鼠标、游戏杆、打印机、扫描仪、存储设备、调制解调器和视频) 的标准低成本连接。会议摄像机。  
当我们谈到 USB 设备时, USB 函数堆栈是指由即插即用 Manager 枚举和加载的一组驱动程序, 复合 USB 设备可以在单个配置中支持多个接口。 尽管本文中所述的大部分内容都与用于 USB 2.0 的双重角色相关, 但更常见的是 usb 即用或 USB OTG 或 OTG, 但知道 USB 3.0 以及它与 USB 2.0 有何不同。 USB OTG 为设备定义了两个角色:OTG A-设备和 OTG B-设备, 指定哪一端提供链接电源, 后者最初为主机。 由于每个 OTG 控制器都支持这两个角色, 因此它们通常称为 "双角色" 控制器而不是 "OTG 控制器"。 另一方面, USB 3.0 可以使设备进入主机或外围设备。 某些设备可以采用这两种角色, 具体取决于在另一端上检测到的类型。 这类端口称为 "双角色数据" (DRD)。 连接两个此类设备时, 将随机分配角色, 但可以从任一端发出交换。 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a>Windows 10 IoT Core 中的 USB 功能的体系结构

当 Windows 10 IoT 平台充当 USB 设备时, 它将使用几种配置中的一种。 每个配置都有一个或多个 USB 接口。 若要在 Windows 10 IoT 上正确支持 USB OTG, 需要注意以下几件事。  

## <a name="components-oems-have-to-supply"></a>Oem 必须提供的组件

Oem 需要为 USB 设备端和 USB 主机端提供两端的组件。  

![OEM 供应的组件](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a>Oem 支持两侧

每个 USB 设备都具有唯一的 VID 和 PID, 用于识别它。 作为基于 Windows IoT 的 USB 设备的制造商, OEM 需要提供这些。  Oem 可应用于 USB 联盟, 并获取其公司 VID (如果尚未安装), 然后选择对该产品唯一的 PID。 当带有 USBFN 功能的 Windows 10 IoT 连接到电脑时, 它将充当 USB 设备 (在 myUSBFN 中选择的任何功能), 其中包含 "VID_nnn" 和 "PID_NNN"。 宿主 PC 将使用此 VID 和 PID 组合查找适当的驱动程序以进行加载 (myUSB)。 

![USB 函数如何结合在一起](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a>从设备端支持

_要在 FFU 中包含的用于启用 USBFN 的映像生成的功能_
* IoT 映像必须包含其中所需的包, 即 ufx01000 和 usbfnclx。 它们都附带了以下程序包`Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`。 Oem 必须在其 XML 文件中使用正确的 "feature" 标记, 其中列出了 FFU 中包含的所有功能。 例如, 在 BoardTestOEMInput 文件中, " <Microsoft>功能" 部分中将包含以下项<Feature>IOT_USBFN_CLASS_EXTENSION</Feature> 。 

_USB 角色切换驱动程序_
* 对于 USB OTG, Oem 必须为 USB 角色切换驱动程序和驱动程序本身 (* myURS) 提供正确的 ACPI 表条目 (*myOTGacpi*)。

_USB 函数控制器驱动程序_
* 这取决于 Oem 使用的硬件。 Microsoft 为两个常见 USB OTG 芯片集提供 USB 函数控制器驱动程序-Synopsys 和 ChipIdea。
* 如果 OEM 选择使用另一个 USB OTG 芯片, 则 OEM 必须提供其自己的 USB 函数控制器硬件 (*myfunctioncontroller*)。

_USB 函数类驱动程序_
* 必须至少提供一个 USB 函数类驱动程序。
* 此驱动程序实现特定的 USB 设备功能。 它确定设备将在主机端显示的内容以及它将会执行的操作。
例如, 它可能显示为串行通信设备或大容量存储设备或完全自定义类型的设备 (*myUSBFN*)。

_正在配置 USB 函数设备_
* 当 IoT 平台处于 USB 设备模式时, 它可以在一个或多个配置下运行。 必须添加每个使用中的配置, 并指定其属性。

_通用属性_
* IoT 平台的所有 USB 功能配置都有常见的属性。 最终, OEM 需要指定标准 USB 描述符条目, 例如 VID、PID、DeviceClass、DeviceProtocol、Manufacturerer 字符串、序列号等。
* 在注册表中的以下位置设置这些通用属性:`HKLM\System\ControlSet001\Control\USBFN\default`

```
BcdDevice=0x1 
bDeviceClass=0x0 
bDeviceProtocol=0x0 
bDeviceSubClass= 0x0 
idProduct= 0xc0c0 
idVendor=0x045e 
iManufacturer=1 
iSerialNumber=3 
ManufacturerString=OEMname 
ProductString="Windows IOT" 
SerialNumberString=0x123 
```
> [!IMPORTANT]
> 上述值仅用于演示目的, 不能用于任何产品。 OEM 必须将这些占位符字段替换为上述每个条目中的*实际值*。

_按配置属性_

配置存储在注册表中的以下项下面:`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

默认情况下, FFU 中包含空的默认 USB 函数配置, 如中所述:`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

此空的默认配置会导致 IoT 平台显示为在其上未安装主机端驱动程序的 Windows IoT 设备。

![USBFN 的配置](../media/USB-Support/config-screenshot.png)

每个配置必须指定特定的属性, 如 Interface List。 IoT 平台可以作为带有不同配置的 USB 设备运行, 这些配置 h 由从 USB 设备向 USB 主机公开的 USB 接口定义。

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

目前, 所选配置是在连接到 USB 热:`HKLM\SYSTEM\ControlSet001\Control\USBFN`

_配置示例_

1. 单个配置
   1. 必须至少包含一个接口
   2. 可以是默认配置
   3. 连接到电脑时, IoT 平台将显示为该类型的 USB 设备 (例如调制解调器或存储)。
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`， `InterfaceList = "MODEM\0MTP"`

2. 复合配置
   1. 包含具有其他参数的接口的列表
   2. 当连接到电脑时, IoT 平台将显示为复合 USB 设备, 其中包含多个单位 (即 MTP 设备、串行设备、自定义设备)。
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`， `InterfaceList = "MODEM\0MTP"`

在注册表中的以下项下枚举 USBFN 接口:`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

每个 USB 接口条目都必须包含一个接口描述符值和一个接口 GUID。

### <a name="supporting-from-the-host-side"></a>从宿主端支持

如果 OEM 选择实现任何标准 USB 接口 (例如 大容量存储), 则主机 PC 可以为该类型的 USB 设备使用内置的 Windows 驱动程序。 如果 OEM 在设备端实现任何自定义 USB 接口, 则 OEM 需要为该自定义 USB 功能设备开发 Windows 主机驱动程序。 
