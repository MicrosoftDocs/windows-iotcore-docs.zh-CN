---
title: Windows 10 IoT 核心版概述
ms.date: 01/18/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 阅读 Windows 10 IoT 核心版的概述。 了解 Windows 10 桌面版和 Windows 10 IoT 核心版之间的差异。
keywords: Windows 10 IoT 核心版, 占用空间小, 无外设
ms.openlocfilehash: 86566ae5715d8975f71481a76a6290dd9970d789
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230754"
---
# <a name="an-overview-of-windows-10-iot-core"></a>Windows 10 IoT 核心版概述

> [!NOTE]
> Windows 容器受到支持，能够以商业方式部署在 Windows Server、Windows IoT Server、Windows IoT Enterprise 和 Windows IoT Core 上。  从 Windows 10 月更新 2018（版本 17763）开始，Windows 容器只能与 Windows 企业版和专业版配合使用，用于开发/测试目的。

## <a name="what-is-windows-10-iot-core"></a>什么是 Windows 10 IoT 核心版？
Windows 10 IoT 核心版是针对带显示屏或不带显示屏的小型设备进行了优化的一个 Windows 10 版本，可以在 ARM 和 x86/x64 设备上运行。 此 Windows IoT 核心版文档介绍如何连接、管理、更新、保护设备，等等。

如果准备进入下一阶段并开始将解决方案商业化，则可参阅 [Windows 10 IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)，了解如何使用 Windows 10 IoT 核心版进行制造。

## <a name="getting-started"></a>入门

在尝试制造某个设备之前，最好是先使用 Windows 10 IoT 核心版尝试该设备并制作其原型。 这样就可以了解在要制造时需要的功能和配置。

<table>  
<colgroup> <col width="50%" /> <col width="50%" /> </colgroup>  
<thead>  
<tr class="header">  
<th align="left">主题</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. 选取原型板</a></p></td>
<td align="left"><p>查看常见的原型板，选择一个开始其原型制作。</p></td>
</tr>

<tr class="odd">
<td align="left"><p>2. 刷写原型映像</p></td>
<td align="left"><p>转到教程部分，了解如何将原型映像刷写到所选设备中。 </p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller">3. 安装应用</a></p></td>
<td align="left"><p>了解如何使用不同工具来安装应用。</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appdeployment">4. 部署应用</a></p></td>
<td align="left"><p>了解如何使用 Visual Studio 来部署应用。</p></td>
</tr>

</tbody>
</table>

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Windows 10 IoT 核心版和 Windows 10 IoT 企业版之间的差异

虽然 Windows 10 IoT 核心版和 Windows 10 IoT 企业版在名称上类似，但其提供的东西和支持的东西存在差异。 下面是一个功能列表，其中突出显示了版本差异。

