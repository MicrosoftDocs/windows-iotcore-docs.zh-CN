---
title: Windows 设备门户
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 设备门户远程配置和管理你的设备。
keywords: windows iot，Windows 设备门户，远程，设备门户
ms.openlocfilehash: 22c8bd5b9908fd3d3d44563167a7950fc2f8c244
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655583"
---
# <a name="windows-device-portal"></a><span data-ttu-id="68574-104">Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="68574-104">Windows Device Portal</span></span>
   <span data-ttu-id="68574-105">通过 Windows 设备门户 (WDP) ，你可以通过本地网络远程配置和管理你的设备。</span><span class="sxs-lookup"><span data-stu-id="68574-105">The Windows Device Portal (WDP) lets you configure and manage your device remotely over your local network.</span></span>
<span data-ttu-id="68574-106">[Windows 设备门户](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)的 "概述" 页上介绍了主要功能</span><span class="sxs-lookup"><span data-stu-id="68574-106">The main features are documented on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

![设备门户主页](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> <span data-ttu-id="68574-108">请勿将创客映像用于商业化。</span><span class="sxs-lookup"><span data-stu-id="68574-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="68574-109">若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。</span><span class="sxs-lookup"><span data-stu-id="68574-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="68574-110">在[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="68574-110">Learn more [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!WARNING]
> <span data-ttu-id="68574-111">对于 ARM 设备，实时内核调试当前失败。</span><span class="sxs-lookup"><span data-stu-id="68574-111">Live kernel debug is currently failing for ARM devices.</span></span> <span data-ttu-id="68574-112">我们正在努力解决此情况。</span><span class="sxs-lookup"><span data-stu-id="68574-112">We are working to get this fixed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="68574-113">如果要构建一个开源零售设备，用于商业部署到“特定/有限安装”（即工厂或零售商店），然后由最终用户进行最终配置，并且您要为客户登记归档，他们必须[获取 WDP 证书，并将其安装到 WDP 和联网的浏览器上，且在 WDP 更改了密码](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)，那么在这种范围狭窄的商用实例中使用 WDP 是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="68574-113">If you are building an open retail device for commercial deployment to a "specific/limited installation" (i.e. factory or retail store) where the end-user does the final configuration and you document your customers that they must [obtain a certificate for WDP and install it on both WDP and connecting browsers and passwords are changed on WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), then using WDP in this narrow commercial instance is acceptable.</span></span> <span data-ttu-id="68574-114">此方案中的零售映像仍 *不* 包含 IOT_TOOLKIT，但应使用 IOT_WEBBEXTN 包来请求 WDP。</span><span class="sxs-lookup"><span data-stu-id="68574-114">Retail images in this scenario should still *not* include IOT_TOOLKIT, but should use the IOT_WEBBEXTN package to pull in WDP.</span></span>

## <a name="shared-documentation"></a><span data-ttu-id="68574-115">共享文档</span><span class="sxs-lookup"><span data-stu-id="68574-115">Shared Documentation</span></span>
<span data-ttu-id="68574-116">WDP 是在所有 Windows 10 设备上共享的开发人员工具。</span><span class="sxs-lookup"><span data-stu-id="68574-116">WDP is a developer tool shared among all Windows 10 devices.</span></span> <span data-ttu-id="68574-117">每个产品都有其自己独特的功能，但核心功能是相同的。</span><span class="sxs-lookup"><span data-stu-id="68574-117">Each product has its own unique features, but the core functionality is the same.</span></span>
<span data-ttu-id="68574-118">有关主要功能的文档，请参阅 [Windows 设备门户](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)的 "概述" 页。</span><span class="sxs-lookup"><span data-stu-id="68574-118">Documentation for the main features is found on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span> <span data-ttu-id="68574-119">以下文档的其余部分将是特定于 IoT 的文档。</span><span class="sxs-lookup"><span data-stu-id="68574-119">The rest of the documentation below will be IoT specific.</span></span>

## <a name="set-up"></a><span data-ttu-id="68574-120">设置</span><span class="sxs-lookup"><span data-stu-id="68574-120">Set up</span></span>

<span data-ttu-id="68574-121">可以通过两种方式启动并运行 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="68574-121">There are two ways to go get the Windows Device Portal up and running.</span></span>

### <a name="1-windows-10-iot-dashboard"></a><span data-ttu-id="68574-122">1. Windows 10 IoT 面板</span><span class="sxs-lookup"><span data-stu-id="68574-122">1. Windows 10 IoT Dashboard</span></span>

<span data-ttu-id="68574-123">首先，你将需要下载 [Windows 10 IoT 仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)，它是一个开发人员工具，可让你轻松地设置新设备。</span><span class="sxs-lookup"><span data-stu-id="68574-123">First, you'll want to download the [Windows 10 IoT Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard), a developer tool that makes it easy to set up new devices.</span></span> <span data-ttu-id="68574-124">使用仪表板将 Windows 10 IoT Core 映像闪存到设备后，请检查设备是否显示在 "我的设备" 下。</span><span class="sxs-lookup"><span data-stu-id="68574-124">Once you've used the Dashboard to flash a Windows 10 IoT Core image onto your device, check that your device shows up under "My devices".</span></span>

<span data-ttu-id="68574-125">在此处使用 "操作" 下的省略号选择 "在设备门户中打开"。</span><span class="sxs-lookup"><span data-stu-id="68574-125">From there, use the ellipses under "Actions" to select "Open in Device Portal".</span></span> <span data-ttu-id="68574-126">在这里，你将转到设备门户身份验证页面，除非最初更改了凭据，否则默认凭据为：</span><span class="sxs-lookup"><span data-stu-id="68574-126">From there, you'll be taken to the Device Portal authentication page where, unless you changed the credentials initially, the default credentials are:</span></span>
```
    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
```
 ### <a name="2-browser"></a><span data-ttu-id="68574-127">2. 浏览器</span><span class="sxs-lookup"><span data-stu-id="68574-127">2. Browser</span></span>
<span data-ttu-id="68574-128">如果在仪表板中找不到设备或希望跳过仪表板，还可以通过输入设备的 IP 地址并 `:8080` 将其插入到末尾来打开设备门户。</span><span class="sxs-lookup"><span data-stu-id="68574-128">If you cannot find your device in the dashboard or prefer to skip using the dashboard, you can also open the Device Portal by entering the IP address of your device plus `:8080` onto the end.</span></span> <span data-ttu-id="68574-129">正确完成后，其外观应如下所示：</span><span class="sxs-lookup"><span data-stu-id="68574-129">When done correctly, it should look something like this:</span></span>


   ![IoTDashboard 视图设备](../media/deviceportal/Dashboard-Action.gif)


## <a name="iot-specific-features"></a><span data-ttu-id="68574-131">IoT 特定功能</span><span class="sxs-lookup"><span data-stu-id="68574-131">IoT specific features</span></span>

### <a name="device-settings"></a><span data-ttu-id="68574-132">设备设置</span><span class="sxs-lookup"><span data-stu-id="68574-132">Device Settings</span></span>

<span data-ttu-id="68574-133">IoT Core 添加复选框以启用或禁用 [屏幕键盘](../develop-your-app/OnScreenKeyboard.md)</span><span class="sxs-lookup"><span data-stu-id="68574-133">IoT Core adds a checkbox to enable or disable the [on-screen keyboard](../develop-your-app/OnScreenKeyboard.md)</span></span>
> [!NOTE]
> <span data-ttu-id="68574-134">此复选框有一个已知 bug，它会将 "flash" 从选中状态 "未选中"。</span><span class="sxs-lookup"><span data-stu-id="68574-134">This checkbox has a known bug where it will "flash" from checked to non-checked.</span></span> <span data-ttu-id="68574-135">单击以确保该复选框显示所需状态时，请刷新 (F5) 的页面。</span><span class="sxs-lookup"><span data-stu-id="68574-135">Please refresh the page (F5) after clicking to ensure that the checkbox is showing your desired state.</span></span>

### <a name="apps"></a><span data-ttu-id="68574-136">应用</span><span class="sxs-lookup"><span data-stu-id="68574-136">Apps</span></span>
<span data-ttu-id="68574-137">在设备上提供 AppX 包和绑定的安装/卸载功能。</span><span class="sxs-lookup"><span data-stu-id="68574-137">Provides install/uninstall functionality for AppX packages and bundles on your device.</span></span>
<span data-ttu-id="68574-138">![应用列表](../media/DevicePortal/AppList.png)</span><span class="sxs-lookup"><span data-stu-id="68574-138">![App list](../media/DevicePortal/AppList.png)</span></span>

<span data-ttu-id="68574-139">IoT 核心的独特之处在于，它只允许一次运行一次前台应用。</span><span class="sxs-lookup"><span data-stu-id="68574-139">IoT Core is unique in that it only allows one foreground app to run at one time.</span></span> <span data-ttu-id="68574-140">修改应用列表以确保这种情况。</span><span class="sxs-lookup"><span data-stu-id="68574-140">The app list is modified to ensure that this is the case.</span></span> <span data-ttu-id="68574-141">在 " **启动** " 列下，可以选择默认情况下启动的多个后台应用程序，但只能设置一个前景应用程序。</span><span class="sxs-lookup"><span data-stu-id="68574-141">Under the **STARTUP** column, you can select as many background applications to start by default, but can only set one foreground application.</span></span>  

### <a name="app-file-explorer"></a><span data-ttu-id="68574-142">应用文件资源管理器</span><span class="sxs-lookup"><span data-stu-id="68574-142">App File Explorer</span></span>

<span data-ttu-id="68574-143">应用文件资源管理器显示应用可以访问的目录。</span><span class="sxs-lookup"><span data-stu-id="68574-143">The app file explorer shows the directories that your apps can access.</span></span>

* <span data-ttu-id="68574-144">CameraRoll 在所有应用之间共享</span><span class="sxs-lookup"><span data-stu-id="68574-144">CameraRoll is shared among all apps</span></span>
* <span data-ttu-id="68574-145">文档在所有应用中共享</span><span class="sxs-lookup"><span data-stu-id="68574-145">Documents are shared among all apps</span></span>
* <span data-ttu-id="68574-146">LocalAppData 包含特定于每个应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="68574-146">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="68574-147">此文件夹将与你的应用同名，并且其他应用无法访问该文件夹。</span><span class="sxs-lookup"><span data-stu-id="68574-147">This folder will be the same name as your app and other apps cannot access it.</span></span>

### <a name="debugging"></a><span data-ttu-id="68574-148">调试</span><span class="sxs-lookup"><span data-stu-id="68574-148">Debugging</span></span>

#### <a name="kernel-dumps"></a><span data-ttu-id="68574-149">内核转储</span><span class="sxs-lookup"><span data-stu-id="68574-149">Kernel dumps</span></span>
![用内核转储进行调试](../media/DevicePortal/Debug1.png)

<span data-ttu-id="68574-151">系统崩溃将自动记录并可通过 web 管理工具查看。</span><span class="sxs-lookup"><span data-stu-id="68574-151">Any system crashes will automatically be logged and available to view through the web management tool.</span></span>  <span data-ttu-id="68574-152">然后，你可以下载内核转储，尝试找出正在进行的操作。</span><span class="sxs-lookup"><span data-stu-id="68574-152">You can then download the kernel dump and try to figure out what's going on.</span></span>

#### <a name="process-dumps"></a><span data-ttu-id="68574-153">进程转储</span><span class="sxs-lookup"><span data-stu-id="68574-153">Process dumps</span></span>
![用进程转储进行调试](../media/DevicePortal/Debug2.png)

<span data-ttu-id="68574-155">这类似于实时内核转储，但适用于用户模式进程。</span><span class="sxs-lookup"><span data-stu-id="68574-155">This is similar to Live kernel dumps, but for the user mode processes.</span></span>
<span data-ttu-id="68574-156">单击 " **下载** " 按钮将导致 "小型转储"，并将下载该进程的全部状态。</span><span class="sxs-lookup"><span data-stu-id="68574-156">Clicking the **download** button will cause a 'minidump', and the entire state of that process will be downloaded.</span></span> <span data-ttu-id="68574-157">这适用于调试挂起进程。</span><span class="sxs-lookup"><span data-stu-id="68574-157">This is good for debugging hanging processes.</span></span>

#### <a name="kernel-crash-settings"></a><span data-ttu-id="68574-158">内核故障设置</span><span class="sxs-lookup"><span data-stu-id="68574-158">Kernel crash settings</span></span>
![内核故障设置](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a><span data-ttu-id="68574-160">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="68574-160">Bluetooth</span></span>
<span data-ttu-id="68574-161">此页显示所有蓝牙配对设备以及可发现的所有设备。</span><span class="sxs-lookup"><span data-stu-id="68574-161">This page shows you all the bluetooth paired devices and all the devices that are discoverable.</span></span> <span data-ttu-id="68574-162">要与另一台蓝牙设备配对，请将设备置于配对模式，并等待它出现在 "可用设备" 列表中。</span><span class="sxs-lookup"><span data-stu-id="68574-162">To pair with another Bluetooth device, put the device in pairing mode and wait for it to appear in the available devices list.</span></span>  
![蓝牙设备列表](../media/DevicePortal/Bluetooth.png)

<span data-ttu-id="68574-164">单击 " **对" 链接** 以将设备配对。</span><span class="sxs-lookup"><span data-stu-id="68574-164">Click on **Pair link** to pair the device.</span></span> <span data-ttu-id="68574-165">如果设备要求使用 PIN 进行配对，它将弹出一个显示该 PIN 的消息框。</span><span class="sxs-lookup"><span data-stu-id="68574-165">If the device requires a PIN for pairing, it will pop up a message box displaying the PIN.</span></span> <span data-ttu-id="68574-166">设备配对后，它将显示在 "配对的设备" 列表中。</span><span class="sxs-lookup"><span data-stu-id="68574-166">Once the device is paired, it will show up in the Paired devices list.</span></span> <span data-ttu-id="68574-167">可以通过单击 " **删除**" 取消配对设备。</span><span class="sxs-lookup"><span data-stu-id="68574-167">You can unpair the device by clicking on **Remove**.</span></span>

<span data-ttu-id="68574-168">导航到蓝牙页面后，其他设备将可以发现你的设备。</span><span class="sxs-lookup"><span data-stu-id="68574-168">Once you navigate to the Bluetooth page, your device will be discoverable by other devices.</span></span> <span data-ttu-id="68574-169">你还可以从你的电脑/手机中查找它，并将其配对。</span><span class="sxs-lookup"><span data-stu-id="68574-169">You can also find it from your PC/Phone and pair it from there.</span></span>

<span data-ttu-id="68574-170">有关蓝牙的详细信息，请参阅 [蓝牙页面](https://go.microsoft.com/fwlink/?linkid=823223)。</span><span class="sxs-lookup"><span data-stu-id="68574-170">More information on bluetooth can be found on the [bluetooth page](https://go.microsoft.com/fwlink/?linkid=823223).</span></span>

### <a name="iot-onboarding"></a><span data-ttu-id="68574-171">IoT 载入</span><span class="sxs-lookup"><span data-stu-id="68574-171">IoT Onboarding</span></span>

<span data-ttu-id="68574-172">IoT 载入为配置 IoT 设备的 Wi-fi 连接选项提供支持。</span><span class="sxs-lookup"><span data-stu-id="68574-172">IoT Onboarding provides support for configuring an IoT device's Wi-Fi connectivity options.</span></span>

<span data-ttu-id="68574-173">\*\* (ICS) 的 Internet 连接共享 \*\* Internet 连接共享允许与通过 Wi-fi SoftAP 连接到设备的其他设备共享设备的 Internet 访问。</span><span class="sxs-lookup"><span data-stu-id="68574-173">**Internet Connection Sharing (ICS)** Internet Connection Sharing allows you to share the Internet access of your device with other devices connected to your device over the Wi-Fi SoftAP.</span></span>
<span data-ttu-id="68574-174">若要使用此功能，Windows 10 IoT 设备需要有权访问 internet (例如，通过有线 LAN 连接) 。</span><span class="sxs-lookup"><span data-stu-id="68574-174">To use this feature, your Windows 10 IoT Device needs to have access to the internet (e.g. through a wired LAN connection).</span></span>  <span data-ttu-id="68574-175">在 "连接->载入->SoftAP 设置" 中，单击 "启用" 并设置 SSID 名称和密码。</span><span class="sxs-lookup"><span data-stu-id="68574-175">In 'Connectivity->Onboarding->SoftAP settings' click 'enable' and set SSID name and password.</span></span>  <span data-ttu-id="68574-176">然后，在 "连接->Internet 连接共享" 中为 "访问点适配器" 选择 "Microsoft Wi-fi Direct 虚拟适配器 #2" 和 "共享网络适配器"，然后选择有线以太网适配器。</span><span class="sxs-lookup"><span data-stu-id="68574-176">Then in 'Connectivity->Internet connection sharing' for 'access point adapter' select "Microsoft Wi-Fi Direct Virtual Adapter #2" and for 'shared network adapter' select your wired ethernet adapter.</span></span>  <span data-ttu-id="68574-177">最后，单击 "启动共享访问"。</span><span class="sxs-lookup"><span data-stu-id="68574-177">Finally, click 'start shared access.'</span></span>  <span data-ttu-id="68574-178">启动后，将单独的 Wi-fi 启用的设备连接到 Windows 10 IoT 设备上的 SoftAP。</span><span class="sxs-lookup"><span data-stu-id="68574-178">Once started, connect a separate Wi-Fi enabled device to the SoftAP on your Windows 10 IoT device.</span></span>  <span data-ttu-id="68574-179">建立连接后，单独的 Wi-fi 设备将能够通过 Windows 10 IoT 设备连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="68574-179">After a connection is established, your separate Wi-Fi enabled device will be able to connect to the internet through your Windows 10 IoT device.</span></span>

> [!NOTE]
> <span data-ttu-id="68574-180">当设备上存在 Wi-fi 配置文件时，ICS 处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="68574-180">ICS is disabled when a Wi-Fi profile exists on the device.</span></span>
><span data-ttu-id="68574-181">例如，如果连接到 Wi-fi 访问点并选中 "创建配置文件 (自动重新连接) "，则将禁用 ICS。</span><span class="sxs-lookup"><span data-stu-id="68574-181">For example, ICS will be disabled if you connect to a Wi-Fi access point and check “Create profile (auto re-connect)”.</span></span>

<span data-ttu-id="68574-182">**SoftAP 设置** SoftAP 设置用于控制是否已启用设备的 SoftAP。</span><span class="sxs-lookup"><span data-stu-id="68574-182">**SoftAP Settings** The SoftAP Settings allow you to control whether or not your device's SoftAP is enabled.</span></span>  <span data-ttu-id="68574-183">它还提供了一种方法，用于配置 SoftAP 的 SSID 和 WPA2-PSK 密钥，这是从其他设备连接 SoftAP 所必需的。</span><span class="sxs-lookup"><span data-stu-id="68574-183">It also provides a means for configuring your SoftAP's SSID and the WPA2-PSK key, which are necessary to connect the SoftAP from another device.</span></span>

<span data-ttu-id="68574-184">**AllJoyn 载入设置** 使用 AllJoyn 载入设置，可以控制是否可以通过设备的 AllJoyn 载入制造者配置设备的 Wi-fi 连接。</span><span class="sxs-lookup"><span data-stu-id="68574-184">**AllJoyn Onboarding Settings** The AllJoyn Onboarding Settings allow you to control whether or not your device's Wi-Fi connection can be configured through your device's AllJoyn Onboarding Producer.</span></span>  <span data-ttu-id="68574-185">当运行 AllJoyn 载入使用者应用程序的单独设备连接到 Windows 10 IoT SoftAP 时，可以使用 AllJoyn 载入消费者应用程序来配置 IoT 设备的 Wi-fi 适配器。</span><span class="sxs-lookup"><span data-stu-id="68574-185">When a separate device running an AllJoyn Onboarding Consumer application connects to your Windows 10 IoT SoftAP, the AllJoyn Onboarding Consumer application can be used to configure your IoT device's Wi-Fi adapter.</span></span>  <span data-ttu-id="68574-186">启用后，AllJoyn 载入制造者应用 (IoTOnboarding) 使用 ECDHE_NULL 身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="68574-186">When enabled, the AllJoyn Onboarding Producer app (IoTOnboarding) uses the ECDHE_NULL authentication method.</span></span>

> [!NOTE]
> <span data-ttu-id="68574-187">若要在 Windows 10 IoT 版本10.0.14393 或更早版本中使用 AllJoyn 载入，需要更新 <strong>IotOnboarding</strong> 示例，此示例可在 [此处下载](https://github.com/ms-iot/samples)。</span><span class="sxs-lookup"><span data-stu-id="68574-187">To use AllJoyn Onboarding with Windows 10 IoT builds 10.0.14393 or earlier requires an update to the <strong>IotOnboarding</strong> sample which may be [downloaded here](https://github.com/ms-iot/samples).</span></span>

<span data-ttu-id="68574-188">![在 ICS 上加入到 AllJoyn ](../media/DevicePortal/OnboardingAllJoyn.png)
 ![ 载入](../media/DevicePortal/OnboardingICS.png)</span><span class="sxs-lookup"><span data-stu-id="68574-188">![Onboarding onto AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding onto ICS](../media/DevicePortal/OnboardingICS.png)</span></span>

> [!NOTE]
> <span data-ttu-id="68574-189">接入点适配器是作为 WiFi 接入点的 WiFi 适配器， (通常具有类似于 192.168.137.1) 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="68574-189">Access point adapter is the WiFi adapter that act as a WiFi access point (it usually has an IP address like 192.168.137.1).</span></span>
> <span data-ttu-id="68574-190">共享网络适配器是连接到 Internet 的适配器 (例如：以太网适配器) 。</span><span class="sxs-lookup"><span data-stu-id="68574-190">Shared network adapter is the adapter that connects to Internet (e.g.: Ethernet adapter).</span></span>

![载入软 AP](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> <span data-ttu-id="68574-192">如果启用了 AllJoyn 载入并使用 Wifi 适配器的 MAC 地址后缀，SoftAP SSID 将自动以 "AJ_" 作为前缀。</span><span class="sxs-lookup"><span data-stu-id="68574-192">SoftAP SSID will be automatically prefixed by "AJ_" if AllJoyn onboarding is enabled and postfixed with the MAC address of the Wifi adapter.</span></span> <span data-ttu-id="68574-193">SoftAP 密码必须介于8到 63 ASCII 字符之间。</span><span class="sxs-lookup"><span data-stu-id="68574-193">The SoftAP passphrase must be between 8 and 63 ASCII characters.</span></span>


### <a name="tpm-configuration"></a><span data-ttu-id="68574-194">TPM 配置</span><span class="sxs-lookup"><span data-stu-id="68574-194">TPM configuration</span></span>
<span data-ttu-id="68574-195">受信任的平台模块 (TPM) 是一种加密协处理器，其中包括用于随机编号生成的功能、安全生成的加密密钥和其使用限制。</span><span class="sxs-lookup"><span data-stu-id="68574-195">The Trusted Platform Module (TPM) is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="68574-196">它还包括远程证明和密封的存储等功能。</span><span class="sxs-lookup"><span data-stu-id="68574-196">It also includes capabilities such as remote attestation and sealed storage.</span></span> <span data-ttu-id="68574-197">若要了解有关 IoT Core 上的 TPM 和安全性的信息，请访问 [构建安全设备](../secure-your-device/BuildingSecureDevices.md) 页面和 [TPM](../secure-your-device/TPM.md) 页面。</span><span class="sxs-lookup"><span data-stu-id="68574-197">To learn about the TPM and security on IoT Core, visit the [Building secure devices](../secure-your-device/BuildingSecureDevices.md) page and the [TPM](../secure-your-device/TPM.md) page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="68574-198">Limpet.exe 用作 Windows IoT Core 的一部分。</span><span class="sxs-lookup"><span data-stu-id="68574-198">Limpet.exe used to be part of Windows IoT Core.</span></span> <span data-ttu-id="68574-199">从10月2018开始，现在可作为开源 porject [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client) 。</span><span class="sxs-lookup"><span data-stu-id="68574-199">Starting with October 2018, it is now available as an open source porject at [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client).</span></span>

<span data-ttu-id="68574-200">为了使测试更轻松，我们提供了一个未签名的预构建版本的 Limpet.exe，可以从 WDP 下载。</span><span class="sxs-lookup"><span data-stu-id="68574-200">To make testing easier, we have a non-signed pre-built version of Limpet.exe available and can be downloaded right from WDP.</span></span> <span data-ttu-id="68574-201">只需执行 "TPM 配置" 选项卡，然后单击 "安装最新的" 按钮即可。</span><span class="sxs-lookup"><span data-stu-id="68574-201">You just need to go the 'TPM Configuration' tab and click the 'Install Latest' button.</span></span>

> [!NOTE]
> <span data-ttu-id="68574-202">此版本的 Limpet.exe 不应随最终产品一起提供。</span><span class="sxs-lookup"><span data-stu-id="68574-202">This version of Limpet.exe should not be shipped with your final product.</span></span> <span data-ttu-id="68574-203">相反，你需要构建开源项目，对其进行签名，然后将其与你的映像一起打包。</span><span class="sxs-lookup"><span data-stu-id="68574-203">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

### <a name="azure-clients-configuration"></a><span data-ttu-id="68574-204">Azure 客户端配置</span><span class="sxs-lookup"><span data-stu-id="68574-204">Azure Clients configuration</span></span>

<span data-ttu-id="68574-205">IoT 设备可以通过云服务进行远程管理。</span><span class="sxs-lookup"><span data-stu-id="68574-205">IoT devices can be remotely managed through cloud services.</span></span> <span data-ttu-id="68574-206">Azure 提供了一组丰富的服务来实现此类方案。</span><span class="sxs-lookup"><span data-stu-id="68574-206">Azure provides a rich set of services to enable such scenarios.</span></span> <span data-ttu-id="68574-207">我们创建了一个设备管理客户端，该客户端补充了 Azure 设备预配服务 (DPS) 和 Windows 平台上的 Azure IoT 中心服务，同时还公开了多个 Windows 可管理性功能。</span><span class="sxs-lookup"><span data-stu-id="68574-207">We have created a device management client that complements Azure's Device Provisioning Service (DPS) and Azure's IoT Hub service on the Windows platform and which also exposes several Windows manageability features.</span></span>

<span data-ttu-id="68574-208">客户端将作为开源项目提供。</span><span class="sxs-lookup"><span data-stu-id="68574-208">The clients will be provided as open-source projects.</span></span> <span data-ttu-id="68574-209">为了使测试变得更容易，我们将提供预先生成的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="68574-209">To make testing them easier, we will be providing pre-built binaries.</span></span> <span data-ttu-id="68574-210">可以使用 WDP 中的 "Azure 客户端" 选项卡来安装和运行这些测试二进制文件。</span><span class="sxs-lookup"><span data-stu-id="68574-210">You can use the 'Azure Clients' tab in WDP to install and run those test binaries.</span></span>

> [!NOTE]
> <span data-ttu-id="68574-211">此版本的工具不应随最终产品一起提供。</span><span class="sxs-lookup"><span data-stu-id="68574-211">This version of the tools should not be shipped with your final product.</span></span> <span data-ttu-id="68574-212">相反，你需要构建开源项目，对其进行签名，然后将其与你的映像一起打包。</span><span class="sxs-lookup"><span data-stu-id="68574-212">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

<span data-ttu-id="68574-213">当开源项目可用于使用后，我们将更新此文档。</span><span class="sxs-lookup"><span data-stu-id="68574-213">We will update this documentation once the open-source projects are available for consumption.</span></span>

### <a name="remote"></a><span data-ttu-id="68574-214">Remote</span><span class="sxs-lookup"><span data-stu-id="68574-214">Remote</span></span>
<span data-ttu-id="68574-215">Windows IoT 远程服务器允许用户查看其设备的显示内容，而无需将物理监视器连接到键盘。</span><span class="sxs-lookup"><span data-stu-id="68574-215">The Windows IoT Remote Server allows users to see what their device is displaying without connecting a physical monitor to the keyboard.</span></span>


## <a name="additional-information"></a><span data-ttu-id="68574-216">其他信息</span><span class="sxs-lookup"><span data-stu-id="68574-216">Additional Information</span></span>

### <a name="changing-the-default-port"></a><span data-ttu-id="68574-217">更改默认端口</span><span class="sxs-lookup"><span data-stu-id="68574-217">Changing the default port</span></span>

1. <span data-ttu-id="68574-218">启动 PowerShell 并 [连接到你的设备。](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="68574-218">Launch PowerShell and [connect to your device.](../connect-your-device/PowerShell.md)</span></span>
2. <span data-ttu-id="68574-219">下载 [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) 工具，生成它，然后将其复制到你的设备。</span><span class="sxs-lookup"><span data-stu-id="68574-219">Download [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, build it, and copy it to your device.</span></span>
3. <span data-ttu-id="68574-220">通过运行来取得服务的注册表项的所有权</span><span class="sxs-lookup"><span data-stu-id="68574-220">Take ownership of the registry key for the service by running</span></span>
```
        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service
```
4. <span data-ttu-id="68574-221">通过修改注册表设置来设置所需的端口</span><span class="sxs-lookup"><span data-stu-id="68574-221">Set the desired port by modifying the registry settings</span></span>
```
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
```
5. <span data-ttu-id="68574-222">通过运行以下或重启设备重启 WebManagement 服务</span><span class="sxs-lookup"><span data-stu-id="68574-222">Restart the WebManagement service by running following or by restarting the device</span></span>
```
        net stop webmanagement ; net start webmanagement
```
### <a name="using-https"></a><span data-ttu-id="68574-223">使用 HTTPS</span><span class="sxs-lookup"><span data-stu-id="68574-223">Using HTTPS</span></span>

<span data-ttu-id="68574-224">如果要使用 HTTPS，请先获取上一部分所述的注册表项的所有权，并按如下所述设置 HttpsPort 和 EncryptionMode 注册表项，然后重新启动 webmanagement 服务</span><span class="sxs-lookup"><span data-stu-id="68574-224">If you want to use HTTPS, first take the ownership of the registry key as described in previous section and set the HttpsPort and EncryptionMode registry keys as below and then restart the webmanagement service</span></span>
```
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement
```
### <a name="provisioning-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="68574-225">使用自定义 SSL 证书预配设备门户</span><span class="sxs-lookup"><span data-stu-id="68574-225">Provisioning Device Portal with a custom SSL certificate</span></span>

<span data-ttu-id="68574-226">在 Windows 10 创意者更新中，Windows 设备门户为设备管理员添加了一种安装自定义证书以用于 HTTPS 通信的方式。</span><span class="sxs-lookup"><span data-stu-id="68574-226">In the Windows 10 Creators Update, the Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span>

<span data-ttu-id="68574-227">若要了解详细信息，请 [阅读 Windows 设备门户文档下的文档](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)。</span><span class="sxs-lookup"><span data-stu-id="68574-227">To learn more, [read the documentation under the Windows Device Portal docs](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span></span>

### <a name="crash-dump-settings-for-capturing-memory-dump"></a><span data-ttu-id="68574-228">捕获内存转储的故障转储设置：</span><span class="sxs-lookup"><span data-stu-id="68574-228">Crash Dump Settings for Capturing Memory Dump:</span></span>

<span data-ttu-id="68574-229">若要捕获完整的内存转储，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="68574-229">To capture a Full Memory Dump, do the following:</span></span>

1. <span data-ttu-id="68574-230">通过 WDP 连接到 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="68574-230">Connect to a IoT device through WDP.</span></span>

2. <span data-ttu-id="68574-231">从调试 > 调试设置-> 内核故障设置-> 故障转储类型。</span><span class="sxs-lookup"><span data-stu-id="68574-231">From Debug -> Debug settings -> Kernel crash settings -> Crash dump type.</span></span>

3. <span data-ttu-id="68574-232">选择 "使用内存) 完成内存转储 (。</span><span class="sxs-lookup"><span data-stu-id="68574-232">Select: Complete memory dump (in use memory).</span></span>
    <span data-ttu-id="68574-233">请确保设备重新启动后，设置才会生效。</span><span class="sxs-lookup"><span data-stu-id="68574-233">Make sure the device is rebooted for the setting to take effect.</span></span>

4. <span data-ttu-id="68574-234">验证 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` 是否已设置为0x1。</span><span class="sxs-lookup"><span data-stu-id="68574-234">Verify  that `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` is set to 0x1.</span></span>

5. <span data-ttu-id="68574-235">更新 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` 为0x0。</span><span class="sxs-lookup"><span data-stu-id="68574-235">Update `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` to 0x0.</span></span>

6. <span data-ttu-id="68574-236">请确保设备上有足够的空间用于生成此转储。</span><span class="sxs-lookup"><span data-stu-id="68574-236">Make sure you have enough space on the device for this Dump to be generated.</span></span> <span data-ttu-id="68574-237">你可以在此处配置更改 DumpFile 位置： `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span><span class="sxs-lookup"><span data-stu-id="68574-237">You can configure the changing the DumpFile location from here: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span></span>


## <a name="additional-resources"></a><span data-ttu-id="68574-238">其他资源</span><span class="sxs-lookup"><span data-stu-id="68574-238">Additional Resources</span></span>
___

1. [<span data-ttu-id="68574-239">Windows 设备门户的 "概述" 页</span><span class="sxs-lookup"><span data-stu-id="68574-239">Windows Device Portal overview page</span></span>](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
