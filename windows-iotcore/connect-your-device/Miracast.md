---
title: Miracast IoT 核心
ms.date: 11/30/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在设备上Miracast功能。 阅读Miracast概述、硬件要求以及如何将 IoT Windows接收器Miracast源。
keywords: windows iot， miracast， 连接
ms.openlocfilehash: 72c2ef6b7a710cf120c45ebf265f0930c960d062
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229244"
---
# <a name="miracast-on-iot-core"></a><span data-ttu-id="2d072-105">Miracast IoT 核心</span><span class="sxs-lookup"><span data-stu-id="2d072-105">Miracast on IoT Core</span></span>

<span data-ttu-id="2d072-106">本文档将展示如何在 IoT core Miracast包括其他功能。</span><span class="sxs-lookup"><span data-stu-id="2d072-106">This document will show you how to include Miracast functionality on your IoT Core device.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d072-107">此功能仅在预览体验内部版本 17093 及以上版本上可用</span><span class="sxs-lookup"><span data-stu-id="2d072-107">This feature is only available on Insider Build 17093 and above</span></span>

## <a name="miracast-overview"></a><span data-ttu-id="2d072-108">Miracast概述</span><span class="sxs-lookup"><span data-stu-id="2d072-108">Miracast Overview</span></span>

<span data-ttu-id="2d072-109">一Miracast连接由两个组件组成：Source 和 Sink。</span><span class="sxs-lookup"><span data-stu-id="2d072-109">A Miracast connection is made up of two components: the Source and the Sink.</span></span> <span data-ttu-id="2d072-110">源 **Miracast将** 内容发送到 Miracast **接收器**，该接收器显示内容。</span><span class="sxs-lookup"><span data-stu-id="2d072-110">The **Miracast Source** sends content to the **Miracast Sink**, which displays the content.</span></span> <span data-ttu-id="2d072-111">若要创建连接，接收器将自身播发到连接的Wi-Fi网络。</span><span class="sxs-lookup"><span data-stu-id="2d072-111">To create the connection, the Sink advertises itself to the connected Wi-Fi network.</span></span> <span data-ttu-id="2d072-112">源使用 **设备选取器** 选择接收器并请求连接。</span><span class="sxs-lookup"><span data-stu-id="2d072-112">The Source uses the **Device Picker** to select the Sink and request a connection.</span></span> <span data-ttu-id="2d072-113">请求连接后，接收器的用户会收到一条警报，指出源正在尝试建立连接，并且必须验证连接是否应发生。</span><span class="sxs-lookup"><span data-stu-id="2d072-113">Once the connection is requested, a user at the Sink receives an alert that the source is attempting to make a connection and must verify that the connection should take place.</span></span> <span data-ttu-id="2d072-114">发生这种情况后，源开始强制转换到接收器，直到源取消连接或接收器停止广告。</span><span class="sxs-lookup"><span data-stu-id="2d072-114">Once this happens, the Source begins casting to the Sink until either the Source cancels the connection or the Sink stops advertising.</span></span>

## <a name="hardware-requirements"></a><span data-ttu-id="2d072-115">硬件要求</span><span class="sxs-lookup"><span data-stu-id="2d072-115">Hardware requirements</span></span>

<span data-ttu-id="2d072-116">源和接收器设备都需要Miracast兼容的Wi-Fi和图形驱动程序和芯片组正常工作。</span><span class="sxs-lookup"><span data-stu-id="2d072-116">Both Source and Sink devices require Miracast-compatible Wi-Fi and Graphics drivers and chipsets to function properly.</span></span> <span data-ttu-id="2d072-117">若要了解设备是否具有Miracast兼容硬件，请运行：</span><span class="sxs-lookup"><span data-stu-id="2d072-117">To find out if your device has Miracast-compatible hardware, run:</span></span> 
```
netsh wlan show driver
```
<span data-ttu-id="2d072-118">在设备的命令提示符下。</span><span class="sxs-lookup"><span data-stu-id="2d072-118">in the device's command prompt.</span></span>

<span data-ttu-id="2d072-119">如果设备支持Miracast，应会看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="2d072-119">If the device supports Miracast, you should see the output below:</span></span>

![兼容的设备输出](../media/Miracast/CompatibleDevice.png)

<span data-ttu-id="2d072-121">下表显示了 IoT Miracast平台的兼容性：</span><span class="sxs-lookup"><span data-stu-id="2d072-121">The below table shows Miracast compatibility for the IoT Core reference platforms:</span></span>

