---
title: Windows 10 IoT Core 命令行实用程序
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解要连接到你的设备后用于 PowreShell 的命令行实用程序。
keywords: windows iot、 命令行、 命令行实用工具，PowerShell
ms.openlocfilehash: 2fb009115dc929540c30d5403c1877051f6b7037
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510878"
---
# <a name="windows-10-iot-core-command-line-utils"></a>Windows 10 IoT Core 命令行实用程序

正在寻找可用于配置设备上的某些设置的工具？ 以下工具是可供您使用可用。 在[连接到你的设备](../connect-your-device/PowerShell.md)后，使用 PowerShell 运行这些命令。

> [!NOTE]
> 这些工具不会预先加载-你将需要包括适当的功能 Id 以在图像中获取这些工具。

## <a name="iot-core-specific-command-line-utils"></a>特定于 IoT Core 的命令行实用工具

### **<a name="setting-startup-app"></a>设置启动应用程序：**
使用启动编辑器在你的 Windows 10 IoT Core 设备上配置启动应用。 借助以下选项之一，运行 `IotStartup`：

* `IotStartup list` 列出已安装的应用程序
* `IotStartup list headed` 列出已安装向应用程序
* `IotStartup list headless` 列出已安装的无外设的应用程序
* `IotStartup list [MyApp]` 列出已安装的应用程序与模式匹配 `MyApp`
* `IotStartup add` 添加主和无外设的应用程序
* `IotStartup add headed [MyApp]` 将与模式匹配的主应用程序添加`MyApp`。  模式必须只匹配一个应用程序。
* `IotStartup add headless [Task1]` 添加无外设与模式匹配的应用程序 `Task1`
* `IotStartup remove` 删除讲述的内容和无外设的应用程序
* `IotStartup remove headed [MyApp]` 删除讲述的内容与模式匹配的应用程序 `MyApp`
* `IotStartup remove headless [Task1]` 删除无外设与模式匹配的应用程序 `Task1`
* `IotStartup startup` 为启动讲述的内容的列表和无外设的应用程序注册
* `IotStartup startup [MyApp]` 讲述的内容的列表和无外设的应用程序注册为启动该匹配模式 `MyApp`
* `IotStartup startup headed [MyApp]` 列表讲述的内容匹配的应用程序启动时注册 `MyApp`
* `IotStartup startup headless [Task1]` 列出了无外设匹配的应用程序启动时注册 `Task1`

    * 有关更多帮助，请尝试 `IotStartup help`
    
### **<a name="change-settings-for-region-and-user-or-speech-language"></a>更改区域和用户或语音语言设置：**

`IoTSettings`工具更改区域、 用户语言或语音语言。 这是可以从使用 ProcessLauncher API 的应用程序调用的命令行工具。 这些命令必须作为默认帐户，不是管理员身份运行。

* `IotSettings del account {all | username}` 删除系统上的所有 MSA 或 AAD 帐户或特定的帐户。  特定帐户采用窗体 username@provider.com
* `IotSettings del diagnostics` 删除当前的设备在云中的诊断信息。  请注意，这将删除到调用的时间的历史记录。  新的诊断信息仍要记入日志。
* `IotSettings list account` 列出所有 MSA 或 AAD 帐户登录到的设备。
* `IotSettings list uilanguage` 列出所有的 UI 语言
* `IotSettings list speechlanguage` 列出所有语音语言
* `IotSettings get uilanguage` 显示当前 UI 语言
* `IotSettings get speechlanguage` 显示当前语音语言
* `IotSettings get region` 显示当前的区域
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)` 设置默认 UI 语言加拿大法语）
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` 设置语音语言加拿大法语）
* `IotSettings set region region\_code - (e.g. CA)` 将默认区域设置为加拿大）
* `IotSettings set bluetoothpref {sink | source}` 指定蓝牙角色首选项时使用 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 功能生成的设备连接到另一台设备同时支持这两个角色选择。
* `IotSettings get bluetoothpref` 返回使用 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 构建的设备的当前蓝牙角色首选项。  默认值为源。

