---
title: 在 Windows 10 IoT 核心版设备上使用 WiFi
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用、 安装程序，并在 Windows 10 IoT Core 设备上配置 wifi。
keywords: windows iot、 wifi、 安装程序、 设备
ms.openlocfilehash: 20f61114323baa60c8052038df68a8c172ce1c95
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510893"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a><span data-ttu-id="897e8-104">在 Windows 10 IoT 核心版设备上使用 WiFi</span><span class="sxs-lookup"><span data-stu-id="897e8-104">Using WiFi on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="897e8-105">在使用 USB WLAN 适配器的过程中，WLAN 在 Windows 10 IoT 核心版设备上受支持。</span><span class="sxs-lookup"><span data-stu-id="897e8-105">WiFi is supported on Windows 10 IoT Core devices through the use of a USB WiFi adapter.</span></span> <span data-ttu-id="897e8-106">使用 WLAN 可提供有线连接的所有功能，包括 [SSH](../connect-your-device/SSH.md)、[Powershell](../connect-your-device/PowerShell.md)、[Windows Device Portal](../manage-your-device/DevicePortal.md) 以及应用程序调试和部署。</span><span class="sxs-lookup"><span data-stu-id="897e8-106">Using WiFi provides all the functionality of a wired connection, including [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), and application debugging and deployment.</span></span>

> [!NOTE]
> <span data-ttu-id="897e8-107">在有线以太网电缆插入将 WiFi 重写为默认网络接口。</span><span class="sxs-lookup"><span data-stu-id="897e8-107">Plugging in a wired Ethernet cable will override WiFi as the default network interface.</span></span>

### <a name="supported-adapters"></a><span data-ttu-id="897e8-108">支持的适配器</span><span class="sxs-lookup"><span data-stu-id="897e8-108">Supported Adapters</span></span>
<span data-ttu-id="897e8-109">Windows 10 IoT Core 进行了测试的 WiFi 适配器的列表，可我们[支持硬件](../learn-about-hardware/HardwareCompatList.md)页。</span><span class="sxs-lookup"><span data-stu-id="897e8-109">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span>

### <a name="configuring-wifi"></a><span data-ttu-id="897e8-110">配置 WLAN</span><span class="sxs-lookup"><span data-stu-id="897e8-110">Configuring WiFi</span></span>
<span data-ttu-id="897e8-111">若要使用 WiFi，将需要向 Windows 10 IoT 核心版提供 WiFi 网络凭据。</span><span class="sxs-lookup"><span data-stu-id="897e8-111">To use WiFi, you'll need to provide Windows 10 IoT core with the WiFi network credentials.</span></span> <span data-ttu-id="897e8-112">有关如何构建辅助应用程序和 WPS 自定义解决方案的文档，除了有执行此操作，因此下面列出的几个不同的选项。</span><span class="sxs-lookup"><span data-stu-id="897e8-112">In addition to documentation on how to build companion app and WPS custom solutions, there are a few different options for doing so listed below.</span></span>

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a><span data-ttu-id="897e8-113">自定义辅助应用程序和 WPS 的 Wi-fi 载入示例</span><span class="sxs-lookup"><span data-stu-id="897e8-113">Custom Companion App & WPS Wi-Fi Onboarding Samples</span></span>

<span data-ttu-id="897e8-114">目前，我们提供多种方式开发人员可以构建其设备的自定义 wifi 载入解决方案。</span><span class="sxs-lookup"><span data-stu-id="897e8-114">Currently, we offer a number of ways for developers to build a custom wifi onboarding solution for their device.</span></span> 

