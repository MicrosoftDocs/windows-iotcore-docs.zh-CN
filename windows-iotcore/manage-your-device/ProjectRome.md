---
title: 将 Project 罗马用于 Windows 10 IoT Core
ms.date: 11/14/2017
ms.topic: article
description: 了解并了解将 Windows IoT 设备投放市场的步骤。
keywords: windows 10 IoT Core、Project 罗马、远程设备
ms.openlocfilehash: dcf1ba9bec776b2ebde0d374266bb4d7dba3baec
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917323"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a><span data-ttu-id="e17f0-104">将 Project 罗马用于 Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="e17f0-104">Using Project Rome with Windows 10 IoT Core</span></span> 
 
<span data-ttu-id="e17f0-105">使用[Project 罗马](https://developer.microsoft.com/en-us/windows/project-rome)，可以通过 RemoteSystems 和 AppServiceProvider api 与运行 Windows 10 IoT Core 的设备进行远程工作。</span><span class="sxs-lookup"><span data-stu-id="e17f0-105">[Project Rome](https://developer.microsoft.com/en-us/windows/project-rome) allows you to work remotely with devices running Windows 10 IoT Core using the RemoteSystems and AppServiceProvider APIs.</span></span> 
 
<span data-ttu-id="e17f0-106">在本文中，我们将介绍如何使用 Project 罗马发现、控制和连接运行 Windows 10 IoT Core 的设备。</span><span class="sxs-lookup"><span data-stu-id="e17f0-106">In this article, we'll go through how to discover, control, and connect to devices running Windows 10 IoT Core with Project Rome.</span></span>  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a><span data-ttu-id="e17f0-107">通过 RemoteSystem Api 查找 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="e17f0-107">Discovering IoT Core devices with the RemoteSystem APIs</span></span> 
 
<span data-ttu-id="e17f0-108">_程序_</span><span class="sxs-lookup"><span data-stu-id="e17f0-108">_Setup:_</span></span>
* <span data-ttu-id="e17f0-109">登录到 Microsoft 帐户时，请在桌面上运行 RemoteSystems 示例。</span><span class="sxs-lookup"><span data-stu-id="e17f0-109">Run the RemoteSystems sample on a Desktop while signed into your Microsoft account.</span></span>  
* <span data-ttu-id="e17f0-110">如果未在 IoT Core 上运行任何应用，请转到 Cortana 登录到你的 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="e17f0-110">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
<span data-ttu-id="e17f0-111">_逐步_</span><span class="sxs-lookup"><span data-stu-id="e17f0-111">_Steps:_</span></span>
1. <span data-ttu-id="e17f0-112">在桌面上运行 RemoteSystems 示例</span><span class="sxs-lookup"><span data-stu-id="e17f0-112">Run the RemoteSystems sample on your desktop</span></span> 
2. <span data-ttu-id="e17f0-113">在 "1）发现" 下，单击 "搜索系统"</span><span class="sxs-lookup"><span data-stu-id="e17f0-113">Under "1) Discovery," click "Search for systems"</span></span> 

![搜索系统](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a><span data-ttu-id="e17f0-115">控制包含 RemoteSystems 的 IoT 核心设备。 LaunchUri</span><span class="sxs-lookup"><span data-stu-id="e17f0-115">Control IoT Core devices with RemoteSystems.LaunchUri</span></span> 
 
<span data-ttu-id="e17f0-116">_程序_</span><span class="sxs-lookup"><span data-stu-id="e17f0-116">_Setup:_</span></span>
* <span data-ttu-id="e17f0-117">[登录到 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)时，请在桌面上运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)。</span><span class="sxs-lookup"><span data-stu-id="e17f0-117">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span>
* <span data-ttu-id="e17f0-118">如果未在 IoT Core 上运行任何应用，请转到 Cortana 登录到你的 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="e17f0-118">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
<span data-ttu-id="e17f0-119">_逐步_</span><span class="sxs-lookup"><span data-stu-id="e17f0-119">_Steps:_</span></span>
1. <span data-ttu-id="e17f0-120">打开包含 Cortana 的 IoT Core 虚拟机，并从 Cortana 登录到你的 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="e17f0-120">Turn on the IoT Core virtual machine with Cortana and sign into your Microsoft account from Cortana.</span></span> 
2. <span data-ttu-id="e17f0-121">在桌面上运行 RemoteSystems 示例。</span><span class="sxs-lookup"><span data-stu-id="e17f0-121">Run the RemoteSystems sample on Desktop.</span></span> 
3. <span data-ttu-id="e17f0-122">在 "1）发现" 下，单击 "搜索系统"。</span><span class="sxs-lookup"><span data-stu-id="e17f0-122">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="e17f0-123">在 "2）启动 URI" 下，选择运行 Cortana 的 IoT 核心设备。</span><span class="sxs-lookup"><span data-stu-id="e17f0-123">Under "2) Launch URI", select the IoT Core device that is running Cortana.</span></span> 
5. <span data-ttu-id="e17f0-124">输入此 URI，然后启动。</span><span class="sxs-lookup"><span data-stu-id="e17f0-124">Enter this URI and launch.</span></span> 

![启动 URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a><span data-ttu-id="e17f0-126">连接到在 IoT Core 上运行的远程应用服务</span><span class="sxs-lookup"><span data-stu-id="e17f0-126">Connecting to the Remote App Service running on IoT Core</span></span> 
<span data-ttu-id="e17f0-127">_程序_</span><span class="sxs-lookup"><span data-stu-id="e17f0-127">_Setup:_</span></span>
* <span data-ttu-id="e17f0-128">[登录到 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)时，请在桌面上运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)。</span><span class="sxs-lookup"><span data-stu-id="e17f0-128">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span> 
* <span data-ttu-id="e17f0-129">请确保已在至少一个 IoT Core 设备上部署并运行[AppServiceProvider 应用](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices)。</span><span class="sxs-lookup"><span data-stu-id="e17f0-129">Make sure to have the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and running on at least one IoT Core device.</span></span> 
 
<span data-ttu-id="e17f0-130">_逐步_</span><span class="sxs-lookup"><span data-stu-id="e17f0-130">_Steps:_</span></span>
1. <span data-ttu-id="e17f0-131">打开包含 Cortana 的 IoT 核心虚拟机，并登录到 Cortana 中的 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="e17f0-131">Turn on the IoT Core Virtual Machine with Cortana, and sign into your Microsoft account from Cortana.</span></span> <span data-ttu-id="e17f0-132">部署 AppServiceProvider 应用，只运行一次，然后将其关闭。</span><span class="sxs-lookup"><span data-stu-id="e17f0-132">Deploy the AppServiceProvider app, run it once, then shut it down.</span></span> 
2. <span data-ttu-id="e17f0-133">在桌面上运行 RemoteSystems 示例。</span><span class="sxs-lookup"><span data-stu-id="e17f0-133">Run the RemoteSystems sample on desktop.</span></span> 
3. <span data-ttu-id="e17f0-134">在 "1）发现" 下，单击 "搜索系统"。</span><span class="sxs-lookup"><span data-stu-id="e17f0-134">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="e17f0-135">在 "3）启动应用服务" 下，选择已部署并已运行 AppServiceProvider 应用的 IoT core 设备。</span><span class="sxs-lookup"><span data-stu-id="e17f0-135">Under "3) Launch App Services," select the IoT core device that has the AppServiceProvider app deployed and has been run previously.</span></span> 
5. <span data-ttu-id="e17f0-136">生成一个随机数。</span><span class="sxs-lookup"><span data-stu-id="e17f0-136">Generate a random number.</span></span>  

![启动应用服务](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a><span data-ttu-id="e17f0-138">从 IoT Core 设备控制其他设备和应用服务</span><span class="sxs-lookup"><span data-stu-id="e17f0-138">Controlling other devices and app services from an IoT Core device</span></span> 

<span data-ttu-id="e17f0-139">_程序_</span><span class="sxs-lookup"><span data-stu-id="e17f0-139">_Setup:_</span></span>
* <span data-ttu-id="e17f0-140">从 Cortana 应用中[登录到 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)时，运行在 IoT Core 设备上部署的[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)。</span><span class="sxs-lookup"><span data-stu-id="e17f0-140">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) deployed on an IoT Core device while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) from the Cortana app.</span></span> 
* <span data-ttu-id="e17f0-141">已部署[AppServiceProvider 应用](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices)且至少运行一次的台式计算机。</span><span class="sxs-lookup"><span data-stu-id="e17f0-141">Have a desktop machine with the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and having been run at least once.</span></span> 
 
