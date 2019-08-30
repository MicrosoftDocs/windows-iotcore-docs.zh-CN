---
title: 在 Windows 10 Iot Core 设备上使用 WiFi Direct
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何通过启用的 USB wifi 适配器在设备上设置、测试和使用 wifi direct。
keywords: windows iot, wifi 直接, 安装, wifi, 设备
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169362"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a><span data-ttu-id="88918-104">在 Windows 10 IoT Core 设备上使用 WiFi Direct</span><span class="sxs-lookup"><span data-stu-id="88918-104">Using WiFi Direct on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="88918-105">在 Windows 10 IoT Core 设备上, 通过使用 WiFi 直接启用的 USB WiFi 适配器支持 WiFi 直接。</span><span class="sxs-lookup"><span data-stu-id="88918-105">WiFi Direct is supported on Windows 10 IoT Core devices through the use of a WiFi Direct enabled USB WiFi adapter.</span></span> <span data-ttu-id="88918-106">若要确保启用 WiFi Direct, 需要满足以下两个事项:</span><span class="sxs-lookup"><span data-stu-id="88918-106">To make sure that WiFi Direct is enabled two things need to be true:</span></span>
* <span data-ttu-id="88918-107">USB WiFi 适配器的硬件需要支持 WiFi Direct,</span><span class="sxs-lookup"><span data-stu-id="88918-107">the hardware of the USB WiFi adapter needs to support WiFi Direct,</span></span>
* <span data-ttu-id="88918-108">USB WiFi 适配器的相应驱动程序需要支持 WiFi Direct。</span><span class="sxs-lookup"><span data-stu-id="88918-108">the corresponding driver of the USB WiFi adapter needs to support WiFi Direct.</span></span> 

<span data-ttu-id="88918-109">WiFi Direct 为 WiFi 设备到设备连接提供了一种解决方案, 无需无线接入点 (无线 AP) 来设置连接。</span><span class="sxs-lookup"><span data-stu-id="88918-109">WiFi Direct provides a solution for WiFi device-to-device connectivity without the need for either a Wireless Access Point (wireless AP) to setup the connection.</span></span> <span data-ttu-id="88918-110">查看[WiFiDirect 命名空间](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx)中提供的 UWP api, 查看可以使用 WiFiDirect 执行的操作。</span><span class="sxs-lookup"><span data-stu-id="88918-110">Take a look at the UWP APIs available in the [Windows.Devices.WiFiDirect namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) to see what you can do with WiFiDirect.</span></span>

## <a name="supported-adapters"></a><span data-ttu-id="88918-111">支持的适配器</span><span class="sxs-lookup"><span data-stu-id="88918-111">Supported Adapters</span></span>

<span data-ttu-id="88918-112">可以在[受支持的硬件](../learn-about-hardware/HardwareCompatList.md)页上找到已在 Windows 10 IoT Core 上测试的 WiFi 适配器列表。</span><span class="sxs-lookup"><span data-stu-id="88918-112">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span> 

## <a name="basic-sample-for-wifi-direct"></a><span data-ttu-id="88918-113">WiFi Direct 的基本示例</span><span class="sxs-lookup"><span data-stu-id="88918-113">Basic sample for WiFi Direct</span></span>

<span data-ttu-id="88918-114">可以通过 WiFi 直接 UWP[示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)轻松测试 wifi 直接功能。</span><span class="sxs-lookup"><span data-stu-id="88918-114">You can easily test the WiFi Direct functionality with the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span></span> <span data-ttu-id="88918-115">我们将使用C#版本并运行两个设备的示例。</span><span class="sxs-lookup"><span data-stu-id="88918-115">We will use the C# version and run the sample of two devices.</span></span>

