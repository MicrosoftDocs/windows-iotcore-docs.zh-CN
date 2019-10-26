---
title: 在 Windows 10 IoT 核心版设备上使用 WiFi
ms.date: 08/28/2017
ms.topic: article
description: 了解如何在 Windows 10 IoT Core 设备上使用、设置和配置 wifi。
keywords: windows iot，wifi，安装程序，设备
ms.openlocfilehash: b8fa691da0560a741c0078d0030f10ae4ceb6c17
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918300"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a><span data-ttu-id="9f41d-104">在 Windows 10 IoT 核心版设备上使用 WiFi</span><span class="sxs-lookup"><span data-stu-id="9f41d-104">Using WiFi on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="9f41d-105">在使用 USB WLAN 适配器的过程中，WLAN 在 Windows 10 IoT 核心版设备上受支持。</span><span class="sxs-lookup"><span data-stu-id="9f41d-105">WiFi is supported on Windows 10 IoT Core devices through the use of a USB WiFi adapter.</span></span> <span data-ttu-id="9f41d-106">使用 WLAN 可提供有线连接的所有功能，包括 [SSH](../connect-your-device/SSH.md)、[Powershell](../connect-your-device/PowerShell.md)、[Windows Device Portal](../manage-your-device/DevicePortal.md) 以及应用程序调试和部署。</span><span class="sxs-lookup"><span data-stu-id="9f41d-106">Using WiFi provides all the functionality of a wired connection, including [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), and application debugging and deployment.</span></span>

> [!NOTE]
> <span data-ttu-id="9f41d-107">插入有线以太网电缆会将 WiFi 替代为默认网络接口。</span><span class="sxs-lookup"><span data-stu-id="9f41d-107">Plugging in a wired Ethernet cable will override WiFi as the default network interface.</span></span>

### <a name="supported-adapters"></a><span data-ttu-id="9f41d-108">支持的适配器</span><span class="sxs-lookup"><span data-stu-id="9f41d-108">Supported Adapters</span></span>
<span data-ttu-id="9f41d-109">可以在[受支持的硬件](../learn-about-hardware/HardwareCompatList.md)页上找到已在 Windows 10 IoT Core 上测试的 WiFi 适配器列表。</span><span class="sxs-lookup"><span data-stu-id="9f41d-109">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span>

### <a name="configuring-wifi"></a><span data-ttu-id="9f41d-110">配置 WLAN</span><span class="sxs-lookup"><span data-stu-id="9f41d-110">Configuring WiFi</span></span>
<span data-ttu-id="9f41d-111">若要使用 WiFi，将需要向 Windows 10 IoT 核心版提供 WiFi 网络凭据。</span><span class="sxs-lookup"><span data-stu-id="9f41d-111">To use WiFi, you'll need to provide Windows 10 IoT core with the WiFi network credentials.</span></span> <span data-ttu-id="9f41d-112">除了介绍如何生成伴随式应用和 WPS 自定义解决方案的文档外，还提供了几种不同的选项来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="9f41d-112">In addition to documentation on how to build companion app and WPS custom solutions, there are a few different options for doing so listed below.</span></span>

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a><span data-ttu-id="9f41d-113">自定义辅助应用 & WPS Wi-fi 载入示例</span><span class="sxs-lookup"><span data-stu-id="9f41d-113">Custom Companion App & WPS Wi-Fi Onboarding Samples</span></span>

<span data-ttu-id="9f41d-114">目前，我们为开发人员提供了许多方法来为其设备构建自定义的 wifi 载入解决方案。</span><span class="sxs-lookup"><span data-stu-id="9f41d-114">Currently, we offer a number of ways for developers to build a custom wifi onboarding solution for their device.</span></span> 

