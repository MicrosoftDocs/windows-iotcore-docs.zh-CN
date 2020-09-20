---
title: 在 Windows 10 IoT Core 设备上使用 WiFi
ms.date: 08/28/2017
ms.topic: article
description: 了解如何在 Windows 10 IoT Core 设备上使用、设置和配置 wifi。
keywords: windows iot，wifi，安装程序，设备
ms.openlocfilehash: 716dc8cec6a70977c7283773db8bc12b50d00f2e
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782539"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a><span data-ttu-id="54c0a-104">在 Windows 10 IoT Core 设备上使用 WiFi</span><span class="sxs-lookup"><span data-stu-id="54c0a-104">Using WiFi on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="54c0a-105">在 Windows 10 IoT Core 设备上，通过使用 USB WiFi 适配器支持 WiFi。</span><span class="sxs-lookup"><span data-stu-id="54c0a-105">WiFi is supported on Windows 10 IoT Core devices through the use of a USB WiFi adapter.</span></span> <span data-ttu-id="54c0a-106">使用 WiFi 提供有线连接的所有功能，包括 [SSH](../connect-your-device/SSH.md)、 [PowerShell](../connect-your-device/PowerShell.md)、 [Windows 设备门户](../manage-your-device/DevicePortal.md)和应用程序调试和部署。</span><span class="sxs-lookup"><span data-stu-id="54c0a-106">Using WiFi provides all the functionality of a wired connection, including [SSH](../connect-your-device/SSH.md), [PowerShell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), and application debugging and deployment.</span></span>

> [!NOTE]
> <span data-ttu-id="54c0a-107">插入有线以太网电缆会将 WiFi 替代为默认网络接口。</span><span class="sxs-lookup"><span data-stu-id="54c0a-107">Plugging in a wired Ethernet cable will override WiFi as the default network interface.</span></span>

### <a name="supported-adapters"></a><span data-ttu-id="54c0a-108">支持的适配器</span><span class="sxs-lookup"><span data-stu-id="54c0a-108">Supported Adapters</span></span>
<span data-ttu-id="54c0a-109">可以在 [受支持的硬件](../learn-about-hardware/HardwareCompatList.md) 页上找到已在 Windows 10 IoT Core 上测试的 WiFi 适配器列表。</span><span class="sxs-lookup"><span data-stu-id="54c0a-109">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span>

### <a name="configuring-wifi"></a><span data-ttu-id="54c0a-110">配置 WiFi</span><span class="sxs-lookup"><span data-stu-id="54c0a-110">Configuring WiFi</span></span>
<span data-ttu-id="54c0a-111">若要使用 WiFi，需要提供具有 WiFi 网络凭据的 Windows 10 IoT core。</span><span class="sxs-lookup"><span data-stu-id="54c0a-111">To use WiFi, you'll need to provide Windows 10 IoT core with the WiFi network credentials.</span></span> <span data-ttu-id="54c0a-112">除了介绍如何生成伴随式应用和 WPS 自定义解决方案的文档外，还提供了几种不同的选项来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="54c0a-112">In addition to documentation on how to build companion app and WPS custom solutions, there are a few different options for doing so listed below.</span></span>

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a><span data-ttu-id="54c0a-113">自定义辅助应用 & WPS Wi-fi 载入示例</span><span class="sxs-lookup"><span data-stu-id="54c0a-113">Custom Companion App & WPS Wi-Fi Onboarding Samples</span></span>

<span data-ttu-id="54c0a-114">目前，我们为开发人员提供了许多方法来为其设备构建自定义的 wifi 载入解决方案。</span><span class="sxs-lookup"><span data-stu-id="54c0a-114">Currently, we offer a number of ways for developers to build a custom wifi onboarding solution for their device.</span></span> 

