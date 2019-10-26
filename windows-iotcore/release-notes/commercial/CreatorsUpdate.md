---
title: 创意者更新-生成15063
ms.date: 08/28/2017
ms.topic: article
description: 阅读并了解创意者更新中的新增功能。
keywords: windows iot，创意者更新，发行说明
ms.openlocfilehash: f62bb14e99c8509374c776172cfcb495b62325da
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918719"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a>Windows 10 IoT Core 的创意者更新发行说明
内部版本号15063。 2017 年 4 月

Windows 10 IoT Core 允许开发嵌入或专用设备，并且是针对小型设备构建 Windows 解决方案的 Oem 和开发人员的选择。

本文档提供的信息补充了此版本的 Windows 10 IoT Core 的其他内容和文档。

此版本中的包包含在基于 Intel Atom 多少的 Minnowboard 最大平台上安装 Windows 10 IoT Core 所需的工具和组件、基于 ARM Cortex-a9 A7 的 Raspberry Pi 2，以及基于 Qualcomm Dragonboard 400 系列的 410C Snapdragon款.   

合作伙伴可以使用[其他平台和处理器](../../learn-about-hardware/SoCsAndCustomBoards.md)。

## <a name="privacy-statement"></a>隐私声明

可在[此处](http://go.microsoft.com/fwlink/?LinkId=506737)查看此 Windows 操作系统版本的隐私声明。

## <a name="whats-new"></a>新增功能
* Windows 10 IoT Core 公有版。 
   * Azure 设备管理支持-Oem 可以使用 Windows IoT Azure DM 客户端库向其 Azure IoT 中心连接的设备添加设备管理功能。
   * 额外硅支持
      * 验证了对 Intel Joule、Intel Pentium N4200、Intel 赛扬 N3350、即将发布的 Atom x5-E39xx 处理器（以前称为 Apollo Lake）和 Raspberry Pi 3 SOMs 的 Windows 10 IoT Core 的支持。
      * Allwinner 已使用 Allwinner A64 SoC 为其松树64和香蕉 Pi 设备启用了支持。 
   * 发现你的远程设备-发现你的设备已登录到你的 Microsoft 帐户无需任何特殊软件。
   * 新的 UWP Api 和控件，适用于振动、亮度、新式连接待机、电源管理、电池电量和 NFC （w/o HCE）。 
   * ARM PCIe、USB 功能模式、Wi-fi Direct 和 GPIO 中断计数 API 的新总线和功能。 
   * 重置/恢复上的新嵌入功能，On SOC PWM 和自动 USB 预配 
   * 改进的工具-VS Code、新的 Windows 设备门户和 IoT 面板功能，VS 2017 支持。
   * Windows IoT Core 上的 cortana-Cortana 现在在 Windows 10 IoT Core 上可用。 向 Cortana 询问一个问题。
   * IoT 面板改进-新增功能和稳定性错误修复
      * 适用于 Raspberry Pi 和 Minnowboard 的 Windows 预览体验版预览版 
      * 使用 Windows IoT 远程客户端连接设备 
      * 发现设备中的 Ipv6 地址 
      * 提交反馈时上载设备日志
   *  新的高精度 GPIO Api-新 Api （GpioInterruptBuffer），用于使用 GPIO 中断准确有效地测量脉冲宽度。  GPIO 提供程序包括新的中断缓冲接口，以允许应用程序（如旋转编码器和距离测量设备）的高精度中断计时
   * Device Guard for IoT-设备构建者现在可以完全锁定 IoT 设备，并针对新的未知恶意软件变种获取高级恶意软件防护。  为此，可以为在设备上运行的允许的应用程序和驱动程序指定签名颁发机构，同时禁止执行未知或不受信任的代码。  这意味着提高了对恶意软件和零天攻击的安全性。 
   * 其他更新包括： 
      * 改进了更新支持 
      * Azure 网关 SDK 支持 
      * 基于 USB 驱动器的自动预配 
      * 设备门户重新设计 
      * 64位映像现在最多支持 16384 MB 的内存 
      * WinRT 振动 Api 
      * 改进的语言支持 
   * 其他  
      * 已对默认的 BCD 设置进行了更改，以防止设备在恢复模式不存在时尝试启动到恢复模式。 
      * IOT_POWER_SETTINGS 功能现在包含 powercfg。 这适用于所有体系结构（ARM32、x86 和 x64）。 
      * 对 Applyupdate 进行了更改以添加 blockrebooton/blockrebootoff 标志 
      * 已将硬件通知（hwnclx）和 USB 函数（usbfnclx）的类扩展添加到默认 IoT Core 映像

## <a name="known-issues"></a>已知问题

### <a name="raspberry-pi"></a>Raspberry Pi  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Raspberry Pi 显示器分辨率（在监视器断开连接的情况下） 
在监视器断开连接的情况下，Raspberry Pi 可能无法保持显示器分辨率。 监视器的 EDID 用于在连接到系统时设置系统的分辨率。  
断开连接时，Raspberry Pi 固件默认设置为 SD 卡根目录的 config.txt 中的值。 

#### <a name="raspberry-pi-video-performance"></a>Raspberry Pi 视频性能 
Raspberry Pi 平台上的视频播放性能尚未进行优化。  动画用户元素（包括基于 XAML 的下拉菜单）可能会小于最佳性能。 

#### <a name="raspberry-pi-camera-support"></a>Raspberry Pi 相机支持 
Windows 10 IoT 核心支持，适用于 Raspberry Pi 设备的相机外设设备受到限制。 当前不支持直接连接到板载相机总线的 PiCam 设备，因为它需要在 Raspberry Pi 上当前不可用的 GPU 服务，因为未实现 DirectX 驱动程序。 现代 USB 摄像头可在 USB 主控制器上生成要求极度严苛的数据流。  即使与低分辨率设置网络摄像机一起使用，也需要额外的 USB 微调和专用控制逻辑。  

#### <a name="raspberry-pi-3-bluetooth-support"></a>Raspberry Pi 3 蓝牙支持 
Raspberry Pi3 内置蓝牙驱动程序仅支持低带宽设备  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a>Raspberry Pi 2 上的串行端口使用和访问 
Raspberry Pi 2 支持通过 PL011 UART 串行传输通信。  默认情况下，在内核调试方案中设置此值。  应用程序或设备驱动程序可以使用 PL011 UART 来发送和接收数据，PL011 设备驱动程序使用以下命令关闭调试器：   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a>龙板 

#### <a name="dragonboard-410c-shutdown"></a>Dragonboard 410c 关机 
在 DragonBoard 上，关机命令不会关闭开发板电源。 系统将会重新启动。 请通过断开电源连接来关闭开发板电源。 

#### <a name="dragon-board-headset--microphone-jack"></a>Dragon Board 耳机和麦克风插孔  
Dragonboard BSP 具有耳机插孔和麦克风插孔的驱动程序，但它在开发板上没有这两种插孔。  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a>Dragonboard SPI 以 lock 速度运行  
Dragonboard 上的 SPI 将忽略请求的速度，并始终以预配置的速度运行。  

#### <a name="dragonboard-connected-standby"></a>Dragonboard 连接待机 
默认情况下，连接待机在 Qualcomm Dragonboard 上未启用。  若要在 DragonBoard 上启用连接备用，需要将以下注册表项设置为 "1" 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
请注意，并非所有平台都支持 CS，因此这可能在其他平台上不起作用。    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a>振动 API 在某些 Qualcomm 平台上可能不起作用 
建议的解决方法是添加以下注册表项： 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
对于使用 SSH 或 PowerShell 进行的现有映像连接确认/验证，请运行以下命令： 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a>MinnowBoard  

#### <a name="minnowboard-max-firmware-update"></a>Minnowboard 最大固件更新 
除非固件为092或更高版本，否则不会启动 MinnowBoard Max。  
MinnowBoard Max （MBM）固件版本0.93 可能存在网络连接故障。   此问题已在固件版本0.94 中解决。）  最小建议固件版本为 "MinnowBoard MAX 0.94 32-bit"。 可从 [此处](http://go.microsoft.com/fwlink/?LinkId=708613)下载固件更新。
  
 
### <a name="all-platforms"></a>所有平台 

#### <a name="mouse-pointer-disappears-while-debugging"></a>调试时鼠标指针消失 
在某些情况下，在使用 Visual Studio 部署或调试应用程序后不会显示鼠标指针，如果使用键盘（选项卡）更改焦点，则会重新显示鼠标指针  

#### <a name="server-applications-with-softap"></a>服务器应用程序与 SoftAP  
使用 SoftAP 客户端时，客户端将无法访问 UAP 应用公开的内容。  
若要通过 SoftAP 公开 UAP 应用程序，必须从设备上的控制台进行以下更改：  
<br>
`reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 `
<br>
`checknetisolation loopbackexempt -a -n=<AppID for SoftAP App>`
<br>
`checknetisolation loopbackexempt -a -n=<AppID for Additional App> `
<br>
`For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym`
<br>
`Reboot`

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>在预先构建的 FFU 中出现传感器驱动程序冲突 
在提供的 FFU 中存在传感器驱动程序冲突。 Remote Sensor Framework 可为指南针、磁力计、加速计和陀螺仪安装驱动程序。 从应用程序访问这些项目的 UWP API 会假定只安装了其中 1 项。 如果要开发用于物理连接的设备的驱动程序，Microsoft 提供的 FFUs 上的远程驱动程序将发生冲突。  
解决方法：可以通过 SSH 或 PowerShell 连接到设备，并使用工具 devcon 删除远程传感器驱动程序，只需要键入 "ROOT\REMOTESENSORDRIVER *" 即可删除该驱动程序。 远程传感器驱动程序不影响 OEM 创建的 FFU。 
 
#### <a name="default-administrator-user-name-and-password"></a>默认管理员用户名和密码 
默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。 这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。 
 
#### <a name="volume-controls"></a>音量控件 
依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。 
 
#### <a name="usb-keyboards"></a>USB 键盘  
某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。 使用其他键盘或鼠标。 可在[此处](../../learn-about-hardware/HardwareCompatList.md)找到已验证的外围设备的列表。  
 
#### <a name="screen-orientation"></a>屏幕方向 
在通用应用中将方向设置为 "纵向" 可能不起作用 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a>使用 AllJoyn 模板引用适配器 
尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。  若要解决这些错误，请更改 Visual Studio 的目标平台，使其与当前 SDK 版本匹配，然后重新加载项目。 

#### <a name="non-default-drive-mode"></a>非默认驱动器模式  
在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。 解决方法： 在应用程序开端处设置一次驱动器模式。 
 
#### <a name="application-already-running"></a>已处于运行状态的应用程序  
如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。 解决方法： 将默认启动应用更改为不希望部署的应用程序。 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃  
以下代码行可能会崩溃： `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`。
<br>
若要防止发生崩溃，请添加以下代码，使其先执行 `var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a>Azure Active Directory 身份验证支持  
Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。  
 
#### <a name="shell-management-of-application-crashes"></a>应用程序崩溃的 Shell 管理 
IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。  如果重新启动的应用程序仍然崩溃，shell 将使用 __failfast –导致错误检查的系统关键过程，并在尝试恢复时重新启动。  可比较的逻辑和处理用于头配置中的后台任务和前景应用程序。   

下面捕获的是崩溃处理和重试逻辑： 

Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig （或 ForegroundAppConfig） 
* Qword： "FailureResetIntervalMs" –应用必须成功运行的时间长度，才能将出现的故障重置为0。 –默认值为 0x00000000000493E0 = = 5 分钟。 
* Qword： "BaseRetryDelayMs"--等待时间系数。  默认值为0xa。
* Dword:"MaxFailureCount"。 默认值为10。
* DWord:"FallbackExponentNumerator"，默认值为 31。
* Dword： "FallbackExponentDenominator"，默认值为20。
 
```C#
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator;
// default is 1.55
When app crash is detected:
    if time_since_last_crash > failureresetinterval then crashes_seen = 1
    else ++crashes_seen;

if crashes_seen > MaxFailureCount then __failfast;

else

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent))
// wait for delay and relaunch app
```
 
#### <a name="time-synchronization"></a>时间同步  
如果时间同步失败或超时，可能是因为时间服务器无法访问或过于遥远，可以通过以下操作来添加额外的或本地的时间服务器。 
 
* 在设备的命令行（例如 SSH，PowerShell）  w32tm/config/syncfromflags： manual/manualpeerlist： "1.pool.ntp.org 2. 其他 ..." 
* 如果需要，还可以通过启动脚本或作为映像创建过程的一部分包含的自定义运行时配置包，将这些添加到注册表中。 
有关更多详细信息，请参阅： 
* [向映像添加文件和注册表设置](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [Windows 10 IoT Core 映像创建](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a>启动 FTP 服务器 
默认情况下，FTP 服务器在启动时不再运行 
<br>
若要运行一次： 
`Login with SSH\PS` 运行以下命令以启动 FTP：  
`start ftpd.exe`    
若要在每个启动用户上运行，应创建计划程序任务。 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a>版权信息 

© Microsoft。 保留所有权利。 
 
本文档按原样提供。  本文档中表达的信息和视图（包括 URL 和其他 Internet 网站引用）可能会更改，恕不另行通知。 

此处所述的某些示例仅用于进行说明，是虚构的。  不打算或不应推断真正的关联或连接。  

本文档不提供任何 Microsoft 产品中任何知识产权的任何法律权利。  本文档可用于内部、参考目的。 
  
Microsoft 不作任何明示或默示的保证。  

有关商标字产品的列表，请参阅 Microsoft 商标。 

所有其他商标的所有权属于其各自所有者。  

UPnP ™ 是 UPnP™ Implementers Corporation 的认证标记。 

蓝牙®是蓝牙 SIG、Inc. 的商标，并授权给 Microsoft Corporation。 

Intel 是 Intel Corporation 的注册商标。 

Itanium 是 Intel Corporation 的注册商标。
 
本软件的某些部分基于 MCSA 马赛克，由美国大学伊利诺斯州大学的超级计算中心应用程序开发，由美国应用程序开发，并按与 Urbana-champaign，Inc. 的许可协议一起分发。 

此产品包含的安全软件是从 RSA Data Security，Inc. 授权的。 
