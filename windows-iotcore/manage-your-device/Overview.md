---
title: 调试概述
ms.date: 05/10/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解可用于调试 Windows 10 IoT 核心版的不同方式。
keywords: windows iot，调试，调试，PowerShell，SSH
ms.openlocfilehash: e5cbea6b408540803ae5dc629e2866f6e06c17b7
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229424"
---
# <a name="debugging-on-windows-iot-core"></a><span data-ttu-id="399f3-104">调试 Windows IoT 核心</span><span class="sxs-lookup"><span data-stu-id="399f3-104">Debugging on Windows IoT Core</span></span>
<span data-ttu-id="399f3-105">使用运行中的应用程序设置 IoT 核心映像后，就必须根据需要调试应用程序或系统。</span><span class="sxs-lookup"><span data-stu-id="399f3-105">Once you have your IoT Core image setup with running application, it is important that you can debug the application, or the system as needed.</span></span> <span data-ttu-id="399f3-106">调试和测试系统的最佳时间是测试映像状态。</span><span class="sxs-lookup"><span data-stu-id="399f3-106">The best time to debug and test the system is while the test image state.</span></span> <span data-ttu-id="399f3-107">一旦基于 IoT 核心的系统出现在本质上，调试可能会变得很困难。</span><span class="sxs-lookup"><span data-stu-id="399f3-107">Once IoT Core based systems are out in the wild, debugging can become challenging.</span></span> <span data-ttu-id="399f3-108">这并不是说它无法完成，而是为了进行调试而增加了额外的问题，而与测试阶段相比。</span><span class="sxs-lookup"><span data-stu-id="399f3-108">That is not to say it cannot be done, but with additional layers of difficulties added to debug, compared to a testing phase.</span></span> <span data-ttu-id="399f3-109">在测试模式下，可以使用以下操作调试应用程序或映像：</span><span class="sxs-lookup"><span data-stu-id="399f3-109">You can use the following to debug your application or image while in test mode:</span></span>