> | <span data-ttu-id="9f41d-115">示例</span><span class="sxs-lookup"><span data-stu-id="9f41d-115">Samples</span></span> | <span data-ttu-id="9f41d-116">描述</span><span class="sxs-lookup"><span data-stu-id="9f41d-116">Description</span></span> | <span data-ttu-id="9f41d-117">优势</span><span class="sxs-lookup"><span data-stu-id="9f41d-117">Benefits</span></span>  |  <span data-ttu-id="9f41d-118">弊端</span><span class="sxs-lookup"><span data-stu-id="9f41d-118">Drawbacks</span></span>  |
> |-------------|----------|---------|---------|
> | [<span data-ttu-id="9f41d-119">辅助应用</span><span class="sxs-lookup"><span data-stu-id="9f41d-119">Companion App</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | <span data-ttu-id="9f41d-120">创建可配置设备 Wi-fi 的简单 Xamarin 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9f41d-120">Create a simple Xamarin app that can configure your device's Wi-Fi.</span></span> |  <span data-ttu-id="9f41d-121">易于使用;IoT 核心的头或无外设;客户端跨平台工作</span><span class="sxs-lookup"><span data-stu-id="9f41d-121">Simple to use; Headed or headless for IoT Core; Clients work cross-platform</span></span> | <span data-ttu-id="9f41d-122">开发人员正在创建自己的协议;要求开发人员实现安全性</span><span class="sxs-lookup"><span data-stu-id="9f41d-122">Developer is creating his or her own protocol; requires developer to implement security</span></span> |
> | [<span data-ttu-id="9f41d-123">具有蓝牙 RFCOMM 的 IoT 载入</span><span class="sxs-lookup"><span data-stu-id="9f41d-123">IoT Onboarding with Bluetooth RFCOMM</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | <span data-ttu-id="9f41d-124">创建解决方案，将无外设 IoT 设备配置为使用 Bluetooth RFCOMM 连接到 Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="9f41d-124">Create solution to configure your headless IoT device to connect with your Wi-Fi using Bluetooth RFCOMM.</span></span>  | <span data-ttu-id="9f41d-125">在头设备或无外设设备上相关;使用熟悉的技术和概念;不需要 IoT 设备启动 SoftAP;不需要调整防火墙设置</span><span class="sxs-lookup"><span data-stu-id="9f41d-125">Relevant in headed or headless devices; Uses familiar technologies and concepts; Does not require IoT device to start a SoftAP; Does not need to adjust firewall settings</span></span> | <span data-ttu-id="9f41d-126">需要对客户端和服务器设备提供蓝牙支持;示例仅提供适用于 Windows 10 的客户端应用;服务器应用预定义/硬编码客户端设备的名称。</span><span class="sxs-lookup"><span data-stu-id="9f41d-126">Requires Bluetooth support for client and server devices; Sample only provides client app for Windows 10; Server app pre-defines/hard-codes the names of the client device.</span></span> |
> | [<span data-ttu-id="9f41d-127">通过 AllJoyn 加入 IoT</span><span class="sxs-lookup"><span data-stu-id="9f41d-127">IoT Onboarding with AllJoyn</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | <span data-ttu-id="9f41d-128">通过家庭 Wi-fi 网络远程加入无头 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="9f41d-128">Remotely join your headless IoT device with your home Wi-Fi network.</span></span> | <span data-ttu-id="9f41d-129">适用于 AllJoyn</span><span class="sxs-lookup"><span data-stu-id="9f41d-129">Works with AllJoyn</span></span> | <span data-ttu-id="9f41d-130">对 AllJoyn 的某些支持已弃用</span><span class="sxs-lookup"><span data-stu-id="9f41d-130">Some support for AllJoyn is deprecated</span></span> |
> | <span data-ttu-id="9f41d-131">适用于设备的 wi-fi 保护的安装程序（WPS） Api</span><span class="sxs-lookup"><span data-stu-id="9f41d-131">Wi-Fi Protected Setup (WPS) APIs for devices</span></span> | <span data-ttu-id="9f41d-132">执行 WPS 发现以查询网络支持的 WPS 方法。</span><span class="sxs-lookup"><span data-stu-id="9f41d-132">Perform WPS discovery to query the WPS methods supported by the network.</span></span> | <span data-ttu-id="9f41d-133">只需利用[WiFiAdapter GetWpsConfigurationAsync （WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync)和[WiFiAdapter](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync)方法将 wi-fi 设备连接到特定网络即可。</span><span class="sxs-lookup"><span data-stu-id="9f41d-133">Simply leverage the [WiFiAdapter.GetWpsConfigurationAsync(WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) and [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) methods to connect wi-fi devices to specific networks.</span></span> | <span data-ttu-id="9f41d-134">你将需要熟悉这些 Api 才能利用它们。仅兼容启用了 WPS 的路由器</span><span class="sxs-lookup"><span data-stu-id="9f41d-134">You will need to become familiar with these APIs to leverage them.; only compatible with WPS-enabled routers</span></span>|

## <a name="headed-options"></a><span data-ttu-id="9f41d-135">有外设选项：</span><span class="sxs-lookup"><span data-stu-id="9f41d-135">Headed Options:</span></span>

### <a name="option-1-startup-configuration"></a><span data-ttu-id="9f41d-136">选项 1： 启动配置</span><span class="sxs-lookup"><span data-stu-id="9f41d-136">Option 1: Startup Configuration</span></span>
<span data-ttu-id="9f41d-137">**先决条件：** Windows 10 IoT 核心版设备需要插入鼠标、键盘、显示器和 USB WiFi 适配器</span><span class="sxs-lookup"><span data-stu-id="9f41d-137">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="9f41d-138">首次使用受支持的 USB WiFi 适配器启动 Windows 10 IoT 核心版时，将呈现配置屏幕。</span><span class="sxs-lookup"><span data-stu-id="9f41d-138">The first time you boot Windows 10 IoT Core with a supported USB WiFi adapter, you will be presented with a configuration screen.</span></span>
<span data-ttu-id="9f41d-139">在配置屏幕上，选择想要连接到的 WiFi 网络，并提供密码。</span><span class="sxs-lookup"><span data-stu-id="9f41d-139">On the configuration screen, select the WiFi network you would like to connect to and supply the password.</span></span> <span data-ttu-id="9f41d-140">单击“连接”以启动连接。</span><span class="sxs-lookup"><span data-stu-id="9f41d-140">Click **connect** to initiate the connection.</span></span>

![启动 WLAN 配置屏幕](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a><span data-ttu-id="9f41d-142">选项 2： 默认应用配置</span><span class="sxs-lookup"><span data-stu-id="9f41d-142">Option 2: Default App Configuration</span></span>
<span data-ttu-id="9f41d-143">**先决条件：** Windows 10 IoT 核心版设备需要插入鼠标、键盘、显示器和 USB WiFi 适配器</span><span class="sxs-lookup"><span data-stu-id="9f41d-143">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="9f41d-144">配置 WiFi 的替代方法是使用默认应用。</span><span class="sxs-lookup"><span data-stu-id="9f41d-144">An alternative way to configure WiFi is to use the default app.</span></span> <span data-ttu-id="9f41d-145">可使用此方法在启动设备后配置或修改 WiFi 设置。</span><span class="sxs-lookup"><span data-stu-id="9f41d-145">You can use this to configure or modify WiFi settings after the device has booted.</span></span>

1. <span data-ttu-id="9f41d-146">单击主页上的齿轮形设置图标</span><span class="sxs-lookup"><span data-stu-id="9f41d-146">Click on the gear-shaped settings icon on the homepage</span></span>
2. <span data-ttu-id="9f41d-147">在左侧窗格中选择“网络和 WLAN”</span><span class="sxs-lookup"><span data-stu-id="9f41d-147">Select **Network & Wi-Fi** in the left pane</span></span>
3. <span data-ttu-id="9f41d-148">单击要连接到的 WiFi 网络。</span><span class="sxs-lookup"><span data-stu-id="9f41d-148">Click on the WiFi network you want to connect to.</span></span> <span data-ttu-id="9f41d-149">在提示时提供密码，然后单击“连接”</span><span class="sxs-lookup"><span data-stu-id="9f41d-149">Supply the password if prompted, and click **Connect**</span></span>

![默认应用 WiFi 配置](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a><span data-ttu-id="9f41d-151">无外设选项：</span><span class="sxs-lookup"><span data-stu-id="9f41d-151">Headless Options:</span></span>




### <a name="option-1-web-based-configuration"></a><span data-ttu-id="9f41d-152">选项 1： 基于 Web 的配置</span><span class="sxs-lookup"><span data-stu-id="9f41d-152">Option 1: Web-Based Configuration</span></span>
<span data-ttu-id="9f41d-153">**先决条件：** 设备已需要通过以太网连接到本地网络，并且应插入了 USB WLAN 适配器</span><span class="sxs-lookup"><span data-stu-id="9f41d-153">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="9f41d-154">如果设备缺少 UI、屏幕或输入设备，仍可通过 [Windows Device Portal](../manage-your-device/DevicePortal.md) 配置该设备。</span><span class="sxs-lookup"><span data-stu-id="9f41d-154">If you have device a with no UI, display, or input devices, you can still configure it through the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>
<span data-ttu-id="9f41d-155">在 **Windows 10 IoT 核心版仪表板**上，*单击*设备的“在 Device Portal 中打开”图标。</span><span class="sxs-lookup"><span data-stu-id="9f41d-155">In **Windows 10 IoT Core Dashboard**, *Click* on the **Open in Device Portal** icon for your device.</span></span>

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. <span data-ttu-id="9f41d-156">输入“Administrator”作为用户名，并提供密码（默认情况下为 p@ssw0rd）</span><span class="sxs-lookup"><span data-stu-id="9f41d-156">Enter **Administrator** for the username, and supply your password (p@ssw0rd by default)</span></span>
2. <span data-ttu-id="9f41d-157">单击左侧窗格中的 "**网络**"</span><span class="sxs-lookup"><span data-stu-id="9f41d-157">Click on **Network** in the left-hand pane</span></span>
3. <span data-ttu-id="9f41d-158">在“可用网络”下，选择要连接到的网络，并提供连接凭据。</span><span class="sxs-lookup"><span data-stu-id="9f41d-158">Under **Available networks**, select network you would like to connect to and supply the connection credentials.</span></span> <span data-ttu-id="9f41d-159">单击“连接”以启动连接</span><span class="sxs-lookup"><span data-stu-id="9f41d-159">Click **Connect** to initiate the connection</span></span>

![基于 Web 的 WLAN 配置](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a><span data-ttu-id="9f41d-161">选项 2： 使用 WLAN 配置文件进行连接</span><span class="sxs-lookup"><span data-stu-id="9f41d-161">Option 2: Connect using WiFi Profiles</span></span>

<span data-ttu-id="9f41d-162">**先决条件：** 设备已需要通过以太网连接到本地网络，并且插入了 USB WiFi 适配器。</span><span class="sxs-lookup"><span data-stu-id="9f41d-162">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in.</span></span> <span data-ttu-id="9f41d-163">还需要具有 WiFi 功能的 Windows 电脑。</span><span class="sxs-lookup"><span data-stu-id="9f41d-163">You also need a Windows PC with WiFi capability.</span></span>

<span data-ttu-id="9f41d-164">Windows 10 IoT 核心版支持使用无线配置文件设置 WiFi。</span><span class="sxs-lookup"><span data-stu-id="9f41d-164">Setting up WiFi using wireless profiles is supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="9f41d-165">有关详细信息和示例，请参阅 [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853)。</span><span class="sxs-lookup"><span data-stu-id="9f41d-165">See [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) for details and examples.</span></span>

1. <span data-ttu-id="9f41d-166">将 Windows 电脑连接到所需的无线网络，并使用以下命令创建 WiFi 配置文件 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="9f41d-166">Connect your Windows PC to the desired wireless network and create WiFi profile XML file with these commands:</span></span>

    * <span data-ttu-id="9f41d-167">`netsh wlan show profiles` -> 查找刚添加的配置文件名称</span><span class="sxs-lookup"><span data-stu-id="9f41d-167">`netsh wlan show profiles` -> find the name of the profile you just added</span></span>

    * <span data-ttu-id="9f41d-168">`netsh wlan export profile name=<your profilename>`。</span><span class="sxs-lookup"><span data-stu-id="9f41d-168">`netsh wlan export profile name=<your profilename>`.</span></span> <span data-ttu-id="9f41d-169">这会将配置文件导出到某个 XML 文件</span><span class="sxs-lookup"><span data-stu-id="9f41d-169">This will export the profile to an XML file</span></span>

2. <span data-ttu-id="9f41d-170">打开“文件资源管理器”窗口，并在地址栏中键入 `\\<TARGET_DEVICE>\C$\`，然后点击 Enter。</span><span class="sxs-lookup"><span data-stu-id="9f41d-170">Open up a **File Explorer** window, and in the address bar type `\\<TARGET_DEVICE>\C$\` and then hit enter.</span></span>  <span data-ttu-id="9f41d-171">在此特定情况下，`<TARGET_DEVICE>` 可以是 Windows 10 IoT 核心版设备的名称或 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="9f41d-171">In this particular case, `<TARGET_DEVICE>` is either the name or the IP address of your Windows 10 IoT Core device:</span></span>

    ![使用文件资源管理器的 SMB](../media/SetupWifi/smb1.png)

    <span data-ttu-id="9f41d-173">如果系统提示输入用户名和密码，请使用以下凭据：</span><span class="sxs-lookup"><span data-stu-id="9f41d-173">If you are prompted for a user name and password, use the following credentials:</span></span>

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![使用文件资源管理器的 SMB](../media/SetupWifi/cred1.png)

> [!NOTE]
> <span data-ttu-id="9f41d-175">**强烈建议**你更新管理员帐户的默认密码。</span><span class="sxs-lookup"><span data-stu-id="9f41d-175">It is **highly recommended** that you update the default password for the Administrator account.</span></span>  <span data-ttu-id="9f41d-176">请按照[此处](../connect-your-device/PowerShell.md)的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="9f41d-176">Please follow the instructions found [here](../connect-your-device/PowerShell.md).</span></span>

3. <span data-ttu-id="9f41d-177">将导出的 WiFi 配置文件 XML 文件从 Windows 电脑复制到 Windows 10 IoT 核心版设备</span><span class="sxs-lookup"><span data-stu-id="9f41d-177">Copy the exported WiFi profile XML file from the Windows PC to your Windows 10 IoT Core device</span></span>

4. <span data-ttu-id="9f41d-178">通过执行以下命令，使用 [PowerShell](../connect-your-device/PowerShell.md) 连接到设备，并向你的设备添加新的 WLAN 配置文件</span><span class="sxs-lookup"><span data-stu-id="9f41d-178">Connect to your device using [PowerShell](../connect-your-device/PowerShell.md) and add the new WiFi profile to your device by executing the following commands</span></span>

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. <span data-ttu-id="9f41d-179">通过 netsh，将 Windows 10 IoT 核心版设备连接到无线网络</span><span class="sxs-lookup"><span data-stu-id="9f41d-179">Connect the Windows 10 IoT Core device to wireless network via netsh</span></span>

    * `netsh wlan connect name=<profile name>`

6. <span data-ttu-id="9f41d-180">请验证设备是否连接到无线网络并且可访问 Internet</span><span class="sxs-lookup"><span data-stu-id="9f41d-180">Verify that your device is connected to the wireless network and can reach the internet</span></span>

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a><span data-ttu-id="9f41d-181">连接到 WPA2-PSK 个人网络</span><span class="sxs-lookup"><span data-stu-id="9f41d-181">Connecting to WPA2-PSK Personal networks</span></span>

<span data-ttu-id="9f41d-182">如果需要连接到 WPA2-PSK 个人 WiFi 网络，请首先按照上述说明进行操作，但要对 XML 文件作出以下更改。</span><span class="sxs-lookup"><span data-stu-id="9f41d-182">If you need to connect to a WPA2-PSK Personal WiFi network, follow the instructions above first, but make the following changes to the XML file.</span></span> <span data-ttu-id="9f41d-183">唯一的区别是，在 Windows 电脑导出 XML 时，它将对密码进行加密。</span><span class="sxs-lookup"><span data-stu-id="9f41d-183">The only difference is that when your Windows PC exports the XML it encrypts the password.</span></span>

> [!WARNING] 
> <span data-ttu-id="9f41d-184">这会使连接不安全。</span><span class="sxs-lookup"><span data-stu-id="9f41d-184">This will make your connection insecure.</span></span>

<span data-ttu-id="9f41d-185">从 Windows 电脑导出的配置文件 XML：</span><span class="sxs-lookup"><span data-stu-id="9f41d-185">Profile XML exported from Windows PC:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


<span data-ttu-id="9f41d-186">需要在 Windows 10 IoT 核心版上生效的更改：</span><span class="sxs-lookup"><span data-stu-id="9f41d-186">Changes needed to work on Windows 10 IoT Core:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
