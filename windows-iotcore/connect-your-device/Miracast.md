---
title: IoT Core 上的 Miracast
ms.date: 11/30/2017
ms.topic: article
description: 请参阅如何在设备上包含 Miracast 功能。 阅读 Miracast 概述、硬件要求，以及如何使 Windows IoT 成为 Miracast 接收器或源。
keywords: windows iot，miracast，连接
ms.openlocfilehash: 344d7af4c89ef3c2d41ea8261895884cdf174067
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782569"
---
# <a name="miracast-on-iot-core"></a><span data-ttu-id="e7409-105">IoT Core 上的 Miracast</span><span class="sxs-lookup"><span data-stu-id="e7409-105">Miracast on IoT Core</span></span>

<span data-ttu-id="e7409-106">本文档将演示如何在 IoT Core 设备上包含 Miracast 功能。</span><span class="sxs-lookup"><span data-stu-id="e7409-106">This document will show you how to include Miracast functionality on your IoT Core device.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e7409-107">此功能仅适用于有问必答版本17093及更高版本</span><span class="sxs-lookup"><span data-stu-id="e7409-107">This feature is only available on Insider Build 17093 and above</span></span>

## <a name="miracast-overview"></a><span data-ttu-id="e7409-108">Miracast 概述</span><span class="sxs-lookup"><span data-stu-id="e7409-108">Miracast Overview</span></span>

<span data-ttu-id="e7409-109">Miracast 连接由两个组件组成：源和接收器。</span><span class="sxs-lookup"><span data-stu-id="e7409-109">A Miracast connection is made up of two components: the Source and the Sink.</span></span> <span data-ttu-id="e7409-110">**Miracast 源**会将内容发送到**miracast 接收器**，其中显示内容。</span><span class="sxs-lookup"><span data-stu-id="e7409-110">The **Miracast Source** sends content to the **Miracast Sink**, which displays the content.</span></span> <span data-ttu-id="e7409-111">若要创建连接，接收器会将其自身播发到连接的 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="e7409-111">To create the connection, the Sink advertises itself to the connected Wi-Fi network.</span></span> <span data-ttu-id="e7409-112">源使用 **设备选取器** 来选择接收器并请求连接。</span><span class="sxs-lookup"><span data-stu-id="e7409-112">The Source uses the **Device Picker** to select the Sink and request a connection.</span></span> <span data-ttu-id="e7409-113">请求连接后，接收器上的用户将收到一个警报，指出源正在尝试建立连接，并且必须验证是否应进行连接。</span><span class="sxs-lookup"><span data-stu-id="e7409-113">Once the connection is requested, a user at the Sink receives an alert that the source is attempting to make a connection and must verify that the connection should take place.</span></span> <span data-ttu-id="e7409-114">出现这种情况后，源将开始强制转换到接收器，直到源取消了该连接或接收器停止公布。</span><span class="sxs-lookup"><span data-stu-id="e7409-114">Once this happens, the Source begins casting to the Sink until either the Source cancels the connection or the Sink stops advertising.</span></span>

## <a name="hardware-requirements"></a><span data-ttu-id="e7409-115">硬件要求</span><span class="sxs-lookup"><span data-stu-id="e7409-115">Hardware requirements</span></span>

<span data-ttu-id="e7409-116">源设备和接收器设备都需要与 Miracast 兼容的 Wi-fi 和图形驱动程序和芯片组才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="e7409-116">Both Source and Sink devices require Miracast-compatible Wi-Fi and Graphics drivers and chipsets to function properly.</span></span> <span data-ttu-id="e7409-117">若要查明设备是否具有与 Miracast 兼容的硬件，请运行：</span><span class="sxs-lookup"><span data-stu-id="e7409-117">To find out if your device has Miracast-compatible hardware, run:</span></span> 
```
netsh wlan show driver
```
<span data-ttu-id="e7409-118">在设备的命令提示符下。</span><span class="sxs-lookup"><span data-stu-id="e7409-118">in the device's command prompt.</span></span>

<span data-ttu-id="e7409-119">如果设备支持 Miracast，应会看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="e7409-119">If the device supports Miracast, you should see the output below:</span></span>

![兼容设备输出](../media/Miracast/CompatibleDevice.png)

<span data-ttu-id="e7409-121">下表显示 IoT 核心参考平台的 Miracast 兼容性：</span><span class="sxs-lookup"><span data-stu-id="e7409-121">The below table shows Miracast compatibility for the IoT Core reference platforms:</span></span>

