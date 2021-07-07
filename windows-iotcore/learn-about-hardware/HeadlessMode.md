---
title: 有外设设备和无外设设备
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何为设备Windows头模式或无头模式配置 IoT 核心。
keywords: windows iot， 屏幕， 头， 无头， UI
ms.openlocfilehash: 73168eae98747a13a6880de9a5ec581102dc859c
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228833"
---
# <a name="headed-and-headless-devices"></a><span data-ttu-id="d8e04-104">头设备和无头设备</span><span class="sxs-lookup"><span data-stu-id="d8e04-104">Headed and Headless devices</span></span>

<span data-ttu-id="d8e04-105">Windows 10 IoT 核心版可配置为有 *向模式或\*\*无头* 模式。</span><span class="sxs-lookup"><span data-stu-id="d8e04-105">Windows 10 IoT Core can be configured for either *headed* or *headless* mode.</span></span> 

## <a name="headed-mode"></a><span data-ttu-id="d8e04-106">前向模式</span><span class="sxs-lookup"><span data-stu-id="d8e04-106">Headed mode</span></span>
<span data-ttu-id="d8e04-107">方向模式由 UI 的存在定义。</span><span class="sxs-lookup"><span data-stu-id="d8e04-107">Headed mode is defined by the presence of UI.</span></span> <span data-ttu-id="d8e04-108">在 *引导* 模式下，将在系统启动时启动单个 UI 应用，此外，StartupTasks (0) 。</span><span class="sxs-lookup"><span data-stu-id="d8e04-108">In *headed* mode, a single UI app will be launched at system boot and there can additionally be 0 or more "Background Apps" (StartupTasks).</span></span> 

## <a name="headless-mode"></a><span data-ttu-id="d8e04-109">无头模式</span><span class="sxs-lookup"><span data-stu-id="d8e04-109">Headless mode</span></span>
<span data-ttu-id="d8e04-110">无头模式没有 UI。</span><span class="sxs-lookup"><span data-stu-id="d8e04-110">Headless mode has no UI.</span></span>  <span data-ttu-id="d8e04-111">不需要 UI 功能的设备可以设置为无 *头* 模式。</span><span class="sxs-lookup"><span data-stu-id="d8e04-111">Devices that don't need UI functionality can be set to *headless* mode.</span></span> <span data-ttu-id="d8e04-112">UI 堆栈已禁用，UI 应用不会启动。</span><span class="sxs-lookup"><span data-stu-id="d8e04-112">The UI stack is disabled and UI apps will not launch.</span></span> <span data-ttu-id="d8e04-113">这会减少使用的系统资源量。</span><span class="sxs-lookup"><span data-stu-id="d8e04-113">This reduces the amount of system resources used.</span></span> <span data-ttu-id="d8e04-114">如果将监视器附加到设备，屏幕将为黑色。</span><span class="sxs-lookup"><span data-stu-id="d8e04-114">If you attach a monitor to your device, the screen will be black.</span></span>

> [!NOTE]
> <span data-ttu-id="d8e04-115">如果将设备置于无头模式，可以使用 Windows 10 IoT 核心版仪表板应用程序（如下所述）查找其 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d8e04-115">If you put your device into headless mode, then you can use the Windows 10 IoT Core Dashboard application, described below, to find its IP address.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="d8e04-116">更改模式</span><span class="sxs-lookup"><span data-stu-id="d8e04-116">Changing the mode</span></span>
<span data-ttu-id="d8e04-117">可以从会话或 SSH 会话修改设备的Windows PowerShell/无头状态。</span><span class="sxs-lookup"><span data-stu-id="d8e04-117">You can modify the headed/headless state of your device from a Windows PowerShell session or an SSH session.</span></span> <span data-ttu-id="d8e04-118">若要详细了解 PowerShell，请参阅 [PowerShell for IoT Core](../connect-your-device/PowerShell.md) 页。</span><span class="sxs-lookup"><span data-stu-id="d8e04-118">To learn more about PowerShell, see the [PowerShell for IoT Core](../connect-your-device/PowerShell.md) page.</span></span> <span data-ttu-id="d8e04-119">若要详细了解 SSH，请参阅 [SSH for IoT Core](../connect-your-device/SSH.md) 页。</span><span class="sxs-lookup"><span data-stu-id="d8e04-119">To learn more about SSH, see the [SSH for IoT Core](../connect-your-device/SSH.md) page.</span></span>

* <span data-ttu-id="d8e04-120">若要显示设备的当前状态，请使用 `setbootoption` 实用工具：</span><span class="sxs-lookup"><span data-stu-id="d8e04-120">To display the current state of your device, use the `setbootoption` utility:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* <span data-ttu-id="d8e04-121">若要修改设备的状态以启用无头模式，请通过 `setbootoption` arg 使用 `headless` 实用工具：</span><span class="sxs-lookup"><span data-stu-id="d8e04-121">To modify the state of your device to enable headless mode, use the `setbootoption` utility with the `headless` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* <span data-ttu-id="d8e04-122">若要修改设备的状态以启用前向模式，请通过 `setbootoption` arg 使用 `headed` 实用工具：</span><span class="sxs-lookup"><span data-stu-id="d8e04-122">To modify the state of your device to enable headed mode, use the `setbootoption` utility with the `headed` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a><span data-ttu-id="d8e04-123">查找无头设备</span><span class="sxs-lookup"><span data-stu-id="d8e04-123">Finding your headless device</span></span>

<span data-ttu-id="d8e04-124">可以使用无头模式发现采用无头模式的 IoT 核心 **Windows 10 IoT 核心版仪表板应用程序。**</span><span class="sxs-lookup"><span data-stu-id="d8e04-124">An IoT Core device that is in headless mode can be discovered using the **Windows 10 IoT Core Dashboard** application.</span></span>  <span data-ttu-id="d8e04-125">若要下载IoT 仪表板，请参阅 [下载](https://go.microsoft.com/fwlink/?LinkID=708576) 页。</span><span class="sxs-lookup"><span data-stu-id="d8e04-125">To download the IoT Dashboard, see the [Downloads](https://go.microsoft.com/fwlink/?LinkID=708576) page.</span></span>
<span data-ttu-id="d8e04-126">运行时，应用程序侦听来自本地网络上任何 IoT 核心设备的 ping，并显示设备信息，例如名称、IP 地址等。</span><span class="sxs-lookup"><span data-stu-id="d8e04-126">When running, the application listens for pings from any IoT Core devices on the local network and displays device information such as the name, IP address, and more.</span></span>

![Windows 10 IoT 核心版仪表板](../media/HeadlessMode/selectDevice.png)