| <span data-ttu-id="2d072-122">Board</span><span class="sxs-lookup"><span data-stu-id="2d072-122">Board</span></span> | <span data-ttu-id="2d072-123">SoC</span><span class="sxs-lookup"><span data-stu-id="2d072-123">SoC</span></span> | <span data-ttu-id="2d072-124">WiFi 驱动程序存在</span><span class="sxs-lookup"><span data-stu-id="2d072-124">WiFi Drivers Present</span></span> | <span data-ttu-id="2d072-125">图形驱动程序存在</span><span class="sxs-lookup"><span data-stu-id="2d072-125">Graphics Drivers Present</span></span> | <span data-ttu-id="2d072-126">Miracast-Compatible</span><span class="sxs-lookup"><span data-stu-id="2d072-126">Miracast-Compatible</span></span> |
|-------|-----|----------------------|--------------------------|---------------------|
| <span data-ttu-id="2d072-127">Qualcomm Dragonboard 410c</span><span class="sxs-lookup"><span data-stu-id="2d072-127">Qualcomm Dragonboard 410c</span></span> | <span data-ttu-id="2d072-128">Snapdragon 410</span><span class="sxs-lookup"><span data-stu-id="2d072-128">Snapdragon 410</span></span> | <span data-ttu-id="2d072-129">是</span><span class="sxs-lookup"><span data-stu-id="2d072-129">Yes</span></span> | <span data-ttu-id="2d072-130">是</span><span class="sxs-lookup"><span data-stu-id="2d072-130">Yes</span></span> | <span data-ttu-id="2d072-131">是</span><span class="sxs-lookup"><span data-stu-id="2d072-131">Yes</span></span> |
| <span data-ttu-id="2d072-132">Raspberry Pi 2/3</span><span class="sxs-lookup"><span data-stu-id="2d072-132">Raspberry Pi 2/3</span></span> | <span data-ttu-id="2d072-133">Broadcom BCM283x</span><span class="sxs-lookup"><span data-stu-id="2d072-133">Broadcom BCM283x</span></span> | <span data-ttu-id="2d072-134">是</span><span class="sxs-lookup"><span data-stu-id="2d072-134">Yes</span></span> | <span data-ttu-id="2d072-135">否</span><span class="sxs-lookup"><span data-stu-id="2d072-135">No</span></span> | <span data-ttu-id="2d072-136">否</span><span class="sxs-lookup"><span data-stu-id="2d072-136">No</span></span> |
| <span data-ttu-id="2d072-137">Minnowboard Max</span><span class="sxs-lookup"><span data-stu-id="2d072-137">Minnowboard Max</span></span> | <span data-ttu-id="2d072-138">Intel Atom E3825</span><span class="sxs-lookup"><span data-stu-id="2d072-138">Intel Atom E3825</span></span> | <span data-ttu-id="2d072-139">是</span><span class="sxs-lookup"><span data-stu-id="2d072-139">Yes</span></span> | <span data-ttu-id="2d072-140">否</span><span class="sxs-lookup"><span data-stu-id="2d072-140">No</span></span> | <span data-ttu-id="2d072-141">否</span><span class="sxs-lookup"><span data-stu-id="2d072-141">No</span></span> |
| <span data-ttu-id="2d072-142">UP Squared</span><span class="sxs-lookup"><span data-stu-id="2d072-142">UP Squared</span></span> | <span data-ttu-id="2d072-143">Intel Celeron N3350</span><span class="sxs-lookup"><span data-stu-id="2d072-143">Intel Celeron N3350</span></span> | <span data-ttu-id="2d072-144">是</span><span class="sxs-lookup"><span data-stu-id="2d072-144">Yes</span></span> | <span data-ttu-id="2d072-145">是</span><span class="sxs-lookup"><span data-stu-id="2d072-145">Yes</span></span> | <span data-ttu-id="2d072-146">是</span><span class="sxs-lookup"><span data-stu-id="2d072-146">Yes</span></span> |


### <a name="wi-fi"></a><span data-ttu-id="2d072-147">Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="2d072-147">Wi-Fi</span></span>

