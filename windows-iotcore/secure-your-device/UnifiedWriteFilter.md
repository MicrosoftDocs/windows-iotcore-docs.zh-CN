---
title: 使用统一写入筛选器
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用统一写入筛选器保护物理存储媒体的数据写入。
keywords: windows iot，统一写入筛选器，安全，内存，存储媒体
ms.openlocfilehash: 78f9780c6d8fd5850ef3ca362c439c9a8c65c7a1
ms.sourcegitcommit: 7b4f4da423dccbbf038f32e2fba94ae1287da355
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/24/2020
ms.locfileid: "95820622"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a>使用统一写入筛选器 (Windows 10 IoT Core 上的 UWF) 

统一写入筛选器 (UWF) 是一项功能，可保护物理存储媒体的数据写入。 UWF 将拦截所有针对受保护卷的写入尝试，并将这些写入尝试重定向到虚拟覆盖。 这可改进设备的可靠性和稳定性，同时减少写入敏感介质（例如，诸如固态硬盘等闪存介质）的损耗。

有关详细信息，请参阅有关 [统一写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) 的文档。

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a>如何在运行 Windows 10 IoT Core 的设备上安装 UWF

* 如果尚未安装最新版本的 Windows 10 IoT Core 工具包，请下载并安装 [windows 10 Iot Core 包](https://www.microsoft.com/en-us/software-download/windows10iotcore)。
* 根据设备体系结构，将 azure 包 `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` 从电脑 () 复制 ( 和 ) `C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\` 到设备 (例如，通过 [Windows 文件共享](../manage-your-device/WindowsFileSharing.md)) 。
* 启动 [SSH](../connect-your-device/SSH.md) 或 [PowerShell](../connect-your-device/PowerShell.md) ，并访问运行 Windows 10 IoT Core 的设备。
* 在 SSH 或 PowerShell 中，执行以下操作：
  * 更改到已将文件复制到的目录
    * `cd C:\<dir>`
  * 运行以下命令，将包安装到 IoT 设备系统映像：
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* 设备将启动到更新操作系统，安装 UWF 功能，并重新启动到 MainOS。
* 设备返回到 MainOS 后，UWF 功能便已准备就绪，可供使用。 可以通过 ```uwfmgr.exe``` 在 PowerShell 或 SSH 窗口中键入来验证这一点。

  ![Windows 10 IoT Core 上的 uwfmgr.exe](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a>如何在自定义 FFU 中包含 UWF

* 将 **IOT_UNIFIED_WRITE_FILTER** 功能 ID 添加到 OEM 输入文件
* 创建 image\FFU。 有关说明，请参阅 [创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 。


## <a name="how-to-use-uwf"></a>如何使用 UWF

可以通过 PowerShell 或 SSH 会话使用 uwfmgr.exe 工具配置 UWF。
针对可用选项的读取[ `uwfmgr.exe` 工具](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe)，其中的某些命令例外，IoT Core 不支持这些命令。
查看覆盖配置的默认设置，并根据需要对其进行调整。

还可以使用 [统一写入筛选器 CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)通过 MDM 通道配置 UWF。


* 例如，以下命令组合可使 uwfmgr 和 configure 来保护 C 驱动器

  `uwfmgr.exe filter enable`      启用写入筛选器
  <br>
  `uwfmgr.exe volume protect c:`  保护卷 C
  <br>
  `shutdown /r /t 0`              重新启动设备以使写入筛选器设置生效

需要 *重新启动* 才能使所有 uwfmgr 设置生效。


## <a name="protecting-a-data-volume"></a>保护数据卷

可以使用卷的 GUID 保护 IoT Core 中的数据量。
可用卷的 GUID 可通过以下命令找到

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![保护 Windows 10 IoT Core 上的卷](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a>建议排除项
保护数据卷时，建议你为 Windows OS 服务访问的服务和日志记录文件夹添加例外。

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

添加排除项： `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a>为 UWF 受保护设备提供服务

> [!Note]
> 启动 Windows 10 IoT Core 版本1709，版本16299，主 OS 卷 (C： \) 可以通过 UWF 进行保护，并 *自动* 提供服务而无需任何特殊步骤。

对于包含受保护的数据卷的 UWF 保护设备，需要执行以下步骤。

* `uwfmgr.exe filter disable` 禁用 UWF
* `shutdown /r /t 0` 重新启动设备以禁用 UWF
* 使用预配包或 MDM 启用维护 (来设置更新策略) 
   * 请注意，设备将自动重新启动以执行服务更新
* `uwfmgr.exe filter enable` 启用 UWF
* `shutdown /r /t 0` 重新启动设备以启用 UWF

## <a name="unsupported-uwfmgrexe-commands"></a>不支持的 uwfmgr.exe 命令

IoT 核心不支持 **UWF 服务模式**。

`uwfmgr.exe` 在 Windows 10 IoT Core 上不支持下面列出的命令。

```
Filter
    Shutdown
    Restart
Servicing
    Enable
    Disable
    Update-Windows
```