| <span data-ttu-id="e7409-122">Board</span><span class="sxs-lookup"><span data-stu-id="e7409-122">Board</span></span> | <span data-ttu-id="e7409-123">SoC</span><span class="sxs-lookup"><span data-stu-id="e7409-123">SoC</span></span> | <span data-ttu-id="e7409-124">提供 WiFi 驱动程序</span><span class="sxs-lookup"><span data-stu-id="e7409-124">WiFi Drivers Present</span></span> | <span data-ttu-id="e7409-125">图形驱动程序存在</span><span class="sxs-lookup"><span data-stu-id="e7409-125">Graphics Drivers Present</span></span> | <span data-ttu-id="e7409-126">Miracast 兼容</span><span class="sxs-lookup"><span data-stu-id="e7409-126">Miracast-Compatible</span></span> |
|-------|-----|----------------------|--------------------------|---------------------|
| <span data-ttu-id="e7409-127">Qualcomm Dragonboard 410c</span><span class="sxs-lookup"><span data-stu-id="e7409-127">Qualcomm Dragonboard 410c</span></span> | <span data-ttu-id="e7409-128">Snapdragon 410</span><span class="sxs-lookup"><span data-stu-id="e7409-128">Snapdragon 410</span></span> | <span data-ttu-id="e7409-129">是</span><span class="sxs-lookup"><span data-stu-id="e7409-129">Yes</span></span> | <span data-ttu-id="e7409-130">是</span><span class="sxs-lookup"><span data-stu-id="e7409-130">Yes</span></span> | <span data-ttu-id="e7409-131">是</span><span class="sxs-lookup"><span data-stu-id="e7409-131">Yes</span></span> |
| <span data-ttu-id="e7409-132">Raspberry Pi 2/3</span><span class="sxs-lookup"><span data-stu-id="e7409-132">Raspberry Pi 2/3</span></span> | <span data-ttu-id="e7409-133">Broadcom BCM283x</span><span class="sxs-lookup"><span data-stu-id="e7409-133">Broadcom BCM283x</span></span> | <span data-ttu-id="e7409-134">是</span><span class="sxs-lookup"><span data-stu-id="e7409-134">Yes</span></span> | <span data-ttu-id="e7409-135">否</span><span class="sxs-lookup"><span data-stu-id="e7409-135">No</span></span> | <span data-ttu-id="e7409-136">否</span><span class="sxs-lookup"><span data-stu-id="e7409-136">No</span></span> |
| <span data-ttu-id="e7409-137">Minnowboard Max</span><span class="sxs-lookup"><span data-stu-id="e7409-137">Minnowboard Max</span></span> | <span data-ttu-id="e7409-138">Intel Atom E3825</span><span class="sxs-lookup"><span data-stu-id="e7409-138">Intel Atom E3825</span></span> | <span data-ttu-id="e7409-139">是</span><span class="sxs-lookup"><span data-stu-id="e7409-139">Yes</span></span> | <span data-ttu-id="e7409-140">否</span><span class="sxs-lookup"><span data-stu-id="e7409-140">No</span></span> | <span data-ttu-id="e7409-141">否</span><span class="sxs-lookup"><span data-stu-id="e7409-141">No</span></span> |
| <span data-ttu-id="e7409-142">上 Squared</span><span class="sxs-lookup"><span data-stu-id="e7409-142">UP Squared</span></span> | <span data-ttu-id="e7409-143">Intel 赛扬 N3350</span><span class="sxs-lookup"><span data-stu-id="e7409-143">Intel Celeron N3350</span></span> | <span data-ttu-id="e7409-144">是</span><span class="sxs-lookup"><span data-stu-id="e7409-144">Yes</span></span> | <span data-ttu-id="e7409-145">是</span><span class="sxs-lookup"><span data-stu-id="e7409-145">Yes</span></span> | <span data-ttu-id="e7409-146">是</span><span class="sxs-lookup"><span data-stu-id="e7409-146">Yes</span></span> |


### <a name="wi-fi"></a><span data-ttu-id="e7409-147">Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="e7409-147">Wi-Fi</span></span>

