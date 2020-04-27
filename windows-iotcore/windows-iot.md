---
title: Windows 10 IoT 概述
ms.date: 01/30/2018
ms.topic: article
description: 了解 Windows 10 IoT 是什么，以及可以用它执行什么操作。
keywords: Windows 10 IoT 企业版, Windows 10 IoT 核心版, 无外设, 语音, 功能, 二进制版本, 版本
ms.openlocfilehash: 9ef9562e93dbaa71b97f75689adc3eed28ac1f9f
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2020
ms.locfileid: "75721793"
---
# <a name="an-overview-of-windows-10-iot"></a>Windows 10 IoT 概述 

> [!NOTE]
> Windows 容器受到支持，能够以商业方式部署在 Windows Server、Windows IoT Server、Windows IoT Enterprise 和 Windows IoT Core 上。  从 Windows 10 月更新 2018（版本 17763）开始，Windows 容器只能与 Windows 企业版和专业版配合使用，用于开发/测试目的。

## <a name="what-is-windows-10-iot"></a>什么是 Windows 10 IoT？
Windows 10 IoT 是 Windows 10 系列的成员，为物联网提供企业级功能、安全性和可管理性。  它利用 Windows 的嵌入式体验、生态系统和云连接，让组织可以通过安全的设备创建其物联网。这些设备可以快速进行预配、轻松进行管理，并可无缝连接到总体云策略。  

## <a name="windows-10-iot-editions"></a>Windows 10 IoT 版本
Windows 10 IoT 有两个版本。  Windows 10 IoT 核心版是 Windows 10 操作系统系列的最小成员。  虽然只运行单个应用，但它仍然具有 Windows 10 应有的可管理性和安全性。  与之相比，Windows 10 IoT 企业版则是 Windows 10 的完整版本，其专用功能可以用来创建专用设备，而这些设备则锁定到特定的一组应用程序和外设。 

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Windows 10 IoT 核心版和 Windows 10 IoT 企业版之间的差异

虽然 Windows 10 IoT 核心版和 Windows 10 IoT 企业版在名称上类似，但其提供的东西和支持的东西存在差异。 下面是一个功能列表，其中突出显示了版本差异。

> |             | Windows 10 IoT 核心版  |  Windows 10 IoT 企业版  |
> |-------------|----------|---------|
> | 用户体验 | 在某个时刻前台中会有一个 UWP 应用（请参阅 [IoT Shell 文档](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell)，了解如何进行应用 Backstack 处理），此外还有提供支持的后台应用和服务。 | 带有高级锁定功能的传统 Windows Shell |
> | 支持无外设 | 是 | 是 |
> | 支持应用体系结构 | 仅 UWP UI | 完整 Windows UI 支持（例如 UWP、WinForms 等） |
> | Cortana | [*Cortana SDK*](https://developer.microsoft.com/cortana/devices) | 是 |
> | 域加入 | 仅 AAD | AAD 和传统域 |
> | Management | MDM | MDM |
> | 设备安全技术 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm)、[安全启动、BitLocker、Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker)，以及设备运行状况证明 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm)、[安全启动、BitLocker、Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker)，以及设备运行状况证明 |
> | CPU 体系结构支持 | x86、x64 和 ARM | x86 和 x64 |
> | 授权 | 免版税联机许可协议和嵌入式 OEM 协议 | 直接和间接嵌入式 OEM 协议 |
> | 使用方案 | [数字签名](https://www.microsoft.com/windowsforbusiness/digital-signage)、智能建筑、IoT 网关、HMI、智能家居、可穿戴设备 | 工业平板电脑、零售服务点、展台、[数字签名](https://www.microsoft.com/windowsforbusiness/digital-signage)、ATM、医疗设备、制造设备、瘦客户端 |

如需最低要求的详细信息，请访问 [Windows 硬件站点](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview)。

如果想要详细了解服务点，请访问[有关此主题的 UWP 文档](https://aka.ms/pointofservice)。

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Windows 10 桌面版和 Windows 10 IoT 核心版之间的差异

### <a name="different-features-available-on-desktop-and-iot-core"></a>桌面版和 IoT 核心版上提供的不同功能

* 从版本 1809 (17763) 开始，Windows 10 IoT 核心版不再提供内置 Cortana。 若要让支持语音的设备快速面市，则可使用 [Cortana 设备 SDK 预览版](https://developer.microsoft.com/cortana/devices)将 Cortana 支持集成到设备中。
* Windows 10 IoT 核心版不支持 [FileOpenPicker API](https://docs.microsoft.com/uwp/api/windows.storage.pickers.fileopenpicker)。 若要访问本地驱动器或可移动存储，可以在自己的应用程序中实现此 API。
* Windows 10 IoT 核心版设备会启动到[默认应用](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)，这一点不同于桌面类电脑。 此应用程序的用途在于，它不仅为你提供一个友好的用于在首次启动时进行交互的 shell，而且允许你使用此应用程序的[开源代码](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)，这样你就可以使用这些功能对自己的自定义应用程序进行即插即用操作。

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

在此发布文章中显示的命令可能会随时间而变化，因为 Windows 10 IoT 核心版始终在更新。

## <a name="iot-edge-support-for-windows-10-iot"></a>针对 Windows 10 IoT 的 IoT Edge 支持
若要详细了解针对 Windows 10 IoT 的 IoT Edge 支持，请详细阅读[此处](https://docs.microsoft.com/azure/iot-edge/support#operating-systems)提供的 Azure IoT Edge 文章的“操作系统”部分。


## <a name="helpful-resources"></a>有用资源
* [Windows 10 IoT 企业版](windows-iot-enterprise.md)
* [Windows 10 IoT 核心板](windows-iot-core.md)
