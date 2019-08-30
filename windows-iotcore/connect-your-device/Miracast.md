---
title: IoT Core 上的 Miracast
author: saraclay
ms.author: saclayt
ms.date: 11/30/2017
ms.topic: article
description: 了解如何在设备上包含 Miracast 功能
keywords: windows iot, miracast, 连接
ms.openlocfilehash: c58def4b218d35c78532f54df4a74fb572c8549e
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168088"
---
# <a name="miracast-on-iot-core"></a><span data-ttu-id="dfdc9-104">IoT Core 上的 Miracast</span><span class="sxs-lookup"><span data-stu-id="dfdc9-104">Miracast on IoT Core</span></span>

<span data-ttu-id="dfdc9-105">本文档将演示如何在 IoT Core 设备上包含 Miracast 功能。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-105">This document will show you how to include Miracast functionality on your IoT Core device.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfdc9-106">此功能仅适用于有问必答版本17093及更高版本</span><span class="sxs-lookup"><span data-stu-id="dfdc9-106">This feature is only available on Insider Build 17093 and above</span></span>

## <a name="miracast-overview"></a><span data-ttu-id="dfdc9-107">Miracast 概述</span><span class="sxs-lookup"><span data-stu-id="dfdc9-107">Miracast Overview</span></span>

<span data-ttu-id="dfdc9-108">Miracast 连接由两个组件组成: 源和接收器。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-108">A Miracast connection is made up of two components: the Source and the Sink.</span></span> <span data-ttu-id="dfdc9-109">**Miracast 源**会将内容发送到**miracast 接收器**, 其中显示内容。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-109">The **Miracast Source** sends content to the **Miracast Sink**, which displays the content.</span></span> <span data-ttu-id="dfdc9-110">若要创建连接, 接收器会将其自身播发到连接的 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-110">To create the connection, the Sink advertises itself to the connected Wi-Fi network.</span></span> <span data-ttu-id="dfdc9-111">源使用**设备选取器**来选择接收器并请求连接。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-111">The Source uses the **Device Picker** to select the Sink and request a connection.</span></span> <span data-ttu-id="dfdc9-112">请求连接后, 接收器上的用户将收到一个警报, 指出源正在尝试建立连接, 并且必须验证是否应进行连接。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-112">Once the connection is requested, a user at the Sink receives an alert that the source is attempting to make a connection and must verify that the connection should take place.</span></span> <span data-ttu-id="dfdc9-113">出现这种情况后, 源将开始强制转换到接收器, 直到源取消了该连接或接收器停止公布。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-113">Once this happens, the Source begins casting to the Sink until either the Source cancels the connection or the Sink stops advertising.</span></span>

## <a name="hardware-requirements"></a><span data-ttu-id="dfdc9-114">硬件要求</span><span class="sxs-lookup"><span data-stu-id="dfdc9-114">Hardware requirements</span></span>

<span data-ttu-id="dfdc9-115">源设备和接收器设备都需要与 Miracast 兼容的 Wi-fi 和图形驱动程序和芯片组才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-115">Both Source and Sink devices require Miracast-compatible Wi-Fi and Graphics drivers and chipsets to function properly.</span></span> <span data-ttu-id="dfdc9-116">若要查明设备是否具有与 Miracast 兼容的硬件, 请运行:</span><span class="sxs-lookup"><span data-stu-id="dfdc9-116">To find out if your device has Miracast-compatible hardware, run:</span></span> 
```
netsh wlan show driver
```
<span data-ttu-id="dfdc9-117">在设备的命令提示符下。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-117">in the device's command prompt.</span></span>

<span data-ttu-id="dfdc9-118">如果设备支持 Miracast, 应会看到以下输出:</span><span class="sxs-lookup"><span data-stu-id="dfdc9-118">If the device supports Miracast, you should see the output below:</span></span>

![兼容设备输出](../media/Miracast/CompatibleDevice.png)

<span data-ttu-id="dfdc9-120">下表显示 IoT 核心参考平台的 Miracast 兼容性:</span><span class="sxs-lookup"><span data-stu-id="dfdc9-120">The below table shows Miracast compatibility for the IoT Core reference platforms:</span></span>