> [!TIP]
> `IoTSettings -list uiLanguage` 将为返回受支持的 UI 语言的列表 （在 Windows IoT core 映像已针对执行的版本）
    
### **<a name="change-default-audio-device-and-volume"></a>更改默认音频设备和卷：**

`IoTCoreAudioControlTool`工具控制音频相关的选项，如设置捕获和播放设备的默认值和更改音量。 有关参数的完整列表，运行`IoTCoreAudioControlTool h`。

### **<a name="manually-installing-appx-files"></a>手动安装。APPX 文件：**
DeployAppx 使安装和删除。在开发方案的 APPX 包。  安装的正确方法。在生产映像中的 APPX 包是使用预配包，如中所述[安装您的应用程序](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd)主题。  DeployAppx 还支持查询。APPX 包信息。

*  `DeployAppx install MyApp.appx` 安装。APPX 和具有相同名称的证书如果找到。
* `DeployAppx install force MyApp.appx` 强制卸载当前安装。如果名称与同一个包的 APPX 安装新之前找到。APPX。  这可用于安装。作为当前安装的相同或更低版本号的 APPX。APPX。
* `DeployAppx install retry MyApp.appx` 重试安装。在失败时使用 2 个第二个 APPX 10 次尝试的时间间隔。
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123` 卸载.appx 具有匹配的包完整名称。
*  `DeployAppx uninstall MyApp.appx` 卸载任何已安装。具有匹配的包系列名称的 APPX。
* `DeployAppx getpackages` 列出已安装的包完整名称。
* `DeployAppx getpackageid IotCoreDefaultApp.appx` 打印出包名称、 包系列名称和包的完整名称。APPX。
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml` 不受支持


## <a name="general-command-line-utils"></a>常规命令行实用工具

### **<a name="update-account-password"></a>更新帐户密码：**

强烈建议你更新默认的管理员帐户密码。 若要更新帐户密码，你可以发出以下命令：`net user Administrator [new password]`（其中 `[new password]` 表示你选择的强密码）。

### **<a name="create-local-user-accounts"></a>创建本地用户帐户：**

如果你想要授予其他人访问你的 Windows IoT Core 设备的权限，你可以通过在 `net user [username] [password] /add` 中键入，并使用 PS 创建其他本地用户帐户。 如果你想要将此用户添加到其他组（例如管理员组），则使用 `net localgroup Administrators [username] /add`。

### **<a name="set-password"></a>设置密码：**

若要更改你的设备上的帐户密码，可通过运行 `net user [account-username] [new-password]` 来更改帐户密码。

### **<a name="query-and-set-device-name"></a>查询和设置设备名称：**

若要确定当前设备名称，只需键入 `hostname`。 若要更改你的 Windows IoT Core 设备的名称，应键入 `SetComputerName [new machinename]`。 你可能需要重新启动你的设备才能使更改的名称生效。

### **<a name="basic-network-configuration"></a>基本网络配置：**

许多您可能已经熟悉的基本网络配置实用工具都可以在 Windows IoT Core 中，其中包括命令，例如`ping.exe`， `netstat.exe`， `netsh.exe`， `ipconfig.exe`， `tracert.exe`，并`arp.exe`。

### **<a name="copy-utilities"></a>将复制实用程序：**

Microsoft 将提供熟悉的工具，包括 `sfpcopy.exe` 以及 `xcopy.exe`。

### **<a name="process-management"></a>进程管理：**

若要查看当前正在运行的进程，可以尝试 `get-process` 或 `tlist.exe`。 若要停止正在运行的进程，请键入 `kill.exe [pid or process name]`。


### **<a name="set-boot-option-headless-vs-headed-boot"></a>设置启动选项 （无外设与主启动）：**

Windows IoT Core 设备可以设置为有外设设备模式（需要显示功能时）或无外设设备模式（显示功能不是必需项或不可用时）。 若要更改此设置，请使用 `setbootoption.exe [headed | headless]`。

