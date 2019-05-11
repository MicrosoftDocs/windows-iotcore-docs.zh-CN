---
title: 调试概述
author: saraclay
ms.author: saclayt
ms.date: 05/10/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解有关您可以调试 Windows 10 IoT Core 的不同方式。
keywords: windows iot，调试时，PowerShell SSH
ms.openlocfilehash: 64fa743416823a849deb2cb7826c149f9023a893
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535827"
---
# <a name="debugging-on-windows-iot-core"></a>在 Windows IoT Core 上进行调试
一旦有 IoT Core 映像安装程序正在运行的应用程序，很重要，您可以调试应用程序或系统根据需要。 调试和测试系统的最佳时机是同时测试图像状态。 后 IoT 核心版基于系统在现实出，则调试会变得 challanging。 这并不是说它无法完成，但与其他层的问题添加调试比较测试阶段。 以下可用于调试应用程序或在测试模式下的映像：

## <a name="device-portal"></a>设备门户
Windows Device Portal (WDP) 允许您配置和管理 IoT 设备 remoately 通过本地网络。 WDP 可以是可通过 IoT 设备的本地 ip 访问。 可以找到有关 IoT WDP 的其他信息[此处](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/DevicePortal)。

### <a name="collecting-etw--wpp-logs"></a>收集 ETW / WPP 日志 
-----

### <a name="file-sharing"></a>文件共享
应用文件资源管理器可以允许对您的应用程序可以访问的目录访问 * 之间的所有应用共享 vCameraRoll
* 在所有应用之间共享文档
* LocalAppData 包含特定于每个应用程序的文件夹。 此文件夹将为您的应用程序相同的名称和其他应用程序不能访问它。
请参阅上面的链接的其他信息。

### <a name="kernel-debug"></a>内核调试
您可以下载实时内核转储通过 WDP 也。 任何系统崩溃将自动为已登录并且可供下载。 请参阅上面的链接的其他信息。

### <a name="enable-crash-dump"></a>启用故障转储
您可以下载通过 WDP IoT 设备上的应用程序的故障转储。 请参阅上面的链接的其他信息。

## <a name="sshpowershelltshell"></a>SSH/PowerShell/TShell
PowerShell 是基于任务的命令行 Shell 和脚本语言，专为进行系统管理而设计。 调试和设置 powershell 的详细信息，请[此处](../connect-your-device/powershell.md)。

## <a name="debug-through-visual-studio-deployment"></a>通过 Visual Studio 部署调试
使用 Visual Studio 部署和调试应用程序很简单。 可以使用远程调试功能来部署和调试本地连接的 Windows 10 IoT Core 设备到应用。 详细的部署和调试可以找到[此处](../develop-your-app/RemoteDebugging.md)。

-----
## <a name="live-app-debug"></a>实时应用程序调试
在 Visual Studio 中 （2015年和更高版本），可以分析性能和诊断问题在调试和在生产中，在 ASP.NET web 应用中使用来自 Azure Application Insights 的遥测数据。 该功能更高版本扩展为包括桌面和 UWP 应用程序，在 Visual Studio 2017 中，通过 Azure 门户。 可调试的项目的其他信息[这里](https://docs.microsoft.com/en-us/azure/azure-monitor/app/visual-studio)和监视使用情况和性能在 desktop 或 UWP 应用可将中的可以找到[此处](https://docs.microsoft.com/en-us/azure/azure-monitor/app/windows-desktop)。
