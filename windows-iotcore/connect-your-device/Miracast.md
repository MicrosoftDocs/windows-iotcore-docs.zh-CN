---
title: 在 IoT Core 上 Miracast
author: saraclay
ms.author: saclayt
ms.date: 11/30/2017
ms.topic: article
description: 了解如何包括你的设备上的 Miracast 功能
keywords: windows iot、 miracast、 连接性
ms.openlocfilehash: c58def4b218d35c78532f54df4a74fb572c8549e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512087"
---
# <a name="miracast-on-iot-core"></a><span data-ttu-id="6f1de-104">在 IoT Core 上 Miracast</span><span class="sxs-lookup"><span data-stu-id="6f1de-104">Miracast on IoT Core</span></span>

<span data-ttu-id="6f1de-105">本文档将演示如何以包含 Miracast IoT Core 设备上的功能。</span><span class="sxs-lookup"><span data-stu-id="6f1de-105">This document will show you how to include Miracast functionality on your IoT Core device.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f1de-106">此功能仅在内部生成 17093 及更高版本</span><span class="sxs-lookup"><span data-stu-id="6f1de-106">This feature is only available on Insider Build 17093 and above</span></span>

## <a name="miracast-overview"></a><span data-ttu-id="6f1de-107">Miracast 概述</span><span class="sxs-lookup"><span data-stu-id="6f1de-107">Miracast Overview</span></span>

<span data-ttu-id="6f1de-108">Miracast 连接由两个组件组成： 源和接收器。</span><span class="sxs-lookup"><span data-stu-id="6f1de-108">A Miracast connection is made up of two components: the Source and the Sink.</span></span> <span data-ttu-id="6f1de-109">**Miracast 源**发送到的内容**Miracast 接收器**，其中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="6f1de-109">The **Miracast Source** sends content to the **Miracast Sink**, which displays the content.</span></span> <span data-ttu-id="6f1de-110">若要创建的连接，接收器将公布自己为连接的 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="6f1de-110">To create the connection, the Sink advertises itself to the connected Wi-Fi network.</span></span> <span data-ttu-id="6f1de-111">源使用**设备选取器**选择接收器并请求连接的连接。</span><span class="sxs-lookup"><span data-stu-id="6f1de-111">The Source uses the **Device Picker** to select the Sink and request a connection.</span></span> <span data-ttu-id="6f1de-112">后请求连接时，接收器在用户将收到一条警报源尝试建立连接，必须验证该连接应发生。</span><span class="sxs-lookup"><span data-stu-id="6f1de-112">Once the connection is requested, a user at the Sink receives an alert that the source is attempting to make a connection and must verify that the connection should take place.</span></span> <span data-ttu-id="6f1de-113">一旦发生这种情况，源将开始强制转换为接收器，直到源取消连接或接收器停止公布自己。</span><span class="sxs-lookup"><span data-stu-id="6f1de-113">Once this happens, the Source begins casting to the Sink until either the Source cancels the connection or the Sink stops advertising.</span></span>

## <a name="hardware-requirements"></a><span data-ttu-id="6f1de-114">硬件要求</span><span class="sxs-lookup"><span data-stu-id="6f1de-114">Hardware requirements</span></span>

<span data-ttu-id="6f1de-115">源和接收器的设备需要 Miracast-兼容的 Wi-fi 和图形驱动程序和芯片集才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="6f1de-115">Both Source and Sink devices require Miracast-compatible Wi-Fi and Graphics drivers and chipsets to function properly.</span></span> <span data-ttu-id="6f1de-116">若要了解你的设备是否具有兼容 Miracast 的硬件，运行：</span><span class="sxs-lookup"><span data-stu-id="6f1de-116">To find out if your device has Miracast-compatible hardware, run:</span></span> 
```
netsh wlan show driver
```
<span data-ttu-id="6f1de-117">在设备的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="6f1de-117">in the device's command prompt.</span></span>

<span data-ttu-id="6f1de-118">如果设备支持 Miracast，应看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="6f1de-118">If the device supports Miracast, you should see the output below:</span></span>

![兼容的设备输出](../media/Miracast/CompatibleDevice.png)

<span data-ttu-id="6f1de-120">下表显示了 Miracast IoT Core 引用平台的兼容性：</span><span class="sxs-lookup"><span data-stu-id="6f1de-120">The below table shows Miracast compatibility for the IoT Core reference platforms:</span></span>

