---
title: IoT Core 上的 Miracast
ms.date: 11/30/2017
ms.topic: article
description: 了解如何在设备上包含 Miracast 功能
keywords: windows iot，miracast，连接
ms.openlocfilehash: bb997d0ec2899e7a0a988674ae8907e15e87b3c3
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918322"
---
# <a name="miracast-on-iot-core"></a>IoT Core 上的 Miracast

本文档将演示如何在 IoT Core 设备上包含 Miracast 功能。

> [!IMPORTANT]
> 此功能仅适用于有问必答版本17093及更高版本

## <a name="miracast-overview"></a>Miracast 概述

Miracast 连接由两个组件组成：源和接收器。 **Miracast 源**会将内容发送到**miracast 接收器**，其中显示内容。 若要创建连接，接收器会将其自身播发到连接的 Wi-fi 网络。 源使用**设备选取器**来选择接收器并请求连接。 请求连接后，接收器上的用户将收到一个警报，指出源正在尝试建立连接，并且必须验证是否应进行连接。 出现这种情况后，源将开始强制转换到接收器，直到源取消了该连接或接收器停止公布。

## <a name="hardware-requirements"></a>硬件要求

源设备和接收器设备都需要与 Miracast 兼容的 Wi-fi 和图形驱动程序和芯片组才能正常工作。 若要查明设备是否具有与 Miracast 兼容的硬件，请运行： 
```
netsh wlan show driver
```
在设备的命令提示符下。

如果设备支持 Miracast，应会看到以下输出：

![兼容设备输出](../media/Miracast/CompatibleDevice.png)

下表显示 IoT 核心参考平台的 Miracast 兼容性：

| 插件 | SoC | 提供 WiFi 驱动程序 | 图形驱动程序存在 | Miracast 兼容 |
|-------|-----|----------------------|--------------------------|---------------------|
| Qualcomm Dragonboard 410c | Snapdragon 410 | “是” | “是” | “是” |
| Raspberry Pi 2/3 | Broadcom BCM283x | “是” | 无 | 无 |
| Minnowboard Max | Intel Atom E3825 | “是” | 无 | 无 |
| 上 Squared | Intel 赛扬 N3350 | “是” | “是” | “是” |


### <a name="wi-fi"></a>WLAN

设备的 Wi-fi 驱动程序和芯片集必须支持 Wi-fi Direct （除了其他功能）才能支持 Miracast。 如果设备没有这些功能，则可以改用 USB Wi-fi 转换器。 建议[300M 无线 USB 适配器](http://a.co/fdhEhV9)。

### <a name="graphics"></a>显卡

图形驱动程序和芯片组必须支持 h.264 编码和解码以支持 Miracast。 如果设备没有兼容的图形驱动程序和/或芯片集，则必须选择新的设备。 请在选择与 Miracast 兼容的设备时查阅上述矩阵。

## <a name="windows-iot-as-a-miracast-sink"></a>Windows IoT 作为 Miracast 接收器

若要将设备启用为 Miracast 接收器，你将需要在设备上启用连接应用，然后在注册表中启用 Miracast。

### <a name="enable-the-connect-app"></a>启用连接应用

若要启用连接应用，需要在映像中包含**IOT_MIRACAST_RX_APP**功能。 还需要在映像中包含**Microsoft-Connect-Package**和**MICROSOFT-CONNECT-PACKAGE_LANG_XXXX** （其中 XXXX 是一种语言，即 "enUS"）。 

有关如何向映像添加功能和包的详细信息，请参阅[此页](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest)。 还可以按照[这些说明](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)将包和功能并行加载到现有映像。 请记住，在这种情况下，加载此功能会阻止它接收更新。


### <a name="enable-miracast"></a>启用 Miracast

通过[PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)或[Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)连接到设备，并运行以下命令：
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
这将在不同意通知的情况下启用 Miracast，仅在安全网络上启用，且仅在连接到/C 电源时启用。 这是在 IoT Core 上运行 Miracast 接收器的建议方法。

## <a name="windows-iot-as-a-miracast-source"></a>作为 Miracast 源的 Windows IoT

> [!IMPORTANT]
> 在尝试将你的设备用作 Miracast 源之前，请从[Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)关闭 IoTOnboardingTask 应用，如下所示，你只需要执行一次： ![关闭 IoTOnboardingTask 应用](../media/Miracast/IoTOnboardingOff.gif)
>
> 之后，请重新启动设备

可以通过应用中 `Windows.Media.Casting` 命名空间的公共 Api 在兼容的设备上设置 Miracast 强制转换。

若要查看这些 Api 的运行情况，请下载[BASICMEDIACASTING UWP 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting)并在设备上运行它。 示例中的 Api 涵盖以下方案，所有这些方案都在与 Miracast 兼容的 IoT Core 设备上运行：
1. 基本媒体转换，使用内置转换将内容发送到 Miracast、DLNA 和蓝牙设备
2. 使用强制转换选取器强制转换，这允许你进一步自定义设备选取器
3. 使用自定义选取器进行强制转换，该选取器阐释了如何生成用于选择设备的自定义 UX

> [!NOTE]
> 某些 Miracast 接收器（Surface 膝上机、Surface Hub、带有无线显示适配器的 PC）与 IoT 核心电影设备不兼容。 建议将[Microsoft 无线显示适配器](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001)用于兼容的监视器作为 Miracast 接收器。
