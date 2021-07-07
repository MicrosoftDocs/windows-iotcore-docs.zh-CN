---
title: Windows 10 IoT 核心版命令行实用程序
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解连接到设备后用于 PowerShell 的命令行实用程序。
keywords: windows iot，命令行，命令行实用工具，PowerShell
ms.openlocfilehash: b52f0ca49bfa27721099b2546d92e2ae0eda06e9
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229434"
---
# <a name="windows-10-iot-core-command-line-utils"></a>Windows 10 IoT 核心版命令行 Utils

想要在设备上配置某些设置？ 以下工具可供你使用。 在 [连接到你的设备](../connect-your-device/PowerShell.md)后，使用 PowerShell 来运行这些命令。

> [!NOTE]
> 这些工具未预先加载-需要包含相应的功能 Id 才能在映像中获取这些工具。

## <a name="iot-core-specific-command-line-utils"></a>IoT Core 特定的命令行 Utils

### <a name="setting-startup-app"></a>**设置启动应用程序：**
使用启动编辑器在 Windows IoT 核心设备上配置启动应用。 `IotStartup`用以下任一选项运行：

* `IotStartup list` 列出已安装的应用程序
* `IotStartup list headed` 列出已安装的应用程序
* `IotStartup list headless` 列出安装的无外设应用程序
* `IotStartup list [MyApp]` 列出与模式匹配的已安装应用程序 `MyApp`
* `IotStartup add` 添加头和无外设应用程序
* `IotStartup add headed [MyApp]` 添加匹配模式的应用程序 `MyApp` 。  模式只能与一个应用程序匹配。
* `IotStartup add headless [Task1]` 添加匹配模式的无外设应用程序 `Task1`
* `IotStartup remove` 删除头和无外设应用程序
* `IotStartup remove headed [MyApp]` 删除匹配模式的头应用程序 `MyApp`
* `IotStartup remove headless [Task1]` 删除与模式匹配的无外设应用程序 `Task1`
* `IotStartup startup` 列出注册为启动的头和无外设应用程序
* `IotStartup startup [MyApp]` 列出注册为与模式匹配的启动的头和无外设应用程序 `MyApp`
* `IotStartup startup headed [MyApp]` 列出注册为启动的应用程序匹配的应用程序 `MyApp`
* `IotStartup startup headless [Task1]` 列出注册为启动的无外设应用程序匹配 `Task1`
* `IotStartup run [MyApp]` 启动应用标识 `MyApp`
* `IotStartup stop [MyApp]` 停止应用标识 `MyApp`
* 如需进一步的帮助，请尝试 `IotStartup help`

### <a name="change-settings-for-region-and-user-or-speech-language"></a>**更改区域和用户或语音语言的设置：**

该 `IoTSettings` 工具更改了区域、用户语言或语音语言。 这是一个命令行工具，可使用 ProcessLauncher API 从应用程序中调用。 这些命令必须作为默认帐户运行，而不是以管理员身份运行。

* `IotSettings del account {all | username}` 删除系统上的所有 MSA 或 Azure AD 帐户或特定的帐户。  特定帐户采用窗体 username@provider.com
* `IotSettings del diagnostics` 为当前设备删除云中的诊断信息。  请注意，这会删除与调用时相同的历史记录。  将继续记录新的诊断信息。
* `IotSettings list account` 列出已登录到设备的所有 MSA 或 Azure AD 帐户。
* `IotSettings list uilanguage` 列出所有 UI 语言
* `IotSettings list speechlanguage` 列出所有语音语言
* `IotSettings get uilanguage` 显示当前 UI 语言
* `IotSettings get speechlanguage` 显示当前语音语言
* `IotSettings get region` 显示当前区域
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)` 设置默认的 UI 语言加拿大法语) 
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` 设置语音语言法语（加拿大）) 
* `IotSettings set region region\_code - (e.g. CA)` 将默认区域设置为加拿大) 
* `IotSettings set bluetoothpref {sink | source}`指定在采用 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 功能构建的设备连接到同时支持这两种角色的另一台设备时要选择蓝牙角色首选项。
* `IotSettings get bluetoothpref`返回 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 生成的设备的当前蓝牙角色首选项。  默认值为 source。