> [!NOTE]
> 更改此设置将需要重新启动顺序的更改才能生效。

### **<a name="task-scheduler"></a>任务计划程序：**

若要查看计划任务的当前列表，请使用 `schtasks.exe` 命令。 你可以使用 `/create` 开关创建新任务，或使用 `/run` 开关运行按需任务。 对于受支持的参数的完整列表，请使用 `schtasks.exe /?`

### **<a name="device-drivers"></a>设备驱动程序：**

设备控制台实用程序在识别和管理已安装的设备和驱动程序方面十分有用。 对于参数的完整列表，请使用 `devcon.exe /?`

### **<a name="registry-access"></a>注册表访问权限：**

如果你需要通过访问注册表来查看或修改设置，请使用 `reg.exe /?` 命令获取有关支持的参数的完整列表。

### **<a name="services"></a>服务：**

管理 Windows 服务可以通过 `net.exe` 命令来完成。 若要查看运行中的服务的列表，请键入 `net start`。 若要启动或停止特定的服务，请键入 `net [start | stop] [service name]`。 此外，还可以通过 `sc.exe` 命令使用服务控制管理器。

### **<a name="boot-configuration"></a>启动配置：**

可以在 Windows IoT Core 设备的启动配置进行更改，通过使用`bcdedit.exe`。 例如，可启用 testsigning 与`bcdedit –set testsigning on`命令。

### **<a name="shutdownrestart-device"></a>关闭/重新启动设备：**

若要关闭设备，请键入 `shutdown /s /t 0`。 若要重新启动设备，请使用`/r`改为开关与命令`shutdown /r /t 0`。

### **<a name="viewing-and-changing-display-settings"></a>查看和更改显示设置**
可能使用 SetDisplayResolution 工具，用于列出当前的显示设置和显示的支持的值的列表。  它可以进一步使用调整显示器的分辨率、 刷新频率和/或为你的平台支持的值的方向。  该实用程序接受以下的命令行参数：

* `SetDisplayResolution` 列出了当前显示 resoltuion。
* `SetDisplayResolution -list` 列出支持的显示分辨率。
* `SetDisplayResolution -orientation:[n]` 更改显示方向，其中 n = 0、 90、 180 或 270。
* `SetDisplayResolution [width] [height]` 更改宽度和高度 （像素） 
* `SetDisplayResolution [width] [height] [refreshrate]` 更改宽度、 高度和刷新率的宽度和高度位于像素和 refreshrate hz 
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]` 更改宽度、 高度、 refreshrate 和屏幕方向的宽度和高度均以像素为单位，在 Hz refreshrate 和方向是 0、 90、 180 或 270 之一。

### **<a name="take-screenshot"></a>拍摄的屏幕快照：**

使用可用来拍摄 Windows IoTCore 设备的屏幕截图`ScreenCapture.exe`。 例如，运行`ScreenCapture c:\folder\screencap.jpg`将屏幕截图并将其保存在 screencap.jpg 文件中。

### **<a name="get-information-about-network-adapters"></a>获取有关网络适配器的信息：**

若要查看所有可用的网络适配器的列表，请运行`GetAdapterInfo`工具。

### **<a name="set-folder-permissions-for-uwp-apps"></a>设置适用于 UWP 应用的文件夹权限：**

在设备上的不是所有文件夹都是通过通用 Windows 应用的访问。 若要对 UWP 应用进行文件夹访问，可以使用`FolderPermissions`工具。 例如运行`FolderPermissions c:\test -e`要提供 UWP 应用访问权限`c:\test`文件夹。 请注意这会仅使用本机 Win32 api，可用于例如。 CreateFile2 而不能使用 WinRT api，如 StorageFolder，StorageFile 等。

### **<a name="work-with-serial-ports"></a>使用串行端口：**
[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm)使您可以使用命令行中的串行端口。 它作为 ms iot 示例存储库中的示例项目提供。 

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


