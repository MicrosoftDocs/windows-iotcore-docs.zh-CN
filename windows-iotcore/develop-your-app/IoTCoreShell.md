---
title: IoT Shell 概述
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何利用 IoT 外壳程序，以在设备上的导航之间导航。
keywords: windows iot，IoT core 命令行程序、 应用程序、 前台应用程序、 后台应用程序
ms.openlocfilehash: 74d8406036aa18dc5f8dcaa871e116eb7f8ec29b
ms.sourcegitcommit: beed912a2266d6dbc06a8a26b85ff49f1feffd69
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2019
ms.locfileid: "67316632"
---
# <a name="iot-shell-overview"></a><span data-ttu-id="bf547-104">IoT Shell 概述</span><span class="sxs-lookup"><span data-stu-id="bf547-104">IoT Shell Overview</span></span>

<span data-ttu-id="bf547-105">本文档介绍 IoT Shell、 前景色和背景的应用程序，以及如何在设备上这些应用程序之间浏览。</span><span class="sxs-lookup"><span data-stu-id="bf547-105">This document covers the IoT Shell, foreground and background applications, and how to navigate between these applications on your device.</span></span>

## <a name="iot-shell-foreground-and-background-apps"></a><span data-ttu-id="bf547-106">IoT Shell、 前景和背景应用</span><span class="sxs-lookup"><span data-stu-id="bf547-106">IoT Shell, Foreground, and Background Apps</span></span>

<span data-ttu-id="bf547-107">IoT Core 设备运行 IoT Shell。</span><span class="sxs-lookup"><span data-stu-id="bf547-107">Your IoT Core device runs the IoT Shell.</span></span> <span data-ttu-id="bf547-108">它有许多职责，但它主要工作是确保已注册的启动应用的启动。</span><span class="sxs-lookup"><span data-stu-id="bf547-108">It has many responsibilities, but its primary job is to make sure registered startup apps are launched.</span></span> <span data-ttu-id="bf547-109">它有两种模式：主和无外设。</span><span class="sxs-lookup"><span data-stu-id="bf547-109">It has two modes: Headed and Headless.</span></span> <span data-ttu-id="bf547-110">在 Headed 模式下，IoT 命令行程序将启动一个单个已注册的启动应用，它将显示其 UI 在全屏幕模式 （也称为 Headed 应用）。</span><span class="sxs-lookup"><span data-stu-id="bf547-110">In Headed mode, the IoT Shell will launch a single registered startup app that will show its UI in full screen (also known as a Headed app).</span></span> <span data-ttu-id="bf547-111">主的模式假定你已连接的屏幕，并显示 UI。</span><span class="sxs-lookup"><span data-stu-id="bf547-111">Headed mode assumes you have a screen connected and shows UI.</span></span> <span data-ttu-id="bf547-112">在无外设模式下 (详细信息中所述[此处](../learn-about-hardware/HeadlessMode.md))，没有用户界面; IoT Shell 启动后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf547-112">In Headless mode (explained in detail [here](../learn-about-hardware/HeadlessMode.md)), there is no UI; the IoT Shell launches background applications only.</span></span>

<span data-ttu-id="bf547-113">下面是前景色和背景的应用程序之间的主要区别：</span><span class="sxs-lookup"><span data-stu-id="bf547-113">Here are the main differences between foreground and background applications:</span></span>

- <span data-ttu-id="bf547-114">**前台应用程序**具有用户界面。</span><span class="sxs-lookup"><span data-stu-id="bf547-114">**Foreground applications** have a UI.</span></span> <span data-ttu-id="bf547-115">其中一种在启动时在设备处于主模式启动。</span><span class="sxs-lookup"><span data-stu-id="bf547-115">One of these is launched at startup when the device is in headed mode.</span></span> <span data-ttu-id="bf547-116">在设备上注册所有前台应用程序和用户可以在设备操作期间的前台应用程序之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="bf547-116">All foreground apps are registered on the device and the user can switch between foreground apps during device operation.</span></span>

- <span data-ttu-id="bf547-117">**后台应用程序**不具有 UI，并关闭 UI 堆栈，因此将保存设备资源。</span><span class="sxs-lookup"><span data-stu-id="bf547-117">**Background applications** have no UI and thus save device resources by turning off the UI stack.</span></span> <span data-ttu-id="bf547-118">后台应用程序通常从启动连续运行，并通常用于监视设备。</span><span class="sxs-lookup"><span data-stu-id="bf547-118">Background applications often run continuously from startup and are often used to monitor the device.</span></span>

