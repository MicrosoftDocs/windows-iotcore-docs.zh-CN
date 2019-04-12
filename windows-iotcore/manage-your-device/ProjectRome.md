---
title: 使用 Windows 10 IoT 核心版项目罗马
author: saraclay
ms.author: saclayt
ms.date: 11/14/2017
ms.topic: article
description: 了解并了解要执行 Windows IoT 设备推向市场的步骤。
keywords: windows 10 IoT Core，项目罗马，远程设备
ms.openlocfilehash: cc016abad05dd54c7b948bcae8120b6da1724ee0
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59511018"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a><span data-ttu-id="b1f19-104">使用 Windows 10 IoT 核心版项目罗马</span><span class="sxs-lookup"><span data-stu-id="b1f19-104">Using Project Rome with Windows 10 IoT Core</span></span> 
 
<span data-ttu-id="b1f19-105">[项目罗马](https://developer.microsoft.com/en-us/windows/project-rome)，可远程使用运行 Windows 10 IoT 核心版 RemoteSystems 和 AppServiceProvider Api 使用的设备。</span><span class="sxs-lookup"><span data-stu-id="b1f19-105">[Project Rome](https://developer.microsoft.com/en-us/windows/project-rome) allows you to work remotely with devices running Windows 10 IoT Core using the RemoteSystems and AppServiceProvider APIs.</span></span> 
 
<span data-ttu-id="b1f19-106">在本文中，我们将逐一介绍如何发现，控件，并连接到与项目罗马运行 Windows 10 IoT 核心版的设备。</span><span class="sxs-lookup"><span data-stu-id="b1f19-106">In this article, we'll go through how to discover, control, and connect to devices running Windows 10 IoT Core with Project Rome.</span></span>  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a><span data-ttu-id="b1f19-107">发现与 RemoteSystem Api IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="b1f19-107">Discovering IoT Core devices with the RemoteSystem APIs</span></span> 
 
_<span data-ttu-id="b1f19-108">安装：</span><span class="sxs-lookup"><span data-stu-id="b1f19-108">Setup:</span></span>_
* <span data-ttu-id="b1f19-109">在桌面上到你的 Microsoft 帐户登录时运行 RemoteSystems 示例。</span><span class="sxs-lookup"><span data-stu-id="b1f19-109">Run the RemoteSystems sample on a Desktop while signed into your Microsoft account.</span></span>  
* <span data-ttu-id="b1f19-110">与任何 IoT Core 上运行的应用，登录到你的 Microsoft 帐户上通过转到 Cortana 到登录名。</span><span class="sxs-lookup"><span data-stu-id="b1f19-110">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
_<span data-ttu-id="b1f19-111">步骤：</span><span class="sxs-lookup"><span data-stu-id="b1f19-111">Steps:</span></span>_
1. <span data-ttu-id="b1f19-112">在您的桌面上运行 RemoteSystems 示例</span><span class="sxs-lookup"><span data-stu-id="b1f19-112">Run the RemoteSystems sample on your desktop</span></span> 
2. <span data-ttu-id="b1f19-113">"1） 发现，"下单击"搜索系统"</span><span class="sxs-lookup"><span data-stu-id="b1f19-113">Under "1) Discovery," click "Search for systems"</span></span> 

![搜索系统](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a><span data-ttu-id="b1f19-115">控制与 RemoteSystems.LaunchUri IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="b1f19-115">Control IoT Core devices with RemoteSystems.LaunchUri</span></span> 
 
_<span data-ttu-id="b1f19-116">安装：</span><span class="sxs-lookup"><span data-stu-id="b1f19-116">Setup:</span></span>_
* <span data-ttu-id="b1f19-117">运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)上桌面 while[登录到你的 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)。</span><span class="sxs-lookup"><span data-stu-id="b1f19-117">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span>
* <span data-ttu-id="b1f19-118">与任何 IoT Core 上运行的应用，登录到你的 Microsoft 帐户上通过转到 Cortana 到登录名。</span><span class="sxs-lookup"><span data-stu-id="b1f19-118">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
_<span data-ttu-id="b1f19-119">步骤：</span><span class="sxs-lookup"><span data-stu-id="b1f19-119">Steps:</span></span>_
1. <span data-ttu-id="b1f19-120">打开 Cortana 并登录到你的 Microsoft 帐户从 Cortana IoT 核心版虚拟机。</span><span class="sxs-lookup"><span data-stu-id="b1f19-120">Turn on the IoT Core virtual machine with Cortana and sign into your Microsoft account from Cortana.</span></span> 
2. <span data-ttu-id="b1f19-121">在桌面上运行 RemoteSystems 示例。</span><span class="sxs-lookup"><span data-stu-id="b1f19-121">Run the RemoteSystems sample on Desktop.</span></span> 
3. <span data-ttu-id="b1f19-122">在"1） 发现"，单击"搜索系统"。</span><span class="sxs-lookup"><span data-stu-id="b1f19-122">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="b1f19-123">在"2） 启动 URI"，选择正在运行 Cortana 的 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="b1f19-123">Under "2) Launch URI", select the IoT Core device that is running Cortana.</span></span> 
5. <span data-ttu-id="b1f19-124">输入此 URI 并启动。</span><span class="sxs-lookup"><span data-stu-id="b1f19-124">Enter this URI and launch.</span></span> 

![启动 URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a><span data-ttu-id="b1f19-126">连接到 IoT Core 上运行的远程应用程序服务</span><span class="sxs-lookup"><span data-stu-id="b1f19-126">Connecting to the Remote App Service running on IoT Core</span></span> 
_<span data-ttu-id="b1f19-127">安装：</span><span class="sxs-lookup"><span data-stu-id="b1f19-127">Setup:</span></span>_
* <span data-ttu-id="b1f19-128">运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)上桌面 while[登录到你的 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)。</span><span class="sxs-lookup"><span data-stu-id="b1f19-128">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span> 
* <span data-ttu-id="b1f19-129">请确保有[AppServiceProvider 应用](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices)部署且至少一个 IoT Core 设备上正在运行。</span><span class="sxs-lookup"><span data-stu-id="b1f19-129">Make sure to have the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and running on at least one IoT Core device.</span></span> 
 
_<span data-ttu-id="b1f19-130">步骤：</span><span class="sxs-lookup"><span data-stu-id="b1f19-130">Steps:</span></span>_
1. <span data-ttu-id="b1f19-131">打开 IoT Core 虚拟机上与 Cortana，并登录到 Microsoft 帐户从 Cortana。</span><span class="sxs-lookup"><span data-stu-id="b1f19-131">Turn on the IoT Core Virtual Machine with Cortana, and sign into your Microsoft account from Cortana.</span></span> <span data-ttu-id="b1f19-132">AppServiceProvider 应用部署，运行一次，然后将其关闭。</span><span class="sxs-lookup"><span data-stu-id="b1f19-132">Deploy the AppServiceProvider app, run it once, then shut it down.</span></span> 
2. <span data-ttu-id="b1f19-133">在桌面上运行 RemoteSystems 示例。</span><span class="sxs-lookup"><span data-stu-id="b1f19-133">Run the RemoteSystems sample on desktop.</span></span> 
3. <span data-ttu-id="b1f19-134">在"1） 发现"，单击"搜索系统"。</span><span class="sxs-lookup"><span data-stu-id="b1f19-134">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="b1f19-135">在"3） 启动应用服务、"选择 IoT core 设备具有部署的 AppServiceProvider 应用并且已运行。</span><span class="sxs-lookup"><span data-stu-id="b1f19-135">Under "3) Launch App Services," select the IoT core device that has the AppServiceProvider app deployed and has been run previously.</span></span> 
5. <span data-ttu-id="b1f19-136">生成一个随机数。</span><span class="sxs-lookup"><span data-stu-id="b1f19-136">Generate a random number.</span></span>  

![启动应用服务](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a><span data-ttu-id="b1f19-138">控制其他设备和应用程序服务从 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="b1f19-138">Controlling other devices and app services from an IoT Core device</span></span> 

_<span data-ttu-id="b1f19-139">安装：</span><span class="sxs-lookup"><span data-stu-id="b1f19-139">Setup:</span></span>_
* <span data-ttu-id="b1f19-140">运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)同时 IoT Core 设备上部署[登录到你的 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)从 Cortana 应用。</span><span class="sxs-lookup"><span data-stu-id="b1f19-140">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) deployed on an IoT Core device while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) from the Cortana app.</span></span> 
* <span data-ttu-id="b1f19-141">桌面计算机有[AppServiceProvider 应用](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices)部署并且具有运行至少一次。</span><span class="sxs-lookup"><span data-stu-id="b1f19-141">Have a desktop machine with the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and having been run at least once.</span></span> 
 
