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
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a>在 UWF (使用统一) 筛选器Windows 10 IoT 核心版

UWF (统一) 是一项保护物理存储媒体免受数据写入影响的功能。 UWF 将拦截所有针对受保护卷的写入尝试，并将这些写入尝试重定向到虚拟覆盖。 这可改进设备的可靠性和稳定性，同时减少写入敏感介质（例如，诸如固态硬盘等闪存介质）的损耗。

有关详细信息，请阅读 [有关统一写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) 的文档。

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a>如何在运行 UWF 的设备上安装 UWF Windows 10 IoT 核心版

* 如果还没有最新版本的 Windows 10 IoT 核心版 工具包，请下载并安装 Windows 10 IoT 核心版[包](https://www.microsoft.com/en-us/software-download/windows10iotcore)。
* 根据设备体系结构，将 UWF 包 ( 和 ) 从电脑 () 复制到设备 (例如，使用 `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` Windows `C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\` [文件共享](../manage-your-device/WindowsFileSharing.md)) 。
* 启动[SSH](../connect-your-device/SSH.md)或[PowerShell](../connect-your-device/PowerShell.md)并访问运行 Windows 10 IoT 核心版。
* 在 SSH 或 PowerShell 中执行以下操作：
  * 更改为已复制文件的目录
    * `cd C:\<dir>`
  * 运行以下命令，将包安装到 IoT 设备系统映像：
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* 设备将启动到更新 OS、安装 UWF 功能，并重新启动到 MainOS。
* 设备返回到 MainOS 后，UWF 功能即已准备就绪且可供使用。 可以通过在 PowerShell 或 ```uwfmgr.exe``` SSH 窗口中键入 来验证这一点。

  ![uwfmgr.exe上Windows 10 IoT 核心版](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a>如何在自定义 FFU 中包括 UWF

* 将 **IOT_UNIFIED_WRITE_FILTER** ID 添加到 OEM 输入文件
* 创建 image\FFU。 有关 [说明，请阅读创建](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 基本映像。


## <a name="how-to-use-uwf"></a>如何使用 UWF

可以通过 PowerShell 或 SSH 会话使用 uwfmgr.exe工具配置 UWF。
读取[ `uwfmgr.exe` 工具](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe)，了解可用选项，但下面列出的某些命令在 IoT Core 中不受支持。
查看覆盖配置的默认设置，并按要求调整这些设置。

也可使用统一写入筛选器 CSP 通过 MDM 通道 [配置](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)UWF。


* 例如，以下命令组合启用 uwfmgr 并配置为保护 C 驱动器

  `uwfmgr.exe filter enable`      启用写入筛选器
  <br>
  `uwfmgr.exe volume protect c:`  保护卷 C
  <br>
  `shutdown /r /t 0`              重启设备，使写入筛选器设置生效

*需要* 重新启动才能使所有 uwfmgr 设置生效。


## <a name="protecting-a-data-volume"></a>保护数据卷

可以使用卷的 GUID 保护 IoT Core 中的数据卷。
可通过以下命令找到可用卷的 GUID

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![保护卷Windows 10 IoT 核心版](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a>建议的排除项
保护数据卷时，建议为 OS 服务访问的服务文件夹和日志记录Windows例外。

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

添加排除项： `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a>维护受 UWF 保护的设备

> [!Note]
> 从 Windows 10 IoT 核心版 版本 1709 版本 16299 开始，主 OS 卷 (C： 可以使用 UWF 进行保护并自动提供服务，无需任何 \) 特殊步骤。

若要使用受保护的数据卷为受 UWF 保护的设备提供服务，需要执行以下步骤。

* `uwfmgr.exe filter disable` 禁用 UWF
* `shutdown /r /t 0` 重新启动设备以禁用 UWF
* 使用预配 (MDM 启用维护服务包以设置更新策略) 
   * 请注意，设备将自动重新启动以执行服务更新
* `uwfmgr.exe filter enable` 启用 UWF
* `shutdown /r /t 0` 重新启动设备以启用 UWF

## <a name="unsupported-uwfmgrexe-commands"></a>不支持uwfmgr.exe命令

**IoT 核心不支持 UWF** 维护模式。

`uwfmgr.exe`on Windows 10 IoT 核心版 不支持下面列出的命令。

```
Filter
    Shutdown
    Restart
Servicing
    Enable
    Disable
    Update-Windows
```