<span data-ttu-id="e7409-148">设备的 Wi-fi 驱动程序和芯片集必须支持 Wi-fi Direct （除了其他功能）才能支持 Miracast。</span><span class="sxs-lookup"><span data-stu-id="e7409-148">The Wi-Fi driver and chipset for the device must support Wi-Fi Direct, among other capabilities, to support Miracast.</span></span> <span data-ttu-id="e7409-149">如果设备没有这些功能，则可以改用 USB Wi-fi 转换器。</span><span class="sxs-lookup"><span data-stu-id="e7409-149">If your device does not have these features, you can use a USB Wi-Fi dongle instead.</span></span> <span data-ttu-id="e7409-150">建议 [300M 无线 USB 适配器](http://a.co/fdhEhV9)。</span><span class="sxs-lookup"><span data-stu-id="e7409-150">We recommend the [300M Wireless USB Adapter](http://a.co/fdhEhV9).</span></span>

### <a name="graphics"></a><span data-ttu-id="e7409-151">显卡</span><span class="sxs-lookup"><span data-stu-id="e7409-151">Graphics</span></span>

<span data-ttu-id="e7409-152">图形驱动程序和芯片组必须支持 h.264 编码和解码以支持 Miracast。</span><span class="sxs-lookup"><span data-stu-id="e7409-152">The Graphics driver and chipset must support h.264 encoding and decoding to support Miracast.</span></span> <span data-ttu-id="e7409-153">如果设备没有兼容的图形驱动程序和/或芯片集，则必须选择新的设备。</span><span class="sxs-lookup"><span data-stu-id="e7409-153">If your device does not have a compatible graphics driver and/or chipset, you will have to pick a new device.</span></span> <span data-ttu-id="e7409-154">请在选择与 Miracast 兼容的设备时查阅上述矩阵。</span><span class="sxs-lookup"><span data-stu-id="e7409-154">Please consult the above matrix when choosing a Miracast-compatible device.</span></span>

## <a name="windows-iot-as-a-miracast-sink"></a><span data-ttu-id="e7409-155">Windows IoT 作为 Miracast 接收器</span><span class="sxs-lookup"><span data-stu-id="e7409-155">Windows IoT as a Miracast Sink</span></span>

<span data-ttu-id="e7409-156">若要将设备启用为 Miracast 接收器，你将需要在设备上启用连接应用，然后在注册表中启用 Miracast。</span><span class="sxs-lookup"><span data-stu-id="e7409-156">To enable your device as a Miracast sink, you will need to enable the Connect app on your device, then enable Miracast in the registry.</span></span>

### <a name="enable-the-connect-app"></a><span data-ttu-id="e7409-157">启用连接应用</span><span class="sxs-lookup"><span data-stu-id="e7409-157">Enable the Connect App</span></span>

<span data-ttu-id="e7409-158">若要启用连接应用，需要将 **IOT_MIRACAST_RX_APP** 功能包含到映像。</span><span class="sxs-lookup"><span data-stu-id="e7409-158">To enable the Connect app, you'll need to include the **IOT_MIRACAST_RX_APP** feature to your image.</span></span> <span data-ttu-id="e7409-159">还需要在映像中包括  **Microsoft-Connect-Package.cab** 和 **Microsoft-Connect-Package_Lang_XXXX.cab** (其中 XXXX 是一种语言，即 "enUS" ) 。</span><span class="sxs-lookup"><span data-stu-id="e7409-159">You'll also need to include  **Microsoft-Connect-Package.cab** and **Microsoft-Connect-Package_Lang_XXXX.cab** in your image (where XXXX is a language, i.e. "enUS").</span></span> 

<span data-ttu-id="e7409-160">有关如何向映像添加功能和包的详细信息，请查看 [IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) 。</span><span class="sxs-lookup"><span data-stu-id="e7409-160">Check out the [IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) for more details about how to add features and packages to your image.</span></span> <span data-ttu-id="e7409-161">还可以按照 [这些说明](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)将包和功能并行加载到现有映像。</span><span class="sxs-lookup"><span data-stu-id="e7409-161">You can also side-load the package and features to existing images by following [these instructions](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage).</span></span> <span data-ttu-id="e7409-162">请记住，在这种情况下，加载此功能会阻止它接收更新。</span><span class="sxs-lookup"><span data-stu-id="e7409-162">Keep in mind that side-loading this feature will prevent it from receiving updates.</span></span>


### <a name="enable-miracast"></a><span data-ttu-id="e7409-163">启用 Miracast</span><span class="sxs-lookup"><span data-stu-id="e7409-163">Enable Miracast</span></span>

<span data-ttu-id="e7409-164">通过 [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) 或 [Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 连接到设备，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e7409-164">Connect to your device through [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) or the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) and run the following commands:</span></span>
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
<span data-ttu-id="e7409-165">这将在不同意通知的情况下启用 Miracast，仅在安全网络上启用，且仅在连接到/C 电源时启用。</span><span class="sxs-lookup"><span data-stu-id="e7409-165">This will enable Miracast without a consent notification, only on secure networks, and only while connected to A/C power.</span></span> <span data-ttu-id="e7409-166">这是在 IoT Core 上运行 Miracast 接收器的建议方法。</span><span class="sxs-lookup"><span data-stu-id="e7409-166">This is the recommended way to run a Miracast receiver on IoT Core.</span></span>

## <a name="windows-iot-as-a-miracast-source"></a><span data-ttu-id="e7409-167">作为 Miracast 源的 Windows IoT</span><span class="sxs-lookup"><span data-stu-id="e7409-167">Windows IoT as a Miracast Source</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e7409-168">尝试将你的设备用作 Miracast 源之前，请从 [Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 关闭 IoTOnboardingTask 应用，如下所示，你只需要执行一次： ![ 关闭 IoTOnboardingTask 应用](../media/Miracast/IoTOnboardingOff.gif)</span><span class="sxs-lookup"><span data-stu-id="e7409-168">Before trying to use your device as a Miracast Source, please turn off the IoTOnboardingTask app from the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) as shown below, which you'll only need to do once: ![Turn off IoTOnboardingTask app](../media/Miracast/IoTOnboardingOff.gif)</span></span>
>
> <span data-ttu-id="e7409-169">之后，请重新启动设备</span><span class="sxs-lookup"><span data-stu-id="e7409-169">Afterwards, please restart the device</span></span>

<span data-ttu-id="e7409-170">可以通过 `Windows.Media.Casting` 应用中命名空间的公共 api 在兼容的设备上设置 Miracast 强制转换。</span><span class="sxs-lookup"><span data-stu-id="e7409-170">You can set up Miracast casting on your compatible device through public APIs from the `Windows.Media.Casting` namespace in your app.</span></span>

<span data-ttu-id="e7409-171">若要查看这些 Api 的运行情况，请下载 [BASICMEDIACASTING UWP 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) 并在设备上运行它。</span><span class="sxs-lookup"><span data-stu-id="e7409-171">To see these APIs in action, download the [BasicMediaCasting UWP sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) and run it on your device.</span></span> <span data-ttu-id="e7409-172">示例中的 Api 涵盖以下方案，所有这些方案都在与 Miracast 兼容的 IoT Core 设备上运行：</span><span class="sxs-lookup"><span data-stu-id="e7409-172">The APIs in the sample cover the following scenarios, all of which run on Miracast-compatible IoT Core devices:</span></span>
1. <span data-ttu-id="e7409-173">基本媒体转换，使用内置转换将内容发送到 Miracast、DLNA 和蓝牙设备</span><span class="sxs-lookup"><span data-stu-id="e7409-173">Basic Media Casting, which uses the built-in casting to send content to Miracast, DLNA, and Bluetooth devices</span></span>
2. <span data-ttu-id="e7409-174">使用强制转换选取器强制转换，这允许你进一步自定义设备选取器</span><span class="sxs-lookup"><span data-stu-id="e7409-174">Casting Using the Casting Picker, which allows you to further customize the Device Picker</span></span>
3. <span data-ttu-id="e7409-175">使用自定义选取器进行强制转换，该选取器阐释了如何生成用于选择设备的自定义 UX</span><span class="sxs-lookup"><span data-stu-id="e7409-175">Casting Using a Custom Picker, which illustrates how to build custom UX for selecting devices</span></span>

> [!NOTE]
> <span data-ttu-id="e7409-176">某些 Miracast 接收器 (Surface 便携机、Surface Hub、具有无线显示适配器的 PC) 与 IoT 核心强制转换设备不兼容。</span><span class="sxs-lookup"><span data-stu-id="e7409-176">Some Miracast sinks (Surface Laptop, Surface Hub, PC with a Wireless Display Adapter) are incompatible with IoT Core casting devices.</span></span> <span data-ttu-id="e7409-177">建议将 [Microsoft 无线显示适配器](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) 用于兼容的监视器作为 Miracast 接收器。</span><span class="sxs-lookup"><span data-stu-id="e7409-177">We recommend using the [Microsoft Wireless Display Adapter](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) with a compatible monitor as your Miracast sink.</span></span>
