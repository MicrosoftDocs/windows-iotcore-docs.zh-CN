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
# <a name="windows-10-iot-core"></a>Windows 10 IoT 核心版

## <a name="what-is-windows-10-iot-core"></a>什么是 Windows 10 IoT 核心版？
Windows 10 IoT 核心版是针对同时 ARM 运行的较小设备使用或不带显示器和 x86/x64 设备优化的 Windows 10 版本。 Windows IoT Core 文档提供有关连接、 管理、 更新、 保护你的设备和的详细信息。 

## <a name="getting-started"></a>即刻体验
若要开始使用 Windows 10 IoT 核心版，我们已创建[Windows 10 IoT Core Quickstarter](tutorials/Tutorials.md)以帮助您快速熟悉平台。 

在这里，您可以继续通过开发自己的应用程序对平台进行试验或开始制定计划以将你的设备推向市场，或商业化你的设备。 若要开始使用 commercializing，请参阅自带设备推向市场中的部分[入门的文章](https://docs.microsoft.com/windows/iot-core/getstarted)。

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Windows 10 桌面版和 Windows 10 IoT 核心版之间的差异

### <a name="different-features-available-on-desktop-and-iot-core"></a>可在桌面和 IoT Core 上的不同功能

* 收件箱 Cortana 之后的版本 1809 (17763) 不再可在 Windows 10 IoT 核心版上。 如果想要将具有语音功能的设备要快地进入市场，可以将 Cortana 支持集成到设备使用[Cortana 设备 SDK 的预览](https://developer.microsoft.com/en-us/cortana/devices)。
* [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker)不支持在 Windows 10 IoT 核心版中。 若要访问本地驱动器或可移动存储，可以在自己的应用程序中实现此。
* Windows 10 IoT Core 设备将启动到[默认应用](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp)而不是类似于桌面的 PC。 此应用程序的目的不是仅为你提供要与首次启动时进行交互，但还允许你使用的友好 shell[开放源代码代码](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)为此应用程序，以便您可以使用这些功能即插你自己的自定义应用程序。

### <a name="differences-in-driver-supported-areas"></a>驱动程序支持的区域之间的差异

* Windows 10 桌面版具有更比 Windows 10 IoT Core 支持的驱动程序。 若要使相同设备适用于 Windows 10 IoT Core 因为在桌面上，可能需要生成来自源的 Windows 10 IoT Core 设备驱动程序或查找另一个解决方法，尤其是对于 ARM 体系结构。
* Libusb 为 Windows 10 IoT Core (ARM) 没有开箱驱动程序-你将需要生成源中要面向 ARM 体系结构。

### <a name="differences-in-available-registry-set"></a>可用的注册表设置中的差异

* 在桌面上，是"自动隐藏滚动条在 Windows"，可以设置为 off 的选项。 受以下注册表项： 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* 有默认情况下是在 Windows 10 IoT Core 设备上的任何此类注册表。 你将需要根据需要添加"动态滚动条"注册。
* 若要启用自动在 UWP 应用程序中隐藏滚动条，可以添加"DynamicScrollbars"注册并将值设置为"1"像这样：

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* 必须从默认帐户设置的注册表项。 如果 ScrollViewer 的 XAML 设置为"Visible"，那么注册表设置为 0 将强制滚动条以显示 regardlss 是否足够要具有在 UI 中显示滚动的内容。 注册表设置为 1 将保留前没有足够内容隐藏滚动条。

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* 最后，如果 ScrollViewer XAML 的设置为"Auto"然后注册表设置为 0 将只显示完整的滚动条当没有足够的内容显示滚动条。 如果注册表设置为 1，隐藏足够内容如果时没有任何内容，然后将显示滚动条。

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>支持的不同命令

* PowerShell 删除 AppxPackage 命令的工作上桌面，但不是在 Windows 10 IoT Core。
* 并非所有设备上的文件夹都进行访问的通用 Windows 应用程序。 Windows 10 IoT Core 上可以使用 FolderPermissions 工具以便向 UWP 应用可以访问一个文件夹。 例如，运行 FolderPermissions c:\test-e 使 UWP 应用能够访问 c:\test 文件夹。 但是，这不是在桌面上可用的。

在这篇文章所述的所有差异可能不是有效将来因为 Windows 10 IoT Core 不断地进行更新。

## <a name="helpful-resources"></a>有用资源
[阅读我们的文档](https://docs.microsoft.com/windows/iot-core/)若要了解有关 Windows 10 IoT Core 的详细信息。
