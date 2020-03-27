---
title: Windows 10 IoT 核心版概述
ms.date: 01/18/2018
ms.topic: article
description: 了解 Windows 10 IoT 核心版是什么，以及可以用它执行什么操作。
keywords: Windows 10 IoT 核心版, 占用空间小, 无外设
ms.openlocfilehash: 270d2e2491514a1b5b0c0fefb7c16da326512355
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080525"
---
# <a name="an-overview-of-windows-10-iot-core"></a><span data-ttu-id="bb350-104">Windows 10 IoT 核心版概述</span><span class="sxs-lookup"><span data-stu-id="bb350-104">An overview of Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="bb350-105">Windows 容器受到支持，能够以商业方式部署在 Windows Server、Windows IoT Server、Windows IoT Enterprise 和 Windows IoT Core 上。</span><span class="sxs-lookup"><span data-stu-id="bb350-105">Windows Containers are supported for commercial deployments on Windows Server, Windows IoT Server, Windows IoT Enterprise and Windows IoT Core.</span></span>  <span data-ttu-id="bb350-106">从 Windows 10 月更新 2018（版本 17763）开始，Windows 容器只能与 Windows 企业版和专业版配合使用，用于开发/测试目的。</span><span class="sxs-lookup"><span data-stu-id="bb350-106">As of Windows October Update 2018 (Build 17763), Windows Containers can only be used with Windows Enterprise and Professional for dev/test purposes.</span></span>

## <a name="what-is-windows-10-iot-core"></a><span data-ttu-id="bb350-107">什么是 Windows 10 IoT 核心版？</span><span class="sxs-lookup"><span data-stu-id="bb350-107">What is Windows 10 IoT Core?</span></span>
<span data-ttu-id="bb350-108">Windows 10 IoT 核心版是针对带显示屏或不带显示屏的小型设备进行了优化的一个 Windows 10 版本，可以在 ARM 和 x86/x64 设备上运行。</span><span class="sxs-lookup"><span data-stu-id="bb350-108">Windows 10 IoT Core is a version of Windows 10 that is optimized for smaller devices with or without a display that run on both ARM and x86/x64 devices.</span></span> <span data-ttu-id="bb350-109">此 Windows IoT 核心版文档介绍如何连接、管理、更新、保护设备，等等。</span><span class="sxs-lookup"><span data-stu-id="bb350-109">The Windows IoT Core documentation provides information on connecting, managing, updating, securing your devices, and more.</span></span> 

<span data-ttu-id="bb350-110">如果准备进入下一阶段并开始将解决方案商业化，则可参阅 [Windows 10 IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)，了解如何使用 Windows 10 IoT 核心版进行制造。</span><span class="sxs-lookup"><span data-stu-id="bb350-110">If you're ready to go to the next level and start commercializing your solution, you can learn how to manufacture with Windows 10 IoT Core with our [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> 

## <a name="getting-started"></a><span data-ttu-id="bb350-111">入门</span><span class="sxs-lookup"><span data-stu-id="bb350-111">Getting started</span></span>

<span data-ttu-id="bb350-112">在尝试制造某个设备之前，最好是先使用 Windows 10 IoT 核心版尝试该设备并制作其原型。</span><span class="sxs-lookup"><span data-stu-id="bb350-112">Before attempting to manufacture a device, it's best to first try and prototype a device with Windows 10 IoT Core.</span></span> <span data-ttu-id="bb350-113">这样就可以了解在要制造时需要的功能和配置。</span><span class="sxs-lookup"><span data-stu-id="bb350-113">That way, you can understand what features you'll need and what configurations you'll want when it's time to manufacture.</span></span>

