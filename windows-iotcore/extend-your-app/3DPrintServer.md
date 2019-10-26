---
title: 带有 Windows 10 IoT Core 的网络3D 打印机
ms.date: 09/05/2017
ms.topic: article
description: 了解如何将 Windows 10 IoT Core 设备转换为打印服务器，并将3D 打印机连接到该服务器。
keywords: windows iot，3D，3D 打印机，打印服务器，网络3D 打印机
ms.openlocfilehash: 3c11756f7832952f816978244d401d1d735a8f80
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918199"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a><span data-ttu-id="d9649-104">带有 Windows 10 IoT Core 的网络3D 打印机</span><span class="sxs-lookup"><span data-stu-id="d9649-104">Network 3D Printer with Windows 10 IoT Core</span></span>

<span data-ttu-id="d9649-105">将 Windows 10 IoT Core 设备转换为打印服务器，并将3D 打印机连接到该服务器。</span><span class="sxs-lookup"><span data-stu-id="d9649-105">Turn your Windows 10 IoT Core device into a print server and connect your 3D Printer to it.</span></span> <span data-ttu-id="d9649-106">你将能够从其他设备通过无线方式访问打印机。</span><span class="sxs-lookup"><span data-stu-id="d9649-106">You will be able to access your printer wirelessly from other devices.</span></span>

## <a name="1-install-windows-10-iot-core-on-your-device"></a><span data-ttu-id="d9649-107">1. 在设备上安装 Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="d9649-107">1. Install Windows 10 IoT Core on your device</span></span>
___
<span data-ttu-id="d9649-108">在开始之前，你将需要：</span><span class="sxs-lookup"><span data-stu-id="d9649-108">Before you start, you will need:</span></span>

