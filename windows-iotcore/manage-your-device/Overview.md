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
# <a name="debugging-on-windows-iot-core"></a><span data-ttu-id="a9299-104">在 Windows IoT Core 上进行调试</span><span class="sxs-lookup"><span data-stu-id="a9299-104">Debugging on Windows IoT Core</span></span>
<span data-ttu-id="a9299-105">一旦有 IoT Core 映像安装程序正在运行的应用程序，很重要，您可以调试应用程序或系统根据需要。</span><span class="sxs-lookup"><span data-stu-id="a9299-105">Once you have your IoT Core image setup with running application, it is important that you can debug the application or the system as needed.</span></span> <span data-ttu-id="a9299-106">调试和测试系统的最佳时机是同时测试图像状态。</span><span class="sxs-lookup"><span data-stu-id="a9299-106">The best time to debug and test the system is while the test image state.</span></span> <span data-ttu-id="a9299-107">后 IoT 核心版基于系统在现实出，则调试会变得 challanging。</span><span class="sxs-lookup"><span data-stu-id="a9299-107">Once IoT Core based systems is out in the wild, debugging can become challanging.</span></span> <span data-ttu-id="a9299-108">这并不是说它无法完成，但与其他层的问题添加调试比较测试阶段。</span><span class="sxs-lookup"><span data-stu-id="a9299-108">That is not to say it can not be done but with additional layers of difficulties added to debug compare to a testing phases.</span></span> <span data-ttu-id="a9299-109">以下可用于调试应用程序或在测试模式下的映像：</span><span class="sxs-lookup"><span data-stu-id="a9299-109">You can use the following to debug your application or image while in test mode:</span></span>

## <a name="device-portal"></a><span data-ttu-id="a9299-110">设备门户</span><span class="sxs-lookup"><span data-stu-id="a9299-110">Device Portal</span></span>
<span data-ttu-id="a9299-111">Windows Device Portal (WDP) 允许您配置和管理 IoT 设备 remoately 通过本地网络。</span><span class="sxs-lookup"><span data-stu-id="a9299-111">Windows Device Portal (WDP) allows for you to configure and manage your IoT Device remoately over local network.</span></span> <span data-ttu-id="a9299-112">WDP 可以是可通过 IoT 设备的本地 ip 访问。</span><span class="sxs-lookup"><span data-stu-id="a9299-112">WDP can be reachable via local ip of the IoT Device.</span></span> <span data-ttu-id="a9299-113">可以找到有关 IoT WDP 的其他信息[此处](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/DevicePortal)。</span><span class="sxs-lookup"><span data-stu-id="a9299-113">Additional information on WDP on IoT can be found [here](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/DevicePortal).</span></span>

### <a name="collecting-etw--wpp-logs"></a><span data-ttu-id="a9299-114">收集 ETW / WPP 日志</span><span class="sxs-lookup"><span data-stu-id="a9299-114">Collecting ETW / WPP Logs</span></span> 
-----

### <a name="file-sharing"></a><span data-ttu-id="a9299-115">文件共享</span><span class="sxs-lookup"><span data-stu-id="a9299-115">File Sharing</span></span>
<span data-ttu-id="a9299-116">应用文件资源管理器可以允许对您的应用程序可以访问的目录访问 \* 之间的所有应用共享 vCameraRoll</span><span class="sxs-lookup"><span data-stu-id="a9299-116">The App File Explorer can allow access to the directories that your apps can access \*vCameraRoll is shared among all apps</span></span>
* <span data-ttu-id="a9299-117">在所有应用之间共享文档</span><span class="sxs-lookup"><span data-stu-id="a9299-117">Documents is shared among all apps</span></span>
* <span data-ttu-id="a9299-118">LocalAppData 包含特定于每个应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a9299-118">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="a9299-119">此文件夹将为您的应用程序相同的名称和其他应用程序不能访问它。</span><span class="sxs-lookup"><span data-stu-id="a9299-119">This folder will be the same name as your app and other apps cannot access it.</span></span>
<span data-ttu-id="a9299-120">请参阅上面的链接的其他信息。</span><span class="sxs-lookup"><span data-stu-id="a9299-120">See above link for additional information.</span></span>

