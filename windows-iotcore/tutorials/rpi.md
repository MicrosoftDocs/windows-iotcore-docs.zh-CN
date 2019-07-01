---
title: 设置 Raspberry Pi
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解如何通过 Windows 10 IoT 核心版来设置 Raspberry Pi。
keywords: Windows 10 IoT 核心版, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: 3269aa2ed102b667519baa9212e604083f910783
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "66182189"
---
# <a name="setting-up-a-raspberry-pi"></a><span data-ttu-id="0a23e-104">设置 Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="0a23e-104">Setting up a Raspberry Pi</span></span>

## <a name="overview"></a><span data-ttu-id="0a23e-105">概述</span><span class="sxs-lookup"><span data-stu-id="0a23e-105">Overview</span></span>

> [!NOTE]
> <span data-ttu-id="0a23e-106">仪表板不能用来设置 Raspberry Pi 3B+。</span><span class="sxs-lookup"><span data-stu-id="0a23e-106">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="0a23e-107">如果有 3B+ 设备，则必须使用 [3B+ 技术预览版](https://www.microsoft.com/en-us/software-download/windowsiot)。</span><span class="sxs-lookup"><span data-stu-id="0a23e-107">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="0a23e-108">请查看技术预览版的[已知限制](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)，确定它是否适合开发。</span><span class="sxs-lookup"><span data-stu-id="0a23e-108">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a23e-109">出现“格式化此磁盘”弹出窗口时，请勿格式化磁盘。 </span><span class="sxs-lookup"><span data-stu-id="0a23e-109">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="0a23e-110">我们正在修复此问题。</span><span class="sxs-lookup"><span data-stu-id="0a23e-110">We are working on a fix for this issue.</span></span>

<span data-ttu-id="0a23e-111">设置进行原型制作的 Raspberry Pi 时，建议使用 Windows 10 IoT 核心版仪表板。</span><span class="sxs-lookup"><span data-stu-id="0a23e-111">When setting up a Raspberry Pi for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="0a23e-112">但是，若要使用 Raspberry Pi 进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="0a23e-112">However, if you're looking to manufacture with a Raspberry Pi, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="0a23e-113">不能将创客映像用于制作。</span><span class="sxs-lookup"><span data-stu-id="0a23e-113">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="0a23e-114">使用仪表板</span><span class="sxs-lookup"><span data-stu-id="0a23e-114">Using the Dashboard</span></span>

<span data-ttu-id="0a23e-115">若要将 IoT 核心版刷写或下载到 Raspberry Pi，需要以下项：</span><span class="sxs-lookup"><span data-stu-id="0a23e-115">To flash, or download, IoT Core onto your Raspberry Pi, you'll need:</span></span>
* <span data-ttu-id="0a23e-116">运行 Windows 10 的计算机</span><span class="sxs-lookup"><span data-stu-id="0a23e-116">A computer running Windows 10</span></span> 
* [<span data-ttu-id="0a23e-117">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="0a23e-117">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="0a23e-118">高性能 SD 卡，例如 SanDisk SD 卡</span><span class="sxs-lookup"><span data-stu-id="0a23e-118">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="0a23e-119">外部显示器</span><span class="sxs-lookup"><span data-stu-id="0a23e-119">An external display</span></span>
* <span data-ttu-id="0a23e-120">任何其他外设（例如鼠标、键盘等）</span><span class="sxs-lookup"><span data-stu-id="0a23e-120">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="0a23e-121">说明</span><span class="sxs-lookup"><span data-stu-id="0a23e-121">Instructions</span></span>

1. <span data-ttu-id="0a23e-122">运行 Windows 10 IoT 核心版仪表板，单击“设置新设备”，然后将 SD 卡插入计算机中。 </span><span class="sxs-lookup"><span data-stu-id="0a23e-122">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="0a23e-123">将 Raspberry Pi 连接到外部显示器。</span><span class="sxs-lookup"><span data-stu-id="0a23e-123">Hook up your Raspberry Pi to an external display.</span></span>
3. <span data-ttu-id="0a23e-124">填写字段。</span><span class="sxs-lookup"><span data-stu-id="0a23e-124">Fill out the fields.</span></span> <span data-ttu-id="0a23e-125">选择“Broadcomm [Raspberry Pi 2 & 3]”作为设备类型。</span><span class="sxs-lookup"><span data-stu-id="0a23e-125">Select "Broadcomm [Raspberry Pi 2 & 3]" as the device type.</span></span> <span data-ttu-id="0a23e-126">确保为设备提供新的名称和密码。</span><span class="sxs-lookup"><span data-stu-id="0a23e-126">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="0a23e-127">否则，默认凭据仍旧为：</span><span class="sxs-lookup"><span data-stu-id="0a23e-127">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="0a23e-128">接受软件许可条款，然后单击“下载并安装”  。</span><span class="sxs-lookup"><span data-stu-id="0a23e-128">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="0a23e-129">如果一切正常，则可以看到 Windows 10 IoT 核心版此时正刷写 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="0a23e-129">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![仪表板屏幕截图](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="0a23e-131">连接到网络</span><span class="sxs-lookup"><span data-stu-id="0a23e-131">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="0a23e-132">有线连接</span><span class="sxs-lookup"><span data-stu-id="0a23e-132">Wired connection</span></span>
<span data-ttu-id="0a23e-133">如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。</span><span class="sxs-lookup"><span data-stu-id="0a23e-133">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="0a23e-134">无线连接</span><span class="sxs-lookup"><span data-stu-id="0a23e-134">Wireless connection</span></span>
<span data-ttu-id="0a23e-135">如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="0a23e-135">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="0a23e-136">进入默认应用程序，单击时钟旁边的设置按钮。</span><span class="sxs-lookup"><span data-stu-id="0a23e-136">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="0a23e-137">在设置页上，选择“网络和 Wi-Fi”。 </span><span class="sxs-lookup"><span data-stu-id="0a23e-137">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="0a23e-138">设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="0a23e-138">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="0a23e-139">你的网络显示在此列表中以后，将其选中，然后单击“连接”。 </span><span class="sxs-lookup"><span data-stu-id="0a23e-139">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="0a23e-140">如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="0a23e-140">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="0a23e-141">转到 IoT 仪表板，单击“我的设备”。 </span><span class="sxs-lookup"><span data-stu-id="0a23e-141">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="0a23e-142">从列表中找到你的未配置的板。</span><span class="sxs-lookup"><span data-stu-id="0a23e-142">Find your unconfigured board from the list.</span></span> <span data-ttu-id="0a23e-143">其名称会以“AJ_”开头（例如 AJ_58EA6C68）。</span><span class="sxs-lookup"><span data-stu-id="0a23e-143">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="0a23e-144">如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。</span><span class="sxs-lookup"><span data-stu-id="0a23e-144">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="0a23e-145">单击“配置设备”，然后输入网络凭据。 </span><span class="sxs-lookup"><span data-stu-id="0a23e-145">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="0a23e-146">这样就会将板连接到网络。</span><span class="sxs-lookup"><span data-stu-id="0a23e-146">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="0a23e-147">需启用计算机上的 Wi-Fi 才能找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="0a23e-147">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="0a23e-148">连接到 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="0a23e-148">Connect to Windows Device Portal</span></span>

<span data-ttu-id="0a23e-149">使用 [Windows 设备门户](../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。</span><span class="sxs-lookup"><span data-stu-id="0a23e-149">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="0a23e-150">设备门户提供重要的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="0a23e-150">The device portal makes valuable configuration and device management capabilities available.</span></span> 
