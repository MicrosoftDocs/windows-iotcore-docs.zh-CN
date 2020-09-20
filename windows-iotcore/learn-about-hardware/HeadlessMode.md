---
title: 有外设设备和无外设设备
ms.date: 08/28/2017
ms.topic: article
description: 了解如何为设备配置 Windows IoT Core，使其适用于 "头" 或 "无外设" 模式。
keywords: windows iot，屏幕，头，无外设，UI
ms.openlocfilehash: a402697d1e5169a313f7c8ebc0604f74e24b00d8
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782659"
---
# <a name="headed-and-headless-devices"></a>头和无外设设备

可以为 " *头* " 或 "无 *外设* " 模式配置 Windows 10 IoT Core。 

## <a name="headed-mode"></a>头模式
头模式由 UI 的状态定义。 在 *"方向" 模式下* ，将在系统启动时启动单个 UI 应用，还可以有0个或更多 "后台应用" (StartupTasks) 。 

## <a name="headless-mode"></a>无外设模式
无外设模式没有 UI。  不需要 UI 功能的设备可以设置为无 *外设* 模式。 UI 堆栈处于禁用状态，UI 应用将无法启动。 这会减少使用的系统资源量。 如果将监视器连接到设备，屏幕将为黑色。

> [!NOTE]
> 如果将设备置于无外设模式，则可以使用下面所述的 Windows 10 IoT Core 仪表板应用程序来查找其 IP 地址。

## <a name="changing-the-mode"></a>更改模式
你可以从 Windows PowerShell 会话或 SSH 会话中修改设备的头/无外设状态。 若要了解有关 PowerShell 的详细信息，请参阅 [powershell For IoT Core](../connect-your-device/PowerShell.md) 页。 若要了解有关 SSH 的详细信息，请参阅 [ssh 的 IoT 核心](../connect-your-device/SSH.md) 页面。

* 若要显示设备的当前状态，请使用 `setbootoption` 实用工具：

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* 若要修改设备的状态以启用无外设模式，请使用 `setbootoption` 带有 arg 的实用工具 `headless` ：

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* 若要将设备的状态修改为启用方向模式，请使用 `setbootoption` 带有 arg 的实用工具 `headed` ：

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a>查找无外设设备

在无外设模式下的 IoT 核心设备可以使用 **Windows 10 IoT Core 仪表板** 应用程序来发现。  若要下载 IoT 面板，请参阅 [下载](https://go.microsoft.com/fwlink/?LinkID=708576) 页。
运行时，应用程序会侦听来自本地网络上的任何 IoT 核心设备的 ping，并显示设备信息，如名称、IP 地址等。

![Windows 10 IoT 核心版仪表板](../media/HeadlessMode/selectDevice.png)
