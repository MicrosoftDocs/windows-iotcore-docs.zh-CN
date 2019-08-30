---
title: Windows 10 IoT Core 命令行实用程序
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解连接到设备后要用于 PowreShell 的命令行实用程序。
keywords: windows iot, 命令行, 命令行实用工具, PowerShell
ms.openlocfilehash: 4ba4ce1b77e14bb6cd8323ce44cb3a7b82ae8dbc
ms.sourcegitcommit: 3aaacf5e3ddbebb4a9324cfc8688110a2eb067ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132263"
---
# <a name="windows-10-iot-core-command-line-utils"></a>Windows 10 IoT Core 命令行实用程序

正在寻找可用于配置设备上的某些设置的工具？ 以下工具可供你使用。 在[连接到你的设备](../connect-your-device/PowerShell.md)后，使用 PowerShell 运行这些命令。

> [!NOTE]
> 这些工具未预先加载-需要包含相应的功能 Id 才能在映像中获取这些工具。

## <a name="iot-core-specific-command-line-utils"></a>IoT Core 特定的命令行 Utils

### <a name="setting-startup-app"></a>**设置启动应用：**
使用启动编辑器在你的 Windows 10 IoT Core 设备上配置启动应用。 借助以下选项之一，运行 `IotStartup`：

* `IotStartup list`，用于列出已安装的应用程序
* `IotStartup list headed`，用于列出已安装的有外设应用程序
* `IotStartup list headless`，用于列出已安装的无外设应用程序
* `IotStartup list [MyApp]`，用于列出已安装的与模式 `MyApp` 匹配的应用程序
* `IotStartup add`，用于添加有外设和无外设应用程序
* `IotStartup add headed [MyApp]`，用于添加与模式 `MyApp` 匹配的有外设应用程序  模式必须只匹配一个应用程序。
* `IotStartup add headless [Task1]`，用于添加与模式 `Task1` 匹配的无外设应用程序
* `IotStartup remove`，用于删除有外设和无外设应用程序
* `IotStartup remove headed [MyApp]`，用于删除与模式 `MyApp` 匹配的有外设应用程序
* `IotStartup remove headless [Task1]`，用于删除与模式 `Task1` 匹配的无外设应用程序
* `IotStartup startup`，用于列出针对启动所注册的有外设和无外设应用程序
* `IotStartup startup [MyApp]`，用于列出针对启动所注册的且与模式 `MyApp` 匹配的有外设和无外设应用程序
* `IotStartup startup headed [MyApp]`，用于列出针对启动所注册的且与 `MyApp` 匹配的有外设应用程序
* `IotStartup startup headless [Task1]`，用于列出针对启动所注册的且与 `Task1` 匹配的无外设应用程序
* `IotStartup run [MyApp]`启动应用标识`MyApp`
* `IotStartup stop [MyApp]`停止应用标识`MyApp`
* 若要获取进一步帮助，请尝试 `IotStartup help`

### <a name="change-settings-for-region-and-user-or-speech-language"></a>**更改区域和用户或语音语言的设置:**

该`IoTSettings`工具更改了区域、用户语言或语音语言。 这是一个命令行工具, 可使用 ProcessLauncher API 从应用程序中调用。 这些命令必须作为默认帐户运行, 而不是以管理员身份运行。

* `IotSettings del account {all | username}`删除系统或特定帐户上的所有 MSA 或 AAD 帐户。  特定帐户采用窗体username@provider.com
* `IotSettings del diagnostics`为当前设备删除云中的诊断信息。  请注意, 这会删除与调用时相同的历史记录。  将继续记录新的诊断信息。
* `IotSettings list account`列出已登录到设备的所有 MSA 或 AAD 帐户。
* `IotSettings list uilanguage`列出所有 UI 语言
* `IotSettings list speechlanguage`列出所有语音语言
* `IotSettings get uilanguage`显示当前 UI 语言
* `IotSettings get speechlanguage`显示当前语音语言
* `IotSettings get region`显示当前区域
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)`设置默认的 UI 语言加拿大法语)
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)`设置加拿大法语)
* `IotSettings set region region\_code - (e.g. CA)`将默认区域设置为加拿大)
* `IotSettings set bluetoothpref {sink | source}`指定在通过 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 功能构建的设备连接到同时支持这两种角色的另一台设备时要选择的蓝牙角色首选项。
* `IotSettings get bluetoothpref`返回通过 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 生成的设备的当前蓝牙角色首选项。  默认值为 source。

> [!TIP]
> `IoTSettings -list uiLanguage`将返回受支持的 UI 语言列表 (在已对其执行的 Windows IoT core 映像版本中)
    
### <a name="change-default-audio-device-and-volume"></a>**更改默认音频设备和卷:**

