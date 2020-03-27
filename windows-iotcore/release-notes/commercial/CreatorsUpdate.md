---
title: Creators Update - 版本 15063
ms.date: 08/28/2017
ms.topic: article
description: 阅读并了解 Creators Update 的新增内容。
keywords: Windows IoT, Creators Update, 发行说明
ms.openlocfilehash: 09157cb634de971bfe57f549c3c87354f814f9e9
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080562"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a>Windows 10 IoT 核心板的 Creators Update 的发行说明
内部版本号 15063。 2017 年 4 月

Windows 10 IoT 核心版支持开发嵌入式设备或专用设备，适合 OEM 和开发人员用来为小型设备构建 Windows 解决方案。

本文档旨在为此版本 Windows 10 IoT 核心版的其他内容和文档提供补充。

此版本中的程序包包含在以下平台和处理器上安装 Windows 10 IoT 核心版所需的工具和组件：基于 Intel Atom 处理器的 Minnowboard Max 平台、基于 ARM Cortex A7 的 Raspberry Pi 2 以及基于 Qualcomm Snapdragon 400 系列处理器的 Dragonboard 410c。   

[其他平台和处理器](../../learn-about-hardware/SoCsAndCustomBoards.md)可从相应合作伙伴处获得。

## <a name="privacy-statement"></a>隐私声明

