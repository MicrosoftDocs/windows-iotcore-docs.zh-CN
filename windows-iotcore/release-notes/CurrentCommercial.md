---
title: 发行说明生成 17763.253
author: zeeshanfurqan
ms.author: zeeshan.furqan
ms.date: 02/14/2019
ms.topic: article
description: 阅读并了解有关新增功能 Windows Insider 生成号 17763.253 中的新增功能
keywords: windows iot、 Windows 预览体验，发行说明
ms.openlocfilehash: dde4089d16ff552e665d341b432f663293ede6b8
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510759"
---
# <a name="release-notes-for-build-17763253"></a>发行说明生成 17763.253
_生成号 17763.253。 2019 年 2 月。_

&copy; 2019 Microsoft Corporation. 保留所有权利。

本文档提供最新进展或其他信息，用于补充 Windows 10 IoT 核心版随附的文档。

感谢下载 Windows 10 IoT 核心版。 Windows 10 IoT 核心版是用于开发嵌入式或专用设备的 Windows 10 版本，可供制造商社区选择使用。 此版本中的包包含的工具和 Minnowboard 最大平台基于 Intel Atom 处理器 Raspberry Pi 2/3 基于 Broadcom 2836/2837 和 Dragonboard 410 c 基于 Qualcomm Snapdragon 400 系列上安装 Windows 10 IoT 核心版所需的内容处理器。


## <a name="privacy-statement"></a>隐私声明

