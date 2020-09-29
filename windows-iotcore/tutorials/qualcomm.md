---
title: 设置 Qualcomm 设备
ms.date: 05/22/2019
ms.topic: article
description: 了解如何通过 Windows 10 IoT 核心版来设置 Qualcomm 设备。
keywords: Windows 10 IoT 核心版, Qualcomm
ms.custom: RS5
ms.openlocfilehash: 15e72c6c094aa4f6b34c4bd9c6eb078fae4b5d07
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90781729"
---
# <a name="setting-up-a-qualcomm-device"></a><span data-ttu-id="37f51-104">设置 Qualcomm 设备</span><span class="sxs-lookup"><span data-stu-id="37f51-104">Setting up a Qualcomm device</span></span>

<span data-ttu-id="37f51-105">若要使用 Qualcomm 设备进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="37f51-105">If you're looking to manufacture with a Qualcomm device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="37f51-106">不能将创客映像用于制作。</span><span class="sxs-lookup"><span data-stu-id="37f51-106">You cannot use maker images for manufacturing.</span></span>

> [!NOTE]
> <span data-ttu-id="37f51-107">确保设备现在是从 eMMC 内存启动，方法是：再次进入 BIOS 设置，切换驱动器启动顺序，使之从硬盘驱动器加载，而不是从 USB 盘加载。</span><span class="sxs-lookup"><span data-stu-id="37f51-107">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>

## <a name="using-emmc"></a><span data-ttu-id="37f51-108">使用 eMMC</span><span class="sxs-lookup"><span data-stu-id="37f51-108">Using eMMC</span></span>

1. <span data-ttu-id="37f51-109">为 [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 或 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 计算机下载并安装 DragonBoard Update Tool。</span><span class="sxs-lookup"><span data-stu-id="37f51-109">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="37f51-110">下载 [Windows 10 IoT 核心版 DragonBoard FFU](https://docs.microsoft.com/windows/iot-core/downloads)。</span><span class="sxs-lookup"><span data-stu-id="37f51-110">Download the [Windows 10 IoT Core DragonBoard FFU](https://docs.microsoft.com/windows/iot-core/downloads).</span></span>
3. <span data-ttu-id="37f51-111">双击下载的 ISO 文件，找到装载的虚拟 CD 驱动器。</span><span class="sxs-lookup"><span data-stu-id="37f51-111">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="37f51-112">此驱动器将包含一个安装程序文件 (.msi)；双击它。</span><span class="sxs-lookup"><span data-stu-id="37f51-112">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="37f51-113">这样会在电脑中的 `C:\Program Files (x86)\Microsoft IoT\FFU\` 下创建一个新目录，其中可以看到映像文件“flash.ffu”。</span><span class="sxs-lookup"><span data-stu-id="37f51-113">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="37f51-114">确保 DragonBoard 处于下载模式，方法是将板上的第一个启动开关设置为“USB 启动”，如下所示。</span><span class="sxs-lookup"><span data-stu-id="37f51-114">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="37f51-115">接着通过 microUSB 电缆将 DragonBoard 连接到主机，然后将 DragonBoard 连接到 12V (> 1A) 电源。</span><span class="sxs-lookup"><span data-stu-id="37f51-115">Then, connect the DragonBoard to the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="37f51-116">启动 DragonBoard Update Tool，该工具会通过一个绿色圆圈来表示已检测到 DragonBoard 连接到电脑。</span><span class="sxs-lookup"><span data-stu-id="37f51-116">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connected to your PC with a green circle.</span></span> <span data-ttu-id="37f51-117">“浏览”到 DragonBoard 的已下载 FFU，然后单击“程序”按钮。 </span><span class="sxs-lookup"><span data-stu-id="37f51-117">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="37f51-118">再次单击“浏览”，选择在步骤 5 创建的“rawprogram0.xml”。</span><span class="sxs-lookup"><span data-stu-id="37f51-118">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="37f51-119">然后单击“程序”按钮。</span><span class="sxs-lookup"><span data-stu-id="37f51-119">Then click the "Program" button.</span></span>
7. <span data-ttu-id="37f51-120">下载完以后，请断开板的电源和 microUSB 电缆连接，将 USB 启动开关切换回到“关”的位置。 </span><span class="sxs-lookup"><span data-stu-id="37f51-120">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="37f51-121">将 HDMI 显示器、鼠标和键盘连接到 DragonBoard，然后重新连接电源。</span><span class="sxs-lookup"><span data-stu-id="37f51-121">Connect an HDMI display, a mouse, and a keyboard to the DragonBoard and reconnect the power supply.</span></span> <span data-ttu-id="37f51-122">数分钟后，应该会看到 Windows 10 IoT 核心版默认应用程序。</span><span class="sxs-lookup"><span data-stu-id="37f51-122">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![处于下载模式的 DragonBoard](../media/DeviceSetup/db1.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="37f51-124">连接到网络</span><span class="sxs-lookup"><span data-stu-id="37f51-124">Connect to a network</span></span>

### <a name="wired-connection"></a><span data-ttu-id="37f51-125">有线连接</span><span class="sxs-lookup"><span data-stu-id="37f51-125">Wired connection</span></span>
<span data-ttu-id="37f51-126">如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。</span><span class="sxs-lookup"><span data-stu-id="37f51-126">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="37f51-127">无线连接</span><span class="sxs-lookup"><span data-stu-id="37f51-127">Wireless connection</span></span>
<span data-ttu-id="37f51-128">如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="37f51-128">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="37f51-129">进入默认应用程序，单击时钟旁边的设置按钮。</span><span class="sxs-lookup"><span data-stu-id="37f51-129">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="37f51-130">在设置页上，选择“网络和 Wi-Fi”。 </span><span class="sxs-lookup"><span data-stu-id="37f51-130">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="37f51-131">设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="37f51-131">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="37f51-132">你的网络显示在此列表中以后，将其选中，然后单击“连接”。 </span><span class="sxs-lookup"><span data-stu-id="37f51-132">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="37f51-133">如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="37f51-133">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="37f51-134">转到 IoT 仪表板，单击“我的设备”。 </span><span class="sxs-lookup"><span data-stu-id="37f51-134">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="37f51-135">从列表中找到你的未配置的板。</span><span class="sxs-lookup"><span data-stu-id="37f51-135">Find your unconfigured board from the list.</span></span> <span data-ttu-id="37f51-136">其名称会以“AJ_”开头（例如 AJ_58EA6C68）。</span><span class="sxs-lookup"><span data-stu-id="37f51-136">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="37f51-137">如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。</span><span class="sxs-lookup"><span data-stu-id="37f51-137">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="37f51-138">单击“配置设备”，然后输入网络凭据。 </span><span class="sxs-lookup"><span data-stu-id="37f51-138">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="37f51-139">这样就会将板连接到网络。</span><span class="sxs-lookup"><span data-stu-id="37f51-139">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="37f51-140">需启用计算机上的 Wi-Fi 才能找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="37f51-140">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="37f51-141">连接到 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="37f51-141">Connect to Windows Device Portal</span></span>

<span data-ttu-id="37f51-142">使用 [Windows 设备门户](../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。</span><span class="sxs-lookup"><span data-stu-id="37f51-142">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="37f51-143">设备门户提供重要的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="37f51-143">The device portal makes valuable configuration and device management capabilities available.</span></span> 