可在[此处](https://go.microsoft.com/fwlink/?LinkId=506737)查看此 Windows 操作系统版本的隐私声明。

## <a name="whats-new"></a>新增功能
* Windows 10 IoT 核心版公共版本。 
   * 支持 Azure 设备管理 - OEM 可以使用 Windows IoT Azure DM 客户端库向 Azure IoT 中心的连接设备添加设备管理功能。
   * 支持更多处理器
      * 经证实，Windows 10 IoT 核心版支持以下处理器：Intel Joule、Intel Pentium N4200、Intel Celeron N3350、即将发布的 Atom x5-E39xx 处理器（以前称为 Apollo Lake）和 Raspberry Pi 3 SOM。
      * Allwinner 已启用对使用 Allwinner A64 SoC 的 Pine 64 和 Banana Pi 设备的支持。 
   * 发现远程设备 - 无需任何特殊软件即可发现使用 Microsoft 帐户登录的设备。
   * 新增可用于振动、亮度、新式连接待机、电源管理、电池充电和 NFC（不含 HCE）的 UWP API 和控件。 
   * 新增可用于 ARM PCIe、USB 功能模式、Wi-fi Direct 和 GPIO 中断计数 API 的总线和功能。 
   * 新增重置/恢复、On-SOC PWM 和自动 USB 预配等嵌入式功能 
   * 改进了以下工具：VS Code、新的 Windows 设备门户和 IoT 面板功能、VS 2017 支持。
   * Windows IoT 核心版上的 Cortana - Cortana 现已在 Windows 10 IoT 核心版上可用。 向 Cortana 询问一个问题。
   * IoT 仪表板改进 - 新增功能和稳定性错误修复
      * 适用于 Raspberry Pi 和 Minnowboard 的 Windows 预览体验成员预览版 
      * 使用 Windows IoT 远程客户端连接设备 
      * 发现设备中的 Ipv6 地址 
      * 提交反馈时上传设备日志
   *  新增高精度 GPIO API - 新的 API (Windows.Devices.Gpio.GpioInterruptBuffer) 可用于利用 GPIO 中断准确有效地测量脉冲宽度。  GPIO 提供程序包括新的中断缓冲接口，可实现应用程序（如旋转编码器和距离测量设备）的高精度中断计时
   * Device Guard for IoT - 设备构建者现在可以完全锁定 IoT 设备，并获得高级恶意软件防护以防范未知的新恶意软件变体。  实现方法如下：为设备上运行的获得许可的应用程序和驱动程序指定签名机构，同时禁止执行未知或不受信任的代码。  这意味着提高了防范恶意软件和零日攻击的安全性。 
   * 其他更新包括： 
      * 改进的更新支持 
      * Azure 网关 SDK 支持 
      * 基于 USB 驱动器的自动预配 
      * 设备门户重新设计 
      * 64 位映像现在支持高达 16,384MB 的内存 
      * WinRT Vibration API 
      * 改进的语言支持 
   * 杂项  
      * 已对默认的 BCD 设置进行了更改，以防止设备在恢复模式不存在时尝试启动到恢复模式。 
      * IOT_POWER_SETTINGS 功能现在包含 powercfg.exe。 这适用于所有体系结构（ARM32、x86 和 x64）。 
      * 对 Applyupdate 进行了更改，添加了 blockrebooton/blockrebootoff 标志 
      * 已将硬件通知 (hwnclx) 和 USB 函数 (usbfnclx) 的类扩展添加到默认 IoT 核心版映像

## <a name="known-issues"></a>已知问题

### <a name="raspberry-pi"></a>Raspberry Pi  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Raspberry Pi 显示器分辨率（在监视器断开连接的情况下） 
在监视器断开连接的情况下，Raspberry Pi 可能无法保持显示器分辨率。 在连接的情况下，监视器的 EDID 用于设置系统的分辨率。  
断开连接时，Raspberry Pi 固件默认设置为 SD 卡根目录的 config.txt 中的值。 

#### <a name="raspberry-pi-video-performance"></a>Raspberry Pi 视频性能 
Raspberry Pi 平台上的视频播放性能尚未进行优化。  动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。 

#### <a name="raspberry-pi-camera-support"></a>Raspberry Pi 相机支持 
包含 Raspberry Pi 设备的相机外围设备的 Windows 10 IoT 核心版支持受到限制。 直接连接到板载相机总线的 PiCam 设备当前不受支持，因为它要求 GPU 服务，但由于 DirectX 驱动程序尚未实现，因此该服务当前在 Raspberry Pi 上不可用。 现代 USB 摄像头可在 USB 主控制器上生成要求极度严苛的数据流。  即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。  

#### <a name="raspberry-pi-3-bluetooth-support"></a>Raspberry Pi 3 蓝牙支持 
Raspberry Pi3 内置蓝牙驱动程序仅支持低带宽设备  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a>Raspberry Pi 2 上的串行端口用法和访问权限 
Raspberry Pi 2 支持通过 PL011 UART 串行传输通信。  这是内核调试方案中的默认设置。  应用程序或设备驱动程序可以使用 PL011 UART 在 PL011 设备驱动程序使用以下命令关闭调试程序的情况下发送和接收数据：   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a>Dragon Board 

#### <a name="dragonboard-410c-shutdown"></a>Dragonboard 410c 关机 
在 DragonBoard 上，关机命令不会关闭开发板电源。 系统将会重新启动。 请通过断开电源连接来关闭开发板电源。 

#### <a name="dragon-board-headset--microphone-jack"></a>Dragon Board 耳机和麦克风插孔  
Dragonboard BSP 具有耳机插孔和麦克风插孔的驱动程序，但它在开发板上没有这两种插孔。  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a>Dragonboard SPI 以锁定速度运行  
Dragonboard 上的 SPI 将会忽略所请求的速度，并始终以预配置的速度运行。  

#### <a name="dragonboard-connected-standby"></a>Dragonboard 连接待机 
默认情况下，连接待机在 Qualcomm Dragonboard 上未启用。  若要在 DragonBoard 上启用连接待机，需将以下注册表项设置为“1” 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
请注意，并非所有平台都支持 CS，因此这可能不适用于其他平台。    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a>Vibration API 在某些 Qualcomm 平台上可能不起作用 
建议的解决方法是添加以下注册表项： 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
要在现有映像上进行确认/验证，请使用 SSH 或 PowerShell 连接并运行以下命令： 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a>MinnowBoard  

#### <a name="minnowboard-max-firmware-update"></a>Minnowboard Max 固件更新 
除非固件是 0.92 版或更高版本，否则 MinnowBoard Max 不会启动。  
MinnowBoard Max (MBM) 固件版本 0.93 可能存在网络连接故障。   此问题已在固件版本 0.94 中解决。） 推荐的最低固件版本是“MinnowBoard MAX 0.94 32 位”。 固件更新可从 [此处](https://go.microsoft.com/fwlink/?LinkId=708613)下载。
  
 
### <a name="all-platforms"></a>所有平台 

#### <a name="mouse-pointer-disappears-while-debugging"></a>调试时鼠标指针消失 
在某些情况下，在使用 Visual Studio 部署或调试应用后，鼠标指针会变得不可见，此时如果使用键盘 (Tab) 更改焦点，鼠标指针就会重新显示  

#### <a name="server-applications-with-softap"></a>服务器应用程序与 SoftAP  
使用 SoftAP 时，客户端将无法访问 UAP 应用公开的内容。  
若要通过 SoftAP 公开 UAP 应用程序，必须通过设备上的控制台进行以下更改：  
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
在提供的 FFU 中存在传感器驱动程序冲突。 Remote Sensor Framework 可为指南针、磁力计、加速计和陀螺仪安装驱动程序。 从应用程序访问这些项目的 UWP API 会假定只安装了其中 1 项。 如果你为通过物理方式连接的设备开发驱动程序，则 Microsoft 提供的 FFU 上的远程驱动程序会产生冲突。  
分辨率：可以删除发生冲突的驱动程序，方法是：通过 SSH 或 PowerShell 连接到设备，然后键入“devcon.exe remove @”ROOT\REMOTESENSORDRIVER*”，使用 devcon.exe 工具删除远程传感器驱动程序。 远程传感器驱动程序不影响 OEM 创建的 FFU。 
 
#### <a name="default-administrator-user-name-and-password"></a>默认管理员用户名和密码 
默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。 这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。 
 
#### <a name="volume-controls"></a>音量控件 
依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。 
 
#### <a name="usb-keyboards"></a>USB 键盘  
某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。 使用其他键盘或鼠标。 在[此处](../../learn-about-hardware/HardwareCompatList.md)可用找到已验证的外围设备列表。  
 
#### <a name="screen-orientation"></a>屏幕方向 
将方向设置为“纵向”在通用应用中可能不受支持 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a>使用 AllJoyn 模板引用适配器 
尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。  若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。 

#### <a name="non-default-drive-mode"></a>非默认驱动器模式  
在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。 解决方法：在应用程序开端处设置一次驱动器模式。 
 
#### <a name="application-already-running"></a>已处于运行状态的应用程序  
如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。 解决方法：将默认启动应用更改为不希望部署的应用程序。 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃  
以下代码行可能崩溃：`BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`。
<br>
若要防止崩溃，请添加此代码，以便首先执行它 `var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a>Azure Active Directory 身份验证支持  
Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。  
 
#### <a name="shell-management-of-application-crashes"></a>应用程序崩溃的 Shell 管理 
IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。  如果重新启动的应用程序继续崩溃，shell 将采用 __failfast 这一系统关键进程，可引起错误检测并重新启动以尝试恢复。  可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。   

下面捕获的是崩溃处理和重试逻辑： 

Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig（或适用于外设的 ForegroundAppConfig） 
* Qword:"FailureResetIntervalMs"：为了将出现的故障重置为 0，应用需要成功运行的时长。 （默认值为 0x00000000000493E0 == 5 分钟。） 
* Qword:"BaseRetryDelayMs"：等待时间系数。  默认值为 0xa。
* Dword:"MaxFailureCount"。 默认值为 10。
* DWord:"FallbackExponentNumerator"，默认值为 31。
* Dword:"FallbackExponentDenominator"，默认值为 20。
 
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
 
* 在设备的命令行（例如 SSH、Powershell）  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..." 
* 也可根据需要通过启动脚本或自定义运行时配置包（在创建映像过程中包括进来）将其添加到注册表中。 
有关更多详细信息，请参阅： 
* [将文件和注册表设置添加到映像](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [Windows 10 IoT 核心板映像创建](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a>启动 FTP 服务器 
FTP 服务器不再在启动时默认运行 
<br>
若要运行一次： 
`Login with SSH\PS`运行以下命令以启动 FTP：  
`start ftpd.exe`    
若要在每次启动时运行，用户应创建一项计划程序任务。 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a>版权信息 

© Microsoft。 保留所有权利。 
 
本文档按原样提供。  本文档中表达的信息和视图（包括 URL 和其他 Internet 网站引用）如有更改，恕不另行通知。 

此处所述的某些示例仅用于进行说明，是虚构的。  不打算存在或不应推断存在实际关联或联系。  

本文档未提供针对任何 Microsoft 产品的任何知识产权的任何法律权限。  本文档仅供内部参考。 
  
Microsoft 不做出任何明示或暗示担保。  

有关标有商标的产品的列表，请参阅 Microsoft 商标。 

所有其他商标均为各自所有者的财产。  

UPnP ™ 是 UPnP™ Implementers Corporation 的认证标记。 

Bluetooth® 是美国 Bluetooth SIG, Inc. 拥有的商标，并已向 Microsoft Corporation 授予了许可证。 

Intel 是 Intel Corporation 的注册商标。 

Itanium 是 Intel Corporation 的注册商标。
 
本软件的某些部分基于 MCSA Mosaic，并由伊利诺伊大学厄巴纳-香槟分校的国家超级计算应用中心开发，按照与 Spyglass, Inc. 签订的许可协议进行分发。 

本产品包含 RSA Data Security, Inc 授予许可证的安全软件。 