| <span data-ttu-id="dfdc9-121">插件</span><span class="sxs-lookup"><span data-stu-id="dfdc9-121">Board</span></span> | <span data-ttu-id="dfdc9-122">SoC</span><span class="sxs-lookup"><span data-stu-id="dfdc9-122">SoC</span></span> | <span data-ttu-id="dfdc9-123">提供 WiFi 驱动程序</span><span class="sxs-lookup"><span data-stu-id="dfdc9-123">WiFi Drivers Present</span></span> | <span data-ttu-id="dfdc9-124">图形驱动程序存在</span><span class="sxs-lookup"><span data-stu-id="dfdc9-124">Graphics Drivers Present</span></span> | <span data-ttu-id="dfdc9-125">Miracast 兼容</span><span class="sxs-lookup"><span data-stu-id="dfdc9-125">Miracast-Compatible</span></span> |
|-------|-----|----------------------|--------------------------|---------------------|
| <span data-ttu-id="dfdc9-126">Qualcomm Dragonboard 410c</span><span class="sxs-lookup"><span data-stu-id="dfdc9-126">Qualcomm Dragonboard 410c</span></span> | <span data-ttu-id="dfdc9-127">Snapdragon 410</span><span class="sxs-lookup"><span data-stu-id="dfdc9-127">Snapdragon 410</span></span> | <span data-ttu-id="dfdc9-128">是</span><span class="sxs-lookup"><span data-stu-id="dfdc9-128">Yes</span></span> | <span data-ttu-id="dfdc9-129">是</span><span class="sxs-lookup"><span data-stu-id="dfdc9-129">Yes</span></span> | <span data-ttu-id="dfdc9-130">是</span><span class="sxs-lookup"><span data-stu-id="dfdc9-130">Yes</span></span> |
| <span data-ttu-id="dfdc9-131">Raspberry Pi 2/3</span><span class="sxs-lookup"><span data-stu-id="dfdc9-131">Raspberry Pi 2/3</span></span> | <span data-ttu-id="dfdc9-132">Broadcom BCM283x</span><span class="sxs-lookup"><span data-stu-id="dfdc9-132">Broadcom BCM283x</span></span> | <span data-ttu-id="dfdc9-133">是</span><span class="sxs-lookup"><span data-stu-id="dfdc9-133">Yes</span></span> | <span data-ttu-id="dfdc9-134">否</span><span class="sxs-lookup"><span data-stu-id="dfdc9-134">No</span></span> | <span data-ttu-id="dfdc9-135">否</span><span class="sxs-lookup"><span data-stu-id="dfdc9-135">No</span></span> |
| <span data-ttu-id="dfdc9-136">Minnowboard Max</span><span class="sxs-lookup"><span data-stu-id="dfdc9-136">Minnowboard Max</span></span> | <span data-ttu-id="dfdc9-137">Intel Atom E3825</span><span class="sxs-lookup"><span data-stu-id="dfdc9-137">Intel Atom E3825</span></span> | <span data-ttu-id="dfdc9-138">是</span><span class="sxs-lookup"><span data-stu-id="dfdc9-138">Yes</span></span> | <span data-ttu-id="dfdc9-139">否</span><span class="sxs-lookup"><span data-stu-id="dfdc9-139">No</span></span> | <span data-ttu-id="dfdc9-140">否</span><span class="sxs-lookup"><span data-stu-id="dfdc9-140">No</span></span> |
| <span data-ttu-id="dfdc9-141">上 Squared</span><span class="sxs-lookup"><span data-stu-id="dfdc9-141">UP Squared</span></span> | <span data-ttu-id="dfdc9-142">Intel 赛扬 N3350</span><span class="sxs-lookup"><span data-stu-id="dfdc9-142">Intel Celeron N3350</span></span> | <span data-ttu-id="dfdc9-143">是</span><span class="sxs-lookup"><span data-stu-id="dfdc9-143">Yes</span></span> | <span data-ttu-id="dfdc9-144">是</span><span class="sxs-lookup"><span data-stu-id="dfdc9-144">Yes</span></span> | <span data-ttu-id="dfdc9-145">是</span><span class="sxs-lookup"><span data-stu-id="dfdc9-145">Yes</span></span> |


### <a name="wi-fi"></a><span data-ttu-id="dfdc9-146">WLAN</span><span class="sxs-lookup"><span data-stu-id="dfdc9-146">Wi-Fi</span></span>