> [!TIP]
> `IoTSettings -list uiLanguage`会在对其执行的 Windows IoT 核心映像的版本中，为 (提供支持的 UI 语言列表) 

### <a name="change-default-audio-device-and-volume"></a>**更改默认音频设备和卷：**

该 `IoTCoreAudioControlTool` 工具控制音频相关的选项，如设置默认捕获和播放设备以及更改卷。 有关参数的完整列表，请运行 `IoTCoreAudioControlTool h` 。

### <a name="manually-installing-appx-files"></a>**手动安装。APPX 文件：**
DeployAppx 支持在中安装和删除。开发方案中的 APPX 包。  用于安装的正确方法。生产映像中的 APPX 包是使用 [安装应用程序](https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) 主题中所述的预配包。  DeployAppx 还支持查询。APPX 包信息。

*  `DeployAppx install MyApp.appx` 安装。如果找到，则为 APPX 和同名证书。
* `DeployAppx install force MyApp.appx` 强制卸载当前安装的。如果在安装新的之前找到了相同的包名称，则为 APPX。约.  这对于安装是非常有用的。APPX，与当前安装的版本号相同或较低。约.
* `DeployAppx install retry MyApp.appx` 重试安装。APPX 10 次失败，两次尝试之间的延迟为2秒。
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123` 卸载具有匹配的包全名的 .appx。
*  `DeployAppx uninstall MyApp.appx` 卸载已安装的任何。具有匹配包系列名称的 APPX。
* `DeployAppx getpackages` 列出已安装的包的完整名称。
* `DeployAppx getpackageid IotCoreDefaultApp.appx` 输出包名称、包系列名称和包的完整名称。约.
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml` 不支持


## <a name="general-command-line-utils"></a>常规命令行 Utils

### <a name="update-account-password"></a>**更新帐户密码：**

强烈建议您更新管理员帐户的默认密码。 为此，可以发出以下命令： `net user Administrator [new password]` 其中 `[new password]` 表示所选的强密码。

### <a name="create-local-user-accounts"></a>**创建本地用户帐户：**

如果要向其他人授予对 Windows IoT 核心设备的访问权限，则可以通过键入来使用 PS 创建其他本地用户帐户 `net user [username] [password] /add` 。 如果希望将此用户添加到其他组（如管理员组），请使用 `net localgroup Administrators [username] /add` 。

### <a name="set-password"></a>**设置密码：**

若要更改设备上帐户的密码，请运行 `net user [account-username] [new-password]` 以更改帐户密码。

### <a name="query-and-set-device-name"></a>**查询和设置设备名称：**

若要确定当前设备名称，只需键入即可 `hostname` 。 若要更改 Windows IoT 核心设备的名称，请键入 `SetComputerName [new machinename]` 。 你可能需要重新启动设备以使名称更改生效。

### <a name="basic-network-configuration"></a>**基本网络配置：**

您可能已熟悉的许多基本网络配置实用程序在 Windows IoT 核心中提供，其中包括、、、、 `ping.exe` 和等命令 `netstat.exe` `netsh.exe` `ipconfig.exe` `tracert.exe` `arp.exe` 。

### <a name="copy-utilities"></a>**复制实用工具：**

Microsoft 提供熟悉的工具，包括 `sfpcopy.exe` 和 `xcopy.exe` 。

### <a name="process-management"></a>**流程管理：**

若要查看当前正在运行的进程，可以尝试 `get-process` 或 `tlist.exe` 。 若要停止正在运行的进程，请键入 `kill.exe [pid or process name]` 。


### <a name="set-boot-option-headless-vs-headed-boot"></a>**设置启动选项 (无外设 vs Boot) ：**

Windows如果需要显示功能，可以将 IoT 核心设备设置为 () 或无外设 (当) 设备模式下不需要或不可用时。 若要更改此设置，请使用 `setbootoption.exe [headed | headless]` 。

