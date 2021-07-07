---
title: 有外设设备和无外设设备
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何为设备Windows头模式或无头模式配置 IoT 核心。
keywords: windows iot， 屏幕， 头， 无头， UI
ms.openlocfilehash: 73168eae98747a13a6880de9a5ec581102dc859c
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228833"
---
# <a name="headed-and-headless-devices"></a>头设备和无头设备

Windows 10 IoT 核心版可配置为有 *向模式或**无头* 模式。 

## <a name="headed-mode"></a>前向模式
方向模式由 UI 的存在定义。 在 *引导* 模式下，将在系统启动时启动单个 UI 应用，此外，StartupTasks (0) 。 

## <a name="headless-mode"></a>无头模式
无头模式没有 UI。  不需要 UI 功能的设备可以设置为无 *头* 模式。 UI 堆栈已禁用，UI 应用不会启动。 这会减少使用的系统资源量。 如果将监视器附加到设备，屏幕将为黑色。

> [!NOTE]
> 如果将设备置于无头模式，可以使用 Windows 10 IoT 核心版仪表板应用程序（如下所述）查找其 IP 地址。

## <a name="changing-the-mode"></a>更改模式
可以从会话或 SSH 会话修改设备的Windows PowerShell/无头状态。 若要详细了解 PowerShell，请参阅 [PowerShell for IoT Core](../connect-your-device/PowerShell.md) 页。 若要详细了解 SSH，请参阅 [SSH for IoT Core](../connect-your-device/SSH.md) 页。

* 若要显示设备的当前状态，请使用 `setbootoption` 实用工具：

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* 若要修改设备的状态以启用无头模式，请通过 `setbootoption` arg 使用 `headless` 实用工具：

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* 若要修改设备的状态以启用前向模式，请通过 `setbootoption` arg 使用 `headed` 实用工具：

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a>查找无头设备

可以使用无头模式发现采用无头模式的 IoT 核心 **Windows 10 IoT 核心版仪表板应用程序。**  若要下载IoT 仪表板，请参阅 [下载](https://go.microsoft.com/fwlink/?LinkID=708576) 页。
运行时，应用程序侦听来自本地网络上任何 IoT 核心设备的 ping，并显示设备信息，例如名称、IP 地址等。

![Windows 10 IoT 核心版仪表板](../media/HeadlessMode/selectDevice.png)
