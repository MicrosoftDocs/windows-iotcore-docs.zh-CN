---
title: 使用统一写入筛选器
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用统一写入筛选器保护物理存储媒体的数据写入。
keywords: windows iot, 统一写入筛选器, 安全, 内存, 存储媒体
ms.openlocfilehash: d1d6927fe19b5888ef0393d0b101065096cd9f63
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167538"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a><span data-ttu-id="83c8c-104">使用 Windows 10 IoT Core 上的统一写入筛选器 (UWF)</span><span class="sxs-lookup"><span data-stu-id="83c8c-104">Using the Unified Write Filter (UWF) on Windows 10 IoT Core</span></span>

> [!WARNING]
> <span data-ttu-id="83c8c-105">UWF 不支持动态磁盘。</span><span class="sxs-lookup"><span data-stu-id="83c8c-105">The dynamic disk is not supported for the UWF.</span></span>

<span data-ttu-id="83c8c-106">统一写入筛选器 (UWF) 是一项功能, 可保护物理存储媒体的数据写入。</span><span class="sxs-lookup"><span data-stu-id="83c8c-106">The Unified Write Filter (UWF) is a feature that protects physical storage media from data writes.</span></span> <span data-ttu-id="83c8c-107">UWF 将拦截所有针对受保护卷的写入尝试，并将这些写入尝试重定向到虚拟覆盖。</span><span class="sxs-lookup"><span data-stu-id="83c8c-107">UWF intercepts all write attempts to a protected volume and redirects those write attempts to a virtual overlay.</span></span> <span data-ttu-id="83c8c-108">这可改进设备的可靠性和稳定性，同时减少写入敏感媒体（例如，诸如固态硬盘等闪存媒体）的损耗。</span><span class="sxs-lookup"><span data-stu-id="83c8c-108">This improves the reliability and stability of your device and reduces the wear on write-sensitive media, such as flash memory media like solid-state drives.</span></span>

<span data-ttu-id="83c8c-109">有关详细信息, 请参阅有关[统一写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)的文档。</span><span class="sxs-lookup"><span data-stu-id="83c8c-109">Read our documentation on the [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) for more information.</span></span>

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="83c8c-110">如何在运行 Windows 10 IoT Core 的设备上安装 UWF</span><span class="sxs-lookup"><span data-stu-id="83c8c-110">How to Install UWF on a device running Windows 10 IoT Core</span></span>

