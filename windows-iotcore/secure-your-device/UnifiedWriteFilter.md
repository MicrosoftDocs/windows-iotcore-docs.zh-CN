---
title: 使用统一的写入筛选器
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用统一写入筛选器来防止数据写入物理存储介质。
keywords: windows iot，统一写入筛选器，安全性、 内存、 存储媒体
ms.openlocfilehash: d1d6927fe19b5888ef0393d0b101065096cd9f63
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512099"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a><span data-ttu-id="38563-104">在 Windows 10 IoT Core 上使用统一的写入筛选器 (UWF)</span><span class="sxs-lookup"><span data-stu-id="38563-104">Using the Unified Write Filter (UWF) on Windows 10 IoT Core</span></span>

> [!WARNING]
> <span data-ttu-id="38563-105">UWF 不支持动态磁盘。</span><span class="sxs-lookup"><span data-stu-id="38563-105">The dynamic disk is not supported for the UWF.</span></span>

<span data-ttu-id="38563-106">统一写入筛选器 (UWF) 是一项功能，防止数据写入物理存储介质。</span><span class="sxs-lookup"><span data-stu-id="38563-106">The Unified Write Filter (UWF) is a feature that protects physical storage media from data writes.</span></span> <span data-ttu-id="38563-107">UWF 将拦截所有针对受保护卷的写入尝试，并将这些写入尝试重定向到虚拟覆盖。</span><span class="sxs-lookup"><span data-stu-id="38563-107">UWF intercepts all write attempts to a protected volume and redirects those write attempts to a virtual overlay.</span></span> <span data-ttu-id="38563-108">这可改进设备的可靠性和稳定性，同时减少写入敏感媒体（例如，诸如固态硬盘等闪存媒体）的损耗。</span><span class="sxs-lookup"><span data-stu-id="38563-108">This improves the reliability and stability of your device and reduces the wear on write-sensitive media, such as flash memory media like solid-state drives.</span></span>

<span data-ttu-id="38563-109">阅读我们的文档[统一写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)有关详细信息。</span><span class="sxs-lookup"><span data-stu-id="38563-109">Read our documentation on the [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) for more information.</span></span>

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="38563-110">如何在运行 Windows 10 IoT 核心版的设备上安装 UWF</span><span class="sxs-lookup"><span data-stu-id="38563-110">How to Install UWF on a device running Windows 10 IoT Core</span></span>

