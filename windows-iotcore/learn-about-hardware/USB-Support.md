---
title: Windows 10 IoT 核心版的 USB 支持和双重角色概述
ms.date: 10/11/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解什么是 USB 支持和双角色，以及如何为 Windows 10 IoT 核心版设备自定义此功能。
keywords: windows iot，USB 支持，双角色，USB
ms.openlocfilehash: df7a6d857e147c12c4e679f70b5c28e02e623f61
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229584"
---
# <a name="overview-of-usb-support-and-dual-role"></a>USB 支持和双重角色概述

通用串行总线 (USB) 提供一个可扩展、可热插拔的即插即用串行接口，该接口可确保外围设备（例如键盘、鼠标、游戏杆、打印机、扫描仪、存储设备、调制解调器和视频会议摄像机）的标准、低成本连接。  
当我们谈到 USB 设备时，USB 函数堆栈是指由即插即用 Manager 枚举和加载的一组驱动程序，复合 USB 设备可以在单个配置中支持多个接口。 尽管本文中所述的大部分内容都与用于 USB 2.0 的双重角色相关，但更常见的是 usb 即用或 USB OTG 或 OTG，但知道 USB 3.0 以及它与 USB 2.0 有何不同。 USB OTG 为设备定义了两个角色： OTG A-设备和 OTG B-设备，指定哪一端提供对链接的电源，哪一方最初为主机。 由于每个 OTG 控制器都支持这两个角色，因此它们通常称为 "双角色" 控制器而不是 "OTG 控制器"。 另一方面，USB 3.0 可以使设备进入主机或外围设备。 某些设备可以采用这两种角色，具体取决于在另一端上检测到的类型。 这些类型的端口称为双角色数据 (DRD) 。 连接两个此类设备时，将随机分配角色，但可以从任一端发出交换。 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a>Windows 10 IoT 核心版中的 USB 功能的体系结构

当 Windows 10 IoT 平台充当 USB 设备时，它将使用几种配置中的一种。 每个配置都有一个或多个 USB 接口。 若要在 Windows 10 IoT 上正确支持 USB OTG，需要注意几个问题。  

## <a name="components-oems-have-to-supply"></a>Oem 必须提供的组件

Oem 需要为 USB 设备端和 USB 主机端提供两端的组件。  

![OEM 供应的组件](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a>Oem 支持两侧

每个 USB 设备都具有唯一的 VID 和 PID，用于识别它。 作为 Windows 基于 IoT 的 USB 设备的制造商，OEM 需要提供这些。  Oem 可以应用于 USB 联盟，并获取其公司 VID (如果没有) ，然后选择对于该产品唯一的 PID。 当 Windows 10 IoT with USBFN 功能连接到电脑时，它将充当 myUSBFN.sys) 中设置的任何功能的 USB 设备 (，其中包含 "VID_nnn" 和 "PID_NNN"。 然后，主机将使用此 VID 和 PID 组合查找适当的驱动程序，以便 (myUSB.sys) 负载。 

![USB 函数如何结合在一起](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a>从设备端支持

_要在 FFU 中包含的用于启用 USBFN 的映像生成的功能_
* IoT 映像必须包含所需的包，即 ufx01000.sys 和 usbfnclx.sys。 它们都附带了以下程序包 `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab` 。 Oem 必须在其 XML 文件中使用正确的 "feature" 标记，其中列出了 FFU 中包含的所有功能。 例如，在 BoardTestOEMInput.xml 文件中，"功能" 部分 <Feature>IOT_USBFN_CLASS_EXTENSION</Feature>  包含以下条目 <Microsoft> 。 

_USB 角色切换驱动程序_
* 对于 USB OTG，Oem 必须为 USB 角色切换驱动程序提供正确的 ACPI 表条目 (*myOTGacpi*) ，驱动程序本身 ( * myURS.sys) 。

_USB 函数控制器驱动程序_
* 这取决于 Oem 使用的硬件。 Microsoft 为两个常见 USB OTG 芯片集提供 USB 函数控制器驱动程序-Synopsys 和 ChipIdea。
* 如果 OEM 选择使用另一个 USB OTG 芯片，则 OEM 必须提供其自己的 USB 函数控制器硬件 (*myfunctioncontroller.sys*) 。

_USB 函数类驱动程序_
* 必须至少提供一个 USB 函数类驱动程序。
* 此驱动程序实现特定的 USB 设备功能。 它确定设备将在主机端显示的内容以及它将会执行的操作。
例如，它可能显示为串行通信设备或大容量存储设备或完全自定义类型的设备 (*myUSBFN.sys*) 。

_正在配置 USB 函数设备_
* 当 IoT 平台处于 USB 设备模式时，它可以在一个或多个配置下运行。 必须添加每个使用中的配置，并指定其属性。

_Common Properties_
* IoT 平台的所有 USB 功能配置都有常见的属性。 最终，OEM 需要指定标准 USB 描述符条目，如 VID、PID、DeviceClass、DeviceProtocol、制造商字符串、序列号等。
* 在注册表中的以下位置设置这些通用属性： `HKLM\System\ControlSet001\Control\USBFN\default`

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
```
> [!IMPORTANT]
> 上述值仅用于演示目的，不能用于任何产品。 OEM 必须将这些占位符字段替换为上述每个条目中的 *实际值* 。

_按配置属性_

配置存储在注册表中的以下项下面： `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

默认情况下，FFU 中包含空的默认 USB 函数配置，如中所述： `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

这一空的默认配置会导致 iot 平台显示为未安装主机端上没有驱动程序的 Windows iot 设备。

![USBFN 的配置](../media/USB-Support/config-screenshot.png)

每个配置必须指定特定的属性，如 Interface List。 IoT 平台可以作为带有不同配置的 USB 设备运行，这些配置 h 由从 USB 设备向 USB 主机公开的 USB 接口定义。

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

目前，所选配置是在连接到 USB 热： `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_配置示例_

1. 单个配置
   1. 必须至少包含一个接口
   2. 可以是默认配置
   3. 连接到电脑时，IoT 平台将显示为该类型的 USB 设备 (例如，调制解调器或存储) 。
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`

2. 复合配置
   1. 包含具有其他参数的接口的列表
   2. 当连接到电脑时，IoT 平台将显示为复合 USB 设备，其中有多个单位 (即 MTP 设备、串行设备、自定义设备) 。
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`

在注册表中的以下项下枚举 USBFN 接口： `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

每个 USB 接口条目都必须包含一个接口描述符值和一个接口 GUID。

### <a name="supporting-from-the-host-side"></a>从宿主端支持

如果 OEM 选择实现任何标准 USB 接口 (例如 大容量存储) 在设备端，则主机 PC 可为该类型的 USB 设备使用内置 Windows 驱动程序。 如果 oem 在设备端实现任何自定义 usb 接口，则 oem 需要为该自定义 usb 功能设备开发 Windows 主机驱动程序。 
