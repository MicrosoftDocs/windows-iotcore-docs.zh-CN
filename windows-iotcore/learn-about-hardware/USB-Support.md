---
title: 有关 USB 支持和 Windows 10 IoT core 的双角色概述
author: saraclay
ms.author: saclayt
ms.date: 10/11/2017
ms.topic: article
description: 了解有关 USB 支持以及双角色新增功能以及如何进行此自定义适用于 Windows 10 IoT Core 设备。
keywords: windows iot、 USB 支持、 双重角色、 USB
ms.openlocfilehash: be1ba523975a0a39414537242ca3b14b680d9799
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510757"
---
# <a name="overview-of-usb-support-and-dual-role"></a>USB 支持和双角色概述

通用串行总线 (USB) 提供了可展开，热插拔插串行接口，可确保键盘、 鼠标、 游戏杆、 打印机、 扫描仪、 存储设备、 调制解调器和视频之类的外设的标准、 低成本的连接会议摄像机。  
当我们谈及 USB 设备时，USB 函数堆栈是指一组枚举并由插管理器中，加载驱动程序和复合的 USB 设备可以支持一种配置中的多个接口。 尽管大部分什么我们讨论有关在此文章的 USB 2.0 与双角色通常称为 USB 在外出时随时或 USB OTG 或 OTG，该技术还有助于了解有关 USB 3.0 和它区别 USB 2.0。 USB OTG 定义适用于设备的两个角色：OTG 的设备和 OTG B 设备，指定哪一侧提供链接，它最初是在主机的电源。 由于每个 OTG 控制器支持这两个角色，它们通常称为"双角色"控制器而不是"OTG 控制器"。 USB 3.0，另一方面，可以使设备成为主机或外围设备。 某些设备可能需要根据哪种类型的另一端上检测到任一角色。 这些类型的端口称为双角色数据 (DRD)。 两个此类设备连接时，会随机分配角色，但可以从任何一端命令交换。 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a>USB 函数在 Windows 10 IoT 核心版中的体系结构

当在 Windows 10 IoT 平台充当 USB 设备时，它将使用几种配置之一。 每个配置了一个或多个 USB 接口。 若要正确地在 Windows 10 IoT 上支持 USB OTG，需要注意几件事情。  

## <a name="components-oems-have-to-supply"></a>组件 Oem 必须提供

Oem 需要提供两面 – USB 设备端以及可能是 USB 主机端上的组件。  

![组件 OEM 提供，数量](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a>双方的 Oem 支持

每个 USB 设备具有唯一 VID 和 PID，以便将其标记。 OEM，为基于 Windows IoT 的 USB 设备制造商需要提供这些。  Oem 可以将应用于 USB 联盟并获取其公司 VID （如果它们尚未拥有的话），然后选择将是该产品的唯一的 PID。 USBFN 功能的 Windows 10 IoT 连接到 PC 时它将使用这些"VID_nnn"和"PID_NNN"充当 USB 设备 （用于选择作为任何功能集的 myUSBFN.sys 中）。 宿主 PC 然后使用此 VID 和 PID 组合以查找相应的驱动程序加载 (myUSB.sys)。 

![USB 函数如何组合在一起](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a>从设备端支持

_要包括在 FFU 映像生成了 USBFN 启用的功能_
* IoT 映像必须包含所需的包，即 ufx01000.sys 和 usbfnclx.sys。 这两个都具有以下包`Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`。 在其 XML 文件中，其中列出了在 FFU 中包含的所有功能，Oem 必须使用正确的"功能"标记。 例如，在 BoardTestOEMInput.xml 文件中将有以下条目<Feature>IOT_USBFN_CLASS_EXTENSION</Feature>将其纳入<Microsoft>功能部分。 

_角色切换中 USB 驱动程序_
* 有关 USB OTG，Oem 必须提供正确的 ACPI 表条目 (*myOTGacpi*) USB 角色切换驱动程序和驱动程序本身 (* myURS.sys)。

_USB 函数控制器驱动程序_
* 这取决于由 Oem 硬件。 Microsoft 提供了用于两个常用 USB OTG 芯片集-Synopsys 和 ChipIdea USB 函数控制器驱动程序。
* 如果 OEM 选择使用另一个 USB OTG 芯片组，则 OEM 必须提供其自己的 USB 函数控制器硬件 (*myfunctioncontroller.sys*)。

_USB 函数类驱动程序_
* 必须提供至少一个 USB 函数类驱动程序。
* 此驱动程序实现特定 USB 设备的功能。 它确定该设备将显示为在主机端也为 it 将执行操作。
例如，它可能显示为串行通信的设备或作为大容量存储设备或完全自定义类型设备 (*myUSBFN.sys*)。

_配置函数的 USB 设备_
* 在 USB 设备模式下的 IoT 平台时，它可以在一个或多个配置下进行操作。 必须添加在使用每个配置，并指定其属性。

_通用属性_
* 没有为所有 USB 函数配置 IoT 平台的常见属性。 最终将由最多 OEM 用来指定标准 USB 描述符条目，例如视频、 PID、 DeviceClass、 DeviceProtocol，Manufacturerer 字符串、 序列号，等等。
* 在以下位置的注册表中设置这些通用属性： `HKLM\System\ControlSet001\Control\USBFN\default`

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
> 上面的值是仅用于演示目的并不能在任何产品中使用。 OEM 必须替换这些占位符字段*实际值*上述每个条目中。

_每个配置属性_

配置存储在注册表中的以下项： `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

默认情况下，没有包含在 FFU，按照中的一个空的默认 USB 函数配置： `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

此空的默认配置会导致 Windows IoT 设备与为其在此处显示的 IoT 平台是在主机端安装任何驱动程序。

![USBFN 的配置](../media/USB-Support/config-screenshot.png)

每个配置必须指定某些属性，例如接口列表。 IoT 平台可以充当具有不同的配置，一起共享到 USB 主机公开从 USB 设备的 USB 接口定义的 USB 设备。

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

目前，所选的配置是将连接到 USB 热时实际上是一个： `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_配置示例_

1. 单个配置
   1. 必须包含至少一个接口
   2. 可以是默认配置
   3. 当连接到 PC 时，IoT 平台将显示为该类型的 USB 设备 （例如调制解调器或存储）。
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`， `InterfaceList = "MODEM\0MTP"`

2. 复合配置
   1. 包含一系列具有其他参数的接口
   2. 当连接到 PC 时，IoT 平台会作为具有多个单元中 （即 MTP 设备、 串行设备、 自定义设备） 的复合 USB 设备。
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`， `InterfaceList = "MODEM\0MTP"`

USBFN 接口枚举注册表中的以下项下：
`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

USB 接口的每个条目必须包含一个接口描述符值和接口的 GUID。

### <a name="supporting-from-the-host-side"></a>从宿主端支持

如果 OEM 选择实现任何标准的 USB 接口 （例如 大容量存储） 在设备端，然后宿主 PC 可以使用现成的 Windows 驱动程序为该类型的 USB 设备。 如果 OEM 在设备端实现任何自定义的 USB 接口，则有必要 oem 用来开发的自定义的函数 USB 设备的 Windows 主机驱动程序。 