### <a name="kernel-debug"></a><span data-ttu-id="a9299-121">内核调试</span><span class="sxs-lookup"><span data-stu-id="a9299-121">Kernel Debug</span></span>
<span data-ttu-id="a9299-122">您可以下载实时内核转储通过 WDP 也。</span><span class="sxs-lookup"><span data-stu-id="a9299-122">You can download live Kernel dumps via WDP as well.</span></span> <span data-ttu-id="a9299-123">任何系统崩溃将自动为已登录并且可供下载。</span><span class="sxs-lookup"><span data-stu-id="a9299-123">Any system crashes will be automatically be logged and available for download.</span></span> <span data-ttu-id="a9299-124">请参阅上面的链接的其他信息。</span><span class="sxs-lookup"><span data-stu-id="a9299-124">See above link for additional information.</span></span>

### <a name="enable-crash-dump"></a><span data-ttu-id="a9299-125">启用故障转储</span><span class="sxs-lookup"><span data-stu-id="a9299-125">Enable Crash Dump</span></span>
<span data-ttu-id="a9299-126">您可以下载通过 WDP IoT 设备上的应用程序的故障转储。</span><span class="sxs-lookup"><span data-stu-id="a9299-126">You can download crash dumps of applications on IoT Device via WDP.</span></span> <span data-ttu-id="a9299-127">请参阅上面的链接的其他信息。</span><span class="sxs-lookup"><span data-stu-id="a9299-127">See above link for additional information.</span></span>

## <a name="sshpowershelltshell"></a><span data-ttu-id="a9299-128">SSH/PowerShell/TShell</span><span class="sxs-lookup"><span data-stu-id="a9299-128">SSH/PowerShell/TShell</span></span>
<span data-ttu-id="a9299-129">PowerShell 是基于任务的命令行 Shell 和脚本语言，专为进行系统管理而设计。</span><span class="sxs-lookup"><span data-stu-id="a9299-129">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span> <span data-ttu-id="a9299-130">调试和设置 powershell 的详细信息，请[此处](../connect-your-device/powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a9299-130">Details on debugging and setting up powershell can be found [here](../connect-your-device/powershell.md).</span></span>

## <a name="debug-through-visual-studio-deployment"></a><span data-ttu-id="a9299-131">通过 Visual Studio 部署调试</span><span class="sxs-lookup"><span data-stu-id="a9299-131">Debug through Visual Studio Deployment</span></span>
<span data-ttu-id="a9299-132">使用 Visual Studio 部署和调试应用程序很简单。</span><span class="sxs-lookup"><span data-stu-id="a9299-132">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="a9299-133">可以使用远程调试功能来部署和调试本地连接的 Windows 10 IoT Core 设备到应用。</span><span class="sxs-lookup"><span data-stu-id="a9299-133">Remote Debugging feature can be used to deploy and debug the app to your locally connected Windows 10 IoT Core device.</span></span> <span data-ttu-id="a9299-134">详细的部署和调试可以找到[此处](../develop-your-app/RemoteDebugging.md)。</span><span class="sxs-lookup"><span data-stu-id="a9299-134">Detailed on deployment and debugging can be found [here](../develop-your-app/RemoteDebugging.md).</span></span>

-----
## <a name="live-app-debug"></a><span data-ttu-id="a9299-135">实时应用程序调试</span><span class="sxs-lookup"><span data-stu-id="a9299-135">Live App Debug</span></span>
<span data-ttu-id="a9299-136">在 Visual Studio 中 （2015年和更高版本），可以分析性能和诊断问题在调试和在生产中，在 ASP.NET web 应用中使用来自 Azure Application Insights 的遥测数据。</span><span class="sxs-lookup"><span data-stu-id="a9299-136">In Visual Studio (2015 and later), you can analyze performance and diagnose issues in your ASP.NET web app both in debugging and in production, using telemetry from Azure Application Insights.</span></span> <span data-ttu-id="a9299-137">该功能更高版本扩展为包括桌面和 UWP 应用程序，在 Visual Studio 2017 中，通过 Azure 门户。</span><span class="sxs-lookup"><span data-stu-id="a9299-137">The feature is later extended to include desktop and UWP applications in Visual Studio 2017 and via Azure Portal.</span></span> <span data-ttu-id="a9299-138">可调试的项目的其他信息[这里](https://docs.microsoft.com/en-us/azure/azure-monitor/app/visual-studio)和监视使用情况和性能在 desktop 或 UWP 应用可将中的可以找到[此处](https://docs.microsoft.com/en-us/azure/azure-monitor/app/windows-desktop)。</span><span class="sxs-lookup"><span data-stu-id="a9299-138">Additional information on debugging your project can be found [here](https://docs.microsoft.com/en-us/azure/azure-monitor/app/visual-studio) and monitoring usage, and performance in desktop or UWP appplications can be found [here](https://docs.microsoft.com/en-us/azure/azure-monitor/app/windows-desktop).</span></span>
