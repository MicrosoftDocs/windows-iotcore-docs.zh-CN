---
title: 远程显示
ms.date: 08/28/2017
ms.topic: article
description: 了解如何远程查看和控制 Windows 10 IoT Core UWP 应用程序。
keywords: windows iot，UWP，远程显示，远程，UWP 应用程序
ms.openlocfilehash: 146863bf02db3941b3fbc70c8c8e48add65cd27a
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782409"
---
# <a name="remote-display"></a><span data-ttu-id="50bae-104">远程显示</span><span class="sxs-lookup"><span data-stu-id="50bae-104">Remote display</span></span>
<span data-ttu-id="50bae-105">从 Windows 10 台式计算机、平板电脑或手机远程查看并控制 Windows 10 IoT Core UWP 应用程序</span><span class="sxs-lookup"><span data-stu-id="50bae-105">View and control your Windows 10 IoT Core UWP applications remotely, from a Windows 10 desktop PC, tablet, or phone</span></span>

> [!WARNING]
> <span data-ttu-id="50bae-106">Windows IoT 远程客户端是一项仅开发人员功能。</span><span class="sxs-lookup"><span data-stu-id="50bae-106">Windows IoT Remote Client is a developer only feature.</span></span> <span data-ttu-id="50bae-107">它不适合生产设备，也不受支持。</span><span class="sxs-lookup"><span data-stu-id="50bae-107">It is not intended or supported for production devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50bae-108">Windows IoT 远程客户端不适用于 Raspberry Pi。</span><span class="sxs-lookup"><span data-stu-id="50bae-108">The Windows IoT Remote client does not work for Raspberry Pi.</span></span> <span data-ttu-id="50bae-109">使用带加速图形的板（例如 Minnowboard Max 或 Dragonboard），或者连接一个用于本地显示的监视器。</span><span class="sxs-lookup"><span data-stu-id="50bae-109">Use a board with accelerated graphics such as Minnowboard Max or Dragonboard or attach a monitor for local display.</span></span>

## <a name="overview"></a><span data-ttu-id="50bae-110">概述</span><span class="sxs-lookup"><span data-stu-id="50bae-110">Overview</span></span>
___
<span data-ttu-id="50bae-111">远程显示体验是一种开发人员工具，用于远程控制 Windows 10 IoT Core 设备上运行的 UWP 应用程序。</span><span class="sxs-lookup"><span data-stu-id="50bae-111">The remote display experience is a developer tool used to remotely control UWP applications running on a Windows 10 IoT Core device.</span></span>   

