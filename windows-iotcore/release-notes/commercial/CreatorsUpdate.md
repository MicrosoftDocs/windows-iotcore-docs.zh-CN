---
title: 创意者更新的内部版本 15063
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 08/28/2017
ms.topic: article
description: 阅读并了解有关新增功能创意者更新中的新增功能。
keywords: windows iot，创意者更新发行说明
ms.openlocfilehash: 73be3f48ce1051d98aa9ebce06dbdc4682fff0fa
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510925"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a>创意者更新的 Windows 10 IoT 核心版发行说明
内部版本 15063 版本号。 2017 年 4 月

Windows 10 IoT Core 支持的嵌入式或专用用途设备的开发，Oem 和构建小型设备的 Windows 解决方案的开发人员的选择。

本文档提供补充其他内容和文档，了解此版本的 Windows 10 IoT 核心版的信息。

此版本中的包包含工具和组件需要 Minnowboard 最大平台基于 Intel Atom 处理器基于 ARM Cortex A7 和 Dragonboard 410 c 基于 Qualcomm Snapdragon 400 系列的 Raspberry Pi 2 上安装 Windows 10 IoT 核心版处理器。   

[其他平台和处理器](../../learn-about-hardware/SoCsAndCustomBoards.md)可以由合作伙伴。

## <a name="privacy-statement"></a>隐私声明

可以查看此版本的 Windows 操作系统的隐私声明[此处](http://go.microsoft.com/fwlink/?LinkId=506737)。

## <a name="whats-new"></a>新增功能
* Windows 10 IoT 核心版公开发行版。 
   * Azure 设备管理支持的 Oem 可以使用 Windows IoT Azure DM 客户端库以将设备管理功能添加到其 Azure IoT 中心连接设备。
   * 其他硅支持
      * 验证对 Intel Joule，Intel Pentium N4200，Intel Celeron N3350 即将发布 Atom x5 E39xx 处理器 (以前称为 Apollo Lake) 上的 Windows 10 IoT Core 的支持和 Raspberry Pi 3 Som。
      * Allwinner 具有启用了对使用 Allwinner A64 SoC.其松树 64 和香蕉 Pi 设备 
   * 发现发现你已使用你的 Microsoft 帐户登录的设备所需的远程设备的任何特殊软件。
   * 有关振动、 亮度、 现代连接的待机、 电源管理、 电池电量和 NFC （不带百 HCE) 的新 UWP Api 和控件。 
   * 新总线和 ARM PCIe USB 函数模式、 Wi-Fi Direct 和 GPIO 中断计数 API 的功能。 
   * 重置/恢复、 在 SOC PWM 和自动 USB 预配新的嵌入功能 
   * 改进了的工具的 VS Code 中，新 Windows Device Portal 和 IoT 仪表板功能，VS 2017 支持。
   * 在 Windows IoT Core-Cortana Cortana 现可在 Windows 10 IoT 核心版上。 向 Cortana 提问。
   * IoT 仪表板的改进的新功能和稳定性 bug 修复
      * Windows Insider Preview 内部版本为 Raspberry Pi 和 Minnowboard 
      * 使用 Windows IoT 远程客户端的设备连接 
      * Ipv6 地址中发现的设备 
      * 设备日志上传提交反馈时
   *  新的高精度 GPIO Api-使用 GPIO pulse 宽度的精确和高效测量的新 Api (Windows.Devices.Gpio.GpioInterruptBuffer) 会中断。  GPIO 提供程序包括新的中断缓冲区接口，以便计时拨号式编码器和距离测量设备等应用程序的高精度中断
   * IoT-设备构建者现在可以完全锁定的设备保护 IoT 设备并获取高级恶意软件防护针对新的和未知恶意软件变体。  这可以通过指定的允许的应用程序和驱动程序在设备上运行时不允许执行未知或不受信任代码签名颁发机构。  这意味着，改进了的安全性，以防止恶意软件和零时差攻击。 
   * 其他更新包括： 
      * 改进的更新支持 
      * Azure 网关 SDK 支持 
      * USB 驱动器基于自动预配 
      * 设备门户重新设计 
      * 64 位映像现在支持最多 16384 MB 的内存 
      * WinRT 振动 Api 
      * 改进了语言支持 
   * 其他  
      * 已更改为默认 BCD 设置以防止设备尝试恢复模式下不存在时启动到恢复模式。 
      * IOT_POWER_SETTINGS 功能现在包括 powercfg.exe。 此功能适用于所有体系结构 (ARM32，x86 和 x64)。 
      * 对进行了更改 Applyupdate.exe 添加 blockrebooton/blockrebootoff 标志 
      * 硬件通知 (hwnclx) 和 USB 函数 (usbfnclx) 的类扩展已添加到默认映像 IoT 核心版

