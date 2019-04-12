---
title: 使用 Windows 10 IoT Core 网络 3D 打印机
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: 了解有关如何将 Windows 10 IoT Core 设备转换为打印服务器和 3D 打印机连接到它。
keywords: windows iot、 3D、 3D 打印机、 打印服务器、 网络 3D 打印机
ms.openlocfilehash: 7a9bcc7871c62be5a73319ca284127ee4abc42f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510637"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a><span data-ttu-id="cc22b-104">使用 Windows 10 IoT Core 网络 3D 打印机</span><span class="sxs-lookup"><span data-stu-id="cc22b-104">Network 3D Printer with Windows 10 IoT Core</span></span>

<span data-ttu-id="cc22b-105">将变成打印服务器的 Windows 10 IoT Core 设备并连接到它的 3D 打印机。</span><span class="sxs-lookup"><span data-stu-id="cc22b-105">Turn your Windows 10 IoT Core device into a print server and connect your 3D Printer to it.</span></span> <span data-ttu-id="cc22b-106">你将能够从其他设备以无线方式访问您的打印机。</span><span class="sxs-lookup"><span data-stu-id="cc22b-106">You will be able to access your printer wirelessly from other devices.</span></span>

## <a name="1-install-windows-10-iot-core-on-your-device"></a><span data-ttu-id="cc22b-107">1.在设备上安装 Windows 10 IoT 核心版</span><span class="sxs-lookup"><span data-stu-id="cc22b-107">1. Install Windows 10 IoT Core on your device</span></span>
___
<span data-ttu-id="cc22b-108">在开始之前，你将需要：</span><span class="sxs-lookup"><span data-stu-id="cc22b-108">Before you start, you will need:</span></span>