<span data-ttu-id="2d072-148">设备Wi-Fi驱动程序和芯片组必须支持 Wi-Fi Direct 和其他功能，以支持Miracast。</span><span class="sxs-lookup"><span data-stu-id="2d072-148">The Wi-Fi driver and chipset for the device must support Wi-Fi Direct, among other capabilities, to support Miracast.</span></span> <span data-ttu-id="2d072-149">如果设备没有这些功能，可以改为使用 USB Wi-Fi适配器。</span><span class="sxs-lookup"><span data-stu-id="2d072-149">If your device does not have these features, you can use a USB Wi-Fi dongle instead.</span></span> <span data-ttu-id="2d072-150">建议使用 [300M 无线 USB 适配器](http://a.co/fdhEhV9)。</span><span class="sxs-lookup"><span data-stu-id="2d072-150">We recommend the [300M Wireless USB Adapter](http://a.co/fdhEhV9).</span></span>

### <a name="graphics"></a><span data-ttu-id="2d072-151">显卡</span><span class="sxs-lookup"><span data-stu-id="2d072-151">Graphics</span></span>

<span data-ttu-id="2d072-152">图形驱动程序和芯片组必须支持 h.264 编码和解码，以支持Miracast。</span><span class="sxs-lookup"><span data-stu-id="2d072-152">The Graphics driver and chipset must support h.264 encoding and decoding to support Miracast.</span></span> <span data-ttu-id="2d072-153">如果设备没有兼容的图形驱动程序和/或芯片组，必须选择新设备。</span><span class="sxs-lookup"><span data-stu-id="2d072-153">If your device does not have a compatible graphics driver and/or chipset, you will have to pick a new device.</span></span> <span data-ttu-id="2d072-154">选择与设备兼容的设备时，Miracast上述矩阵。</span><span class="sxs-lookup"><span data-stu-id="2d072-154">Please consult the above matrix when choosing a Miracast-compatible device.</span></span>

## <a name="windows-iot-as-a-miracast-sink"></a><span data-ttu-id="2d072-155">WindowsIoT 作为Miracast接收器</span><span class="sxs-lookup"><span data-stu-id="2d072-155">Windows IoT as a Miracast Sink</span></span>

<span data-ttu-id="2d072-156">若要将设备作为 Miracast接收器，需要在设备上启用 连接 应用，然后在注册表中Miracast应用。</span><span class="sxs-lookup"><span data-stu-id="2d072-156">To enable your device as a Miracast sink, you will need to enable the Connect app on your device, then enable Miracast in the registry.</span></span>

### <a name="enable-the-connect-app"></a><span data-ttu-id="2d072-157">启用 连接 应用</span><span class="sxs-lookup"><span data-stu-id="2d072-157">Enable the Connect App</span></span>

<span data-ttu-id="2d072-158">若要连接应用，需要将 IOT_MIRACAST_RX_APP **功能包括在** 映像中。</span><span class="sxs-lookup"><span data-stu-id="2d072-158">To enable the Connect app, you'll need to include the **IOT_MIRACAST_RX_APP** feature to your image.</span></span> <span data-ttu-id="2d072-159">在 XXXX **是** 一种语言Microsoft-Connect-Package.cab"enUS"Microsoft-Connect-Package_Lang_XXXX.cab中，还需要在映像 (和) 。 </span><span class="sxs-lookup"><span data-stu-id="2d072-159">You'll also need to include  **Microsoft-Connect-Package.cab** and **Microsoft-Connect-Package_Lang_XXXX.cab** in your image (where XXXX is a language, i.e. "enUS").</span></span> 

<span data-ttu-id="2d072-160">若要详细了解如何将功能和包添加到映像，请查看 [IoT 核心](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) 制造指南。</span><span class="sxs-lookup"><span data-stu-id="2d072-160">Check out the [IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) for more details about how to add features and packages to your image.</span></span> <span data-ttu-id="2d072-161">还可按照这些说明将包和功能旁加载到 [现有映像](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)。</span><span class="sxs-lookup"><span data-stu-id="2d072-161">You can also side-load the package and features to existing images by following [these instructions](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage).</span></span> <span data-ttu-id="2d072-162">请记住，旁加载此功能会阻止它接收更新。</span><span class="sxs-lookup"><span data-stu-id="2d072-162">Keep in mind that side-loading this feature will prevent it from receiving updates.</span></span>


### <a name="enable-miracast"></a><span data-ttu-id="2d072-163">启用Miracast</span><span class="sxs-lookup"><span data-stu-id="2d072-163">Enable Miracast</span></span>

<span data-ttu-id="2d072-164">连接[PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)或 Windows 设备门户连接到设备[，](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2d072-164">Connect to your device through [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) or the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) and run the following commands:</span></span>
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
<span data-ttu-id="2d072-165">这样，Miracast在安全网络上，并且仅在连接到 A/C 电源时，才允许无许可通知。</span><span class="sxs-lookup"><span data-stu-id="2d072-165">This will enable Miracast without a consent notification, only on secure networks, and only while connected to A/C power.</span></span> <span data-ttu-id="2d072-166">这是在 IoT 核心Miracast接收器的建议方法。</span><span class="sxs-lookup"><span data-stu-id="2d072-166">This is the recommended way to run a Miracast receiver on IoT Core.</span></span>

## <a name="windows-iot-as-a-miracast-source"></a><span data-ttu-id="2d072-167">WindowsIoT 作为Miracast源</span><span class="sxs-lookup"><span data-stu-id="2d072-167">Windows IoT as a Miracast Source</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d072-168">在尝试将设备用作 Miracast 源之前，请从 Windows 设备门户 关闭 IoTOnboardingTask 应用[，](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)如下所示，只需执行一次操作：关闭 ![ IoTOnboardingTask 应用](../media/Miracast/IoTOnboardingOff.gif)</span><span class="sxs-lookup"><span data-stu-id="2d072-168">Before trying to use your device as a Miracast Source, please turn off the IoTOnboardingTask app from the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) as shown below, which you'll only need to do once: ![Turn off IoTOnboardingTask app](../media/Miracast/IoTOnboardingOff.gif)</span></span>
>
> <span data-ttu-id="2d072-169">然后，请重启设备</span><span class="sxs-lookup"><span data-stu-id="2d072-169">Afterwards, please restart the device</span></span>

<span data-ttu-id="2d072-170">可以通过应用Miracast命名空间中的公共 API 在兼容设备上设置 `Windows.Media.Casting` 强制转换。</span><span class="sxs-lookup"><span data-stu-id="2d072-170">You can set up Miracast casting on your compatible device through public APIs from the `Windows.Media.Casting` namespace in your app.</span></span>

<span data-ttu-id="2d072-171">若要了解这些 API 的运行，请下载 [BasicMediaCasting UWP 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) ，然后在你的设备上运行它。</span><span class="sxs-lookup"><span data-stu-id="2d072-171">To see these APIs in action, download the [BasicMediaCasting UWP sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) and run it on your device.</span></span> <span data-ttu-id="2d072-172">示例中的 API 涵盖以下方案，所有这些方案都Miracast IoT Core 设备上运行：</span><span class="sxs-lookup"><span data-stu-id="2d072-172">The APIs in the sample cover the following scenarios, all of which run on Miracast-compatible IoT Core devices:</span></span>
1. <span data-ttu-id="2d072-173">基本媒体强制转换，它使用内置强制转换将内容发送到 Miracast、DLNA 和 蓝牙设备</span><span class="sxs-lookup"><span data-stu-id="2d072-173">Basic Media Casting, which uses the built-in casting to send content to Miracast, DLNA, and Bluetooth devices</span></span>
2. <span data-ttu-id="2d072-174">使用强制转换选取器进行强制转换，用于进一步自定义设备选取器</span><span class="sxs-lookup"><span data-stu-id="2d072-174">Casting Using the Casting Picker, which allows you to further customize the Device Picker</span></span>
3. <span data-ttu-id="2d072-175">使用自定义选取器进行强制转换，演示如何生成用于选择设备的自定义 UX</span><span class="sxs-lookup"><span data-stu-id="2d072-175">Casting Using a Custom Picker, which illustrates how to build custom UX for selecting devices</span></span>

> [!NOTE]
> <span data-ttu-id="2d072-176">具有无线Miracast适配器 (Surface Laptop、Surface Hub电脑的一些) 接收器与 IoT 核心强制转换设备不兼容。</span><span class="sxs-lookup"><span data-stu-id="2d072-176">Some Miracast sinks (Surface Laptop, Surface Hub, PC with a Wireless Display Adapter) are incompatible with IoT Core casting devices.</span></span> <span data-ttu-id="2d072-177">建议使用具有兼容[监视器的 Microsoft 无线](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001)显示适配器作为Miracast接收器。</span><span class="sxs-lookup"><span data-stu-id="2d072-177">We recommend using the [Microsoft Wireless Display Adapter](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) with a compatible monitor as your Miracast sink.</span></span>