_<span data-ttu-id="b1f19-142">步骤：</span><span class="sxs-lookup"><span data-stu-id="b1f19-142">Steps:</span></span>_
1. <span data-ttu-id="b1f19-143">运行 RemoteSystems 示例。</span><span class="sxs-lookup"><span data-stu-id="b1f19-143">Run the RemoteSystems sample.</span></span> 
2. <span data-ttu-id="b1f19-144">在"1） 发现"，单击"搜索系统"。</span><span class="sxs-lookup"><span data-stu-id="b1f19-144">Under "1) Discovery", click on "Search for systems".</span></span> 
3. <span data-ttu-id="b1f19-145">在"2） 启动 URI"，选择桌面计算机并启动。</span><span class="sxs-lookup"><span data-stu-id="b1f19-145">Under "2) Launch URI", select the Desktop machine and launch.</span></span> 
4. <span data-ttu-id="b1f19-146">在"3） 启动应用服务"下选择的桌面机。</span><span class="sxs-lookup"><span data-stu-id="b1f19-146">Under "3) Launch App Services", select the desktop machine.</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="b1f19-147">第一次尝试，这可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="b1f19-147">On first attempt, this may take a long time.</span></span> <span data-ttu-id="b1f19-148">这再试一次更快响应。</span><span class="sxs-lookup"><span data-stu-id="b1f19-148">Try this again for a much quicker response.</span></span> 
 
### <a name="helpful-links"></a><span data-ttu-id="b1f19-149">有用的链接：</span><span class="sxs-lookup"><span data-stu-id="b1f19-149">Helpful links:</span></span> 
* [<span data-ttu-id="b1f19-150">MSDN 上的项目罗马文档</span><span class="sxs-lookup"><span data-stu-id="b1f19-150">Project Rome documentation on MSDN</span></span>](https://developer.microsoft.com/en-us/windows/project-rome )
* [<span data-ttu-id="b1f19-151">使用适用于 UWP 项目罗马</span><span class="sxs-lookup"><span data-stu-id="b1f19-151">Using Project Rome for UWP</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
