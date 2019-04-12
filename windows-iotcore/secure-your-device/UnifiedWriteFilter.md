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
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a>在 Windows 10 IoT Core 上使用统一的写入筛选器 (UWF)

> [!WARNING]
> UWF 不支持动态磁盘。

统一写入筛选器 (UWF) 是一项功能，防止数据写入物理存储介质。 UWF 将拦截所有针对受保护卷的写入尝试，并将这些写入尝试重定向到虚拟覆盖。 这可改进设备的可靠性和稳定性，同时减少写入敏感媒体（例如，诸如固态硬盘等闪存媒体）的损耗。

阅读我们的文档[统一写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)有关详细信息。

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a>如何在运行 Windows 10 IoT 核心版的设备上安装 UWF

* 如果你还没有 Windows 10 IoT Core 工具包的当前版本，下载并安装[Windows 10 IoT Core 包](https://www.microsoft.com/en-us/software-download/windows10iotcore)。
* 基于设备体系结构上，复制 UWF 包 (`Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`和`Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`) 从您的 PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) 到设备 (例如，对于[Windows 文件共享](../manage-your-device/WindowsFileSharing.md))。
* 启动[SSH](../connect-your-device/SSH.md)或[Powershell](../connect-your-device/PowerShell.md)和访问运行 Windows 10 IoT 核心版的设备。
* 从 SSH 或 Powershell，请执行以下操作：
  * 将更改为已复制文件的目录
    * `cd C:\<dir>`
  * 运行以下命令，以将程序包安装到 IoT 设备系统映像：
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* 设备将启动到更新 OS，安装 UWF 的功能，然后重启到 MainOS。
* 设备回到 MainOS 后，UWF 功能即准备就绪并可供使用。 这可通过在 Powershell 或 SSH 窗口中键入 ```uwfmgr.exe``` 来进行验证。

  ![Windows 10 IoT 核心版上的 uwfmgr.exe](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a>如何在自定义 FFU 中包含 UWF 

* 添加**IOT_UNIFIED_WRITE_FILTER** OEM 输入文件的功能 id 
* 创建 image\FFU。 读取[创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)有关的说明。


## <a name="how-to-use-uwf"></a>如何使用 UWF

可以通过 Powershell 或 SSH 会话使用 uwfmgr.exe 工具配置 UWF。
读取[`uwfmgr.exe`工具](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe)IoT 核心版中不支持一些命令下面列出的异常的可用选项。
查看覆盖配置的默认设置，并根据你的要求对其进行调整。

此外可通过 MDM 通道使用配置 UWF[统一写入筛选器 CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)。


* 例如，以下命令组合可启用 uwfmgr 并配置为保护 C 驱动器

  `uwfmgr.exe filter enable`      启用写入筛选器
  <br>
  `uwfmgr.exe volume protect c:`  保护的卷 C
  <br>
  `shutdown /r /t 0`              重新启动设备以使写入筛选器设置生效

*重新启动*需使所有 uwfmgr 设置生效。 


## <a name="protecting-a-data-volume"></a>保护数据卷

可以使用卷的 GUID 来保护 IoT 核心版中的数据卷。 可以通过以下命令查找可用卷的 GUID

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![在 Windows 10 IoT 核心版上保护卷](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a>建议的排除项
保护的数据量，我们建议您添加的服务和日志记录文件夹均由 Windows 操作系统服务访问的例外。

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

若要添加生成的排除项： `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a>维护 UWF 受保护的设备

> [!Note]
> 从 Windows 10 IoT Core 版本 1709年版本 16299，主要的 OS 卷 (c:\)可以使用 UWF 保护和维护*自动*而无需任何特殊步骤。

以下步骤所需服务 UWF 受保护的设备的受保护的数据卷。

* `uwfmgr.exe filter disable` 禁用 UWF
* `shutdown /r /t 0` 重新启动设备，若要禁用 UWF
* 启用服务 （使用预配包或 MDM 设置更新策略）
   * 请注意，每个设备将自动重新启动以执行维护服务更新
* `uwfmgr.exe filter enable` 启用 UWF
* `shutdown /r /t 0` 重新启动设备，以启用 UWF

## <a name="unsupported-uwfmgrexe-commands"></a>不受支持的 uwfmgr.exe 命令

**UWF 维护模式**IoT 核心版中不支持。

`uwfmgr.exe` Windows 10 IoT Core 上不支持下面列出的命令。

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