* <span data-ttu-id="d9649-109">安装了最新版本的 Windows 10 IoT Core 内幕预览版的板。</span><span class="sxs-lookup"><span data-stu-id="d9649-109">A board with the latest version of Windows 10 IoT Core Insider Preview installed.</span></span> <span data-ttu-id="d9649-110">请按照[入门指南](https://developer.microsoft.com/en-us/windows/iot/getstarted)获取 IoT 面板应用并安装 Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="d9649-110">Follow the [Get Started guide](https://developer.microsoft.com/en-us/windows/iot/getstarted) to get the IoT Dashboard app and install Windows 10 IoT Core.</span></span>
* <span data-ttu-id="d9649-111">与我们的网络3D 打印机应用兼容的3D 打印机：</span><span class="sxs-lookup"><span data-stu-id="d9649-111">A 3D Printer compatible with our Network 3D Printer app:</span></span>

    * <span data-ttu-id="d9649-112">Lulzbot Taz 6</span><span class="sxs-lookup"><span data-stu-id="d9649-112">Lulzbot Taz 6</span></span>
    * <span data-ttu-id="d9649-113">Makergear M2</span><span class="sxs-lookup"><span data-stu-id="d9649-113">Makergear M2</span></span>
    * <span data-ttu-id="d9649-114">Printrbot 重头戏、Plus 和 Simple</span><span class="sxs-lookup"><span data-stu-id="d9649-114">Printrbot Play, Plus and Simple</span></span>
    * <span data-ttu-id="d9649-115">Prusa i3 Mk2</span><span class="sxs-lookup"><span data-stu-id="d9649-115">Prusa i3 Mk2</span></span>
    * <span data-ttu-id="d9649-116">Ultimaker 原始和原始 +</span><span class="sxs-lookup"><span data-stu-id="d9649-116">Ultimaker Original and Original+</span></span>
    * <span data-ttu-id="d9649-117">Ultimaker 2 和 2 +</span><span class="sxs-lookup"><span data-stu-id="d9649-117">Ultimaker 2 and 2+</span></span>
    * <span data-ttu-id="d9649-118">Ultimaker 2 扩展和扩展 +</span><span class="sxs-lookup"><span data-stu-id="d9649-118">Ultimaker 2 Extended and Extended+</span></span>
    * <span data-ttu-id="d9649-119">CraftBot 2</span><span class="sxs-lookup"><span data-stu-id="d9649-119">CraftBot 2</span></span>
    * <span data-ttu-id="d9649-120">CraftBot PLUS</span><span class="sxs-lookup"><span data-stu-id="d9649-120">CraftBot PLUS</span></span>
    * <span data-ttu-id="d9649-121">LulzBot 微型</span><span class="sxs-lookup"><span data-stu-id="d9649-121">LulzBot Mini</span></span>
    * <span data-ttu-id="d9649-122">Velleman K8200</span><span class="sxs-lookup"><span data-stu-id="d9649-122">Velleman K8200</span></span>

## <a name="2-connect-your-3d-printer-to-your-device"></a><span data-ttu-id="d9649-123">2. 将3D 打印机连接到设备</span><span class="sxs-lookup"><span data-stu-id="d9649-123">2. Connect your 3D Printer to your device</span></span>
___
* <span data-ttu-id="d9649-124">使用 USB 电缆将3D 打印机插入到 Windows 10 IoT 核心板。</span><span class="sxs-lookup"><span data-stu-id="d9649-124">Plug-in your 3D printer to your Windows 10 IoT Core board using the USB cable.</span></span>

    ![将3D 打印机连接到设备](../media/3DPrintServer/connect-3d-printer.png)

* <span data-ttu-id="d9649-126">打开 IoT 面板应用并验证设备是否显示在 "**我的设备**" 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="d9649-126">Open the IoT Dashboard app and verify that your device shows up in the **My devices** tab.</span></span>

    ![验证设备是否显示在 IoT 面板中](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a><span data-ttu-id="d9649-128">3. 部署网络3D 打印机应用</span><span class="sxs-lookup"><span data-stu-id="d9649-128">3. Deploy the Network 3D Printer app</span></span>
___
* <span data-ttu-id="d9649-129">在 IoT 面板中，单击 "**试用某些示例**" 部分。</span><span class="sxs-lookup"><span data-stu-id="d9649-129">In IoT Dashboard, click on the **Try some samples** section.</span></span>
* <span data-ttu-id="d9649-130">选择网络3D 打印机示例应用。</span><span class="sxs-lookup"><span data-stu-id="d9649-130">Select the Network 3D Printer sample app.</span></span>

   ![安装3D 网络打印机](../media/3dprintserver/dashboard-samples.png)

* <span data-ttu-id="d9649-132">选择3D 打印机型号，并按 "**部署并运行**" 按钮，将应用部署到 IoT 核心设备。</span><span class="sxs-lookup"><span data-stu-id="d9649-132">Select your 3D Printer model and press the **Deploy and run** button to deploy the app to your IoT Core device.</span></span> 

    ![安装3D 网络打印机](../media/3dprintserver/dashboard-app.png)

    <span data-ttu-id="d9649-134">[Aleph 对象，inc.](https://www.alephobjects.com/)的[LulzBot TAZ 6 映像](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png)是在[CC x SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)下授权的。</span><span class="sxs-lookup"><span data-stu-id="d9649-134">[LulzBot TAZ 6 image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) by [Aleph Objects, Inc.](https://www.alephobjects.com/) is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>
    
    <span data-ttu-id="d9649-135">如果要安装自定义打印机，请从打印机列表中选择 "自定义" 选项。</span><span class="sxs-lookup"><span data-stu-id="d9649-135">If you wish to install a custom printer select the "Custom" option from the list of Printers.</span></span> <span data-ttu-id="d9649-136">自定义三维打印机需要一个名为 PrintDeviceCapabilities 文件的配置 xml，以便正确连接和打印到3d 打印机。</span><span class="sxs-lookup"><span data-stu-id="d9649-136">Custom 3d Printers need a configuration xml called the PrintDeviceCapabilities.xml file to be provided to correctly connect and print to the 3d printer.</span></span> <span data-ttu-id="d9649-137">可在此处找到示例 PrintDeviceCapabilities 文件 https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span><span class="sxs-lookup"><span data-stu-id="d9649-137">A sample PrintDeviceCapabilities.xml file can be found here https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span></span>
   
   <span data-ttu-id="d9649-138">在 xml 文件中所需的最小更改是，用特定于兼容打印机的正确值更新下列部分。</span><span class="sxs-lookup"><span data-stu-id="d9649-138">The minimum changes you need to make in the xml file are to update the following sections with the correct values specific to your compatible printer.</span></span>

<span data-ttu-id="d9649-139">处理三维模型时，这些值指定3d 打印机的打印平台尺寸</span><span class="sxs-lookup"><span data-stu-id="d9649-139">These values specify the print bed dimensions of your 3d printer to the slicer when processing the 3d model</span></span>

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


<span data-ttu-id="d9649-140">Psk3dx：波特率 xml 标记中的值控制与 raspberry pi3 中的3d 打印机通信时要使用的特定波特率。</span><span class="sxs-lookup"><span data-stu-id="d9649-140">The value in the psk3dx:baudrate xml tag controls the specific baud rate to use while communicating with the 3d printer from the raspberry pi3.</span></span> <span data-ttu-id="d9649-141">设置特定于3d 打印机的适当波特率。</span><span class="sxs-lookup"><span data-stu-id="d9649-141">Set the appropriate baud rate specific to your 3d printer.</span></span> 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

<span data-ttu-id="d9649-142">PrintDeviceCapabilities xml 中的其他值用于通知3d 打印驱动程序中的切片器，以便使用您的特定兼容打印机来微调其工作方式。</span><span class="sxs-lookup"><span data-stu-id="d9649-142">The other values in the PrintDeviceCapabilities xml are used to notify the slicer in the 3d print driver to fine tune how it works with your specific compatible printer.</span></span>
<span data-ttu-id="d9649-143">[此处](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings)提供了有关所有这些值的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d9649-143">More information on all these values are provided [here](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).</span></span>

    
    
## <a name="4-add-your-3d-printer"></a><span data-ttu-id="d9649-144">4. 添加3D 打印机</span><span class="sxs-lookup"><span data-stu-id="d9649-144">4. Add your 3D Printer</span></span>
___
* <span data-ttu-id="d9649-145">请切换到 Windows 10 电脑，并 -> **设备**" -> **打印机 & 扫描仪**上的"**设置**"。</span><span class="sxs-lookup"><span data-stu-id="d9649-145">Go to your Windows 10 PC and go to **Settings** -> **Devices** -> **Printers & Scanners**.</span></span>
* <span data-ttu-id="d9649-146">按 "**添加打印机或扫描程序**"。</span><span class="sxs-lookup"><span data-stu-id="d9649-146">Press **Add a printer or scanner**.</span></span>

     ![Windows 设置添加设备](../media/3dprintserver/add-printer.png)

* <span data-ttu-id="d9649-148">选择3D 打印机并按 "**添加设备**"。</span><span class="sxs-lookup"><span data-stu-id="d9649-148">Select your 3D Printer and press **Add device**.</span></span> <span data-ttu-id="d9649-149">打印机将自动安装。</span><span class="sxs-lookup"><span data-stu-id="d9649-149">The printer will install automatically.</span></span>

     ![Windows 设置添加设备](../media/3dprintserver/add-device.png)

<span data-ttu-id="d9649-151">恭喜，现在已安装打印机，其行为与使用 USB 电缆连接时的行为完全相同。</span><span class="sxs-lookup"><span data-stu-id="d9649-151">Congratulations your printer is now installed and will behave exactly as if it was connected with a USB cable.</span></span>
<span data-ttu-id="d9649-152">现在可以使用[三维生成器](https://msdn.microsoft.com/windows/hardware/mt561568.aspx)打印到它。</span><span class="sxs-lookup"><span data-stu-id="d9649-152">You can now print to it using [3D Builder](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).</span></span>
