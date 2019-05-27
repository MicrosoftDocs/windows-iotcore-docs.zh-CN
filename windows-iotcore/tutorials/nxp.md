---
title: 设置 NXP 设备
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解有关如何设置使用 Windows 10 IoT Core NXP 设备。
keywords: Windows 10 IoT Core NXP
ms.custom: RS5
ms.openlocfilehash: 58bed6c49a5a05afe0852572051132f8731dfcb1
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182169"
---
# <a name="setting-up-a-nxp-device"></a><span data-ttu-id="43338-104">设置 NXP 设备</span><span class="sxs-lookup"><span data-stu-id="43338-104">Setting up a NXP device</span></span>

## <a name="overview"></a><span data-ttu-id="43338-105">概述</span><span class="sxs-lookup"><span data-stu-id="43338-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43338-106">当"格式化此磁盘"弹出最多启动后，请执行_不_格式化该磁盘。</span><span class="sxs-lookup"><span data-stu-id="43338-106">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="43338-107">我们正在努力修复此问题。</span><span class="sxs-lookup"><span data-stu-id="43338-107">We are working on a fix for this issue.</span></span>

<span data-ttu-id="43338-108">当设置 NXP 设备用于原型制作，我们建议使用 Windows 10 IoT Core 仪表板。</span><span class="sxs-lookup"><span data-stu-id="43338-108">When setting up a NXP device for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="43338-109">但是，如果您希望通过 NXP 设备制造，请参阅[IoT Core 交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="43338-109">However, if you're looking to manufacture with a NXP device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="43338-110">创建者映像不能用于生产。</span><span class="sxs-lookup"><span data-stu-id="43338-110">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="43338-111">使用仪表板</span><span class="sxs-lookup"><span data-stu-id="43338-111">Using the Dashboard</span></span>

<span data-ttu-id="43338-112">Flash，或下载，IoT 核心版到 NXP 设备，你将需要：</span><span class="sxs-lookup"><span data-stu-id="43338-112">To flash, or download, IoT Core onto your NXP device, you'll need:</span></span>
* <span data-ttu-id="43338-113">运行 Windows 10 的计算机</span><span class="sxs-lookup"><span data-stu-id="43338-113">A computer running Windows 10</span></span> 
* [<span data-ttu-id="43338-114">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="43338-114">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="43338-115">高性能 SD 卡，如 SanDisk SD 卡</span><span class="sxs-lookup"><span data-stu-id="43338-115">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="43338-116">外部显示器</span><span class="sxs-lookup"><span data-stu-id="43338-116">An external display</span></span>
* <span data-ttu-id="43338-117">任何其他外围设备 （例如鼠标、 键盘等）</span><span class="sxs-lookup"><span data-stu-id="43338-117">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="43338-118">说明</span><span class="sxs-lookup"><span data-stu-id="43338-118">Instructions</span></span>

1. <span data-ttu-id="43338-119">运行 Windows 10 IOT Core 仪表板，然后单击*设置新设备*和 SD 卡插入到计算机。</span><span class="sxs-lookup"><span data-stu-id="43338-119">Run the Windows 10 IOT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="43338-120">挂接到外部显示器 NXP 设备。</span><span class="sxs-lookup"><span data-stu-id="43338-120">Hook up your NXP device to an external display.</span></span>
3. <span data-ttu-id="43338-121">填写字段。</span><span class="sxs-lookup"><span data-stu-id="43338-121">Fill out the fields.</span></span> <span data-ttu-id="43338-122">选择"NXP [i.MX6/i.MX7]"作为设备类型。</span><span class="sxs-lookup"><span data-stu-id="43338-122">Select "NXP [i.MX6/i.MX7]" as the device type.</span></span> <span data-ttu-id="43338-123">请确保为你的设备提供新名称和密码。</span><span class="sxs-lookup"><span data-stu-id="43338-123">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="43338-124">否则默认凭据将保持为：</span><span class="sxs-lookup"><span data-stu-id="43338-124">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="43338-125">上传您使用"浏览"函数的预下载的图像文件。</span><span class="sxs-lookup"><span data-stu-id="43338-125">Upload your pre-downloaded image file using the "Browse" function.</span></span> <span data-ttu-id="43338-126">有关详细信息，请参阅我们[NXP 文档](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp)。</span><span class="sxs-lookup"><span data-stu-id="43338-126">For more information, see our [NXP documentation](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp).</span></span>
5. <span data-ttu-id="43338-127">接受软件许可条款，然后单击*下载并安装*。</span><span class="sxs-lookup"><span data-stu-id="43338-127">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="43338-128">如果一切顺利，您将看到 Windows 10 IoT Core 现在闪 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="43338-128">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![仪表板的屏幕截图](../media/DeviceSetup/Dashboard-Screenshot.jpg)


## <a name="connect-to-a-network"></a><span data-ttu-id="43338-130">连接到网络</span><span class="sxs-lookup"><span data-stu-id="43338-130">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="43338-131">有线的连接</span><span class="sxs-lookup"><span data-stu-id="43338-131">Wired connection</span></span>
<span data-ttu-id="43338-132">如果你的设备附带的以太网端口或 USB 以太网适配器支持，使您的有线的连接，将附加以太网电缆连接到你的网络。</span><span class="sxs-lookup"><span data-stu-id="43338-132">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="43338-133">无线连接</span><span class="sxs-lookup"><span data-stu-id="43338-133">Wireless connection</span></span>
<span data-ttu-id="43338-134">如果你的设备支持的 Wi-fi 连接，并且你已连接到它的显示，你将需要：</span><span class="sxs-lookup"><span data-stu-id="43338-134">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="43338-135">转到默认应用程序并单击设置按钮旁边的时钟。</span><span class="sxs-lookup"><span data-stu-id="43338-135">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="43338-136">在设置页上选择_网络和 Wi-fi_。</span><span class="sxs-lookup"><span data-stu-id="43338-136">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="43338-137">你的设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="43338-137">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="43338-138">一旦你的网络会显示此列表中，选择它，然后单击_Connect_。</span><span class="sxs-lookup"><span data-stu-id="43338-138">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="43338-139">如果尚未连接显示，并且想要通过 Wi-fi 连接，你将需要：</span><span class="sxs-lookup"><span data-stu-id="43338-139">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="43338-140">转到 IoT 仪表板，并单击_我的设备_。</span><span class="sxs-lookup"><span data-stu-id="43338-140">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="43338-141">查找从列表中未配置开发板。</span><span class="sxs-lookup"><span data-stu-id="43338-141">Find your unconfigured board from the list.</span></span> <span data-ttu-id="43338-142">其名称开头"AJ_"...(例如 AJ_58EA6C68)。</span><span class="sxs-lookup"><span data-stu-id="43338-142">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="43338-143">如果看不到开发板出现几分钟后，请尝试重新启动你的板。</span><span class="sxs-lookup"><span data-stu-id="43338-143">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="43338-144">单击_配置设备_并输入你的网络凭据。</span><span class="sxs-lookup"><span data-stu-id="43338-144">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="43338-145">这将连接到网络的开发板。</span><span class="sxs-lookup"><span data-stu-id="43338-145">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="43338-146">您的计算机上的 Wifi 将需要打开以便找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="43338-146">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="43338-147">连接到 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="43338-147">Connect to Windows Device Portal</span></span>

<span data-ttu-id="43338-148">使用[Windows Device Portal](../manage-your-device/DevicePortal.md)通过 web 浏览器连接你的设备。</span><span class="sxs-lookup"><span data-stu-id="43338-148">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="43338-149">设备门户提供有价值的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="43338-149">The device portal makes valuable configuration and device management capabilities available.</span></span> 

