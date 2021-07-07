---
title: 使用统一写入筛选器
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用统一写入筛选器来保护物理存储媒体免受数据写入。
keywords: windows iot， 统一写入筛选器， 安全性， 内存， 存储媒体
ms.openlocfilehash: 20c62b979e46188b3c2af98f709f841c9f90beb0
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230694"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a><span data-ttu-id="0e917-104">在 UWF (使用统一) 筛选器Windows 10 IoT 核心版</span><span class="sxs-lookup"><span data-stu-id="0e917-104">Using the Unified Write Filter (UWF) on Windows 10 IoT Core</span></span>

<span data-ttu-id="0e917-105">UWF (统一) 是一项保护物理存储媒体免受数据写入影响的功能。</span><span class="sxs-lookup"><span data-stu-id="0e917-105">The Unified Write Filter (UWF) is a feature that protects physical storage media from data writes.</span></span> <span data-ttu-id="0e917-106">UWF 将拦截所有针对受保护卷的写入尝试，并将这些写入尝试重定向到虚拟覆盖。</span><span class="sxs-lookup"><span data-stu-id="0e917-106">UWF intercepts all write attempts to a protected volume and redirects those write attempts to a virtual overlay.</span></span> <span data-ttu-id="0e917-107">这可改进设备的可靠性和稳定性，同时减少写入敏感介质（例如，诸如固态硬盘等闪存介质）的损耗。</span><span class="sxs-lookup"><span data-stu-id="0e917-107">This improves the reliability and stability of your device and reduces the wear on write-sensitive media, such as flash memory media like solid-state drives.</span></span>

<span data-ttu-id="0e917-108">有关详细信息，请阅读 [有关统一写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) 的文档。</span><span class="sxs-lookup"><span data-stu-id="0e917-108">Read our documentation on the [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) for more information.</span></span>

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="0e917-109">如何在运行 UWF 的设备上安装 UWF Windows 10 IoT 核心版</span><span class="sxs-lookup"><span data-stu-id="0e917-109">How to Install UWF on a device running Windows 10 IoT Core</span></span>

