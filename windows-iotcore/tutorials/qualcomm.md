---
title: Qualcomm 设备设置
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解有关如何设置使用 Windows 10 IoT Core Qualcomm 设备。
keywords: Windows 10 IoT Core Qualcomm
ms.custom: RS5
ms.openlocfilehash: 42ccf65023b2742fc584760d09f679c4f6a5b197
ms.sourcegitcommit: dcaeaa6c5e84dd6a4974a56098f3bab151209e41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66760370"
---
# <a name="setting-up-a-qualcomm-device"></a><span data-ttu-id="34799-104">Qualcomm 设备设置</span><span class="sxs-lookup"><span data-stu-id="34799-104">Setting up a Qualcomm device</span></span>

<span data-ttu-id="34799-105">如果您希望通过 Qualcomm 设备制造，请参阅[IoT Core 交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="34799-105">If you're looking to manufacture with a Qualcomm device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="34799-106">创建者映像不能用于生产。</span><span class="sxs-lookup"><span data-stu-id="34799-106">You cannot use maker images for manufacturing.</span></span>

> [!NOTE]
> <span data-ttu-id="34799-107">请确保设备现已通过重新输入 BIOS 设置，并切换启动驱动器顺序加载从硬盘驱动器而不是从 USB 驱动器启动从 eMMC 内存。</span><span class="sxs-lookup"><span data-stu-id="34799-107">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>

## <a name="using-emmc"></a><span data-ttu-id="34799-108">使用 eMMC</span><span class="sxs-lookup"><span data-stu-id="34799-108">Using eMMC</span></span>

1. <span data-ttu-id="34799-109">下载并安装 DragonBoard 更新工具为你[x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip)或[x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip)机。</span><span class="sxs-lookup"><span data-stu-id="34799-109">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="34799-110">下载[Windows 10 IoT 核心 DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads)。</span><span class="sxs-lookup"><span data-stu-id="34799-110">Download the [Windows 10 IoT Core DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads).</span></span>
3. <span data-ttu-id="34799-111">双击下载的 ISO 文件并找到已装载的虚拟 CD 的驱动器。</span><span class="sxs-lookup"><span data-stu-id="34799-111">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="34799-112">此驱动器将包含的安装程序文件 (.msi);双击该文件。</span><span class="sxs-lookup"><span data-stu-id="34799-112">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="34799-113">这将创建一个新的目录下在电脑上 `C:\Program Files (x86)\Microsoft IoT\FFU\`中应看到图像文件、"flash.ffu"。</span><span class="sxs-lookup"><span data-stu-id="34799-113">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="34799-114">请确保你 DragonBoard 是在下载模式下设置首次启动板上切换到 USB 启动，如下所示。</span><span class="sxs-lookup"><span data-stu-id="34799-114">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="34799-115">然后，连接 DragonBoard 宿主 PC 通过 microUSB 电缆，然后插入到 12V DragonBoard (> 1A) 电源。</span><span class="sxs-lookup"><span data-stu-id="34799-115">Then, connect DragonBoard the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="34799-116">启动 DragonBoard 更新工具，它应检测 DragonBoard 连接到您的 PC 的绿色圆圈。</span><span class="sxs-lookup"><span data-stu-id="34799-116">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connect to your PC with a green circle.</span></span> <span data-ttu-id="34799-117">"浏览"到 DragonBoard FFU 下载，然后单击_程序_按钮。</span><span class="sxs-lookup"><span data-stu-id="34799-117">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="34799-118">再次单击"浏览"，然后选择"rawprogram0.xml"已在步骤 5 中生成。</span><span class="sxs-lookup"><span data-stu-id="34799-118">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="34799-119">然后单击"计划"按钮。</span><span class="sxs-lookup"><span data-stu-id="34799-119">Then click the "Program" button.</span></span>
7. <span data-ttu-id="34799-120">下载完成后，从 USB 启动切换回的看板和切换断开电源供应和 microUSB 线_OFF_。</span><span class="sxs-lookup"><span data-stu-id="34799-120">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="34799-121">连接到 DragonBoard 和 rec onnect 电源 HDMI 显示器、 鼠标和键盘。</span><span class="sxs-lookup"><span data-stu-id="34799-121">Connect a HDMI display, a mouse, and a keyboard to the DragonBoard and rec-onnect the power supply.</span></span> <span data-ttu-id="34799-122">几分钟后，您应该看到 Windows 10 IoT 核心版默认应用程序。</span><span class="sxs-lookup"><span data-stu-id="34799-122">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![在下载模式下的 DragonBoard](../media/DeviceSetup/db1.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="34799-124">连接到网络</span><span class="sxs-lookup"><span data-stu-id="34799-124">Connect to a network</span></span>

### <a name="wired-connection"></a><span data-ttu-id="34799-125">有线的连接</span><span class="sxs-lookup"><span data-stu-id="34799-125">Wired connection</span></span>
<span data-ttu-id="34799-126">如果你的设备附带的以太网端口或 USB 以太网适配器支持，使您的有线的连接，将附加以太网电缆连接到你的网络。</span><span class="sxs-lookup"><span data-stu-id="34799-126">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="34799-127">无线连接</span><span class="sxs-lookup"><span data-stu-id="34799-127">Wireless connection</span></span>
<span data-ttu-id="34799-128">如果你的设备支持的 Wi-fi 连接，并且你已连接到它的显示，你将需要：</span><span class="sxs-lookup"><span data-stu-id="34799-128">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="34799-129">转到默认应用程序并单击设置按钮旁边的时钟。</span><span class="sxs-lookup"><span data-stu-id="34799-129">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="34799-130">在设置页上选择_网络和 Wi-fi_。</span><span class="sxs-lookup"><span data-stu-id="34799-130">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="34799-131">你的设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="34799-131">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="34799-132">一旦你的网络会显示此列表中，选择它，然后单击_Connect_。</span><span class="sxs-lookup"><span data-stu-id="34799-132">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="34799-133">如果尚未连接显示，并且想要通过 Wi-fi 连接，你将需要：</span><span class="sxs-lookup"><span data-stu-id="34799-133">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="34799-134">转到 IoT 仪表板，并单击_我的设备_。</span><span class="sxs-lookup"><span data-stu-id="34799-134">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="34799-135">查找从列表中未配置开发板。</span><span class="sxs-lookup"><span data-stu-id="34799-135">Find your unconfigured board from the list.</span></span> <span data-ttu-id="34799-136">其名称开头"AJ_"...(例如 AJ_58EA6C68)。</span><span class="sxs-lookup"><span data-stu-id="34799-136">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="34799-137">如果看不到开发板出现几分钟后，请尝试重新启动你的板。</span><span class="sxs-lookup"><span data-stu-id="34799-137">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="34799-138">单击_配置设备_并输入你的网络凭据。</span><span class="sxs-lookup"><span data-stu-id="34799-138">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="34799-139">这将连接到网络的开发板。</span><span class="sxs-lookup"><span data-stu-id="34799-139">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="34799-140">您的计算机上的 Wifi 将需要打开以便找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="34799-140">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="34799-141">连接到 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="34799-141">Connect to Windows Device Portal</span></span>

<span data-ttu-id="34799-142">使用[Windows Device Portal](../manage-your-device/DevicePortal.md)通过 web 浏览器连接你的设备。</span><span class="sxs-lookup"><span data-stu-id="34799-142">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="34799-143">设备门户提供有价值的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="34799-143">The device portal makes valuable configuration and device management capabilities available.</span></span> 



