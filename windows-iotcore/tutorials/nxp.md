---
title: 设置 NXP 设备
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解如何通过 Windows 10 IoT 核心版来设置 NXP 设备。
keywords: Windows 10 IoT 核心版, NXP
ms.custom: RS5
ms.openlocfilehash: 58bed6c49a5a05afe0852572051132f8731dfcb1
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "66182169"
---
# <a name="setting-up-a-nxp-device"></a><span data-ttu-id="af5c4-104">设置 NXP 设备</span><span class="sxs-lookup"><span data-stu-id="af5c4-104">Setting up a NXP device</span></span>

## <a name="overview"></a><span data-ttu-id="af5c4-105">概述</span><span class="sxs-lookup"><span data-stu-id="af5c4-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af5c4-106">出现“格式化此磁盘”弹出窗口时，请勿格式化磁盘。 </span><span class="sxs-lookup"><span data-stu-id="af5c4-106">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="af5c4-107">我们正在修复此问题。</span><span class="sxs-lookup"><span data-stu-id="af5c4-107">We are working on a fix for this issue.</span></span>

<span data-ttu-id="af5c4-108">设置进行原型制作的 NXP 设备时，建议使用 Windows 10 IoT 核心版仪表板。</span><span class="sxs-lookup"><span data-stu-id="af5c4-108">When setting up a NXP device for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="af5c4-109">但是，若要使用 NXP 设备进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="af5c4-109">However, if you're looking to manufacture with a NXP device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="af5c4-110">不能将创客映像用于制作。</span><span class="sxs-lookup"><span data-stu-id="af5c4-110">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="af5c4-111">使用仪表板</span><span class="sxs-lookup"><span data-stu-id="af5c4-111">Using the Dashboard</span></span>

<span data-ttu-id="af5c4-112">若要将 IoT 核心版刷写或下载到 NXP 设备，需要以下项：</span><span class="sxs-lookup"><span data-stu-id="af5c4-112">To flash, or download, IoT Core onto your NXP device, you'll need:</span></span>
* <span data-ttu-id="af5c4-113">运行 Windows 10 的计算机</span><span class="sxs-lookup"><span data-stu-id="af5c4-113">A computer running Windows 10</span></span> 
* [<span data-ttu-id="af5c4-114">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="af5c4-114">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="af5c4-115">高性能 SD 卡，例如 SanDisk SD 卡</span><span class="sxs-lookup"><span data-stu-id="af5c4-115">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="af5c4-116">外部显示器</span><span class="sxs-lookup"><span data-stu-id="af5c4-116">An external display</span></span>
* <span data-ttu-id="af5c4-117">任何其他外设（例如鼠标、键盘等）</span><span class="sxs-lookup"><span data-stu-id="af5c4-117">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="af5c4-118">说明</span><span class="sxs-lookup"><span data-stu-id="af5c4-118">Instructions</span></span>

1. <span data-ttu-id="af5c4-119">运行 Windows 10 IOT 核心版仪表板，单击“设置新设备”，然后将 SD 卡插入计算机中。 </span><span class="sxs-lookup"><span data-stu-id="af5c4-119">Run the Windows 10 IOT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="af5c4-120">将 NXP 设备连接到外部显示器。</span><span class="sxs-lookup"><span data-stu-id="af5c4-120">Hook up your NXP device to an external display.</span></span>
3. <span data-ttu-id="af5c4-121">填写字段。</span><span class="sxs-lookup"><span data-stu-id="af5c4-121">Fill out the fields.</span></span> <span data-ttu-id="af5c4-122">选择“NXP [i.MX6/i.MX7]”作为设备类型。</span><span class="sxs-lookup"><span data-stu-id="af5c4-122">Select "NXP [i.MX6/i.MX7]" as the device type.</span></span> <span data-ttu-id="af5c4-123">确保为设备提供新的名称和密码。</span><span class="sxs-lookup"><span data-stu-id="af5c4-123">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="af5c4-124">否则，默认凭据仍旧为：</span><span class="sxs-lookup"><span data-stu-id="af5c4-124">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="af5c4-125">使用“浏览”功能上传预先下载的映像文件。</span><span class="sxs-lookup"><span data-stu-id="af5c4-125">Upload your pre-downloaded image file using the "Browse" function.</span></span> <span data-ttu-id="af5c4-126">有关详细信息，请参阅 [NXP 文档](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp)。</span><span class="sxs-lookup"><span data-stu-id="af5c4-126">For more information, see our [NXP documentation](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp).</span></span>
5. <span data-ttu-id="af5c4-127">接受软件许可条款，然后单击“下载并安装”  。</span><span class="sxs-lookup"><span data-stu-id="af5c4-127">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="af5c4-128">如果一切正常，则可以看到 Windows 10 IoT 核心版此时正刷写 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="af5c4-128">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![仪表板屏幕截图](../media/DeviceSetup/Dashboard-Screenshot.jpg)


## <a name="connect-to-a-network"></a><span data-ttu-id="af5c4-130">连接到网络</span><span class="sxs-lookup"><span data-stu-id="af5c4-130">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="af5c4-131">有线连接</span><span class="sxs-lookup"><span data-stu-id="af5c4-131">Wired connection</span></span>
<span data-ttu-id="af5c4-132">如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。</span><span class="sxs-lookup"><span data-stu-id="af5c4-132">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="af5c4-133">无线连接</span><span class="sxs-lookup"><span data-stu-id="af5c4-133">Wireless connection</span></span>
<span data-ttu-id="af5c4-134">如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="af5c4-134">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="af5c4-135">进入默认应用程序，单击时钟旁边的设置按钮。</span><span class="sxs-lookup"><span data-stu-id="af5c4-135">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="af5c4-136">在设置页上，选择“网络和 Wi-Fi”。 </span><span class="sxs-lookup"><span data-stu-id="af5c4-136">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="af5c4-137">设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="af5c4-137">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="af5c4-138">你的网络显示在此列表中以后，将其选中，然后单击“连接”。 </span><span class="sxs-lookup"><span data-stu-id="af5c4-138">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="af5c4-139">如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="af5c4-139">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="af5c4-140">转到 IoT 仪表板，单击“我的设备”。 </span><span class="sxs-lookup"><span data-stu-id="af5c4-140">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="af5c4-141">从列表中找到你的未配置的板。</span><span class="sxs-lookup"><span data-stu-id="af5c4-141">Find your unconfigured board from the list.</span></span> <span data-ttu-id="af5c4-142">其名称会以“AJ_”开头（例如 AJ_58EA6C68）。</span><span class="sxs-lookup"><span data-stu-id="af5c4-142">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="af5c4-143">如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。</span><span class="sxs-lookup"><span data-stu-id="af5c4-143">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="af5c4-144">单击“配置设备”，然后输入网络凭据。 </span><span class="sxs-lookup"><span data-stu-id="af5c4-144">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="af5c4-145">这样就会将板连接到网络。</span><span class="sxs-lookup"><span data-stu-id="af5c4-145">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="af5c4-146">需启用计算机上的 Wi-Fi 才能找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="af5c4-146">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="af5c4-147">连接到 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="af5c4-147">Connect to Windows Device Portal</span></span>

<span data-ttu-id="af5c4-148">使用 [Windows 设备门户](../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。</span><span class="sxs-lookup"><span data-stu-id="af5c4-148">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="af5c4-149">设备门户提供重要的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="af5c4-149">The device portal makes valuable configuration and device management capabilities available.</span></span> 

