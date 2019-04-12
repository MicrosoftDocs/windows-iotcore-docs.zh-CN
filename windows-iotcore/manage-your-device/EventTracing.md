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
# <a name="event-tracing-for-windows-iot-core"></a><span data-ttu-id="5b538-104">Windows IoT Core 的事件跟踪</span><span class="sxs-lookup"><span data-stu-id="5b538-104">Event Tracing for Windows IoT Core</span></span>

<span data-ttu-id="5b538-105">Windows 事件跟踪 (ETW) 为开发人员提供了可启动和停止检测应用程序能够提供跟踪事件和使用跟踪事件的事件跟踪会话。</span><span class="sxs-lookup"><span data-stu-id="5b538-105">Event Tracing for Windows (ETW) provides developers the ability to start and stop event tracing sessions, instrument an application to provide trace events, and consume trace events.</span></span>
<span data-ttu-id="5b538-106">在 Windows IoT Core 设备上的 ETW 支持基于清单的和经典事件，并与其他 Windows 10 设备没有任何差别。</span><span class="sxs-lookup"><span data-stu-id="5b538-106">ETW on Windows IoT Core devices supports both manifest-based and classic events, and is no different than other Windows 10 devices.</span></span>

<span data-ttu-id="5b538-107">本部分将提供有用的链接上编写和使用事件的基础知识。</span><span class="sxs-lookup"><span data-stu-id="5b538-107">This section will provide useful links on the basics of writing and consuming events.</span></span> <span data-ttu-id="5b538-108">查找更多详细的信息从[Windows 事件跟踪页](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="5b538-108">Find more detailed information from the [Windows Event Tracing page](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span></span>

## <a name="writing-events"></a><span data-ttu-id="5b538-109">编写事件</span><span class="sxs-lookup"><span data-stu-id="5b538-109">Writing Events</span></span>

<span data-ttu-id="5b538-110">查找 UWP 示例实现的一部分写入事件的不同方法[Windows 通用示例 Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging)。</span><span class="sxs-lookup"><span data-stu-id="5b538-110">Find a UWP sample that implements the different methods of writing events as part of the [Windows Universal Samples Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span></span>
<span data-ttu-id="5b538-111">这将在 Windows IoT Core 设备上运行，也很好的代码引用。</span><span class="sxs-lookup"><span data-stu-id="5b538-111">This will run on Windows IoT Core devices and is also a great code reference.</span></span>

<span data-ttu-id="5b538-112">可以找到有关编写事件并获取 Guid 的详细的指南[此处](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="5b538-112">Detailed guide on writing events and obtaining GUIDs can be found [here](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span></span>

## <a name="consuming-events"></a><span data-ttu-id="5b538-113">使用事件</span><span class="sxs-lookup"><span data-stu-id="5b538-113">Consuming Events</span></span>

<span data-ttu-id="5b538-114">事件是或者保存到 ETL 文件中实时捕获。</span><span class="sxs-lookup"><span data-stu-id="5b538-114">Events are either saved to an ETL file or captured in real-time.</span></span>
<span data-ttu-id="5b538-115">使用[FTP](../connect-your-device/FTP.md)或[Windows 文件共享](../manage-your-device/WindowsFileSharing.md)从 Windows IoT Core 设备检索 ETL 文件。</span><span class="sxs-lookup"><span data-stu-id="5b538-115">Use [FTP](../connect-your-device/FTP.md) or [Windows File Sharing](../manage-your-device/WindowsFileSharing.md) to retrieve ETL files from Windows IoT Core devices.</span></span>

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a><span data-ttu-id="5b538-116">使用 Windows 评估和部署工具包中的工具</span><span class="sxs-lookup"><span data-stu-id="5b538-116">Use Tools in Windows Assessment and Deployment Kit</span></span>

<span data-ttu-id="5b538-117">Windows 评估和部署工具包包括 3 个工具以帮助捕获并分析事件。</span><span class="sxs-lookup"><span data-stu-id="5b538-117">Windows Assessment and Deployment Kit includes 3 tools to help capture and analyze events.</span></span> [<span data-ttu-id="5b538-118">单击此处下载</span><span class="sxs-lookup"><span data-stu-id="5b538-118">Click here to download</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)


1. <span data-ttu-id="5b538-119">**Windows Performance Analyzer**分步指南将直观显示在桌面上，ETL 文件[此处](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="5b538-119">**Windows Performance Analyzer** visualizes ETL files on desktop, with a step by step guide [here](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span></span>

2. <span data-ttu-id="5b538-120">**Xperf 命令行工具**捕获实时事件，并将其写入到 ETL 文件。</span><span class="sxs-lookup"><span data-stu-id="5b538-120">**Xperf command line tool** captures real-time events and writes them to an ETL file.</span></span> <span data-ttu-id="5b538-121">此工具已安装在 Windows IoT Core 设备上，只需在设备上运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="5b538-121">This tool is already installed on Windows IoT Core devices, just run the following commands on the devices:</span></span>

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. <span data-ttu-id="5b538-122">**Tracerpt 命令行工具**ETL 文件转换为 xml 文件。</span><span class="sxs-lookup"><span data-stu-id="5b538-122">**Tracerpt command line tool** converts ETL files into xml files.</span></span>

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a><span data-ttu-id="5b538-123">使用设备门户</span><span class="sxs-lookup"><span data-stu-id="5b538-123">Use Device Portal</span></span>

<span data-ttu-id="5b538-124">设备门户可以捕获中的事件的说明通过实时[此处](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)。</span><span class="sxs-lookup"><span data-stu-id="5b538-124">Device portal can capture events in real-time, with instructions [here](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="5b538-125">此方法不会生成 ETL 文件以做进一步分析，但需要最少的设置。</span><span class="sxs-lookup"><span data-stu-id="5b538-125">This method does not produce an ETL file for further analysis, but requires minimal setup.</span></span>

## <a name="use-function-calls"></a><span data-ttu-id="5b538-126">使用函数调用</span><span class="sxs-lookup"><span data-stu-id="5b538-126">Use Function Calls</span></span>

<span data-ttu-id="5b538-127">启用应用程序来使用 ETL 文件中或在实时事件使用函数调用。</span><span class="sxs-lookup"><span data-stu-id="5b538-127">Enable an application to consume events from an ETL file or in real-time using function calls.</span></span>
<span data-ttu-id="5b538-128">了解如何使用这些函数[此处](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="5b538-128">Learn how to use these functions [here](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span></span>