> | <span data-ttu-id="54c0a-115">示例</span><span class="sxs-lookup"><span data-stu-id="54c0a-115">Samples</span></span> | <span data-ttu-id="54c0a-116">说明</span><span class="sxs-lookup"><span data-stu-id="54c0a-116">Description</span></span> | <span data-ttu-id="54c0a-117">优点</span><span class="sxs-lookup"><span data-stu-id="54c0a-117">Benefits</span></span>  |  <span data-ttu-id="54c0a-118">缺点</span><span class="sxs-lookup"><span data-stu-id="54c0a-118">Drawbacks</span></span>  |
> |-------------|----------|---------|---------|
> | [<span data-ttu-id="54c0a-119">辅助应用</span><span class="sxs-lookup"><span data-stu-id="54c0a-119">Companion App</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | <span data-ttu-id="54c0a-120">创建可配置设备 Wi-fi 的简单 Xamarin 应用程序。</span><span class="sxs-lookup"><span data-stu-id="54c0a-120">Create a simple Xamarin app that can configure your device's Wi-Fi.</span></span> |  <span data-ttu-id="54c0a-121">易于使用;IoT 核心的头或无外设;客户端跨平台工作</span><span class="sxs-lookup"><span data-stu-id="54c0a-121">Simple to use; Headed or headless for IoT Core; Clients work cross-platform</span></span> | <span data-ttu-id="54c0a-122">开发人员正在创建自己的协议;要求开发人员实现安全性</span><span class="sxs-lookup"><span data-stu-id="54c0a-122">Developer is creating his or her own protocol; requires developer to implement security</span></span> |
> | [<span data-ttu-id="54c0a-123">具有蓝牙 RFCOMM 的 IoT 载入</span><span class="sxs-lookup"><span data-stu-id="54c0a-123">IoT Onboarding with Bluetooth RFCOMM</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | <span data-ttu-id="54c0a-124">创建解决方案，将无外设 IoT 设备配置为使用 Bluetooth RFCOMM 连接到 Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="54c0a-124">Create solution to configure your headless IoT device to connect with your Wi-Fi using Bluetooth RFCOMM.</span></span>  | <span data-ttu-id="54c0a-125">在头设备或无外设设备上相关;使用熟悉的技术和概念;不需要 IoT 设备启动 SoftAP;不需要调整防火墙设置</span><span class="sxs-lookup"><span data-stu-id="54c0a-125">Relevant in headed or headless devices; Uses familiar technologies and concepts; Does not require IoT device to start a SoftAP; Does not need to adjust firewall settings</span></span> | <span data-ttu-id="54c0a-126">需要对客户端和服务器设备提供蓝牙支持;示例仅提供适用于 Windows 10 的客户端应用;服务器应用预定义/硬编码客户端设备的名称。</span><span class="sxs-lookup"><span data-stu-id="54c0a-126">Requires Bluetooth support for client and server devices; Sample only provides client app for Windows 10; Server app pre-defines/hard-codes the names of the client device.</span></span> |
> | [<span data-ttu-id="54c0a-127">通过 AllJoyn 加入 IoT</span><span class="sxs-lookup"><span data-stu-id="54c0a-127">IoT Onboarding with AllJoyn</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | <span data-ttu-id="54c0a-128">通过家庭 Wi-fi 网络远程加入无头 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="54c0a-128">Remotely join your headless IoT device with your home Wi-Fi network.</span></span> | <span data-ttu-id="54c0a-129">适用于 AllJoyn</span><span class="sxs-lookup"><span data-stu-id="54c0a-129">Works with AllJoyn</span></span> | <span data-ttu-id="54c0a-130">对 AllJoyn 的某些支持已弃用</span><span class="sxs-lookup"><span data-stu-id="54c0a-130">Some support for AllJoyn is deprecated</span></span> |
> | <span data-ttu-id="54c0a-131">适用于设备的 wi-fi 保护安装 (WPS) Api</span><span class="sxs-lookup"><span data-stu-id="54c0a-131">Wi-Fi Protected Setup (WPS) APIs for devices</span></span> | <span data-ttu-id="54c0a-132">执行 WPS 发现以查询网络支持的 WPS 方法。</span><span class="sxs-lookup"><span data-stu-id="54c0a-132">Perform WPS discovery to query the WPS methods supported by the network.</span></span> | <span data-ttu-id="54c0a-133">只需利用 [WiFiAdapter. GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) 和 [WiFiAdapter](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) 方法将 wi-fi 设备连接到特定网络。</span><span class="sxs-lookup"><span data-stu-id="54c0a-133">Simply leverage the [WiFiAdapter.GetWpsConfigurationAsync(WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) and [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) methods to connect wi-fi devices to specific networks.</span></span> | <span data-ttu-id="54c0a-134">你将需要熟悉这些 Api 才能利用它们。仅兼容启用了 WPS 的路由器</span><span class="sxs-lookup"><span data-stu-id="54c0a-134">You will need to become familiar with these APIs to leverage them.; only compatible with WPS-enabled routers</span></span>|

## <a name="headed-options"></a><span data-ttu-id="54c0a-135">方向选项：</span><span class="sxs-lookup"><span data-stu-id="54c0a-135">Headed Options:</span></span>

### <a name="option-1-startup-configuration"></a><span data-ttu-id="54c0a-136">选项1：启动配置</span><span class="sxs-lookup"><span data-stu-id="54c0a-136">Option 1: Startup Configuration</span></span>
<span data-ttu-id="54c0a-137">**必备组件：** Windows 10 IoT core 设备需要插入鼠标、键盘、显示器和 USB WiFi 适配器</span><span class="sxs-lookup"><span data-stu-id="54c0a-137">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="54c0a-138">首次使用受支持的 USB WiFi 适配器启动 Windows 10 IoT Core 时，会显示一个配置屏幕。</span><span class="sxs-lookup"><span data-stu-id="54c0a-138">The first time you boot Windows 10 IoT Core with a supported USB WiFi adapter, you will be presented with a configuration screen.</span></span>
<span data-ttu-id="54c0a-139">在 "配置" 屏幕上，选择你想要连接到的 WiFi 网络并提供密码。</span><span class="sxs-lookup"><span data-stu-id="54c0a-139">On the configuration screen, select the WiFi network you would like to connect to and supply the password.</span></span> <span data-ttu-id="54c0a-140">单击 " **连接** " 以启动连接。</span><span class="sxs-lookup"><span data-stu-id="54c0a-140">Click **connect** to initiate the connection.</span></span>

![启动 WiFi 配置屏幕](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a><span data-ttu-id="54c0a-142">选项2：默认应用配置</span><span class="sxs-lookup"><span data-stu-id="54c0a-142">Option 2: Default App Configuration</span></span>
<span data-ttu-id="54c0a-143">**必备组件：** Windows 10 IoT core 设备需要插入鼠标、键盘、显示器和 USB WiFi 适配器</span><span class="sxs-lookup"><span data-stu-id="54c0a-143">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="54c0a-144">配置 WiFi 的另一种方法是使用默认应用。</span><span class="sxs-lookup"><span data-stu-id="54c0a-144">An alternative way to configure WiFi is to use the default app.</span></span> <span data-ttu-id="54c0a-145">可以使用此设置在设备启动后配置或修改 WiFi 设置。</span><span class="sxs-lookup"><span data-stu-id="54c0a-145">You can use this to configure or modify WiFi settings after the device has booted.</span></span>

1. <span data-ttu-id="54c0a-146">单击主页上的 "齿轮形设置" 图标</span><span class="sxs-lookup"><span data-stu-id="54c0a-146">Click on the gear-shaped settings icon on the homepage</span></span>
2. <span data-ttu-id="54c0a-147">在左窗格中选择 " **网络 & wi-fi** "</span><span class="sxs-lookup"><span data-stu-id="54c0a-147">Select **Network & Wi-Fi** in the left pane</span></span>
3. <span data-ttu-id="54c0a-148">单击要连接到的 WiFi 网络。</span><span class="sxs-lookup"><span data-stu-id="54c0a-148">Click on the WiFi network you want to connect to.</span></span> <span data-ttu-id="54c0a-149">如果出现提示，请提供密码，然后单击 "**连接**"</span><span class="sxs-lookup"><span data-stu-id="54c0a-149">Supply the password if prompted, and click **Connect**</span></span>

![默认应用 WiFi 配置](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a><span data-ttu-id="54c0a-151">无外设选项：</span><span class="sxs-lookup"><span data-stu-id="54c0a-151">Headless Options:</span></span>




### <a name="option-1-web-based-configuration"></a><span data-ttu-id="54c0a-152">选项1：基于 Web 的配置</span><span class="sxs-lookup"><span data-stu-id="54c0a-152">Option 1: Web-Based Configuration</span></span>
<span data-ttu-id="54c0a-153">**必备组件：** 你的设备将需要通过以太网连接到你的本地网络，并应插入 USB WiFi 适配器</span><span class="sxs-lookup"><span data-stu-id="54c0a-153">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="54c0a-154">如果你的设备没有 UI、显示或输入设备，你仍可以通过 [Windows 设备门户](../manage-your-device/DevicePortal.md)进行配置。</span><span class="sxs-lookup"><span data-stu-id="54c0a-154">If you have a device with no UI, display, or input devices, you can still configure it through the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>
<span data-ttu-id="54c0a-155">在 **Windows 10 IoT Core 仪表板**中， *单击* 设备的 " **在设备门户中打开** " 图标。</span><span class="sxs-lookup"><span data-stu-id="54c0a-155">In **Windows 10 IoT Core Dashboard**, *Click* on the **Open in Device Portal** icon for your device.</span></span>

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. <span data-ttu-id="54c0a-156">输入用户名的 **管理员** ，并在 p@ssw0rd 默认情况下提供密码 () </span><span class="sxs-lookup"><span data-stu-id="54c0a-156">Enter **Administrator** for the username, and supply your password (p@ssw0rd by default)</span></span>
2. <span data-ttu-id="54c0a-157">单击左侧窗格中的 " **网络** "</span><span class="sxs-lookup"><span data-stu-id="54c0a-157">Click on **Network** in the left-hand pane</span></span>
3. <span data-ttu-id="54c0a-158">在 " **可用网络**" 下，选择要连接到的网络并提供连接凭据。</span><span class="sxs-lookup"><span data-stu-id="54c0a-158">Under **Available networks**, select network you would like to connect to and supply the connection credentials.</span></span> <span data-ttu-id="54c0a-159">单击 " **连接** " 以启动连接</span><span class="sxs-lookup"><span data-stu-id="54c0a-159">Click **Connect** to initiate the connection</span></span>

![基于 Web 的 WiFi 配置](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a><span data-ttu-id="54c0a-161">选项2：使用 WiFi 配置文件进行连接</span><span class="sxs-lookup"><span data-stu-id="54c0a-161">Option 2: Connect using WiFi Profiles</span></span>

<span data-ttu-id="54c0a-162">**必备组件：** 你的设备将需要通过以太网连接到你的本地网络，并应插入 USB WiFi 适配器。</span><span class="sxs-lookup"><span data-stu-id="54c0a-162">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in.</span></span> <span data-ttu-id="54c0a-163">还需要具有 WiFi 功能的 Windows 电脑。</span><span class="sxs-lookup"><span data-stu-id="54c0a-163">You also need a Windows PC with WiFi capability.</span></span>

<span data-ttu-id="54c0a-164">Windows 10 IoT Core 支持使用无线配置文件设置 WiFi。</span><span class="sxs-lookup"><span data-stu-id="54c0a-164">Setting up WiFi using wireless profiles is supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="54c0a-165">有关详细信息和示例，请参阅 [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) 。</span><span class="sxs-lookup"><span data-stu-id="54c0a-165">See [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) for details and examples.</span></span>

1. <span data-ttu-id="54c0a-166">将 Windows 电脑连接到所需的无线网络，并创建具有以下命令的 WiFi 配置文件 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="54c0a-166">Connect your Windows PC to the desired wireless network and create WiFi profile XML file with these commands:</span></span>

    * <span data-ttu-id="54c0a-167">`netsh wlan show profiles` -> 查找刚添加的配置文件的名称</span><span class="sxs-lookup"><span data-stu-id="54c0a-167">`netsh wlan show profiles` -> find the name of the profile you just added</span></span>

    * <span data-ttu-id="54c0a-168">`netsh wlan export profile name=<your profilename>`.</span><span class="sxs-lookup"><span data-stu-id="54c0a-168">`netsh wlan export profile name=<your profilename>`.</span></span> <span data-ttu-id="54c0a-169">这会将配置文件导出到 XML 文件</span><span class="sxs-lookup"><span data-stu-id="54c0a-169">This will export the profile to an XML file</span></span>

2. <span data-ttu-id="54c0a-170">打开 **文件资源管理器** 窗口，在地址栏中键入， `\\<TARGET_DEVICE>\C$\` 然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="54c0a-170">Open up a **File Explorer** window, and in the address bar type `\\<TARGET_DEVICE>\C$\` and then hit enter.</span></span>  <span data-ttu-id="54c0a-171">在此特定情况下， `<TARGET_DEVICE>` 为 Windows 10 IoT Core 设备的名称或 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="54c0a-171">In this particular case, `<TARGET_DEVICE>` is either the name or the IP address of your Windows 10 IoT Core device:</span></span>

    ![具有文件资源管理器的 SMB](../media/SetupWifi/smb1.png)

    <span data-ttu-id="54c0a-173">如果系统提示你输入用户名和密码，请使用以下凭据：</span><span class="sxs-lookup"><span data-stu-id="54c0a-173">If you are prompted for a user name and password, use the following credentials:</span></span>

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![具有文件资源管理器的 SMB](../media/SetupWifi/cred1.png)

> [!NOTE]
> <span data-ttu-id="54c0a-175">**强烈建议**您更新管理员帐户的默认密码。</span><span class="sxs-lookup"><span data-stu-id="54c0a-175">It is **highly recommended** that you update the default password for the Administrator account.</span></span>  <span data-ttu-id="54c0a-176">请按照 [此处](../connect-your-device/PowerShell.md)的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="54c0a-176">Please follow the instructions found [here](../connect-your-device/PowerShell.md).</span></span>

3. <span data-ttu-id="54c0a-177">将导出的 WiFi 配置文件 XML 文件从 Windows 电脑复制到 Windows 10 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="54c0a-177">Copy the exported WiFi profile XML file from the Windows PC to your Windows 10 IoT Core device</span></span>

4. <span data-ttu-id="54c0a-178">使用 [PowerShell](../connect-your-device/PowerShell.md) 连接到设备，并通过执行以下命令将新的 WiFi 配置文件添加到设备</span><span class="sxs-lookup"><span data-stu-id="54c0a-178">Connect to your device using [PowerShell](../connect-your-device/PowerShell.md) and add the new WiFi profile to your device by executing the following commands</span></span>

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. <span data-ttu-id="54c0a-179">通过 netsh 将 Windows 10 IoT Core 设备连接到无线网络</span><span class="sxs-lookup"><span data-stu-id="54c0a-179">Connect the Windows 10 IoT Core device to wireless network via netsh</span></span>

    * `netsh wlan connect name=<profile name>`

6. <span data-ttu-id="54c0a-180">验证设备是否已连接到无线网络并可访问 internet</span><span class="sxs-lookup"><span data-stu-id="54c0a-180">Verify that your device is connected to the wireless network and can reach the internet</span></span>

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a><span data-ttu-id="54c0a-181">连接到 WPA2-PSK 个人网络</span><span class="sxs-lookup"><span data-stu-id="54c0a-181">Connecting to WPA2-PSK Personal networks</span></span>

<span data-ttu-id="54c0a-182">如果需要连接到 WPA2-PSK 个人 WiFi 网络，请先按照上面的说明进行操作，但对 XML 文件进行以下更改。</span><span class="sxs-lookup"><span data-stu-id="54c0a-182">If you need to connect to a WPA2-PSK Personal WiFi network, follow the instructions above first, but make the following changes to the XML file.</span></span> <span data-ttu-id="54c0a-183">唯一的区别在于，当 Windows 电脑导出 XML 时，它会对密码进行加密。</span><span class="sxs-lookup"><span data-stu-id="54c0a-183">The only difference is that when your Windows PC exports the XML it encrypts the password.</span></span>

> [!WARNING] 
> <span data-ttu-id="54c0a-184">这会使连接不安全。</span><span class="sxs-lookup"><span data-stu-id="54c0a-184">This will make your connection insecure.</span></span>

<span data-ttu-id="54c0a-185">从 Windows 电脑导出的配置文件 XML：</span><span class="sxs-lookup"><span data-stu-id="54c0a-185">Profile XML exported from Windows PC:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


<span data-ttu-id="54c0a-186">需要在 Windows 10 IoT Core 上运行的更改：</span><span class="sxs-lookup"><span data-stu-id="54c0a-186">Changes needed to work on Windows 10 IoT Core:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