## <a name="known-issues"></a>已知问题

### <a name="raspberry-pi"></a>Raspberry Pi  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Raspberry Pi 的显示分辨率如果断开连接监视器 
在 Raspberry Pi 如果断开连接监视器不能保持显示分辨率。 监视器 EDID 用于设置系统的解决方法，当其中一个连接。  
当断开连接，Raspberry Pi 固件默认为根目录中的 SD 卡 config.txt 中内容。 

#### <a name="raspberry-pi-video-performance"></a>Raspberry Pi 视频性能 
Raspberry Pi 平台上的视频播放性能尚未进行优化。  动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。 

#### <a name="raspberry-pi-camera-support"></a>Raspberry Pi 相机支持 
与 Raspberry Pi 设备相机外围设备的 Windows 10 IoT Core 支持是有限的。 直接连接到载入照相机总线 PiCam 设备是当前不支持，因为它需要将 Raspberry Pi 上当前无效，因为未实现的 DirectX 驱动程序的 GPU 服务。 现代 USB 摄像头可在 USB 主控制器上生成要求极度严苛的数据流。  即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。  

#### <a name="raspberry-pi-3-bluetooth-support"></a>Raspberry Pi 3 蓝牙支持 
Raspberry Pi3 内置的蓝牙驱动程序仅支持带宽较低的设备  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a>串行端口使用情况和 Raspberry Pi 2 上的访问 
Raspberry Pi 2 支持通过 PL011 UART 串行传输通信。  这是内核调试方案中的默认设置。  应用程序或设备驱动程序可以使用 PL011 UART 在 PL011 设备驱动程序使用以下命令关闭调试程序的情况下发送和接收数据：   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a>龙板 

#### <a name="dragonboard-410c-shutdown"></a>Dragonboard 410c 关机 
在 DragonBoard 上，关机命令不会关闭开发板电源。 系统将会重新启动。 请通过断开电源连接来关闭开发板电源。 

#### <a name="dragon-board-headset--microphone-jack"></a>龙板耳机和麦克风插孔  
Dragonboard BSP 具有耳机插孔和麦克风插孔的驱动程序，但它在开发板上没有这两种插孔。  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a>锁的速度运行 Dragonboard SPI  
上 Dragonboard SPI 将忽略所请求的速度，并始终以预配置的速度运行。  

#### <a name="dragonboard-connected-standby"></a>Dragonboard 连接待机状态 
不，默认情况下，Qualcomm Dragonboard 启用连接待机状态。  若要启用连接待机 DragonBoard 上的以下注册表项需要设置为"1" 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
请注意，不是所有平台支持为 CS，因此这不可能在其他平台上工作。    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a>在某些 Qualcomm 平台上可能无法正常振动 API 
建议的解决方法是将添加以下注册表项： 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
确认 / 验证现有的映像上使用 SSH 或 PowerShell 连接并运行以下命令： 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a>MinnowBoard  

