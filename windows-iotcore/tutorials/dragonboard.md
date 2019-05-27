---
title: 设置 Dragonboard
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解如何设置使用 Windows 10 IoT Core 你 Dragonboard。
keywords: Windows 10 IoT Core Dragonboard
ms.custom: RS5
ms.openlocfilehash: 8e4acc77d902124934e1bdae249f76c7f76306a6
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182269"
---
# <a name="setting-up-a-dragonboard"></a><span data-ttu-id="ee4d9-104">设置 Dragonboard</span><span class="sxs-lookup"><span data-stu-id="ee4d9-104">Setting up a Dragonboard</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee4d9-105">当您正在使用新 Dragonboard 时，它还提供安装 Android。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-105">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="ee4d9-106">需要擦除并加载使用 eMMC 闪烁方法的设备。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-106">You will need to wipe and load the device using the eMMC flashing method.</span></span>

> [!NOTE]
> <span data-ttu-id="ee4d9-107">如果正运行带有你 DragonBoard 到任何音频相关的问题，我们建议你通读 Qualcomm 的手册[此处](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-107">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span> 

<span data-ttu-id="ee4d9-108">在设置用于原型制作 Dragonboard，我们建议使用 Windows 10 IoT Core 仪表板。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-108">When setting up a Dragonboard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="ee4d9-109">但是，如果您希望与 Dragonboard 制造，请参阅[IoT Core 交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-109">However, if you're looking to manufacture with a Dragonboard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="ee4d9-110">创建者映像不能用于生产。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-110">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a><span data-ttu-id="ee4d9-111">使用仪表板</span><span class="sxs-lookup"><span data-stu-id="ee4d9-111">Using the Dashboard</span></span>

<span data-ttu-id="ee4d9-112">Flash，或下载，IoT 核心版到你 MinnowBoard，你将需要：</span><span class="sxs-lookup"><span data-stu-id="ee4d9-112">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="ee4d9-113">运行 Windows 10 的计算机</span><span class="sxs-lookup"><span data-stu-id="ee4d9-113">A computer running Windows 10</span></span> 
* [<span data-ttu-id="ee4d9-114">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="ee4d9-114">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="ee4d9-115">MicroUSB 电缆</span><span class="sxs-lookup"><span data-stu-id="ee4d9-115">MicroUSB cable</span></span>
* <span data-ttu-id="ee4d9-116">外部显示器</span><span class="sxs-lookup"><span data-stu-id="ee4d9-116">An external display</span></span>
* <span data-ttu-id="ee4d9-117">任何其他外围设备 （例如鼠标、 键盘等）</span><span class="sxs-lookup"><span data-stu-id="ee4d9-117">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="ee4d9-118">说明</span><span class="sxs-lookup"><span data-stu-id="ee4d9-118">Instructions</span></span>

1. <span data-ttu-id="ee4d9-119">运行 Windows 10 IoT Core 仪表板，然后单击*设置新设备*。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-119">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device*.</span></span>
2. <span data-ttu-id="ee4d9-120">选择"Qualcomm [DragonBoard 410 c]"作为设备类型。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-120">Select "Qualcomm [DragonBoard 410c]" as the device type.</span></span>
3. <span data-ttu-id="ee4d9-121">连接到使用 microUSB 电缆在 compuetr DragonBoard。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-121">Connect the DragonBoard to your compuetr using a microUSB cable.</span></span>
4. <span data-ttu-id="ee4d9-122">挂接到外部显示器你 DragongBoard。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-122">Hook up your DragongBoard to a external display.</span></span>
5. <span data-ttu-id="ee4d9-123">使用 12V 你 Dragonboard 开机 (> 1A) 在按下向上 （+） 的卷的电源按钮。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-123">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="ee4d9-124">设备-连接到显示-时应显示一把铁锤、 闪电，齿轮图标的图像。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-124">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span>
6. <span data-ttu-id="ee4d9-125">设备现在应可以看到如下所示的仪表板上。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-125">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="ee4d9-126">选择适当的设备。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-126">Select the appropriate device.</span></span>
7. <span data-ttu-id="ee4d9-127">接受软件 licnse 条款，然后单击**下载并安装**。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-127">Accept the software licnse terms and click **Download and install**.</span></span> <span data-ttu-id="ee4d9-128">你将看到 Windows 10 IoT Core 现在闪到你的设备上。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-128">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>

![在闪存模式下的 DragonBoard](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="ee4d9-130">连接到网络</span><span class="sxs-lookup"><span data-stu-id="ee4d9-130">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="ee4d9-131">有线的连接</span><span class="sxs-lookup"><span data-stu-id="ee4d9-131">Wired connection</span></span>
<span data-ttu-id="ee4d9-132">如果你的设备附带的以太网端口或 USB 以太网适配器支持，使您的有线的连接，将附加以太网电缆连接到你的网络。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-132">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="ee4d9-133">无线连接</span><span class="sxs-lookup"><span data-stu-id="ee4d9-133">Wireless connection</span></span>
<span data-ttu-id="ee4d9-134">如果你的设备支持的 Wi-fi 连接，并且你已连接到它的显示，你将需要：</span><span class="sxs-lookup"><span data-stu-id="ee4d9-134">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="ee4d9-135">转到默认应用程序并单击设置按钮旁边的时钟。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-135">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="ee4d9-136">在设置页上选择_网络和 Wi-fi_。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-136">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="ee4d9-137">你的设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-137">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="ee4d9-138">一旦你的网络会显示此列表中，选择它，然后单击_Connect_。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-138">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="ee4d9-139">如果尚未连接显示，并且想要通过 Wi-fi 连接，你将需要：</span><span class="sxs-lookup"><span data-stu-id="ee4d9-139">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="ee4d9-140">转到 IoT 仪表板，并单击_我的设备_。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-140">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="ee4d9-141">查找从列表中未配置开发板。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-141">Find your unconfigured board from the list.</span></span> <span data-ttu-id="ee4d9-142">其名称开头"AJ_"...(例如 AJ_58EA6C68)。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-142">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="ee4d9-143">如果看不到开发板出现几分钟后，请尝试重新启动你的板。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-143">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="ee4d9-144">单击_配置设备_并输入你的网络凭据。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-144">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="ee4d9-145">这将连接到网络的开发板。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-145">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="ee4d9-146">您的计算机上的 Wifi 将需要打开以便找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-146">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="ee4d9-147">连接到 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="ee4d9-147">Connect to Windows Device Portal</span></span>

<span data-ttu-id="ee4d9-148">使用[Windows Device Portal](../manage-your-device/DevicePortal.md)通过 web 浏览器连接你的设备。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-148">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="ee4d9-149">设备门户提供有价值的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="ee4d9-149">The device portal makes valuable configuration and device management capabilities available.</span></span> 