| <span data-ttu-id="6f1de-121">看板</span><span class="sxs-lookup"><span data-stu-id="6f1de-121">Board</span></span> | <span data-ttu-id="6f1de-122">SoC</span><span class="sxs-lookup"><span data-stu-id="6f1de-122">SoC</span></span> | <span data-ttu-id="6f1de-123">提供的 WiFi 驱动程序</span><span class="sxs-lookup"><span data-stu-id="6f1de-123">WiFi Drivers Present</span></span> | <span data-ttu-id="6f1de-124">显示图形驱动程序</span><span class="sxs-lookup"><span data-stu-id="6f1de-124">Graphics Drivers Present</span></span> | <span data-ttu-id="6f1de-125">Miracast-Compatible</span><span class="sxs-lookup"><span data-stu-id="6f1de-125">Miracast-Compatible</span></span> |
|-------|-----|----------------------|--------------------------|---------------------|
| <span data-ttu-id="6f1de-126">Qualcomm Dragonboard 410 c</span><span class="sxs-lookup"><span data-stu-id="6f1de-126">Qualcomm Dragonboard 410c</span></span> | <span data-ttu-id="6f1de-127">Snapdragon 410</span><span class="sxs-lookup"><span data-stu-id="6f1de-127">Snapdragon 410</span></span> | <span data-ttu-id="6f1de-128">是</span><span class="sxs-lookup"><span data-stu-id="6f1de-128">Yes</span></span> | <span data-ttu-id="6f1de-129">是</span><span class="sxs-lookup"><span data-stu-id="6f1de-129">Yes</span></span> | <span data-ttu-id="6f1de-130">是</span><span class="sxs-lookup"><span data-stu-id="6f1de-130">Yes</span></span> |
| <span data-ttu-id="6f1de-131">Raspberry Pi 2/3</span><span class="sxs-lookup"><span data-stu-id="6f1de-131">Raspberry Pi 2/3</span></span> | <span data-ttu-id="6f1de-132">Broadcom BCM283x</span><span class="sxs-lookup"><span data-stu-id="6f1de-132">Broadcom BCM283x</span></span> | <span data-ttu-id="6f1de-133">是</span><span class="sxs-lookup"><span data-stu-id="6f1de-133">Yes</span></span> | <span data-ttu-id="6f1de-134">否</span><span class="sxs-lookup"><span data-stu-id="6f1de-134">No</span></span> | <span data-ttu-id="6f1de-135">否</span><span class="sxs-lookup"><span data-stu-id="6f1de-135">No</span></span> |
| <span data-ttu-id="6f1de-136">Minnowboard Max</span><span class="sxs-lookup"><span data-stu-id="6f1de-136">Minnowboard Max</span></span> | <span data-ttu-id="6f1de-137">Intel Atom E3825</span><span class="sxs-lookup"><span data-stu-id="6f1de-137">Intel Atom E3825</span></span> | <span data-ttu-id="6f1de-138">是</span><span class="sxs-lookup"><span data-stu-id="6f1de-138">Yes</span></span> | <span data-ttu-id="6f1de-139">否</span><span class="sxs-lookup"><span data-stu-id="6f1de-139">No</span></span> | <span data-ttu-id="6f1de-140">否</span><span class="sxs-lookup"><span data-stu-id="6f1de-140">No</span></span> |
| <span data-ttu-id="6f1de-141">最多平方</span><span class="sxs-lookup"><span data-stu-id="6f1de-141">UP Squared</span></span> | <span data-ttu-id="6f1de-142">Intel Celeron N3350</span><span class="sxs-lookup"><span data-stu-id="6f1de-142">Intel Celeron N3350</span></span> | <span data-ttu-id="6f1de-143">是</span><span class="sxs-lookup"><span data-stu-id="6f1de-143">Yes</span></span> | <span data-ttu-id="6f1de-144">是</span><span class="sxs-lookup"><span data-stu-id="6f1de-144">Yes</span></span> | <span data-ttu-id="6f1de-145">是</span><span class="sxs-lookup"><span data-stu-id="6f1de-145">Yes</span></span> |


### <a name="wi-fi"></a><span data-ttu-id="6f1de-146">WLAN</span><span class="sxs-lookup"><span data-stu-id="6f1de-146">Wi-Fi</span></span>

