---
title: 远程显示
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何查看和远程控制您的 Windows 10 IoT Core UWP 应用程序。
keywords: windows iot，UWP，远程显示远程，UWP 应用程序
ms.openlocfilehash: 6f46ddbc5738f377ce3ebd15a49785e27c6a40bf
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510886"
---
# <a name="remote-display"></a><span data-ttu-id="3e58e-104">远程显示</span><span class="sxs-lookup"><span data-stu-id="3e58e-104">Remote display</span></span>
<span data-ttu-id="3e58e-105">查看和控制 Windows 10 IoT Core UWP 应用程序远程，从 Windows 10 桌面 PC、 平板电脑或手机</span><span class="sxs-lookup"><span data-stu-id="3e58e-105">View and control your Windows 10 IoT Core UWP applications remotely, from a Windows 10 desktop PC, tablet, or phone</span></span>

> [!WARNING]
> <span data-ttu-id="3e58e-106">Windows IoT 远程客户端是开发人员的唯一功能。</span><span class="sxs-lookup"><span data-stu-id="3e58e-106">Windows IoT Remote Client is a developer only feature.</span></span> <span data-ttu-id="3e58e-107">它不打算使用或生产设备的受支持。</span><span class="sxs-lookup"><span data-stu-id="3e58e-107">It is not intended or supported for production devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e58e-108">Windows IoT 远程客户端并不适用于 Raspberry Pi。</span><span class="sxs-lookup"><span data-stu-id="3e58e-108">The Windows IoT Remote client does not work for Raspberry Pi.</span></span> <span data-ttu-id="3e58e-109">使用如 Minnowboard 最大或 Dragonboard 加速图形使用看板或附加的本地显示的监视器。</span><span class="sxs-lookup"><span data-stu-id="3e58e-109">Use a board with accelerated graphics such as Minnowboard Max or Dragonboard or attach a monitor for local display.</span></span>

## <a name="overview"></a><span data-ttu-id="3e58e-110">概述</span><span class="sxs-lookup"><span data-stu-id="3e58e-110">Overview</span></span>
___
<span data-ttu-id="3e58e-111">远程显示体验是用来远程控制的 Windows 10 IoT Core 设备上运行的 UWP 应用程序的开发人员工具。</span><span class="sxs-lookup"><span data-stu-id="3e58e-111">The remote display experience is a developer tool used to remotely control UWP applications running on a Windows 10 IoT Core device.</span></span>   

