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
# <a name="media-transfer-protocol"></a><span data-ttu-id="f9e25-104">媒体传输协议</span><span class="sxs-lookup"><span data-stu-id="f9e25-104">Media Transfer Protocol</span></span>
<span data-ttu-id="f9e25-105">媒体传输协议 (MTP)，可从 Windows 10 IoT Core 设备通过 USB 来回传输文件。</span><span class="sxs-lookup"><span data-stu-id="f9e25-105">The Media Transfer Protocol (MTP) allows you to transfer files to and from your Windows 10 IoT Core device through USB.</span></span> <span data-ttu-id="f9e25-106">如果存在，它允许访问设备的内部存储和 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="f9e25-106">It allows access to the device's internal storage and the SD card, if present.</span></span>

<span data-ttu-id="f9e25-107">功能是可以下载并安装从 IoT Core 工具包的一部分[Windows 10 IoT Core 包](https://www.microsoft.com/en-us/download/details.aspx?id=55031)。</span><span class="sxs-lookup"><span data-stu-id="f9e25-107">The feature is part of the IoT Core Kits, which can be downloaded and installed from the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/download/details.aspx?id=55031).</span></span>

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="f9e25-108">如何在运行 Windows 10 IoT 核心版的设备上安装 MTP 功能</span><span class="sxs-lookup"><span data-stu-id="f9e25-108">How to install the MTP feature on a device running Windows 10 IoT Core</span></span>

### <a name="provisioning-the-device-with-required-packages"></a><span data-ttu-id="f9e25-109">预配设备所需的包</span><span class="sxs-lookup"><span data-stu-id="f9e25-109">Provisioning the device with required packages</span></span>

1. <span data-ttu-id="f9e25-110">启动[Powershell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)和访问运行 Windows 10 IoT 核心版的设备。</span><span class="sxs-lookup"><span data-stu-id="f9e25-110">Launch [Powershell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md) and access your device running Windows 10 IoT Core.</span></span>
2. <span data-ttu-id="f9e25-111">从 Powershell 或 SSH，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f9e25-111">From Powershell or SSH, do the following:</span></span>
    1. <span data-ttu-id="f9e25-112">在目标计算机上创建临时文件夹（例如 `C:\MTPTemp`）。</span><span class="sxs-lookup"><span data-stu-id="f9e25-112">Create a temporary folder on the target machine (e.g. `C:\MTPTemp`).</span></span>
    2. <span data-ttu-id="f9e25-113">基于设备的体系结构，将以下包从您的 PC 复制 (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`) 到`C:\MTPTemp`:</span><span class="sxs-lookup"><span data-stu-id="f9e25-113">Based on your device's architecture, copy the following packages from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`) to `C:\MTPTemp`:</span></span>
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. <span data-ttu-id="f9e25-114">运行以下命令从`C:\MTPTemp`若要将包安装到你的 IoT 设备的系统映像：</span><span class="sxs-lookup"><span data-stu-id="f9e25-114">Run these commands from `C:\MTPTemp` to install the packages to your IoT device's system image:</span></span>
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. <span data-ttu-id="f9e25-115">设备将启动到更新 OS，安装 MTP 功能，然后重启到 MainOS。</span><span class="sxs-lookup"><span data-stu-id="f9e25-115">The device will boot to the Update OS, install the MTP feature, and reboot to the MainOS.</span></span>

### <a name="enabling-the-mtp-usb-interface"></a><span data-ttu-id="f9e25-116">启用 MTP USB 接口</span><span class="sxs-lookup"><span data-stu-id="f9e25-116">Enabling the MTP USB interface</span></span>

<span data-ttu-id="f9e25-117">设备到 MainOS 返回后，一旦 USBFN 配置仍需要更新，以包含 MTP。</span><span class="sxs-lookup"><span data-stu-id="f9e25-117">Once the device comes back to the MainOS, the USBFN configuration still needs to be updated to include MTP.</span></span> <span data-ttu-id="f9e25-118">为此，需要将 MTP 添加到 USBFN 枚举的接口。</span><span class="sxs-lookup"><span data-stu-id="f9e25-118">In order to do that, you will need to add MTP to the interfaces enumerated by USBFN.</span></span>
<span data-ttu-id="f9e25-119">[USB 注册表设置](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver)文章介绍了 USB 的配置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f9e25-119">The [USB registry settings](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver) article explains the details of USB's configuration.</span></span>

<span data-ttu-id="f9e25-120">尽管可以修改默认 USBFN 配置下提供`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`密钥，建议定义您自己，因为它们将不会被覆盖的系统更新。</span><span class="sxs-lookup"><span data-stu-id="f9e25-120">While you can modify the default USBFN configuration available under the `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` key, it is recommended to define your own, as they will not get overwritten by system updates.</span></span>

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a><span data-ttu-id="f9e25-121">与 MTP 接口创建新的 USBFN 配置</span><span class="sxs-lookup"><span data-stu-id="f9e25-121">Creating a new USBFN configuration with the MTP interface</span></span>

<span data-ttu-id="f9e25-122">请按照以下步骤添加新的配置与 MTP 操作：</span><span class="sxs-lookup"><span data-stu-id="f9e25-122">Follow these steps to add a new configuration with MTP:</span></span>
1. <span data-ttu-id="f9e25-123">添加新的密钥下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-123">Add a new key under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations`.</span></span> <span data-ttu-id="f9e25-124">例如：`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-124">Example: `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`.</span></span>
2. <span data-ttu-id="f9e25-125">在新的项下创建`REG_MULTI_SZ`值`InterfaceList`等于`MTP`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-125">Under the new key create a `REG_MULTI_SZ` value `InterfaceList` equal to `MTP`.</span></span>
3. <span data-ttu-id="f9e25-126">在同一个项下创建`REG_BINARY`值`MSOSCompatIdDescriptor`等于`2800000000010400010000000000000000014D545000000000000000000000000000000000000000`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-126">Under the same key create a `REG_BINARY` value `MSOSCompatIdDescriptor` equal to `2800000000010400010000000000000000014D545000000000000000000000000000000000000000`.</span></span>
4. <span data-ttu-id="f9e25-127">下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`添加一个新`REG_SZ`值`CurrentConfiguration`等于新创建的密钥的名称。</span><span class="sxs-lookup"><span data-stu-id="f9e25-127">Under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` add a new `REG_SZ` value `CurrentConfiguration` equal to the name of the newly created key.</span></span> <span data-ttu-id="f9e25-128">在这种情况下会`MyConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-128">In this case it would be `MyConfiguration`.</span></span>
5. <span data-ttu-id="f9e25-129">[**可选**] 下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`添加新`REG_DWORD`值`IncludeDefaultCfg`等于 1。</span><span class="sxs-lookup"><span data-stu-id="f9e25-129">[**Optional**] Under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` add a new `REG_DWORD` value `IncludeDefaultCfg` equal to 1.</span></span> <span data-ttu-id="f9e25-130">这将使枚举以及 MTP 默认接口的 USB 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="f9e25-130">This will make the USB driver enumerate the default interfaces along with MTP.</span></span>

> [!NOTE]
> <span data-ttu-id="f9e25-131">如果你已在使用必须对其进行修改而不是创建一个新的自定义配置。</span><span class="sxs-lookup"><span data-stu-id="f9e25-131">If you are already using a custom configuration you will have to modify it instead of creating a new one.</span></span>

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a><span data-ttu-id="f9e25-132">将 MTP 接口添加到现有的配置</span><span class="sxs-lookup"><span data-stu-id="f9e25-132">Adding the MTP interface to an existing configuration</span></span>

<span data-ttu-id="f9e25-133">请按照以下步骤添加到现有 USBFN 配置 MTP 操作：</span><span class="sxs-lookup"><span data-stu-id="f9e25-133">Follow these steps to add MTP to an existing USBFN configuration:</span></span>
1. <span data-ttu-id="f9e25-134">通过检查查找当前的配置`CurrentConfiguration`值下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-134">Find the current configuration by checking the `CurrentConfiguration` value under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`.</span></span> <span data-ttu-id="f9e25-135">如果值存在，则可在当前配置下找到`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-135">If the value is present, then the current configuration can be found under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]`.</span></span> <span data-ttu-id="f9e25-136">否则将下`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-136">Otherwise it is under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`.</span></span>
2. <span data-ttu-id="f9e25-137">在当前的配置项下添加`\0MTP`的值`InterfaceList`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-137">Under the current configuration key add `\0MTP` to the value of `InterfaceList`.</span></span> <span data-ttu-id="f9e25-138">***\0***为的类型使用部分`InterfaceList`是`REG_MULTI_SZ`和它需要此值之间的分隔符。</span><span class="sxs-lookup"><span data-stu-id="f9e25-138">The ***\0*** part is used as the type of `InterfaceList` is `REG_MULTI_SZ` and it requires this separator between values.</span></span>
3. <span data-ttu-id="f9e25-139">修改`MSOSCompatIdDescriptor`值，以包括 MTP 的描述符。</span><span class="sxs-lookup"><span data-stu-id="f9e25-139">Modify the `MSOSCompatIdDescriptor` value to include the MTP's descriptor.</span></span> <span data-ttu-id="f9e25-140">若要创建一个包含所有接口当前下的有效说明符`InterfaceList`值，请按照在底部提供的说明文档[本页](https://msdn.microsoft.com/windows/hardware/gg463179.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f9e25-140">In order to create a valid descriptor containing all interfaces currently under the `InterfaceList` value, please follow the instructions documentation available at the bottom of [this page](https://msdn.microsoft.com/windows/hardware/gg463179.aspx).</span></span> <span data-ttu-id="f9e25-141">*OS_Desc_CompatID.doc*提供描述符的格式和描述符中包括多个接口的示例的说明。</span><span class="sxs-lookup"><span data-stu-id="f9e25-141">*OS_Desc_CompatID.doc* gives an explanation of the descriptor's format and an example of including multiple interfaces in the descriptor.</span></span> <span data-ttu-id="f9e25-142">MTP 的兼容和次级兼容 Id 也是可在同一页上，并使用中的一个示例。</span><span class="sxs-lookup"><span data-stu-id="f9e25-142">MTP's compatible and sub-compatible IDs are also available on the same page and are used in one of the examples.</span></span>

## <a name="how-to-include-mtp-in-your-custom-ffu"></a><span data-ttu-id="f9e25-143">如何在您的自定义 FFU 中包含 MTP</span><span class="sxs-lookup"><span data-stu-id="f9e25-143">How to include MTP in Your Custom FFU</span></span>

1. <span data-ttu-id="f9e25-144">添加**IOT_MTP**功能到 OEM 输入文件的 ID。</span><span class="sxs-lookup"><span data-stu-id="f9e25-144">Add **IOT_MTP** feature ID to the OEM Input file.</span></span> <span data-ttu-id="f9e25-145">这是从步骤等效项"[**预配所需的包与设备**](#provisioning-the-device-with-required-packages)"部分。</span><span class="sxs-lookup"><span data-stu-id="f9e25-145">This is an equivalent of following the steps from the "[**Provisioning the device with required packages**](#provisioning-the-device-with-required-packages)" section.</span></span>
2. <span data-ttu-id="f9e25-146">请确保应用相同的注册表更改，如中所述"[**与 MTP 接口创建新的 USBFN 配置**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)"部分。</span><span class="sxs-lookup"><span data-stu-id="f9e25-146">Make sure to apply the same registry changes as mentioned in the "[**Creating a new USBFN configuration with the MTP interface**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)" section.</span></span> <span data-ttu-id="f9e25-147">请按照[这些说明](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image)若要了解如何应用于 FFU 注册表更改。</span><span class="sxs-lookup"><span data-stu-id="f9e25-147">Follow [these instructions](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) to learn how to apply registry changes to an FFU.</span></span>
3. <span data-ttu-id="f9e25-148">创建 image\FFU。</span><span class="sxs-lookup"><span data-stu-id="f9e25-148">Create the image\FFU.</span></span> <span data-ttu-id="f9e25-149">读取[这篇文章](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)有关的说明。</span><span class="sxs-lookup"><span data-stu-id="f9e25-149">Read [this article](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>

> [!WARNING]
> <span data-ttu-id="f9e25-150">通过 FFU 自定义项不应尝试修改默认配置。</span><span class="sxs-lookup"><span data-stu-id="f9e25-150">Modifying the default configuration should not be attempted through FFU customization.</span></span> <span data-ttu-id="f9e25-151">系统定义的项的系统更新刷新/更改且所有自定义设置都将丢失。</span><span class="sxs-lookup"><span data-stu-id="f9e25-151">System-defined entries may be refreshed/changed by a system update and any custom settings will be lost.</span></span>

## <a name="how-to-setup-the-mtp-sd-card-filter"></a><span data-ttu-id="f9e25-152">如何设置 MTP SD 卡筛选器</span><span class="sxs-lookup"><span data-stu-id="f9e25-152">How to setup the MTP SD card filter</span></span>

<span data-ttu-id="f9e25-153">默认情况下 MTP 将枚举中的所有内容的 SD 卡中，如果存在在设备上。</span><span class="sxs-lookup"><span data-stu-id="f9e25-153">By default MTP will enumerate all of the contents of an SD card, if it is present on the device.</span></span> <span data-ttu-id="f9e25-154">很有可能，但是，若要限制到特定的子文件夹的此枚举。</span><span class="sxs-lookup"><span data-stu-id="f9e25-154">It is possible, however, to limit this enumeration to a specific subfolder.</span></span> <span data-ttu-id="f9e25-155">为了执行此操作，必须添加注册表值`MTPSDFolderFilter`注册表项下`HKEY_LOCAL_MACHINE\Software\Microsoft\MTP`。</span><span class="sxs-lookup"><span data-stu-id="f9e25-155">In order to do so, you must add a registry value `MTPSDFolderFilter` under the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP`.</span></span>
<span data-ttu-id="f9e25-156">值为类型`REG_SZ`，并且应包含你想 MTP 要枚举的文件夹的相对路径。</span><span class="sxs-lookup"><span data-stu-id="f9e25-156">The value is of type `REG_SZ` and should contain a relative path to the folder you would like MTP to enumerate.</span></span> <span data-ttu-id="f9e25-157">如果尚不存在，则获取自动创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="f9e25-157">The folder will get automatically created if it does not already exist.</span></span>

<span data-ttu-id="f9e25-158">示例路径：</span><span class="sxs-lookup"><span data-stu-id="f9e25-158">Sample paths:</span></span>
- <span data-ttu-id="f9e25-159">\FirstLevelDirectory;</span><span class="sxs-lookup"><span data-stu-id="f9e25-159">\FirstLevelDirectory;</span></span>
- <span data-ttu-id="f9e25-160">FirstLevelDirectory;</span><span class="sxs-lookup"><span data-stu-id="f9e25-160">FirstLevelDirectory;</span></span>
- <span data-ttu-id="f9e25-161">\FirstLevelDirectory\SecondLevelDirectory;</span><span class="sxs-lookup"><span data-stu-id="f9e25-161">\FirstLevelDirectory\SecondLevelDirectory;</span></span>
- <span data-ttu-id="f9e25-162">Never\Before\Created\Directory.</span><span class="sxs-lookup"><span data-stu-id="f9e25-162">Never\Before\Created\Directory.</span></span>

> [!WARNING]
> <span data-ttu-id="f9e25-163">不要使用绝对路径包含类似的驱动器号`C:\Some\Folder\Path`-这可能会阻止正在枚举 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="f9e25-163">Do not use an absolute path containing the drive letter like `C:\Some\Folder\Path` - this might prevent the SD card from being enumerated.</span></span>

<span data-ttu-id="f9e25-164">请参阅[此链接](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image)有关自定义映像与特定的注册表项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f9e25-164">See [this link](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) for details about customizing your image with specific registry entries.</span></span>