<span data-ttu-id="dfdc9-147">设备的 Wi-fi 驱动程序和芯片集必须支持 Wi-fi Direct (除了其他功能) 才能支持 Miracast。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-147">The Wi-Fi driver and chipset for the device must support Wi-Fi Direct, among other capabilities, to support Miracast.</span></span> <span data-ttu-id="dfdc9-148">如果设备没有这些功能, 则可以改用 USB Wi-fi 转换器。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-148">If your device does not have these features, you can use a USB Wi-Fi dongle instead.</span></span> <span data-ttu-id="dfdc9-149">建议[300M 无线 USB 适配器](http://a.co/fdhEhV9)。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-149">We recommend the [300M Wireless USB Adapter](http://a.co/fdhEhV9).</span></span>

### <a name="graphics"></a><span data-ttu-id="dfdc9-150">图形</span><span class="sxs-lookup"><span data-stu-id="dfdc9-150">Graphics</span></span>

<span data-ttu-id="dfdc9-151">图形驱动程序和芯片组必须支持 h.264 编码和解码以支持 Miracast。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-151">The Graphics driver and chipset must support h.264 encoding and decoding to support Miracast.</span></span> <span data-ttu-id="dfdc9-152">如果设备没有兼容的图形驱动程序和/或芯片集, 则必须选择新的设备。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-152">If your device does not have a compatible graphics driver and/or chipset, you will have to pick a new device.</span></span> <span data-ttu-id="dfdc9-153">请在选择与 Miracast 兼容的设备时查阅上述矩阵。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-153">Please consult the above matrix when choosing a Miracast-compatible device.</span></span>

## <a name="windows-iot-as-a-miracast-sink"></a><span data-ttu-id="dfdc9-154">Windows IoT 作为 Miracast 接收器</span><span class="sxs-lookup"><span data-stu-id="dfdc9-154">Windows IoT as a Miracast Sink</span></span>

<span data-ttu-id="dfdc9-155">若要将设备启用为 Miracast 接收器, 你将需要在设备上启用连接应用, 然后在注册表中启用 Miracast。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-155">To enable your device as a Miracast sink, you will need to enable the Connect app on your device, then enable Miracast in the registry.</span></span>

### <a name="enable-the-connect-app"></a><span data-ttu-id="dfdc9-156">启用连接应用</span><span class="sxs-lookup"><span data-stu-id="dfdc9-156">Enable the Connect App</span></span>

<span data-ttu-id="dfdc9-157">若要启用连接应用, 需要在映像中包含**IOT_MIRACAST_RX_APP**功能。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-157">To enable the Connect app, you'll need to include the **IOT_MIRACAST_RX_APP** feature to your image.</span></span> <span data-ttu-id="dfdc9-158">还需要在映像中包含**Microsoft-Connect-Package**和**MICROSOFT-CONNECT-PACKAGE_LANG_XXXX** (其中 XXXX 是一种语言, 即 "enUS")。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-158">You'll also need to include  **Microsoft-Connect-Package.cab** and **Microsoft-Connect-Package_Lang_XXXX.cab** in your image (where XXXX is a language, i.e. "enUS").</span></span> 

<span data-ttu-id="dfdc9-159">有关如何向映像添加功能和包的详细信息, 请参阅[此页](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest)。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-159">See [this page](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) for more details about how to add features and packages to your image.</span></span> <span data-ttu-id="dfdc9-160">还可以按照[这些说明](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)将包和功能并行加载到现有映像。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-160">You can also side-load the package and features to existing images by following [these instructions](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage).</span></span> <span data-ttu-id="dfdc9-161">请记住, 在这种情况下, 加载此功能会阻止它接收更新。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-161">Keep in mind that side-loading this feature will prevent it from receiving updates.</span></span>


### <a name="enable-miracast"></a><span data-ttu-id="dfdc9-162">启用 Miracast</span><span class="sxs-lookup"><span data-stu-id="dfdc9-162">Enable Miracast</span></span>

<span data-ttu-id="dfdc9-163">通过[PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)或[Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)连接到设备, 并运行以下命令:</span><span class="sxs-lookup"><span data-stu-id="dfdc9-163">Connect to your device through [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) or the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) and run the following commands:</span></span>
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
<span data-ttu-id="dfdc9-164">这将在不同意通知的情况下启用 Miracast, 仅在安全网络上启用, 且仅在连接到/C 电源时启用。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-164">This will enable Miracast without a consent notification, only on secure networks, and only while connected to A/C power.</span></span> <span data-ttu-id="dfdc9-165">这是在 IoT Core 上运行 Miracast 接收器的建议方法。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-165">This is the recommended way to run a Miracast receiver on IoT Core.</span></span>

