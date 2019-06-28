---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解有关如何使用 Windows Device Portal 若要配置和远程管理你的设备。
keywords: windows iot、 Windows Device Portal，远程，设备门户
ms.openlocfilehash: 8e430365ea09509f5638d86ac77b151226df488f
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412154"
---
# <a name="windows-device-portal"></a><span data-ttu-id="11ceb-104">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="11ceb-104">Windows Device Portal</span></span>
   <span data-ttu-id="11ceb-105">Windows Device Portal (WDP) 允许您配置和通过本地网络的远程管理你的设备。</span><span class="sxs-lookup"><span data-stu-id="11ceb-105">The Windows Device Portal (WDP) lets you configure and manage your device remotely over your local network.</span></span>
<span data-ttu-id="11ceb-106">主要功能已记录在[Windows Device Portal 概述页](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="11ceb-106">The main features are documented on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

![Device Portal 主页](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> <span data-ttu-id="11ceb-108">请勿将创客映像用于商业化。</span><span class="sxs-lookup"><span data-stu-id="11ceb-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="11ceb-109">若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。</span><span class="sxs-lookup"><span data-stu-id="11ceb-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="11ceb-110">在[此处](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="11ceb-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!WARNING]
> <span data-ttu-id="11ceb-111">实时内核调试目前适用于 ARM 设备将失败。</span><span class="sxs-lookup"><span data-stu-id="11ceb-111">Live kernel debug is currently failing for ARM devices.</span></span> <span data-ttu-id="11ceb-112">我们正在努力获得修复此问题。</span><span class="sxs-lookup"><span data-stu-id="11ceb-112">We are working to get this fixed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11ceb-113">如果您正在构建商业上部署的"特定于/受限安装"将打开零售设备 （即工厂或零售商店） 的最终用户执行最终配置和文档客户，他们必须[获取它同时 WDP 和连接的浏览器和密码时更改 WDP WDP 和安装证书](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)，则此窄的商业实例中使用 WDP 是可接受。</span><span class="sxs-lookup"><span data-stu-id="11ceb-113">If you are building an open retail device for commercial deployment to a "specific/limited installation" (i.e. factory or retail store) where the end-user does the final configuration and you document your customers that they must [obtain a certificate for WDP and install it on both WDP and connecting browsers and passwords are changed on WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), then using WDP in this narrow commercial instance is acceptable.</span></span> <span data-ttu-id="11ceb-114">在此方案中的零售映像也应仍然*不*包括 IOT_TOOLKIT，但应使用 IOT_WEBBEXTN 包 WDP 拉取。</span><span class="sxs-lookup"><span data-stu-id="11ceb-114">Retail images in this scenario should still *not* include IOT_TOOLKIT, but should use the IOT_WEBBEXTN package to pull in WDP.</span></span> 

## <a name="shared-documentation"></a><span data-ttu-id="11ceb-115">共享的文档</span><span class="sxs-lookup"><span data-stu-id="11ceb-115">Shared Documentation</span></span>
<span data-ttu-id="11ceb-116">WDP 是在所有 Windows 10 设备之间共享的开发人员工具。</span><span class="sxs-lookup"><span data-stu-id="11ceb-116">WDP is a developer tool shared among all Windows 10 devices.</span></span> <span data-ttu-id="11ceb-117">每个产品都有其自己独特的功能，但核心功能是相同的。</span><span class="sxs-lookup"><span data-stu-id="11ceb-117">Each product has its own unique features, but the core functionality is the same.</span></span>
<span data-ttu-id="11ceb-118">上找到有关的主要功能的文档[Windows Device Portal 概述页](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)。</span><span class="sxs-lookup"><span data-stu-id="11ceb-118">Documentation for the main features are found on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span> <span data-ttu-id="11ceb-119">以下文档的其余部分将特定的 IoT。</span><span class="sxs-lookup"><span data-stu-id="11ceb-119">The rest of the documentation below will be IoT specific.</span></span>

## <a name="set-up"></a><span data-ttu-id="11ceb-120">设置</span><span class="sxs-lookup"><span data-stu-id="11ceb-120">Set up</span></span>

<span data-ttu-id="11ceb-121">有两种方法可获取 Windows Device Portal，启动并运行。</span><span class="sxs-lookup"><span data-stu-id="11ceb-121">There are two ways to go get the Windows Device Portal up and running.</span></span>

### <a name="1-windows-10-iot-dashboard"></a><span data-ttu-id="11ceb-122">1.Windows 10 IoT 仪表板</span><span class="sxs-lookup"><span data-stu-id="11ceb-122">1. Windows 10 IoT Dashboard</span></span>

<span data-ttu-id="11ceb-123">首先，你将想要下载[Windows 10 IoT 仪表板](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)，可以轻松地设置新设备的开发人员工具。</span><span class="sxs-lookup"><span data-stu-id="11ceb-123">First, you'll want to download the [Windows 10 IoT Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), a developer tool that makes it easy to set up new devices.</span></span> <span data-ttu-id="11ceb-124">一旦您使用仪表板闪烁的 Windows 10 IoT 核心版映像，到你的设备上，检查，你的设备显示在"我的设备"。</span><span class="sxs-lookup"><span data-stu-id="11ceb-124">Once you've used the Dashboard to flash a Windows 10 IoT Core image onto your device, check that your device shows up under "My devices".</span></span> 

<span data-ttu-id="11ceb-125">在这里，使用省略号"操作"下的选择"打开在设备门户"。</span><span class="sxs-lookup"><span data-stu-id="11ceb-125">From there, use the ellipses under "Actions" to select "Open in Device Portal".</span></span> <span data-ttu-id="11ceb-126">在这里，你将转到设备门户身份验证页面，除非最初更改凭据，否则默认凭据是：</span><span class="sxs-lookup"><span data-stu-id="11ceb-126">From there, you'll be taken to the Device Portal authentication page where, unless you changed the credentials initially, the default credentials are:</span></span> 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a><span data-ttu-id="11ceb-127">2.浏览器</span><span class="sxs-lookup"><span data-stu-id="11ceb-127">2. Browser</span></span>
<span data-ttu-id="11ceb-128">如果您不能在仪表板中找到你的设备或更想跳过使用仪表板，还可以通过输入加上你设备的 IP 地址打开设备门户`:8080`到末尾。</span><span class="sxs-lookup"><span data-stu-id="11ceb-128">If you cannot find your device in the dashboard or prefer to skip using the dashboard, you can also open the Device Portal by entering the IP address of your device plus `:8080` onto the end.</span></span> <span data-ttu-id="11ceb-129">如果操作无误，它应如下所示：</span><span class="sxs-lookup"><span data-stu-id="11ceb-129">When done correctly, it should look something like this:</span></span>


   ![IoTDashboard 查看设备](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a><span data-ttu-id="11ceb-131">IoT 特定功能</span><span class="sxs-lookup"><span data-stu-id="11ceb-131">IoT specific features</span></span>

### <a name="device-settings"></a><span data-ttu-id="11ceb-132">设备设置</span><span class="sxs-lookup"><span data-stu-id="11ceb-132">Device Settings</span></span>

<span data-ttu-id="11ceb-133">IoT 核心版将添加一个复选框以启用或禁用[屏幕键盘](../develop-your-app/OnScreenKeyboard.md)</span><span class="sxs-lookup"><span data-stu-id="11ceb-133">IoT Core adds a checkbox to enable or disable the [on-screen keyboard](../develop-your-app/OnScreenKeyboard.md)</span></span>
> [!NOTE]
> <span data-ttu-id="11ceb-134">此复选框都有一个已知的 bug，它将"闪烁"从检查到非检查。</span><span class="sxs-lookup"><span data-stu-id="11ceb-134">This checkbox has a known bug where it will "flash" from checked to non-checked.</span></span> <span data-ttu-id="11ceb-135">请单击以确保复选框将显示你所需的状态后，刷新页面 (F5)。</span><span class="sxs-lookup"><span data-stu-id="11ceb-135">Please refresh the page (F5) after clicking to ensure that the checkbox is showing your desired state.</span></span>

### <a name="apps"></a><span data-ttu-id="11ceb-136">应用</span><span class="sxs-lookup"><span data-stu-id="11ceb-136">Apps</span></span>
<span data-ttu-id="11ceb-137">为设备上的 AppX 程序包和捆绑包提供安装/卸载功能。</span><span class="sxs-lookup"><span data-stu-id="11ceb-137">Provides install/uninstall functionality for AppX packages and bundles on your device.</span></span>
<span data-ttu-id="11ceb-138">![应用列表](../media/DevicePortal/AppList.png)</span><span class="sxs-lookup"><span data-stu-id="11ceb-138">![App list](../media/DevicePortal/AppList.png)</span></span>

<span data-ttu-id="11ceb-139">IoT Core 是唯一的因为它只允许一个前台应用程序运行一次。</span><span class="sxs-lookup"><span data-stu-id="11ceb-139">IoT Core is unique in that it only allows one foreground app to run at one time.</span></span> <span data-ttu-id="11ceb-140">修改应用程序列表，以确保这种情况。</span><span class="sxs-lookup"><span data-stu-id="11ceb-140">The app list is modified to ensure that this is the case.</span></span> <span data-ttu-id="11ceb-141">下**启动**列中，您可以选择任意多个后台应用程序启动默认情况下，但只能设置一个前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="11ceb-141">Under the **STARTUP** column, you can select as many background applications to start by default, but can only set one foreground application.</span></span>  

### <a name="app-file-explorer"></a><span data-ttu-id="11ceb-142">应用文件资源管理器</span><span class="sxs-lookup"><span data-stu-id="11ceb-142">App File Explorer</span></span>

<span data-ttu-id="11ceb-143">应用文件资源管理器显示的目录，可以访问您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="11ceb-143">The app file explorer shows the directories that your apps can access.</span></span>

* <span data-ttu-id="11ceb-144">在所有应用之间共享 CameraRoll</span><span class="sxs-lookup"><span data-stu-id="11ceb-144">CameraRoll is shared among all apps</span></span>
* <span data-ttu-id="11ceb-145">在所有应用之间共享文档</span><span class="sxs-lookup"><span data-stu-id="11ceb-145">Documents is shared among all apps</span></span>
* <span data-ttu-id="11ceb-146">LocalAppData 包含特定于每个应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="11ceb-146">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="11ceb-147">此文件夹将为您的应用程序相同的名称和其他应用程序不能访问它。</span><span class="sxs-lookup"><span data-stu-id="11ceb-147">This folder will be the same name as your app and other apps cannot access it.</span></span>

### <a name="debugging"></a><span data-ttu-id="11ceb-148">调试</span><span class="sxs-lookup"><span data-stu-id="11ceb-148">Debugging</span></span>

#### <a name="kernel-dumps"></a><span data-ttu-id="11ceb-149">内核转储</span><span class="sxs-lookup"><span data-stu-id="11ceb-149">Kernel dumps</span></span>
![转储的内核调试](../media/DevicePortal/Debug1.png)

<span data-ttu-id="11ceb-151">将自动记录任何系统崩溃，并且可通过 Web 管理工具查看这些崩溃。</span><span class="sxs-lookup"><span data-stu-id="11ceb-151">Any system crashes will automatically be logged and available to view through the web management tool.</span></span>  <span data-ttu-id="11ceb-152">然后你可以下载内核转储，并尝试查明发生了什么情况。</span><span class="sxs-lookup"><span data-stu-id="11ceb-152">You can then download the kernel dump and try to figure out what's going on.</span></span>

#### <a name="process-dumps"></a><span data-ttu-id="11ceb-153">进程转储</span><span class="sxs-lookup"><span data-stu-id="11ceb-153">Process dumps</span></span>
![与进程转储调试](../media/DevicePortal/Debug2.png)

<span data-ttu-id="11ceb-155">这类似于动态内核转储，但适用于用户模式处理。</span><span class="sxs-lookup"><span data-stu-id="11ceb-155">This is similar to Live kernel dumps, but for the user mode processes.</span></span> <span data-ttu-id="11ceb-156">单击**下载**按钮都将导致小型转储，，将下载该过程的整个状态。</span><span class="sxs-lookup"><span data-stu-id="11ceb-156">Clicking the **download** button will cause a 'minidump', and the entire state of that process will be downloaded.</span></span> <span data-ttu-id="11ceb-157">这是适用于调试挂起进程。</span><span class="sxs-lookup"><span data-stu-id="11ceb-157">This is good for debugging hanging processes.</span></span>

#### <a name="kernel-crash-settings"></a><span data-ttu-id="11ceb-158">内核故障设置</span><span class="sxs-lookup"><span data-stu-id="11ceb-158">Kernel crash settings</span></span>
![内核故障设置](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a><span data-ttu-id="11ceb-160">蓝牙</span><span class="sxs-lookup"><span data-stu-id="11ceb-160">Bluetooth</span></span>
<span data-ttu-id="11ceb-161">此页显示所有配对的蓝牙设备以及所有可发现的设备。</span><span class="sxs-lookup"><span data-stu-id="11ceb-161">This page shows you all the bluetooth paired devices and all the devices which are discoverable.</span></span> <span data-ttu-id="11ceb-162">若要与其他蓝牙设备配对，将设备放在配对的模式下并等待它显示在可用设备列表中。</span><span class="sxs-lookup"><span data-stu-id="11ceb-162">To pair with another Bluetooth device, put the device in pairing mode and wait for it to appear in the available devices list.</span></span>  
![蓝牙设备列表](../media/DevicePortal/Bluetooth.png)

<span data-ttu-id="11ceb-164">单击**对链接**配对设备。</span><span class="sxs-lookup"><span data-stu-id="11ceb-164">Click on **Pair link** to pair the device.</span></span> <span data-ttu-id="11ceb-165">如果设备需要 PIN 才能配对，它将弹出一个消息框，显示 PIN。</span><span class="sxs-lookup"><span data-stu-id="11ceb-165">If the device requires a PIN for pairing, it will pop-up a message box displaying the PIN.</span></span> <span data-ttu-id="11ceb-166">设备配对后，它将显示在成对设备列表中。</span><span class="sxs-lookup"><span data-stu-id="11ceb-166">Once the device is paired, it will show up in the Paired devices list.</span></span> <span data-ttu-id="11ceb-167">通过单击可取消对设备**删除**。</span><span class="sxs-lookup"><span data-stu-id="11ceb-167">You can un-pair the device by clicking on **Remove**.</span></span> 

<span data-ttu-id="11ceb-168">一旦您导航到蓝牙页上，你的设备将其他设备发现。</span><span class="sxs-lookup"><span data-stu-id="11ceb-168">Once you navigate to the Bluetooth page, your device will be discoverable by other devices.</span></span> <span data-ttu-id="11ceb-169">此外可以找到从您的 PC/电话，并从该处对其进行配对。</span><span class="sxs-lookup"><span data-stu-id="11ceb-169">You can also find it from your PC/Phone and pair it from there.</span></span>

<span data-ttu-id="11ceb-170">蓝牙的详细信息可在上找到[蓝牙页](https://go.microsoft.com/fwlink/?linkid=823223)。</span><span class="sxs-lookup"><span data-stu-id="11ceb-170">More information on bluetooth can be found on the [bluetooth page](https://go.microsoft.com/fwlink/?linkid=823223).</span></span>

### <a name="iot-onboarding"></a><span data-ttu-id="11ceb-171">IoT 载入</span><span class="sxs-lookup"><span data-stu-id="11ceb-171">IoT Onboarding</span></span>

<span data-ttu-id="11ceb-172">IoT 载入配置 IoT 设备的 Wi-fi 连接选项提供支持。</span><span class="sxs-lookup"><span data-stu-id="11ceb-172">IoT Onboarding provides support for configuring an IoT device's Wi-Fi connectivity options.</span></span>

<span data-ttu-id="11ceb-173">**Internet 连接共享 (ICS)** Internet 连接共享，可与其他设备的 Wi-fi SoftAP 通过连接到你的设备共享您的设备的 Internet 访问权限。</span><span class="sxs-lookup"><span data-stu-id="11ceb-173">**Internet Connection Sharing (ICS)** Internet Connection Sharing allows you to share the Internet access of your device with other devices connected to your device over the Wi-Fi SoftAP.</span></span>
<span data-ttu-id="11ceb-174">若要使用此功能，你的 Windows 10 IoT 设备需要有权访问 internet （例如通过有线 LAN 连接）。</span><span class="sxs-lookup"><span data-stu-id="11ceb-174">To use this feature, your Windows 10 IoT Device needs to have access to the internet (e.g. through a wired LAN connection).</span></span>  <span data-ttu-id="11ceb-175">在连接-> 载入-> SoftAP 设置，请单击启用，并设置 SSID 名称和密码。</span><span class="sxs-lookup"><span data-stu-id="11ceb-175">In 'Connectivity->Onboarding->SoftAP settings' click 'enable' and set SSID name and password.</span></span>  <span data-ttu-id="11ceb-176">然后在连接-> Internet 连接共享为访问点适配器选择"Microsoft WI-FI Direct 虚拟适配器 #2"和共享的网络适配器中选择有线以太网适配器。</span><span class="sxs-lookup"><span data-stu-id="11ceb-176">Then in 'Connectivity->Internet connection sharing' for 'access point adapter' select "Microsoft Wi-FI Direct Virtual Adapter #2" and for 'shared network adapter' select your wired ethernet adapter.</span></span>  <span data-ttu-id="11ceb-177">最后，单击启动共享的访问。</span><span class="sxs-lookup"><span data-stu-id="11ceb-177">Finally, click 'start shared access.'</span></span>  <span data-ttu-id="11ceb-178">启动后，连接到 Windows 10 IoT 设备上 SoftAP 单独启用 Wi-fi 的设备。</span><span class="sxs-lookup"><span data-stu-id="11ceb-178">Once started, connect a separate Wi-Fi enabled device to the SoftAP on your Windows 10 IoT device.</span></span>  <span data-ttu-id="11ceb-179">建立连接后单独支持 Wi-fi 设备将能够通过 Windows 10 IoT 设备连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="11ceb-179">After a connection is established your separate Wi-Fi enabled device will be able to connect to the internet through your Windows 10 IoT device.</span></span>

> [!NOTE]
> <span data-ttu-id="11ceb-180">在设备上存在的 Wi-fi 配置文件时，会禁用 ICS。</span><span class="sxs-lookup"><span data-stu-id="11ceb-180">ICS is disabled when a Wi-Fi profile exists on the device.</span></span> <span data-ttu-id="11ceb-181">例如，如果您连接到 Wi-fi 访问点并检查"创建配置文件 （自动重新连接）"，则将禁用 ICS。</span><span class="sxs-lookup"><span data-stu-id="11ceb-181">For example, ICS will be disabled if you connect to a Wi-Fi access point and check “Create profile (auto re-connect)”.</span></span>

<span data-ttu-id="11ceb-182">**SoftAP 设置**SoftAP 设置，可以控制是否启用你的设备的 SoftAP。</span><span class="sxs-lookup"><span data-stu-id="11ceb-182">**SoftAP Settings** The SoftAP Settings allow you to control whether or not your device's SoftAP is enabled.</span></span>  <span data-ttu-id="11ceb-183">它还提供了一种方法用于配置 SoftAP 的 SSID 和 WPA2-PSK 密钥是从另一台设备连接 SoftAP 所必需。</span><span class="sxs-lookup"><span data-stu-id="11ceb-183">It also provides a means for configuring your SoftAP's SSID and the WPA2-PSK key which are necessary to connect the SoftAP from another device.</span></span>

<span data-ttu-id="11ceb-184">**AllJoyn 载入设置**AllJoyn 载入设置允许你控制是否可以在设备的 Wi-fi 连接设备的 AllJoyn 载入制造者通过配置。</span><span class="sxs-lookup"><span data-stu-id="11ceb-184">**AllJoyn Onboarding Settings** The AllJoyn Onboarding Settings allow you to control whether or not your device's Wi-Fi connection can configured through your device's AllJoyn Onboarding Producer.</span></span>  <span data-ttu-id="11ceb-185">当运行应用程序连接到你的 Windows 10 IoT SoftAP AllJoyn 载入使用者的单独设备时，AllJoyn 载入使用者应用程序可以用于配置你的 IoT 设备的 Wi-fi 适配器。</span><span class="sxs-lookup"><span data-stu-id="11ceb-185">When a separate device running an AllJoyn Onboarding Consumer application connects to your Windows 10 IoT SoftAP, the AllJoyn Onboarding Consumer application can be used to configure your IoT device's Wi-Fi adapter.</span></span>  <span data-ttu-id="11ceb-186">启用时，AllJoyn 载入生成者应用程序 (IoTOnboarding) 使用 ECDHE_NULL 身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="11ceb-186">When enabled, the AllJoyn Onboarding Producer app (IoTOnboarding) uses the ECDHE_NULL authentication method.</span></span> 

> [!NOTE]
> <span data-ttu-id="11ceb-187">若要使用 AllJoyn 使用 Windows 10 IoT 载入生成 10.0.14393 或需要更新前面<strong>IotOnboarding</strong>示例可能[从此处下载](https://github.com/ms-iot/samples)。</span><span class="sxs-lookup"><span data-stu-id="11ceb-187">To use AllJoyn Onboarding with Windows 10 IoT builds 10.0.14393 or earlier requires an update to the <strong>IotOnboarding</strong> sample which may be [downloaded here](https://github.com/ms-iot/samples).</span></span>

<span data-ttu-id="11ceb-188">![载入到 AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![载入到 ICS](../media/DevicePortal/OnboardingICS.png)</span><span class="sxs-lookup"><span data-stu-id="11ceb-188">![Onboarding onto AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding onto ICS](../media/DevicePortal/OnboardingICS.png)</span></span>

> [!NOTE]
> <span data-ttu-id="11ceb-189">访问点适配器是充当 （它通常具有如下 192.168.137.1 IP 地址） 的 WiFi 访问点的 WiFi 适配器。</span><span class="sxs-lookup"><span data-stu-id="11ceb-189">Access point adapter is the WiFi adapter that act as a WiFi access point (it usually has an IP address like 192.168.137.1).</span></span>
> <span data-ttu-id="11ceb-190">共享的网络适配器是连接到 Internet 的适配器 (例如：以太网适配器）。</span><span class="sxs-lookup"><span data-stu-id="11ceb-190">Shared network adapter is the adapter that connects to Internet (e.g.: Ethernet adapter).</span></span>

![载入到软亚太](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> <span data-ttu-id="11ceb-192">如果启用并使用 Wifi 适配器的 MAC 地址为后缀 AllJoyn 载入，将"AJ_"通过自动前缀 SoftAP SSID。</span><span class="sxs-lookup"><span data-stu-id="11ceb-192">SoftAP SSID will be automatically prefixed by "AJ_" if AllJoyn onboarding is enabled and postfixed with the MAC address of the Wifi adapter.</span></span> <span data-ttu-id="11ceb-193">SoftAP 通行短语必须介于 8 到 63 个 ASCII 字符之间。</span><span class="sxs-lookup"><span data-stu-id="11ceb-193">The SoftAP passphrase must be between 8 and 63 ASCII characters.</span></span>


### <a name="tpm-configuration"></a><span data-ttu-id="11ceb-194">TPM 配置</span><span class="sxs-lookup"><span data-stu-id="11ceb-194">TPM configuration</span></span>
<span data-ttu-id="11ceb-195">受信任的平台模块 (TPM) 是包括功能的随机数字生成、 安全的加密密钥的生成和限制其使用了加密协处理器。</span><span class="sxs-lookup"><span data-stu-id="11ceb-195">The Trusted Platform Module (TPM) is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="11ceb-196">它还包括诸如远程证明和密封存储等功能。</span><span class="sxs-lookup"><span data-stu-id="11ceb-196">It also includes capabilities such as remote attestation and sealed storage.</span></span> <span data-ttu-id="11ceb-197">若要了解有关 TPM 和 IoT Core 上的安全，请访问[构建安全的设备](../secure-your-device/BuildingSecureDevices.md)页并[TPM](../secure-your-device/TPM.md)页。</span><span class="sxs-lookup"><span data-stu-id="11ceb-197">To learn about the TPM and security on IoT Core, visit the [Building secure devices](../secure-your-device/BuildingSecureDevices.md) page and the [TPM](../secure-your-device/TPM.md) page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11ceb-198">Limpet.exe 使用是 Windows IoT Core 的一部分。</span><span class="sxs-lookup"><span data-stu-id="11ceb-198">Limpet.exe used to be part of Windows IoT Core.</span></span> <span data-ttu-id="11ceb-199">从 2018 年 10 月开始，它现已推出，在开放源代码 porject [ https://github.com/ms-iot/azure-dm-client ](https://github.com/ms-iot/azure-dm-client)。</span><span class="sxs-lookup"><span data-stu-id="11ceb-199">Starting with October 2018, it is now available as an open source porject at [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client).</span></span>

<span data-ttu-id="11ceb-200">若要使测试更加轻松，我们无签名的 Limpet.exe 可用的预建版本，并且可以直接从 WDP 下载。</span><span class="sxs-lookup"><span data-stu-id="11ceb-200">To make testing easier, we have a non-signed pre-built version of Limpet.exe available and can be downloaded right from WDP.</span></span> <span data-ttu-id="11ceb-201">只需转到 TPM 配置选项卡，然后单击安装最新按钮。</span><span class="sxs-lookup"><span data-stu-id="11ceb-201">You just need to go the 'TPM Configuration' tab and click the 'Install Latest' button.</span></span> 

> [!NOTE]
> <span data-ttu-id="11ceb-202">此版本的 Limpet.exe 不应随最终产品。</span><span class="sxs-lookup"><span data-stu-id="11ceb-202">This version of Limpet.exe should not be shipped with your final product.</span></span> <span data-ttu-id="11ceb-203">相反，您需要生成开放源代码项目，其签名，并将其打包与你的映像。</span><span class="sxs-lookup"><span data-stu-id="11ceb-203">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

### <a name="azure-clients-configuration"></a><span data-ttu-id="11ceb-204">Azure 客户端配置</span><span class="sxs-lookup"><span data-stu-id="11ceb-204">Azure Clients configuration</span></span>

<span data-ttu-id="11ceb-205">可以通过云服务远程管理 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="11ceb-205">IoT devices can be remotely managed through cloud services.</span></span> <span data-ttu-id="11ceb-206">Azure 提供了非常丰富的服务，使这种情况。</span><span class="sxs-lookup"><span data-stu-id="11ceb-206">Azure provides a very rich set of services to enable such scenarios.</span></span> <span data-ttu-id="11ceb-207">我们已创建的设备管理客户端，它补充 Windows 平台上的 Azure 的设备预配服务 (DPS) 和 Azure 的 IoT 中心服务，还公开多个 Windows 可管理性功能。</span><span class="sxs-lookup"><span data-stu-id="11ceb-207">We have created a device management client that complements Azure's Device Provisioning Service (DPS) and Azure's IoT Hub service on the Windows platform and which also exposes several Windows manageability features.</span></span>

<span data-ttu-id="11ceb-208">客户端将作为开放源代码项目提供。</span><span class="sxs-lookup"><span data-stu-id="11ceb-208">The clients will be provided as open source projects.</span></span> <span data-ttu-id="11ceb-209">若要使测试更加容易，我们将提供预先生成的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="11ceb-209">To make testing them easier, we will be providing pre-built binaries.</span></span> <span data-ttu-id="11ceb-210">您可以使用 Azure 客户端选项卡中 WDP 安装和运行这些测试二进制文件。</span><span class="sxs-lookup"><span data-stu-id="11ceb-210">You can use the 'Azure Clients' tab in WDP to install and run those test binaries.</span></span>

> [!NOTE]
> <span data-ttu-id="11ceb-211">此版本的工具不应随最终产品。</span><span class="sxs-lookup"><span data-stu-id="11ceb-211">This version of the tools should not be shipped with your final product.</span></span> <span data-ttu-id="11ceb-212">相反，您需要生成开放源代码项目，其签名，并将其打包与你的映像。</span><span class="sxs-lookup"><span data-stu-id="11ceb-212">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

<span data-ttu-id="11ceb-213">可供使用的开放源代码项目后，我们将更新本文档。</span><span class="sxs-lookup"><span data-stu-id="11ceb-213">We will update this documentation once the open source projects are available for consumption.</span></span>

### <a name="remote"></a><span data-ttu-id="11ceb-214">遥控器</span><span class="sxs-lookup"><span data-stu-id="11ceb-214">Remote</span></span>
<span data-ttu-id="11ceb-215">Windows IoT 远程服务器允许用户查看其设备无需连接到键盘的物理显示器显示。</span><span class="sxs-lookup"><span data-stu-id="11ceb-215">The Windows IoT Remote Server allows users to see what their device is displaying without connecting a physical monitor to the keyboard.</span></span>


## <a name="additional-information"></a><span data-ttu-id="11ceb-216">其他信息</span><span class="sxs-lookup"><span data-stu-id="11ceb-216">Additional Information</span></span> 

### <a name="changing-the-default-port"></a><span data-ttu-id="11ceb-217">更改默认端口</span><span class="sxs-lookup"><span data-stu-id="11ceb-217">Changing the default port</span></span>
 
1. <span data-ttu-id="11ceb-218">启动 powershell 并[连接到设备。](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="11ceb-218">Launch powershell and [connect to your device.](../connect-your-device/PowerShell.md)</span></span>
2. <span data-ttu-id="11ceb-219">下载[TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership)工具中，生成它，并将其复制到你的设备。</span><span class="sxs-lookup"><span data-stu-id="11ceb-219">Download [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, build it, and copy it to your device.</span></span> 
3. <span data-ttu-id="11ceb-220">通过运行获取服务的注册表项的所有权</span><span class="sxs-lookup"><span data-stu-id="11ceb-220">Take ownership of the registry key for the service by running</span></span>

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. <span data-ttu-id="11ceb-221">通过修改注册表设置来设置所需的端口</span><span class="sxs-lookup"><span data-stu-id="11ceb-221">Set the desired port by modifying the registry settings</span></span> 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. <span data-ttu-id="11ceb-222">重新启动 WebManagement 服务通过运行以下或通过重新启动设备</span><span class="sxs-lookup"><span data-stu-id="11ceb-222">Restart the WebManagement service by running following or by restarting the device</span></span>

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a><span data-ttu-id="11ceb-223">使用 HTTPS</span><span class="sxs-lookup"><span data-stu-id="11ceb-223">Using HTTPS</span></span> 

<span data-ttu-id="11ceb-224">如果你想要使用 HTTPS，首先获取注册表项的所有权上, 一节中所述并按如下所示设置 HttpsPort 和 EncryptionMode 注册表项，然后重新启动 webmanagement 服务</span><span class="sxs-lookup"><span data-stu-id="11ceb-224">If you want to use HTTPS, first take the ownership of the registry key as described in previous section and set the HttpsPort and EncryptionMode registry keys as below and then restart the webmanagement service</span></span>

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="11ceb-225">设置设备门户中使用自定义 SSL 证书</span><span class="sxs-lookup"><span data-stu-id="11ceb-225">Provisoning Device Portal with a custom SSL certificate</span></span>

<span data-ttu-id="11ceb-226">在 Windows 10 创意者更新，Windows Device Portal 添加了设备管理员安装使用的自定义证书中的 HTTPS 通信的方法。</span><span class="sxs-lookup"><span data-stu-id="11ceb-226">In the Windows 10 Creators Update, the Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span>

<span data-ttu-id="11ceb-227">若要了解更多信息，请[阅读 Windows Device Portal docs 下的文档](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)。</span><span class="sxs-lookup"><span data-stu-id="11ceb-227">To learn more, [read the documentation under the Windows Device Portal docs](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span></span> 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a><span data-ttu-id="11ceb-228">用于捕获内存转储崩溃转储设置：</span><span class="sxs-lookup"><span data-stu-id="11ceb-228">Crash Dump Settings for Capturing Memory Dump:</span></span>

<span data-ttu-id="11ceb-229">若要捕获完整内存转储，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="11ceb-229">To capture a Full Memory Dump, do the following:</span></span>

1. <span data-ttu-id="11ceb-230">连接到通过 WDP IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="11ceb-230">Connect to a IoT device through WDP.</span></span>

2. <span data-ttu-id="11ceb-231">从调试-> 的调试-> 设置内核故障设置-> 故障转储类型。</span><span class="sxs-lookup"><span data-stu-id="11ceb-231">From Debug -> Debug settings -> Kernel crash settings -> Crash dump type.</span></span> 

3. <span data-ttu-id="11ceb-232">选择：完全内存转储 （使用内存中）。</span><span class="sxs-lookup"><span data-stu-id="11ceb-232">Select: Complete memory dump (in use memory).</span></span>
    <span data-ttu-id="11ceb-233">请确保在设备重新启动设置才能生效。</span><span class="sxs-lookup"><span data-stu-id="11ceb-233">Make sure the device is rebooted for the setting to take effect.</span></span> 
    
4. <span data-ttu-id="11ceb-234">验证`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled`设置为 0x1。</span><span class="sxs-lookup"><span data-stu-id="11ceb-234">Verify  that `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` is set to 0x1.</span></span>

5. <span data-ttu-id="11ceb-235">更新`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize`为 0x0。</span><span class="sxs-lookup"><span data-stu-id="11ceb-235">Update `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` to 0x0.</span></span>

6. <span data-ttu-id="11ceb-236">请确保有足够的空间来生成此转储在设备上。</span><span class="sxs-lookup"><span data-stu-id="11ceb-236">Make sure you have enough space on the device for this Dump to be generated.</span></span> <span data-ttu-id="11ceb-237">你可以配置更改的转储文件位置在此处： `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span><span class="sxs-lookup"><span data-stu-id="11ceb-237">You can configure the changing the DumpFile location from here: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span></span>


## <a name="additional-resources"></a><span data-ttu-id="11ceb-238">其他资源</span><span class="sxs-lookup"><span data-stu-id="11ceb-238">Additional Resources</span></span>
___ 

1. [<span data-ttu-id="11ceb-239">Windows Device Portal 概述页</span><span class="sxs-lookup"><span data-stu-id="11ceb-239">Windows Device Portal overview page</span></span>](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
