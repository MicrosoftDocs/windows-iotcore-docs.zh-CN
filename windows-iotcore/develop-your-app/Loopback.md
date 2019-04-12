---
title: 与本地主机通信
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: 了解如何通过启用本地主机环回使用两个进程创建的 TCP/IP 连接。
keywords: windows iot、 localhost、 环回、 UWP、 visual studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510616"
---
# <a name="communicating-with-localhost-loopback"></a>与本地主机 （环回） 进行通信

在 Windows IoT Core，如果你想要创建运行在同一设备上的 2 个进程之间的 TCP/IP 连接，并且其中一种是 UWP 应用必须启用本地主机环回。

## <a name="loopback-and-the-debugger"></a>Loopback 和调试器 
默认情况下，在 Visual Studio 调试器下的运行，可以在出站环回自动仅适用于该调试会话。  您无需执行任何操作，只要启动项目的调试程序设置中选中的环回复选框。  如果您想要实现的套接字侦听器则必须启用本地主机环回为入站连接 （见下文）。
 
## <a name="enabling-the-inbound-loopback-policy"></a>如果启用入站的环回策略
本地主机的入站环回策略**Windows IoT Core**必须适用于 UWP 应用实现服务器启用。  此策略控制由以下注册表项：

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

此 IoTInboundLoopbackPolicy 注册表项值必须设置为 dword: 00000001 启用。 如果您更改 IoTInboundLoopbackPolicy 注册表值，您必须重新启动计算机更改才能生效。  应在默认情况下启用本地主机环回策略**Windows IoT 核心版**

若要验证的值是组执行以下命令上**Windows IoT Core**设备：

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

若要启用该策略执行以下命令上**Windows IoT Core**设备：

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a>UWP 应用程序的启用环回
在启用环回应用程序之前，你将需要包系列名称。  可以通过运行安装的应用程序中找到包系列名称**iotstartup 列表**。  如果**iotstartup 列表**应用程序的条目是 IoTCoreDefaultApp\_1w720vyc4ccym ！应用程序然后包系列名称是 IoTCoreDefaultApp\_1w720vyc4ccym

若要启用用于客户端连接的环回`CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`。  CheckNetIsolation.exe 将配置应用程序和退出的环回。 这将使应用程序以进行出站连接到服务器。

例如： `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

若要启用的服务器应用程序接收的入站的连接，请使用`CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`。 与出站连接配置中，不同的入站的连接需要 CheckNetIsolation.exe 运行服务器应用程序正在接收的连接时，持续。  这需要更高版本低于 10.0.14393 的 OS 生成。

例如： `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

在启动时自动运行 CheckNetIsolation.exe 的最佳方式是使用 schtasks.exe: `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

在重新启动时应为能够验证该 checknetisolation.exe 运行通过使用 tlist.exe 或[Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)
