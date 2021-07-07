---
title: 在 Iot 核心设备上Windows 10 WiFi Direct
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在具有已启用 USB wifi 适配器的设备上设置、测试和使用 wifi direct。
keywords: windows iot， wifi direct， 安装程序， wifi， 设备
ms.openlocfilehash: 2ddf06dba6fe30ed7d9152b4500177e73e9243d4
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229225"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a><span data-ttu-id="9a234-104">在设备设备上Windows 10 IoT 核心版 WiFi Direct</span><span class="sxs-lookup"><span data-stu-id="9a234-104">Using WiFi Direct on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="9a234-105">使用已启用 WiFi Direct 的 USB wiFi 适配器Windows 10 IoT 核心版设备支持 WiFi Direct。</span><span class="sxs-lookup"><span data-stu-id="9a234-105">WiFi Direct is supported on Windows 10 IoT Core devices through the use of a WiFi Direct enabled USB WiFi adapter.</span></span> <span data-ttu-id="9a234-106">若要确保启用 WiFi Direct，需要确保两项内容正确：</span><span class="sxs-lookup"><span data-stu-id="9a234-106">To make sure that WiFi Direct is enabled, two things need to be true:</span></span>
* <span data-ttu-id="9a234-107">USB WiFi 适配器的硬件需要支持 WiFi Direct，</span><span class="sxs-lookup"><span data-stu-id="9a234-107">the hardware of the USB WiFi adapter needs to support WiFi Direct,</span></span>
* <span data-ttu-id="9a234-108">USB WiFi 适配器的相应驱动程序需要支持 WiFi Direct。</span><span class="sxs-lookup"><span data-stu-id="9a234-108">the corresponding driver of the USB WiFi adapter needs to support WiFi Direct.</span></span> 

<span data-ttu-id="9a234-109">WiFi Direct 提供 WiFi 设备到设备连接的解决方案，无需无线接入点 (无线 AP) 来设置连接。</span><span class="sxs-lookup"><span data-stu-id="9a234-109">WiFi Direct provides a solution for WiFi device-to-device connectivity without the need for either a Wireless Access Point (wireless AP) to set up the connection.</span></span> <span data-ttu-id="9a234-110">查看以下资源中提供的 UWP [Windows。Devices.WiFiDirect 命名空间](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx)，查看可以使用 WiFiDirect 执行哪些操作。</span><span class="sxs-lookup"><span data-stu-id="9a234-110">Take a look at the UWP APIs available in the [Windows.Devices.WiFiDirect namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) to see what you can do with WiFiDirect.</span></span>

## <a name="supported-adapters"></a><span data-ttu-id="9a234-111">支持的适配器</span><span class="sxs-lookup"><span data-stu-id="9a234-111">Supported Adapters</span></span>

<span data-ttu-id="9a234-112">可以在支持的硬件页上找到已在 Windows 10 IoT 核心版测试的[WiFi 适配器](../learn-about-hardware/HardwareCompatList.md)列表。</span><span class="sxs-lookup"><span data-stu-id="9a234-112">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span> 

## <a name="basic-sample-for-wifi-direct"></a><span data-ttu-id="9a234-113">WiFi Direct 的基本示例</span><span class="sxs-lookup"><span data-stu-id="9a234-113">Basic sample for WiFi Direct</span></span>

<span data-ttu-id="9a234-114">可以使用 WiFi Direct UWP 示例 轻松测试 WiFi Direct [功能](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)。</span><span class="sxs-lookup"><span data-stu-id="9a234-114">You can easily test the WiFi Direct functionality with the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span></span> <span data-ttu-id="9a234-115">我们将使用 C# 版本并运行两个设备的示例。</span><span class="sxs-lookup"><span data-stu-id="9a234-115">We will use the C# version and run the sample of two devices.</span></span>

