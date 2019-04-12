---
title: 媒体传输协议
author: PawelWMS
ms.author: pawelwi
ms.date: 12/06/2017
ms.topic: article
description: 了解如何启用可选的媒体传输协议 (MTP) 功能，若要从你的设备通过 USB 来回传输文件。
keywords: windows iot，MTP，媒体传输协议、 文件传输、 设备
ms.openlocfilehash: 72856617c8d49a1b06eadd13ab5fb085340d2ed4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510624"
---
# <a name="media-transfer-protocol"></a>媒体传输协议
媒体传输协议 (MTP)，可从 Windows 10 IoT Core 设备通过 USB 来回传输文件。 如果存在，它允许访问设备的内部存储和 SD 卡。

功能是可以下载并安装从 IoT Core 工具包的一部分[Windows 10 IoT Core 包](https://www.microsoft.com/en-us/download/details.aspx?id=55031)。

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a>如何在运行 Windows 10 IoT 核心版的设备上安装 MTP 功能

### <a name="provisioning-the-device-with-required-packages"></a>预配设备所需的包

1. 启动[Powershell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)和访问运行 Windows 10 IoT 核心版的设备。
2. 从 Powershell 或 SSH，请执行以下操作：
    1. 在目标计算机上创建临时文件夹（例如 `C:\MTPTemp`）。
    2. 基于设备的体系结构，将以下包从您的 PC 复制 (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`) 到`C:\MTPTemp`:
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. 运行以下命令从`C:\MTPTemp`若要将包安装到你的 IoT 设备的系统映像：
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. 设备将启动到更新 OS，安装 MTP 功能，然后重启到 MainOS。

### <a name="enabling-the-mtp-usb-interface"></a>启用 MTP USB 接口

设备到 MainOS 返回后，一旦 USBFN 配置仍需要更新，以包含 MTP。 为此，需要将 MTP 添加到 USBFN 枚举的接口。
[USB 注册表设置](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver)文章介绍了 USB 的配置的详细信息。

尽管可以修改默认 USBFN 配置下提供`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`密钥，建议定义您自己，因为它们将不会被覆盖的系统更新。

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a>与 MTP 接口创建新的 USBFN 配置

请按照以下步骤添加新的配置与 MTP 操作：
1. 添加新的密钥下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations`。 例如：`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`。
2. 在新的项下创建`REG_MULTI_SZ`值`InterfaceList`等于`MTP`。
3. 在同一个项下创建`REG_BINARY`值`MSOSCompatIdDescriptor`等于`2800000000010400010000000000000000014D545000000000000000000000000000000000000000`。
4. 下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`添加一个新`REG_SZ`值`CurrentConfiguration`等于新创建的密钥的名称。 在这种情况下会`MyConfiguration`。
5. [**可选**] 下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`添加新`REG_DWORD`值`IncludeDefaultCfg`等于 1。 这将使枚举以及 MTP 默认接口的 USB 驱动程序。

> [!NOTE]
> 如果你已在使用必须对其进行修改而不是创建一个新的自定义配置。

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a>将 MTP 接口添加到现有的配置

请按照以下步骤添加到现有 USBFN 配置 MTP 操作：
1. 通过检查查找当前的配置`CurrentConfiguration`值下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`。 如果值存在，则可在当前配置下找到`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]`。 否则将下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`。
2. 在当前的配置项下添加`\0MTP`的值`InterfaceList`。 ***\0***为的类型使用部分`InterfaceList`是`REG_MULTI_SZ`和它需要此值之间的分隔符。
3. 修改`MSOSCompatIdDescriptor`值，以包括 MTP 的描述符。 若要创建一个包含所有接口当前下的有效说明符`InterfaceList`值，请按照在底部提供的说明文档[本页](https://msdn.microsoft.com/windows/hardware/gg463179.aspx)。 *OS_Desc_CompatID.doc*提供描述符的格式和描述符中包括多个接口的示例的说明。 MTP 的兼容和次级兼容 Id 也是可在同一页上，并使用中的一个示例。

## <a name="how-to-include-mtp-in-your-custom-ffu"></a>如何在您的自定义 FFU 中包含 MTP

1. 添加**IOT_MTP**功能到 OEM 输入文件的 ID。 这是从步骤等效项"[**预配所需的包与设备**](#provisioning-the-device-with-required-packages)"部分。
2. 请确保应用相同的注册表更改，如中所述"[**与 MTP 接口创建新的 USBFN 配置**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)"部分。 请按照[这些说明](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image)若要了解如何应用于 FFU 注册表更改。
3. 创建 image\FFU。 读取[这篇文章](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)有关的说明。

> [!WARNING]
> 通过 FFU 自定义项不应尝试修改默认配置。 系统定义的项的系统更新刷新/更改且所有自定义设置都将丢失。

## <a name="how-to-setup-the-mtp-sd-card-filter"></a>如何设置 MTP SD 卡筛选器

默认情况下 MTP 将枚举中的所有内容的 SD 卡中，如果存在在设备上。 很有可能，但是，若要限制到特定的子文件夹的此枚举。 为了执行此操作，必须添加注册表值`MTPSDFolderFilter`注册表项下`HKEY_LOCAL_MACHINE\Software\Microsoft\MTP`。
值为类型`REG_SZ`，并且应包含你想 MTP 要枚举的文件夹的相对路径。 如果尚不存在，则获取自动创建文件夹。

示例路径：
- \FirstLevelDirectory;
- FirstLevelDirectory;
- \FirstLevelDirectory\SecondLevelDirectory;
- Never\Before\Created\Directory.

> [!WARNING]
> 不要使用绝对路径包含类似的驱动器号`C:\Some\Folder\Path`-这可能会阻止正在枚举 SD 卡。

请参阅[此链接](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image)有关自定义映像与特定的注册表项的详细信息。