该`IoTCoreAudioControlTool`工具控制音频相关的选项, 如设置默认捕获和播放设备以及更改卷。 有关参数的完整列表, 请运行`IoTCoreAudioControlTool h`。

### <a name="manually-installing-appx-files"></a>**手动安装。APPX 文件:**
DeployAppx 支持在中安装和删除。开发方案中的 APPX 包。  用于安装的正确方法。生产映像中的 APPX 包是使用[安装应用程序](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd)主题中所述的预配包。  DeployAppx 还支持查询。APPX 包信息。

*  `DeployAppx install MyApp.appx`安装。如果找到, 则为 APPX 和同名证书。
* `DeployAppx install force MyApp.appx`强制卸载当前安装的。如果在安装新的之前找到了相同的包名称, 则为 APPX。约.  这对于安装是非常有用的。APPX, 与当前安装的版本号相同或较低。约.
* `DeployAppx install retry MyApp.appx`重试安装。APPX 10 次失败, 两次尝试之间的延迟为2秒。
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123`卸载具有匹配的包全名的 .appx。
*  `DeployAppx uninstall MyApp.appx`卸载已安装的任何。具有匹配包系列名称的 APPX。
* `DeployAppx getpackages`列出已安装的包的完整名称。
* `DeployAppx getpackageid IotCoreDefaultApp.appx`输出包名称、包系列名称和包的完整名称。约.
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml`不支持


## <a name="general-command-line-utils"></a>常规命令行 Utils

### <a name="update-account-password"></a>**更新帐户密码：**

强烈建议你更新默认的管理员帐户密码。 若要更新帐户密码，你可以发出以下命令：`net user Administrator [new password]`（其中 `[new password]` 表示你选择的强密码）。

### <a name="create-local-user-accounts"></a>**创建本地用户帐户：**

如果你想要授予其他人访问你的 Windows IoT Core 设备的权限，你可以通过在 `net user [username] [password] /add` 中键入，并使用 PS 创建其他本地用户帐户。 如果你想要将此用户添加到其他组（例如管理员组），则使用 `net localgroup Administrators [username] /add`。

### <a name="set-password"></a>**设置密码:**

若要更改你的设备上的帐户密码，可通过运行 `net user [account-username] [new-password]` 来更改帐户密码。

### <a name="query-and-set-device-name"></a>**查询和设置设备名称：**

若要确定当前设备名称，只需键入 `hostname`。 若要更改你的 Windows IoT Core 设备的名称，应键入 `SetComputerName [new machinename]`。 你可能需要重新启动你的设备才能使更改的名称生效。

### <a name="basic-network-configuration"></a>**基本网络配置：**

您可能已熟悉的许多基本网络配置实用工具在 Windows IoT Core (包括`ping.exe` `netsh.exe`、 `tracert.exe` `netstat.exe` `ipconfig.exe`、、、和`arp.exe`等命令) 中可用。

### <a name="copy-utilities"></a>**复制实用程序：**

Microsoft 将提供熟悉的工具，包括 `sfpcopy.exe` 以及 `xcopy.exe`。

### <a name="process-management"></a>**进程管理：**

若要查看当前正在运行的进程，可以尝试 `get-process` 或 `tlist.exe`。 若要停止正在运行的进程，请键入 `kill.exe [pid or process name]`。


### <a name="set-boot-option-headless-vs-headed-boot"></a>**设置启动选项（无外设与有外设启动）：**

Windows IoT Core 设备可以设置为有外设设备模式（需要显示功能时）或无外设设备模式（显示功能不是必需项或不可用时）。 若要更改此设置，请使用 `setbootoption.exe [headed | headless]`。

> [!NOTE]
> 更改此设置将需要重新启动才能使更改生效。

### <a name="task-scheduler"></a>**任务计划程序：**

若要查看计划任务的当前列表，请使用 `schtasks.exe` 命令。 你可以使用 `/create` 开关创建新任务，或使用 `/run` 开关运行按需任务。 若要获取支持的参数的完整列表，请使用 `schtasks.exe /?`

### <a name="device-drivers"></a>**设备驱动程序：**

设备控制台实用程序在识别和管理已安装的设备和驱动程序方面十分有用。 若要获取参数的完整列表，请使用 `devcon.exe /?`

### <a name="registry-access"></a>**注册表访问：**

如果你需要通过访问注册表来查看或修改设置，请使用 `reg.exe /?` 命令获取有关支持的参数的完整列表。

### <a name="services"></a>**服务：**

管理 Windows 服务可以通过 `net.exe` 命令来完成。 若要查看运行中的服务的列表，请键入 `net start`。 若要启动或停止特定的服务，请键入 `net [start | stop] [service name]`。 此外，还可以通过 `sc.exe` 命令使用服务控制管理器。

