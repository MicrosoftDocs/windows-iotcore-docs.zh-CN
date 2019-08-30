---
title: 蓝牙支持
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何利用适用于运行 Windows 10 IoT Core 的设备的蓝牙。
keywords: windows iot, 蓝牙, 蓝牙支持, 设备, 设备门户
ms.openlocfilehash: f24b50b65b192ed6bd9309eeda30dbadfedf5bc2
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168958"
---
# <a name="bluetooth-support"></a>蓝牙支持
Windows 10 IoT Core 支持蓝牙4.0。 可以在[硬件兼容性列表](../learn-about-hardware/HardwareCompatList.md)中找到受支持的蓝牙连接器列表。

## <a name="about-bluetooth"></a>关于蓝牙
你可以选择两种不同的蓝牙技术来在应用程序中实现:

* 经典蓝牙 (RFCOMM) 在蓝牙 LE 之前, 设备通常使用此协议通过蓝牙进行通信。 此协议十分简单，可用于设备到设备的通信而无需节能。 连接要求配对。

* 蓝牙低能耗 (BLE/LE) 蓝牙低能耗 (LE) 是一个规范, 用于定义在具有有效能源使用要求的设备之间的发现和通信协议。 如需更多详细信息 (包括代码示例), 则设备无需配对即可连接到 BLE 设备。

## <a name="supported-bluetooth-profiles"></a>受支持的蓝牙配置文件
Windows 10 IoT Core 支持以下蓝牙配置文件:

1.  **人体学接口设备配置文件概念 (HID)** HID 设备从用户那里获取输入, 并为人类 consumpation 提供输出。 例如键盘、鼠标、游戏控制器、条形码读取器、LED 和字母数字显示。 Windows 10 IoT Core 设备可以通过蓝牙连接到 HID 设备。 请参阅 Windows 上下文中有关 HID 的一般主题:[HID 概念简介](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts)。 

2.  **射频通信 (RFCOMM)** RFCOMMM 是经典蓝牙的基础串行通信。 对于 UWP 应用, 支持以下 RFCOMM 服务:

* serialPort
* obexObjectPush
* obexFileTransfer
* phoneBookAccessPce
* phoneBookAccessPse
* genericFileTransfer

3. **泛型属性配置文件 (GATT)** 请参阅[UWP-蓝牙低能耗](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview)主题。 

> [!NOTE]
> 你将需要在 AppManifest 中手动指定 RFCOMM 服务。  请参阅[UWP-蓝牙 RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm)主题。 另请参阅[UWP-蓝牙 Rfcomm Chat 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat)主题。

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a>使用设备门户连接蓝牙设备
使用[windows 10 IoT Core 版本映像](https://developer.microsoft.com/en-us/windows/iot/downloads)时, 可以使用设备门户将蓝牙设备与 Windows IoT core 设备配对。 导航到 "蓝牙" 选项卡时, 设备将查找蓝牙设备, 还会被其他蓝牙设备发现。 下图显示了传入配对请求。 

![蓝牙传入配对](../media/Bluetooth/Portal_BT_2.png)

成功配对设备后, 它将在 "配对设备" 部分下列出 

![蓝牙传入配对](../media/Bluetooth/Portal_BT_3.png)