* <span data-ttu-id="0e917-110">如果还没有最新版本的 Windows 10 IoT 核心版 工具包，请下载并安装 Windows 10 IoT 核心版[包](https://www.microsoft.com/en-us/software-download/windows10iotcore)。</span><span class="sxs-lookup"><span data-stu-id="0e917-110">If you do not have the current version of the Windows 10 IoT Core Kits yet, download and install the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span></span>
* <span data-ttu-id="0e917-111">根据设备体系结构，将 UWF 包 ( 和 ) 从电脑 () 复制到设备 (例如，使用 `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` Windows `C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\` [文件共享](../manage-your-device/WindowsFileSharing.md)) 。</span><span class="sxs-lookup"><span data-stu-id="0e917-111">Based on your device architecture, copy UWF packages ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` and `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) to the device (for example, with [Windows file sharing](../manage-your-device/WindowsFileSharing.md)).</span></span>
* <span data-ttu-id="0e917-112">启动[SSH](../connect-your-device/SSH.md)或[PowerShell](../connect-your-device/PowerShell.md)并访问运行 Windows 10 IoT 核心版。</span><span class="sxs-lookup"><span data-stu-id="0e917-112">Launch [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/PowerShell.md) and access your device running Windows 10 IoT Core.</span></span>
* <span data-ttu-id="0e917-113">在 SSH 或 PowerShell 中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="0e917-113">From SSH or PowerShell, do the following:</span></span>
  * <span data-ttu-id="0e917-114">更改为已复制文件的目录</span><span class="sxs-lookup"><span data-stu-id="0e917-114">change to the directory where you have copied your files</span></span>
    * `cd C:\<dir>`
  * <span data-ttu-id="0e917-115">运行以下命令，将包安装到 IoT 设备系统映像：</span><span class="sxs-lookup"><span data-stu-id="0e917-115">Run these commands to install the packages to your IoT device system image:</span></span>
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* <span data-ttu-id="0e917-116">设备将启动到更新 OS、安装 UWF 功能，并重新启动到 MainOS。</span><span class="sxs-lookup"><span data-stu-id="0e917-116">The device will boot to the Update OS, install UWF features, and reboot to the MainOS.</span></span>
* <span data-ttu-id="0e917-117">设备返回到 MainOS 后，UWF 功能即已准备就绪且可供使用。</span><span class="sxs-lookup"><span data-stu-id="0e917-117">Once the device comes back to the MainOS, the UWF feature is ready and available to use.</span></span> <span data-ttu-id="0e917-118">可以通过在 PowerShell 或 ```uwfmgr.exe``` SSH 窗口中键入 来验证这一点。</span><span class="sxs-lookup"><span data-stu-id="0e917-118">This can be verified by typing ```uwfmgr.exe``` into your PowerShell or SSH window.</span></span>

  ![uwfmgr.exe上Windows 10 IoT 核心版](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a><span data-ttu-id="0e917-120">如何在自定义 FFU 中包括 UWF</span><span class="sxs-lookup"><span data-stu-id="0e917-120">How to include UWF in Your Custom FFU</span></span>

* <span data-ttu-id="0e917-121">将 **IOT_UNIFIED_WRITE_FILTER** ID 添加到 OEM 输入文件</span><span class="sxs-lookup"><span data-stu-id="0e917-121">Add **IOT_UNIFIED_WRITE_FILTER** feature ID to the OEM Input file</span></span>
* <span data-ttu-id="0e917-122">创建 image\FFU。</span><span class="sxs-lookup"><span data-stu-id="0e917-122">Create the image\FFU.</span></span> <span data-ttu-id="0e917-123">有关 [说明，请阅读创建](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 基本映像。</span><span class="sxs-lookup"><span data-stu-id="0e917-123">Read [Create a basic image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>


## <a name="how-to-use-uwf"></a><span data-ttu-id="0e917-124">如何使用 UWF</span><span class="sxs-lookup"><span data-stu-id="0e917-124">How to Use UWF</span></span>

<span data-ttu-id="0e917-125">可以通过 PowerShell 或 SSH 会话使用 uwfmgr.exe工具配置 UWF。</span><span class="sxs-lookup"><span data-stu-id="0e917-125">UWF can be configured using the uwfmgr.exe tool via a PowerShell or SSH session.</span></span>
<span data-ttu-id="0e917-126">读取[ `uwfmgr.exe` 工具](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe)，了解可用选项，但下面列出的某些命令在 IoT Core 中不受支持。</span><span class="sxs-lookup"><span data-stu-id="0e917-126">Read [`uwfmgr.exe` tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) for the available options with an exception of some commands listed below that are not supported in IoT Core.</span></span>
<span data-ttu-id="0e917-127">查看覆盖配置的默认设置，并按要求调整这些设置。</span><span class="sxs-lookup"><span data-stu-id="0e917-127">Review the default settings of the Overlay configurations and adapt them per your requirements.</span></span>

<span data-ttu-id="0e917-128">也可使用统一写入筛选器 CSP 通过 MDM 通道 [配置](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)UWF。</span><span class="sxs-lookup"><span data-stu-id="0e917-128">UWF can also be configured via MDM channel using [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span></span>


* <span data-ttu-id="0e917-129">例如，以下命令组合启用 uwfmgr 并配置为保护 C 驱动器</span><span class="sxs-lookup"><span data-stu-id="0e917-129">For example, the following combinations of commands enable uwfmgr and configure to protect the C drive</span></span>

  <span data-ttu-id="0e917-130">`uwfmgr.exe filter enable`      启用写入筛选器</span><span class="sxs-lookup"><span data-stu-id="0e917-130">`uwfmgr.exe filter enable`      Enables the write filter</span></span>
  <br>
  <span data-ttu-id="0e917-131">`uwfmgr.exe volume protect c:`  保护卷 C</span><span class="sxs-lookup"><span data-stu-id="0e917-131">`uwfmgr.exe volume protect c:`  Protects the Volume C</span></span>
  <br>
  <span data-ttu-id="0e917-132">`shutdown /r /t 0`              重启设备，使写入筛选器设置生效</span><span class="sxs-lookup"><span data-stu-id="0e917-132">`shutdown /r /t 0`              Restarts the device to make the write filter settings effective</span></span>

<span data-ttu-id="0e917-133">*需要* 重新启动才能使所有 uwfmgr 设置生效。</span><span class="sxs-lookup"><span data-stu-id="0e917-133">*Reboot* is required to make all the uwfmgr settings effective.</span></span>


## <a name="protecting-a-data-volume"></a><span data-ttu-id="0e917-134">保护数据卷</span><span class="sxs-lookup"><span data-stu-id="0e917-134">Protecting a Data Volume</span></span>

<span data-ttu-id="0e917-135">可以使用卷的 GUID 保护 IoT Core 中的数据卷。</span><span class="sxs-lookup"><span data-stu-id="0e917-135">Data volume in IoT Core can be protected using the GUID for the volume.</span></span>
<span data-ttu-id="0e917-136">可通过以下命令找到可用卷的 GUID</span><span class="sxs-lookup"><span data-stu-id="0e917-136">The GUID for the available volumes can be found through the following command</span></span>

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![保护卷Windows 10 IoT 核心版](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a><span data-ttu-id="0e917-138">建议的排除项</span><span class="sxs-lookup"><span data-stu-id="0e917-138">Recommended Exclusions</span></span>
<span data-ttu-id="0e917-139">保护数据卷时，建议为 OS 服务访问的服务文件夹和日志记录Windows例外。</span><span class="sxs-lookup"><span data-stu-id="0e917-139">When protecting the data volume, we recommend that you add exceptions for the servicing and logging folders that are accessed by Windows OS Services.</span></span>

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

<span data-ttu-id="0e917-140">添加排除项： `uwfmgr.exe file Add-Exclusion <file/folder name>`</span><span class="sxs-lookup"><span data-stu-id="0e917-140">To add the exclusions: `uwfmgr.exe file Add-Exclusion <file/folder name>`</span></span>



## <a name="servicing-uwf-protected-devices"></a><span data-ttu-id="0e917-141">维护受 UWF 保护的设备</span><span class="sxs-lookup"><span data-stu-id="0e917-141">Servicing UWF protected devices</span></span>

> [!Note]
> <span data-ttu-id="0e917-142">从 Windows 10 IoT 核心版 版本 1709 版本 16299 开始，主 OS 卷 (C： 可以使用 UWF 进行保护并自动提供服务，无需任何 \) 特殊步骤。</span><span class="sxs-lookup"><span data-stu-id="0e917-142">Starting Windows 10 IoT Core Release 1709, version 16299, the main OS volume (C:\) can be protected with UWF and serviced *automatically* without any special steps.</span></span>

<span data-ttu-id="0e917-143">若要使用受保护的数据卷为受 UWF 保护的设备提供服务，需要执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="0e917-143">The following steps are required to service UWF protected devices with protected data volumes.</span></span>

* <span data-ttu-id="0e917-144">`uwfmgr.exe filter disable` 禁用 UWF</span><span class="sxs-lookup"><span data-stu-id="0e917-144">`uwfmgr.exe filter disable` Disable UWF</span></span>
* <span data-ttu-id="0e917-145">`shutdown /r /t 0` 重新启动设备以禁用 UWF</span><span class="sxs-lookup"><span data-stu-id="0e917-145">`shutdown /r /t 0` Reboot device to disable UWF</span></span>
* <span data-ttu-id="0e917-146">使用预配 (MDM 启用维护服务包以设置更新策略) </span><span class="sxs-lookup"><span data-stu-id="0e917-146">Enable Servicing (using provisioning package or MDM to set Update policy)</span></span>
   * <span data-ttu-id="0e917-147">请注意，设备将自动重新启动以执行服务更新</span><span class="sxs-lookup"><span data-stu-id="0e917-147">Note that the device will automatically reboot to perform the servicing updates</span></span>
* <span data-ttu-id="0e917-148">`uwfmgr.exe filter enable` 启用 UWF</span><span class="sxs-lookup"><span data-stu-id="0e917-148">`uwfmgr.exe filter enable` Enable UWF</span></span>
* <span data-ttu-id="0e917-149">`shutdown /r /t 0` 重新启动设备以启用 UWF</span><span class="sxs-lookup"><span data-stu-id="0e917-149">`shutdown /r /t 0` Reboot device to enable UWF</span></span>

## <a name="unsupported-uwfmgrexe-commands"></a><span data-ttu-id="0e917-150">不支持uwfmgr.exe命令</span><span class="sxs-lookup"><span data-stu-id="0e917-150">Unsupported uwfmgr.exe Commands</span></span>

<span data-ttu-id="0e917-151">**IoT 核心不支持 UWF** 维护模式。</span><span class="sxs-lookup"><span data-stu-id="0e917-151">**UWF Servicing Mode** is not supported in IoT Core.</span></span>

<span data-ttu-id="0e917-152">`uwfmgr.exe`on Windows 10 IoT 核心版 不支持下面列出的命令。</span><span class="sxs-lookup"><span data-stu-id="0e917-152">`uwfmgr.exe` on Windows 10 IoT Core does not support commands listed below.</span></span>

```
Filter
    Shutdown
    Restart
Servicing
    Enable
    Disable
    Update-Windows
```
