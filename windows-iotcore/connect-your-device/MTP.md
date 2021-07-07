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
# <a name="media-transfer-protocol"></a><span data-ttu-id="48037-104">媒体传输协议</span><span class="sxs-lookup"><span data-stu-id="48037-104">Media Transfer Protocol</span></span>
<span data-ttu-id="48037-105">使用媒体传输协议 (MTP) ，可以通过 USB 将文件Windows 10 IoT 核心版设备中传输。</span><span class="sxs-lookup"><span data-stu-id="48037-105">The Media Transfer Protocol (MTP) allows you to transfer files to and from your Windows 10 IoT Core device through USB.</span></span> <span data-ttu-id="48037-106">它允许访问设备的内部存储和 SD 卡（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="48037-106">It allows access to the device's internal storage and the SD card, if present.</span></span>

<span data-ttu-id="48037-107">此功能是 IoT 核心工具包的一部分，可从应用程序包[下载Windows 10 IoT 核心版安装](https://www.microsoft.com/en-us/download/details.aspx?id=55031)。</span><span class="sxs-lookup"><span data-stu-id="48037-107">The feature is part of the IoT Core Kits, which can be downloaded and installed from the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/download/details.aspx?id=55031).</span></span>

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="48037-108">如何在运行 MTP 的设备上安装 MTP Windows 10 IoT 核心版</span><span class="sxs-lookup"><span data-stu-id="48037-108">How to install the MTP feature on a device running Windows 10 IoT Core</span></span>

### <a name="provisioning-the-device-with-required-packages"></a><span data-ttu-id="48037-109">使用所需的包预配设备</span><span class="sxs-lookup"><span data-stu-id="48037-109">Provisioning the device with required packages</span></span>

1. <span data-ttu-id="48037-110">启动[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)并访问运行 Windows 10 IoT 核心版。</span><span class="sxs-lookup"><span data-stu-id="48037-110">Launch [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md) and access your device running Windows 10 IoT Core.</span></span>
2. <span data-ttu-id="48037-111">在 PowerShell 或 SSH 中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="48037-111">From PowerShell or SSH, do the following:</span></span>
    1. <span data-ttu-id="48037-112">在目标计算机上创建一个 (文件夹，例如 `C:\MTPTemp`) 。</span><span class="sxs-lookup"><span data-stu-id="48037-112">Create a temporary folder on the target machine (e.g. `C:\MTPTemp`).</span></span>
    2. <span data-ttu-id="48037-113">根据设备的体系结构，将以下包从电脑 () `C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre` 复制到 `C:\MTPTemp` ：</span><span class="sxs-lookup"><span data-stu-id="48037-113">Based on your device's architecture, copy the following packages from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`) to `C:\MTPTemp`:</span></span>
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. <span data-ttu-id="48037-114">从 运行以下 `C:\MTPTemp` 命令，将包安装到 IoT 设备的系统映像：</span><span class="sxs-lookup"><span data-stu-id="48037-114">Run these commands from `C:\MTPTemp` to install the packages to your IoT device's system image:</span></span>
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. <span data-ttu-id="48037-115">设备将启动到更新 OS，安装 MTP 功能，然后重新启动到 MainOS。</span><span class="sxs-lookup"><span data-stu-id="48037-115">The device will boot to the Update OS, install the MTP feature, and reboot to the MainOS.</span></span>

### <a name="enabling-the-mtp-usb-interface"></a><span data-ttu-id="48037-116">启用 MTP USB 接口</span><span class="sxs-lookup"><span data-stu-id="48037-116">Enabling the MTP USB interface</span></span>

<span data-ttu-id="48037-117">设备返回到 MainOS 后，仍然需要更新 USBFN 配置以包括 MTP。</span><span class="sxs-lookup"><span data-stu-id="48037-117">Once the device comes back to the MainOS, the USBFN configuration still needs to be updated to include MTP.</span></span> <span data-ttu-id="48037-118">为此，需要将 MTP 添加到 USBFN 枚举的接口。</span><span class="sxs-lookup"><span data-stu-id="48037-118">In order to do that, you will need to add MTP to the interfaces enumerated by USBFN.</span></span>
<span data-ttu-id="48037-119">[USB 注册表设置](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver)一文介绍了 USB 配置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="48037-119">The [USB registry settings](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver) article explains the details of USB's configuration.</span></span>

<span data-ttu-id="48037-120">虽然可以修改密钥下可用的默认 USBFN 配置，但建议定义自己的配置，因为它们不会被系统更新 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` 覆盖。</span><span class="sxs-lookup"><span data-stu-id="48037-120">While you can modify the default USBFN configuration available under the `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` key, it is recommended to define your own, as they will not get overwritten by system updates.</span></span>

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a><span data-ttu-id="48037-121">使用 MTP 接口创建新的 USBFN 配置</span><span class="sxs-lookup"><span data-stu-id="48037-121">Creating a new USBFN configuration with the MTP interface</span></span>

<span data-ttu-id="48037-122">按照以下步骤使用 MTP 添加新配置：</span><span class="sxs-lookup"><span data-stu-id="48037-122">Follow these steps to add a new configuration with MTP:</span></span>
1. <span data-ttu-id="48037-123">在 下添加新密钥 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations` 。</span><span class="sxs-lookup"><span data-stu-id="48037-123">Add a new key under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations`.</span></span> <span data-ttu-id="48037-124">示例：`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="48037-124">Example: `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`.</span></span>
2. <span data-ttu-id="48037-125">在新键下，创建 `REG_MULTI_SZ` 一个 `InterfaceList` 等于 的值 `MTP` 。</span><span class="sxs-lookup"><span data-stu-id="48037-125">Under the new key, create a `REG_MULTI_SZ` value `InterfaceList` equal to `MTP`.</span></span>
3. <span data-ttu-id="48037-126">在同一键下，创建 `REG_BINARY` 一 `MSOSCompatIdDescriptor` 个等于 的值 `2800000000010400010000000000000000014D545000000000000000000000000000000000000000` 。</span><span class="sxs-lookup"><span data-stu-id="48037-126">Under the same key, create a `REG_BINARY` value `MSOSCompatIdDescriptor` equal to `2800000000010400010000000000000000014D545000000000000000000000000000000000000000`.</span></span>
4. <span data-ttu-id="48037-127">在 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 下， `REG_SZ` 添加新 `CurrentConfiguration` 值，该值等于新创建的密钥的名称。</span><span class="sxs-lookup"><span data-stu-id="48037-127">Under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` add a new `REG_SZ` value `CurrentConfiguration` equal to the name of the newly created key.</span></span> <span data-ttu-id="48037-128">在本例中，该值为 `MyConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="48037-128">In this case, it would be `MyConfiguration`.</span></span>
5. <span data-ttu-id="48037-129">[**可选**]在 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 下添加一 `REG_DWORD` 个等于 `IncludeDefaultCfg` 1 的新值。</span><span class="sxs-lookup"><span data-stu-id="48037-129">[**Optional**] Under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` add a new `REG_DWORD` value `IncludeDefaultCfg` equal to 1.</span></span> <span data-ttu-id="48037-130">这样，USB 驱动程序就会枚举默认接口以及 MTP。</span><span class="sxs-lookup"><span data-stu-id="48037-130">This will make the USB driver enumerate the default interfaces along with MTP.</span></span>

> [!NOTE]
> <span data-ttu-id="48037-131">如果已在使用自定义配置，必须对其进行修改，而不是创建新的配置。</span><span class="sxs-lookup"><span data-stu-id="48037-131">If you are already using a custom configuration you will have to modify it instead of creating a new one.</span></span>

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a><span data-ttu-id="48037-132">将 MTP 接口添加到现有配置</span><span class="sxs-lookup"><span data-stu-id="48037-132">Adding the MTP interface to an existing configuration</span></span>

<span data-ttu-id="48037-133">按照以下步骤将 MTP 添加到现有的 USBFN 配置：</span><span class="sxs-lookup"><span data-stu-id="48037-133">Follow these steps to add MTP to an existing USBFN configuration:</span></span>
1. <span data-ttu-id="48037-134">通过检查 下的值查找 `CurrentConfiguration` 当前配置 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 。</span><span class="sxs-lookup"><span data-stu-id="48037-134">Find the current configuration by checking the `CurrentConfiguration` value under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`.</span></span> <span data-ttu-id="48037-135">如果值存在，可以在 下找到当前配置 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]` 。</span><span class="sxs-lookup"><span data-stu-id="48037-135">If the value is present, then the current configuration can be found under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]`.</span></span> <span data-ttu-id="48037-136">否则，它位于 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` 下。</span><span class="sxs-lookup"><span data-stu-id="48037-136">Otherwise it is under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`.</span></span>
2. <span data-ttu-id="48037-137">在当前配置键下，将 `\0MTP` 添加到 的值 `InterfaceList` 。</span><span class="sxs-lookup"><span data-stu-id="48037-137">Under the current configuration key, add `\0MTP` to the value of `InterfaceList`.</span></span> <span data-ttu-id="48037-138">***\0*** 部分用作 的类型 `InterfaceList` 为 ， `REG_MULTI_SZ` 它需要值之间的此分隔符。</span><span class="sxs-lookup"><span data-stu-id="48037-138">The ***\0*** part is used as the type of `InterfaceList` is `REG_MULTI_SZ` and it requires this separator between values.</span></span>
3. <span data-ttu-id="48037-139">修改 `MSOSCompatIdDescriptor` 值以包括 MTP 的描述符。</span><span class="sxs-lookup"><span data-stu-id="48037-139">Modify the `MSOSCompatIdDescriptor` value to include the MTP's descriptor.</span></span> <span data-ttu-id="48037-140">若要创建包含值下当前所有接口的有效描述符，请按照此页底部的说明 `InterfaceList` [文档进行操作](https://msdn.microsoft.com/windows/hardware/gg463179.aspx)。</span><span class="sxs-lookup"><span data-stu-id="48037-140">In order to create a valid descriptor containing all interfaces currently under the `InterfaceList` value, please follow the instructions documentation available at the bottom of [this page](https://msdn.microsoft.com/windows/hardware/gg463179.aspx).</span></span> <span data-ttu-id="48037-141">*OS_Desc_CompatID.doc* 说明描述符的格式，以及描述符中包含多个接口的示例。</span><span class="sxs-lookup"><span data-stu-id="48037-141">*OS_Desc_CompatID.doc* gives an explanation of the descriptor's format and an example of including multiple interfaces in the descriptor.</span></span> <span data-ttu-id="48037-142">MTP 的兼容和子兼容性的 ID 也在同一页上提供，并用于其中一个示例。</span><span class="sxs-lookup"><span data-stu-id="48037-142">MTP's compatible and subcompatible IDs are also available on the same page and are used in one of the examples.</span></span>

