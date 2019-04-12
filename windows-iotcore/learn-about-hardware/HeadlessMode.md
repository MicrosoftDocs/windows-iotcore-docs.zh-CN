---
title: 主和无外设设备
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何为设备的主或无外设模式下配置 Windows IoT Core。
keywords: windows iot、 屏幕，讨论的问题，无外设，UI
ms.openlocfilehash: 8ac0d7e06477836aa080af1b7556b054957d0cac
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510868"
---
# <a name="headed-and-headless-devices"></a>主和无外设设备

Windows 10 IoT 核心版可以配置其中任何*讲述的内容*或*无外设*模式。 

## <a name="headed-mode"></a>主的模式
主的模式被定义的 UI 存在。 在中*讲述的内容*模式单个 UI 应用程序将在系统引导启动和另外有可以为 0 或更多"后台应用程序"(StartupTasks)。 

## <a name="headless-mode"></a>无外设模式
无外设模式具有任何 UI。  无需 UI 功能的设备可设置为*无外设*模式。 禁用 UI 堆栈，并且将不启动 UI 应用。 这将减少使用的系统资源量。 如果将监视器附加到你的设备，屏幕将显示为黑色。

> [!NOTE]
> 如果你的设备将进入无外设模式中，您可以使用 Windows 10 IoT 核心版仪表板应用程序，若要查找其 IP 地址，如下所述。

## <a name="changing-the-mode"></a>更改模式
你可以修改你的设备在 Windows PowerShell 会话或 SSH 会话中讨论的问题/无外设状态。 若要了解有关 PowerShell 的详细信息，请参阅[适用于 IoT 核心版的 PowerShell](../connect-your-device/PowerShell.md)页。 若要了解有关 SSH 的详细信息，请参阅[IoT Core 的 SSH](../connect-your-device/SSH.md)页。

* 若要显示你的设备的当前状态，请使用`setbootoption`实用程序：

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* 若要修改设备的状态以启用无外设模式，请将 `setbootoption` 实用工具与 `headless` 参数结合使用：

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* 若要修改设备的状态以启用有外设模式，请将 `setbootoption` 实用工具与 `headed` 参数结合使用：

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a>查找无外设设备

可以使用发现 IoT Core 设备是处于无外设模式下**Windows 10 IoT 核心版仪表板**应用程序。  若要下载 IoT 仪表板，请参阅[下载](http://go.microsoft.com/fwlink/?LinkID=708576)页。
运行时，应用程序侦听的 ping 中的任何 IoT Core 设备上的本地网络，并显示设备信息，例如名称、 IP 地址和的详细信息。

![Windows 10 IoT 核心版仪表板](../media/HeadlessMode/selectDevice.png)