> [!NOTE]
> 更改此设置将需要重新启动才能使更改生效。

### <a name="task-scheduler"></a>**任务计划程序：**

若要查看计划任务的当前列表，请使用 `schtasks.exe` 命令。 可以通过开关创建新任务， `/create` 也可以用开关运行按需任务 `/run` 。 有关受支持参数的完整列表，请使用 `schtasks.exe /?`

### <a name="device-drivers"></a>**设备驱动程序：**

设备控制台实用工具可用于识别和管理已安装的设备和驱动程序。 有关参数的完整列表，请使用 `devcon.exe /?`

### <a name="registry-access"></a>**注册表访问：**

如果需要访问注册表以查看或修改设置，请使用 `reg.exe /?` 命令获取受支持参数的完整列表。

### <a name="services"></a>**服务：**

可以通过命令来实现 Windows 服务的管理 `net.exe` 。 若要查看正在运行的服务的列表，请键入 `net start` 。 若要启动或停止特定服务，请键入 `net [start | stop] [service name]` 。 此外，也可以通过命令使用服务控制管理器 `sc.exe` 。

### <a name="boot-configuration"></a>**启动配置：**

你可以通过使用对 Windows IoT 核心设备的启动配置进行更改 `bcdedit.exe` 。 例如，可以使用命令来启用 testsigning `bcdedit –set testsigning on` 。

### <a name="shutdownrestart-device"></a>**关机/重新启动设备：**

若要关闭设备，请键入 `shutdown /s /t 0` 。 若要重新启动设备，请改用 `/r` 命令 `shutdown /r /t 0` 。

### <a name="viewing-and-changing-display-settings"></a>**查看和更改显示设置**
SetDisplayResolution 工具可用于列出当前显示设置并显示受支持值的列表。  它可以进一步用于调整显示器的分辨率、刷新率和/或方向，以适应平台支持的值。  实用程序接受以下命令行参数：

* `SetDisplayResolution` 列出当前显示分辨率。
* `SetDisplayResolution -list` 列出支持的显示分辨率。
* `SetDisplayResolution -orientation:[n]` 更改显示方向，其中 n = 0、90180或270。
* `SetDisplayResolution [width] [height]` 更改宽度和高度（以像素为单位）
* `SetDisplayResolution [width] [height] [refreshrate]` 更改宽度、高度和刷新率，其中宽度和高度以像素为单位，refreshrate 以 Hz 为单位。
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]` 更改 width、height、refreshrate 和 screen 的宽度和高度（以像素为单位），refreshrate 以 Hz 为单位，方向为0、90、180或270。

### <a name="take-screenshot"></a>**拍摄屏幕截图：**

你可以使用来获取 Windows IoTCore 设备的屏幕截图 `ScreenCapture.exe` 。 例如，"运行 `ScreenCapture c:\folder\screencap.jpg` " 将获取屏幕截图，并将其保存到 screencap.jpg 文件中。

### <a name="get-information-about-network-adapters"></a>**获取网络适配器的相关信息：**

若要查看所有可用网络适配器的列表，请运行 `GetAdapterInfo` 工具。

### <a name="set-folder-permissions-for-uwp-apps"></a>**设置 UWP 应用的文件夹权限：**

并非设备上的所有文件夹都可供通用 Windows 应用访问。 若要使某个文件夹可供 UWP 应用访问，可以使用 `FolderPermissions` 工具。 例如，运行 `FolderPermissions c:\test -e` 以提供 UWP 应用对 `c:\test` 文件夹的访问权限。 请注意，这仅适用于示例的本机 Win32 api。 CreateFile2，而不是采用 WinRT api，如 StorageFolder、StorageFile 等。

### <a name="work-with-serial-ports"></a>**使用串行端口：**
[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) 使你能够从命令行使用串行端口。 它作为示例项目提供到了 ms iot 示例存储库中。

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
    MinComm.exe \\?\USB#VID_FFFF&PID_0005#{86e0d1e0-8089-11d0-9ce4-08003e301f73} baud=115200 parity=n data=8 stop=1
```