* <span data-ttu-id="83c8c-111">如果尚未安装最新版本的 Windows 10 IoT Core 工具包, 请下载并安装[windows 10 Iot Core 包](https://www.microsoft.com/en-us/software-download/windows10iotcore)。</span><span class="sxs-lookup"><span data-stu-id="83c8c-111">If you do not have the current version of the Windows 10 IoT Core Kits yet, download and install the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span></span>
* <span data-ttu-id="83c8c-112">根据设备体系结构, 将 azure 包`Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` (和`Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) 从电脑 (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) 复制到设备 (例如, 通过[Windows 文件共享](../manage-your-device/WindowsFileSharing.md))。</span><span class="sxs-lookup"><span data-stu-id="83c8c-112">Based on your device architecture, copy UWF packages ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` and `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) to the device (for example, with [Windows file sharing](../manage-your-device/WindowsFileSharing.md)).</span></span>
* <span data-ttu-id="83c8c-113">启动[SSH](../connect-your-device/SSH.md)或[Powershell](../connect-your-device/PowerShell.md) , 并访问运行 Windows 10 IoT Core 的设备。</span><span class="sxs-lookup"><span data-stu-id="83c8c-113">Launch [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/PowerShell.md) and access your device running Windows 10 IoT Core.</span></span>
* <span data-ttu-id="83c8c-114">在 SSH 或 Powershell 中, 执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="83c8c-114">From SSH or Powershell, do the following:</span></span>
  * <span data-ttu-id="83c8c-115">更改到已将文件复制到的目录</span><span class="sxs-lookup"><span data-stu-id="83c8c-115">change to the directory where you have copied your files</span></span>
    * `cd C:\<dir>`
  * <span data-ttu-id="83c8c-116">运行以下命令，以将程序包安装到 IoT 设备系统映像：</span><span class="sxs-lookup"><span data-stu-id="83c8c-116">Run these commands to install the packages to your IoT device system image:</span></span>
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* <span data-ttu-id="83c8c-117">设备将启动到更新操作系统, 安装 UWF 功能, 并重新启动到 MainOS。</span><span class="sxs-lookup"><span data-stu-id="83c8c-117">The device will boot to the Update OS, install UWF features, and reboot to the MainOS.</span></span>
* <span data-ttu-id="83c8c-118">设备回到 MainOS 后，UWF 功能即准备就绪并可供使用。</span><span class="sxs-lookup"><span data-stu-id="83c8c-118">Once the device comes back to the MainOS, the UWF feature is ready and available to use.</span></span> <span data-ttu-id="83c8c-119">这可通过在 Powershell 或 SSH 窗口中键入 ```uwfmgr.exe``` 来进行验证。</span><span class="sxs-lookup"><span data-stu-id="83c8c-119">This can be verified by typing ```uwfmgr.exe``` into your Powershell or SSH window.</span></span>

  ![Windows 10 IoT 核心版上的 uwfmgr.exe](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a><span data-ttu-id="83c8c-121">如何在自定义 FFU 中包含 UWF</span><span class="sxs-lookup"><span data-stu-id="83c8c-121">How to include UWF in Your Custom FFU</span></span> 

* <span data-ttu-id="83c8c-122">将**IOT_UNIFIED_WRITE_FILTER**功能 id 添加到 OEM 输入文件</span><span class="sxs-lookup"><span data-stu-id="83c8c-122">Add **IOT_UNIFIED_WRITE_FILTER** feature id to the OEM Input file</span></span> 
* <span data-ttu-id="83c8c-123">创建 image\FFU。</span><span class="sxs-lookup"><span data-stu-id="83c8c-123">Create the image\FFU.</span></span> <span data-ttu-id="83c8c-124">有关说明, 请参阅[创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)。</span><span class="sxs-lookup"><span data-stu-id="83c8c-124">Read [Create a basic image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>


## <a name="how-to-use-uwf"></a><span data-ttu-id="83c8c-125">如何使用 UWF</span><span class="sxs-lookup"><span data-stu-id="83c8c-125">How to Use UWF</span></span>

<span data-ttu-id="83c8c-126">可以通过 Powershell 或 SSH 会话使用 uwfmgr.exe 工具配置 UWF。</span><span class="sxs-lookup"><span data-stu-id="83c8c-126">UWF can be configured using the uwfmgr.exe tool via a Powershell or SSH session.</span></span>
<span data-ttu-id="83c8c-127">针对可用选项的读取[ `uwfmgr.exe`工具](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe), 其中的某些命令例外, IoT Core 不支持这些命令。</span><span class="sxs-lookup"><span data-stu-id="83c8c-127">Read [`uwfmgr.exe` tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) for the available options with an exception of some commands listed below that are not supported in IoT Core.</span></span>
<span data-ttu-id="83c8c-128">查看覆盖配置的默认设置，并根据你的要求对其进行调整。</span><span class="sxs-lookup"><span data-stu-id="83c8c-128">Review the default settings of the Overlay configurations and adapt them per your requirements.</span></span>

<span data-ttu-id="83c8c-129">还可以使用[统一写入筛选器 CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)通过 MDM 通道配置 UWF。</span><span class="sxs-lookup"><span data-stu-id="83c8c-129">UWF can also be configured via MDM channel using [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span></span>


* <span data-ttu-id="83c8c-130">例如，以下命令组合可启用 uwfmgr 并配置为保护 C 驱动器</span><span class="sxs-lookup"><span data-stu-id="83c8c-130">For example, the following combination of commands enable uwfmgr and configure to protect the C drive</span></span>

  <span data-ttu-id="83c8c-131">`uwfmgr.exe filter enable`启用写入筛选器</span><span class="sxs-lookup"><span data-stu-id="83c8c-131">`uwfmgr.exe filter enable`      Enables the write filter</span></span>
  <br>
  <span data-ttu-id="83c8c-132">`uwfmgr.exe volume protect c:`保护卷 C</span><span class="sxs-lookup"><span data-stu-id="83c8c-132">`uwfmgr.exe volume protect c:`  Protects the Volume C</span></span>
  <br>
  <span data-ttu-id="83c8c-133">`shutdown /r /t 0`重新启动设备以使写入筛选器设置生效</span><span class="sxs-lookup"><span data-stu-id="83c8c-133">`shutdown /r /t 0`              Restarts the device to make the write filter settings effective</span></span>

<span data-ttu-id="83c8c-134">需要*重新启动*才能使所有 uwfmgr 设置生效。</span><span class="sxs-lookup"><span data-stu-id="83c8c-134">*Reboot* is required to make all the uwfmgr settings effective.</span></span> 


## <a name="protecting-a-data-volume"></a><span data-ttu-id="83c8c-135">保护数据卷</span><span class="sxs-lookup"><span data-stu-id="83c8c-135">Protecting a Data Volume</span></span>

<span data-ttu-id="83c8c-136">可以使用卷的 GUID 来保护 IoT 核心版中的数据卷。</span><span class="sxs-lookup"><span data-stu-id="83c8c-136">Data volume in IoT Core can be protected using the GUID for the volume.</span></span> <span data-ttu-id="83c8c-137">可以通过以下命令查找可用卷的 GUID</span><span class="sxs-lookup"><span data-stu-id="83c8c-137">The GUID for the available volumes can be found through the following command</span></span>

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![在 Windows 10 IoT 核心版上保护卷](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a><span data-ttu-id="83c8c-139">建议排除项</span><span class="sxs-lookup"><span data-stu-id="83c8c-139">Recommended Exclusions</span></span>
<span data-ttu-id="83c8c-140">保护数据卷时, 建议你为 Windows OS 服务访问的服务和日志记录文件夹添加例外。</span><span class="sxs-lookup"><span data-stu-id="83c8c-140">When protecting the data volume, we recommend that you add exceptions for the servicing and logging folders that are accessed by Windows OS Services.</span></span>

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

<span data-ttu-id="83c8c-141">添加排除项:`uwfmgr.exe file Add-Exclusion <file/folder name>`</span><span class="sxs-lookup"><span data-stu-id="83c8c-141">To add the exclusions: `uwfmgr.exe file Add-Exclusion <file/folder name>`</span></span>



## <a name="servicing-uwf-protected-devices"></a><span data-ttu-id="83c8c-142">为 UWF 受保护设备提供服务</span><span class="sxs-lookup"><span data-stu-id="83c8c-142">Servicing UWF protected devices</span></span>

> [!Note]
> <span data-ttu-id="83c8c-143">启动 Windows 10 IoT Core 版本 1709, 版本 16299, 主 OS 卷 (C:\)可通过 UWF 进行保护, 并*自动*提供服务, 无需任何特殊步骤。</span><span class="sxs-lookup"><span data-stu-id="83c8c-143">Starting Windows 10 IoT Core Release 1709, version 16299, the main OS volume (C:\) can be protected with UWF and serviced *automatically* without any special steps.</span></span>

<span data-ttu-id="83c8c-144">对于包含受保护的数据卷的 UWF 保护设备, 需要执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="83c8c-144">The following steps are required to service UWF protected devices with protected data volumes.</span></span>

* <span data-ttu-id="83c8c-145">`uwfmgr.exe filter disable`禁用 UWF</span><span class="sxs-lookup"><span data-stu-id="83c8c-145">`uwfmgr.exe filter disable` Disable UWF</span></span>
* <span data-ttu-id="83c8c-146">`shutdown /r /t 0`重新启动设备以禁用 UWF</span><span class="sxs-lookup"><span data-stu-id="83c8c-146">`shutdown /r /t 0` Reboot device to disable UWF</span></span>
* <span data-ttu-id="83c8c-147">启用维护 (使用预配包或 MDM 设置更新策略)</span><span class="sxs-lookup"><span data-stu-id="83c8c-147">Enable Servicing ( using provisioning package or MDM to set Update policy )</span></span>
   * <span data-ttu-id="83c8c-148">请注意, 设备将自动重新启动以执行服务更新</span><span class="sxs-lookup"><span data-stu-id="83c8c-148">Note that the device will automatically reboot to perform the servicing updates</span></span>
* <span data-ttu-id="83c8c-149">`uwfmgr.exe filter enable`启用 UWF</span><span class="sxs-lookup"><span data-stu-id="83c8c-149">`uwfmgr.exe filter enable` Enable UWF</span></span>
* <span data-ttu-id="83c8c-150">`shutdown /r /t 0`重新启动设备以启用 UWF</span><span class="sxs-lookup"><span data-stu-id="83c8c-150">`shutdown /r /t 0` Reboot device to enable UWF</span></span>

## <a name="unsupported-uwfmgrexe-commands"></a><span data-ttu-id="83c8c-151">不受支持的 uwfmgr.exe 命令</span><span class="sxs-lookup"><span data-stu-id="83c8c-151">Unsupported uwfmgr.exe Commands</span></span>

<span data-ttu-id="83c8c-152">IoT 核心不支持**UWF 服务模式**。</span><span class="sxs-lookup"><span data-stu-id="83c8c-152">**UWF Servicing Mode** is not supported in IoT Core.</span></span>

<span data-ttu-id="83c8c-153">`uwfmgr.exe`在 Windows 10 IoT Core 上不支持下面列出的命令。</span><span class="sxs-lookup"><span data-stu-id="83c8c-153">`uwfmgr.exe` on Windows 10 IoT Core does not support commands listed below.</span></span>

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