## <a name="setup"></a><span data-ttu-id="3e58e-112">安装</span><span class="sxs-lookup"><span data-stu-id="3e58e-112">Setup</span></span>
___
<span data-ttu-id="3e58e-113">若要开始，你将需要设置具有最新版本的 Windows 10 的 Windows 10 IoT Core 设备-请访问[开始](https://developer.microsoft.com/en-us/windows/iot/getstarted)页后，可以设置你的板。</span><span class="sxs-lookup"><span data-stu-id="3e58e-113">To get started, you'll need to set up a Windows 10 IoT Core device with the latest build of Windows 10 - visit the [Get Started](https://developer.microsoft.com/en-us/windows/iot/getstarted) page to set up your board.</span></span>

<span data-ttu-id="3e58e-114">安装程序的过程快速而简单-请按照下面使用的远程显示技术的三个步骤。</span><span class="sxs-lookup"><span data-stu-id="3e58e-114">Setup is quick and easy - follow the three steps below to use the remote display technology.</span></span>

1. <span data-ttu-id="3e58e-115">请确保 IoT Core 设备和开发计算机上相同的网络和 n 安全的环境。</span><span class="sxs-lookup"><span data-stu-id="3e58e-115">Ensure that your IoT Core device and development computer are on the same network and n a secure environment.</span></span>

    <span data-ttu-id="3e58e-116">一种方法是将设备连接直接到便携式计算机使用支持自动交叉的 USB 以太网适配器。</span><span class="sxs-lookup"><span data-stu-id="3e58e-116">One method is to connect your device directly to your laptop using a USB Ethernet adapter which supports automatic crossover.</span></span>

1. <span data-ttu-id="3e58e-117">启用 Windows 10 IoT Core 设备上的远程显示功能。</span><span class="sxs-lookup"><span data-stu-id="3e58e-117">Turn on the remote display functionality on your Windows 10 IoT Core device.</span></span>
  
    <span data-ttu-id="3e58e-118">将设备连接到 Internet 并连接到 Windows Device Portal。</span><span class="sxs-lookup"><span data-stu-id="3e58e-118">Connect your device to the Internet and connect to Windows Device Portal.</span></span>
  
    <span data-ttu-id="3e58e-119">从左侧的选项选择页"Remote"并标记该复选框，标记为"启用窗口 IoT 远程服务器"。</span><span class="sxs-lookup"><span data-stu-id="3e58e-119">Choose the page "Remote" from the options on the left, and mark the check box labeled "Enable Window IoT Remote Server".</span></span>  <span data-ttu-id="3e58e-120">你的设备现已为远程显示体验。</span><span class="sxs-lookup"><span data-stu-id="3e58e-120">Your device is now enabled for remote display experience.</span></span>
    ![启用远程显示体验](../media/RemoteDisplay/enable-remote.png)

1. <span data-ttu-id="3e58e-122">在随附 Windows 10 设备上安装 Windows IoT 远程客户端。</span><span class="sxs-lookup"><span data-stu-id="3e58e-122">Install the Windows IoT Remote Client on your companion Windows 10 device.</span></span>
  
    <span data-ttu-id="3e58e-123">若要使 Windows 10 设备能够连接到 Windows 10 IoT Core 设备，需要安装应用商店应用程序。</span><span class="sxs-lookup"><span data-stu-id="3e58e-123">To enable a Windows 10 device to connect to your Windows 10 IoT Core device, you need to install our Store application.</span></span>  <span data-ttu-id="3e58e-124">Windows IoT 远程客户端应用程序当前可通过仅链接，可在[此处](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz)。</span><span class="sxs-lookup"><span data-stu-id="3e58e-124">The Windows IoT Remote Client app is currently available by link only and can be found [here](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span></span>
    
    ![安装客户端应用程序](../media/RemoteDisplay/store-app.png)


1. <span data-ttu-id="3e58e-126">连接到 Windows 10 IoT Core 设备通过已安装的应用程序。</span><span class="sxs-lookup"><span data-stu-id="3e58e-126">Connect to your Windows 10 IoT Core device through the installed application.</span></span>
  
    <span data-ttu-id="3e58e-127">在 Windows 10 配套设备上运行 Windows IoT 远程客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="3e58e-127">Run the Windows IoT Remote Client application on your Windows 10 companion device.</span></span>  <span data-ttu-id="3e58e-128">在连接屏幕中，输入你的设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3e58e-128">At the Connect screen, enter the IP address of your device.</span></span> <span data-ttu-id="3e58e-129">两台设备应连接远程处理到伴侣设备的 Windows 10 IoT Core 设备的 UI 体验。</span><span class="sxs-lookup"><span data-stu-id="3e58e-129">The two devices should connect, remoting the UI experience of the Windows 10 IoT Core device to the companion device.</span></span>
    
    <span data-ttu-id="3e58e-130">你现在已连接 ！</span><span class="sxs-lookup"><span data-stu-id="3e58e-130">You're now connected!</span></span> <span data-ttu-id="3e58e-131">从此时转发、 触摸和单击配套设备可用于控制 Windows 10 IoT Core UWP 应用程序的 Windows 10 上的输入。</span><span class="sxs-lookup"><span data-stu-id="3e58e-131">From this point forward, touch and click input on the companion Windows 10 device can be used to control the Windows 10 IoT Core UWP application.</span></span>  
    ![设备连接](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a><span data-ttu-id="3e58e-133">兼容性和作用域</span><span class="sxs-lookup"><span data-stu-id="3e58e-133">Compatibility and scope</span></span>
___
<span data-ttu-id="3e58e-134">若要使用 IoT 远程客户端，您必须在最新版本的 Windows 10 IoT Core 上运行目标设备和最新的客户端应用程序从应用商店。</span><span class="sxs-lookup"><span data-stu-id="3e58e-134">In order to use the IoT Remote Client, you must be running the latest build of Windows 10 IoT Core on the target device and the latest client application from the store.</span></span> 
    
  
## <a name="troubleshooting"></a><span data-ttu-id="3e58e-135">疑难解答</span><span class="sxs-lookup"><span data-stu-id="3e58e-135">Troubleshooting</span></span>
___
<span data-ttu-id="3e58e-136">使用远程显示技术的过程快速而简单，但仍有一些用户可能会遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="3e58e-136">Using the remote display technology is quick and easy, but there are still some issues that users may experience.</span></span>  <span data-ttu-id="3e58e-137">请务必遵循上述说明密切-如果问题仍然存在，请查看以下安装程序。</span><span class="sxs-lookup"><span data-stu-id="3e58e-137">Make sure to follow the Setup instructions above closely - if problems persist, check below.</span></span>

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a><span data-ttu-id="3e58e-138">当我尝试进行连接时，客户端应用程序将进入白色屏幕。</span><span class="sxs-lookup"><span data-stu-id="3e58e-138">When I try to connect, the client app goes to a white screen.</span></span>
<span data-ttu-id="3e58e-139">失败的连接可能会导致通过一系列问题，但我们已经遇到了一些较为常见的问题：</span><span class="sxs-lookup"><span data-stu-id="3e58e-139">Failed connections can be caused by a number of issues, but we've run into a couple more common problems:</span></span>

1. <span data-ttu-id="3e58e-140">请确保运行最新内部版本的 Windows 10 IoT 核心版和 IoT 远程客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="3e58e-140">Ensure that you are running the latest insider version of Windows 10 IoT Core and the IoT Remote Client application.</span></span>
1. <span data-ttu-id="3e58e-141">首先，请确保你的 IoT 设备与伴侣设备位于同一网络上。</span><span class="sxs-lookup"><span data-stu-id="3e58e-141">First, make sure your IoT device is on the same network as your companion device.</span></span>
    <span data-ttu-id="3e58e-142">检查可以启用 Windows IoT 远程服务器运行 Windows 10 IoT Core 的最新的预览体验内部版本。</span><span class="sxs-lookup"><span data-stu-id="3e58e-142">Check that you're running the latest Insider build of Windows 10 IoT Core with the Windows IoT Remote Server enabled.</span></span>
1. <span data-ttu-id="3e58e-143">如果这不是问题，请尝试更改为我们肯定将会支持你设备的分辨率请执行上述步骤 1 中的设置部分的说明进行操作以导航到你的设备的 web 服务器。</span><span class="sxs-lookup"><span data-stu-id="3e58e-143">If this isn't the issue, try changing the resolution of your device to something we're guaranteed to support Follow the instructions in step 1 of the Setup section above to navigate to your device's web server.</span></span>  <span data-ttu-id="3e58e-144">在"主页"页上保持而不是从左侧菜单中选择"远程"，并向下滚动以查找解决方法。</span><span class="sxs-lookup"><span data-stu-id="3e58e-144">Instead of selecting "Remote" from the menu on the left, stay on the "Home" page and scroll down to find resolution.</span></span>  <span data-ttu-id="3e58e-145">请尝试 800 x 600。</span><span class="sxs-lookup"><span data-stu-id="3e58e-145">Try 800x600.</span></span>
1. <span data-ttu-id="3e58e-146">如果这样仍不能解决你遇到的问题，您可能永远不会将你的设备连接到外部显示器的根源的问题。</span><span class="sxs-lookup"><span data-stu-id="3e58e-146">If this still doesn't fix your issue, you may have an issue that stems from never connecting your device to an external display.</span></span>
    <span data-ttu-id="3e58e-147">这将导致设备本身将视为纯无外设。</span><span class="sxs-lookup"><span data-stu-id="3e58e-147">This will cause the device to think of itself as purely headless.</span></span>  <span data-ttu-id="3e58e-148">若要解决此问题：</span><span class="sxs-lookup"><span data-stu-id="3e58e-148">To fix this:</span></span>
    * <span data-ttu-id="3e58e-149">弹出 MicroSD 卡，并将其置于您的计算机</span><span class="sxs-lookup"><span data-stu-id="3e58e-149">Eject the MicroSD Card, and put into your computer</span></span>
    * <span data-ttu-id="3e58e-150">编辑</span><span class="sxs-lookup"><span data-stu-id="3e58e-150">Edit the</span></span> `<MicroSD card drive>:\config.txt`
    * <span data-ttu-id="3e58e-151">添加以下行：</span><span class="sxs-lookup"><span data-stu-id="3e58e-151">Add the following lines:</span></span>
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