* <span data-ttu-id="38563-111">如果你还没有 Windows 10 IoT Core 工具包的当前版本，下载并安装[Windows 10 IoT Core 包](https://www.microsoft.com/en-us/software-download/windows10iotcore)。</span><span class="sxs-lookup"><span data-stu-id="38563-111">If you do not have the current version of the Windows 10 IoT Core Kits yet, download and install the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span></span>
* <span data-ttu-id="38563-112">基于设备体系结构上，复制 UWF 包 (`Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`和`Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`) 从您的 PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) 到设备 (例如，对于[Windows 文件共享](../manage-your-device/WindowsFileSharing.md))。</span><span class="sxs-lookup"><span data-stu-id="38563-112">Based on your device architecture, copy UWF packages ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` and `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) to the device (for example, with [Windows file sharing](../manage-your-device/WindowsFileSharing.md)).</span></span>
* <span data-ttu-id="38563-113">启动[SSH](../connect-your-device/SSH.md)或[Powershell](../connect-your-device/PowerShell.md)和访问运行 Windows 10 IoT 核心版的设备。</span><span class="sxs-lookup"><span data-stu-id="38563-113">Launch [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/PowerShell.md) and access your device running Windows 10 IoT Core.</span></span>
* <span data-ttu-id="38563-114">从 SSH 或 Powershell，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="38563-114">From SSH or Powershell, do the following:</span></span>
  * <span data-ttu-id="38563-115">将更改为已复制文件的目录</span><span class="sxs-lookup"><span data-stu-id="38563-115">change to the directory where you have copied your files</span></span>
    * `cd C:\<dir>`
  * <span data-ttu-id="38563-116">运行以下命令，以将程序包安装到 IoT 设备系统映像：</span><span class="sxs-lookup"><span data-stu-id="38563-116">Run these commands to install the packages to your IoT device system image:</span></span>
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* <span data-ttu-id="38563-117">设备将启动到更新 OS，安装 UWF 的功能，然后重启到 MainOS。</span><span class="sxs-lookup"><span data-stu-id="38563-117">The device will boot to the Update OS, install UWF features, and reboot to the MainOS.</span></span>
* <span data-ttu-id="38563-118">设备回到 MainOS 后，UWF 功能即准备就绪并可供使用。</span><span class="sxs-lookup"><span data-stu-id="38563-118">Once the device comes back to the MainOS, the UWF feature is ready and available to use.</span></span> <span data-ttu-id="38563-119">这可通过在 Powershell 或 SSH 窗口中键入 ```uwfmgr.exe``` 来进行验证。</span><span class="sxs-lookup"><span data-stu-id="38563-119">This can be verified by typing ```uwfmgr.exe``` into your Powershell or SSH window.</span></span>

  ![Windows 10 IoT 核心版上的 uwfmgr.exe](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a><span data-ttu-id="38563-121">如何在自定义 FFU 中包含 UWF</span><span class="sxs-lookup"><span data-stu-id="38563-121">How to include UWF in Your Custom FFU</span></span> 

* <span data-ttu-id="38563-122">添加**IOT_UNIFIED_WRITE_FILTER** OEM 输入文件的功能 id</span><span class="sxs-lookup"><span data-stu-id="38563-122">Add **IOT_UNIFIED_WRITE_FILTER** feature id to the OEM Input file</span></span> 
* <span data-ttu-id="38563-123">创建 image\FFU。</span><span class="sxs-lookup"><span data-stu-id="38563-123">Create the image\FFU.</span></span> <span data-ttu-id="38563-124">读取[创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)有关的说明。</span><span class="sxs-lookup"><span data-stu-id="38563-124">Read [Create a basic image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>


## <a name="how-to-use-uwf"></a><span data-ttu-id="38563-125">如何使用 UWF</span><span class="sxs-lookup"><span data-stu-id="38563-125">How to Use UWF</span></span>

<span data-ttu-id="38563-126">可以通过 Powershell 或 SSH 会话使用 uwfmgr.exe 工具配置 UWF。</span><span class="sxs-lookup"><span data-stu-id="38563-126">UWF can be configured using the uwfmgr.exe tool via a Powershell or SSH session.</span></span>
<span data-ttu-id="38563-127">读取[`uwfmgr.exe`工具](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe)IoT 核心版中不支持一些命令下面列出的异常的可用选项。</span><span class="sxs-lookup"><span data-stu-id="38563-127">Read [`uwfmgr.exe` tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) for the available options with an exception of some commands listed below that are not supported in IoT Core.</span></span>
<span data-ttu-id="38563-128">查看覆盖配置的默认设置，并根据你的要求对其进行调整。</span><span class="sxs-lookup"><span data-stu-id="38563-128">Review the default settings of the Overlay configurations and adapt them per your requirements.</span></span>

<span data-ttu-id="38563-129">此外可通过 MDM 通道使用配置 UWF[统一写入筛选器 CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)。</span><span class="sxs-lookup"><span data-stu-id="38563-129">UWF can also be configured via MDM channel using [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span></span>


* <span data-ttu-id="38563-130">例如，以下命令组合可启用 uwfmgr 并配置为保护 C 驱动器</span><span class="sxs-lookup"><span data-stu-id="38563-130">For example, the following combination of commands enable uwfmgr and configure to protect the C drive</span></span>

  `uwfmgr.exe filter enable`      <span data-ttu-id="38563-131">启用写入筛选器</span><span class="sxs-lookup"><span data-stu-id="38563-131">Enables the write filter</span></span>
  <br>
  `uwfmgr.exe volume protect c:`  <span data-ttu-id="38563-132">保护的卷 C</span><span class="sxs-lookup"><span data-stu-id="38563-132">Protects the Volume C</span></span>
  <br>
  `shutdown /r /t 0`              <span data-ttu-id="38563-133">重新启动设备以使写入筛选器设置生效</span><span class="sxs-lookup"><span data-stu-id="38563-133">Restarts the device to make the write filter settings effective</span></span>

<span data-ttu-id="38563-134">*重新启动*需使所有 uwfmgr 设置生效。</span><span class="sxs-lookup"><span data-stu-id="38563-134">*Reboot* is required to make all the uwfmgr settings effective.</span></span> 


## <a name="protecting-a-data-volume"></a><span data-ttu-id="38563-135">保护数据卷</span><span class="sxs-lookup"><span data-stu-id="38563-135">Protecting a Data Volume</span></span>

<span data-ttu-id="38563-136">可以使用卷的 GUID 来保护 IoT 核心版中的数据卷。</span><span class="sxs-lookup"><span data-stu-id="38563-136">Data volume in IoT Core can be protected using the GUID for the volume.</span></span> <span data-ttu-id="38563-137">可以通过以下命令查找可用卷的 GUID</span><span class="sxs-lookup"><span data-stu-id="38563-137">The GUID for the available volumes can be found through the following command</span></span>

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![在 Windows 10 IoT 核心版上保护卷](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a><span data-ttu-id="38563-139">建议的排除项</span><span class="sxs-lookup"><span data-stu-id="38563-139">Recommended Exclusions</span></span>
<span data-ttu-id="38563-140">保护的数据量，我们建议您添加的服务和日志记录文件夹均由 Windows 操作系统服务访问的例外。</span><span class="sxs-lookup"><span data-stu-id="38563-140">When protecting the data volume, we recommend that you add exceptions for the servicing and logging folders that are accessed by Windows OS Services.</span></span>

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

<span data-ttu-id="38563-141">若要添加生成的排除项：</span><span class="sxs-lookup"><span data-stu-id="38563-141">To add the exclusions:</span></span> `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a><span data-ttu-id="38563-142">维护 UWF 受保护的设备</span><span class="sxs-lookup"><span data-stu-id="38563-142">Servicing UWF protected devices</span></span>

> [!Note]
> <span data-ttu-id="38563-143">从 Windows 10 IoT Core 版本 1709年版本 16299，主要的 OS 卷 (c:\)可以使用 UWF 保护和维护*自动*而无需任何特殊步骤。</span><span class="sxs-lookup"><span data-stu-id="38563-143">Starting Windows 10 IoT Core Release 1709, version 16299, the main OS volume (C:\) can be protected with UWF and serviced *automatically* without any special steps.</span></span>

<span data-ttu-id="38563-144">以下步骤所需服务 UWF 受保护的设备的受保护的数据卷。</span><span class="sxs-lookup"><span data-stu-id="38563-144">The following steps are required to service UWF protected devices with protected data volumes.</span></span>

* `uwfmgr.exe filter disable` <span data-ttu-id="38563-145">禁用 UWF</span><span class="sxs-lookup"><span data-stu-id="38563-145">Disable UWF</span></span>
* `shutdown /r /t 0` <span data-ttu-id="38563-146">重新启动设备，若要禁用 UWF</span><span class="sxs-lookup"><span data-stu-id="38563-146">Reboot device to disable UWF</span></span>
* <span data-ttu-id="38563-147">启用服务 （使用预配包或 MDM 设置更新策略）</span><span class="sxs-lookup"><span data-stu-id="38563-147">Enable Servicing ( using provisioning package or MDM to set Update policy )</span></span>
   * <span data-ttu-id="38563-148">请注意，每个设备将自动重新启动以执行维护服务更新</span><span class="sxs-lookup"><span data-stu-id="38563-148">Note that the device will automatically reboot to perform the servicing updates</span></span>
* `uwfmgr.exe filter enable` <span data-ttu-id="38563-149">启用 UWF</span><span class="sxs-lookup"><span data-stu-id="38563-149">Enable UWF</span></span>
* `shutdown /r /t 0` <span data-ttu-id="38563-150">重新启动设备，以启用 UWF</span><span class="sxs-lookup"><span data-stu-id="38563-150">Reboot device to enable UWF</span></span>

## <a name="unsupported-uwfmgrexe-commands"></a><span data-ttu-id="38563-151">不受支持的 uwfmgr.exe 命令</span><span class="sxs-lookup"><span data-stu-id="38563-151">Unsupported uwfmgr.exe Commands</span></span>

<span data-ttu-id="38563-152">**UWF 维护模式**IoT 核心版中不支持。</span><span class="sxs-lookup"><span data-stu-id="38563-152">**UWF Servicing Mode** is not supported in IoT Core.</span></span>

`uwfmgr.exe` <span data-ttu-id="38563-153">Windows 10 IoT Core 上不支持下面列出的命令。</span><span class="sxs-lookup"><span data-stu-id="38563-153">on Windows 10 IoT Core does not support commands listed below.</span></span>

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