## <a name="setup"></a><span data-ttu-id="50bae-112">设置</span><span class="sxs-lookup"><span data-stu-id="50bae-112">Setup</span></span>
___
<span data-ttu-id="50bae-113">若要开始，需要使用最新版本的 Windows 10 设置 Windows 10 IoT Core 设备-请访问 [入门](https://developer.microsoft.com/en-us/windows/iot/getstarted) 页面以设置板。</span><span class="sxs-lookup"><span data-stu-id="50bae-113">To get started, you'll need to set up a Windows 10 IoT Core device with the latest build of Windows 10 - visit the [Get Started](https://developer.microsoft.com/en-us/windows/iot/getstarted) page to set up your board.</span></span>

<span data-ttu-id="50bae-114">安装程序可以快速轻松地执行以下三个步骤，以使用远程显示技术。</span><span class="sxs-lookup"><span data-stu-id="50bae-114">Setup is quick and easy - follow the three steps below to use the remote display technology.</span></span>

1. <span data-ttu-id="50bae-115">确保 IoT Core 设备和开发计算机位于同一网络中，并确保安全环境为 n。</span><span class="sxs-lookup"><span data-stu-id="50bae-115">Ensure that your IoT Core device and development computer are on the same network and n a secure environment.</span></span>

    <span data-ttu-id="50bae-116">一种方法是使用 USB 以太网适配器将设备直接连接到便携式计算机，它支持自动交叉。</span><span class="sxs-lookup"><span data-stu-id="50bae-116">One method is to connect your device directly to your laptop using a USB Ethernet adapter, which supports automatic crossover.</span></span>

1. <span data-ttu-id="50bae-117">启用 Windows 10 IoT Core 设备上的远程显示功能。</span><span class="sxs-lookup"><span data-stu-id="50bae-117">Turn on the remote display functionality on your Windows 10 IoT Core device.</span></span>
  
    <span data-ttu-id="50bae-118">将设备连接到 Internet 并连接到 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="50bae-118">Connect your device to the Internet and connect to Windows Device Portal.</span></span>
  
    <span data-ttu-id="50bae-119">从左侧的选项中选择 "远程" 页，并将标记为 "启用 Windows IoT 远程服务器" 的复选框标记为 "启用"。</span><span class="sxs-lookup"><span data-stu-id="50bae-119">Choose the page "Remote" from the options on the left, and mark the check box labeled "Enable Window IoT Remote Server".</span></span>  <span data-ttu-id="50bae-120">你的设备现在已启用远程显示体验。</span><span class="sxs-lookup"><span data-stu-id="50bae-120">Your device is now enabled for remote display experience.</span></span>
    <span data-ttu-id="50bae-121">![启用远程显示体验](../media/RemoteDisplay/enable-remote.png)</span><span class="sxs-lookup"><span data-stu-id="50bae-121">![Enable remote display experience](../media/RemoteDisplay/enable-remote.png)</span></span>

1. <span data-ttu-id="50bae-122">在随附的 Windows 10 设备上安装 Windows IoT 远程客户端。</span><span class="sxs-lookup"><span data-stu-id="50bae-122">Install the Windows IoT Remote Client on your companion Windows 10 device.</span></span>
  
    <span data-ttu-id="50bae-123">若要使 Windows 10 设备能够连接到 Windows 10 IoT Core 设备，需要安装我们的应用商店应用程序。</span><span class="sxs-lookup"><span data-stu-id="50bae-123">To enable a Windows 10 device to connect to your Windows 10 IoT Core device, you need to install our Store application.</span></span>  <span data-ttu-id="50bae-124">Windows IoT 远程客户端应用当前仅通过链接提供，可在 [此处](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz)找到。</span><span class="sxs-lookup"><span data-stu-id="50bae-124">The Windows IoT Remote Client app is currently available by link only and can be found [here](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span></span>
    
    ![安装客户端应用](../media/RemoteDisplay/store-app.png)


1. <span data-ttu-id="50bae-126">通过已安装的应用程序连接到 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="50bae-126">Connect to your Windows 10 IoT Core device through the installed application.</span></span>
  
    <span data-ttu-id="50bae-127">在 Windows 10 配套设备上运行 Windows IoT 远程客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="50bae-127">Run the Windows IoT Remote Client application on your Windows 10 companion device.</span></span>  <span data-ttu-id="50bae-128">在 "连接" 屏幕上，输入设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="50bae-128">At the Connect screen, enter the IP address of your device.</span></span> <span data-ttu-id="50bae-129">这两个设备应该连接，将 Windows 10 IoT Core 设备的 UI 体验远程处理到配套设备上。</span><span class="sxs-lookup"><span data-stu-id="50bae-129">The two devices should connect, remoting the UI experience of the Windows 10 IoT Core device to the companion device.</span></span>
    
    <span data-ttu-id="50bae-130">你现在已经连接了！</span><span class="sxs-lookup"><span data-stu-id="50bae-130">You're now connected!</span></span> <span data-ttu-id="50bae-131">从此开始，可使用触控并单击配套 Windows 10 设备上的输入来控制 Windows 10 IoT 核心 UWP 应用程序。</span><span class="sxs-lookup"><span data-stu-id="50bae-131">From this point forward, touch and click input on the companion Windows 10 device can be used to control the Windows 10 IoT Core UWP application.</span></span>  
    ![连接设备](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a><span data-ttu-id="50bae-133">兼容性和范围</span><span class="sxs-lookup"><span data-stu-id="50bae-133">Compatibility and scope</span></span>
___
<span data-ttu-id="50bae-134">若要使用 IoT 远程客户端，必须在目标设备上运行 Windows 10 IoT Core 的最新版本，并在应用商店中运行最新的客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="50bae-134">In order to use the IoT Remote Client, you must be running the latest build of Windows 10 IoT Core on the target device and the latest client application from the store.</span></span> 
    
  
## <a name="troubleshooting"></a><span data-ttu-id="50bae-135">故障排除</span><span class="sxs-lookup"><span data-stu-id="50bae-135">Troubleshooting</span></span>
___
<span data-ttu-id="50bae-136">使用远程显示技术非常简单，但仍有一些用户可能会遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="50bae-136">Using the remote display technology is quick and easy, but there are still some issues that users may experience.</span></span>  <span data-ttu-id="50bae-137">请确保按照上面的设置说明进行操作，如果问题仍然存在，请检查以下各项。</span><span class="sxs-lookup"><span data-stu-id="50bae-137">Make sure to follow the Setup instructions above closely - if problems persist, check below.</span></span>

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a><span data-ttu-id="50bae-138">当我尝试连接时，客户端应用程序会进入一个白屏。</span><span class="sxs-lookup"><span data-stu-id="50bae-138">When I try to connect, the client app goes to a white screen.</span></span>
<span data-ttu-id="50bae-139">失败的连接可能是由许多问题引起的，但我们遇到了一些更常见的问题：</span><span class="sxs-lookup"><span data-stu-id="50bae-139">Failed connections can be caused by a number of issues, but we've run into a couple more common problems:</span></span>

1. <span data-ttu-id="50bae-140">确保运行最新版本的 Windows 10 IoT Core 和 IoT 远程客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="50bae-140">Ensure that you are running the latest insider version of Windows 10 IoT Core and the IoT Remote Client application.</span></span>
1. <span data-ttu-id="50bae-141">首先，请确保 IoT 设备与配套设备位于同一网络中。</span><span class="sxs-lookup"><span data-stu-id="50bae-141">First, make sure your IoT device is on the same network as your companion device.</span></span>
    <span data-ttu-id="50bae-142">检查是否正在运行 windows 10 IoT Core 的最新内部版本，并启用了 Windows IoT 远程服务器。</span><span class="sxs-lookup"><span data-stu-id="50bae-142">Check that you're running the latest Insider build of Windows 10 IoT Core with the Windows IoT Remote Server enabled.</span></span>
1. <span data-ttu-id="50bae-143">如果这不是问题，请尝试将设备的分辨率更改为我们保证支持的内容。</span><span class="sxs-lookup"><span data-stu-id="50bae-143">If this isn't the issue, try changing the resolution of your device to something we're guaranteed to support.</span></span>
    <span data-ttu-id="50bae-144">按照上述设置部分的步骤1中的说明导航到设备的 web 服务器。</span><span class="sxs-lookup"><span data-stu-id="50bae-144">Follow the instructions in step 1 of the Setup section above to navigate to your device's web server.</span></span>  <span data-ttu-id="50bae-145">请在 "主页" 页上停留，并向下滚动以查找分辨率，而不是从左侧菜单中选择 "远程"。</span><span class="sxs-lookup"><span data-stu-id="50bae-145">Instead of selecting "Remote" from the menu on the left, stay on the "Home" page and scroll down to find resolution.</span></span>  <span data-ttu-id="50bae-146">试试800x600。</span><span class="sxs-lookup"><span data-stu-id="50bae-146">Try 800x600.</span></span>
1. <span data-ttu-id="50bae-147">如果这仍不能解决问题，则可能是由于从不将设备连接到外部显示器而产生的问题。</span><span class="sxs-lookup"><span data-stu-id="50bae-147">If this still doesn't fix your issue, you may have an issue that stems from never connecting your device to an external display.</span></span>
    <span data-ttu-id="50bae-148">这将导致设备将自身视为纯粹无外设。</span><span class="sxs-lookup"><span data-stu-id="50bae-148">This will cause the device to think of itself as purely headless.</span></span>  <span data-ttu-id="50bae-149">解决方法：</span><span class="sxs-lookup"><span data-stu-id="50bae-149">To fix this:</span></span>
    * <span data-ttu-id="50bae-150">弹出 MicroSD 卡，并将其放入计算机</span><span class="sxs-lookup"><span data-stu-id="50bae-150">Eject the MicroSD Card, and put into your computer</span></span>
    * <span data-ttu-id="50bae-151">编辑 `<MicroSD card drive>:\config.txt`</span><span class="sxs-lookup"><span data-stu-id="50bae-151">Edit the `<MicroSD card drive>:\config.txt`</span></span>
    * <span data-ttu-id="50bae-152">添加以下行：</span><span class="sxs-lookup"><span data-stu-id="50bae-152">Add the following lines:</span></span>
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
