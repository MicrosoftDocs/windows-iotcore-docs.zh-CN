---
title: 在 Raspberry Pi 3B + 的发行说明
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 05/16/2018
ms.topic: article
description: 阅读并了解有关新增功能的 Raspberry Pi 3B + 内部版本中。
keywords: windows iot、 Windows 预览体验，发行说明，Raspberry Pi 3B +
ms.openlocfilehash: f9a1bf98e6ef53ff7f96d35cb34af9527f1c6de1
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510718"
---
# <a name="release-notes-for-raspberry-pi-3b"></a>在 Raspberry Pi 3B + 的发行说明

&copy; 2018 Microsoft Corporation. 保留所有权利。

> [!NOTE]
> 此版本中的 Raspberry Pi 3B + 是不受支持的 technical preview。 已完成有限的验证和支持。 可找到当前发行[此处](https://www.microsoft.com/en-us/software-download/windowsiot)。 为更好地评估体验和对于任何商业产品，请使用 Raspberry Pi 3B 或其他设备使用受支持的 Intel、 Qualcomm 或 NXP Soc。 解决问题的 Raspberry Pi 3B +，请参阅我们的故障排除指南，[此处](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)。 

## <a name="whats-new-in-this-build"></a>什么是此生成中的新增功能： 
* 一般性的 bug 修复

## <a name="known-issues-in-this-build"></a>此版本中的已知问题：
* 此映像仅适用于 RPi3B +，RPi2 上将不会启动。 
* 从 Visual Studio 的 F5 驱动程序部署不适用于 IoT Core。 
* 载入 WIFI 和蓝牙不适用于 RPI3B +。 
* 上 RPi3B + 禁用了 Ft5406 触摸屏幕驱动程序。 
* 禁用 SD 卡活动 LED。 


### <a name="display-resolution-is-monitor-is-disconnected"></a>显示分辨率是断开连接监视器
Raspberry Pi 3B + 如果断开连接监视器可能维护显示分辨率。 监视器 EDID 用于设置系统的解决方法，当其中一个连接。 当断开连接，固件默认为根目录中的 SD 卡 config.txt 中内容。 


### <a name="video-performance"></a>视频的性能
在平台上的视频播放性能没有进行优化。  动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。  

### <a name="camera-support"></a>照相机支持
照相机外围设备的支持是有限的。 由于平台来支持 D3D 现代 USB USB 主控制器上要求很高的网络摄像头生成数据流中的限制不支持直接连接到载入照相机总线 PiCam 设备。  即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。  


### <a name="mouse-pointer-disappears-while-debugging"></a>鼠标指针在调试时消失
在某些情况下，鼠标指针部署或调试应用程序使用 Visual Studio 后不可见，请将鼠标指针应重新出现，如果使用键盘 （选项卡） (8038595) 的焦点更改。

### <a name="server-applications-with-softap"></a>SoftAP 服务器应用程序
当使用 SoftAP 客户端将无法再访问由 UAP 应用公开的内容。 提供通过 SoftAP UAP 应用程序必须从控制台设备 (8111807) 上进行以下更改：  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

重新启动。

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>在预建 FFUs 传感器驱动程序冲突 
提供 FFUs 中没有传感器驱动程序冲突。 远程传感器框架指南针、 磁力仪、 加速感应器和回转仪安装驱动程序。 用于访问这些应用程序中的 UWP Api 假设只是一个安装。 如果你正在开发以物理方式附加设备的驱动程序，Microsoft 上的远程驱动程序提供 FFUs 会发生冲突。  

若要解决此，可以通过连接到设备通过 SSH 或 Powershell 并使用工具 devcon.exe 通过键入删除远程传感器驱动程序删除冲突的驱动程序： 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

远程传感器驱动程序不会影响创建 FFUs OEM。 


### <a name="default-administrator-user-name-and-password"></a>默认管理员用户名和密码
默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。 这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。 

### <a name="volume-controls"></a>音量控件
依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。 

### <a name="usb-keyboards"></a>USB 键盘
某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。 使用其他键盘或鼠标。 可以在文档中找到的已验证的外围设备列表[此处](http://go.microsoft.com/fwlink/?LinkId=619428)。
 
### <a name="screen-orientation"></a>屏幕方向
在通用应用程序中可能不遵循设置为"纵向"方向。

### <a name="referencing-adapters-with-alljoyn-templates"></a>引用具有 AllJoyn 模板适配器
尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。  若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a>在 Windows 10 IoT Core 上的 WiFi 直接限制
1. Windows 10 IoT 核心版设备必须是连接的设备 – 它不会为广告设备与另一台设备发起连接。   
2. 必须使用高级配对。  示例应用演示了如何在连接前使用高级配对 API 对设备进行配对。 
3. 并非所有无线适配器都支持 WLAN Direct。 我们已测试并验证“Realtek RTL8188EU 无线 LAN 802.11n USB 2.0 网络适配器”有效，但其他适配器可能不受支持。 

### <a name="non-default-drive-mode-3890679"></a>非默认驱动器模式 (3890679) 
在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。 解决此问题，一次在应用程序的开始处设置驱动器模式。 

### <a name="application-already-running-1244550"></a>已处于运行状态的应用程序 (1244550) 
如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。 解决方法：将默认启动应用更改为不希望部署的应用程序。 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a>BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃 (2199869) 
以下代码行可能崩溃： 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

若要防止在发生崩溃，添加以下代码，以便首先执行：
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a>Azure Active Directory 身份验证支持 (4266261) 
Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。  

### <a name="shell-management-of-application-crashes"></a>命令行程序管理的应用程序崩溃
IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。  如果重新启动应用程序继续崩溃，shell 将采用故障快速报警 – 系统关键进程会导致错误检测和恢复以尝试重新启动。  可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。   下面被捕获崩溃处理和重试逻辑：

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

等待延迟，然后重新启动该应用程序。

#### <a name="dragonboard-spi-runs-at-48mhz"></a>Dragonboard SPI 运行 4.8 mhz
Dragonboard 上的 SPI 将会忽略所请求的速度，并始终以 4.8 Mhz 的速度运行。  

#### <a name="dragonboard-connected-standby"></a>Dragonboard 连接待机状态 
不，默认情况下，Qualcomm Dragonboard 启用连接待机状态。  若要启用连接待机 DragonBoard 上需要以下注册表项设置为"1"。


### <a name="time-synchronization"></a>时间同步
如果时间同步失败或超时这可能是由于无法访问或远距离时间服务器，可以执行以下要添加其他或本地时间服务器。 
 
1. 从命令行 （例如在设备上。 SSH，Powershell)。
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. 也可能会对通过启动脚本注册表这些新增功能或自定义运行时配置包包含必要时在映像创建过程的一部分。 

### <a name="starting-the-ftp-server"></a>启动 FTP 服务器 
* 若要运行一次-使用 SSH\PS 登录并运行以下命令以启动 FTP:  

```
start ftpd.exe 
```

* 若要在每次启动上运行，用户应创建计划程序任务-使用 SSH\PS 登录并创建计划程序任务：

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a>更新的分区大小要求 
请确保数据分区将保持足够的空间用于更新功能。  我们建议 1 gb 的可用空间的完整更新功能。  如果数据分区不具有足够的空间，更新将在安装阶段中失败。 

### <a name="powershell-log-generation-on-iot-core"></a>在 IoT Core 上的 PowerShell 日志生成 
在 Iot Core 上的 PowerShell 可能会占用文件系统上的空间的默认情况下生成日志文件。 但日志文件大小受到的限制可能占用空间可能会导致磁盘空间不足的空间这种，此外，可能会导致更新失败情况。 扩展名为.evtx 事件日志文件具有预定义的最大大小的 20 MB。 您可以单独限制文件通过注册表有不同的最大大小。 例如，若要使 security.evtx 保持 10 MB 最大大小： 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a>Schtasks 限制  
Schtasks 不支持使用 /xml 开关。 例如： 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
这将在 IoT Core 上失败。 运行该命令将生成错误：错误：找不到指定的过程。 