## <a name="how-to-include-mtp-in-your-custom-ffu"></a><span data-ttu-id="48037-143">如何在自定义 FFU 中包括 MTP</span><span class="sxs-lookup"><span data-stu-id="48037-143">How to include MTP in Your Custom FFU</span></span>

1. <span data-ttu-id="48037-144">将 **IOT_MTP** ID 添加到 OEM 输入文件。</span><span class="sxs-lookup"><span data-stu-id="48037-144">Add **IOT_MTP** feature ID to the OEM Input file.</span></span> <span data-ttu-id="48037-145">这相当于按照"使用所需包预配设备 [**"部分中的步骤**](#provisioning-the-device-with-required-packages)操作。</span><span class="sxs-lookup"><span data-stu-id="48037-145">This is an equivalent of following the steps from the "[**Provisioning the device with required packages**](#provisioning-the-device-with-required-packages)" section.</span></span>
2. <span data-ttu-id="48037-146">请确保应用与"使用 MTP 接口创建新的 [**USBFN**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)配置"部分中提到的相同的注册表更改。</span><span class="sxs-lookup"><span data-stu-id="48037-146">Make sure to apply the same registry changes as mentioned in the "[**Creating a new USBFN configuration with the MTP interface**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)" section.</span></span> <span data-ttu-id="48037-147">按照 [这些](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) 说明了解如何将注册表更改应用于 FFU。</span><span class="sxs-lookup"><span data-stu-id="48037-147">Follow [these instructions](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) to learn how to apply registry changes to an FFU.</span></span>
3. <span data-ttu-id="48037-148">创建 image\FFU。</span><span class="sxs-lookup"><span data-stu-id="48037-148">Create the image\FFU.</span></span> <span data-ttu-id="48037-149">有关 [说明，](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 请阅读此文。</span><span class="sxs-lookup"><span data-stu-id="48037-149">Read [this article](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>

> [!WARNING]
> <span data-ttu-id="48037-150">不应通过 FFU 自定义来尝试修改默认配置。</span><span class="sxs-lookup"><span data-stu-id="48037-150">Modifying the default configuration should not be attempted through FFU customization.</span></span> <span data-ttu-id="48037-151">系统定义的条目可能会由系统更新刷新/更改，任何自定义设置都将丢失。</span><span class="sxs-lookup"><span data-stu-id="48037-151">System-defined entries may be refreshed/changed by a system update and any custom settings will be lost.</span></span>

## <a name="how-to-set-up-the-mtp-sd-card-filter"></a><span data-ttu-id="48037-152">如何设置 MTP SD 卡筛选器</span><span class="sxs-lookup"><span data-stu-id="48037-152">How to set up the MTP SD card filter</span></span>

<span data-ttu-id="48037-153">默认情况下，MTP 将枚举 SD 卡的所有内容（如果设备上存在）。</span><span class="sxs-lookup"><span data-stu-id="48037-153">By default MTP will enumerate all of the contents of an SD card, if it is present on the device.</span></span> <span data-ttu-id="48037-154">但是，可以限制此枚举到特定的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="48037-154">It is possible, however, to limit this enumeration to a specific subfolder.</span></span> <span data-ttu-id="48037-155">为此，必须在注册表项 下添加 `MTPSDFolderFilter` 注册表值 `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP` 。</span><span class="sxs-lookup"><span data-stu-id="48037-155">In order to do so, you must add a registry value `MTPSDFolderFilter` under the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP`.</span></span>
<span data-ttu-id="48037-156">该值的类型为 `REG_SZ` ，并且应包含要 MTP 枚举的文件夹的相对路径。</span><span class="sxs-lookup"><span data-stu-id="48037-156">The value is of type `REG_SZ` and should contain a relative path to the folder you would like MTP to enumerate.</span></span> <span data-ttu-id="48037-157">如果文件夹不存在，则会自动创建该文件夹。</span><span class="sxs-lookup"><span data-stu-id="48037-157">The folder will get automatically created if it does not already exist.</span></span>

<span data-ttu-id="48037-158">示例路径：</span><span class="sxs-lookup"><span data-stu-id="48037-158">Sample paths:</span></span>
- <span data-ttu-id="48037-159">\FirstLevelDirectory;</span><span class="sxs-lookup"><span data-stu-id="48037-159">\FirstLevelDirectory;</span></span>
- <span data-ttu-id="48037-160">FirstLevelDirectory;</span><span class="sxs-lookup"><span data-stu-id="48037-160">FirstLevelDirectory;</span></span>
- <span data-ttu-id="48037-161">\FirstLevelDirectory\SecondLevelDirectory;</span><span class="sxs-lookup"><span data-stu-id="48037-161">\FirstLevelDirectory\SecondLevelDirectory;</span></span>
- <span data-ttu-id="48037-162">Never\Before\Created\Directory。</span><span class="sxs-lookup"><span data-stu-id="48037-162">Never\Before\Created\Directory.</span></span>

> [!WARNING]
> <span data-ttu-id="48037-163">请勿使用包含驱动器号的绝对路径（如 `C:\Some\Folder\Path` ）- 这可能会阻止枚举 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="48037-163">Do not use an absolute path containing the drive letter like `C:\Some\Folder\Path` - this might prevent the SD card from being enumerated.</span></span>

<span data-ttu-id="48037-164">有关 [使用](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) 特定注册表项自定义映像的详细信息，请参阅此链接。</span><span class="sxs-lookup"><span data-stu-id="48037-164">See [this link](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) for details about customizing your image with specific registry entries.</span></span>