### <a name="set-up-the-two-devices"></a><span data-ttu-id="88918-116">设置两个设备</span><span class="sxs-lookup"><span data-stu-id="88918-116">Set up the two devices</span></span>
* <span data-ttu-id="88918-117">运行 Windows 10 IoT Core 的 MinnowBoardMax (MBM) (请参阅此处的说明), 其中包含 CanaKit WiFi 转换器</span><span class="sxs-lookup"><span data-stu-id="88918-117">MinnowBoardMax (MBM) running Windows 10 IoT Core (see instructions here), with a CanaKit WiFi dongle</span></span>
* <span data-ttu-id="88918-118">将显示器、键盘和鼠标连接到 MBM</span><span class="sxs-lookup"><span data-stu-id="88918-118">Connect monitor, keyboard and mouse to the MBM</span></span>
* <span data-ttu-id="88918-119">运行最新 Windows 10 周年更新的 Windows 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="88918-119">A Windows 10 PC running the latest Windows 10 Anniversary Update.</span></span> <span data-ttu-id="88918-120">电脑 (或便携式计算机) 需要提供 WiFi 直接支持 (如 Microsoft Surface)</span><span class="sxs-lookup"><span data-stu-id="88918-120">The PC (or laptop) will need to have WiFi Direct support (e.g. a Microsoft Surface)</span></span>
* <span data-ttu-id="88918-121">在 Windows 10 电脑上安装 Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="88918-121">Install Visual Studio 2017 on your Windows 10 PC</span></span>
* <span data-ttu-id="88918-122">克隆或下载 WiFi 直接 UWP[示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)([此处](https://github.com/Microsoft/Windows-universal-samples)提供 GitHub 存储库的根目录)。</span><span class="sxs-lookup"><span data-stu-id="88918-122">Clone or download the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(root of the GitHub repo is [here](https://github.com/Microsoft/Windows-universal-samples)).</span></span>
* <span data-ttu-id="88918-123">在 Visual C# Studio 2017 中加载 WIFI Direct UWP 示例的版本</span><span class="sxs-lookup"><span data-stu-id="88918-123">Load the C# version of the WiFi Direct UWP sample in Visual Studio 2017</span></span>

#### <a name="run-the-sample-on-the-two-devices"></a><span data-ttu-id="88918-124">在两个设备上运行示例</span><span class="sxs-lookup"><span data-stu-id="88918-124">Run the sample on the two devices</span></span>
* <span data-ttu-id="88918-125">编译该示例并在 MBM 上部署/运行它:</span><span class="sxs-lookup"><span data-stu-id="88918-125">Compile the sample and deploy/run it on the MBM:</span></span>

    * <span data-ttu-id="88918-126">将 "解决方案平台" 组合框设置为 "x86"</span><span class="sxs-lookup"><span data-stu-id="88918-126">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="88918-127">从 "运行" 下拉列表中选择 "远程计算机"</span><span class="sxs-lookup"><span data-stu-id="88918-127">Select "Remote Machine" from the "Run" dropdown</span></span>
    * <span data-ttu-id="88918-128">在不进行调试的情况下启动 MBM 上的示例 (通过按 Ctrl-F5 或从 "调试" 菜单中选择 "启动 (不调试)")</span><span class="sxs-lookup"><span data-stu-id="88918-128">Start the sample on the MBM without debugging (either by pressing Ctrl-F5 or by selecting "Start Without Debugging" from the "Debug" menu)</span></span>
    * <span data-ttu-id="88918-129">应会在连接到 MBM 的监视器上看到运行的 WiFi 直接示例</span><span class="sxs-lookup"><span data-stu-id="88918-129">You should see the WiFi Direct sample running on the monitor connected to the MBM</span></span>
* <span data-ttu-id="88918-130">编译该示例, 并在 Windows 10 电脑上部署/运行它:</span><span class="sxs-lookup"><span data-stu-id="88918-130">Compile the sample and deploy/run it on the Windows 10 PC:</span></span>
    * <span data-ttu-id="88918-131">将 "解决方案平台" 组合框设置为 "x86"</span><span class="sxs-lookup"><span data-stu-id="88918-131">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="88918-132">从 "运行" 下拉列表中选择 "本地"</span><span class="sxs-lookup"><span data-stu-id="88918-132">Select "Local" from the "Run" dropdown</span></span>
    * <span data-ttu-id="88918-133">启动示例 (按 F5 或 Ctrl-F5)</span><span class="sxs-lookup"><span data-stu-id="88918-133">Start the sample (either F5 or Ctrl-F5)</span></span>
    * <span data-ttu-id="88918-134">你应看到在 Windows 10 电脑上运行的 WiFi Direct 示例</span><span class="sxs-lookup"><span data-stu-id="88918-134">You should see the WiFi Direct sample running on your Windows 10 PC</span></span>

### <a name="set-up-advertiser-and-connector"></a><span data-ttu-id="88918-135">设置广告商和连接器</span><span class="sxs-lookup"><span data-stu-id="88918-135">Set up Advertiser and Connector</span></span>
* <span data-ttu-id="88918-136">在 MBM 上, 选择 (1) "广告商", 并按 "启动广告" 按钮</span><span class="sxs-lookup"><span data-stu-id="88918-136">On the MBM, select (1) "Advertiser" and press the "Start Advertisement" button</span></span>

    * <span data-ttu-id="88918-137">MBM 将在 WiFi 直接通道上开始播发</span><span class="sxs-lookup"><span data-stu-id="88918-137">The MBM will start advertising itself on the WiFi Direct channel</span></span>

        !["广告商配置" 屏幕](../media/SetupWiFiDirect/Advertiser01.png)

        <span data-ttu-id="88918-139">请注意应用底部的 "播发状态" 横幅。</span><span class="sxs-lookup"><span data-stu-id="88918-139">Notice the "Advertisement Status" banner at the bottom of the app.</span></span>
    
* <span data-ttu-id="88918-140">在 Windows 10 电脑上, 选择 (2) "连接器", 并按 "启动观察程序" 按钮</span><span class="sxs-lookup"><span data-stu-id="88918-140">On the Windows 10 PC, select (2) "Connector" and press the "Start Watcher" button</span></span> 

    * <span data-ttu-id="88918-141">Windows 10 电脑将开始扫描可用的 WiFi 直接连接</span><span class="sxs-lookup"><span data-stu-id="88918-141">The Windows 10 PC will start scanning for available WiFi Direct connections</span></span>
    * <span data-ttu-id="88918-142">扫描完成后, 应会在 "发现的设备" 列表中看到 MBM 的名称</span><span class="sxs-lookup"><span data-stu-id="88918-142">When the scanning is complete, you should see the name of your MBM in the "Discovered Devices" list</span></span>

        ![连接器配置屏幕](../media/SetupWiFiDirect/Connector01.png)

        <span data-ttu-id="88918-144">你可以看到列出了两个设备 (对 "ale-mbm01" 感兴趣) 和 "DeviceWatcher 枚举已完成" 消息。</span><span class="sxs-lookup"><span data-stu-id="88918-144">You can see two devices listed (we're interested in "ale-mbm01"), and the "DeviceWatcher enumeration completed" message.</span></span>

### <a name="pair-the-devices"></a><span data-ttu-id="88918-145">配对设备</span><span class="sxs-lookup"><span data-stu-id="88918-145">Pair the devices</span></span>
* <span data-ttu-id="88918-146">在 Windows 10 电脑上的 "发现的设备" 列表中, 选择 MBM (在我们的示例中为 "mbm01"), 然后按 "连接" 按钮</span><span class="sxs-lookup"><span data-stu-id="88918-146">On the Windows 10 PC, select the MBM ("ale-mbm01" in our example) from the "Discovered Devices" list and press the "Connect" button</span></span>
* <span data-ttu-id="88918-147">在 Windows 10 电脑上, 按 "是" 启动配对过程</span><span class="sxs-lookup"><span data-stu-id="88918-147">On the Windows 10 PC, press "Yes" to initiate the pairing process</span></span>

    ![连接器开始配对](../media/SetupWiFiDirect/Connector02.png)

* <span data-ttu-id="88918-149">在 MBM 监视器上, 应使用 PIN 的消息</span><span class="sxs-lookup"><span data-stu-id="88918-149">On the MBM monitor you should a message with the PIN</span></span>

    ![广告商 PIN 对话框](../media/SetupWiFiDirect/Advertiser02.png)

* <span data-ttu-id="88918-151">在 Windows 10 电脑上, 你应该会看到一个对话框, 需要在其中输入 PIN</span><span class="sxs-lookup"><span data-stu-id="88918-151">On the Windows 10 PC, you should see a dialog where you need to enter the PIN</span></span>

    ![连接器 PIN 对话框](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a><span data-ttu-id="88918-153">在频道上交谈</span><span class="sxs-lookup"><span data-stu-id="88918-153">Talk on the channel</span></span>
* <span data-ttu-id="88918-154">应连接两个设备。</span><span class="sxs-lookup"><span data-stu-id="88918-154">The two devices should be connected.</span></span> <span data-ttu-id="88918-155">你应在 "连接的设备" 列表中的两个屏幕上看到随机生成的设备 id (在我们的示例中为 "hqffpzhz ggg")</span><span class="sxs-lookup"><span data-stu-id="88918-155">You should see a randomly generated device id ("hqffpzhz.ggg" in our example) on both screens in the "Connected Devices" list</span></span>

    ![已连接到广告设备](../media/SetupWiFiDirect/Advertiser03.png)

    ![连接器连接设备](../media/SetupWiFiDirect/Connector04.png)

* <span data-ttu-id="88918-158">你现在设置了全双工通道 (或套接字)</span><span class="sxs-lookup"><span data-stu-id="88918-158">You now have a full-duplex channel (or socket) set up</span></span>

    * <span data-ttu-id="88918-159">在 MBM 上, 从 "连接的设备" 列表中选择设备 ("hqffpzhz. ggg")</span><span class="sxs-lookup"><span data-stu-id="88918-159">on the MBM, select the device ("hqffpzhz.ggg") from the "Connected Devices" list</span></span>
    * <span data-ttu-id="88918-160">在 "输入消息" 文本框中键入一条消息</span><span class="sxs-lookup"><span data-stu-id="88918-160">type a message in the "Enter a message" textbox</span></span>
    * <span data-ttu-id="88918-161">按 "发送" 按钮</span><span class="sxs-lookup"><span data-stu-id="88918-161">press the "Send" button</span></span>
    * <span data-ttu-id="88918-162">应会看到从 Windows 10 PC 接收的消息</span><span class="sxs-lookup"><span data-stu-id="88918-162">you should see the message being received from the Windows 10 PC</span></span>
    * <span data-ttu-id="88918-163">尝试将消息从 Windows 10 电脑发送到 MBM</span><span class="sxs-lookup"><span data-stu-id="88918-163">try sending a message from the Windows 10 PC to the MBM</span></span>