<span data-ttu-id="e17f0-142">_逐步_</span><span class="sxs-lookup"><span data-stu-id="e17f0-142">_Steps:_</span></span>
1. <span data-ttu-id="e17f0-143">运行 RemoteSystems 示例。</span><span class="sxs-lookup"><span data-stu-id="e17f0-143">Run the RemoteSystems sample.</span></span> 
2. <span data-ttu-id="e17f0-144">在 "1）发现" 下，单击 "搜索系统"。</span><span class="sxs-lookup"><span data-stu-id="e17f0-144">Under "1) Discovery", click on "Search for systems".</span></span> 
3. <span data-ttu-id="e17f0-145">在 "2）启动 URI" 下，选择桌面计算机，然后启动。</span><span class="sxs-lookup"><span data-stu-id="e17f0-145">Under "2) Launch URI", select the Desktop machine and launch.</span></span> 
4. <span data-ttu-id="e17f0-146">在 "3）启动应用服务" 下，选择桌面计算机。</span><span class="sxs-lookup"><span data-stu-id="e17f0-146">Under "3) Launch App Services", select the desktop machine.</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="e17f0-147">第一次尝试时，这可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="e17f0-147">On first attempt, this may take a long time.</span></span> <span data-ttu-id="e17f0-148">再次尝试此重试以获得更快的响应。</span><span class="sxs-lookup"><span data-stu-id="e17f0-148">Try this again for a much quicker response.</span></span> 
 
### <a name="helpful-links"></a><span data-ttu-id="e17f0-149">有用的链接：</span><span class="sxs-lookup"><span data-stu-id="e17f0-149">Helpful links:</span></span> 
* [<span data-ttu-id="e17f0-150">MSDN 上的项目罗马文档</span><span class="sxs-lookup"><span data-stu-id="e17f0-150">Project Rome documentation on MSDN</span></span>](https://developer.microsoft.com/en-us/windows/project-rome )
* [<span data-ttu-id="e17f0-151">对 UWP 使用 Project 罗马</span><span class="sxs-lookup"><span data-stu-id="e17f0-151">Using Project Rome for UWP</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
