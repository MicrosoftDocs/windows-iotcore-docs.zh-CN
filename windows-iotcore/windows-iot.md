---
title: Windows 10 IoT 的概述
author: saraclay
ms.author: saclayt
ms.date: 01/30/2018
ms.topic: article
description: 了解什么是 Windows 10 IoT，您可以使用它所执行的操作。
keywords: Windows 10 IoT 企业版，Windows 10 IoT Core，无外设、 语音、 功能、 二进制版本，版本
ms.openlocfilehash: ecfb80049b4fe1dd5437faf6bce410f9fcb3c528
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510622"
---
# <a name="an-overview-of-windows-10-iot"></a>Windows 10 IoT 概述 

## <a name="what-is-windows-10-iot"></a>Windows 10 IoT 是什么？
Windows 10 IoT 是 Windows 10 系列，它将企业级的能力、 安全性和可管理性引入到物联网的成员。  它利用 Windows 的嵌入式体验、 生态系统和云连接性，使组织能够使用安全设备，可以快速设置、 轻松地管理和无缝连接到的总体云策略创建其的物联网。  

## <a name="windows-10-iot-editions"></a>Windows 10 IoT 版本
Windows 10 IoT 提供两个版本。  Windows 10 IoT 核心版是 Windows 10 操作系统系列的最小成员。  而只运行单个应用程序，它仍具有可管理性和预期的方式从 Windows 10 的安全性。  与此相反，Windows 10 IoT 企业版是要创建一组特定的应用程序和外围设备锁定的专用的设备的专用功能完整的版本的 Windows 10。 

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Windows 10 IoT 核心版和 Windows 10 IoT 企业版之间的差异

虽然 Windows 10 IoT 核心版和 Windows 10 IoT 企业版是在名称类似，有的功能以及它们所支持内容之间的差异。 下面是一个功能列表，其中突出显示了版本差异。

> |             | Windows 10 IoT 核心版  |  Windows 10 IoT 企业版  |
> |-------------|----------|---------|
> | 用户体验 | 一次的前景中的一个 UWP 应用 (请参阅[IoT Shell 文档](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoreshell)应用 backstack 处理) 提供的支持背景应用和服务。 | 高级的锁定功能与传统的 Windows Shell |
> | 无外设支持 | 是 | 是 |
> | 支持的应用程序体系结构 | UWP 用户界面 | Windows UI 的完整支持 （例如 UWP、 WinForms 等） |
> | Cortana | [*Cortana SDK*](https://developer.microsoft.com/en-us/cortana/devices) | 是 |
> | 域加入 | 只有 AAD | AAD 与传统的域 |
> | Management | MDM | MDM |
> | 设备安全技术 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm)，[安全引导、 BitLocker、 设备保护](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker)，和设备运行状况证明 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm)，[安全引导、 BitLocker、 设备保护](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker)和设备运行状况证明 |
> | CPU 体系结构支持 | x86、 x64 和 ARM | x86 和 x64 |
> | 授权 | 联机免版税的许可协议和嵌入式的 OEM 协议， | 直接和间接的嵌入式的 OEM 协议 |
> | 使用方案 | [数字签名](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage)，智能建筑、 IoT 网关、 HMI，主页，智能可穿戴设备 | 行业平板电脑、 POS、 展台[数字签名](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage)，ATM、 医疗设备、 制造设备，瘦客户端 |

最低要求的详细信息，请访问[Windows 硬件站点](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview)。

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

在此文章中介绍了所有差异可能会都消失，随着时间的推移由于 Windows 10 IoT Core 的就是不断更新。


## <a name="helpful-resources"></a>有用资源
* [Windows 10 IoT 企业版](windows-iot-enterprise.md)
* [Windows 10 IoT 核心版](windows-iot-core.md)