* <span data-ttu-id="cc22b-109">Windows 10 IoT Core Insider Preview 安装为最新版本看板。</span><span class="sxs-lookup"><span data-stu-id="cc22b-109">A board with the latest version of Windows 10 IoT Core Insider Preview installed.</span></span> <span data-ttu-id="cc22b-110">请按照[入门指南](https://developer.microsoft.com/en-us/windows/iot/getstarted)获取 IoT 仪表板应用程序并安装 Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="cc22b-110">Follow the [Get Started guide](https://developer.microsoft.com/en-us/windows/iot/getstarted) to get the IoT Dashboard app and install Windows 10 IoT Core.</span></span>
* <span data-ttu-id="cc22b-111">3D 打印机与我们的网络 3D 打印机应用程序兼容：</span><span class="sxs-lookup"><span data-stu-id="cc22b-111">A 3D Printer compatible with our Network 3D Printer app:</span></span>

    * <span data-ttu-id="cc22b-112">Lulzbot Taz 6</span><span class="sxs-lookup"><span data-stu-id="cc22b-112">Lulzbot Taz 6</span></span>
    * <span data-ttu-id="cc22b-113">Makergear M2</span><span class="sxs-lookup"><span data-stu-id="cc22b-113">Makergear M2</span></span>
    * <span data-ttu-id="cc22b-114">Printrbot Play，加上和简单</span><span class="sxs-lookup"><span data-stu-id="cc22b-114">Printrbot Play, Plus and Simple</span></span>
    * <span data-ttu-id="cc22b-115">Prusa i3 Mk2</span><span class="sxs-lookup"><span data-stu-id="cc22b-115">Prusa i3 Mk2</span></span>
    * <span data-ttu-id="cc22b-116">Ultimaker 原始和原始 +</span><span class="sxs-lookup"><span data-stu-id="cc22b-116">Ultimaker Original and Original+</span></span>
    * <span data-ttu-id="cc22b-117">Ultimaker 2，2 +</span><span class="sxs-lookup"><span data-stu-id="cc22b-117">Ultimaker 2 and 2+</span></span>
    * <span data-ttu-id="cc22b-118">Ultimaker 2 扩展和扩展 +</span><span class="sxs-lookup"><span data-stu-id="cc22b-118">Ultimaker 2 Extended and Extended+</span></span>
    * <span data-ttu-id="cc22b-119">CraftBot 2</span><span class="sxs-lookup"><span data-stu-id="cc22b-119">CraftBot 2</span></span>
    * <span data-ttu-id="cc22b-120">CraftBot 加号</span><span class="sxs-lookup"><span data-stu-id="cc22b-120">CraftBot PLUS</span></span>
    * <span data-ttu-id="cc22b-121">LulzBot Mini</span><span class="sxs-lookup"><span data-stu-id="cc22b-121">LulzBot Mini</span></span>
    * <span data-ttu-id="cc22b-122">Velleman K8200</span><span class="sxs-lookup"><span data-stu-id="cc22b-122">Velleman K8200</span></span>

## <a name="2-connect-your-3d-printer-to-your-device"></a><span data-ttu-id="cc22b-123">2.在 3D 打印机连接到你的设备</span><span class="sxs-lookup"><span data-stu-id="cc22b-123">2. Connect your 3D Printer to your device</span></span>
___
* <span data-ttu-id="cc22b-124">插件 3D 打印机在将 Windows 10 IoT 核心板使用 USB 电缆。</span><span class="sxs-lookup"><span data-stu-id="cc22b-124">Plug-in your 3D printer to your Windows 10 IoT Core board using the USB cable.</span></span>

    ![3D 打印机连接到设备](../media/3DPrintServer/connect-3d-printer.png)

* <span data-ttu-id="cc22b-126">打开 IoT 仪表板应用和验证，你的设备显示在**我的设备**选项卡。</span><span class="sxs-lookup"><span data-stu-id="cc22b-126">Open the IoT Dashboard app and verify that your device shows up in the **My devices** tab.</span></span>

    ![验证在 IoT 仪表板中显示你的设备](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a><span data-ttu-id="cc22b-128">3.部署网络 3D 打印机应用程序</span><span class="sxs-lookup"><span data-stu-id="cc22b-128">3. Deploy the Network 3D Printer app</span></span>
___
* <span data-ttu-id="cc22b-129">在 IoT 仪表板中，单击**尝试一些示例**部分。</span><span class="sxs-lookup"><span data-stu-id="cc22b-129">In IoT Dashboard, click on the **Try some samples** section.</span></span>
* <span data-ttu-id="cc22b-130">选择网络 3D 打印机示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="cc22b-130">Select the Network 3D Printer sample app.</span></span>

   ![安装 3D 网络打印机](../media/3dprintserver/dashboard-samples.png)

* <span data-ttu-id="cc22b-132">选择 3D 打印机模型，并按**部署并运行**按钮以将应用部署到 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="cc22b-132">Select your 3D Printer model and press the **Deploy and run** button to deploy the app to your IoT Core device.</span></span> 

    ![安装 3D 网络打印机](../media/3dprintserver/dashboard-app.png)

    <span data-ttu-id="cc22b-134">[LulzBot TAZ 6 映像](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png)由[Aleph 对象，Inc.](https://www.alephobjects.com/)进行许可[CC BY SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)。</span><span class="sxs-lookup"><span data-stu-id="cc22b-134">[LulzBot TAZ 6 image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) by [Aleph Objects, Inc.](https://www.alephobjects.com/) is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>
    
    <span data-ttu-id="cc22b-135">如果你想要自定义打印机选择"自定义"选项安装来自打印机的列表。</span><span class="sxs-lookup"><span data-stu-id="cc22b-135">If you wish to install a custom printer select the "Custom" option from the list of Printers.</span></span> <span data-ttu-id="cc22b-136">自定义 3d 打印机需要调用 PrintDeviceCapabilities.xml 文件以提供以正确地连接和打印到 3d 打印机配置 xml。</span><span class="sxs-lookup"><span data-stu-id="cc22b-136">Custom 3d Printers need a configuration xml called the PrintDeviceCapabilities.xml file to be provided to correctly connect and print to the 3d printer.</span></span> <span data-ttu-id="cc22b-137">示例 PrintDeviceCapabilities.xml 文件可在此处找到 https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span><span class="sxs-lookup"><span data-stu-id="cc22b-137">A sample PrintDeviceCapabilities.xml file can be found here https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span></span>
   
   <span data-ttu-id="cc22b-138">您需要在 xml 文件中进行最小更改，则使用特定于兼容的打印机的正确值更新以下各节。</span><span class="sxs-lookup"><span data-stu-id="cc22b-138">The minimum changes you need to make in the xml file are to update the following sections with the correct values specific to your compatible printer.</span></span>

<span data-ttu-id="cc22b-139">处理三维模型时，这些值指定为切片器在 3d 打印机的打印平台维度</span><span class="sxs-lookup"><span data-stu-id="cc22b-139">These values specify the print bed dimensions of your 3d printer to the slicer when processing the 3d model</span></span>

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


<span data-ttu-id="cc22b-140">Psk3dx:baudrate xml 标记中的值控制从 raspberry pi3 3d 打印机与通信时使用的特定波特率。</span><span class="sxs-lookup"><span data-stu-id="cc22b-140">The value in the psk3dx:baudrate xml tag controls the specific baud rate to use while communicating with the 3d printer from the raspberry pi3.</span></span> <span data-ttu-id="cc22b-141">设置适当的波特率特定于 3d 打印机。</span><span class="sxs-lookup"><span data-stu-id="cc22b-141">Set the appropriate baud rate specific to your 3d printer.</span></span> 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

<span data-ttu-id="cc22b-142">PrintDeviceCapabilities xml 中的其他值用于通知 3d 打印驱动程序中的切片器，以微调隧道与特定的兼容打印机的工作方式。</span><span class="sxs-lookup"><span data-stu-id="cc22b-142">The other values in the PrintDeviceCapabilities xml are used to notify the slicer in the 3d print driver to fine tune how it works with your specific compatible printer.</span></span>
<span data-ttu-id="cc22b-143">所有提供的这些值的详细信息[此处](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings)。</span><span class="sxs-lookup"><span data-stu-id="cc22b-143">More information on all these values are provided [here](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).</span></span>

    
    
## <a name="4-add-your-3d-printer"></a><span data-ttu-id="cc22b-144">4.添加 3D 打印机</span><span class="sxs-lookup"><span data-stu-id="cc22b-144">4. Add your 3D Printer</span></span>
___
* <span data-ttu-id="cc22b-145">转到 Windows 10 电脑，转到**设置** -> **设备** -> **打印机和扫描仪**。</span><span class="sxs-lookup"><span data-stu-id="cc22b-145">Go to your Windows 10 PC and go to **Settings** -> **Devices** -> **Printers & Scanners**.</span></span>
* <span data-ttu-id="cc22b-146">按**添加打印机或扫描仪**。</span><span class="sxs-lookup"><span data-stu-id="cc22b-146">Press **Add a printer or scanner**.</span></span>

     ![Windows 设置添加设备](../media/3dprintserver/add-printer.png)

* <span data-ttu-id="cc22b-148">选择你的 3D 打印机并按**添加设备**。</span><span class="sxs-lookup"><span data-stu-id="cc22b-148">Select your 3D Printer and press **Add device**.</span></span> <span data-ttu-id="cc22b-149">将自动安装打印机。</span><span class="sxs-lookup"><span data-stu-id="cc22b-149">The printer will install automatically.</span></span>

     ![Windows 设置添加设备](../media/3dprintserver/add-device.png)

<span data-ttu-id="cc22b-151">恭喜现已安装打印机和行为就完全像使用 USB 电缆连接。</span><span class="sxs-lookup"><span data-stu-id="cc22b-151">Congratulations your printer is now installed and will behave exactly as if it was connected with a USB cable.</span></span>
<span data-ttu-id="cc22b-152">现在可以使用打印[3D 生成器](https://msdn.microsoft.com/windows/hardware/mt561568.aspx)。</span><span class="sxs-lookup"><span data-stu-id="cc22b-152">You can now print to it using [3D Builder](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).</span></span>