## <a name="switching-between-apps-with-a-home-app"></a><span data-ttu-id="bf547-119">与主应用程序的应用之间切换</span><span class="sxs-lookup"><span data-stu-id="bf547-119">Switching between apps with a Home App</span></span>

<span data-ttu-id="bf547-120">目前，启动应用，可创建适用于 Windows 10 IoT Core，可用于不同前台应用程序间切换主应用。</span><span class="sxs-lookup"><span data-stu-id="bf547-120">At the moment, the Startup App allows you to create a home app for Windows 10 IoT Core, which allows you to switch between different foreground applications.</span></span> 

<span data-ttu-id="bf547-121">**IoT 启动应用程序**([示例](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp)表示一个简单的启动应用，它列出在设备上已安装的应用，然后启动一个使用 PackageManager Api。</span><span class="sxs-lookup"><span data-stu-id="bf547-121">The **IoT Startup App** ([sample](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp) represents a simple startup app that lists the installed apps on your device, then launches one using the PackageManager APIs.</span></span>

## <a name="switching-between-apps-with-hid-injection-keys"></a><span data-ttu-id="bf547-122">应用与 HID 注入密钥之间切换</span><span class="sxs-lookup"><span data-stu-id="bf547-122">Switching between apps with HID Injection Keys</span></span>

<span data-ttu-id="bf547-123">以下说明介绍如何打开热键支持通过对注册表项。</span><span class="sxs-lookup"><span data-stu-id="bf547-123">The below instructions show you how to turn on Hotkey support through entries to the registry.</span></span> <span data-ttu-id="bf547-124">如果你要构建自己的映像，并想要支持如下而无需访问注册表的热键 （主页、 以前的应用和下一个应用程序），则可以为你处理这些步骤的可选功能包。</span><span class="sxs-lookup"><span data-stu-id="bf547-124">If you are building your own image and want to support the below hotkeys (Home, previous app, and next app) without needing to access the registry, you can include an optional feature package that handles these steps for you.</span></span>

<span data-ttu-id="bf547-125">调用要查找的功能包：**Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab**和功能被称为**IOT_SHELL_HOTKEY_SUPPORT**。</span><span class="sxs-lookup"><span data-stu-id="bf547-125">The feature package to look for is called: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** and the feature is called **IOT_SHELL_HOTKEY_SUPPORT**.</span></span> <span data-ttu-id="bf547-126">请参阅[Settings.HotKey 示例包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml)有关的示例。</span><span class="sxs-lookup"><span data-stu-id="bf547-126">See the [Settings.HotKey sample package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) for an example.</span></span>

<span data-ttu-id="bf547-127">此文档的其余部分介绍如何手动实现此功能。</span><span class="sxs-lookup"><span data-stu-id="bf547-127">The rest of this document covers how to implement this feature manually.</span></span>

### <a name="return-home"></a><span data-ttu-id="bf547-128">返回主页</span><span class="sxs-lookup"><span data-stu-id="bf547-128">Return Home</span></span>

<span data-ttu-id="bf547-129">借助 Windows 10 IoT 周年更新 (1607)，IoT Shell 支持到前台，将默认应用程序窗口，运行时，另一个应用程序是通过按"主页转"键，它设置为版本的键盘上的 Windows 按钮。</span><span class="sxs-lookup"><span data-stu-id="bf547-129">With the Windows 10 IoT Anniversary Update (1607), the IoT Shell supports bringing the default application window to the foreground when another application is running by pressing the "GO HOME" key, which is set to the release of the Windows Button on a keyboard.</span></span> <span data-ttu-id="bf547-130">如果没有 IoT 设备上有键盘并需要将注入通过低级别的键盘事件[HID 注入](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection)，或者如果只是想要重新映射到不同的密钥应用程序中的"转到主页"功能，您可以调整中的密钥值注册表。</span><span class="sxs-lookup"><span data-stu-id="bf547-130">If you don't have a keyboard on your IoT Device and need to inject low-level keyboard events through [HID Injection](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), or if you just want to re-map the "GO HOME" functionality to a different key in your app, you can adjust the key value in the registry.</span></span> <span data-ttu-id="bf547-131">例如，若要启用按转义符键 (0x1B) 到"主页转"，请在注册表中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="bf547-131">For example, to enable pressing the ESCAPE key (0x1B) to "GO HOME", enter the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

<span data-ttu-id="bf547-132">为 REG 文件，这种情况，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf547-132">As a REG file, this looks as follows:</span></span>

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a><span data-ttu-id="bf547-133">应用程序之间切换</span><span class="sxs-lookup"><span data-stu-id="bf547-133">Switch Between Apps</span></span>

<span data-ttu-id="bf547-134">或者，如果你想要在前台应用之间切换，您可以将设置 Alt Tab （下一步应用） 和 Shift Alt Tab （以前的应用） 功能通过在注册表中输入以下命令在映像中：</span><span class="sxs-lookup"><span data-stu-id="bf547-134">Alternatively, if you want to switch between your foreground apps, you can set up Alt-Tab (next app) and Shift-Alt-Tab (previous app) functionality in your image by entering the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

<span data-ttu-id="bf547-135">为 REG 文件，这种情况，如下所示： ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``</span><span class="sxs-lookup"><span data-stu-id="bf547-135">As a REG file, this looks as follows: ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``</span></span>

### <a name="bit-translation"></a><span data-ttu-id="bf547-136">位转换</span><span class="sxs-lookup"><span data-stu-id="bf547-136">Bit Translation</span></span>

<span data-ttu-id="bf547-137">上面的 REG 文件条目解码从左到右，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf547-137">The above REG file entries decode left to right as follows:</span></span>

- <span data-ttu-id="bf547-138">位 0 到 15:虚拟键代码 (即 1B，00 转义)。</span><span class="sxs-lookup"><span data-stu-id="bf547-138">Bits 0-15: Virtual Key Code (i.e. 1B,00 for ESCAPE).</span></span> <span data-ttu-id="bf547-139">请参阅[虚拟键代码](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx)键代码的值的完整列表</span><span class="sxs-lookup"><span data-stu-id="bf547-139">See [Virtual Key Code](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) for the complete list of key code values</span></span>
- <span data-ttu-id="bf547-140">Bits 16-19:修改键。</span><span class="sxs-lookup"><span data-stu-id="bf547-140">Bits 16-19: Modifier Key.</span></span> <span data-ttu-id="bf547-141">0x0 = 无修饰符 0x1 = ALT，0x2 = CTRL 和 0x4 = SHIFT。</span><span class="sxs-lookup"><span data-stu-id="bf547-141">0x0 = No Modifier, 0x1 = ALT, 0x2 = CTRL, and 0x4 = SHIFT.</span></span> <span data-ttu-id="bf547-142">组合密钥相加值 （即 ALT + SHIFT 是 0x5）</span><span class="sxs-lookup"><span data-stu-id="bf547-142">Combining keys adds the values together (i.e. ALT+SHIFT is 0x5)</span></span>
- <span data-ttu-id="bf547-143">Bits 20-47:保留供将来使用;必须为 0</span><span class="sxs-lookup"><span data-stu-id="bf547-143">Bits 20-47: Reserved for future use; must be 0</span></span>
- <span data-ttu-id="bf547-144">Bits 48 62:操作</span><span class="sxs-lookup"><span data-stu-id="bf547-144">Bits 48-62:  Action</span></span>
    - <span data-ttu-id="bf547-145">0 = 主页</span><span class="sxs-lookup"><span data-stu-id="bf547-145">0 = Home</span></span>
    - <span data-ttu-id="bf547-146">1 = 上一个视图 （可能无法在未来版本中）</span><span class="sxs-lookup"><span data-stu-id="bf547-146">1 = Previous View (may not work in future releases)</span></span>
    - <span data-ttu-id="bf547-147">2 = 下一个视图 （可能无法在未来版本中）</span><span class="sxs-lookup"><span data-stu-id="bf547-147">2 = Next View (may not work in future releases)</span></span>
- <span data-ttu-id="bf547-148">第 63 位：保留;必须为 0</span><span class="sxs-lookup"><span data-stu-id="bf547-148">Bit 63: Reserved; must be 0</span></span>

