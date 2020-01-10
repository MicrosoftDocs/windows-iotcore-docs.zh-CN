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
# <a name="event-tracing-for-windows-iot-core"></a><span data-ttu-id="72914-104">Windows IoT Core 事件跟踪</span><span class="sxs-lookup"><span data-stu-id="72914-104">Event Tracing for Windows IoT Core</span></span>

<span data-ttu-id="72914-105">Windows 事件跟踪（ETW）使开发人员能够启动和停止事件跟踪会话，检测应用程序以提供跟踪事件，并使用跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="72914-105">Event Tracing for Windows (ETW) provides developers the ability to start and stop event tracing sessions, instrument an application to provide trace events, and consume trace events.</span></span>
<span data-ttu-id="72914-106">Windows IoT Core 设备上的 ETW 支持基于清单的事件和典型事件，与其他 Windows 10 设备并无区别。</span><span class="sxs-lookup"><span data-stu-id="72914-106">ETW on Windows IoT Core devices supports both manifest-based and classic events, and is no different than other Windows 10 devices.</span></span>

<span data-ttu-id="72914-107">本部分将提供有关编写和使用事件的基本知识的有用链接。</span><span class="sxs-lookup"><span data-stu-id="72914-107">This section will provide useful links on the basics of writing and consuming events.</span></span> <span data-ttu-id="72914-108">从[Windows 事件跟踪页](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx)中查找更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="72914-108">Find more detailed information from the [Windows Event Tracing page](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span></span>

## <a name="writing-events"></a><span data-ttu-id="72914-109">写入事件</span><span class="sxs-lookup"><span data-stu-id="72914-109">Writing Events</span></span>

<span data-ttu-id="72914-110">查找一个 UWP 示例，用于实现在[Windows 通用示例 Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging)中编写事件的不同方法。</span><span class="sxs-lookup"><span data-stu-id="72914-110">Find a UWP sample that implements the different methods of writing events as part of the [Windows Universal Samples Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span></span>
<span data-ttu-id="72914-111">这会在 Windows IoT Core 设备上运行，也是一种很好的代码参考。</span><span class="sxs-lookup"><span data-stu-id="72914-111">This will run on Windows IoT Core devices and is also a great code reference.</span></span>

<span data-ttu-id="72914-112">可在[此处](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx)找到有关写入事件和获取 guid 的详细指南。</span><span class="sxs-lookup"><span data-stu-id="72914-112">Detailed guide on writing events and obtaining GUIDs can be found [here](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span></span>

## <a name="consuming-events"></a><span data-ttu-id="72914-113">使用事件</span><span class="sxs-lookup"><span data-stu-id="72914-113">Consuming Events</span></span>

<span data-ttu-id="72914-114">事件将保存到 ETL 文件或实时捕获。</span><span class="sxs-lookup"><span data-stu-id="72914-114">Events are either saved to an ETL file or captured in real-time.</span></span>
<span data-ttu-id="72914-115">使用[FTP](../connect-your-device/FTP.md)或[windows 文件共享](../manage-your-device/WindowsFileSharing.md)从 Windows IOT Core 设备检索 ETL 文件。</span><span class="sxs-lookup"><span data-stu-id="72914-115">Use [FTP](../connect-your-device/FTP.md) or [Windows File Sharing](../manage-your-device/WindowsFileSharing.md) to retrieve ETL files from Windows IoT Core devices.</span></span>

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a><span data-ttu-id="72914-116">使用 Windows 评估和部署工具包中的工具</span><span class="sxs-lookup"><span data-stu-id="72914-116">Use Tools in Windows Assessment and Deployment Kit</span></span>

<span data-ttu-id="72914-117">Windows 评估和部署工具包包含3个可帮助捕获和分析事件的工具。</span><span class="sxs-lookup"><span data-stu-id="72914-117">Windows Assessment and Deployment Kit includes 3 tools to help capture and analyze events.</span></span> [<span data-ttu-id="72914-118">单击此处下载</span><span class="sxs-lookup"><span data-stu-id="72914-118">Click here to download</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526740)


1. <span data-ttu-id="72914-119">**Windows 性能分析器**直观显示桌面上的 ETL 文件[，其中包含分步指南。](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="72914-119">**Windows Performance Analyzer** visualizes ETL files on desktop, with a step by step guide [here](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span></span>

2. <span data-ttu-id="72914-120">**Xperf 命令行工具**捕获实时事件并将其写入 ETL 文件。</span><span class="sxs-lookup"><span data-stu-id="72914-120">**Xperf command line tool** captures real-time events and writes them to an ETL file.</span></span> <span data-ttu-id="72914-121">此工具已安装在 Windows IoT Core 设备上，只需在设备上运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="72914-121">This tool is already installed on Windows IoT Core devices, just run the following commands on the devices:</span></span>

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. <span data-ttu-id="72914-122">**Tracerpt 命令行工具**将 ETL 文件转换为 xml 文件。</span><span class="sxs-lookup"><span data-stu-id="72914-122">**Tracerpt command line tool** converts ETL files into xml files.</span></span>

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a><span data-ttu-id="72914-123">使用设备门户</span><span class="sxs-lookup"><span data-stu-id="72914-123">Use Device Portal</span></span>

<span data-ttu-id="72914-124">设备门户可实时捕获事件，并提供[此处](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)的说明。</span><span class="sxs-lookup"><span data-stu-id="72914-124">Device portal can capture events in real-time, with instructions [here](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="72914-125">此方法不会生成用于进一步分析的 ETL 文件，但需要最少的设置。</span><span class="sxs-lookup"><span data-stu-id="72914-125">This method does not produce an ETL file for further analysis, but requires minimal setup.</span></span>

## <a name="use-function-calls"></a><span data-ttu-id="72914-126">使用函数调用</span><span class="sxs-lookup"><span data-stu-id="72914-126">Use Function Calls</span></span>

<span data-ttu-id="72914-127">使应用程序能够使用 ETL 文件中的事件，或使用函数调用实时使用这些事件。</span><span class="sxs-lookup"><span data-stu-id="72914-127">Enable an application to consume events from an ETL file or in real-time using function calls.</span></span>
<span data-ttu-id="72914-128">[在此处](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx)了解如何使用这些函数。</span><span class="sxs-lookup"><span data-stu-id="72914-128">Learn how to use these functions [here](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span></span>
