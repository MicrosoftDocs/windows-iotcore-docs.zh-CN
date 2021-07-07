---
title: IoT 外壳概述
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何利用 IoT Shell 在设备上的导航之间导航。
keywords: windows iot，IoT core shell，应用程序，前台应用程序，后台应用程序
ms.openlocfilehash: 38a55e3545116bbddb77c2ec6a7f4de14efc1d0a
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229844"
---
# <a name="iot-shell-overview"></a><span data-ttu-id="2002c-104">IoT 外壳概述</span><span class="sxs-lookup"><span data-stu-id="2002c-104">IoT Shell Overview</span></span>

<span data-ttu-id="2002c-105">本文档介绍 IoT Shell、前台和后台应用程序，以及如何在设备上的这些应用程序之间导航。</span><span class="sxs-lookup"><span data-stu-id="2002c-105">This document covers the IoT Shell, foreground and background applications, and how to navigate between these applications on your device.</span></span>

## <a name="iot-shell-foreground-and-background-apps"></a><span data-ttu-id="2002c-106">IoT Shell、前台和后台应用</span><span class="sxs-lookup"><span data-stu-id="2002c-106">IoT Shell, Foreground, and Background Apps</span></span>

<span data-ttu-id="2002c-107">IoT 核心设备运行 IoT Shell。</span><span class="sxs-lookup"><span data-stu-id="2002c-107">Your IoT Core device runs the IoT Shell.</span></span> <span data-ttu-id="2002c-108">它具有许多责任，但其主要任务是确保已启动注册的启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="2002c-108">It has many responsibilities, but its primary job is to make sure registered startup apps are launched.</span></span> <span data-ttu-id="2002c-109">它有两种模式：头和无外设。</span><span class="sxs-lookup"><span data-stu-id="2002c-109">It has two modes: Headed and Headless.</span></span> <span data-ttu-id="2002c-110">在头模式下，IoT Shell 将启动一个已注册的启动应用程序，该应用程序将以全屏方式显示其 UI (也称为应用) 。</span><span class="sxs-lookup"><span data-stu-id="2002c-110">In Headed mode, the IoT Shell will launch a single registered startup app that will show its UI in full screen (also known as a Headed app).</span></span> <span data-ttu-id="2002c-111">向模式假设已连接屏幕并显示 UI。</span><span class="sxs-lookup"><span data-stu-id="2002c-111">Headed mode assumes you have a screen connected and shows UI.</span></span> <span data-ttu-id="2002c-112">在无外设模式下 (稍后会详细 [介绍) ，](../learn-about-hardware/HeadlessMode.md) 无 UI;IoT Shell 仅启动后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="2002c-112">In Headless mode (explained in detail [here](../learn-about-hardware/HeadlessMode.md)), there is no UI; the IoT Shell launches background applications only.</span></span>

<span data-ttu-id="2002c-113">前台和后台应用程序的主要区别如下：</span><span class="sxs-lookup"><span data-stu-id="2002c-113">Here are the main differences between foreground and background applications:</span></span>

- <span data-ttu-id="2002c-114">**前台应用程序** 有一个 UI。</span><span class="sxs-lookup"><span data-stu-id="2002c-114">**Foreground applications** have a UI.</span></span> <span data-ttu-id="2002c-115">当设备处于头部模式时，将在启动时启动其中的一个。</span><span class="sxs-lookup"><span data-stu-id="2002c-115">One of these is launched at startup when the device is in headed mode.</span></span> <span data-ttu-id="2002c-116">所有前台应用都注册到设备上，用户可以在设备操作过程中在前台应用之间切换。</span><span class="sxs-lookup"><span data-stu-id="2002c-116">All foreground apps are registered on the device and the user can switch between foreground apps during device operation.</span></span>

- <span data-ttu-id="2002c-117">**后台应用程序** 没有 ui，因此可以通过关闭 UI 堆栈来保存设备资源。</span><span class="sxs-lookup"><span data-stu-id="2002c-117">**Background applications** have no UI and thus save device resources by turning off the UI stack.</span></span> <span data-ttu-id="2002c-118">后台应用程序通常在启动时连续运行，并经常用于监视设备。</span><span class="sxs-lookup"><span data-stu-id="2002c-118">Background applications often run continuously from startup and are often used to monitor the device.</span></span>