## <a name="device-portal"></a><span data-ttu-id="399f3-110">设备门户</span><span class="sxs-lookup"><span data-stu-id="399f3-110">Device Portal</span></span>
<span data-ttu-id="399f3-111">Windows设备门户 (WDP) 使你可以通过本地网络远程配置和管理 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="399f3-111">Windows Device Portal (WDP) allows for you to configure and manage your IoT Device remotely over local network.</span></span> <span data-ttu-id="399f3-112">可以通过 IoT 设备的本地 IP 来访问 WDP。</span><span class="sxs-lookup"><span data-stu-id="399f3-112">WDP can be reachable via local IP of the IoT Device.</span></span> <span data-ttu-id="399f3-113">有关 IoT 上的 WDP 的其他信息，请参阅 [此处](https://docs.microsoft.com/windows/iot-core/manage-your-device/DevicePortal)。</span><span class="sxs-lookup"><span data-stu-id="399f3-113">Additional information on WDP on IoT can be found [here](https://docs.microsoft.com/windows/iot-core/manage-your-device/DevicePortal).</span></span>

### <a name="collecting-etw--wpp-logs"></a><span data-ttu-id="399f3-114">收集 ETW/WPP 日志</span><span class="sxs-lookup"><span data-stu-id="399f3-114">Collecting ETW / WPP Logs</span></span>
-----

### <a name="file-sharing"></a><span data-ttu-id="399f3-115">文件共享</span><span class="sxs-lookup"><span data-stu-id="399f3-115">File Sharing</span></span>
<span data-ttu-id="399f3-116">应用文件资源管理器可允许访问你的应用可以访问的目录 \* vCameraRoll 在所有应用之间共享</span><span class="sxs-lookup"><span data-stu-id="399f3-116">The App File Explorer can allow access to the directories that your apps can access \*vCameraRoll is shared among all apps</span></span>
* <span data-ttu-id="399f3-117">文档在所有应用中共享</span><span class="sxs-lookup"><span data-stu-id="399f3-117">Documents are shared among all apps</span></span>
* <span data-ttu-id="399f3-118">LocalAppData 包含特定于每个应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="399f3-118">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="399f3-119">此文件夹将与你的应用同名，并且其他应用无法访问该文件夹。</span><span class="sxs-lookup"><span data-stu-id="399f3-119">This folder will be the same name as your app and other apps cannot access it.</span></span>
<span data-ttu-id="399f3-120">有关其他信息，请参阅上面的链接。</span><span class="sxs-lookup"><span data-stu-id="399f3-120">See above link for additional information.</span></span>

### <a name="kernel-debug"></a><span data-ttu-id="399f3-121">内核调试</span><span class="sxs-lookup"><span data-stu-id="399f3-121">Kernel Debug</span></span>
<span data-ttu-id="399f3-122">还可以通过 WDP 下载实时内核转储。</span><span class="sxs-lookup"><span data-stu-id="399f3-122">You can download live Kernel dumps via WDP as well.</span></span> <span data-ttu-id="399f3-123">系统将自动记录任何系统崩溃并可供下载。</span><span class="sxs-lookup"><span data-stu-id="399f3-123">Any system crashes will automatically be logged and available for download.</span></span> <span data-ttu-id="399f3-124">有关其他信息，请参阅上面的链接。</span><span class="sxs-lookup"><span data-stu-id="399f3-124">See above link for additional information.</span></span>

### <a name="enable-crash-dump"></a><span data-ttu-id="399f3-125">启用故障转储</span><span class="sxs-lookup"><span data-stu-id="399f3-125">Enable Crash Dump</span></span>
<span data-ttu-id="399f3-126">可以通过 WDP 在 IoT 设备上下载应用程序的故障转储。</span><span class="sxs-lookup"><span data-stu-id="399f3-126">You can download crash dumps of applications on IoT Device via WDP.</span></span> <span data-ttu-id="399f3-127">有关其他信息，请参阅上面的链接。</span><span class="sxs-lookup"><span data-stu-id="399f3-127">See above link for additional information.</span></span>

## <a name="sshpowershelltshell"></a><span data-ttu-id="399f3-128">SSH/PowerShell/TShell</span><span class="sxs-lookup"><span data-stu-id="399f3-128">SSH/PowerShell/TShell</span></span>
<span data-ttu-id="399f3-129">PowerShell 是一种基于任务的命令行 shell 和脚本语言，专为系统管理而设计。</span><span class="sxs-lookup"><span data-stu-id="399f3-129">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span> <span data-ttu-id="399f3-130">可在 [此处](../connect-your-device/powershell.md)找到有关调试和设置 PowerShell 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="399f3-130">Details on debugging and setting up PowerShell can be found [here](../connect-your-device/powershell.md).</span></span>

## <a name="debug-through-visual-studio-deployment"></a><span data-ttu-id="399f3-131">通过 Visual Studio 部署进行调试</span><span class="sxs-lookup"><span data-stu-id="399f3-131">Debug through Visual Studio Deployment</span></span>
<span data-ttu-id="399f3-132">部署和调试应用程序非常简单，Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="399f3-132">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="399f3-133">远程调试功能可用于将应用部署并调试到本地连接 Windows 10 IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="399f3-133">Remote Debugging feature can be used to deploy and debug the app to your locally connected Windows 10 IoT Core device.</span></span> <span data-ttu-id="399f3-134">有关部署和调试的详细信息，请参阅 [此处](../develop-your-app/RemoteDebugging.md)。</span><span class="sxs-lookup"><span data-stu-id="399f3-134">Details on deployment and debugging can be found [here](../develop-your-app/RemoteDebugging.md).</span></span>

-----
## <a name="live-app-debug"></a><span data-ttu-id="399f3-135">实时应用调试</span><span class="sxs-lookup"><span data-stu-id="399f3-135">Live App Debug</span></span>
<span data-ttu-id="399f3-136">在 Visual Studio（2015 和更高版本）中，可以使用来自 Azure Application Insights 的遥测，在调试和生产环境中分析 ASP.NET Web 应用中的性能和诊断问题。</span><span class="sxs-lookup"><span data-stu-id="399f3-136">In Visual Studio (2015 and later), you can analyze performance and diagnose issues in your ASP.NET web app both in debugging and in production, using telemetry from Azure Application Insights.</span></span> <span data-ttu-id="399f3-137">此功能在以后扩展，以在 Visual Studio 2017 和通过 Azure 门户中包括桌面和 UWP 应用程序。</span><span class="sxs-lookup"><span data-stu-id="399f3-137">The feature is later extended to include desktop and UWP applications in Visual Studio 2017 and via Azure portal.</span></span> <span data-ttu-id="399f3-138">有关调试项目的其他信息，请参阅 [此处](https://docs.microsoft.com/azure/azure-monitor/app/visual-studio) 和监视使用情况，可以在 [此处](https://docs.microsoft.com/azure/azure-monitor/app/windows-desktop)找到桌面或 UWP 应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="399f3-138">Additional information on debugging your project can be found [here](https://docs.microsoft.com/azure/azure-monitor/app/visual-studio) and monitoring usage, and performance in desktop or UWP applications can be found [here](https://docs.microsoft.com/azure/azure-monitor/app/windows-desktop).</span></span>
