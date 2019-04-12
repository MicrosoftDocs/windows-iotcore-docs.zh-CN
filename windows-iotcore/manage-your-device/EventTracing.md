---
title: Windows IoT Core 的事件跟踪
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用事件跟踪来写入事件和使用适用于 Windows IoT Core 的事件。
keywords: windows iot 事件跟踪，etw 的更多信息，事件跟踪适用于 windows 设备
ms.openlocfilehash: 7e01681e2af2ed8913614ba23bd12dfd36bcd76e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59511065"
---
# <a name="event-tracing-for-windows-iot-core"></a>Windows IoT Core 的事件跟踪

Windows 事件跟踪 (ETW) 为开发人员提供了可启动和停止检测应用程序能够提供跟踪事件和使用跟踪事件的事件跟踪会话。
在 Windows IoT Core 设备上的 ETW 支持基于清单的和经典事件，并与其他 Windows 10 设备没有任何差别。

本部分将提供有用的链接上编写和使用事件的基础知识。 查找更多详细的信息从[Windows 事件跟踪页](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx)。

## <a name="writing-events"></a>编写事件

查找 UWP 示例实现的一部分写入事件的不同方法[Windows 通用示例 Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging)。
这将在 Windows IoT Core 设备上运行，也很好的代码引用。

可以找到有关编写事件并获取 Guid 的详细的指南[此处](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx)。

## <a name="consuming-events"></a>使用事件

事件是或者保存到 ETL 文件中实时捕获。
使用[FTP](../connect-your-device/FTP.md)或[Windows 文件共享](../manage-your-device/WindowsFileSharing.md)从 Windows IoT Core 设备检索 ETL 文件。

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a>使用 Windows 评估和部署工具包中的工具

Windows 评估和部署工具包包括 3 个工具以帮助捕获并分析事件。 [单击此处下载](http://go.microsoft.com/fwlink/p/?LinkId=526740)


1. **Windows Performance Analyzer**分步指南将直观显示在桌面上，ETL 文件[此处](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx)。

2. **Xperf 命令行工具**捕获实时事件，并将其写入到 ETL 文件。 此工具已安装在 Windows IoT Core 设备上，只需在设备上运行以下命令：

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. **Tracerpt 命令行工具**ETL 文件转换为 xml 文件。

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a>使用设备门户

设备门户可以捕获中的事件的说明通过实时[此处](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)。

> [!NOTE]
> 此方法不会生成 ETL 文件以做进一步分析，但需要最少的设置。

## <a name="use-function-calls"></a>使用函数调用

启用应用程序来使用 ETL 文件中或在实时事件使用函数调用。
了解如何使用这些函数[此处](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx)。
