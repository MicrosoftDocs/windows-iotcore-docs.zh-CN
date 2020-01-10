---
title: Windows IoT Core 事件跟踪
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用事件跟踪为 Windows IoT Core 编写事件和使用事件。
keywords: windows iot，事件跟踪，ETW，windows 事件跟踪，设备
ms.openlocfilehash: e5d017c28640f78011ef0b7d82071a51524b2185
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721570"
---
# <a name="event-tracing-for-windows-iot-core"></a>Windows IoT Core 事件跟踪

Windows 事件跟踪（ETW）使开发人员能够启动和停止事件跟踪会话，检测应用程序以提供跟踪事件，并使用跟踪事件。
Windows IoT Core 设备上的 ETW 支持基于清单的事件和典型事件，与其他 Windows 10 设备并无区别。

本部分将提供有关编写和使用事件的基本知识的有用链接。 从[Windows 事件跟踪页](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx)中查找更多详细信息。

## <a name="writing-events"></a>写入事件

查找一个 UWP 示例，用于实现在[Windows 通用示例 Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging)中编写事件的不同方法。
这会在 Windows IoT Core 设备上运行，也是一种很好的代码参考。

可在[此处](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx)找到有关写入事件和获取 guid 的详细指南。

## <a name="consuming-events"></a>使用事件

事件将保存到 ETL 文件或实时捕获。
使用[FTP](../connect-your-device/FTP.md)或[windows 文件共享](../manage-your-device/WindowsFileSharing.md)从 Windows IOT Core 设备检索 ETL 文件。

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a>使用 Windows 评估和部署工具包中的工具

Windows 评估和部署工具包包含3个可帮助捕获和分析事件的工具。 [单击此处下载](https://go.microsoft.com/fwlink/p/?LinkId=526740)


1. **Windows 性能分析器**直观显示桌面上的 ETL 文件[，其中包含分步指南。](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx)

2. **Xperf 命令行工具**捕获实时事件并将其写入 ETL 文件。 此工具已安装在 Windows IoT Core 设备上，只需在设备上运行以下命令：

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. **Tracerpt 命令行工具**将 ETL 文件转换为 xml 文件。

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a>使用设备门户

设备门户可实时捕获事件，并提供[此处](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)的说明。

> [!NOTE]
> 此方法不会生成用于进一步分析的 ETL 文件，但需要最少的设置。

## <a name="use-function-calls"></a>使用函数调用

使应用程序能够使用 ETL 文件中的事件，或使用函数调用实时使用这些事件。
[在此处](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx)了解如何使用这些函数。