## <a name="windows-iot-as-a-miracast-source"></a><span data-ttu-id="dfdc9-166">作为 Miracast 源的 Windows IoT</span><span class="sxs-lookup"><span data-stu-id="dfdc9-166">Windows IoT as a Miracast Source</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfdc9-167">尝试将你的设备用作 Miracast 源之前, 请从[Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)关闭 IoTOnboardingTask 应用, 如下所示, 你只需要执行一次:![关闭 IoTOnboardingTask 应用](../media/Miracast/IoTOnboardingOff.gif)</span><span class="sxs-lookup"><span data-stu-id="dfdc9-167">Before trying to use your device as a Miracast Source, please turn off the IoTOnboardingTask app from the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) as shown below, which you'll only need to do once: ![Turn off IoTOnboardingTask app](../media/Miracast/IoTOnboardingOff.gif)</span></span>
>
> <span data-ttu-id="dfdc9-168">之后, 请重新启动设备</span><span class="sxs-lookup"><span data-stu-id="dfdc9-168">Afterwards, please restart the device</span></span>

<span data-ttu-id="dfdc9-169">可以通过应用中命名空间的`Windows.Media.Casting`公共 api 在兼容的设备上设置 Miracast 强制转换。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-169">You can set up Miracast casting on your compatible device through public APIs from the `Windows.Media.Casting` namespace in your app.</span></span>

<span data-ttu-id="dfdc9-170">若要查看这些 Api 的运行情况, 请下载[BASICMEDIACASTING UWP 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting)并在设备上运行它。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-170">To see these APIs in action, download the [BasicMediaCasting UWP sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) and run it on your device.</span></span> <span data-ttu-id="dfdc9-171">示例中的 Api 涵盖以下方案, 所有这些方案都在与 Miracast 兼容的 IoT Core 设备上运行:</span><span class="sxs-lookup"><span data-stu-id="dfdc9-171">The APIs in the sample cover the following scenarios, all of which run on Miracast-compatible IoT Core devices:</span></span>
1. <span data-ttu-id="dfdc9-172">基本媒体转换, 使用内置转换将内容发送到 Miracast、DLNA 和蓝牙设备</span><span class="sxs-lookup"><span data-stu-id="dfdc9-172">Basic Media Casting, which uses the built-in casting to send content to Miracast, DLNA, and Bluetooth devices</span></span>
2. <span data-ttu-id="dfdc9-173">使用强制转换选取器强制转换, 这允许你进一步自定义设备选取器</span><span class="sxs-lookup"><span data-stu-id="dfdc9-173">Casting Using the Casting Picker, which allows you to further customize the Device Picker</span></span>
3. <span data-ttu-id="dfdc9-174">使用自定义选取器进行强制转换, 该选取器阐释了如何生成用于选择设备的自定义 UX</span><span class="sxs-lookup"><span data-stu-id="dfdc9-174">Casting Using a Custom Picker, which illustrates how to build custom UX for selecting devices</span></span>

> [!NOTE]
> <span data-ttu-id="dfdc9-175">某些 Miracast 接收器 (Surface 膝上机、Surface Hub、带有无线显示适配器的 PC) 与 IoT 核心电影设备不兼容。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-175">Some Miracast sinks (Surface Laptop, Surface Hub, PC with a Wireless Display Adapter) are incompatible with IoT Core casting devices.</span></span> <span data-ttu-id="dfdc9-176">建议将[Microsoft 无线显示适配器](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001)用于兼容的监视器作为 Miracast 接收器。</span><span class="sxs-lookup"><span data-stu-id="dfdc9-176">We recommend using the [Microsoft Wireless Display Adapter](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) with a compatible monitor as your Miracast sink.</span></span>