#### <a name="minnowboard-max-firmware-update"></a>Minnowboard 最大固件更新 
除非固件版本.092，否则将不会启动 MinnowBoard 最大或更高版本。  
可能存在网络连接故障中 MinnowBoard 最大值 (MBM) 固件版本 0.93。   问题被固定的固件版本 0.94。） 最小建议的固件的版本是"MinnowBoard 最大 0.94 32-bit"。 可以从下载固件更新 [此处](http://go.microsoft.com/fwlink/?LinkId=708613)。
  
 
### <a name="all-platforms"></a>所有平台 

#### <a name="mouse-pointer-disappears-while-debugging"></a>鼠标指针在调试时消失 
在某些情况下，鼠标指针在部署或调试应用程序使用 Visual Studio 后不可见，如果使用键盘 (Tab) 的焦点更改鼠标指针应会重新出现  

#### <a name="server-applications-with-softap"></a>SoftAP 服务器应用程序  
当使用 SoftAP 客户端将无法再访问由 UAP 应用公开的内容。  
提供通过 SoftAP UAP 应用程序必须从设备上的控制台进行以下更改：  
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

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>在预建 FFUs 传感器驱动程序冲突 
提供 FFUs 中没有传感器驱动程序冲突。 远程传感器框架指南针、 磁力仪、 加速感应器和回转仪安装驱动程序。 用于访问这些应用程序中的 UWP Api 假定安装了只是 1。 如果你正在开发以物理方式附加设备的驱动程序，Microsoft 上的远程驱动程序提供 FFUs 会发生冲突。  
解决方案：可以通过连接到设备通过 SSH 或 PowerShell 并使用工具 devcon.exe 通过键入删除远程传感器驱动程序删除冲突的驱动程序"devcon.exe 删除 @"ROOT\REMOTESENSORDRIVER *"。 远程传感器驱动程序不会影响创建 FFUs OEM。 
 
#### <a name="default-administrator-user-name-and-password"></a>默认管理员用户名和密码 
默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。 这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。 
 
#### <a name="volume-controls"></a>音量控件 
依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。 
 
#### <a name="usb-keyboards"></a>USB 键盘  
某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。 使用其他键盘或鼠标。 可以找到已验证的外围设备的列表[此处](../../learn-about-hardware/HardwareCompatList.md)。  
 
#### <a name="screen-orientation"></a>屏幕方向 
设置为"纵向"方向可能不会采用中通用的应用程序 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a>使用 AllJoyn 模板引用适配器 
尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。  若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。 

#### <a name="non-default-drive-mode"></a>非默认驱动器模式  
在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。 解决方法：在应用程序开端处设置一次驱动器模式。 
 
#### <a name="application-already-running"></a>已在运行的应用程序  
如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。 解决方法：将默认启动应用更改为不希望部署的应用程序。 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃  
以下代码行可能会崩溃： `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`。
<br>
若要防止在发生崩溃，添加此代码，以便首先执行 `var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a>Azure Active Directory 身份验证支持  
Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。  
 
#### <a name="shell-management-of-application-crashes"></a>命令行程序管理的应用程序崩溃 
IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。  如果重新启动应用程序继续崩溃，shell 将采用 __failfast – 系统关键进程导致的 bug 检查和恢复以尝试重新启动。  可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。   

下面捕获的是崩溃处理和重试逻辑： 

Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig （或对于 ForegroundAppConfig 讲述的内容） 
* Qword:"FailureResetIntervalMs"– 时间应用的长度必须运行成功重置为 0 出现故障。 -默认值是 0x00000000000493E0 = = 5 分钟。 
* Qword:"BaseRetryDelayMs"-等待时间系数。  默认值为 0xa。
* Dword:"MaxFailureCount"。 默认值为 10。
* DWord:"FallbackExponentNumerator"，默认值为 31。
* Dword:"FallbackExponentDenominator"默认值为 20。
 
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
如果时间同步失败或超时这可能是由于无法访问或远距离时间服务器，可以执行以下要添加其他或本地时间服务器。 
 
* 从命令行 （例如在设备上。 SSH, PowerShell)  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..." 
* 也可能会对通过启动脚本注册表这些新增功能或自定义运行时配置包包含必要时在映像创建过程的一部分。 
有关更多详细信息，请参阅： 
* [将文件和注册表设置添加到映像](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [Windows 10 IoT 核心版映像创建](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a>启动 FTP 服务器 
FTP 服务器无法再运行默认情况下在启动时 
<br>
若要运行一次： 
`Login with SSH\PS`运行以下命令以启动 FTP:  
`start ftpd.exe` 
  
若要在每次启动上运行用户应创建计划程序任务。 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a>版权信息 

© Microsoft. 保留所有权利。 
 
本文档按原样提供。  在此文档中，包括 URL 和其他 Internet 网站引用表达信息和观点可能会更改恕不另行通知。 

此处所述的某些示例仅用于进行说明，是虚构的。  不存在任何实际关联或联系，请勿妄加推断。  

本文档不提供任何 Microsoft 产品中的任何知识产权的任何法律权利。  本文档可用于内部参考目的。 
  
Microsoft 不做任何明示或暗示的担保。  

请参阅 Microsoft 商标商标字产品的列表。 

所有其他商标的所有权属于其各自所有者。  

UPnP ™ 是 UPnP™ Implementers Corporation 的认证标记。 

Bluetooth® 是蓝牙 SIG，inc.的商标美国并授权 Microsoft Corporation。 

Intel 是 Intel Corporation 的注册的商标。 

Itanium 是 Intel Corporation 的注册的商标。
 
此软件的部分基于 MCSA 马赛克，at Urbana-champaign 的伊利诺伊大学的超级计算技术应用程序开发的国家/地区中心，分发与 Spyglass，Inc.的许可协议 

本产品包含由 RSA Data Security，Inc.授权的安全软件 
