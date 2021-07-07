---
title: Windows 设备门户
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 设备门户远程配置和管理设备。
keywords: windows iot， Windows 设备门户， 远程， 设备门户
ms.openlocfilehash: 37d51ab3043630b08ea13e4c65858bcda8fbe1a1
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229474"
---
# <a name="windows-device-portal"></a><span data-ttu-id="8a4f7-104">Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="8a4f7-104">Windows Device Portal</span></span>
   <span data-ttu-id="8a4f7-105">使用 Windows 设备门户 (WDP) ，可以远程通过本地网络配置和管理设备。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-105">The Windows Device Portal (WDP) lets you configure and manage your device remotely over your local network.</span></span>
<span data-ttu-id="8a4f7-106">主要功能记录在Windows 设备门户[页上](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="8a4f7-106">The main features are documented on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

![设备门户主页](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> <span data-ttu-id="8a4f7-108">请勿将创客映像用于商业化。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="8a4f7-109">若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="8a4f7-110">在[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-110">Learn more [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!WARNING]
> <span data-ttu-id="8a4f7-111">ARM 设备当前无法进行实时内核调试。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-111">Live kernel debug is currently failing for ARM devices.</span></span> <span data-ttu-id="8a4f7-112">我们正在努力修复这一问题。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-112">We are working to get this fixed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a4f7-113">如果要构建一个开源零售设备，用于商业部署到“特定/有限安装”（即工厂或零售商店），然后由最终用户进行最终配置，并且您要为客户登记归档，他们必须[获取 WDP 证书，并将其安装到 WDP 和联网的浏览器上，且在 WDP 更改了密码](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)，那么在这种范围狭窄的商用实例中使用 WDP 是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-113">If you are building an open retail device for commercial deployment to a "specific/limited installation" (i.e. factory or retail store) where the end-user does the final configuration and you document your customers that they must [obtain a certificate for WDP and install it on both WDP and connecting browsers and passwords are changed on WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), then using WDP in this narrow commercial instance is acceptable.</span></span> <span data-ttu-id="8a4f7-114">此方案中的零售映像仍 *不应包含* IOT_TOOLKIT，但应该使用 IOT_WEBBEXTN 包来拉取 WDP。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-114">Retail images in this scenario should still *not* include IOT_TOOLKIT, but should use the IOT_WEBBEXTN package to pull in WDP.</span></span>

## <a name="shared-documentation"></a><span data-ttu-id="8a4f7-115">共享文档</span><span class="sxs-lookup"><span data-stu-id="8a4f7-115">Shared Documentation</span></span>
<span data-ttu-id="8a4f7-116">WDP 是在所有设备之间共享的开发人员Windows 10工具。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-116">WDP is a developer tool shared among all Windows 10 devices.</span></span> <span data-ttu-id="8a4f7-117">每个产品都有其自己的独特功能，但核心功能是相同的。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-117">Each product has its own unique features, but the core functionality is the same.</span></span>
<span data-ttu-id="8a4f7-118">有关主要功能的文档，请参阅Windows 设备门户[页](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-118">Documentation for the main features is found on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span> <span data-ttu-id="8a4f7-119">以下文档的其余部分将特定于 IoT。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-119">The rest of the documentation below will be IoT specific.</span></span>

## <a name="set-up"></a><span data-ttu-id="8a4f7-120">设置</span><span class="sxs-lookup"><span data-stu-id="8a4f7-120">Set up</span></span>

<span data-ttu-id="8a4f7-121">有两种方法可以启动Windows 设备门户运行。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-121">There are two ways to go get the Windows Device Portal up and running.</span></span>

### <a name="1-windows-10-iot-dashboard"></a><span data-ttu-id="8a4f7-122">1.Windows 10 IoT 仪表板</span><span class="sxs-lookup"><span data-stu-id="8a4f7-122">1. Windows 10 IoT Dashboard</span></span>

<span data-ttu-id="8a4f7-123">首先，需要下载 Windows 10 IoT 仪表板，这是一[](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)种开发人员工具，可以轻松设置新设备。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-123">First, you'll want to download the [Windows 10 IoT Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard), a developer tool that makes it easy to set up new devices.</span></span> <span data-ttu-id="8a4f7-124">使用仪表板将图像刷Windows 10 IoT 核心版设备后，请检查设备是否显示在"我的设备"下。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-124">Once you've used the Dashboard to flash a Windows 10 IoT Core image onto your device, check that your device shows up under "My devices".</span></span>

<span data-ttu-id="8a4f7-125">然后，使用"操作"下的省略号选择"在 设备门户 中打开"。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-125">From there, use the ellipses under "Actions" to select "Open in Device Portal".</span></span> <span data-ttu-id="8a4f7-126">在这里，你将看到"设备门户"页，除非最初更改了凭据，否则默认凭据为：</span><span class="sxs-lookup"><span data-stu-id="8a4f7-126">From there, you'll be taken to the Device Portal authentication page where, unless you changed the credentials initially, the default credentials are:</span></span>
```
    Username: Administrator
    Password: p@ssw0rd
```
 ### <a name="2-browser"></a><span data-ttu-id="8a4f7-127">2.浏览器</span><span class="sxs-lookup"><span data-stu-id="8a4f7-127">2. Browser</span></span>
<span data-ttu-id="8a4f7-128">如果无法在仪表板中查找设备或不想使用仪表板，则还可以在设备门户 IP 地址加上终端来打开 `:8080` 设备。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-128">If you cannot find your device in the dashboard or prefer to skip using the dashboard, you can also open the Device Portal by entering the IP address of your device plus `:8080` onto the end.</span></span> <span data-ttu-id="8a4f7-129">正确完成后，应如下所示：</span><span class="sxs-lookup"><span data-stu-id="8a4f7-129">When done correctly, it should look something like this:</span></span>


   ![IoTDashboard 视图设备](../media/deviceportal/Dashboard-Action.gif)


## <a name="iot-specific-features"></a><span data-ttu-id="8a4f7-131">IoT 特定功能</span><span class="sxs-lookup"><span data-stu-id="8a4f7-131">IoT specific features</span></span>

### <a name="device-settings"></a><span data-ttu-id="8a4f7-132">设备设置</span><span class="sxs-lookup"><span data-stu-id="8a4f7-132">Device Settings</span></span>

<span data-ttu-id="8a4f7-133">IoT 核心添加复选框以启用或禁用 [屏幕键盘](../develop-your-app/OnScreenKeyboard.md)</span><span class="sxs-lookup"><span data-stu-id="8a4f7-133">IoT Core adds a checkbox to enable or disable the [on-screen keyboard](../develop-your-app/OnScreenKeyboard.md)</span></span>
> [!NOTE]
> <span data-ttu-id="8a4f7-134">此复选框有一个已知 bug，其中它将"闪烁"从选中状态"闪烁"为"未选中"。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-134">This checkbox has a known bug where it will "flash" from checked to non-checked.</span></span> <span data-ttu-id="8a4f7-135">请在单击后 (F5) 页面，以确保复选框显示所需状态。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-135">Please refresh the page (F5) after clicking to ensure that the checkbox is showing your desired state.</span></span>

### <a name="apps"></a><span data-ttu-id="8a4f7-136">应用</span><span class="sxs-lookup"><span data-stu-id="8a4f7-136">Apps</span></span>
<span data-ttu-id="8a4f7-137">为设备上 AppX 包和捆绑包提供安装/卸载功能。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-137">Provides install/uninstall functionality for AppX packages and bundles on your device.</span></span>
<span data-ttu-id="8a4f7-138">![应用列表](../media/DevicePortal/AppList.png)</span><span class="sxs-lookup"><span data-stu-id="8a4f7-138">![App list](../media/DevicePortal/AppList.png)</span></span>

<span data-ttu-id="8a4f7-139">IoT 核心是唯一的，因为它只允许一次运行一个前台应用。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-139">IoT Core is unique in that it only allows one foreground app to run at one time.</span></span> <span data-ttu-id="8a4f7-140">修改应用列表以确保情况如此。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-140">The app list is modified to ensure that this is the case.</span></span> <span data-ttu-id="8a4f7-141">在 **"启动** "列下，可以选择默认启动的后台应用程序，但只能设置一个前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-141">Under the **STARTUP** column, you can select as many background applications to start by default, but can only set one foreground application.</span></span>  

### <a name="app-file-explorer"></a><span data-ttu-id="8a4f7-142">应用文件资源管理器</span><span class="sxs-lookup"><span data-stu-id="8a4f7-142">App File Explorer</span></span>

<span data-ttu-id="8a4f7-143">应用文件资源管理器显示应用可以访问的目录。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-143">The app file explorer shows the directories that your apps can access.</span></span>

* <span data-ttu-id="8a4f7-144">CameraRoll 在所有应用之间共享</span><span class="sxs-lookup"><span data-stu-id="8a4f7-144">CameraRoll is shared among all apps</span></span>
* <span data-ttu-id="8a4f7-145">文档在所有应用之间共享</span><span class="sxs-lookup"><span data-stu-id="8a4f7-145">Documents are shared among all apps</span></span>
* <span data-ttu-id="8a4f7-146">LocalAppData 包含特定于每个应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-146">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="8a4f7-147">此文件夹与应用的名称相同，其他应用无法访问它。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-147">This folder will be the same name as your app and other apps cannot access it.</span></span>

### <a name="debugging"></a><span data-ttu-id="8a4f7-148">调试</span><span class="sxs-lookup"><span data-stu-id="8a4f7-148">Debugging</span></span>

#### <a name="kernel-dumps"></a><span data-ttu-id="8a4f7-149">内核转储</span><span class="sxs-lookup"><span data-stu-id="8a4f7-149">Kernel dumps</span></span>
![使用内核转储进行调试](../media/DevicePortal/Debug1.png)

<span data-ttu-id="8a4f7-151">系统崩溃将自动记录，并且可以通过 Web 管理工具查看。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-151">Any system crashes will automatically be logged and available to view through the web management tool.</span></span>  <span data-ttu-id="8a4f7-152">然后，可以下载内核转储，并尝试找出发生什么问题。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-152">You can then download the kernel dump and try to figure out what's going on.</span></span>

#### <a name="process-dumps"></a><span data-ttu-id="8a4f7-153">进程转储</span><span class="sxs-lookup"><span data-stu-id="8a4f7-153">Process dumps</span></span>
![使用进程转储进行调试](../media/DevicePortal/Debug2.png)

<span data-ttu-id="8a4f7-155">这类似于实时内核转储，但适用于用户模式进程。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-155">This is similar to Live kernel dumps, but for the user mode processes.</span></span>
<span data-ttu-id="8a4f7-156">单击 **下载** 按钮将导致"minidump"，并且将下载该进程的整个状态。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-156">Clicking the **download** button will cause a 'minidump', and the entire state of that process will be downloaded.</span></span> <span data-ttu-id="8a4f7-157">这适用于调试挂起的进程。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-157">This is good for debugging hanging processes.</span></span>

#### <a name="kernel-crash-settings"></a><span data-ttu-id="8a4f7-158">内核崩溃设置</span><span class="sxs-lookup"><span data-stu-id="8a4f7-158">Kernel crash settings</span></span>
![内核崩溃设置](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a><span data-ttu-id="8a4f7-160">蓝牙</span><span class="sxs-lookup"><span data-stu-id="8a4f7-160">Bluetooth</span></span>
<span data-ttu-id="8a4f7-161">此页显示所有蓝牙配对设备和可发现的所有设备。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-161">This page shows you all the bluetooth paired devices and all the devices that are discoverable.</span></span> <span data-ttu-id="8a4f7-162">若要与另蓝牙设备配对，请使设备进入配对模式，并等待该设备显示在可用设备列表中。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-162">To pair with another Bluetooth device, put the device in pairing mode and wait for it to appear in the available devices list.</span></span>  
![蓝牙设备列表](../media/DevicePortal/Bluetooth.png)

<span data-ttu-id="8a4f7-164">单击" **配对"链接** 以配对设备。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-164">Click on **Pair link** to pair the device.</span></span> <span data-ttu-id="8a4f7-165">如果设备需要 PIN 进行配对，它将弹出一个显示 PIN 的消息框。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-165">If the device requires a PIN for pairing, it will pop up a message box displaying the PIN.</span></span> <span data-ttu-id="8a4f7-166">设备配对后，会显示在"配对设备"列表中。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-166">Once the device is paired, it will show up in the Paired devices list.</span></span> <span data-ttu-id="8a4f7-167">可以通过单击"删除"来对设备 **进行配对**。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-167">You can unpair the device by clicking on **Remove**.</span></span>

<span data-ttu-id="8a4f7-168">导航到"蓝牙"页后，设备将被其他设备发现。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-168">Once you navigate to the Bluetooth page, your device will be discoverable by other devices.</span></span> <span data-ttu-id="8a4f7-169">还可以从电脑/设备找到电话并在那里配对。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-169">You can also find it from your PC/Phone and pair it from there.</span></span>

<span data-ttu-id="8a4f7-170">有关蓝牙详细信息，请参阅 [蓝牙页](https://go.microsoft.com/fwlink/?linkid=823223)。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-170">More information on bluetooth can be found on the [bluetooth page](https://go.microsoft.com/fwlink/?linkid=823223).</span></span>

### <a name="iot-onboarding"></a><span data-ttu-id="8a4f7-171">IoT 载入</span><span class="sxs-lookup"><span data-stu-id="8a4f7-171">IoT Onboarding</span></span>

<span data-ttu-id="8a4f7-172">IoT 载入支持配置 IoT 设备Wi-Fi连接选项。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-172">IoT Onboarding provides support for configuring an IoT device's Wi-Fi connectivity options.</span></span>

<span data-ttu-id="8a4f7-173">**Internet 连接共享 (ICS)** 使用 Internet 连接共享，你可以与通过 SoftAP 连接到设备的其他设备共享Wi-Fi Internet 访问权限。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-173">**Internet Connection Sharing (ICS)** Internet Connection Sharing allows you to share the Internet access of your device with other devices connected to your device over the Wi-Fi SoftAP.</span></span>
<span data-ttu-id="8a4f7-174">若要使用此功能，Windows 10 IoT 设备需要有权访问 Internet (例如通过有线 LAN 连接) 。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-174">To use this feature, your Windows 10 IoT Device needs to have access to the internet (e.g. through a wired LAN connection).</span></span>  <span data-ttu-id="8a4f7-175">在"Connectivity->Onboarding->SoftAP 设置"中，单击"启用"并设置 SSID 名称和密码。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-175">In 'Connectivity->Onboarding->SoftAP settings' click 'enable' and set SSID name and password.</span></span>  <span data-ttu-id="8a4f7-176">然后在"连接>Internet 连接共享"中，为"接入点适配器"选择"Microsoft Wi-Fi 直接虚拟适配器 #2"，对于"共享网络适配器"，请选择有线以太网适配器。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-176">Then in 'Connectivity->Internet connection sharing' for 'access point adapter' select "Microsoft Wi-Fi Direct Virtual Adapter #2" and for 'shared network adapter' select your wired ethernet adapter.</span></span>  <span data-ttu-id="8a4f7-177">最后，单击"启动共享访问"。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-177">Finally, click 'start shared access.'</span></span>  <span data-ttu-id="8a4f7-178">启动后，将Wi-Fi设备连接到 IoT Windows 10 SoftAP。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-178">Once started, connect a separate Wi-Fi enabled device to the SoftAP on your Windows 10 IoT device.</span></span>  <span data-ttu-id="8a4f7-179">建立连接后，已启用Wi-Fi的设备可以通过 IoT 设备连接到Windows 10 Internet。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-179">After a connection is established, your separate Wi-Fi enabled device will be able to connect to the internet through your Windows 10 IoT device.</span></span>

> [!NOTE]
> <span data-ttu-id="8a4f7-180">当设备上存在一个Wi-Fi配置文件时，ICS 处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-180">ICS is disabled when a Wi-Fi profile exists on the device.</span></span>
><span data-ttu-id="8a4f7-181">例如，如果连接到 Wi-Fi访问点并选中"创建配置文件 (自动重新连接，ICS 将) "。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-181">For example, ICS will be disabled if you connect to a Wi-Fi access point and check “Create profile (auto re-connect)”.</span></span>

<span data-ttu-id="8a4f7-182">**SoftAP 设置** 使用 SoftAP 设置可控制是否启用设备的 SoftAP。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-182">**SoftAP Settings** The SoftAP Settings allow you to control whether or not your device's SoftAP is enabled.</span></span>  <span data-ttu-id="8a4f7-183">它还提供了一种配置 SoftAP SSID 和 WPA2-PSK 密钥（从另一台设备连接 SoftAP 所必需的）的方式。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-183">It also provides a means for configuring your SoftAP's SSID and the WPA2-PSK key, which are necessary to connect the SoftAP from another device.</span></span>

<span data-ttu-id="8a4f7-184">**AllJoyn 载入设置** AllJoyn 加入设置允许你控制是否可以通过设备的 AllJoyn Onboarding Producer 配置设备的 Wi-Fi 连接。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-184">**AllJoyn Onboarding Settings** The AllJoyn Onboarding Settings allow you to control whether or not your device's Wi-Fi connection can be configured through your device's AllJoyn Onboarding Producer.</span></span>  <span data-ttu-id="8a4f7-185">当运行 AllJoyn Onboarding Consumer 应用程序的单独设备连接到 Windows 10 IoT SoftAP 时，AllJoyn Onboarding Consumer 应用程序可用于配置 IoT 设备的 Wi-Fi 适配器。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-185">When a separate device running an AllJoyn Onboarding Consumer application connects to your Windows 10 IoT SoftAP, the AllJoyn Onboarding Consumer application can be used to configure your IoT device's Wi-Fi adapter.</span></span>  <span data-ttu-id="8a4f7-186">启用后，IoTOnboarding (AllJoyn Onboarding 生成者) 使用 ECDHE_NULL身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-186">When enabled, the AllJoyn Onboarding Producer app (IoTOnboarding) uses the ECDHE_NULL authentication method.</span></span>

> [!NOTE]
> <span data-ttu-id="8a4f7-187">若要将 AllJoyn Onboarding 与 Windows 10 IoT 内部版本 10.0.14393 或更早版本一起使用，需要对<strong>IotOnboarding</strong>示例进行更新，该示例可在此处[下载](https://github.com/ms-iot/samples)。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-187">To use AllJoyn Onboarding with Windows 10 IoT builds 10.0.14393 or earlier requires an update to the <strong>IotOnboarding</strong> sample which may be [downloaded here](https://github.com/ms-iot/samples).</span></span>

<span data-ttu-id="8a4f7-188">![载入到 ICS 上的 AllJoyn ](../media/DevicePortal/OnboardingAllJoyn.png)
 ![ 载入](../media/DevicePortal/OnboardingICS.png)</span><span class="sxs-lookup"><span data-stu-id="8a4f7-188">![Onboarding onto AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding onto ICS](../media/DevicePortal/OnboardingICS.png)</span></span>

> [!NOTE]
> <span data-ttu-id="8a4f7-189">接入点适配器是充当 WiFi 接入点的 WiFi 适配器 (它通常具有类似 192.168.137.1) 。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-189">Access point adapter is the WiFi adapter that act as a WiFi access point (it usually has an IP address like 192.168.137.1).</span></span>
> <span data-ttu-id="8a4f7-190">共享网络适配器是连接到 Internet (，例如：以太网适配器) 。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-190">Shared network adapter is the adapter that connects to Internet (e.g.: Ethernet adapter).</span></span>

![载入到软 AP](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> <span data-ttu-id="8a4f7-192">如果启用了 AllJoyn 载入，并且已用 Wifi 适配器的 MAC 地址进行附加，SoftAP SSID 将自动以"AJ_"作为前缀。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-192">SoftAP SSID will be automatically prefixed by "AJ_" if AllJoyn onboarding is enabled and postfixed with the MAC address of the Wifi adapter.</span></span> <span data-ttu-id="8a4f7-193">SoftAP 通行短语必须介于 8 到 63 个 ASCII 字符之间。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-193">The SoftAP passphrase must be between 8 and 63 ASCII characters.</span></span>


### <a name="tpm-configuration"></a><span data-ttu-id="8a4f7-194">TPM 配置</span><span class="sxs-lookup"><span data-stu-id="8a4f7-194">TPM configuration</span></span>
<span data-ttu-id="8a4f7-195">TPM 受信任的平台模块 (是) 处理器，包括随机数生成、加密密钥的安全生成及其使用限制等功能。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-195">The Trusted Platform Module (TPM) is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="8a4f7-196">它还包括远程证明和密封存储等功能。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-196">It also includes capabilities such as remote attestation and sealed storage.</span></span> <span data-ttu-id="8a4f7-197">若要了解 IoT 核心版上的 TPM 和安全性，请访问构建 [安全设备](../secure-your-device/BuildingSecureDevices.md) 页和 [TPM](../secure-your-device/TPM.md) 页。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-197">To learn about the TPM and security on IoT Core, visit the [Building secure devices](../secure-your-device/BuildingSecureDevices.md) page and the [TPM](../secure-your-device/TPM.md) page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a4f7-198">Limpet.exe IoT 核心Windows一部分。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-198">Limpet.exe used to be part of Windows IoT Core.</span></span> <span data-ttu-id="8a4f7-199">从 2018 年 10 月开始，它现已在 上作为开源项目提供 [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client) 。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-199">Starting with October 2018, it is now available as an open source porject at [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client).</span></span>

<span data-ttu-id="8a4f7-200">为了简化测试，我们提供了一个未签名的预生成版本Limpet.exe可从 WDP 下载。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-200">To make testing easier, we have a non-signed pre-built version of Limpet.exe available and can be downloaded right from WDP.</span></span> <span data-ttu-id="8a4f7-201">只需转到"TPM 配置"选项卡，然后单击"安装最新"按钮。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-201">You just need to go the 'TPM Configuration' tab and click the 'Install Latest' button.</span></span>

> [!NOTE]
> <span data-ttu-id="8a4f7-202">此版本的 Limpet.exe不得随最终产品一起提供。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-202">This version of Limpet.exe should not be shipped with your final product.</span></span> <span data-ttu-id="8a4f7-203">相反，你需要生成开放源代码项目，对该项目进行签名，然后使用映像打包该项目。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-203">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

### <a name="azure-clients-configuration"></a><span data-ttu-id="8a4f7-204">Azure 客户端配置</span><span class="sxs-lookup"><span data-stu-id="8a4f7-204">Azure Clients configuration</span></span>

<span data-ttu-id="8a4f7-205">可以通过云服务远程管理 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-205">IoT devices can be remotely managed through cloud services.</span></span> <span data-ttu-id="8a4f7-206">Azure 提供了一组丰富的服务来启用此类方案。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-206">Azure provides a rich set of services to enable such scenarios.</span></span> <span data-ttu-id="8a4f7-207">我们创建了一个设备管理客户端，用于补充 Azure 的设备预配服务 (DPS) 和 Windows 平台上的 Azure IoT 中心服务，并公开了多个 Windows 可管理性功能。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-207">We have created a device management client that complements Azure's Device Provisioning Service (DPS) and Azure's IoT Hub service on the Windows platform and which also exposes several Windows manageability features.</span></span>

<span data-ttu-id="8a4f7-208">客户端将作为开放源代码项目提供。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-208">The clients will be provided as open-source projects.</span></span> <span data-ttu-id="8a4f7-209">为了更轻松地测试它们，我们将提供预建的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-209">To make testing them easier, we will be providing pre-built binaries.</span></span> <span data-ttu-id="8a4f7-210">可以使用 WDP 中的"Azure 客户端"选项卡来安装和运行这些测试二进制文件。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-210">You can use the 'Azure Clients' tab in WDP to install and run those test binaries.</span></span>

> [!NOTE]
> <span data-ttu-id="8a4f7-211">此版本的工具不应随最终产品一起提供。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-211">This version of the tools should not be shipped with your final product.</span></span> <span data-ttu-id="8a4f7-212">相反，你需要生成开放源代码项目，对该项目进行签名，然后使用映像打包该项目。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-212">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

<span data-ttu-id="8a4f7-213">开放源代码项目可供使用后，我们将更新此文档。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-213">We will update this documentation once the open-source projects are available for consumption.</span></span>

### <a name="remote"></a><span data-ttu-id="8a4f7-214">Remote</span><span class="sxs-lookup"><span data-stu-id="8a4f7-214">Remote</span></span>
<span data-ttu-id="8a4f7-215">使用 Windows IoT 远程服务器，用户可以在不将物理监视器连接到键盘的情况下查看其设备显示内容。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-215">The Windows IoT Remote Server allows users to see what their device is displaying without connecting a physical monitor to the keyboard.</span></span>


## <a name="additional-information"></a><span data-ttu-id="8a4f7-216">其他信息</span><span class="sxs-lookup"><span data-stu-id="8a4f7-216">Additional Information</span></span>

### <a name="changing-the-default-port"></a><span data-ttu-id="8a4f7-217">更改默认端口</span><span class="sxs-lookup"><span data-stu-id="8a4f7-217">Changing the default port</span></span>

1. <span data-ttu-id="8a4f7-218">启动 PowerShell [并连接到设备。](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="8a4f7-218">Launch PowerShell and [connect to your device.](../connect-your-device/PowerShell.md)</span></span>
2. <span data-ttu-id="8a4f7-219">下载 [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) 工具，生成该工具，并复制到设备。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-219">Download [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, build it, and copy it to your device.</span></span>
3. <span data-ttu-id="8a4f7-220">通过运行 来取得服务注册表项的所有权</span><span class="sxs-lookup"><span data-stu-id="8a4f7-220">Take ownership of the registry key for the service by running</span></span>
```
        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service
```
4. <span data-ttu-id="8a4f7-221">通过修改注册表设置设置所需的端口</span><span class="sxs-lookup"><span data-stu-id="8a4f7-221">Set the desired port by modifying the registry settings</span></span>
```
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
```
5. <span data-ttu-id="8a4f7-222">通过运行以下代码或重启设备来重启 WebManagement 服务</span><span class="sxs-lookup"><span data-stu-id="8a4f7-222">Restart the WebManagement service by running following or by restarting the device</span></span>
```
        net stop webmanagement ; net start webmanagement
```
### <a name="using-https"></a><span data-ttu-id="8a4f7-223">使用 HTTPS</span><span class="sxs-lookup"><span data-stu-id="8a4f7-223">Using HTTPS</span></span>

<span data-ttu-id="8a4f7-224">如果要使用 HTTPS，请首先获得上一部分中所述的注册表项的所有权，并设置如下所示的 HttpsPort 和 EncryptionMode 注册表项，然后重启 webmanagement 服务</span><span class="sxs-lookup"><span data-stu-id="8a4f7-224">If you want to use HTTPS, first take the ownership of the registry key as described in previous section and set the HttpsPort and EncryptionMode registry keys as below and then restart the webmanagement service</span></span>
```
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement
```
### <a name="provisioning-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="8a4f7-225">使用设备门户 SSL 证书预配证书</span><span class="sxs-lookup"><span data-stu-id="8a4f7-225">Provisioning Device Portal with a custom SSL certificate</span></span>

<span data-ttu-id="8a4f7-226">在Windows 10 创意者更新中，Windows 设备门户为设备管理员添加了一种安装自定义证书以用于 HTTPS 通信的方法。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-226">In the Windows 10 Creators Update, the Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span>

<span data-ttu-id="8a4f7-227">若要了解有关详细信息，[请阅读文档 下Windows 设备门户文档](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-227">To learn more, [read the documentation under the Windows Device Portal docs](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span></span>

### <a name="crash-dump-settings-for-capturing-memory-dump"></a><span data-ttu-id="8a4f7-228">用于设置内存转储的故障转储对象：</span><span class="sxs-lookup"><span data-stu-id="8a4f7-228">Crash Dump Settings for Capturing Memory Dump:</span></span>

<span data-ttu-id="8a4f7-229">若要捕获完整内存转储，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="8a4f7-229">To capture a Full Memory Dump, do the following:</span></span>

1. <span data-ttu-id="8a4f7-230">连接 WDP 连接到 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-230">Connect to a IoT device through WDP.</span></span>

2. <span data-ttu-id="8a4f7-231">从"调试>调试设置 ->内核故障设置 ->故障转储类型" 。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-231">From Debug -> Debug settings -> Kernel crash settings -> Crash dump type.</span></span>

3. <span data-ttu-id="8a4f7-232">选择：完成 (内存转储) 。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-232">Select: Complete memory dump (in use memory).</span></span>
    <span data-ttu-id="8a4f7-233">确保重启设备，设置生效。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-233">Make sure the device is rebooted for the setting to take effect.</span></span>

4. <span data-ttu-id="8a4f7-234">验证 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` 是否设置为 0x1。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-234">Verify  that `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` is set to 0x1.</span></span>

5. <span data-ttu-id="8a4f7-235">更新 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` 到 0x0。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-235">Update `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` to 0x0.</span></span>

6. <span data-ttu-id="8a4f7-236">请确保设备上有足够的空间来生成此转储。</span><span class="sxs-lookup"><span data-stu-id="8a4f7-236">Make sure you have enough space on the device for this Dump to be generated.</span></span> <span data-ttu-id="8a4f7-237">可以从此处配置更改 DumpFile 位置： `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span><span class="sxs-lookup"><span data-stu-id="8a4f7-237">You can configure the changing the DumpFile location from here: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span></span>


## <a name="additional-resources"></a><span data-ttu-id="8a4f7-238">其他资源</span><span class="sxs-lookup"><span data-stu-id="8a4f7-238">Additional Resources</span></span>
___

1. [<span data-ttu-id="8a4f7-239">Windows设备门户概述页</span><span class="sxs-lookup"><span data-stu-id="8a4f7-239">Windows Device Portal overview page</span></span>](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
