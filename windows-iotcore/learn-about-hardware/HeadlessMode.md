---
title: 主和无外设设备
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何为设备的主或无外设模式下配置 Windows IoT Core。
keywords: windows iot、 屏幕，讨论的问题，无外设，UI
ms.openlocfilehash: 8ac0d7e06477836aa080af1b7556b054957d0cac
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510868"
---
# <a name="headed-and-headless-devices"></a><span data-ttu-id="e6b0f-104">主和无外设设备</span><span class="sxs-lookup"><span data-stu-id="e6b0f-104">Headed and Headless devices</span></span>

<span data-ttu-id="e6b0f-105">Windows 10 IoT 核心版可以配置其中任何*讲述的内容*或*无外设*模式。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-105">Windows 10 IoT Core can be configured for either *headed* or *headless* mode.</span></span> 

## <a name="headed-mode"></a><span data-ttu-id="e6b0f-106">主的模式</span><span class="sxs-lookup"><span data-stu-id="e6b0f-106">Headed mode</span></span>
<span data-ttu-id="e6b0f-107">主的模式被定义的 UI 存在。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-107">Headed mode is defined by the presence of UI.</span></span> <span data-ttu-id="e6b0f-108">在中*讲述的内容*模式单个 UI 应用程序将在系统引导启动和另外有可以为 0 或更多"后台应用程序"(StartupTasks)。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-108">In *headed* mode a single UI app will be launched at system boot and there can additionally be 0 or more "Background Apps" (StartupTasks).</span></span> 

## <a name="headless-mode"></a><span data-ttu-id="e6b0f-109">无外设模式</span><span class="sxs-lookup"><span data-stu-id="e6b0f-109">Headless mode</span></span>
<span data-ttu-id="e6b0f-110">无外设模式具有任何 UI。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-110">Headless mode has no UI.</span></span>  <span data-ttu-id="e6b0f-111">无需 UI 功能的设备可设置为*无外设*模式。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-111">Devices that don't need UI functionality can be set to *headless* mode.</span></span> <span data-ttu-id="e6b0f-112">禁用 UI 堆栈，并且将不启动 UI 应用。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-112">The UI stack is disabled and UI apps will not launch.</span></span> <span data-ttu-id="e6b0f-113">这将减少使用的系统资源量。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-113">This reduces the amount of system resources used.</span></span> <span data-ttu-id="e6b0f-114">如果将监视器附加到你的设备，屏幕将显示为黑色。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-114">If you attach a monitor to your device, the screen will be black.</span></span>

> [!NOTE]
> <span data-ttu-id="e6b0f-115">如果你的设备将进入无外设模式中，您可以使用 Windows 10 IoT 核心版仪表板应用程序，若要查找其 IP 地址，如下所述。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-115">If you put your device into headless mode, then you can use the Windows 10 IoT Core Dashboard application, described below, to find its IP address.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="e6b0f-116">更改模式</span><span class="sxs-lookup"><span data-stu-id="e6b0f-116">Changing the mode</span></span>
<span data-ttu-id="e6b0f-117">你可以修改你的设备在 Windows PowerShell 会话或 SSH 会话中讨论的问题/无外设状态。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-117">You can modify the headed/headless state of your device from a Windows PowerShell session or an SSH session.</span></span> <span data-ttu-id="e6b0f-118">若要了解有关 PowerShell 的详细信息，请参阅[适用于 IoT 核心版的 PowerShell](../connect-your-device/PowerShell.md)页。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-118">To learn more about PowerShell, see the [PowerShell for IoT Core](../connect-your-device/PowerShell.md) page.</span></span> <span data-ttu-id="e6b0f-119">若要了解有关 SSH 的详细信息，请参阅[IoT Core 的 SSH](../connect-your-device/SSH.md)页。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-119">To learn more about SSH, see the [SSH for IoT Core](../connect-your-device/SSH.md) page.</span></span>

* <span data-ttu-id="e6b0f-120">若要显示你的设备的当前状态，请使用`setbootoption`实用程序：</span><span class="sxs-lookup"><span data-stu-id="e6b0f-120">To display the current state of your device, use the `setbootoption` utility:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* <span data-ttu-id="e6b0f-121">若要修改设备的状态以启用无外设模式，请将 `setbootoption` 实用工具与 `headless` 参数结合使用：</span><span class="sxs-lookup"><span data-stu-id="e6b0f-121">To modify the state of your device to enable headless mode, use the `setbootoption` utility with the `headless` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* <span data-ttu-id="e6b0f-122">若要修改设备的状态以启用有外设模式，请将 `setbootoption` 实用工具与 `headed` 参数结合使用：</span><span class="sxs-lookup"><span data-stu-id="e6b0f-122">To modify the state of your device to enable headed mode, use the `setbootoption` utility with the `headed` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a><span data-ttu-id="e6b0f-123">查找无外设设备</span><span class="sxs-lookup"><span data-stu-id="e6b0f-123">Finding your headless device</span></span>

<span data-ttu-id="e6b0f-124">可以使用发现 IoT Core 设备是处于无外设模式下**Windows 10 IoT 核心版仪表板**应用程序。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-124">An IoT Core device that is in headless mode can be discovered using the **Windows 10 IoT Core Dashboard** application.</span></span>  <span data-ttu-id="e6b0f-125">若要下载 IoT 仪表板，请参阅[下载](http://go.microsoft.com/fwlink/?LinkID=708576)页。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-125">To download the IoT Dashboard, see the [Downloads](http://go.microsoft.com/fwlink/?LinkID=708576) page.</span></span>
<span data-ttu-id="e6b0f-126">运行时，应用程序侦听的 ping 中的任何 IoT Core 设备上的本地网络，并显示设备信息，例如名称、 IP 地址和的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e6b0f-126">When running, the application listens for pings from any IoT Core devices on the local network and displays device information such as the name, IP address, and more.</span></span>

![Windows 10 IoT 核心版仪表板](../media/HeadlessMode/selectDevice.png)
