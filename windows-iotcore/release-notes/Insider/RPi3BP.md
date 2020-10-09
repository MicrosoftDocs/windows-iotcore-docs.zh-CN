---
title: Raspberry Pi 3B + 的发行说明
ms.date: 05/16/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 阅读发行说明，了解 Raspberry Pi 3B + 内部版本包含的内容。 查看该内部版本中的已知问题。
keywords: windows iot, Windows 预览体验成员, 发行说明, Raspberry Pi 3B +
ms.openlocfilehash: 93dfb07d2b16dca2a7c282bd2b1fc57ccd8cccac
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91657203"
---
# <a name="release-notes-for-raspberry-pi-3b"></a>Raspberry Pi 3B + 的发行说明

&copy; 2018 Microsoft Corporation。 保留所有权利。

> [!NOTE]
> Raspberry Pi 3B+ 的此版本是不受支持的技术预览版。 已完成有限的验证和启用。 在[此处](https://www.microsoft.com/en-us/software-download/windowsiot)可找到当前版本。 若要获得更好的评估体验，或者要将产品商用化，请使用 Raspberry Pi 3B 或者其他带有受支持的 Intel、Qualcomm 或 NXP SoC 的设备。 若要排查 Raspberry Pi 3B+ 的问题，请参阅[此处](https://docs.microsoft.com/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)的故障排除指南。 

## <a name="whats-new-in-this-build"></a>此内部版本的新增功能： 
* 常规 Bug 修复

## <a name="known-issues-in-this-build"></a>此版本中的已知问题：
* 此映像仅适用于 RPi3B +，并且不会在 RPi2 上启动。 
* 不能在 IoT 核心版上通过 Visual Studio 进行 F5 驱动程序部署。 
* 板载 WIFI 和蓝牙不适用于 RPI3B +。 
* Ft5406 触摸屏驱动程序在 RPi3B + 上禁用。 
* SD 卡活动 LED 禁用。 


### <a name="display-resolution-is-monitor-is-disconnected"></a>显示器分辨率（在显示器断开连接的情况下）
在监视器断开连接的情况下，Raspberry Pi 3B+ 可能无法保持显示器分辨率。 在连接的情况下，监视器的 EDID 用于设置系统的分辨率。 断开连接时，固件默认设置为 SD 卡根目录的 config.txt 中的值。 


### <a name="video-performance"></a>视频性能
平台上的视频播放性能未进行优化。  动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。  

### <a name="camera-support"></a>相机支持
对相机外围设备的支持受限。 直接连接到板载相机总线的 PiCam 设备不受支持，因为平台支持 D3D 现代 USB 摄像头在 USB 主控制器上生成要求极度严苛的数据流的能力有限。  即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。  


### <a name="mouse-pointer-disappears-while-debugging"></a>调试时鼠标指针消失
在某些情况下，在使用 Visual Studio 部署或调试应用后，鼠标指针会变得不可见，此时如果使用键盘 (Tab) 更改焦点，鼠标指针就会重新显示 (8038595)。

### <a name="server-applications-with-softap"></a>服务器应用程序与 SoftAP
使用 SoftAP 时，客户端将无法访问 UAP 应用公开的内容。 若要通过 SoftAP 公开 UAP 应用程序，必须通过设备上的控制台进行以下更改 (8111807)：  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

重新启动。

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>在预先构建的 FFU 中出现传感器驱动程序冲突 
在提供的 FFU 中存在传感器驱动程序冲突。 Remote Sensor Framework 可为指南针、磁力计、加速计和陀螺仪安装驱动程序。 从应用程序访问这些项目的 UWP API 会假定只安装了其中一项。 如果你为通过物理方式连接的设备开发驱动程序，则 Microsoft 提供的 FFU 上的远程驱动程序会产生冲突。  

若要解决此问题，可以删除发生冲突的驱动程序，方法是通过 SSH 或 Powershell 连接到设备，然后键入以下命令，使用 devcon.exe 工具删除远程传感器驱动程序： 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

远程传感器驱动程序不影响 OEM 创建的 FFU。 


### <a name="default-administrator-user-name-and-password"></a>默认管理员用户名和密码
默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。 这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。 

### <a name="volume-controls"></a>音量控件
依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。 

### <a name="usb-keyboards"></a>USB 键盘
某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。 使用其他键盘或鼠标。 有关已验证的外围设备列表，可参阅[此处](https://go.microsoft.com/fwlink/?LinkId=619428)的文档。
 
### <a name="screen-orientation"></a>屏幕方向
将方向设置为“纵向”在通用应用中可能不受支持。

### <a name="referencing-adapters-with-alljoyn-templates"></a>使用 AllJoyn 模板引用适配器
尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。  若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a>Windows 10 IoT 核心版上的 WiFi Direct 限制
1. Windows 10 IoT 核心版设备必须是连接设备，因为在其他设备初始化连接时，该设备无法作为广告设备运行。   
2. 必须使用高级配对。  示例应用演示了如何在连接前使用高级配对 API 对设备进行配对。 
3. 并非所有无线适配器都支持 WLAN Direct。 我们已测试并验证“Realtek RTL8188EU 无线 LAN 802.11n USB 2.0 网络适配器”有效，但其他适配器可能不受支持。 

### <a name="non-default-drive-mode-3890679"></a>非默认驱动器模式 (3890679) 
在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。 若要解决此问题，请在应用程序启动时设置一次驱动器模式。 

### <a name="application-already-running-1244550"></a>已处于运行状态的应用程序 (1244550) 
如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。 解决方法：将默认启动应用更改为不希望部署的应用程序。 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a>BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃 (2199869) 
以下代码行可能崩溃： 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

若要防止崩溃，请添加此代码，以便首先执行它：
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a>Azure Active Directory 身份验证支持 (4266261) 
Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。  

### <a name="shell-management-of-application-crashes"></a>应用程序崩溃的 Shell 管理
IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。  如果重新启动的应用程序继续崩溃，shell 将采用 failfast，这一系统关键进程可引起错误检测并重新启动以尝试恢复。  可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。   下面捕获的是崩溃处理和重试逻辑：

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
  Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
  Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
  Dword:"MaxFailureCount". Default is 10 
  DWord:"FallbackExponentNumerator", default is 31. 
  Dword:"FallbackExponentDenominator", default is 20 
  
  
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
When app crash is detected: 
    if time_since_last_crash > failureresetinterval then crashes_seen = 1 
    else ++crashes_seen; 
  
if crashes_seen > MaxFailureCount then __failfast; 
  
else  
  
delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

等待延迟并重新启动应用。

#### <a name="dragonboard-spi-runs-at-48mhz"></a>Dragonboard SPI 以 4.8Mhz 的速度运行
Dragonboard 上的 SPI 将会忽略所请求的速度，并始终以 4.8 Mhz 的速度运行。  

#### <a name="dragonboard-connected-standby"></a>Dragonboard 连接待机 
默认情况下，连接待机在 Qualcomm Dragonboard 上未启用。  若要在 DragonBoard 上启用连接待机，需将以下注册表项设置为“1”。


### <a name="time-synchronization"></a>时间同步
如果时间同步失败或超时，可能是因为时间服务器无法访问或过于遥远，可以通过以下操作来添加额外的或本地的时间服务器。 
 
1. 在设备的命令行（例如 SSH 和 Powershell）。
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. 也可根据需要通过启动脚本或自定义运行时配置包（在创建映像过程中包括进来）将其添加到注册表中。 

### <a name="starting-the-ftp-server"></a>启动 FTP 服务器 
* 若要运行一次 - 请使用 SSH\PS 登录，然后运行以下命令来启动 FTP：  

```
start ftpd.exe 
```

* 若要在每次启动时运行，用户应创建计划程序任务 - 使用 SSH\PS 登录并创建计划程序任务：

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a>更新的分区大小要求 
确保数据分区保持足够的空间来更新功能。  我们建议保留 1GB 的可用空间来进行完整的功能更新。  如果数据分区没有足够的空间，则在安装阶段中更新将会失败。 

### <a name="powershell-log-generation-on-iot-core"></a>IoT 核心版上的 PowerShell 日志生成 
默认情况下，Iot 核心版上的 PowerShell 可能会生成日志文件，从而占用文件系统上的空间。 虽然日志文件大小有限，但可能会占用空间，从而导致磁盘空间不足，此外还可能会导致更新失败。 每个 .evtx 事件日志文件的预定义大小上限为 20 MB。 你可以通过注册表单独限制文件的大小上限。 例如，若要将 security.evtx 的最大上限设置为 10 MB，请输入以下命令： 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a>Schtasks 限制  
Schtasks 不支持使用 /xml 开关。 例如： 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
这会在 IoT 核心版上失败。 运行命令将生成以下错误：错误：找不到指定的过程。 
