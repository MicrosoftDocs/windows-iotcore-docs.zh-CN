---
title: 设置 Raspberry Pi
ms.date: 05/22/2019
ms.topic: article
description: 了解如何通过 Windows 10 IoT 核心版来设置 Raspberry Pi。 使用仪表板、连接到网络，并连接到 Windows 设备门户。
keywords: Windows 10 IoT 核心版, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: b07ffa15cb42a7ad486db31124a32a5f3bdff703
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90781639"
---
# <a name="setting-up-a-raspberry-pi"></a><span data-ttu-id="30a30-105">设置 Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="30a30-105">Setting up a Raspberry Pi</span></span>

## <a name="overview"></a><span data-ttu-id="30a30-106">概述</span><span class="sxs-lookup"><span data-stu-id="30a30-106">Overview</span></span>

> [!NOTE]
> <span data-ttu-id="30a30-107">仪表板不能用来设置 Raspberry Pi 3B+。</span><span class="sxs-lookup"><span data-stu-id="30a30-107">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="30a30-108">如果有 3B+ 设备，则必须使用 [3B+ 技术预览版](https://www.microsoft.com/en-us/software-download/windowsiot)。</span><span class="sxs-lookup"><span data-stu-id="30a30-108">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="30a30-109">请查看技术预览版的[已知限制](https://docs.microsoft.com/windows/iot-core/troubleshooting)，确定它是否适合开发。</span><span class="sxs-lookup"><span data-stu-id="30a30-109">Please view the [known limitations](https://docs.microsoft.com/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30a30-110">出现“格式化此磁盘”弹出窗口时，请勿格式化磁盘。__</span><span class="sxs-lookup"><span data-stu-id="30a30-110">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="30a30-111">我们正在努力修复此问题。</span><span class="sxs-lookup"><span data-stu-id="30a30-111">We are working on a fix for this issue.</span></span>

<span data-ttu-id="30a30-112">设置进行原型制作的 Raspberry Pi 时，建议使用 Windows 10 IoT 核心版仪表板。</span><span class="sxs-lookup"><span data-stu-id="30a30-112">When setting up a Raspberry Pi for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="30a30-113">但是，若要使用 Raspberry Pi 进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="30a30-113">However, if you're looking to manufacture with a Raspberry Pi, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="30a30-114">不能将创客映像用于制作。</span><span class="sxs-lookup"><span data-stu-id="30a30-114">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="30a30-115">使用仪表板</span><span class="sxs-lookup"><span data-stu-id="30a30-115">Using the Dashboard</span></span>

<span data-ttu-id="30a30-116">若要将 IoT 核心版刷写或下载到 Raspberry Pi，需要以下项：</span><span class="sxs-lookup"><span data-stu-id="30a30-116">To flash, or download, IoT Core onto your Raspberry Pi, you'll need:</span></span>
* <span data-ttu-id="30a30-117">运行 Windows 10 的计算机</span><span class="sxs-lookup"><span data-stu-id="30a30-117">A computer running Windows 10</span></span> 
* [<span data-ttu-id="30a30-118">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="30a30-118">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="30a30-119">高性能 SD 卡，例如 SanDisk SD 卡</span><span class="sxs-lookup"><span data-stu-id="30a30-119">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="30a30-120">外部显示器</span><span class="sxs-lookup"><span data-stu-id="30a30-120">An external display</span></span>
* <span data-ttu-id="30a30-121">任何其他外设（例如鼠标、键盘等）</span><span class="sxs-lookup"><span data-stu-id="30a30-121">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="30a30-122">Instructions</span><span class="sxs-lookup"><span data-stu-id="30a30-122">Instructions</span></span>

1. <span data-ttu-id="30a30-123">运行 Windows 10 IoT 核心版仪表板，单击“设置新设备”，然后将 SD 卡插入计算机中。</span><span class="sxs-lookup"><span data-stu-id="30a30-123">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert an SD card into your computer.</span></span>
2. <span data-ttu-id="30a30-124">将 Raspberry Pi 连接到外部显示器。</span><span class="sxs-lookup"><span data-stu-id="30a30-124">Hook up your Raspberry Pi to an external display.</span></span>
3. <span data-ttu-id="30a30-125">填写字段。</span><span class="sxs-lookup"><span data-stu-id="30a30-125">Fill out the fields.</span></span> <span data-ttu-id="30a30-126">选择“Broadcomm [Raspberry Pi 2 & 3]”作为设备类型。</span><span class="sxs-lookup"><span data-stu-id="30a30-126">Select "Broadcomm [Raspberry Pi 2 & 3]" as the device type.</span></span> <span data-ttu-id="30a30-127">确保为设备提供新的名称和密码。</span><span class="sxs-lookup"><span data-stu-id="30a30-127">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="30a30-128">否则，默认凭据仍旧为：</span><span class="sxs-lookup"><span data-stu-id="30a30-128">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="30a30-129">接受软件许可条款，然后单击“下载并安装”。</span><span class="sxs-lookup"><span data-stu-id="30a30-129">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="30a30-130">如果一切正常，则可以看到 Windows 10 IoT 核心版此时正刷写 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="30a30-130">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![仪表板屏幕截图](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="30a30-132">连接到网络</span><span class="sxs-lookup"><span data-stu-id="30a30-132">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="30a30-133">有线连接</span><span class="sxs-lookup"><span data-stu-id="30a30-133">Wired connection</span></span>
<span data-ttu-id="30a30-134">如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。</span><span class="sxs-lookup"><span data-stu-id="30a30-134">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="30a30-135">无线连接</span><span class="sxs-lookup"><span data-stu-id="30a30-135">Wireless connection</span></span>
<span data-ttu-id="30a30-136">如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="30a30-136">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="30a30-137">进入默认应用程序，单击时钟旁边的设置按钮。</span><span class="sxs-lookup"><span data-stu-id="30a30-137">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="30a30-138">在设置页上，选择“网络和 Wi-Fi”。__</span><span class="sxs-lookup"><span data-stu-id="30a30-138">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="30a30-139">设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="30a30-139">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="30a30-140">你的网络显示在此列表中以后，将其选中，然后单击“连接”。__</span><span class="sxs-lookup"><span data-stu-id="30a30-140">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="30a30-141">如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="30a30-141">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="30a30-142">转到 IoT 仪表板，单击“我的设备”。__</span><span class="sxs-lookup"><span data-stu-id="30a30-142">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="30a30-143">从列表中找到你的未配置的板。</span><span class="sxs-lookup"><span data-stu-id="30a30-143">Find your unconfigured board from the list.</span></span> <span data-ttu-id="30a30-144">其名称会以“AJ_”开头（例如 AJ_58EA6C68）。</span><span class="sxs-lookup"><span data-stu-id="30a30-144">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="30a30-145">如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。</span><span class="sxs-lookup"><span data-stu-id="30a30-145">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="30a30-146">单击“配置设备”，然后输入网络凭据。__</span><span class="sxs-lookup"><span data-stu-id="30a30-146">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="30a30-147">这样就会将板连接到网络。</span><span class="sxs-lookup"><span data-stu-id="30a30-147">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="30a30-148">需启用计算机上的 Wi-Fi 才能找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="30a30-148">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="30a30-149">连接到 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="30a30-149">Connect to Windows Device Portal</span></span>

<span data-ttu-id="30a30-150">使用 [Windows 设备门户](../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。</span><span class="sxs-lookup"><span data-stu-id="30a30-150">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="30a30-151">设备门户提供重要的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="30a30-151">The device portal makes valuable configuration and device management capabilities available.</span></span> 
