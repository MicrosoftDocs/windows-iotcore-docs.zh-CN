---
title: 在 Windows 10 Iot Core 设备上使用 WiFi Direct
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何设置、 测试和启用了 USB wifi 适配器的设备上使用 wifi direct。
keywords: windows iot、 直接的 wifi，安装程序、 wifi、 设备
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510894"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a><span data-ttu-id="076e4-104">在 Windows 10 IoT Core 设备上使用 WiFi Direct</span><span class="sxs-lookup"><span data-stu-id="076e4-104">Using WiFi Direct on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="076e4-105">支持 WiFi 直接在 Windows 10 IoT Core 上通过 WiFi 直接使用的设备启用 USB WiFi 适配器。</span><span class="sxs-lookup"><span data-stu-id="076e4-105">WiFi Direct is supported on Windows 10 IoT Core devices through the use of a WiFi Direct enabled USB WiFi adapter.</span></span> <span data-ttu-id="076e4-106">若要确保 WiFi 直接启用了两件事情需要为 true:</span><span class="sxs-lookup"><span data-stu-id="076e4-106">To make sure that WiFi Direct is enabled two things need to be true:</span></span>
* <span data-ttu-id="076e4-107">需要支持 WiFi Direct USB WiFi 适配器的硬件</span><span class="sxs-lookup"><span data-stu-id="076e4-107">the hardware of the USB WiFi adapter needs to support WiFi Direct,</span></span>
* <span data-ttu-id="076e4-108">USB WiFi 适配器的相应驱动程序需要支持 WiFi Direct。</span><span class="sxs-lookup"><span data-stu-id="076e4-108">the corresponding driver of the USB WiFi adapter needs to support WiFi Direct.</span></span> 

<span data-ttu-id="076e4-109">WiFi 直接提供的 WiFi 设备的连接，而无需为任一无线访问点 (无线 AP) 来设置连接的解决方案。</span><span class="sxs-lookup"><span data-stu-id="076e4-109">WiFi Direct provides a solution for WiFi device-to-device connectivity without the need for either a Wireless Access Point (wireless AP) to setup the connection.</span></span> <span data-ttu-id="076e4-110">看一看中提供的 UWP Api [Windows.Devices.WiFiDirect 命名空间](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx)若要查看对 WiFiDirect 可以执行哪些操作。</span><span class="sxs-lookup"><span data-stu-id="076e4-110">Take a look at the UWP APIs available in the [Windows.Devices.WiFiDirect namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) to see what you can do with WiFiDirect.</span></span>

## <a name="supported-adapters"></a><span data-ttu-id="076e4-111">支持的适配器</span><span class="sxs-lookup"><span data-stu-id="076e4-111">Supported Adapters</span></span>

<span data-ttu-id="076e4-112">Windows 10 IoT Core 进行了测试的 WiFi 适配器的列表，可我们[支持硬件](../learn-about-hardware/HardwareCompatList.md)页。</span><span class="sxs-lookup"><span data-stu-id="076e4-112">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span> 

## <a name="basic-sample-for-wifi-direct"></a><span data-ttu-id="076e4-113">WiFi 直接的基本示例</span><span class="sxs-lookup"><span data-stu-id="076e4-113">Basic sample for WiFi Direct</span></span>

<span data-ttu-id="076e4-114">您可以轻松地测试 WiFi 直接功能使用 WiFi 直接 UWP[示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)。</span><span class="sxs-lookup"><span data-stu-id="076e4-114">You can easily test the WiFi Direct functionality with the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span></span> <span data-ttu-id="076e4-115">我们将使用C#版本并运行两个设备的示例。</span><span class="sxs-lookup"><span data-stu-id="076e4-115">We will use the C# version and run the sample of two devices.</span></span>