> | <span data-ttu-id="897e8-115">示例</span><span class="sxs-lookup"><span data-stu-id="897e8-115">Samples</span></span> | <span data-ttu-id="897e8-116">描述</span><span class="sxs-lookup"><span data-stu-id="897e8-116">Description</span></span> | <span data-ttu-id="897e8-117">优势</span><span class="sxs-lookup"><span data-stu-id="897e8-117">Benefits</span></span>  |  <span data-ttu-id="897e8-118">缺点</span><span class="sxs-lookup"><span data-stu-id="897e8-118">Drawbacks</span></span>  |
> |-------------|----------|---------|---------|
> | [<span data-ttu-id="897e8-119">辅助应用程序</span><span class="sxs-lookup"><span data-stu-id="897e8-119">Companion App</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | <span data-ttu-id="897e8-120">创建简单的 Xamarin 应用，可以配置你的设备的 Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="897e8-120">Create a simple Xamarin app that can configure your device's Wi-Fi.</span></span> |  <span data-ttu-id="897e8-121">易于使用;主或适用于 IoT Core; 无外设跨平台工作的客户端</span><span class="sxs-lookup"><span data-stu-id="897e8-121">Simple to use; Headed or headless for IoT Core; Clients work cross-platform</span></span> | <span data-ttu-id="897e8-122">开发人员正在创建他或她自己的协议;需要开发人员可以实现安全</span><span class="sxs-lookup"><span data-stu-id="897e8-122">Developer is creating his or her own protocol; requires developer to implement security</span></span> |
> | [<span data-ttu-id="897e8-123">使用蓝牙 RFCOMM IoT 载入</span><span class="sxs-lookup"><span data-stu-id="897e8-123">IoT Onboarding with Bluetooth RFCOMM</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | <span data-ttu-id="897e8-124">创建解决方案配置无外设 IoT 设备与你的 Wi-fi 连接使用蓝牙 RFCOMM。</span><span class="sxs-lookup"><span data-stu-id="897e8-124">Create solution to configure your headless IoT device to connect with your Wi-Fi using Bluetooth RFCOMM.</span></span>  | <span data-ttu-id="897e8-125">适用于主或无外设设备;使用熟悉的技术和概念：不需要 IoT 设备开始 SoftAP;不需要调整防火墙设置</span><span class="sxs-lookup"><span data-stu-id="897e8-125">Relevant in headed or headless devices; Uses familiar technologies and concepts; Does not require IoT device to start a SoftAP; Does not need to adjust firewall settings</span></span> | <span data-ttu-id="897e8-126">适用于客户端和服务器设备; 需要蓝牙的支持示例仅适用于 Windows 10; 提供客户端应用程序服务器应用程序前的 defines/硬编码的客户端设备的名称。</span><span class="sxs-lookup"><span data-stu-id="897e8-126">Requires Bluetooth support for client and server devices; Sample only provides client app for Windows 10; Server app pre-defines/hard-codes the names of the client device.</span></span> |
> | [<span data-ttu-id="897e8-127">使用 AllJoyn IoT 载入</span><span class="sxs-lookup"><span data-stu-id="897e8-127">IoT Onboarding with AllJoyn</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | <span data-ttu-id="897e8-128">远程连接将无外设的 IoT 设备与您的家庭 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="897e8-128">Remotely join your headless IoT device with your home Wi-Fi network.</span></span> | <span data-ttu-id="897e8-129">适用于 AllJoyn</span><span class="sxs-lookup"><span data-stu-id="897e8-129">Works with AllJoyn</span></span> | <span data-ttu-id="897e8-130">AllJoyn 一些支持不推荐使用</span><span class="sxs-lookup"><span data-stu-id="897e8-130">Some support for AllJoyn is deprecated</span></span> |
> | <span data-ttu-id="897e8-131">Wi-fi 受保护的安装程序 (WPS) 适用于设备的 Api</span><span class="sxs-lookup"><span data-stu-id="897e8-131">Wi-Fi Protected Setup (WPS) APIs for devices</span></span> | <span data-ttu-id="897e8-132">执行 WPS 发现能够查询网络支持 WPS 方法。</span><span class="sxs-lookup"><span data-stu-id="897e8-132">Perform WPS discovery to query the WPS methods supported by the network.</span></span> | <span data-ttu-id="897e8-133">只需利用[WiFiAdapter.GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync)并[WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync)方法来连接到特定网络的 wi-fi 的设备。</span><span class="sxs-lookup"><span data-stu-id="897e8-133">Simply leverage the [WiFiAdapter.GetWpsConfigurationAsync(WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) and [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) methods to connect wi-fi devices to specific networks.</span></span> | <span data-ttu-id="897e8-134">将需要熟悉这些 Api 来加以利用。;仅支持 WPS 的路由器与兼容</span><span class="sxs-lookup"><span data-stu-id="897e8-134">You will need to become familiar with these APIs to leverage them.; only compatible with WPS-enabled routers</span></span>|

## <a name="headed-options"></a><span data-ttu-id="897e8-135">有外设选项：</span><span class="sxs-lookup"><span data-stu-id="897e8-135">Headed Options:</span></span>

### <a name="option-1-startup-configuration"></a><span data-ttu-id="897e8-136">选项 1：启动配置</span><span class="sxs-lookup"><span data-stu-id="897e8-136">Option 1: Startup Configuration</span></span>
<span data-ttu-id="897e8-137">**先决条件：** Windows 10 IoT 核心版设备需要插入鼠标、键盘、显示器和 USB WiFi 适配器</span><span class="sxs-lookup"><span data-stu-id="897e8-137">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="897e8-138">首次使用受支持的 USB WiFi 适配器启动 Windows 10 IoT 核心版时，将呈现配置屏幕。</span><span class="sxs-lookup"><span data-stu-id="897e8-138">The first time you boot Windows 10 IoT Core with a supported USB WiFi adapter, you will be presented with a configuration screen.</span></span>
<span data-ttu-id="897e8-139">在配置屏幕上，选择想要连接到的 WiFi 网络，并提供密码。</span><span class="sxs-lookup"><span data-stu-id="897e8-139">On the configuration screen, select the WiFi network you would like to connect to and supply the password.</span></span> <span data-ttu-id="897e8-140">单击“连接”以启动连接。</span><span class="sxs-lookup"><span data-stu-id="897e8-140">Click **connect** to initiate the connection.</span></span>

![启动 WLAN 配置屏幕](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a><span data-ttu-id="897e8-142">选项 2：默认应用配置</span><span class="sxs-lookup"><span data-stu-id="897e8-142">Option 2: Default App Configuration</span></span>
<span data-ttu-id="897e8-143">**先决条件：** Windows 10 IoT 核心版设备需要插入鼠标、键盘、显示器和 USB WiFi 适配器</span><span class="sxs-lookup"><span data-stu-id="897e8-143">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="897e8-144">配置 WiFi 的替代方法是使用默认应用。</span><span class="sxs-lookup"><span data-stu-id="897e8-144">An alternative way to configure WiFi is to use the default app.</span></span> <span data-ttu-id="897e8-145">可使用此方法在启动设备后配置或修改 WiFi 设置。</span><span class="sxs-lookup"><span data-stu-id="897e8-145">You can use this to configure or modify WiFi settings after the device has booted.</span></span>

1. <span data-ttu-id="897e8-146">单击主页上的齿轮形设置图标</span><span class="sxs-lookup"><span data-stu-id="897e8-146">Click on the gear-shaped settings icon on the homepage</span></span>
2. <span data-ttu-id="897e8-147">在左侧窗格中选择“网络和 WLAN”</span><span class="sxs-lookup"><span data-stu-id="897e8-147">Select **Network & Wi-Fi** in the left pane</span></span>
3. <span data-ttu-id="897e8-148">单击要连接到的 WiFi 网络。</span><span class="sxs-lookup"><span data-stu-id="897e8-148">Click on the WiFi network you want to connect to.</span></span> <span data-ttu-id="897e8-149">在提示时提供密码，然后单击“连接”</span><span class="sxs-lookup"><span data-stu-id="897e8-149">Supply the password if prompted, and click **Connect**</span></span>

![默认应用 WiFi 配置](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a><span data-ttu-id="897e8-151">无外设选项：</span><span class="sxs-lookup"><span data-stu-id="897e8-151">Headless Options:</span></span>




### <a name="option-1-web-based-configuration"></a><span data-ttu-id="897e8-152">选项 1：基于 Web 的配置</span><span class="sxs-lookup"><span data-stu-id="897e8-152">Option 1: Web-Based Configuration</span></span>
<span data-ttu-id="897e8-153">**先决条件：** 设备已需要通过以太网连接到本地网络，并且应插入了 USB WLAN 适配器</span><span class="sxs-lookup"><span data-stu-id="897e8-153">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="897e8-154">如果设备缺少 UI、屏幕或输入设备，仍可通过 [Windows Device Portal](../manage-your-device/DevicePortal.md) 配置该设备。</span><span class="sxs-lookup"><span data-stu-id="897e8-154">If you have device a with no UI, display, or input devices, you can still configure it through the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>
<span data-ttu-id="897e8-155">在 **Windows 10 IoT 核心版仪表板**上，*单击*设备的“在 Device Portal 中打开”图标。</span><span class="sxs-lookup"><span data-stu-id="897e8-155">In **Windows 10 IoT Core Dashboard**, *Click* on the **Open in Device Portal** icon for your device.</span></span>

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. <span data-ttu-id="897e8-156">输入“Administrator”作为用户名，并提供密码（默认情况下为 p@ssw0rd）</span><span class="sxs-lookup"><span data-stu-id="897e8-156">Enter **Administrator** for the username, and supply your password (p@ssw0rd by default)</span></span>
2. <span data-ttu-id="897e8-157">单击**网络**的左窗格中</span><span class="sxs-lookup"><span data-stu-id="897e8-157">Click on **Network** in the left-hand pane</span></span>
3. <span data-ttu-id="897e8-158">在“可用网络”下，选择要连接到的网络，并提供连接凭据。</span><span class="sxs-lookup"><span data-stu-id="897e8-158">Under **Available networks**, select network you would like to connect to and supply the connection credentials.</span></span> <span data-ttu-id="897e8-159">单击“连接”以启动连接</span><span class="sxs-lookup"><span data-stu-id="897e8-159">Click **Connect** to initiate the connection</span></span>

![基于 Web 的 WLAN 配置](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a><span data-ttu-id="897e8-161">选项 2：使用 WLAN 配置文件进行连接</span><span class="sxs-lookup"><span data-stu-id="897e8-161">Option 2: Connect using WiFi Profiles</span></span>

<span data-ttu-id="897e8-162">**先决条件：** 设备已需要通过以太网连接到本地网络，并且插入了 USB WiFi 适配器。</span><span class="sxs-lookup"><span data-stu-id="897e8-162">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in.</span></span> <span data-ttu-id="897e8-163">还需要具有 WiFi 功能的 Windows 电脑。</span><span class="sxs-lookup"><span data-stu-id="897e8-163">You also need a Windows PC with WiFi capability.</span></span>

<span data-ttu-id="897e8-164">Windows 10 IoT 核心版支持使用无线配置文件设置 WiFi。</span><span class="sxs-lookup"><span data-stu-id="897e8-164">Setting up WiFi using wireless profiles is supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="897e8-165">有关详细信息和示例，请参阅 [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853)。</span><span class="sxs-lookup"><span data-stu-id="897e8-165">See [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) for details and examples.</span></span>

1. <span data-ttu-id="897e8-166">将 Windows 电脑连接到所需的无线网络，并使用以下命令创建 WiFi 配置文件 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="897e8-166">Connect your Windows PC to the desired wireless network and create WiFi profile XML file with these commands:</span></span>

    * `netsh wlan show profiles` <span data-ttu-id="897e8-167">->，找到您刚添加的配置文件的名称</span><span class="sxs-lookup"><span data-stu-id="897e8-167">-> find the name of the profile you just added</span></span>

    * `netsh wlan export profile name=<your profilename>`<span data-ttu-id="897e8-168">.</span><span class="sxs-lookup"><span data-stu-id="897e8-168">.</span></span> <span data-ttu-id="897e8-169">这会将配置文件导出到某个 XML 文件</span><span class="sxs-lookup"><span data-stu-id="897e8-169">This will export the profile to an XML file</span></span>

2. <span data-ttu-id="897e8-170">打开“文件资源管理器”窗口，并在地址栏中键入 `\\<TARGET_DEVICE>\C$\`，然后点击 Enter。</span><span class="sxs-lookup"><span data-stu-id="897e8-170">Open up a **File Explorer** window, and in the address bar type `\\<TARGET_DEVICE>\C$\` and then hit enter.</span></span>  <span data-ttu-id="897e8-171">在此特定情况下，`<TARGET_DEVICE>` 可以是 Windows 10 IoT 核心版设备的名称或 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="897e8-171">In this particular case, `<TARGET_DEVICE>` is either the name or the IP address of your Windows 10 IoT Core device:</span></span>

    ![使用文件资源管理器的 SMB](../media/SetupWifi/smb1.png)

    <span data-ttu-id="897e8-173">如果系统提示输入用户名和密码，请使用以下凭据：</span><span class="sxs-lookup"><span data-stu-id="897e8-173">If you are prompted for a user name and password, use the following credentials:</span></span>

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![使用文件资源管理器的 SMB](../media/SetupWifi/cred1.png)

> [!NOTE]
> <span data-ttu-id="897e8-175">**强烈建议**你更新管理员帐户的默认密码。</span><span class="sxs-lookup"><span data-stu-id="897e8-175">It is **highly recommended** that you update the default password for the Administrator account.</span></span>  <span data-ttu-id="897e8-176">请按照的说明操作[此处](../connect-your-device/PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="897e8-176">Please follow the instructions found [here](../connect-your-device/PowerShell.md).</span></span>

3. <span data-ttu-id="897e8-177">将导出的 WiFi 配置文件 XML 文件从 Windows 电脑复制到 Windows 10 IoT 核心版设备</span><span class="sxs-lookup"><span data-stu-id="897e8-177">Copy the exported WiFi profile XML file from the Windows PC to your Windows 10 IoT Core device</span></span>

4. <span data-ttu-id="897e8-178">通过执行以下命令，使用 [PowerShell](../connect-your-device/PowerShell.md) 连接到设备，并向你的设备添加新的 WLAN 配置文件</span><span class="sxs-lookup"><span data-stu-id="897e8-178">Connect to your device using [PowerShell](../connect-your-device/PowerShell.md) and add the new WiFi profile to your device by executing the following commands</span></span>

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. <span data-ttu-id="897e8-179">通过 netsh，将 Windows 10 IoT 核心版设备连接到无线网络</span><span class="sxs-lookup"><span data-stu-id="897e8-179">Connect the Windows 10 IoT Core device to wireless network via netsh</span></span>

    * `netsh wlan connect name=<profile name>`

6. <span data-ttu-id="897e8-180">请验证设备是否连接到无线网络并且可访问 Internet</span><span class="sxs-lookup"><span data-stu-id="897e8-180">Verify that your device is connected to the wireless network and can reach the internet</span></span>

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a><span data-ttu-id="897e8-181">连接到 WPA2-PSK 个人网络</span><span class="sxs-lookup"><span data-stu-id="897e8-181">Connecting to WPA2-PSK Personal networks</span></span>

<span data-ttu-id="897e8-182">如果需要连接到 WPA2-PSK 个人 WiFi 网络，请首先按照上述说明进行操作，但要对 XML 文件作出以下更改。</span><span class="sxs-lookup"><span data-stu-id="897e8-182">If you need to connect to a WPA2-PSK Personal WiFi network, follow the instructions above first, but make the following changes to the XML file.</span></span> <span data-ttu-id="897e8-183">唯一的区别是，在 Windows 电脑导出 XML 时，它将对密码进行加密。</span><span class="sxs-lookup"><span data-stu-id="897e8-183">The only difference is that when your Windows PC exports the XML it encrypts the password.</span></span>

> [!WARNING] 
> <span data-ttu-id="897e8-184">这将使你的连接不安全。</span><span class="sxs-lookup"><span data-stu-id="897e8-184">This will make your connection insecure.</span></span>

<span data-ttu-id="897e8-185">从 Windows 电脑导出的配置文件 XML：</span><span class="sxs-lookup"><span data-stu-id="897e8-185">Profile XML exported from Windows PC:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


<span data-ttu-id="897e8-186">需要在 Windows 10 IoT 核心版上生效的更改：</span><span class="sxs-lookup"><span data-stu-id="897e8-186">Changes needed to work on Windows 10 IoT Core:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