<table>  
<span data-ttu-id="bb350-114"><colgroup> <col width="50%" /> <col width="50%" /> </colgroup>  
</span><span class="sxs-lookup"><span data-stu-id="bb350-114"><colgroup> <col width="50%" /> <col width="50%" /> </colgroup>  
</span></span><thead>  
<tr class="header">  
<th align="left"><span data-ttu-id="bb350-115">主题</span><span class="sxs-lookup"><span data-stu-id="bb350-115">Topic</span></span></th>
<th align="left"><span data-ttu-id="bb350-116">说明</span><span class="sxs-lookup"><span data-stu-id="bb350-116">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bb350-117"><a href="https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. 选取原型板</a></span><span class="sxs-lookup"><span data-stu-id="bb350-117"><a href="https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. Pick a prototype board</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="bb350-118">查看常见的原型板，选择一个开始其原型制作。</span><span class="sxs-lookup"><span data-stu-id="bb350-118">Take a look at common prototype boards and choose one to start prototyping with.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bb350-119">2. 刷写原型映像</span><span class="sxs-lookup"><span data-stu-id="bb350-119">2. Flash a prototype image</span></span></p></td>
<td align="left"><p><span data-ttu-id="bb350-120">转到教程部分，了解如何将原型映像刷写到所选设备中。</span><span class="sxs-lookup"><span data-stu-id="bb350-120">Go to our tutorial sections to learn how to flash prototype images onto your selected device(s).</span></span> </p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bb350-121"><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller">3. 安装应用</a></span><span class="sxs-lookup"><span data-stu-id="bb350-121"><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller">3. Install your app</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="bb350-122">了解如何使用不同工具来安装应用。</span><span class="sxs-lookup"><span data-stu-id="bb350-122">Learn how to install your app using different tools.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bb350-123"><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appdeployment">4. 部署应用</a></span><span class="sxs-lookup"><span data-stu-id="bb350-123"><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appdeployment">4. Deploy your app</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="bb350-124">了解如何使用 Visual Studio 来部署应用。</span><span class="sxs-lookup"><span data-stu-id="bb350-124">Learn how to deploy an app using Visual Studio.</span></span></p></td>
</tr>

</tbody>
</table>

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a><span data-ttu-id="bb350-125">Windows 10 桌面版和 Windows 10 IoT 核心版之间的差异</span><span class="sxs-lookup"><span data-stu-id="bb350-125">Differences between Windows 10 Desktop and Windows 10 IoT Core</span></span>

### <a name="different-features-available-on-desktop-and-iot-core"></a><span data-ttu-id="bb350-126">桌面版和 IoT 核心版上提供的不同功能</span><span class="sxs-lookup"><span data-stu-id="bb350-126">Different features available on Desktop and IoT Core</span></span>