### <a name="set-up-the-two-devices"></a><span data-ttu-id="9a234-116">设置两个设备</span><span class="sxs-lookup"><span data-stu-id="9a234-116">Set up the two devices</span></span>
* <span data-ttu-id="9a234-117">MinnowBoardMax (MBM) Windows 10 IoT 核心版 (请参阅此处的说明，) CanaKit WiFi 适配器</span><span class="sxs-lookup"><span data-stu-id="9a234-117">MinnowBoardMax (MBM) running Windows 10 IoT Core (see instructions here), with a CanaKit WiFi dongle</span></span>
* <span data-ttu-id="9a234-118">连接监视器、键盘和鼠标移动到 MBM</span><span class="sxs-lookup"><span data-stu-id="9a234-118">Connect monitor, keyboard, and mouse to the MBM</span></span>
* <span data-ttu-id="9a234-119">运行Windows 10周年更新Windows 10电脑。</span><span class="sxs-lookup"><span data-stu-id="9a234-119">A Windows 10 PC running the latest Windows 10 Anniversary Update.</span></span> <span data-ttu-id="9a234-120">电脑 (或笔记本电脑) 需要具有 WiFi Direct 支持 (例如 Microsoft Surface) </span><span class="sxs-lookup"><span data-stu-id="9a234-120">The PC (or laptop) will need to have WiFi Direct support (e.g. a Microsoft Surface)</span></span>
* <span data-ttu-id="9a234-121">在 Visual Studio 计算机上安装 Windows 10 2017</span><span class="sxs-lookup"><span data-stu-id="9a234-121">Install Visual Studio 2017 on your Windows 10 PC</span></span>
* <span data-ttu-id="9a234-122">在此处的根目录 (或下载 wiFi Direct [UWP](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect) GitHub[示例) 。](https://github.com/Microsoft/Windows-universal-samples)</span><span class="sxs-lookup"><span data-stu-id="9a234-122">Clone or download the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(root of the GitHub repo is [here](https://github.com/Microsoft/Windows-universal-samples)).</span></span>
* <span data-ttu-id="9a234-123">在 2017 年 1 月加载 WiFi Direct UWP 示例的 C# Visual Studio版本</span><span class="sxs-lookup"><span data-stu-id="9a234-123">Load the C# version of the WiFi Direct UWP sample in Visual Studio 2017</span></span>

#### <a name="run-the-sample-on-the-two-devices"></a><span data-ttu-id="9a234-124">在两个设备上运行示例</span><span class="sxs-lookup"><span data-stu-id="9a234-124">Run the sample on the two devices</span></span>
* <span data-ttu-id="9a234-125">编译示例，在 MBM 上部署/运行它：</span><span class="sxs-lookup"><span data-stu-id="9a234-125">Compile the sample and deploy/run it on the MBM:</span></span>

    * <span data-ttu-id="9a234-126">将"解决方案平台"组合框设置为"x86"</span><span class="sxs-lookup"><span data-stu-id="9a234-126">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="9a234-127">从"运行"下拉列表中选择"远程计算机"</span><span class="sxs-lookup"><span data-stu-id="9a234-127">Select "Remote Machine" from the "Run" dropdown</span></span>
    * <span data-ttu-id="9a234-128">通过按 Ctrl-F5 或从"调试"菜单中选择"启动而不调试"，在 M (BM 上启动示例，而无需) </span><span class="sxs-lookup"><span data-stu-id="9a234-128">Start the sample on the MBM without debugging (either by pressing Ctrl-F5 or by selecting "Start Without Debugging" from the "Debug" menu)</span></span>
    * <span data-ttu-id="9a234-129">应会看到 WiFi Direct 示例在连接到 MBM 的监视器上运行</span><span class="sxs-lookup"><span data-stu-id="9a234-129">You should see the WiFi Direct sample running on the monitor connected to the MBM</span></span>
* <span data-ttu-id="9a234-130">编译示例，在电脑上部署/Windows 10它：</span><span class="sxs-lookup"><span data-stu-id="9a234-130">Compile the sample and deploy/run it on the Windows 10 PC:</span></span>
    * <span data-ttu-id="9a234-131">将"解决方案平台"组合框设置为"x86"</span><span class="sxs-lookup"><span data-stu-id="9a234-131">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="9a234-132">从"运行"下拉列表中选择"本地"</span><span class="sxs-lookup"><span data-stu-id="9a234-132">Select "Local" from the "Run" dropdown</span></span>
    * <span data-ttu-id="9a234-133">启动示例 (F5 或 Ctrl-F5) </span><span class="sxs-lookup"><span data-stu-id="9a234-133">Start the sample (either F5 or Ctrl-F5)</span></span>
    * <span data-ttu-id="9a234-134">应会看到 WiFi Direct 示例在 Windows 10 电脑上运行</span><span class="sxs-lookup"><span data-stu-id="9a234-134">You should see the WiFi Direct sample running on your Windows 10 PC</span></span>

### <a name="set-up-advertiser-and-connector"></a><span data-ttu-id="9a234-135">设置用户和连接器</span><span class="sxs-lookup"><span data-stu-id="9a234-135">Set up Advertiser and Connector</span></span>
* <span data-ttu-id="9a234-136">在 MBM 上，选择" (1") "，然后按"开始播发"按钮</span><span class="sxs-lookup"><span data-stu-id="9a234-136">On the MBM, select (1) "Advertiser" and press the "Start Advertisement" button</span></span>

    * <span data-ttu-id="9a234-137">MBM 将在 WiFi Direct 频道上开始广告自身</span><span class="sxs-lookup"><span data-stu-id="9a234-137">The MBM will start advertising itself on the WiFi Direct channel</span></span>

        !["配置"屏幕](../media/SetupWiFiDirect/Advertiser01.png)

        <span data-ttu-id="9a234-139&quot;>请注意应用底部的&quot;播发状态&quot;横幅。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9a234-139&quot;>Notice the &quot;Advertisement Status&quot; banner at the bottom of the app.</span></span>
    
