---
title: 设置 Minnowboard
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解如何通过 Windows 10 IoT 核心版来设置 Minnowboard。
keywords: Windows 10 IoT 核心版, Minnowboard
ms.custom: RS5
ms.openlocfilehash: a8840272e0933ee4255661605a04441d542887f3
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "66182209"
---
# <a name="setting-up-a-minnowboard"></a><span data-ttu-id="a3f74-104">设置 MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="a3f74-104">Setting up a MinnowBoard</span></span>

## <a name="overview"></a><span data-ttu-id="a3f74-105">概述</span><span class="sxs-lookup"><span data-stu-id="a3f74-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3f74-106">MinnowBoard Turbot 的最新 64 位固件可以在 [MinnowBoard 网站](https://minnowboard.org/tutorials/updating-the-firmware)上找到（跳过 MinnowBoard 站点的说明中的步骤 4）。</span><span class="sxs-lookup"><span data-stu-id="a3f74-106">The latest 64-bit firmware for MinnowBoard Turbot can be found on the [MinnowBoard website](https://minnowboard.org/tutorials/updating-the-firmware) (skip step 4 on the MinnowBoard site's instructions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3f74-107">出现“格式化此磁盘”弹出窗口时，请勿格式化磁盘。 </span><span class="sxs-lookup"><span data-stu-id="a3f74-107">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="a3f74-108">我们正在修复此问题。</span><span class="sxs-lookup"><span data-stu-id="a3f74-108">We are working on a fix for this issue.</span></span>

<span data-ttu-id="a3f74-109">设置进行原型制作的 MinnowBoard 时，建议使用 Windows 10 IoT 核心版仪表板。</span><span class="sxs-lookup"><span data-stu-id="a3f74-109">When setting up a MinnowBoard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="a3f74-110">但是，若要使用 MinnowBoard 进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="a3f74-110">However, if you're looking to manufacture with a MinnowBoard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="a3f74-111">不能将创客映像用于制作。</span><span class="sxs-lookup"><span data-stu-id="a3f74-111">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="a3f74-112">使用仪表板</span><span class="sxs-lookup"><span data-stu-id="a3f74-112">Using the Dashboard</span></span>

<span data-ttu-id="a3f74-113">若要将 IoT 核心版刷写或下载到 MinnowBoard，需要以下项：</span><span class="sxs-lookup"><span data-stu-id="a3f74-113">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="a3f74-114">运行 Windows 10 的计算机</span><span class="sxs-lookup"><span data-stu-id="a3f74-114">A computer running Windows 10</span></span> 
* [<span data-ttu-id="a3f74-115">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="a3f74-115">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="a3f74-116">高性能 SD 卡，例如 SanDisk SD 卡</span><span class="sxs-lookup"><span data-stu-id="a3f74-116">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="a3f74-117">外部显示器</span><span class="sxs-lookup"><span data-stu-id="a3f74-117">An external display</span></span>
* <span data-ttu-id="a3f74-118">任何其他外设（例如鼠标、键盘等）</span><span class="sxs-lookup"><span data-stu-id="a3f74-118">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="a3f74-119">说明</span><span class="sxs-lookup"><span data-stu-id="a3f74-119">Instructions</span></span>

1. <span data-ttu-id="a3f74-120">运行 Windows 10 IoT 核心版仪表板，单击“设置新设备”，然后将 SD 卡插入计算机中。 </span><span class="sxs-lookup"><span data-stu-id="a3f74-120">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="a3f74-121">将 MinnowBoard 连接到外部显示器。</span><span class="sxs-lookup"><span data-stu-id="a3f74-121">Hook up your MinnowBoard to an external display.</span></span>
3. <span data-ttu-id="a3f74-122">填写字段。</span><span class="sxs-lookup"><span data-stu-id="a3f74-122">Fill out the fields.</span></span> <span data-ttu-id="a3f74-123">选择“Intel [MinnowBoard Turbox/MAX (x64)]”作为设备类型。</span><span class="sxs-lookup"><span data-stu-id="a3f74-123">Select "Intel [MinnowBoard Turbox/MAX (x64)]" as the device type.</span></span> <span data-ttu-id="a3f74-124">确保为设备提供新的名称和密码。</span><span class="sxs-lookup"><span data-stu-id="a3f74-124">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="a3f74-125">否则，默认凭据仍旧为：</span><span class="sxs-lookup"><span data-stu-id="a3f74-125">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="a3f74-126">接受软件许可条款，然后单击“下载并安装”  。</span><span class="sxs-lookup"><span data-stu-id="a3f74-126">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="a3f74-127">如果一切正常，则可以看到 Windows 10 IoT 核心版此时正刷写 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="a3f74-127">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![仪表板屏幕截图](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="a3f74-129">连接到网络</span><span class="sxs-lookup"><span data-stu-id="a3f74-129">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="a3f74-130">有线连接</span><span class="sxs-lookup"><span data-stu-id="a3f74-130">Wired connection</span></span>
<span data-ttu-id="a3f74-131">如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。</span><span class="sxs-lookup"><span data-stu-id="a3f74-131">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="a3f74-132">无线连接</span><span class="sxs-lookup"><span data-stu-id="a3f74-132">Wireless connection</span></span>
<span data-ttu-id="a3f74-133">如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a3f74-133">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="a3f74-134">进入默认应用程序，单击时钟旁边的设置按钮。</span><span class="sxs-lookup"><span data-stu-id="a3f74-134">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="a3f74-135">在设置页上，选择“网络和 Wi-Fi”。 </span><span class="sxs-lookup"><span data-stu-id="a3f74-135">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="a3f74-136">设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="a3f74-136">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="a3f74-137">你的网络显示在此列表中以后，将其选中，然后单击“连接”。 </span><span class="sxs-lookup"><span data-stu-id="a3f74-137">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="a3f74-138">如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a3f74-138">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="a3f74-139">转到 IoT 仪表板，单击“我的设备”。 </span><span class="sxs-lookup"><span data-stu-id="a3f74-139">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="a3f74-140">从列表中找到你的未配置的板。</span><span class="sxs-lookup"><span data-stu-id="a3f74-140">Find your unconfigured board from the list.</span></span> <span data-ttu-id="a3f74-141">其名称会以“AJ_”开头（例如 AJ_58EA6C68）。</span><span class="sxs-lookup"><span data-stu-id="a3f74-141">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="a3f74-142">如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。</span><span class="sxs-lookup"><span data-stu-id="a3f74-142">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="a3f74-143">单击“配置设备”，然后输入网络凭据。 </span><span class="sxs-lookup"><span data-stu-id="a3f74-143">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="a3f74-144">这样就会将板连接到网络。</span><span class="sxs-lookup"><span data-stu-id="a3f74-144">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="a3f74-145">需启用计算机上的 Wi-Fi 才能找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="a3f74-145">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="a3f74-146">连接到 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="a3f74-146">Connect to Windows Device Portal</span></span>

<span data-ttu-id="a3f74-147">使用 [Windows 设备门户](../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。</span><span class="sxs-lookup"><span data-stu-id="a3f74-147">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="a3f74-148">设备门户提供重要的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="a3f74-148">The device portal makes valuable configuration and device management capabilities available.</span></span> 
