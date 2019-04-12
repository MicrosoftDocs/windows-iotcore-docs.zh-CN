---
title: Windows 10 IoT 核心版的概述
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: 了解什么是 Windows 10 IoT 核心版，可以使用它做什么。
keywords: Windows 10 IoT Core，占用空间小、 无外设
ms.openlocfilehash: 1be159b685ffed30effbb2ae8abc80ded8edd879
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510617"
---
# <a name="windows-10-iot-core"></a><span data-ttu-id="49028-104">Windows 10 IoT 核心版</span><span class="sxs-lookup"><span data-stu-id="49028-104">Windows 10 IoT Core</span></span>

## <a name="what-is-windows-10-iot-core"></a><span data-ttu-id="49028-105">什么是 Windows 10 IoT 核心版？</span><span class="sxs-lookup"><span data-stu-id="49028-105">What is Windows 10 IoT Core?</span></span>
<span data-ttu-id="49028-106">Windows 10 IoT 核心版是针对同时 ARM 运行的较小设备使用或不带显示器和 x86/x64 设备优化的 Windows 10 版本。</span><span class="sxs-lookup"><span data-stu-id="49028-106">Windows 10 IoT Core is a version of Windows 10 that is optimized for smaller devices with or without a display that run on both ARM and x86/x64 devices.</span></span> <span data-ttu-id="49028-107">Windows IoT Core 文档提供有关连接、 管理、 更新、 保护你的设备和的详细信息。</span><span class="sxs-lookup"><span data-stu-id="49028-107">The Windows IoT Core documentation provides information on connecting, managing, updating, securing your devices, and more.</span></span> 

## <a name="getting-started"></a><span data-ttu-id="49028-108">即刻体验</span><span class="sxs-lookup"><span data-stu-id="49028-108">Getting started</span></span>
<span data-ttu-id="49028-109">若要开始使用 Windows 10 IoT 核心版，我们已创建[Windows 10 IoT Core Quickstarter](tutorials/Tutorials.md)以帮助您快速熟悉平台。</span><span class="sxs-lookup"><span data-stu-id="49028-109">To get started with Windows 10 IoT Core, we've created a [Windows 10 IoT Core Quickstarter](tutorials/Tutorials.md) to help you get familiar with the platform quickly.</span></span> 