<span data-ttu-id="6f1de-147">Wi-fi 驱动程序和设备的芯片集必须支持 Wi-Fi Direct，以及其他功能，以支持 Miracast。</span><span class="sxs-lookup"><span data-stu-id="6f1de-147">The Wi-Fi driver and chipset for the device must support Wi-Fi Direct, among other capabilities, to support Miracast.</span></span> <span data-ttu-id="6f1de-148">如果你的设备不具有这些功能，可以改为使用 USB Wi-fi 硬件保护装置。</span><span class="sxs-lookup"><span data-stu-id="6f1de-148">If your device does not have these features, you can use a USB Wi-Fi dongle instead.</span></span> <span data-ttu-id="6f1de-149">我们建议[300 M 无线 USB 适配器](http://a.co/fdhEhV9)。</span><span class="sxs-lookup"><span data-stu-id="6f1de-149">We recommend the [300M Wireless USB Adapter](http://a.co/fdhEhV9).</span></span>

### <a name="graphics"></a><span data-ttu-id="6f1de-150">显卡</span><span class="sxs-lookup"><span data-stu-id="6f1de-150">Graphics</span></span>

<span data-ttu-id="6f1de-151">图形驱动程序和芯片集必须支持 h.264 编码和解码以支持 Miracast。</span><span class="sxs-lookup"><span data-stu-id="6f1de-151">The Graphics driver and chipset must support h.264 encoding and decoding to support Miracast.</span></span> <span data-ttu-id="6f1de-152">如果你的设备不具有兼容的图形驱动程序和/或芯片组，，必须以选择新设备。</span><span class="sxs-lookup"><span data-stu-id="6f1de-152">If your device does not have a compatible graphics driver and/or chipset, you will have to pick a new device.</span></span> <span data-ttu-id="6f1de-153">请选择兼容 Miracast 的设备时，参阅上面的矩阵。</span><span class="sxs-lookup"><span data-stu-id="6f1de-153">Please consult the above matrix when choosing a Miracast-compatible device.</span></span>

## <a name="windows-iot-as-a-miracast-sink"></a><span data-ttu-id="6f1de-154">Windows IoT 作为 Miracast 接收器</span><span class="sxs-lookup"><span data-stu-id="6f1de-154">Windows IoT as a Miracast Sink</span></span>

<span data-ttu-id="6f1de-155">若要启用你的设备作为 Miracast 接收器，将需要启用 Connect 应用在你的设备，然后启用 Miracast 注册表中。</span><span class="sxs-lookup"><span data-stu-id="6f1de-155">To enable your device as a Miracast sink, you will need to enable the Connect app on your device, then enable Miracast in the registry.</span></span>

### <a name="enable-the-connect-app"></a><span data-ttu-id="6f1de-156">启用应用程序连接</span><span class="sxs-lookup"><span data-stu-id="6f1de-156">Enable the Connect App</span></span>

<span data-ttu-id="6f1de-157">若要使连接应用程序，你将需要包括**IOT_MIRACAST_RX_APP**到映像的功能。</span><span class="sxs-lookup"><span data-stu-id="6f1de-157">To enable the Connect app, you'll need to include the **IOT_MIRACAST_RX_APP** feature to your image.</span></span> <span data-ttu-id="6f1de-158">您还需要包括**Microsoft Connect Package.cab**并**Microsoft 连接 Package_Lang_XXXX.cab**映像 （其中 XXXX 是一种语言，即"enUS"） 中。</span><span class="sxs-lookup"><span data-stu-id="6f1de-158">You'll also need to include  **Microsoft-Connect-Package.cab** and **Microsoft-Connect-Package_Lang_XXXX.cab** in your image (where XXXX is a language, i.e. "enUS").</span></span> 

<span data-ttu-id="6f1de-159">请参阅[本页](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest)有关如何将功能和程序包添加到你的映像详细信息。</span><span class="sxs-lookup"><span data-stu-id="6f1de-159">See [this page](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) for more details about how to add features and packages to your image.</span></span> <span data-ttu-id="6f1de-160">您可以还旁加载的包和功能到现有的映像遵循[这些说明](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)。</span><span class="sxs-lookup"><span data-stu-id="6f1de-160">You can also side-load the package and features to existing images by following [these instructions](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage).</span></span> <span data-ttu-id="6f1de-161">请记住，旁加载此功能将阻止其接收更新。</span><span class="sxs-lookup"><span data-stu-id="6f1de-161">Keep in mind that side-loading this feature will prevent it from receiving updates.</span></span>


### <a name="enable-miracast"></a><span data-ttu-id="6f1de-162">启用 Miracast</span><span class="sxs-lookup"><span data-stu-id="6f1de-162">Enable Miracast</span></span>

<span data-ttu-id="6f1de-163">连接到你的设备通过[PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)或[Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="6f1de-163">Connect to your device through [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) or the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) and run the following commands:</span></span>
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
<span data-ttu-id="6f1de-164">这将不同意的情况下通知，仅在安全的网络和连接到交流电源时才启用 Miracast。</span><span class="sxs-lookup"><span data-stu-id="6f1de-164">This will enable Miracast without a consent notification, only on secure networks, and only while connected to A/C power.</span></span> <span data-ttu-id="6f1de-165">这是在 IoT Core 上运行 Miracast 接收方的建议的方法。</span><span class="sxs-lookup"><span data-stu-id="6f1de-165">This is the recommended way to run a Miracast receiver on IoT Core.</span></span>

## <a name="windows-iot-as-a-miracast-source"></a><span data-ttu-id="6f1de-166">Windows IoT 作为 Miracast 源</span><span class="sxs-lookup"><span data-stu-id="6f1de-166">Windows IoT as a Miracast Source</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f1de-167">然后尝试使用你的设备作为 Miracast 源，请关闭该 IoTOnboardingTask 应用从[Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)如下所示，这将只需执行一次：![关闭 IoTOnboardingTask 应用</span><span class="sxs-lookup"><span data-stu-id="6f1de-167">Before trying to use your device as a Miracast Source, please turn off the IoTOnboardingTask app from the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) as shown below, which you'll only need to do once: ![Turn off IoTOnboardingTask app</span></span>](../media/Miracast/IoTOnboardingOff.gif)
>
> <span data-ttu-id="6f1de-168">之后，请重启设备</span><span class="sxs-lookup"><span data-stu-id="6f1de-168">Afterwards, please restart the device</span></span>

<span data-ttu-id="6f1de-169">可以设置在通过从公共 Api 兼容设备上的 Miracast 强制转换`Windows.Media.Casting`应用程序中的命名空间。</span><span class="sxs-lookup"><span data-stu-id="6f1de-169">You can set up Miracast casting on your compatible device through public APIs from the `Windows.Media.Casting` namespace in your app.</span></span>

<span data-ttu-id="6f1de-170">若要查看操作中的这些 Api，请下载[BasicMediaCasting UWP 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting)和在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="6f1de-170">To see these APIs in action, download the [BasicMediaCasting UWP sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) and run it on your device.</span></span> <span data-ttu-id="6f1de-171">此示例中的 Api 包括以下情况下，所有这些在 IoT 核心版兼容 Miracast 的设备运行：</span><span class="sxs-lookup"><span data-stu-id="6f1de-171">The APIs in the sample cover the following scenarios, all of which run on Miracast-compatible IoT Core devices:</span></span>
1. <span data-ttu-id="6f1de-172">基本媒体强制转换，使用内置的强制转换来将内容发送到支持 Miracast、 DLNA 和蓝牙设备</span><span class="sxs-lookup"><span data-stu-id="6f1de-172">Basic Media Casting, which uses the built-in casting to send content to Miracast, DLNA, and Bluetooth devices</span></span>
2. <span data-ttu-id="6f1de-173">使用强制转换选取器，以便您可以进一步自定义设备选取器的强制转换</span><span class="sxs-lookup"><span data-stu-id="6f1de-173">Casting Using the Casting Picker, which allows you to further customize the Device Picker</span></span>
3. <span data-ttu-id="6f1de-174">强制转换使用自定义选取器，该图说明了如何构建自定义用户体验，用于选择设备</span><span class="sxs-lookup"><span data-stu-id="6f1de-174">Casting Using a Custom Picker, which illustrates how to build custom UX for selecting devices</span></span>

> [!NOTE]
> <span data-ttu-id="6f1de-175">某些 Miracast 接收器 (Surface Laptop，Surface Hub PC 使用无线显示适配器) 是与 IoT Core 强制转换设备不兼容。</span><span class="sxs-lookup"><span data-stu-id="6f1de-175">Some Miracast sinks (Surface Laptop, Surface Hub, PC with a Wireless Display Adapter) are incompatible with IoT Core casting devices.</span></span> <span data-ttu-id="6f1de-176">我们建议使用[Microsoft 无线显示适配器](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001)用作为 Miracast 接收器兼容的显示器。</span><span class="sxs-lookup"><span data-stu-id="6f1de-176">We recommend using the [Microsoft Wireless Display Adapter](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) with a compatible monitor as your Miracast sink.</span></span>