可以查看此版本的 Windows 操作系统的隐私声明[此处](http://go.microsoft.com/fwlink/?LinkId=506737)。

可通过将正向链接粘贴到浏览器窗口中，查看链接的条款。

## <a name="whats-new-in-this-build"></a>什么是此生成中的新增功能： 
* 一般性的 bug 修复 


## <a name="additional-information"></a>其他信息
* 使用我们的龙第板映像的 BSP 版本是 2120.0.0.0。 

## <a name="known-issues-in-this-build"></a>此版本中的已知问题：
* 从 Visual Studio 的 F5 驱动程序部署不适用于 IoT Core。
* 通过 NOOBS 安装的设备不能运行 bcdedit 工具来启用内核调试程序。 这可以通过以下解决方法: * * 在电脑上装载的 SD 卡 * * 找到 EFIESP 驱动器分区带有 diskpart 或磁盘管理 （例如它是"m:"） * * 运行命令"bcdedit /store M:\EFI\Microsoft\boot\bcd /set {default} debug 是"* * 卸载 SD 卡。
* * 你现在应能够像往常一样将调试器连接
* 有时，PSSession 将中断时将命令发送到 IoT 设备。
* RPi3 不将 BT + BTLE 载入 Bluetooth 的搭配使用。
* 无法通过使用 SoftAp Up2 WIFI 连接连接到 internet。
* 亮度控制设置不会保留在 IoT 期间重写。


## <a name="iot-core-general-known-issues-and-work-arounds"></a>常规 IoT 核心版的已知的问题和解决方法

### <a name="for-raspberry-pi"></a>Raspberry pi

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Raspberry Pi 的显示分辨率如果断开连接监视器 
在 Raspberry Pi 如果断开连接监视器不能保持显示分辨率。 监视器 EDID 用于设置系统的解决方法，当其中一个连接。 当断开连接，Raspberry Pi 固件默认为根目录中的 SD 卡 config.txt 中内容。 

#### <a name="raspberry-pi-video-performance"></a>Raspberry Pi 视频性能 
在 Raspberry Pi 的平台上的视频播放性能没有进行优化。  动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。 
 
#### <a name="raspberry-pi-camera-support"></a>Raspberry Pi 相机支持 
照相机外围设备的支持是有限的。 由于平台来支持 D3D 现代 USB USB 主控制器上要求很高的网络摄像头生成数据流中的限制不支持直接连接到载入照相机总线 PiCam 设备。  即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。 

#### <a name="raspberry-pi3-bluetooth-support"></a>Raspberry Pi3 蓝牙支持 
Raspberry Pi3 内置的蓝牙驱动程序仅支持带宽较低的设备。 

#### <a name="serial-port-usage-and-access-on-rpi2"></a>RPi2 上的串行端口用法和访问权限 
Raspberry Pi 2 支持通过 PL011 UART 串行传输通信。  这是内核调试方案中的默认设置。  应用程序或设备驱动程序可以使用 PL011 UART 在 PL011 设备驱动程序使用以下命令关闭调试程序的情况下发送和接收数据：
```
bcedit /set debug off 
```

#### <a name="data-breakpoints-have-been-disabled-on-the-raspberry-pi2"></a>数据断点在 Raspberry Pi2 被禁用
目前没有解决方法。

#### <a name="disabling-the-onboard-adapters-for-raspberry-pi-3"></a>为 Raspberry Pi 3 禁用载入适配器
Raspberry Pi 3 具备板载蓝牙必须禁用以使用不同的硬件保护装置禁用到板载蓝牙、 打开 telnet/ssh 会话并运行： 
```
reg add hklm\system\controlset001\services\BtwSerialH5Bus /v Start /t REG_DWORD /d 4 
```

你可以使用以下命令禁用 WiFi: 
```
reg add hklm\system\controlset001\services\bcmsdh43xx /v Start /t REG_DWORD /d 4 
``` 

### <a name="for-dragon-board"></a>龙板

#### <a name="dragonboard-410c-shutdown"></a>Dragonboard 410c 关机
在 DragonBoard 上，关机命令不会关闭开发板电源。 系统将会重新启动。 请通过断开电源连接来关闭开发板电源。

#### <a name="dragon-board-and-windbg"></a>龙板和 windbg
在使用 windbg 连接到 DragonBoard 时，将禁用 GPIO/I2C/SPI/UART 驱动程序。

#### <a name="dragon-board-headset--microphone-jack"></a>龙板耳机和麦克风插孔
Dragonboard BSP 具有耳机插孔和麦克风插孔的驱动程序，但它在开发板上没有这两种插孔。  

#### <a name="dragonboard-spi-runs-at-48mhz"></a>Dragonboard SPI 运行 4.8 mhz
Dragonboard 上的 SPI 将会忽略所请求的速度，并始终以 4.8 Mhz 的速度运行。  

#### <a name="dragonboard-connected-standby"></a>Dragonboard 连接待机状态 
不，默认情况下，Qualcomm Dragonboard 启用连接待机状态。  若要启用连接待机 DragonBoard 上以下注册表项必须设置为"1":

```
HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1 
```

> [!NOTE]
> 不是所有平台都都支持连接待机状态。  这可能不适用于所有平台。    


### <a name="for-minnowboard"></a>有关 MinnowBoard
#### <a name="minnowboard-max-boot-and-firmware-update"></a>Minnowboard Max 启动和固件更新 
除非固件版本.092，否则将不会启动 MinnowBoard 最大或更高版本。 最小建议的固件的版本是"MinnowBoard 最大 0.92 32-Bit"。 可以从下载固件更新[此处](http://go.microsoft.com/fwlink/?LinkId=708613)。

#### <a name="minnow-board-peripheral-support"></a>Minnow 开发板外设支持
此发布中包含的 Windows 10 IoT 核心版映像支持在 MinnowBoard MAX 板上公开的外设。 随后，Intel&reg;将提供的支持包括 Intel Celeron Baytrail 处理器的完整功能集&trade;处理器 J1900/N2930/N2807 和 Intel Atom&trade;处理器 E38XX。


### <a name="for-all-platforms"></a>为所有平台 

#### <a name="mouse-pointer-disappears-while-debugging"></a>鼠标指针在调试时消失 
在某些情况下，鼠标指针部署或调试应用程序使用 Visual Studio 后不可见，请将鼠标指针应重新出现，如果更改焦点使用键盘 (Tab)。

#### <a name="accessing-public-documents"></a>访问公共文档
这要求应用程序才能访问公用文档目录指定 broadFileSystem 访问的文件访问的基础 Api 已更改。

。XML 文件代码段应如下所示：
```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
  IgnorableNamespaces="uap mp rescap">
--snip--
  <Capabilities>
    <uap:Capability Name="removableStorage" />
    <uap:Capability Name="picturesLibrary" />
    <rescap:Capability Name="broadFileSystemAccess" />
 </Capabilities>

</Package>
```

#### <a name="server-applications-with-softap"></a>SoftAP 服务器应用程序
当使用 SoftAP 客户端将无法再访问由 UAP 应用公开的内容。  
提供通过 SoftAP UAP 应用程序必须从设备上的控制台进行以下更改：  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
```

例如：  
```
checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym
```
重新启动 


#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>在预建 FFUs 传感器驱动程序冲突 
提供 FFUs 中没有传感器驱动程序冲突。 远程传感器框架指南针、 磁力仪、 加速感应器和回转仪安装驱动程序。 用于访问这些应用程序中的 UWP Api 假定安装了只是 1。 如果你正在开发以物理方式附加设备的驱动程序，Microsoft 上的远程驱动程序提供 FFUs 会发生冲突。

解决方案：可以通过连接到设备通过 SSH 或 Powershell 并使用工具 devcon.exe 通过键入删除远程传感器驱动程序删除冲突的驱动程序"devcon.exe 删除 @"ROOT\REMOTESENSORDRIVER *"。 远程传感器驱动程序不会影响创建 FFUs OEM。


#### <a name="default-administrator-user-name-and-password"></a>默认管理员用户名和密码
默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。 这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。

#### <a name="volume-controls"></a>音量控件
依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。 

#### <a name="usb-keyboards"></a>USB 键盘  
某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。 使用其他键盘或鼠标。 可以在找到的已验证的外围设备列表[此处的文档](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/hardwarecompatlist)。


#### <a name="screen-orientation"></a>屏幕方向
在通用应用程序中可能不遵循设置为"纵向"方向。

#### <a name="referencing-adapters-with-alljoyn-templates"></a>使用 AllJoyn 模板引用适配器
尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。  若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。

#### <a name="wifi-direct-limitations-on-iotcore"></a>WiFi 直接 IoTCore 的限制
* IoTCore 设备必须是连接设备，因为在其他设备初始化连接时，该设备无法作为广告设备运行。   
* 必须使用高级配对。  示例应用演示了如何在连接前使用高级配对 API 对设备进行配对。 
* 并非所有无线适配器都支持 WLAN Direct。 我们已测试并验证的"Realtek RTL8188EU 无线 Lan 802.11n USB 2.0 端口的网络适配器"可能不受支持的工作原理，但其他适配器。 


#### <a name="non-default-drive-mode"></a>非默认驱动器模式
在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。 解决方法：在应用程序开端处设置一次驱动器模式。

#### <a name="application-already-running"></a>已在运行的应用程序
如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。 解决方法：将默认启动应用更改为不希望部署的应用程序。 

#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃
以下代码行可能崩溃："BackgroundMediaPlayer.MessageReceivedFromForeground + = OnMessageReceivedFromForeground;"。 若要防止在发生崩溃，添加此代码，以便首先执行"var 播放机 = BackgroundMediaPlayer.Current;" 

#### <a name="azure-active-directory-authentication-support"></a>Azure Active Directory 身份验证支持
Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。  

#### <a name="shell-management-of-application-crashes"></a>命令行程序管理的应用程序崩溃
IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。  如果重新启动的应用程序继续崩溃，shell 将采用 __failfast 这一系统关键进程，可引起错误检测并重新启动以尝试恢复。  可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。   下面捕获的是崩溃处理和重试逻辑：

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
Dword:"MaxFailureCount". Default is 10 
DWord:"FallbackExponentNumerator", default is 31. 
Dword:"FallbackExponentDenominator", default is 20 
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
```

当检测到应用崩溃时： 

```
if time_since_last_crash > failureresetinterval then crashes_seen = 1 

else ++crashes_seen; 

if crashes_seen > MaxFailureCount then __failfast; 

else  

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

等待延迟和重新启动应用程序 


#### <a name="time-synchronization"></a>时间同步  
如果时间同步失败或超时这可能是由于无法访问或远距离时间服务器，可以执行以下要添加其他或本地时间服务器。 

1) 从命令行 （例如在设备上。 SSH, Powershell) w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..." 

2) 也可能会对通过启动脚本注册表这些新增功能或自定义运行时配置包包含必要时在映像创建过程的一部分。 有关更多详细信息，请参阅： 

* [添加到图像文件和注册表设置](https://msdn.microsoft.com/en-us/library/windows/hardware/mt670641(v=vs.85).aspx)


### <a name="starting-the-ftp-server"></a>启动 FTP 服务器 
FTP 服务器无法再运行默认情况下在启动时 

若要运行一次：使用 SSH\PS，然后运行此命令启动 FTP 登录名：  
```
start ftpd.exe 
```

若要运行在每次启动用户应创建计划程序任务：使用 SSH\PS 登录并创建计划程序任务： 
```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD”
```