<span data-ttu-id="49028-110">在这里，您可以继续通过开发自己的应用程序对平台进行试验或开始制定计划以将你的设备推向市场，或商业化你的设备。</span><span class="sxs-lookup"><span data-stu-id="49028-110">From there, you can continue to experiment with the platform by developing your own application or start making plans to bring your device to market, or commercialize your device.</span></span> <span data-ttu-id="49028-111">若要开始使用 commercializing，请参阅自带设备推向市场中的部分[入门的文章](https://docs.microsoft.com/windows/iot-core/getstarted)。</span><span class="sxs-lookup"><span data-stu-id="49028-111">To get started with commercializing, see the Bring a device to market section in the [Get started article](https://docs.microsoft.com/windows/iot-core/getstarted).</span></span>

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a><span data-ttu-id="49028-112">Windows 10 桌面版和 Windows 10 IoT 核心版之间的差异</span><span class="sxs-lookup"><span data-stu-id="49028-112">Differences between Windows 10 Desktop and Windows 10 IoT Core</span></span>

### <a name="different-features-available-on-desktop-and-iot-core"></a><span data-ttu-id="49028-113">可在桌面和 IoT Core 上的不同功能</span><span class="sxs-lookup"><span data-stu-id="49028-113">Different features available on Desktop and IoT Core</span></span>

* <span data-ttu-id="49028-114">收件箱 Cortana 之后的版本 1809 (17763) 不再可在 Windows 10 IoT 核心版上。</span><span class="sxs-lookup"><span data-stu-id="49028-114">Inbox Cortana is no longer available on Windows 10 IoT Core since version 1809 (17763).</span></span> <span data-ttu-id="49028-115">如果想要将具有语音功能的设备要快地进入市场，可以将 Cortana 支持集成到设备使用[Cortana 设备 SDK 的预览](https://developer.microsoft.com/en-us/cortana/devices)。</span><span class="sxs-lookup"><span data-stu-id="49028-115">If you are looking to bring a voice-enabled device to market quickly, you can integrate Cortana support into the device using the [preview of the Cortana Devices SDK](https://developer.microsoft.com/en-us/cortana/devices).</span></span>
* <span data-ttu-id="49028-116">[FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker)不支持在 Windows 10 IoT 核心版中。</span><span class="sxs-lookup"><span data-stu-id="49028-116">The [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) is not supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="49028-117">若要访问本地驱动器或可移动存储，可以在自己的应用程序中实现此。</span><span class="sxs-lookup"><span data-stu-id="49028-117">To access local drives or removable storage, you can implement this in your own application.</span></span>
* <span data-ttu-id="49028-118">Windows 10 IoT Core 设备将启动到[默认应用](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp)而不是类似于桌面的 PC。</span><span class="sxs-lookup"><span data-stu-id="49028-118">The Windows 10 IoT Core device will boot to the [default app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) instead of a desktop-like PC.</span></span> <span data-ttu-id="49028-119">此应用程序的目的不是仅为你提供要与首次启动时进行交互，但还允许你使用的友好 shell[开放源代码代码](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)为此应用程序，以便您可以使用这些功能即插你自己的自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="49028-119">The purpose of this application is not only to provide you with a friendly shell to interact with upon first boot, but to also allow you to use the [open-sourced code](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) for this application so that you can use these features to plug and play your own custom application(s).</span></span>

### <a name="differences-in-driver-supported-areas"></a><span data-ttu-id="49028-120">驱动程序支持的区域之间的差异</span><span class="sxs-lookup"><span data-stu-id="49028-120">Differences in driver-supported areas</span></span>

* <span data-ttu-id="49028-121">Windows 10 桌面版具有更比 Windows 10 IoT Core 支持的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="49028-121">Windows 10 Desktop has more supported drivers than Windows 10 IoT Core.</span></span> <span data-ttu-id="49028-122">若要使相同设备适用于 Windows 10 IoT Core 因为在桌面上，可能需要生成来自源的 Windows 10 IoT Core 设备驱动程序或查找另一个解决方法，尤其是对于 ARM 体系结构。</span><span class="sxs-lookup"><span data-stu-id="49028-122">To make the same device(s) work on Windows 10 IoT Core as on Desktop, you may need to build a driver from soruce for a Windows 10 IoT Core device or find another workaround, especially for ARM architecture.</span></span>
* <span data-ttu-id="49028-123">Libusb 为 Windows 10 IoT Core (ARM) 没有开箱驱动程序-你将需要生成源中要面向 ARM 体系结构。</span><span class="sxs-lookup"><span data-stu-id="49028-123">There is no out-of-the-box driver for libusb for Windows 10 IoT Core (ARM) - you will need to build from source to target the ARM architecture.</span></span>

### <a name="differences-in-available-registry-set"></a><span data-ttu-id="49028-124">可用的注册表设置中的差异</span><span class="sxs-lookup"><span data-stu-id="49028-124">Differences in available registry set</span></span>

* <span data-ttu-id="49028-125">在桌面上，是"自动隐藏滚动条在 Windows"，可以设置为 off 的选项。</span><span class="sxs-lookup"><span data-stu-id="49028-125">On desktop, there is an option to "Automatically hide scroll bars in Windows" that can be set to off.</span></span> <span data-ttu-id="49028-126">受以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="49028-126">It is controlled by the following registry entry:</span></span> 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* <span data-ttu-id="49028-127">有默认情况下是在 Windows 10 IoT Core 设备上的任何此类注册表。</span><span class="sxs-lookup"><span data-stu-id="49028-127">There is no such registry on Windows 10 IoT Core devices by default.</span></span> <span data-ttu-id="49028-128">你将需要根据需要添加"动态滚动条"注册。</span><span class="sxs-lookup"><span data-stu-id="49028-128">You will need to add a "Dynamic Scrollbars" register if you want.</span></span>
* <span data-ttu-id="49028-129">若要启用自动在 UWP 应用程序中隐藏滚动条，可以添加"DynamicScrollbars"注册并将值设置为"1"像这样：</span><span class="sxs-lookup"><span data-stu-id="49028-129">To enable hide scroll bars automatically in a UWP application, you can add the "DynamicScrollbars" register and set the value to "1" like this:</span></span>

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* <span data-ttu-id="49028-130">必须从默认帐户设置的注册表项。</span><span class="sxs-lookup"><span data-stu-id="49028-130">The registry key must be set from the Default Account.</span></span> <span data-ttu-id="49028-131">如果 ScrollViewer 的 XAML 设置为"Visible"，那么注册表设置为 0 将强制滚动条以显示 regardlss 是否足够要具有在 UI 中显示滚动的内容。</span><span class="sxs-lookup"><span data-stu-id="49028-131">If the ScrollViewer's XAML setting is "Visible", the nthe registry setting of 0 will force the scroll bar to appear regardlss of whether there is sufficient content to have the scroll appear in the UI.</span></span> <span data-ttu-id="49028-132">注册表设置为 1 将保留前没有足够内容隐藏滚动条。</span><span class="sxs-lookup"><span data-stu-id="49028-132">A registry setting of 1 will keep the scroll bar hidden until there is sufficient content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* <span data-ttu-id="49028-133">最后，如果 ScrollViewer XAML 的设置为"Auto"然后注册表设置为 0 将只显示完整的滚动条当没有足够的内容显示滚动条。</span><span class="sxs-lookup"><span data-stu-id="49028-133">Lastly, if the ScrollViewer XAML's setting is "Auto" then the registry setting of 0 will only show the full scroll bar when there is enough content to display the scroll bar.</span></span> <span data-ttu-id="49028-134">如果注册表设置为 1，隐藏足够内容如果时没有任何内容，然后将显示滚动条。</span><span class="sxs-lookup"><span data-stu-id="49028-134">When the registry setting is 1, the scroll bar will appear then when there is enough content or hidden if there is no content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a><span data-ttu-id="49028-135">支持的不同命令</span><span class="sxs-lookup"><span data-stu-id="49028-135">Different commands supported</span></span>

* <span data-ttu-id="49028-136">PowerShell 删除 AppxPackage 命令的工作上桌面，但不是在 Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="49028-136">The PowerShell Remove-AppxPackage command works on Dekstop but not on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="49028-137">并非所有设备上的文件夹都进行访问的通用 Windows 应用程序。</span><span class="sxs-lookup"><span data-stu-id="49028-137">Not all folders on your device are accessible by Universal Windows Apps.</span></span> <span data-ttu-id="49028-138">Windows 10 IoT Core 上可以使用 FolderPermissions 工具以便向 UWP 应用可以访问一个文件夹。</span><span class="sxs-lookup"><span data-stu-id="49028-138">On Windows 10 IoT Core you can use the FolderPermissions tool to make a folder accessible to a UWP app.</span></span> <span data-ttu-id="49028-139">例如，运行 FolderPermissions c:\test-e 使 UWP 应用能够访问 c:\test 文件夹。</span><span class="sxs-lookup"><span data-stu-id="49028-139">For example, run FolderPermissions c:\test -e to give UWP apps access to c:\test folder.</span></span> <span data-ttu-id="49028-140">但是，这不是在桌面上可用的。</span><span class="sxs-lookup"><span data-stu-id="49028-140">However, this is not available on Desktop.</span></span>

<span data-ttu-id="49028-141">在这篇文章所述的所有差异可能不是有效将来因为 Windows 10 IoT Core 不断地进行更新。</span><span class="sxs-lookup"><span data-stu-id="49028-141">All differences described in this post may not be valid in the future because Windows 10 IoT Core is constantly being updated.</span></span>

## <a name="helpful-resources"></a><span data-ttu-id="49028-142">有用资源</span><span class="sxs-lookup"><span data-stu-id="49028-142">Helpful resources</span></span>
<span data-ttu-id="49028-143">[阅读我们的文档](https://docs.microsoft.com/windows/iot-core/)若要了解有关 Windows 10 IoT Core 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="49028-143">[Read our documentation](https://docs.microsoft.com/windows/iot-core/) to learn more about Windows 10 IoT Core.</span></span>
