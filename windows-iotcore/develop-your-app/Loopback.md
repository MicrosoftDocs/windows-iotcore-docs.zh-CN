---
title: 与 Localhost 通信
author: paulmon
ms.author: riameser
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何通过启用 localhost 环回来创建包含两个进程的 TCP/IP 连接。
keywords: windows iot，localhost，环回，UWP，visual studio
ms.openlocfilehash: b1edec04959e5d0ca8beb9bc0061f97c143b8cca
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656203"
---
# <a name="communicating-with-localhost-loopback"></a>与 localhost (环回) 通信

在 Windows IoT Core 上，如果要在同一设备上运行的两个进程之间创建 TCP/IP 连接，并且其中一个是 UWP 应用，则必须启用 localhost 环回。

## <a name="loopback-and-the-debugger"></a>环回和调试器 
默认情况下，在 Visual Studio 调试器下运行仅为该调试会话自动启用出站环回。你不必执行任何操作，只要在启动项目的调试器设置中选中了环回复选框。 如果要实现套接字侦听器，必须为入站连接启用 localhost 环回 (参阅下面) 。

## <a name="enabling-the-inbound-loopback-policy"></a>启用入站环回策略
对于实现服务器的 UWP 应用，必须启用 **Windows IoT Core** 的 localhost 入站环回策略。  此策略由以下注册表项控制：
```
        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001
```
此 IoTInboundLoopbackPolicy 注册表项值必须设置为 dword：00000001，才能启用。 如果更改 IoTInboundLoopbackPolicy 注册表值，则必须重新启动才能使更改生效。默认情况下，在**Windows IoT Core**上启用 localhost 环回策略

若要验证是否已设置该值，请在 **Windows IoT Core** 设备上执行以下命令：
```
        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy
```
若要启用策略，请在 **Windows IoT Core** 设备上执行以下命令：
```
        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
```

## <a name="enabling-loopback-for-a-uwp-application"></a>为 UWP 应用程序启用环回
你需要包系列名称，然后才能为应用程序启用环回。  可以通过运行 **iotstartup 列表**来查找已安装应用程序的包系列名称。  如果应用程序的 **iotstartup 列表** 项为 IoTCoreDefaultApp \_ 1w720vyc4ccym！应用 then 包系列名称是 IoTCoreDefaultApp \_ 1w720vyc4ccym

若要为客户端连接启用环回，请使用 `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>` 。  CheckNetIsolation.exe 将为应用程序配置环回，并退出。 这将使应用程序能够与服务器建立出站连接。

示例：`CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

若要使服务器应用程序能够接收入站连接，请使用 `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>` 。 与出站连接配置不同，入站连接需要 CheckNetIsolation.exe 在服务器应用程序接收连接时连续运行。这要求使用比10.0.14393 更高的操作系统版本。

示例：`CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

在启动时自动运行 CheckNetIsolation.exe 的最佳方式是使用 schtasks.exe： `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

重新启动后，应该能够使用 tlist.exe 或[Windows 设备门户](https://developer.microsoft.com/windows/iot/docs/deviceportal)验证 checknetisolation.exe 正在运行
