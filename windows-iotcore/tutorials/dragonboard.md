---
title: 设置 Dragonboard
ms.date: 05/22/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何通过 Windows 10 IoT 核心版来设置 Dragonboard。 使用仪表板、连接到网络，并连接到 Windows 设备门户。
keywords: Windows 10 IoT 核心版, Dragonboard
ms.custom: RS5
ms.openlocfilehash: bde424a321121853dd556eec2fe42a78a8ff3bc4
ms.sourcegitcommit: d048cc83c8a916bc761f5065e880d3555758321c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2021
ms.locfileid: "102247112"
---
# <a name="setting-up-a-dragonboard"></a><span data-ttu-id="ae5d5-105">设置 Dragonboard</span><span class="sxs-lookup"><span data-stu-id="ae5d5-105">Setting up a Dragonboard</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae5d5-106">使用新的 Dragonboard 时，请注意，它已经安装了 Android。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-106">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="ae5d5-107">需使用[此处](https://docs.microsoft.com/windows/iot-core/tutorials/qualcomm)的 eMMC 刷写方法擦除并加载设备。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-107">You will need to wipe and load the device using the eMMC flashing method, [here](https://docs.microsoft.com/windows/iot-core/tutorials/qualcomm).</span></span>

> [!NOTE]
> <span data-ttu-id="ae5d5-108">如果 DragonBoard 出现任何音频相关问题，建议通读[此处](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)提供的 Qualcomm 的手册。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-108">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span>

<span data-ttu-id="ae5d5-109">设置进行原型制作的 Dragonboard 时，建议使用 Windows 10 IoT 核心版仪表板。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-109">When setting up a Dragonboard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="ae5d5-110">但是，若要使用 Dragonboard 进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-110">However, if you're looking to manufacture with a Dragonboard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="ae5d5-111">不能将创客映像用于制作。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-111">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a><span data-ttu-id="ae5d5-112">使用仪表板</span><span class="sxs-lookup"><span data-stu-id="ae5d5-112">Using the Dashboard</span></span>

<span data-ttu-id="ae5d5-113">若要将 IoT 核心版刷写或下载到 MinnowBoard，需要以下项：</span><span class="sxs-lookup"><span data-stu-id="ae5d5-113">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="ae5d5-114">运行 Windows 10 的计算机</span><span class="sxs-lookup"><span data-stu-id="ae5d5-114">A computer running Windows 10</span></span>
* [<span data-ttu-id="ae5d5-115">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="ae5d5-115">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="ae5d5-116">MicroUSB 电缆</span><span class="sxs-lookup"><span data-stu-id="ae5d5-116">MicroUSB cable</span></span>
* <span data-ttu-id="ae5d5-117">外部显示器</span><span class="sxs-lookup"><span data-stu-id="ae5d5-117">An external display</span></span>
* <span data-ttu-id="ae5d5-118">任何其他外设（例如鼠标、键盘等）</span><span class="sxs-lookup"><span data-stu-id="ae5d5-118">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="ae5d5-119">Instructions</span><span class="sxs-lookup"><span data-stu-id="ae5d5-119">Instructions</span></span>

1. <span data-ttu-id="ae5d5-120">运行 Windows 10 IoT 核心版仪表板，然后单击“设置新设备”。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-120">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device*.</span></span>
2. <span data-ttu-id="ae5d5-121">选择“Qualcomm [DragonBoard 410c]”作为设备类型。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-121">Select "Qualcomm [DragonBoard 410c]" as the device type.</span></span>
3. <span data-ttu-id="ae5d5-122">使用 microUSB 电缆将 DragonBoard 连接到计算机。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-122">Connect the DragonBoard to your compuetr using a microUSB cable.</span></span>
4. <span data-ttu-id="ae5d5-123">将 DragongBoard 连接到外部显示器。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-123">Hook up your DragongBoard to an external display.</span></span>
5. <span data-ttu-id="ae5d5-124">使用 12V (>1A) 电源在按住调高音量 (+) 按钮的情况下将 Dragonboard 通电。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-124">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="ae5d5-125">此设备在连接到显示器的情况下应该显示包含一个锤子、一个闪电和一个齿轮的图像。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-125">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span>
6. <span data-ttu-id="ae5d5-126">此设备现在应该在仪表板上可见，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-126">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="ae5d5-127">选择适当的设备。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-127">Select the appropriate device.</span></span>
7. <span data-ttu-id="ae5d5-128">接受软件许可条款，然后单击“下载并安装”。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-128">Accept the software license terms and click **Download and install**.</span></span> <span data-ttu-id="ae5d5-129">可以看到 Windows 10 IoT 核心版此时正刷写到设备上。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-129">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>

![处于刷写模式的 DragonBoard](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="ae5d5-131">连接到网络</span><span class="sxs-lookup"><span data-stu-id="ae5d5-131">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="ae5d5-132">有线连接</span><span class="sxs-lookup"><span data-stu-id="ae5d5-132">Wired connection</span></span>
<span data-ttu-id="ae5d5-133">如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-133">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="ae5d5-134">无线连接</span><span class="sxs-lookup"><span data-stu-id="ae5d5-134">Wireless connection</span></span>
<span data-ttu-id="ae5d5-135">如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ae5d5-135">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="ae5d5-136">进入默认应用程序，单击时钟旁边的设置按钮。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-136">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="ae5d5-137">在设置页上，选择“网络和 Wi-Fi”。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-137">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="ae5d5-138">设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-138">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="ae5d5-139">你的网络显示在此列表中以后，将其选中，然后单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-139">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="ae5d5-140">如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ae5d5-140">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="ae5d5-141">转到 IoT 仪表板，单击“我的设备”。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-141">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="ae5d5-142">从列表中找到你的未配置的板。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-142">Find your unconfigured board from the list.</span></span> <span data-ttu-id="ae5d5-143">其名称会以“AJ_”开头（例如 AJ_58EA6C68）。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-143">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="ae5d5-144">如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-144">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="ae5d5-145">单击“配置设备”，然后输入网络凭据。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-145">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="ae5d5-146">这样就会将板连接到网络。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-146">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="ae5d5-147">需启用计算机上的 Wi-Fi 才能找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-147">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="ae5d5-148">连接到 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="ae5d5-148">Connect to Windows Device Portal</span></span>

<span data-ttu-id="ae5d5-149">使用 [Windows 设备门户](../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-149">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="ae5d5-150">设备门户提供重要的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-150">The device portal makes valuable configuration and device management capabilities available.</span></span>
