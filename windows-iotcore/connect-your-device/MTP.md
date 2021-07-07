---
title: 媒体传输协议
author: PawelWMS
ms.author: pawelwi
ms.date: 12/06/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何启用可选的媒体传输协议 (MTP) 功能，以通过 USB 向/从设备传输文件。
keywords: windows iot， MTP， 媒体传输协议， 文件传输， 设备
ms.openlocfilehash: 0d4569bce99decd0ba2ec4f1e84f6ae4b6b739ad
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229984"
---
# <a name="media-transfer-protocol"></a>媒体传输协议
使用媒体传输协议 (MTP) ，可以通过 USB 将文件Windows 10 IoT 核心版设备中传输。 它允许访问设备的内部存储和 SD 卡（如果存在）。

此功能是 IoT 核心工具包的一部分，可从应用程序包[下载Windows 10 IoT 核心版安装](https://www.microsoft.com/en-us/download/details.aspx?id=55031)。

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a>如何在运行 MTP 的设备上安装 MTP Windows 10 IoT 核心版

### <a name="provisioning-the-device-with-required-packages"></a>使用所需的包预配设备

1. 启动[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)并访问运行 Windows 10 IoT 核心版。
2. 在 PowerShell 或 SSH 中执行以下操作：
    1. 在目标计算机上创建一个 (文件夹，例如 `C:\MTPTemp`) 。
    2. 根据设备的体系结构，将以下包从电脑 () `C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre` 复制到 `C:\MTPTemp` ：
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. 从 运行以下 `C:\MTPTemp` 命令，将包安装到 IoT 设备的系统映像：
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. 设备将启动到更新 OS，安装 MTP 功能，然后重新启动到 MainOS。

### <a name="enabling-the-mtp-usb-interface"></a>启用 MTP USB 接口

设备返回到 MainOS 后，仍然需要更新 USBFN 配置以包括 MTP。 为此，需要将 MTP 添加到 USBFN 枚举的接口。
[USB 注册表设置](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver)一文介绍了 USB 配置的详细信息。

虽然可以修改密钥下可用的默认 USBFN 配置，但建议定义自己的配置，因为它们不会被系统更新 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` 覆盖。

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a>使用 MTP 接口创建新的 USBFN 配置

按照以下步骤使用 MTP 添加新配置：
1. 在 下添加新密钥 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations` 。 示例：`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`。
2. 在新键下，创建 `REG_MULTI_SZ` 一个 `InterfaceList` 等于 的值 `MTP` 。
3. 在同一键下，创建 `REG_BINARY` 一 `MSOSCompatIdDescriptor` 个等于 的值 `2800000000010400010000000000000000014D545000000000000000000000000000000000000000` 。
4. 在 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 下， `REG_SZ` 添加新 `CurrentConfiguration` 值，该值等于新创建的密钥的名称。 在本例中，该值为 `MyConfiguration`。
5. [**可选**]在 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 下添加一 `REG_DWORD` 个等于 `IncludeDefaultCfg` 1 的新值。 这样，USB 驱动程序就会枚举默认接口以及 MTP。

> [!NOTE]
> 如果已在使用自定义配置，必须对其进行修改，而不是创建新的配置。

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a>将 MTP 接口添加到现有配置

按照以下步骤将 MTP 添加到现有的 USBFN 配置：
1. 通过检查 下的值查找 `CurrentConfiguration` 当前配置 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 。 如果值存在，可以在 下找到当前配置 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]` 。 否则，它位于 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` 下。
2. 在当前配置键下，将 `\0MTP` 添加到 的值 `InterfaceList` 。 ***\0*** 部分用作 的类型 `InterfaceList` 为 ， `REG_MULTI_SZ` 它需要值之间的此分隔符。
3. 修改 `MSOSCompatIdDescriptor` 值以包括 MTP 的描述符。 若要创建包含值下当前所有接口的有效描述符，请按照此页底部的说明 `InterfaceList` [文档进行操作](https://msdn.microsoft.com/windows/hardware/gg463179.aspx)。 *OS_Desc_CompatID.doc* 说明描述符的格式，以及描述符中包含多个接口的示例。 MTP 的兼容和子兼容性的 ID 也在同一页上提供，并用于其中一个示例。

## <a name="how-to-include-mtp-in-your-custom-ffu"></a>如何在自定义 FFU 中包括 MTP

1. 将 **IOT_MTP** ID 添加到 OEM 输入文件。 这相当于按照"使用所需包预配设备 [**"部分中的步骤**](#provisioning-the-device-with-required-packages)操作。
2. 请确保应用与"使用 MTP 接口创建新的 [**USBFN**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)配置"部分中提到的相同的注册表更改。 按照 [这些](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) 说明了解如何将注册表更改应用于 FFU。
3. 创建 image\FFU。 有关 [说明，](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 请阅读此文。

> [!WARNING]
> 不应通过 FFU 自定义来尝试修改默认配置。 系统定义的条目可能会由系统更新刷新/更改，任何自定义设置都将丢失。

## <a name="how-to-set-up-the-mtp-sd-card-filter"></a>如何设置 MTP SD 卡筛选器

默认情况下，MTP 将枚举 SD 卡的所有内容（如果设备上存在）。 但是，可以限制此枚举到特定的子文件夹。 为此，必须在注册表项 下添加 `MTPSDFolderFilter` 注册表值 `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP` 。
该值的类型为 `REG_SZ` ，并且应包含要 MTP 枚举的文件夹的相对路径。 如果文件夹不存在，则会自动创建该文件夹。

示例路径：
- \FirstLevelDirectory;
- FirstLevelDirectory;
- \FirstLevelDirectory\SecondLevelDirectory;
- Never\Before\Created\Directory。

> [!WARNING]
> 请勿使用包含驱动器号的绝对路径（如 `C:\Some\Folder\Path` ）- 这可能会阻止枚举 SD 卡。

有关 [使用](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) 特定注册表项自定义映像的详细信息，请参阅此链接。
