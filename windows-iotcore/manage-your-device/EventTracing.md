---
title: Windows IoT 核心的事件跟踪
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用事件跟踪为 Windows IoT 核心编写事件和使用事件。
keywords: windows iot，事件跟踪，ETW，windows 事件跟踪，设备
ms.openlocfilehash: faf7fd9e4269ba8885ca9613dde03c0c080d2363
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228613"
---
# <a name="event-tracing-for-windows-iot-core"></a><span data-ttu-id="3f0c2-104">Windows IoT 核心的事件跟踪</span><span class="sxs-lookup"><span data-stu-id="3f0c2-104">Event Tracing for Windows IoT Core</span></span>

<span data-ttu-id="3f0c2-105">对于 Windows (ETW) 的事件跟踪，使开发人员能够启动和停止事件跟踪会话，检测应用程序以提供跟踪事件，并使用跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-105">Event Tracing for Windows (ETW) provides developers the ability to start and stop event tracing sessions, instrument an application to provide trace events, and consume trace events.</span></span>
<span data-ttu-id="3f0c2-106">Windows IoT 核心设备上的 ETW 支持基于清单的事件和典型事件，并且与其他 Windows 10 设备没有区别。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-106">ETW on Windows IoT Core devices supports both manifest-based and classic events, and is no different than other Windows 10 devices.</span></span>

<span data-ttu-id="3f0c2-107">本部分将提供有关编写和使用事件的基本知识的有用链接。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-107">This section will provide useful links on the basics of writing and consuming events.</span></span> <span data-ttu-id="3f0c2-108">从 " [Windows 事件跟踪" 页](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx)中查找更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-108">Find more detailed information from the [Windows Event Tracing page](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span></span>

## <a name="writing-events"></a><span data-ttu-id="3f0c2-109">写入事件</span><span class="sxs-lookup"><span data-stu-id="3f0c2-109">Writing Events</span></span>

<span data-ttu-id="3f0c2-110">查找可实现不同方法的 UWP 示例，作为[Windows 通用示例 GitHub](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging)的一部分。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-110">Find a UWP sample that implements the different methods of writing events as part of the [Windows Universal Samples GitHub](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span></span>
<span data-ttu-id="3f0c2-111">这会在 Windows IoT 核心设备上运行，也是一种很好的代码参考。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-111">This will run on Windows IoT Core devices and is also a great code reference.</span></span>

<span data-ttu-id="3f0c2-112">可在 [此处](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx)找到有关写入事件和获取 guid 的详细指南。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-112">Detailed guide on writing events and obtaining GUIDs can be found [here](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span></span>

## <a name="consuming-events"></a><span data-ttu-id="3f0c2-113">使用事件</span><span class="sxs-lookup"><span data-stu-id="3f0c2-113">Consuming Events</span></span>

<span data-ttu-id="3f0c2-114">事件要么保存到 ETL 文件中，要么是实时捕获的。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-114">Events are either saved to an ETL file or captured in real time.</span></span>
<span data-ttu-id="3f0c2-115">使用[FTP](../connect-your-device/FTP.md)或[Windows 文件共享](../manage-your-device/WindowsFileSharing.md)从 Windows IoT 核心设备检索 ETL 文件。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-115">Use [FTP](../connect-your-device/FTP.md) or [Windows File Sharing](../manage-your-device/WindowsFileSharing.md) to retrieve ETL files from Windows IoT Core devices.</span></span>

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a><span data-ttu-id="3f0c2-116">使用 Windows 评估和部署工具包中的工具</span><span class="sxs-lookup"><span data-stu-id="3f0c2-116">Use Tools in Windows Assessment and Deployment Kit</span></span>

<span data-ttu-id="3f0c2-117">[Windows 评估和部署工具包](https://go.microsoft.com/fwlink/p/?LinkId=526740)包含三种工具来帮助捕获和分析事件。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-117">[Windows Assessment and Deployment Kit](https://go.microsoft.com/fwlink/p/?LinkId=526740) includes three tools to help capture and analyze events.</span></span>


1. <span data-ttu-id="3f0c2-118">**Windows 性能分析器** 会直观显示桌面上的 ETL 文件 [，其中包含分步指南。](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="3f0c2-118">**Windows Performance Analyzer** visualizes ETL files on desktop, with a step-by-step guide [here](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span></span>

2. <span data-ttu-id="3f0c2-119">**Xperf 命令行工具** 捕获实时事件并将其写入 ETL 文件。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-119">**Xperf command-line tool** captures real-time events and writes them to an ETL file.</span></span> <span data-ttu-id="3f0c2-120">此工具已安装在 Windows IoT Core 设备上，只需在设备上运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f0c2-120">This tool is already installed on Windows IoT Core devices, just run the following commands on the devices:</span></span>
```
        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>
```

3. <span data-ttu-id="3f0c2-121">**Tracerpt 命令行工具** 将 ETL 文件转换为 xml 文件。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-121">**Tracerpt command-line tool** converts ETL files into xml files.</span></span>
```
        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>
```

## <a name="use-device-portal"></a><span data-ttu-id="3f0c2-122">使用设备门户</span><span class="sxs-lookup"><span data-stu-id="3f0c2-122">Use Device Portal</span></span>

<span data-ttu-id="3f0c2-123">设备门户可以实时捕获事件[，其中提供了说明。](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="3f0c2-123">Device portal can capture events in real time, with instructions [here](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="3f0c2-124">此方法不会生成用于进一步分析的 ETL 文件，但需要最少的设置。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-124">This method does not produce an ETL file for further analysis, but requires minimal setup.</span></span>

## <a name="use-function-calls"></a><span data-ttu-id="3f0c2-125">使用函数调用</span><span class="sxs-lookup"><span data-stu-id="3f0c2-125">Use Function Calls</span></span>

<span data-ttu-id="3f0c2-126">使应用程序能够使用 ETL 文件中的事件，或使用函数调用实时使用这些事件。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-126">Enable an application to consume events from an ETL file or in real-time using function calls.</span></span>
<span data-ttu-id="3f0c2-127">[在此处](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx)了解如何使用这些函数。</span><span class="sxs-lookup"><span data-stu-id="3f0c2-127">Learn how to use these functions [here](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span></span>