### <a name="set-up-the-two-devices"></a><span data-ttu-id="076e4-116">设置两个设备</span><span class="sxs-lookup"><span data-stu-id="076e4-116">Set up the two devices</span></span>
* <span data-ttu-id="076e4-117">MinnowBoardMax (MBM) 运行 Windows 10 IoT Core （请参阅此处的说明），与 CanaKit WiFi 硬件保护装置</span><span class="sxs-lookup"><span data-stu-id="076e4-117">MinnowBoardMax (MBM) running Windows 10 IoT Core (see instructions here), with a CanaKit WiFi dongle</span></span>
* <span data-ttu-id="076e4-118">监视器、 键盘和鼠标连接到 MBM</span><span class="sxs-lookup"><span data-stu-id="076e4-118">Connect monitor, keyboard and mouse to the MBM</span></span>
* <span data-ttu-id="076e4-119">运行最新的 Windows 10 周年更新的 Windows 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="076e4-119">A Windows 10 PC running the latest Windows 10 Anniversary Update.</span></span> <span data-ttu-id="076e4-120">PC （或便携式计算机） 将需要具有 WiFi 直接支持 (例如 Microsoft Surface)</span><span class="sxs-lookup"><span data-stu-id="076e4-120">The PC (or laptop) will need to have WiFi Direct support (e.g. a Microsoft Surface)</span></span>
* <span data-ttu-id="076e4-121">在 Windows 10 电脑上安装 Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="076e4-121">Install Visual Studio 2017 on your Windows 10 PC</span></span>
* <span data-ttu-id="076e4-122">克隆或下载 WiFi 直接 UWP[示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(GitHub 存储库的根是[此处](https://github.com/Microsoft/Windows-universal-samples))。</span><span class="sxs-lookup"><span data-stu-id="076e4-122">Clone or download the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(root of the GitHub repo is [here](https://github.com/Microsoft/Windows-universal-samples)).</span></span>
* <span data-ttu-id="076e4-123">加载C#版本的 Visual Studio 2017 中的 WiFi 直接 UWP 示例</span><span class="sxs-lookup"><span data-stu-id="076e4-123">Load the C# version of the WiFi Direct UWP sample in Visual Studio 2017</span></span>

#### <a name="run-the-sample-on-the-two-devices"></a><span data-ttu-id="076e4-124">两个设备上运行示例</span><span class="sxs-lookup"><span data-stu-id="076e4-124">Run the sample on the two devices</span></span>
* <span data-ttu-id="076e4-125">编译该示例并部署/运行它 MBM 上：</span><span class="sxs-lookup"><span data-stu-id="076e4-125">Compile the sample and deploy/run it on the MBM:</span></span>

    * <span data-ttu-id="076e4-126">设置为"x86"的"解决方案平台"组合框</span><span class="sxs-lookup"><span data-stu-id="076e4-126">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="076e4-127">从"运行"的下拉列表中选择"远程计算机"</span><span class="sxs-lookup"><span data-stu-id="076e4-127">Select "Remote Machine" from the "Run" dropdown</span></span>
    * <span data-ttu-id="076e4-128">而不进行调试 （通过按 Ctrl-F5 或从"调试"菜单中选择"启动但不调试"） 上 MBM 启动示例</span><span class="sxs-lookup"><span data-stu-id="076e4-128">Start the sample on the MBM without debugging (either by pressing Ctrl-F5 or by selecting "Start Without Debugging" from the "Debug" menu)</span></span>
    * <span data-ttu-id="076e4-129">应看到 WiFi 直接示例连接到 MBM 在监视器上运行</span><span class="sxs-lookup"><span data-stu-id="076e4-129">You should see the WiFi Direct sample running on the monitor connected to the MBM</span></span>
* <span data-ttu-id="076e4-130">编译该示例并部署/运行其 Windows 10 电脑上：</span><span class="sxs-lookup"><span data-stu-id="076e4-130">Compile the sample and deploy/run it on the Windows 10 PC:</span></span>
    * <span data-ttu-id="076e4-131">设置为"x86"的"解决方案平台"组合框</span><span class="sxs-lookup"><span data-stu-id="076e4-131">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="076e4-132">从"运行"下拉列表中选择"本地"</span><span class="sxs-lookup"><span data-stu-id="076e4-132">Select "Local" from the "Run" dropdown</span></span>
    * <span data-ttu-id="076e4-133">启动 （F5 或 Ctrl-F5） 示例</span><span class="sxs-lookup"><span data-stu-id="076e4-133">Start the sample (either F5 or Ctrl-F5)</span></span>
    * <span data-ttu-id="076e4-134">应看到 WiFi 直接示例在 Windows 10 电脑上运行</span><span class="sxs-lookup"><span data-stu-id="076e4-134">You should see the WiFi Direct sample running on your Windows 10 PC</span></span>

### <a name="set-up-advertiser-and-connector"></a><span data-ttu-id="076e4-135">将广告和连接器设置</span><span class="sxs-lookup"><span data-stu-id="076e4-135">Set up Advertiser and Connector</span></span>
* <span data-ttu-id="076e4-136">在 MBM，选择 (1)"广告"并按"启动播发"按钮</span><span class="sxs-lookup"><span data-stu-id="076e4-136">On the MBM, select (1) "Advertiser" and press the "Start Advertisement" button</span></span>

    * <span data-ttu-id="076e4-137">MBM 将启动其自身公布 WiFi 直接通道上</span><span class="sxs-lookup"><span data-stu-id="076e4-137">The MBM will start advertising itself on the WiFi Direct channel</span></span>

        ![广告配置屏幕](../media/SetupWiFiDirect/Advertiser01.png)

        <span data-ttu-id="076e4-139">请注意，在应用程序底部的"播发状态"横幅。</span><span class="sxs-lookup"><span data-stu-id="076e4-139">Notice the "Advertisement Status" banner at the bottom of the app.</span></span>
    
* <span data-ttu-id="076e4-140">在 Windows 10 PC 上，选择 (2)"连接器"，然后按"启动观察程序"按钮</span><span class="sxs-lookup"><span data-stu-id="076e4-140">On the Windows 10 PC, select (2) "Connector" and press the "Start Watcher" button</span></span> 

    * <span data-ttu-id="076e4-141">Windows 10 电脑将启动扫描提供的 WiFi 直接连接</span><span class="sxs-lookup"><span data-stu-id="076e4-141">The Windows 10 PC will start scanning for available WiFi Direct connections</span></span>
    * <span data-ttu-id="076e4-142">扫描完成后，您应该看到你 MBM"发现的设备"列表中的名称</span><span class="sxs-lookup"><span data-stu-id="076e4-142">When the scanning is complete, you should see the name of your MBM in the "Discovered Devices" list</span></span>

        ![连接器配置屏幕](../media/SetupWiFiDirect/Connector01.png)

        <span data-ttu-id="076e4-144">可以看到列出的两个设备 （我们感兴趣"ale mbm01"），和"DeviceWatcher 枚举已完成"消息。</span><span class="sxs-lookup"><span data-stu-id="076e4-144">You can see two devices listed (we're interested in "ale-mbm01"), and the "DeviceWatcher enumeration completed" message.</span></span>

### <a name="pair-the-devices"></a><span data-ttu-id="076e4-145">对设备</span><span class="sxs-lookup"><span data-stu-id="076e4-145">Pair the devices</span></span>
* <span data-ttu-id="076e4-146">在 Windows 10 PC 上，从"发现的设备"列表中选择 MBM ("ale-mbm01"在我们的示例)，然后按"连接"按钮</span><span class="sxs-lookup"><span data-stu-id="076e4-146">On the Windows 10 PC, select the MBM ("ale-mbm01" in our example) from the "Discovered Devices" list and press the "Connect" button</span></span>
* <span data-ttu-id="076e4-147">在 Windows 10 PC 上，按"是"以启动配对过程</span><span class="sxs-lookup"><span data-stu-id="076e4-147">On the Windows 10 PC, press "Yes" to initiate the pairing process</span></span>

    ![连接器开始配对](../media/SetupWiFiDirect/Connector02.png)

* <span data-ttu-id="076e4-149">MBM 监视器上，您应该使用 PIN 的消息</span><span class="sxs-lookup"><span data-stu-id="076e4-149">On the MBM monitor you should a message with the PIN</span></span>

    ![广告商 PIN 对话框](../media/SetupWiFiDirect/Advertiser02.png)

* <span data-ttu-id="076e4-151">在 Windows 10 电脑，你会看到一个对话框，您需要输入 PIN</span><span class="sxs-lookup"><span data-stu-id="076e4-151">On the Windows 10 PC, you should see a dialog where you need to enter the PIN</span></span>

    ![连接器 PIN 对话框](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a><span data-ttu-id="076e4-153">通信通道</span><span class="sxs-lookup"><span data-stu-id="076e4-153">Talk on the channel</span></span>
* <span data-ttu-id="076e4-154">应连接两个设备。</span><span class="sxs-lookup"><span data-stu-id="076e4-154">The two devices should be connected.</span></span> <span data-ttu-id="076e4-155">在"连接到设备"列表中的两个屏幕上看到一个随机生成的设备 id (在本示例中的"hqffpzhz.ggg")</span><span class="sxs-lookup"><span data-stu-id="076e4-155">You should see a randomly generated device id ("hqffpzhz.ggg" in our example) on both screens in the "Connected Devices" list</span></span>

    ![广告商连接的设备](../media/SetupWiFiDirect/Advertiser03.png)

    ![连接器连接的设备](../media/SetupWiFiDirect/Connector04.png)

* <span data-ttu-id="076e4-158">现在有完全双工通道 （或套接字） 设置</span><span class="sxs-lookup"><span data-stu-id="076e4-158">You now have a full-duplex channel (or socket) set up</span></span>

    * <span data-ttu-id="076e4-159">MBM 上设备 ("hqffpzhz.ggg") 从列表中选择"连接到设备"</span><span class="sxs-lookup"><span data-stu-id="076e4-159">on the MBM, select the device ("hqffpzhz.ggg") from the "Connected Devices" list</span></span>
    * <span data-ttu-id="076e4-160">在"输入一条消息"文本框中键入一条消息</span><span class="sxs-lookup"><span data-stu-id="076e4-160">type a message in the "Enter a message" textbox</span></span>
    * <span data-ttu-id="076e4-161">按"发送"按钮</span><span class="sxs-lookup"><span data-stu-id="076e4-161">press the "Send" button</span></span>
    * <span data-ttu-id="076e4-162">你应看到 Windows 10 电脑正在接收的消息</span><span class="sxs-lookup"><span data-stu-id="076e4-162">you should see the message being received from the Windows 10 PC</span></span>
    * <span data-ttu-id="076e4-163">尝试从 Windows 10 电脑的一条消息发送到 MBM</span><span class="sxs-lookup"><span data-stu-id="076e4-163">try sending a message from the Windows 10 PC to the MBM</span></span>
