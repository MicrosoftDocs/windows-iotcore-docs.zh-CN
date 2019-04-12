---
title: 蓝牙支持
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何利用运行 Windows 10 IoT 核心版的设备的蓝牙。
keywords: windows iot、 蓝牙、 蓝牙的支持、 设备、 设备门户
ms.openlocfilehash: f24b50b65b192ed6bd9309eeda30dbadfedf5bc2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510858"
---
# <a name="bluetooth-support"></a>蓝牙支持
Windows 10 IoT Core 支持蓝牙 4.0。 可以在找到的受支持蓝牙连接器列表[硬件兼容性列表](../learn-about-hardware/HardwareCompatList.md)。

## <a name="about-bluetooth"></a>有关 Bluetooth
有两个不同的蓝牙技术，您可以选择在应用中实现：

* 经典蓝牙 (RFCOMM) 之前蓝牙 LE、 设备通常用于此协议使用蓝牙进行通信。 此协议十分简单，可用于设备到设备的通信而无需节能。 连接需要配对。

* 低耗电 Bluetooth (BLE/LE) 蓝牙低能耗 (LE) 是一种规范，用于定义用于发现和具有有效的能源使用情况要求的设备之间的通信协议。 有关详细信息包括根据最新生成的代码示例，可以连接到 BLE 设备而无需配对设备。

## <a name="supported-bluetooth-profiles"></a>受支持的蓝牙配置文件
Windows 10 IoT Core 支持以下蓝牙配置文件：

1.  **人体学接口设备配置文件的概念 (HID)** HID 设备将用户输入，并提供人工 consumpation 的输出。 示例包括键盘、 鼠标、 游戏控制器、 条形码读取器、 LED 和字母数字显示。 Windows 10 IoT Core 设备可以连接到 HID 设备通过蓝牙。 请参阅有关 HID Windows 上下文中的常规主题：[HID 概念简介](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts)。 

2.  **射频通信 (RFCOMM)** RFCOMMM 是经典蓝牙的基础串行通信。 与 UWP 应用，支持以下 RFCOMM 服务：

* serialPort
* obexObjectPush
* obexFileTransfer
* phoneBookAccessPce
* phoneBookAccessPse
* genericFileTransfer

3. **泛型属性配置文件 (GATT)** 请参阅[UWP 蓝牙低能耗](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview)主题。 

> [!NOTE]
> 你将需要手动指定 AppManifest 中 RFCOMM 服务。  请参阅[UWP 蓝牙 RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm)主题。 另请参阅[UWP 蓝牙 Rfcomm 聊天示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat)主题。

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a>将蓝牙设备使用设备门户连接
使用之一时[Windows 10 IoT Core 版本映像](https://developer.microsoft.com/en-us/windows/iot/downloads)可以与使用设备门户的 Windows IoT Core 设备配对的蓝牙设备。 导航到蓝牙选项卡时设备将寻找 Bluetooth 的设备，并还将对其他蓝牙设备发现。 下图显示了配对的传入请求。 

![配对的蓝牙传入](../media/Bluetooth/Portal_BT_2.png)

成功配对设备后它将列在配对的设备部分下 

![配对的蓝牙传入](../media/Bluetooth/Portal_BT_3.png)