> | 功能&nbsp;/&nbsp;版本 | Windows 10 IoT 核心板  |  Windows 10 IoT 企业版  |
> |-------------|----------|---------|
> | 用户体验 | 在某个时刻前台中会有一个 UWP 应用（请参阅 [IoT Shell 文档](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell)，了解如何进行应用 Backstack 处理），此外还有提供支持的后台应用和服务。 | 带有高级锁定功能的传统 Windows Shell |
> | 支持无外设 | 是 | 是 |
> | 支持应用体系结构 | 仅 UWP UI | 完整 Windows UI 支持（例如 UWP、WinForms 等） |
> | Cortana | [*Cortana SDK*](https://developer.microsoft.com/cortana/devices) | 是 |
> | 域加入 | 仅 AAD | AAD 和传统域 |
> | 管理 | MDM | MDM |
> | 设备安全技术 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm)、[安全启动、BitLocker、Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker)，以及设备运行状况证明 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm)、[安全启动、BitLocker、Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker)，以及设备运行状况证明 |
> | CPU 体系结构支持 | x86、x64 和 ARM | x86 和 x64 |
> | 许可 | 免版税联机许可协议和嵌入式 OEM 协议 | 直接和间接嵌入式 OEM 协议 |
> | 使用方案 | [数字签名](https://www.microsoft.com/windowsforbusiness/digital-signage)、智能建筑、IoT 网关、HMI、智能家居、可穿戴设备 | 工业平板电脑、零售服务点、展台、[数字签名](https://www.microsoft.com/windowsforbusiness/digital-signage)、ATM、医疗设备、制造设备、瘦客户端 |

如需最低要求的详细信息，请访问 [Windows 硬件站点](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview)。

如果想要详细了解服务点，请访问[有关此主题的 UWP 文档](https://aka.ms/pointofservice)。

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Windows 10 桌面版和 Windows 10 IoT 核心版之间的差异

### <a name="different-features-available-on-desktop-and-iot-core"></a>桌面版和 IoT 核心版上提供的不同功能

* 从版本 1809 (17763) 开始，Windows 10 IoT 核心版不再提供内置 Cortana。 若要让支持语音的设备快速面市，则可使用 [Cortana 设备 SDK 预览版](https://developer.microsoft.com/cortana/devices)将 Cortana 支持集成到设备中。
* Windows 10 IoT 核心版不支持 [FileOpenPicker API](https://docs.microsoft.com/uwp/api/windows.storage.pickers.fileopenpicker)。 若要访问本地驱动器或可移动存储，可以在自己的应用程序中实现此 API。
* 现成的 Windows 10 IoT 核心版设备会启动到[默认应用](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)，这一点不同于桌面类电脑。 但是，若要进行商业化，**必须** 将该默认应用替换为可以修改的自定义应用或默认应用。 此应用程序的用途在于，它不仅为你提供一个友好的用于在首次启动时进行交互的 shell，而且允许你使用此应用程序的[开源代码](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)，这样你就可以使用这些功能对自己的自定义应用程序进行即插即用操作。

### <a name="differences-in-driver-supported-areas"></a>驱动程序支持范围的差异

* Windows 10 桌面版支持的驱动程序多于 Windows 10 IoT 核心版。 若要让相同的设备在 Windows 10 IoT 核心版和桌面版上都可以使用，可能需要根据 Windows 10 IoT 核心版设备的源代码构建一个驱动程序，或者找到另一个解决方案，尤其是针对 ARM 体系结构的解决方案。
* 对于适用于 Windows 10 IoT 核心版 (ARM) 的 libusb，没有现成的驱动程序 - 需根据源代码构建面向 ARM 体系结构的驱动程序。

### <a name="differences-in-available-registry-set"></a>可用注册表设置中的差异

* 在桌面版上有一个“自动隐藏 Windows 中的滚动条”选项，可以将其设置为关。 它由以下注册表项控制：

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* 在 Windows 10 IoT 核心版设备上，默认没有此类注册表。 需添加“DynamicScrollbars”注册表项（如果想要这样做）。
* 若要启用在 UWP 应用程序中自动隐藏滚动条的功能，可以添加“DynamicScrollbars”注册表项并将值设置为“1”，如下所示：

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* 必须通过默认帐户设置注册表项。 如果 ScrollViewer 的 XAML 设置为 "Visible"，则注册表设置为 0 会强制滚动条显示，不管是否有足够的内容让滚动条显示在 UI 中。 注册表设置为 1 会使滚动条处于隐藏状态，直至有足够的内容迫使其显示。

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* 最后，如果 ScrollViewer XAML 的设置为 "Auto"，则注册表设置为 0 时，只有在有足够内容的情况下才会显示完整的滚动条。 注册表设置为 1 时，滚动条会在有足够内容的时候显示，在没有内容的时候隐藏。

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>支持的命令不同

* PowerShell 的 Remove-AppxPackage 命令可以在 Windows 10 桌面版上使用，但不能在 Windows 10 IoT 核心版上使用。
* 并非设备上的所有文件夹都可供通用 Windows 应用访问。 在 Windows 10 IoT 核心版上，可以使用 FolderPermissions 工具将文件夹设置为可供 UWP 应用访问。 例如，运行 FolderPermissions c:\test -e 即可让 UWP 应用访问 c:\test 文件夹。 但是，这在桌面版上不适用。

此发布文章中介绍的所有差异在将来可能不适用，因为 Windows 10 IoT 核心版经常进行更新。

## <a name="helpful-resources"></a>有用资源
[阅读我们的文档](https://docs.microsoft.com/windows/iot-core/)，详细了解 Windows 10 IoT 核心版。
