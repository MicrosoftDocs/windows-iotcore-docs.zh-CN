---
title: 调试概述
ms.date: 05/10/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解可用于调试 Windows 10 IoT Core 的不同方式。
keywords: windows iot，调试，PowerShell，SSH
ms.openlocfilehash: f1560cee2a49e2a05d8bd515fa25fc77b5fc2a2e
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782419"
---
# <a name="debugging-on-windows-iot-core"></a>在 Windows IoT Core 上调试
使用运行中的应用程序设置 IoT 核心映像后，就必须根据需要调试应用程序或系统。 调试和测试系统的最佳时间是测试映像状态。 一旦基于 IoT 核心的系统出现在本质上，调试可能会变得很困难。 这并不是说它无法完成，而是为了进行调试而增加了额外的问题，而与测试阶段相比。 在测试模式下，可以使用以下操作调试应用程序或映像：

## <a name="device-portal"></a>设备门户
通过 Windows 设备门户 (WDP) ，你可以通过本地网络远程配置和管理 IoT 设备。 可以通过 IoT 设备的本地 IP 来访问 WDP。 有关 IoT 上的 WDP 的其他信息，请参阅 [此处](https://docs.microsoft.com/windows/iot-core/manage-your-device/DevicePortal)。

### <a name="collecting-etw--wpp-logs"></a>收集 ETW/WPP 日志 
-----

### <a name="file-sharing"></a>文件共享
应用文件资源管理器可允许访问你的应用可以访问的目录 * vCameraRoll 在所有应用之间共享
* 文档在所有应用中共享
* LocalAppData 包含特定于每个应用的文件夹。 此文件夹将与你的应用同名，并且其他应用无法访问该文件夹。
有关其他信息，请参阅上面的链接。

### <a name="kernel-debug"></a>内核调试
还可以通过 WDP 下载实时内核转储。 系统将自动记录任何系统崩溃并可供下载。 有关其他信息，请参阅上面的链接。

### <a name="enable-crash-dump"></a>启用故障转储
可以通过 WDP 在 IoT 设备上下载应用程序的故障转储。 有关其他信息，请参阅上面的链接。

## <a name="sshpowershelltshell"></a>SSH/PowerShell/TShell
PowerShell 是一种基于任务的命令行 shell 和脚本语言，专为系统管理而设计。 可在 [此处](../connect-your-device/powershell.md)找到有关调试和设置 PowerShell 的详细信息。

## <a name="debug-through-visual-studio-deployment"></a>通过 Visual Studio 部署进行调试
部署和调试应用程序与 Visual Studio 非常直接。 远程调试功能可用于将应用程序部署到本地连接的 Windows 10 IoT Core 设备并进行调试。 有关部署和调试的详细信息，请参阅 [此处](../develop-your-app/RemoteDebugging.md)。

-----
## <a name="live-app-debug"></a>实时应用调试
在 Visual Studio（2015 和更高版本）中，可以使用来自 Azure Application Insights 的遥测，在调试和生产环境中分析 ASP.NET Web 应用中的性能和诊断问题。 此功能在以后扩展，以在 Visual Studio 2017 和中通过 Azure 门户包含桌面和 UWP 应用程序。 有关调试项目的其他信息，请参阅 [此处](https://docs.microsoft.com/azure/azure-monitor/app/visual-studio) 和监视使用情况，可以在 [此处](https://docs.microsoft.com/azure/azure-monitor/app/windows-desktop)找到桌面或 UWP 应用程序的性能。
