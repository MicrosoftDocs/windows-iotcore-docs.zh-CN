---
title: 有外设设备和无外设设备
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何为设备配置 Windows IoT Core，使其适用于 "头" 或 "无外设" 模式。
keywords: windows iot，屏幕，头，无外设，UI
ms.openlocfilehash: 9cac0198e58d2ace6bd751c25d97dd964e4db5a9
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655813"
---
# <a name="headed-and-headless-devices"></a><span data-ttu-id="d157c-104">头和无外设设备</span><span class="sxs-lookup"><span data-stu-id="d157c-104">Headed and Headless devices</span></span>

<span data-ttu-id="d157c-105">可以为 " *头* " 或 "无 *外设* " 模式配置 Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="d157c-105">Windows 10 IoT Core can be configured for either *headed* or *headless* mode.</span></span> 

## <a name="headed-mode"></a><span data-ttu-id="d157c-106">头模式</span><span class="sxs-lookup"><span data-stu-id="d157c-106">Headed mode</span></span>
<span data-ttu-id="d157c-107">头模式由 UI 的状态定义。</span><span class="sxs-lookup"><span data-stu-id="d157c-107">Headed mode is defined by the presence of UI.</span></span> <span data-ttu-id="d157c-108">在 *"方向" 模式下* ，将在系统启动时启动单个 UI 应用，还可以有0个或更多 "后台应用" (StartupTasks) 。</span><span class="sxs-lookup"><span data-stu-id="d157c-108">In *headed* mode, a single UI app will be launched at system boot and there can additionally be 0 or more "Background Apps" (StartupTasks).</span></span> 

## <a name="headless-mode"></a><span data-ttu-id="d157c-109">无外设模式</span><span class="sxs-lookup"><span data-stu-id="d157c-109">Headless mode</span></span>
<span data-ttu-id="d157c-110">无外设模式没有 UI。</span><span class="sxs-lookup"><span data-stu-id="d157c-110">Headless mode has no UI.</span></span>  <span data-ttu-id="d157c-111">不需要 UI 功能的设备可以设置为无 *外设* 模式。</span><span class="sxs-lookup"><span data-stu-id="d157c-111">Devices that don't need UI functionality can be set to *headless* mode.</span></span> <span data-ttu-id="d157c-112">UI 堆栈处于禁用状态，UI 应用将无法启动。</span><span class="sxs-lookup"><span data-stu-id="d157c-112">The UI stack is disabled and UI apps will not launch.</span></span> <span data-ttu-id="d157c-113">这会减少使用的系统资源量。</span><span class="sxs-lookup"><span data-stu-id="d157c-113">This reduces the amount of system resources used.</span></span> <span data-ttu-id="d157c-114">如果将监视器连接到设备，屏幕将为黑色。</span><span class="sxs-lookup"><span data-stu-id="d157c-114">If you attach a monitor to your device, the screen will be black.</span></span>

> [!NOTE]
> <span data-ttu-id="d157c-115">如果将设备置于无外设模式，则可以使用下面所述的 Windows 10 IoT Core 仪表板应用程序来查找其 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d157c-115">If you put your device into headless mode, then you can use the Windows 10 IoT Core Dashboard application, described below, to find its IP address.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="d157c-116">更改模式</span><span class="sxs-lookup"><span data-stu-id="d157c-116">Changing the mode</span></span>
<span data-ttu-id="d157c-117">你可以从 Windows PowerShell 会话或 SSH 会话中修改设备的头/无外设状态。</span><span class="sxs-lookup"><span data-stu-id="d157c-117">You can modify the headed/headless state of your device from a Windows PowerShell session or an SSH session.</span></span> <span data-ttu-id="d157c-118">若要了解有关 PowerShell 的详细信息，请参阅 [powershell For IoT Core](../connect-your-device/PowerShell.md) 页。</span><span class="sxs-lookup"><span data-stu-id="d157c-118">To learn more about PowerShell, see the [PowerShell for IoT Core](../connect-your-device/PowerShell.md) page.</span></span> <span data-ttu-id="d157c-119">若要了解有关 SSH 的详细信息，请参阅 [ssh 的 IoT 核心](../connect-your-device/SSH.md) 页面。</span><span class="sxs-lookup"><span data-stu-id="d157c-119">To learn more about SSH, see the [SSH for IoT Core](../connect-your-device/SSH.md) page.</span></span>

* <span data-ttu-id="d157c-120">若要显示设备的当前状态，请使用 `setbootoption` 实用工具：</span><span class="sxs-lookup"><span data-stu-id="d157c-120">To display the current state of your device, use the `setbootoption` utility:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* <span data-ttu-id="d157c-121">若要修改设备的状态以启用无外设模式，请使用 `setbootoption` 带有 arg 的实用工具 `headless` ：</span><span class="sxs-lookup"><span data-stu-id="d157c-121">To modify the state of your device to enable headless mode, use the `setbootoption` utility with the `headless` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* <span data-ttu-id="d157c-122">若要将设备的状态修改为启用方向模式，请使用 `setbootoption` 带有 arg 的实用工具 `headed` ：</span><span class="sxs-lookup"><span data-stu-id="d157c-122">To modify the state of your device to enable headed mode, use the `setbootoption` utility with the `headed` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a><span data-ttu-id="d157c-123">查找无外设设备</span><span class="sxs-lookup"><span data-stu-id="d157c-123">Finding your headless device</span></span>

<span data-ttu-id="d157c-124">在无外设模式下的 IoT 核心设备可以使用 **Windows 10 IoT Core 仪表板** 应用程序来发现。</span><span class="sxs-lookup"><span data-stu-id="d157c-124">An IoT Core device that is in headless mode can be discovered using the **Windows 10 IoT Core Dashboard** application.</span></span>  <span data-ttu-id="d157c-125">若要下载 IoT 面板，请参阅 [下载](https://go.microsoft.com/fwlink/?LinkID=708576) 页。</span><span class="sxs-lookup"><span data-stu-id="d157c-125">To download the IoT Dashboard, see the [Downloads](https://go.microsoft.com/fwlink/?LinkID=708576) page.</span></span>
<span data-ttu-id="d157c-126">运行时，应用程序会侦听来自本地网络上的任何 IoT 核心设备的 ping，并显示设备信息，如名称、IP 地址等。</span><span class="sxs-lookup"><span data-stu-id="d157c-126">When running, the application listens for pings from any IoT Core devices on the local network and displays device information such as the name, IP address, and more.</span></span>

![Windows 10 IoT 核心版仪表板](../media/HeadlessMode/selectDevice.png)
