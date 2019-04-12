---
title: 在 IoT Core 上 Miracast
author: saraclay
ms.author: saclayt
ms.date: 11/30/2017
ms.topic: article
description: 了解如何包括你的设备上的 Miracast 功能
keywords: windows iot、 miracast、 连接性
ms.openlocfilehash: c58def4b218d35c78532f54df4a74fb572c8549e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512087"
---
# <a name="miracast-on-iot-core"></a>在 IoT Core 上 Miracast

本文档将演示如何以包含 Miracast IoT Core 设备上的功能。

> [!IMPORTANT]
> 此功能仅在内部生成 17093 及更高版本

## <a name="miracast-overview"></a>Miracast 概述

Miracast 连接由两个组件组成： 源和接收器。 **Miracast 源**发送到的内容**Miracast 接收器**，其中显示的内容。 若要创建的连接，接收器将公布自己为连接的 Wi-fi 网络。 源使用**设备选取器**选择接收器并请求连接的连接。 后请求连接时，接收器在用户将收到一条警报源尝试建立连接，必须验证该连接应发生。 一旦发生这种情况，源将开始强制转换为接收器，直到源取消连接或接收器停止公布自己。

## <a name="hardware-requirements"></a>硬件要求

源和接收器的设备需要 Miracast-兼容的 Wi-fi 和图形驱动程序和芯片集才能正常工作。 若要了解你的设备是否具有兼容 Miracast 的硬件，运行： 
```
netsh wlan show driver
```
在设备的命令提示符。

如果设备支持 Miracast，应看到以下输出：

![兼容的设备输出](../media/Miracast/CompatibleDevice.png)

下表显示了 Miracast IoT Core 引用平台的兼容性：

| 看板 | SoC | 提供的 WiFi 驱动程序 | 显示图形驱动程序 | Miracast-Compatible |
|-------|-----|----------------------|--------------------------|---------------------|
| Qualcomm Dragonboard 410 c | Snapdragon 410 | 是 | 是 | 是 |
| Raspberry Pi 2/3 | Broadcom BCM283x | 是 | 否 | 否 |
| Minnowboard Max | Intel Atom E3825 | 是 | 否 | 否 |
| 最多平方 | Intel Celeron N3350 | 是 | 是 | 是 |


### <a name="wi-fi"></a>WLAN

Wi-fi 驱动程序和设备的芯片集必须支持 Wi-Fi Direct，以及其他功能，以支持 Miracast。 如果你的设备不具有这些功能，可以改为使用 USB Wi-fi 硬件保护装置。 我们建议[300 M 无线 USB 适配器](http://a.co/fdhEhV9)。

### <a name="graphics"></a>显卡

图形驱动程序和芯片集必须支持 h.264 编码和解码以支持 Miracast。 如果你的设备不具有兼容的图形驱动程序和/或芯片组，，必须以选择新设备。 请选择兼容 Miracast 的设备时，参阅上面的矩阵。

## <a name="windows-iot-as-a-miracast-sink"></a>Windows IoT 作为 Miracast 接收器

若要启用你的设备作为 Miracast 接收器，将需要启用 Connect 应用在你的设备，然后启用 Miracast 注册表中。

### <a name="enable-the-connect-app"></a>启用应用程序连接

若要使连接应用程序，你将需要包括**IOT_MIRACAST_RX_APP**到映像的功能。 您还需要包括**Microsoft Connect Package.cab**并**Microsoft 连接 Package_Lang_XXXX.cab**映像 （其中 XXXX 是一种语言，即"enUS"） 中。 

请参阅[本页](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest)有关如何将功能和程序包添加到你的映像详细信息。 您可以还旁加载的包和功能到现有的映像遵循[这些说明](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)。 请记住，旁加载此功能将阻止其接收更新。


### <a name="enable-miracast"></a>启用 Miracast

连接到你的设备通过[PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)或[Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)并运行以下命令：
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
这将不同意的情况下通知，仅在安全的网络和连接到交流电源时才启用 Miracast。 这是在 IoT Core 上运行 Miracast 接收方的建议的方法。

## <a name="windows-iot-as-a-miracast-source"></a>Windows IoT 作为 Miracast 源

> [!IMPORTANT]
> 然后尝试使用你的设备作为 Miracast 源，请关闭该 IoTOnboardingTask 应用从[Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)如下所示，这将只需执行一次：![关闭 IoTOnboardingTask 应用](../media/Miracast/IoTOnboardingOff.gif)
>
> 之后，请重启设备

可以设置在通过从公共 Api 兼容设备上的 Miracast 强制转换`Windows.Media.Casting`应用程序中的命名空间。

若要查看操作中的这些 Api，请下载[BasicMediaCasting UWP 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting)和在设备上运行。 此示例中的 Api 包括以下情况下，所有这些在 IoT 核心版兼容 Miracast 的设备运行：
1. 基本媒体强制转换，使用内置的强制转换来将内容发送到支持 Miracast、 DLNA 和蓝牙设备
2. 使用强制转换选取器，以便您可以进一步自定义设备选取器的强制转换
3. 强制转换使用自定义选取器，该图说明了如何构建自定义用户体验，用于选择设备

> [!NOTE]
> 某些 Miracast 接收器 (Surface Laptop，Surface Hub PC 使用无线显示适配器) 是与 IoT Core 强制转换设备不兼容。 我们建议使用[Microsoft 无线显示适配器](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001)用作为 Miracast 接收器兼容的显示器。