### <a name="boot-configuration"></a>**启动配置：**

你可以通过使用`bcdedit.exe`对 Windows IoT Core 设备的启动配置进行更改。 例如, 可以使用`bcdedit –set testsigning on`命令来启用 testsigning。

### <a name="shutdownrestart-device"></a>**关闭/重新启动设备：**

若要关闭设备，请键入 `shutdown /s /t 0`。 若要重新启动设备, 请`/r`改用命令。 `shutdown /r /t 0`

### <a name="viewing-and-changing-display-settings"></a>**查看和更改显示设置**
SetDisplayResolution 工具可用于列出当前显示设置并显示受支持值的列表。  它可以进一步用于调整显示器的分辨率、刷新率和/或方向, 以适应平台支持的值。  实用程序接受以下命令行参数:

* `SetDisplayResolution`列出当前显示的 resoltuion。
* `SetDisplayResolution -list`列出支持的显示分辨率。
* `SetDisplayResolution -orientation:[n]`更改显示方向, 其中 n = 0、90180或270。
* `SetDisplayResolution [width] [height]`更改宽度和高度 (以像素为单位) 
* `SetDisplayResolution [width] [height] [refreshrate]`更改宽度、高度和刷新率, 其中宽度和高度以像素为单位, refreshrate 以 Hz 为单位。 
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]`更改 width、height、refreshrate 和 screen 的宽度和高度 (以像素为单位), refreshrate 以 Hz 为单位, 方向为0、90、180或270。

### <a name="take-screenshot"></a>**拍摄屏幕截图:**

你可以使用`ScreenCapture.exe`来获取 Windows IoTCore 设备的屏幕截图。 例如, "运行`ScreenCapture c:\folder\screencap.jpg` " 将获取屏幕截图, 并将其保存在截图文件中。

### <a name="get-information-about-network-adapters"></a>**获取网络适配器的相关信息:**

若要查看所有可用网络适配器的列表, 请运行`GetAdapterInfo`工具。

### <a name="set-folder-permissions-for-uwp-apps"></a>**设置 UWP 应用的文件夹权限:**

不是设备上的所有文件夹都访问通用 Windows 应用。 若要将文件夹访问到 UWP 应用, 可以使用`FolderPermissions`工具。 例如, 运行`FolderPermissions c:\test -e`来向 UWP 应用提供对`c:\test`文件夹的访问权限。 请注意, 这仅适用于示例的本机 Win32 api。 CreateFile2, 而不是采用 WinRT api, 如 StorageFolder、StorageFile 等。

### <a name="work-with-serial-ports"></a>**使用串行端口:**
[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm)使你能够从命令行使用串行端口。 它作为示例项目提供到了 ms iot 示例存储库中。 

``` 
Usage: MinComm.exe [-list] device_path [baud=<B>] [parity=<P>] [data=<D>] [stop=<S>] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]

  -list                List all available serial ports on the system and exit.
  device_path          Device path or COM port to open (e.g. COM1)
  baud=<B>             Specifies the transmission rate in bits per second.
  parity={n|e|o|m|s}   Specifies how the system uses the parity bit to check
                       for transmission errors. The abbreviations stand for
                       none, even, odd, mark, and space.
  data={5|6|7|8}       Specifies the number of data bits in a character.
  stop={1|1.5|2}       Specifies the number of stop bits that define the end of
                       a character.
  xon={on|off}         Specifies whether the xon or xoff protocol for data-flow
                       control is on or off.
  odsr={on|off}        Specifies whether output handshaking that uses the
                       Data Set Ready (DSR) circuit is on or off.
  octs={on|off}        Specifies whether output handshaking that uses the
                       Clear To Send (CTS) circuit is on or off.
  dtr={on|off|hs}      Specifies whether the Data Terminal Ready (DTR) circuit
                       is on or off or set to handshake.
  rts={on|off|hs|tg}   Specifies whether the Request To Send (RTS) circuit is
                       set to on, off, handshake, or toggle.
  idsr={on|off}        Specifies whether the DSR circuit sensitivity is on
                       or off.

Parameters that are not specified will default to the port's current
configuration. For more information on the connection parameters, see the
Technet documentation for the Mode command:
  https://technet.microsoft.com/library/cc732236.aspx

Examples:
  Connect to the first serial port found in the port's current configuration:
    MinComm.exe

  List all serial ports on the system:
    MinComm.exe -list

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe COM1 baud=115200 parity=n data=8 stop=1

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe \\.\COM1 baud=115200 parity=n data=8 stop=1

  Open device interface in 115200 8N1 configuration:
    MinComm.exe \\?\USB#VID_FFFF&PID_0005#{86e0d1e0-8089-11d0-9ce4-08003e301f73} baud=115200 parity=n data=8 stop=1```


