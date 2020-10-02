---
title: 媒体传输协议
author: PawelWMS
ms.author: pawelwi
ms.date: 12/06/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何启用可选的媒体传输协议 (MTP) 功能通过 USB 与设备之间传输文件。
keywords: windows iot，MTP，媒体传输协议，文件传输，设备
ms.openlocfilehash: b7266321bf3fb86014bdaed8cd785f0fa057fe9a
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656623"
---
# <a name="media-transfer-protocol"></a>媒体传输协议
媒体传输协议 (MTP) 使你可以通过 USB 向/从 Windows 10 IoT Core 设备传输文件。 它允许访问设备的内部存储和 SD 卡（如果存在）。

此功能是 IoT Core 工具包的一部分，可从 [Windows 10 IoT Core 包](https://www.microsoft.com/en-us/download/details.aspx?id=55031)下载和安装。

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a>如何在运行 Windows 10 IoT Core 的设备上安装 MTP 功能

### <a name="provisioning-the-device-with-required-packages"></a>用所需的包预配设备

1. 启动 [PowerShell](../connect-your-device/PowerShell.md) 或 [SSH](../connect-your-device/SSH.md) ，并访问运行 Windows 10 IoT Core 的设备。
2. 在 PowerShell 或 SSH 中执行以下操作：
    1. 在目标计算机上创建一个临时文件夹， (例如 `C:\MTPTemp`) 。
    2. 根据设备的体系结构，将以下包从 PC 复制 (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`) 到 `C:\MTPTemp` ：
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. 从运行以下命令，将 `C:\MTPTemp` 包安装到 IoT 设备的系统映像：
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. 设备将启动到更新操作系统，安装 MTP 功能，然后重新启动到 MainOS。

### <a name="enabling-the-mtp-usb-interface"></a>启用 MTP USB 接口

设备返回到 MainOS 后，仍需更新 USBFN 配置，使其包含 MTP。 要执行此操作，需要将 MTP 添加到 USBFN 枚举的接口。
[Usb 注册表设置](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver)一文介绍了 usb 配置的详细信息。

尽管可以修改密钥下可用的默认 USBFN 配置 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` ，但建议定义自己的配置，因为系统更新将不会覆盖这些配置。

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a>使用 MTP 接口创建新的 USBFN 配置

按照以下步骤使用 MTP 添加新配置：
1. 在下添加新项 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations` 。 示例：`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`。
2. 在新项下，创建一个 `REG_MULTI_SZ` `InterfaceList` 等于的值 `MTP` 。
3. 在同一项下，创建一个 `REG_BINARY` `MSOSCompatIdDescriptor` 等于的值 `2800000000010400010000000000000000014D545000000000000000000000000000000000000000` 。
4. 在 " `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 添加新值" 下，为新创建的密钥的 `REG_SZ` `CurrentConfiguration` 名称。 在本例中，该值为 `MyConfiguration`。
5. [**可选**]在 " `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 添加新 `REG_DWORD` 值 `IncludeDefaultCfg` 等于 1" 下。 这会使 USB 驱动程序与 MTP 一起枚举默认接口。

> [!NOTE]
> 如果已在使用自定义配置，则必须对其进行修改，而不是创建一个新配置。

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a>向现有配置添加 MTP 接口

请按照以下步骤将 MTP 添加到现有的 USBFN 配置：
1. 通过检查中的值查找当前配置 `CurrentConfiguration` `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 。 如果值存在，则可以在下找到当前配置 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]` 。 否则为 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` 。
2. 在当前配置项下，将添加 `\0MTP` 到的值 `InterfaceList` 。 ***\ 0***部分用于的类型 `InterfaceList` 为 `REG_MULTI_SZ` ，它要求在值之间使用分隔符。
3. 修改 `MSOSCompatIdDescriptor` 值以包含 MTP 的描述符。 若要创建包含当前值下的所有接口的有效描述符 `InterfaceList` ，请按照 [本页](https://msdn.microsoft.com/windows/hardware/gg463179.aspx)底部提供的说明文档操作。 *OS_Desc_CompatID.doc* 提供了有关描述符的格式的说明，以及一个在描述符中包含多个接口的示例。 在同一页上还提供 MTP 的兼容和 subcompatible Id，并在其中一个示例中使用。

## <a name="how-to-include-mtp-in-your-custom-ffu"></a>如何在自定义 FFU 中包含 MTP

1. 将 **IOT_MTP** 功能 ID 添加到 OEM 输入文件中。 这等效于 "[**使用所需的包预配设备**](#provisioning-the-device-with-required-packages)" 一节中的步骤。
2. 请确保应用 "[**使用 MTP 接口创建新的 USBFN 配置**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)" 部分中提到的相同注册表更改。 按照 [这些说明](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) 操作，了解如何将注册表更改应用于 FFU。
3. 创建 image\FFU。 有关说明，请参阅 [此文](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 。

> [!WARNING]
> 不应通过 FFU 自定义来尝试修改默认配置。 系统定义的项可能会通过系统更新进行刷新/更改，并且任何自定义设置都将丢失。

## <a name="how-to-set-up-the-mtp-sd-card-filter"></a>如何设置 MTP SD 卡筛选器

默认情况下，MTP 会枚举 SD 卡的所有内容（如果它存在于设备上）。 但是，可以将此枚举限制为特定的子文件夹。 若要执行此操作，必须在注册表项下添加一个注册表值 `MTPSDFolderFilter` `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP` 。
值的类型为 `REG_SZ` ，并且应包含要进行 MTP 枚举的文件夹的相对路径。 如果文件夹尚不存在，将自动创建该文件夹。

示例路径：
- \FirstLevelDirectory;
- FirstLevelDirectory;
- \FirstLevelDirectory\SecondLevelDirectory;
- Never\Before\Created\Directory.

> [!WARNING]
> 不要使用包含驱动器号的绝对路径（例如 `C:\Some\Folder\Path` ），这可能会阻止枚举 SD 卡。

请参阅 [此链接](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) ，了解有关自定义带有特定注册表项的映像的详细信息。