* <span data-ttu-id="bb350-127">从版本 1809 (17763) 开始，Windows 10 IoT 核心版不再提供内置 Cortana。</span><span class="sxs-lookup"><span data-stu-id="bb350-127">Inbox Cortana is no longer available on Windows 10 IoT Core since version 1809 (17763).</span></span> <span data-ttu-id="bb350-128">若要让支持语音的设备快速面市，则可使用 [Cortana 设备 SDK 预览版](https://developer.microsoft.com/cortana/devices)将 Cortana 支持集成到设备中。</span><span class="sxs-lookup"><span data-stu-id="bb350-128">If you are looking to bring a voice-enabled device to market quickly, you can integrate Cortana support into the device using the [preview of the Cortana Devices SDK](https://developer.microsoft.com/cortana/devices).</span></span>
* <span data-ttu-id="bb350-129">Windows 10 IoT 核心版不支持 [FileOpenPicker API](https://docs.microsoft.com/uwp/api/windows.storage.pickers.fileopenpicker)。</span><span class="sxs-lookup"><span data-stu-id="bb350-129">The [FileOpenPicker API](https://docs.microsoft.com/uwp/api/windows.storage.pickers.fileopenpicker) is not supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="bb350-130">若要访问本地驱动器或可移动存储，可以在自己的应用程序中实现此 API。</span><span class="sxs-lookup"><span data-stu-id="bb350-130">To access local drives or removable storage, you can implement this in your own application.</span></span>
* <span data-ttu-id="bb350-131">现成的 Windows 10 IoT 核心版设备会启动到[默认应用](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)，这一点不同于桌面类电脑。</span><span class="sxs-lookup"><span data-stu-id="bb350-131">Out of the box, The Windows 10 IoT Core device will boot to the [default app](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) instead of a desktop-like PC.</span></span> <span data-ttu-id="bb350-132">但是，若要进行商业化，**必须**将该默认应用替换为可以修改的自定义应用或默认应用。</span><span class="sxs-lookup"><span data-stu-id="bb350-132">However, for commercialization, this default app **must** be replaced by either a custom app or a default app that can be modified.</span></span> <span data-ttu-id="bb350-133">此应用程序的用途在于，它不仅为你提供一个友好的用于在首次启动时进行交互的 shell，而且允许你使用此应用程序的[开源代码](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)，这样你就可以使用这些功能对自己的自定义应用程序进行即插即用操作。</span><span class="sxs-lookup"><span data-stu-id="bb350-133">The purpose of this application is not only to provide you with a friendly shell to interact with upon first boot, but to also allow you to use the [open-sourced code](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) for this application so that you can use these features to plug and play your own custom application(s).</span></span>

### <a name="differences-in-driver-supported-areas"></a><span data-ttu-id="bb350-134">驱动程序支持范围的差异</span><span class="sxs-lookup"><span data-stu-id="bb350-134">Differences in driver-supported areas</span></span>

* <span data-ttu-id="bb350-135">Windows 10 桌面版支持的驱动程序多于 Windows 10 IoT 核心版。</span><span class="sxs-lookup"><span data-stu-id="bb350-135">Windows 10 Desktop has more supported drivers than Windows 10 IoT Core.</span></span> <span data-ttu-id="bb350-136">若要让相同的设备在 Windows 10 IoT 核心版和桌面版上都可以使用，可能需要根据 Windows 10 IoT 核心版设备的源代码构建一个驱动程序，或者找到另一个解决方案，尤其是针对 ARM 体系结构的解决方案。</span><span class="sxs-lookup"><span data-stu-id="bb350-136">To make the same device(s) work on Windows 10 IoT Core as on Desktop, you may need to build a driver from source for a Windows 10 IoT Core device or find another workaround, especially for ARM architecture.</span></span>
* <span data-ttu-id="bb350-137">对于适用于 Windows 10 IoT 核心版 (ARM) 的 libusb，没有现成的驱动程序 - 需根据源代码构建面向 ARM 体系结构的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="bb350-137">There is no out-of-the-box driver for libusb for Windows 10 IoT Core (ARM) - you will need to build from source to target the ARM architecture.</span></span>

### <a name="differences-in-available-registry-set"></a><span data-ttu-id="bb350-138">可用注册表设置中的差异</span><span class="sxs-lookup"><span data-stu-id="bb350-138">Differences in available registry set</span></span>

* <span data-ttu-id="bb350-139">在桌面版上有一个“自动隐藏 Windows 中的滚动条”选项，可以将其设置为关。</span><span class="sxs-lookup"><span data-stu-id="bb350-139">On desktop, there is an option to "Automatically hide scroll bars in Windows" that can be set to off.</span></span> <span data-ttu-id="bb350-140">它由以下注册表项控制：</span><span class="sxs-lookup"><span data-stu-id="bb350-140">It is controlled by the following registry entry:</span></span> 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* <span data-ttu-id="bb350-141">在 Windows 10 IoT 核心版设备上，默认没有此类注册表。</span><span class="sxs-lookup"><span data-stu-id="bb350-141">There is no such registry on Windows 10 IoT Core devices by default.</span></span> <span data-ttu-id="bb350-142">需添加“DynamicScrollbars”注册表项（如果想要这样做）。</span><span class="sxs-lookup"><span data-stu-id="bb350-142">You will need to add a "Dynamic Scrollbars" register if you want.</span></span>
* <span data-ttu-id="bb350-143">若要启用在 UWP 应用程序中自动隐藏滚动条的功能，可以添加“DynamicScrollbars”注册表项并将值设置为“1”，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bb350-143">To enable hide scroll bars automatically in a UWP application, you can add the "DynamicScrollbars" register and set the value to "1" like this:</span></span>

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* <span data-ttu-id="bb350-144">必须通过默认帐户设置注册表项。</span><span class="sxs-lookup"><span data-stu-id="bb350-144">The registry key must be set from the Default Account.</span></span> <span data-ttu-id="bb350-145">如果 ScrollViewer 的 XAML 设置为 "Visible"，则注册表设置为 0 会强制滚动条显示，不管是否有足够的内容让滚动条显示在 UI 中。</span><span class="sxs-lookup"><span data-stu-id="bb350-145">If the ScrollViewer's XAML setting is "Visible", the nthe registry setting of 0 will force the scroll bar to appear regardlss of whether there is sufficient content to have the scroll appear in the UI.</span></span> <span data-ttu-id="bb350-146">注册表设置为 1 会使滚动条处于隐藏状态，直至有足够的内容迫使其显示。</span><span class="sxs-lookup"><span data-stu-id="bb350-146">A registry setting of 1 will keep the scroll bar hidden until there is sufficient content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* <span data-ttu-id="bb350-147">最后，如果 ScrollViewer XAML 的设置为 "Auto"，则注册表设置为 0 时，只有在有足够内容的情况下才会显示完整的滚动条。</span><span class="sxs-lookup"><span data-stu-id="bb350-147">Lastly, if the ScrollViewer XAML's setting is "Auto" then the registry setting of 0 will only show the full scroll bar when there is enough content to display the scroll bar.</span></span> <span data-ttu-id="bb350-148">注册表设置为 1 时，滚动条会在有足够内容的时候显示，在没有内容的时候隐藏。</span><span class="sxs-lookup"><span data-stu-id="bb350-148">When the registry setting is 1, the scroll bar will appear then when there is enough content or hidden if there is no content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a><span data-ttu-id="bb350-149">支持的命令不同</span><span class="sxs-lookup"><span data-stu-id="bb350-149">Different commands supported</span></span>

* <span data-ttu-id="bb350-150">PowerShell 的 Remove-AppxPackage 命令可以在 Windows 10 桌面版上使用，但不能在 Windows 10 IoT 核心版上使用。</span><span class="sxs-lookup"><span data-stu-id="bb350-150">The PowerShell Remove-AppxPackage command works on Desktop but not on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="bb350-151">并非设备上的所有文件夹都可供通用 Windows 应用访问。</span><span class="sxs-lookup"><span data-stu-id="bb350-151">Not all folders on your device are accessible by Universal Windows Apps.</span></span> <span data-ttu-id="bb350-152">在 Windows 10 IoT 核心版上，可以使用 FolderPermissions 工具将文件夹设置为可供 UWP 应用访问。</span><span class="sxs-lookup"><span data-stu-id="bb350-152">On Windows 10 IoT Core you can use the FolderPermissions tool to make a folder accessible to a UWP app.</span></span> <span data-ttu-id="bb350-153">例如，运行 FolderPermissions c:\test -e 即可让 UWP 应用访问 c:\test 文件夹。</span><span class="sxs-lookup"><span data-stu-id="bb350-153">For example, run FolderPermissions c:\test -e to give UWP apps access to c:\test folder.</span></span> <span data-ttu-id="bb350-154">但是，这在桌面版上不适用。</span><span class="sxs-lookup"><span data-stu-id="bb350-154">However, this is not available on Desktop.</span></span>

<span data-ttu-id="bb350-155">此发布文章中介绍的所有差异在将来可能不适用，因为 Windows 10 IoT 核心版经常进行更新。</span><span class="sxs-lookup"><span data-stu-id="bb350-155">All differences described in this post may not be valid in the future because Windows 10 IoT Core is constantly being updated.</span></span>

## <a name="helpful-resources"></a><span data-ttu-id="bb350-156">有用资源</span><span class="sxs-lookup"><span data-stu-id="bb350-156">Helpful resources</span></span>
<span data-ttu-id="bb350-157">[阅读我们的文档](https://docs.microsoft.com/windows/iot-core/)，详细了解 Windows 10 IoT 核心版。</span><span class="sxs-lookup"><span data-stu-id="bb350-157">[Read our documentation](https://docs.microsoft.com/windows/iot-core/) to learn more about Windows 10 IoT Core.</span></span>
