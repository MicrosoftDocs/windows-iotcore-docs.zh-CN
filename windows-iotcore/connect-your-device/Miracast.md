---
title: Miracast IoT 核心
ms.date: 11/30/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在设备上Miracast功能。 阅读Miracast概述、硬件要求以及如何将 IoT Windows接收器Miracast源。
keywords: windows iot， miracast， 连接
ms.openlocfilehash: 72c2ef6b7a710cf120c45ebf265f0930c960d062
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229244"
---
# <a name="miracast-on-iot-core"></a>Miracast IoT 核心

本文档将展示如何在 IoT core Miracast包括其他功能。

> [!IMPORTANT]
> 此功能仅在预览体验内部版本 17093 及以上版本上可用

## <a name="miracast-overview"></a>Miracast概述

一Miracast连接由两个组件组成：Source 和 Sink。 源 **Miracast将** 内容发送到 Miracast **接收器**，该接收器显示内容。 若要创建连接，接收器将自身播发到连接的Wi-Fi网络。 源使用 **设备选取器** 选择接收器并请求连接。 请求连接后，接收器的用户会收到一条警报，指出源正在尝试建立连接，并且必须验证连接是否应发生。 发生这种情况后，源开始强制转换到接收器，直到源取消连接或接收器停止广告。

## <a name="hardware-requirements"></a>硬件要求

源和接收器设备都需要Miracast兼容的Wi-Fi和图形驱动程序和芯片组正常工作。 若要了解设备是否具有Miracast兼容硬件，请运行： 
```
netsh wlan show driver
```
在设备的命令提示符下。

如果设备支持Miracast，应会看到以下输出：

![兼容的设备输出](../media/Miracast/CompatibleDevice.png)

下表显示了 IoT Miracast平台的兼容性：

| Board | SoC | WiFi 驱动程序存在 | 图形驱动程序存在 | Miracast-Compatible |
|-------|-----|----------------------|--------------------------|---------------------|
| Qualcomm Dragonboard 410c | Snapdragon 410 | 是 | 是 | 是 |
| Raspberry Pi 2/3 | Broadcom BCM283x | 是 | 否 | 否 |
| Minnowboard Max | Intel Atom E3825 | 是 | 否 | 否 |
| UP Squared | Intel Celeron N3350 | 是 | 是 | 是 |


### <a name="wi-fi"></a>Wi-Fi

设备Wi-Fi驱动程序和芯片组必须支持 Wi-Fi Direct 和其他功能，以支持Miracast。 如果设备没有这些功能，可以改为使用 USB Wi-Fi适配器。 建议使用 [300M 无线 USB 适配器](http://a.co/fdhEhV9)。

### <a name="graphics"></a>显卡

图形驱动程序和芯片组必须支持 h.264 编码和解码，以支持Miracast。 如果设备没有兼容的图形驱动程序和/或芯片组，必须选择新设备。 选择与设备兼容的设备时，Miracast上述矩阵。

## <a name="windows-iot-as-a-miracast-sink"></a>WindowsIoT 作为Miracast接收器

若要将设备作为 Miracast接收器，需要在设备上启用 连接 应用，然后在注册表中Miracast应用。

### <a name="enable-the-connect-app"></a>启用 连接 应用

若要连接应用，需要将 IOT_MIRACAST_RX_APP **功能包括在** 映像中。 在 XXXX **是** 一种语言Microsoft-Connect-Package.cab"enUS"Microsoft-Connect-Package_Lang_XXXX.cab中，还需要在映像 (和) 。  

若要详细了解如何将功能和包添加到映像，请查看 [IoT 核心](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) 制造指南。 还可按照这些说明将包和功能旁加载到 [现有映像](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)。 请记住，旁加载此功能会阻止它接收更新。


### <a name="enable-miracast"></a>启用Miracast

连接[PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)或 Windows 设备门户连接到设备[，](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)并运行以下命令：
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
这样，Miracast在安全网络上，并且仅在连接到 A/C 电源时，才允许无许可通知。 这是在 IoT 核心Miracast接收器的建议方法。

## <a name="windows-iot-as-a-miracast-source"></a>WindowsIoT 作为Miracast源

> [!IMPORTANT]
> 在尝试将设备用作 Miracast 源之前，请从 Windows 设备门户 关闭 IoTOnboardingTask 应用[，](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)如下所示，只需执行一次操作：关闭 ![ IoTOnboardingTask 应用](../media/Miracast/IoTOnboardingOff.gif)
>
> 然后，请重启设备

可以通过应用Miracast命名空间中的公共 API 在兼容设备上设置 `Windows.Media.Casting` 强制转换。

若要了解这些 API 的运行，请下载 [BasicMediaCasting UWP 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) ，然后在你的设备上运行它。 示例中的 API 涵盖以下方案，所有这些方案都Miracast IoT Core 设备上运行：
1. 基本媒体强制转换，它使用内置强制转换将内容发送到 Miracast、DLNA 和 蓝牙设备
2. 使用强制转换选取器进行强制转换，用于进一步自定义设备选取器
3. 使用自定义选取器进行强制转换，演示如何生成用于选择设备的自定义 UX

> [!NOTE]
> 具有无线Miracast适配器 (Surface Laptop、Surface Hub电脑的一些) 接收器与 IoT 核心强制转换设备不兼容。 建议使用具有兼容[监视器的 Microsoft 无线](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001)显示适配器作为Miracast接收器。
