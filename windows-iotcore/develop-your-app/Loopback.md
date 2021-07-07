---
title: 与 Localhost 通信
author: paulmon
ms.author: riameser
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何通过启用 localhost 环回创建具有两个过程的 TCP/IP 连接。
keywords: windows iot， localhost， loopback， UWP， visual studio
ms.openlocfilehash: 563edb6c894cf4c2049721d71f1c74d057dfd291
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229804"
---
# <a name="communicating-with-localhost-loopback"></a>与 localhost (环回) 

在 Windows IoT Core 上，如果要在同一设备上运行的两个进程之间创建 TCP/IP 连接，并且其中一个进程是 UWP 应用，则必须启用 localhost 环回。

## <a name="loopback-and-the-debugger"></a>环回和调试器 
默认情况下，在调试器下Visual Studio仅针对该调试会话自动启用出站环回。  只要在启动项目的调试器设置中选中环回复选框，就不需要执行任何操作。  如果要实现套接字侦听器，则必须为入站连接启用 localhost 环回 (请参阅下面的) 。

## <a name="enabling-the-inbound-loopback-policy"></a>启用入站环回策略
必须为实现服务器的 UWP 应用启用 **Windows IoT 核心** 的 localhost 入站环回策略。  此策略由以下注册表项控制：
```
        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001
```
此 IoTInboundLoopbackPolicy 注册表项值必须设置为 dword：00000001 才能启用。 如果更改 IoTInboundLoopbackPolicy 注册表值，则必须重新启动更改才能生效。  默认情况下，应在 IoT Core 上启用 **localhost Windows策略**

若要验证是否设置了该值，请对 **IoT 核心Windows以下** 命令：
```
        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy
```
若要启用策略，请对 **IoT Core** Windows以下命令：
```
        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
```

## <a name="enabling-loopback-for-a-uwp-application"></a>为 UWP 应用程序启用环回
在为应用程序启用环回之前，需要包系列名称。  可以通过运行 **iotstartup** 列表 来查找已安装应用程序的包系列名称。  如果应用程序的 **iotstartup 列表** 条目为 IoTCoreDefaultApp \_ 1w720vyc4ccym！应用，则包系列名称为 IoTCoreDefaultApp \_ 1w720vyc4ccym

若要为客户端连接启用环回，请使用 `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>` 。  CheckNetIsolation.exe配置应用程序的环回并退出。 这将使应用程序能够与服务器建立出站连接。

示例： `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

若要使服务器应用程序能够接收入站连接，请使用 `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>` 。 与出站连接配置不同，入站连接CheckNetIsolation.exe服务器应用程序接收连接时连续运行。  这要求 OS 内部版本高于 10.0.14393。

示例： `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

在启动时自动运行CheckNetIsolation.exe最佳方法为使用schtasks.exe： `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

重新启动后，你应该能够通过使用 checknetisolation.exe 或 tlist.exe 来验证Windows 设备门户[](https://developer.microsoft.com/windows/iot/docs/deviceportal)