* <span data-ttu-id=&quot;9a234-140&quot;>在 Windows 10 电脑上，选择&quot; (2") "连接器"，然后按"启动观察程序"按钮</span><span class="sxs-lookup"><span data-stu-id="9a234-140">On the Windows 10 PC, select (2) "Connector" and press the "Start Watcher" button</span></span> 

    * <span data-ttu-id="9a234-141">Windows 10电脑将开始扫描可用的 WiFi Direct 连接</span><span class="sxs-lookup"><span data-stu-id="9a234-141">The Windows 10 PC will start scanning for available WiFi Direct connections</span></span>
    * <span data-ttu-id="9a234-142">扫描完成后，应在"发现的设备"列表中看到 MBM 的名称</span><span class="sxs-lookup"><span data-stu-id="9a234-142">When the scanning is complete, you should see the name of your MBM in the "Discovered Devices" list</span></span>

        ![连接器配置屏幕](../media/SetupWiFiDirect/Connector01.png)

        <span data-ttu-id="9a234-144&quot;>可以看到两个设备 (我们感兴趣的&quot;ale-mbm01") 和"DeviceWatcher 枚举已完成"消息。</span><span class="sxs-lookup"><span data-stu-id="9a234-144">You can see two devices listed (we're interested in "ale-mbm01"), and the "DeviceWatcher enumeration completed" message.</span></span>

### <a name="pair-the-devices"></a><span data-ttu-id="9a234-145">对设备</span><span class="sxs-lookup"><span data-stu-id="9a234-145">Pair the devices</span></span>
* <span data-ttu-id="9a234-146">在 Windows 10 电脑上，从"发现的设备"列表中选择示例 ("ale-mbm01"中的 MBM) ，然后按"连接"按钮</span><span class="sxs-lookup"><span data-stu-id="9a234-146">On the Windows 10 PC, select the MBM ("ale-mbm01" in our example) from the "Discovered Devices" list and press the "Connect" button</span></span>
* <span data-ttu-id="9a234-147">在 Windows 10 电脑上，按"是"启动配对过程</span><span class="sxs-lookup"><span data-stu-id="9a234-147">On the Windows 10 PC, press "Yes" to initiate the pairing process</span></span>

    ![连接器开始配对](../media/SetupWiFiDirect/Connector02.png)

* <span data-ttu-id="9a234-149">在 MBM 监视器上，应该会显示一条包含 PIN 的消息</span><span class="sxs-lookup"><span data-stu-id="9a234-149">On the MBM monitor, you should a message with the PIN</span></span>

    !["安装 PIN"对话框](../media/SetupWiFiDirect/Advertiser02.png)

* <span data-ttu-id="9a234-151">在Windows 10电脑上，应会看到需要输入 PIN 的对话框</span><span class="sxs-lookup"><span data-stu-id="9a234-151">On the Windows 10 PC, you should see a dialog where you need to enter the PIN</span></span>

    !["连接器 PIN"对话框](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a><span data-ttu-id="9a234-153">在频道上交谈</span><span class="sxs-lookup"><span data-stu-id="9a234-153">Talk on the channel</span></span>
* <span data-ttu-id="9a234-154">两个设备应已连接。</span><span class="sxs-lookup"><span data-stu-id="9a234-154">The two devices should be connected.</span></span> <span data-ttu-id="9a234-155">在"已连接设备"列表的两个屏幕上 (示例中会看到随机生成的设备 ID) "hqffpzhz.ggg"</span><span class="sxs-lookup"><span data-stu-id="9a234-155">You should see a randomly generated device ID ("hqffpzhz.ggg" in our example) on both screens in the "Connected Devices" list</span></span>

    ![已连接的设备](../media/SetupWiFiDirect/Advertiser03.png)

    ![连接器连接设备](../media/SetupWiFiDirect/Connector04.png)

* <span data-ttu-id="9a234-158">现在，你已设置一个全双工 (或) 通道</span><span class="sxs-lookup"><span data-stu-id="9a234-158">You now have a full-duplex channel (or socket) setup</span></span>

    * <span data-ttu-id="9a234-159">在 MBM 上，从" ("列表中选择"hqffpzhz.ggg") 设备</span><span class="sxs-lookup"><span data-stu-id="9a234-159">on the MBM, select the device ("hqffpzhz.ggg") from the "Connected Devices" list</span></span>
    * <span data-ttu-id="9a234-160">在"输入消息"文本框中键入消息</span><span class="sxs-lookup"><span data-stu-id="9a234-160">type a message in the "Enter a message" textbox</span></span>
    * <span data-ttu-id="9a234-161">按"发送"按钮</span><span class="sxs-lookup"><span data-stu-id="9a234-161">press the "Send" button</span></span>
    * <span data-ttu-id="9a234-162">应会看到从计算机接收Windows 10消息</span><span class="sxs-lookup"><span data-stu-id="9a234-162">you should see the message being received from the Windows 10 PC</span></span>
    * <span data-ttu-id="9a234-163">尝试将消息从 Windows 10 PC 发送到 MBM</span><span class="sxs-lookup"><span data-stu-id="9a234-163">try sending a message from the Windows 10 PC to the MBM</span></span>
