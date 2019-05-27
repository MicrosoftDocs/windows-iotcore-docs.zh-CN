---
title: 设置 Minnowboard
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解如何设置使用 Windows 10 IoT Core 你 Minnowboard。
keywords: Windows 10 IoT Core Minnowboard
ms.custom: RS5
ms.openlocfilehash: a8840272e0933ee4255661605a04441d542887f3
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182209"
---
# <a name="setting-up-a-minnowboard"></a><span data-ttu-id="13512-104">设置 MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="13512-104">Setting up a MinnowBoard</span></span>

## <a name="overview"></a><span data-ttu-id="13512-105">概述</span><span class="sxs-lookup"><span data-stu-id="13512-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="13512-106">可以上找到最新的 64 位固件的 MinnowBoard Turbot [MinnowBoard 网站](https://minnowboard.org/tutorials/updating-the-firmware)（MinnowBoard 站点的说明，跳过第 4 步）。</span><span class="sxs-lookup"><span data-stu-id="13512-106">The latest 64-bit firmware for MinnowBoard Turbot can be found on the [MinnowBoard website](https://minnowboard.org/tutorials/updating-the-firmware) (skip step 4 on the MinnowBoard site's instructions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="13512-107">当"格式化此磁盘"弹出最多启动后，请执行_不_格式化该磁盘。</span><span class="sxs-lookup"><span data-stu-id="13512-107">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="13512-108">我们正在努力修复此问题。</span><span class="sxs-lookup"><span data-stu-id="13512-108">We are working on a fix for this issue.</span></span>

<span data-ttu-id="13512-109">在设置用于原型制作 MinnowBoard，我们建议使用 Windows 10 IoT Core 仪表板。</span><span class="sxs-lookup"><span data-stu-id="13512-109">When setting up a MinnowBoard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="13512-110">但是，如果您希望使用 MinnowBoard 制造，请参阅[IoT Core 交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="13512-110">However, if you're looking to manufacture with a MinnowBoard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="13512-111">创建者映像不能用于生产。</span><span class="sxs-lookup"><span data-stu-id="13512-111">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="13512-112">使用仪表板</span><span class="sxs-lookup"><span data-stu-id="13512-112">Using the Dashboard</span></span>

<span data-ttu-id="13512-113">Flash，或下载，IoT 核心版到你 MinnowBoard，你将需要：</span><span class="sxs-lookup"><span data-stu-id="13512-113">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="13512-114">运行 Windows 10 的计算机</span><span class="sxs-lookup"><span data-stu-id="13512-114">A computer running Windows 10</span></span> 
* [<span data-ttu-id="13512-115">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="13512-115">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="13512-116">高性能 SD 卡，如 SanDisk SD 卡</span><span class="sxs-lookup"><span data-stu-id="13512-116">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="13512-117">外部显示器</span><span class="sxs-lookup"><span data-stu-id="13512-117">An external display</span></span>
* <span data-ttu-id="13512-118">任何其他外围设备 （例如鼠标、 键盘等）</span><span class="sxs-lookup"><span data-stu-id="13512-118">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="13512-119">说明</span><span class="sxs-lookup"><span data-stu-id="13512-119">Instructions</span></span>

1. <span data-ttu-id="13512-120">运行 Windows 10 IoT Core 仪表板，然后单击*设置新设备*和 SD 卡插入到计算机。</span><span class="sxs-lookup"><span data-stu-id="13512-120">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="13512-121">挂接到外部显示器你 MinnowBoard。</span><span class="sxs-lookup"><span data-stu-id="13512-121">Hook up your MinnowBoard to an external display.</span></span>
3. <span data-ttu-id="13512-122">填写字段。</span><span class="sxs-lookup"><span data-stu-id="13512-122">Fill out the fields.</span></span> <span data-ttu-id="13512-123">选择"Intel [MinnowBoard Turbox/最大 (x64)]"作为设备类型。</span><span class="sxs-lookup"><span data-stu-id="13512-123">Select "Intel [MinnowBoard Turbox/MAX (x64)]" as the device type.</span></span> <span data-ttu-id="13512-124">请确保为你的设备提供新名称和密码。</span><span class="sxs-lookup"><span data-stu-id="13512-124">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="13512-125">否则默认凭据将保持为：</span><span class="sxs-lookup"><span data-stu-id="13512-125">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="13512-126">接受软件许可条款，然后单击*下载并安装*。</span><span class="sxs-lookup"><span data-stu-id="13512-126">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="13512-127">如果一切顺利，您将看到 Windows 10 IoT Core 现在闪 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="13512-127">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![仪表板的屏幕截图](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="13512-129">连接到网络</span><span class="sxs-lookup"><span data-stu-id="13512-129">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="13512-130">有线的连接</span><span class="sxs-lookup"><span data-stu-id="13512-130">Wired connection</span></span>
<span data-ttu-id="13512-131">如果你的设备附带的以太网端口或 USB 以太网适配器支持，使您的有线的连接，将附加以太网电缆连接到你的网络。</span><span class="sxs-lookup"><span data-stu-id="13512-131">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="13512-132">无线连接</span><span class="sxs-lookup"><span data-stu-id="13512-132">Wireless connection</span></span>
<span data-ttu-id="13512-133">如果你的设备支持的 Wi-fi 连接，并且你已连接到它的显示，你将需要：</span><span class="sxs-lookup"><span data-stu-id="13512-133">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="13512-134">转到默认应用程序并单击设置按钮旁边的时钟。</span><span class="sxs-lookup"><span data-stu-id="13512-134">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="13512-135">在设置页上选择_网络和 Wi-fi_。</span><span class="sxs-lookup"><span data-stu-id="13512-135">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="13512-136">你的设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="13512-136">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="13512-137">一旦你的网络会显示此列表中，选择它，然后单击_Connect_。</span><span class="sxs-lookup"><span data-stu-id="13512-137">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="13512-138">如果尚未连接显示，并且想要通过 Wi-fi 连接，你将需要：</span><span class="sxs-lookup"><span data-stu-id="13512-138">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="13512-139">转到 IoT 仪表板，并单击_我的设备_。</span><span class="sxs-lookup"><span data-stu-id="13512-139">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="13512-140">查找从列表中未配置开发板。</span><span class="sxs-lookup"><span data-stu-id="13512-140">Find your unconfigured board from the list.</span></span> <span data-ttu-id="13512-141">其名称开头"AJ_"...(例如 AJ_58EA6C68)。</span><span class="sxs-lookup"><span data-stu-id="13512-141">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="13512-142">如果看不到开发板出现几分钟后，请尝试重新启动你的板。</span><span class="sxs-lookup"><span data-stu-id="13512-142">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="13512-143">单击_配置设备_并输入你的网络凭据。</span><span class="sxs-lookup"><span data-stu-id="13512-143">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="13512-144">这将连接到网络的开发板。</span><span class="sxs-lookup"><span data-stu-id="13512-144">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="13512-145">您的计算机上的 Wifi 将需要打开以便找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="13512-145">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="13512-146">连接到 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="13512-146">Connect to Windows Device Portal</span></span>

<span data-ttu-id="13512-147">使用[Windows Device Portal](../manage-your-device/DevicePortal.md)通过 web 浏览器连接你的设备。</span><span class="sxs-lookup"><span data-stu-id="13512-147">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="13512-148">设备门户提供有价值的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="13512-148">The device portal makes valuable configuration and device management capabilities available.</span></span> 