## <a name="switching-between-apps-with-a-home-app"></a><span data-ttu-id="2002c-119">使用 Home 应用在应用之间切换</span><span class="sxs-lookup"><span data-stu-id="2002c-119">Switching between apps with a Home App</span></span>

<span data-ttu-id="2002c-120">目前，启动应用程序允许您为 Windows 10 IoT 核心版创建 home 应用程序，使您可以在不同的前台应用程序之间切换。</span><span class="sxs-lookup"><span data-stu-id="2002c-120">At the moment, the Startup App allows you to create a home app for Windows 10 IoT Core, which allows you to switch between different foreground applications.</span></span> 

<span data-ttu-id="2002c-121">**IoT 启动应用** ([示例](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp)表示一个简单的启动应用程序，该应用程序在设备上列出已安装的应用，然后使用 PackageManager api 启动一个应用。</span><span class="sxs-lookup"><span data-stu-id="2002c-121">The **IoT Startup App** ([sample](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp) represents a simple startup app that lists the installed apps on your device, then launches one using the PackageManager APIs.</span></span>

## <a name="switching-between-apps-with-hid-injection-keys"></a><span data-ttu-id="2002c-122">在具有 HID 注入密钥的应用之间切换</span><span class="sxs-lookup"><span data-stu-id="2002c-122">Switching between apps with HID Injection Keys</span></span>

<span data-ttu-id="2002c-123">以下说明介绍了如何通过注册表项打开热键支持。</span><span class="sxs-lookup"><span data-stu-id="2002c-123">The below instructions show you how to turn on Hotkey support through entries to the registry.</span></span> <span data-ttu-id="2002c-124">如果你正在构建自己的映像，并且想要支持以下热键 (Home、previous 应用和下一应用) 无需访问注册表，你可以包含一个可选功能包来处理这些步骤。</span><span class="sxs-lookup"><span data-stu-id="2002c-124">If you are building your own image and want to support the below hotkeys (Home, previous app, and next app) without needing to access the registry, you can include an optional feature package that handles these steps for you.</span></span>

<span data-ttu-id="2002c-125">要查找的功能包称为： **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** ，该功能 **IOT_SHELL_HOTKEY_SUPPORT**。</span><span class="sxs-lookup"><span data-stu-id="2002c-125">The feature package to look for is called: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** and the feature is called **IOT_SHELL_HOTKEY_SUPPORT**.</span></span> <span data-ttu-id="2002c-126">请参阅[设置。示例的热键示例包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml)。</span><span class="sxs-lookup"><span data-stu-id="2002c-126">See the [Settings.HotKey sample package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) for an example.</span></span>

<span data-ttu-id="2002c-127">本文档的其余部分介绍了如何手动实现此功能。</span><span class="sxs-lookup"><span data-stu-id="2002c-127">The rest of this document covers how to implement this feature manually.</span></span>

### <a name="return-home"></a><span data-ttu-id="2002c-128">返回主页</span><span class="sxs-lookup"><span data-stu-id="2002c-128">Return Home</span></span>

<span data-ttu-id="2002c-129">使用 Windows 10 iot 周年更新 (1607) ，iot Shell 支持在运行另一个应用程序时将默认应用程序窗口设置为前台，方法是将设置为键盘上的 Windows 按钮的版本。</span><span class="sxs-lookup"><span data-stu-id="2002c-129">With the Windows 10 IoT Anniversary Update (1607), the IoT Shell supports bringing the default application window to the foreground when another application is running by pressing the "GO HOME" key, which is set to the release of the Windows Button on a keyboard.</span></span> <span data-ttu-id="2002c-130">如果 IoT 设备上没有键盘，并且需要通过 [HID 注入](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection)注入低级键盘事件，或者只是想要在应用程序中将 "中转 HOME" 功能重新映射到其他密钥，则可以在注册表中调整密钥值。</span><span class="sxs-lookup"><span data-stu-id="2002c-130">If you don't have a keyboard on your IoT Device and need to inject low-level keyboard events through [HID Injection](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), or if you just want to re-map the "GO HOME" functionality to a different key in your app, you can adjust the key value in the registry.</span></span> <span data-ttu-id="2002c-131">例如，若要启用 (0x1B) 中按 ESC 键，请在注册表中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="2002c-131">For example, to enable pressing the ESCAPE key (0x1B) to "GO HOME", enter the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

<span data-ttu-id="2002c-132">作为 REG 文件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2002c-132">As a REG file, this looks as follows:</span></span>

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a><span data-ttu-id="2002c-133">在应用之间切换</span><span class="sxs-lookup"><span data-stu-id="2002c-133">Switch Between Apps</span></span>

<span data-ttu-id="2002c-134">或者，如果你想要在前台应用之间切换，则可以通过在注册表中输入以下命令来设置 Alt-Tab (下一个应用) 和移动-Alt-Tab (上一个应用) 功能。</span><span class="sxs-lookup"><span data-stu-id="2002c-134">Alternatively, if you want to switch between your foreground apps, you can set up Alt-Tab (next app) and Shift-Alt-Tab (previous app) functionality in your image by entering the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

<span data-ttu-id="2002c-135">作为 REG 文件，如下所示： ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``</span><span class="sxs-lookup"><span data-stu-id="2002c-135">As a REG file, this looks as follows: ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``</span></span>

### <a name="bit-translation"></a><span data-ttu-id="2002c-136">位转换</span><span class="sxs-lookup"><span data-stu-id="2002c-136">Bit Translation</span></span>

<span data-ttu-id="2002c-137">上述 REG 文件项从左向右解码，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2002c-137">The above REG file entries decode left to right as follows:</span></span>

- <span data-ttu-id="2002c-138">Bits 0-15：对于转义) ，虚拟键代码 (例如1B、00。</span><span class="sxs-lookup"><span data-stu-id="2002c-138">Bits 0-15: Virtual Key Code (i.e. 1B,00 for ESCAPE).</span></span> <span data-ttu-id="2002c-139">有关关键代码值的完整列表，请参阅[虚拟键代码](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="2002c-139">See [Virtual Key Code](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) for the complete list of key code values</span></span>
- <span data-ttu-id="2002c-140">Bits 16-19：修改键。</span><span class="sxs-lookup"><span data-stu-id="2002c-140">Bits 16-19: Modifier Key.</span></span> <span data-ttu-id="2002c-141">0x0 = No 修饰符，0x1 = ALT，0x2 = CTRL，0x4 = SHIFT。</span><span class="sxs-lookup"><span data-stu-id="2002c-141">0x0 = No Modifier, 0x1 = ALT, 0x2 = CTRL, and 0x4 = SHIFT.</span></span> <span data-ttu-id="2002c-142">组合键将值相加 (即 ALT + SHIFT 为 0x5) </span><span class="sxs-lookup"><span data-stu-id="2002c-142">Combining keys adds the values together (i.e. ALT+SHIFT is 0x5)</span></span>
- <span data-ttu-id="2002c-143">Bits 20-47：保留供将来使用;必须为0</span><span class="sxs-lookup"><span data-stu-id="2002c-143">Bits 20-47: Reserved for future use; must be 0</span></span>
- <span data-ttu-id="2002c-144">Bits 48-62：操作</span><span class="sxs-lookup"><span data-stu-id="2002c-144">Bits 48-62:  Action</span></span>
    - <span data-ttu-id="2002c-145">0 = Home</span><span class="sxs-lookup"><span data-stu-id="2002c-145">0 = Home</span></span>
    - <span data-ttu-id="2002c-146">1 = 上一个视图 (在未来版本中可能不起作用) </span><span class="sxs-lookup"><span data-stu-id="2002c-146">1 = Previous View (may not work in future releases)</span></span>
    - <span data-ttu-id="2002c-147">2 = 下一个视图 (在未来版本中可能不起作用) </span><span class="sxs-lookup"><span data-stu-id="2002c-147">2 = Next View (may not work in future releases)</span></span>
- <span data-ttu-id="2002c-148">位63：保留;必须为0</span><span class="sxs-lookup"><span data-stu-id="2002c-148">Bit 63: Reserved; must be 0</span></span>

