---
title: Raspberry Pi 3B + 的发行说明
ms.date: 05/16/2018
ms.topic: article
description: 阅读并了解 Raspberry Pi 3B + 内部版本中的内容。
keywords: windows iot, Windows 预览体验成员, 发行说明, Raspberry Pi 3B +
ms.openlocfilehash: d321676758f7ff438540720098e6a6ecb1ba457f
ms.sourcegitcommit: 34928850d3b1b2fe22a92ebd1d75c01b3d4bf0aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/24/2020
ms.locfileid: "75721012"
---
# <a name="release-notes-for-raspberry-pi-3b"></a><span data-ttu-id="0ffc0-104">Raspberry Pi 3B + 的发行说明</span><span class="sxs-lookup"><span data-stu-id="0ffc0-104">Release Notes for Raspberry Pi 3B+</span></span>

<span data-ttu-id="0ffc0-105">&copy; 2018 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-105">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="0ffc0-106">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-106">All rights reserved.</span></span>

> [!NOTE]
> <span data-ttu-id="0ffc0-107">Raspberry Pi 3B+ 的此版本是不受支持的技术预览版。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-107">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="0ffc0-108">已完成有限的验证和启用。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-108">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="0ffc0-109">在[此处](https://www.microsoft.com/en-us/software-download/windowsiot)可找到当前版本。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-109">The current release can be found [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="0ffc0-110">若要获得更好的评估体验，或者要将产品商用化，请使用 Raspberry Pi 3B 或者其他带有受支持的 Intel、Qualcomm 或 NXP SoC 的设备。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-110">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="0ffc0-111">若要排查 Raspberry Pi 3B+ 的问题，请参阅[此处](https://docs.microsoft.com/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)的故障排除指南。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-111">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

## <a name="whats-new-in-this-build"></a><span data-ttu-id="0ffc0-112">此内部版本的新增功能：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-112">What's new in this build:</span></span> 
* <span data-ttu-id="0ffc0-113">常规 Bug 修复</span><span class="sxs-lookup"><span data-stu-id="0ffc0-113">General bug fixes</span></span>

## <a name="known-issues-in-this-build"></a><span data-ttu-id="0ffc0-114">此版本中的已知问题：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-114">Known issues in this build:</span></span>
* <span data-ttu-id="0ffc0-115">此映像仅适用于 RPi3B +，并且不会在 RPi2 上启动。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-115">This image is only meant for RPi3B+ and will not boot on RPi2.</span></span> 
* <span data-ttu-id="0ffc0-116">不能在 IoT 核心版上通过 Visual Studio 进行 F5 驱动程序部署。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-116">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span> 
* <span data-ttu-id="0ffc0-117">板载 WIFI 和蓝牙不适用于 RPI3B +。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-117">Onboard WIFI and Bluetooth do not work on RPI3B+.</span></span> 
* <span data-ttu-id="0ffc0-118">Ft5406 触摸屏驱动程序在 RPi3B + 上禁用。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-118">Ft5406 touch screen driver is disabled on RPi3B+.</span></span> 
* <span data-ttu-id="0ffc0-119">SD 卡活动 LED 禁用。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-119">SD card activity LED is disabled.</span></span> 


### <a name="display-resolution-is-monitor-is-disconnected"></a><span data-ttu-id="0ffc0-120">显示器分辨率（在显示器断开连接的情况下）</span><span class="sxs-lookup"><span data-stu-id="0ffc0-120">Display resolution is monitor is disconnected</span></span>
<span data-ttu-id="0ffc0-121">在监视器断开连接的情况下，Raspberry Pi 3B+ 可能无法保持显示器分辨率。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-121">The Raspberry Pi 3B+ may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="0ffc0-122">在连接的情况下，监视器的 EDID 用于设置系统的分辨率。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-122">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="0ffc0-123">断开连接时，固件默认设置为 SD 卡根目录的 config.txt 中的值。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-123">When disconnected, the firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 


### <a name="video-performance"></a><span data-ttu-id="0ffc0-124">视频性能</span><span class="sxs-lookup"><span data-stu-id="0ffc0-124">Video performance</span></span>
<span data-ttu-id="0ffc0-125">平台上的视频播放性能未进行优化。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-125">Video playback performance on the platform is not optimized.</span></span>  <span data-ttu-id="0ffc0-126">动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-126">Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span>  

### <a name="camera-support"></a><span data-ttu-id="0ffc0-127">相机支持</span><span class="sxs-lookup"><span data-stu-id="0ffc0-127">Camera support</span></span>
<span data-ttu-id="0ffc0-128">对相机外围设备的支持受限。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-128">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="0ffc0-129">直接连接到板载相机总线的 PiCam 设备不受支持，因为平台支持 D3D 现代 USB 摄像头在 USB 主控制器上生成要求极度严苛的数据流的能力有限。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-129">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span>  <span data-ttu-id="0ffc0-130">即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-130">Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  


### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="0ffc0-131">调试时鼠标指针消失</span><span class="sxs-lookup"><span data-stu-id="0ffc0-131">Mouse pointer disappears while debugging</span></span>
<span data-ttu-id="0ffc0-132">在某些情况下，在使用 Visual Studio 部署或调试应用后，鼠标指针会变得不可见，此时如果使用键盘 (Tab) 更改焦点，鼠标指针就会重新显示 (8038595)。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-132">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab) (8038595).</span></span>

### <a name="server-applications-with-softap"></a><span data-ttu-id="0ffc0-133">服务器应用程序与 SoftAP</span><span class="sxs-lookup"><span data-stu-id="0ffc0-133">Server applications with SoftAP</span></span>
<span data-ttu-id="0ffc0-134">使用 SoftAP 时，客户端将无法访问 UAP 应用公开的内容。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-134">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span> <span data-ttu-id="0ffc0-135">若要通过 SoftAP 公开 UAP 应用程序，必须通过设备上的控制台进行以下更改 (8111807)：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-135">To expose UAP applications via SoftAP the following changes must be made from the console on the device (8111807):</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

<span data-ttu-id="0ffc0-136">重新启动。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-136">Reboot.</span></span>

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="0ffc0-137">在预先构建的 FFU 中出现传感器驱动程序冲突</span><span class="sxs-lookup"><span data-stu-id="0ffc0-137">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="0ffc0-138">在提供的 FFU 中存在传感器驱动程序冲突。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-138">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="0ffc0-139">Remote Sensor Framework 可为指南针、磁力计、加速计和陀螺仪安装驱动程序。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-139">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="0ffc0-140">从应用程序访问这些项目的 UWP API 会假定只安装了其中一项。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-140">The UWP APIs for accessing these from an application assume just one is installed.</span></span> <span data-ttu-id="0ffc0-141">如果你为通过物理方式连接的设备开发驱动程序，则 Microsoft 提供的 FFU 上的远程驱动程序会产生冲突。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-141">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>  

<span data-ttu-id="0ffc0-142">若要解决此问题，可以删除发生冲突的驱动程序，方法是通过 SSH 或 Powershell 连接到设备，然后键入以下命令，使用 devcon.exe 工具删除远程传感器驱动程序：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-142">To solve for this, the conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing:</span></span> 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

<span data-ttu-id="0ffc0-143">远程传感器驱动程序不影响 OEM 创建的 FFU。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-143">The remote sensor driver does not affect OEM created FFUs.</span></span> 


### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="0ffc0-144">默认管理员用户名和密码</span><span class="sxs-lookup"><span data-stu-id="0ffc0-144">Default administrator user name and password</span></span>
<span data-ttu-id="0ffc0-145">默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-145">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="0ffc0-146">这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-146">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 

### <a name="volume-controls"></a><span data-ttu-id="0ffc0-147">音量控件</span><span class="sxs-lookup"><span data-stu-id="0ffc0-147">Volume controls</span></span>
<span data-ttu-id="0ffc0-148">依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-148">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

### <a name="usb-keyboards"></a><span data-ttu-id="0ffc0-149">USB 键盘</span><span class="sxs-lookup"><span data-stu-id="0ffc0-149">USB keyboards</span></span>
<span data-ttu-id="0ffc0-150">某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-150">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="0ffc0-151">使用其他键盘或鼠标。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-151">Use a different keyboard or mouse.</span></span> <span data-ttu-id="0ffc0-152">有关已验证的外围设备列表，可参阅[此处](https://go.microsoft.com/fwlink/?LinkId=619428)的文档。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-152">A list of validated peripheral devices can be found in the documentation [here](https://go.microsoft.com/fwlink/?LinkId=619428).</span></span>
 
### <a name="screen-orientation"></a><span data-ttu-id="0ffc0-153">屏幕方向</span><span class="sxs-lookup"><span data-stu-id="0ffc0-153">Screen orientation</span></span>
<span data-ttu-id="0ffc0-154">将方向设置为“纵向”在通用应用中可能不受支持。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-154">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="0ffc0-155">使用 AllJoyn 模板引用适配器</span><span class="sxs-lookup"><span data-stu-id="0ffc0-155">Referencing adapters with AllJoyn templates</span></span>
<span data-ttu-id="0ffc0-156">尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-156">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="0ffc0-157">若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-157">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a><span data-ttu-id="0ffc0-158">Windows 10 IoT 核心版上的 WiFi Direct 限制</span><span class="sxs-lookup"><span data-stu-id="0ffc0-158">WiFi Direct limitations on Windows 10 IoT Core</span></span>
1. <span data-ttu-id="0ffc0-159">Windows 10 IoT 核心版设备必须是连接设备，因为在其他设备初始化连接时，该设备无法作为广告设备运行。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-159">The Windows 10 IoT Core device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
2. <span data-ttu-id="0ffc0-160">必须使用高级配对。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-160">Advanced pairing must be used.</span></span>  <span data-ttu-id="0ffc0-161">示例应用演示了如何在连接前使用高级配对 API 对设备进行配对。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-161">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
3. <span data-ttu-id="0ffc0-162">并非所有无线适配器都支持 WLAN Direct。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-162">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="0ffc0-163">我们已测试并验证“Realtek RTL8188EU 无线 LAN 802.11n USB 2.0 网络适配器”有效，但其他适配器可能不受支持。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-163">We have tested and validated that the "Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter" works, but other adapters may not be supported.</span></span> 

### <a name="non-default-drive-mode-3890679"></a><span data-ttu-id="0ffc0-164">非默认驱动器模式 (3890679)</span><span class="sxs-lookup"><span data-stu-id="0ffc0-164">Non-default drive mode (3890679)</span></span> 
<span data-ttu-id="0ffc0-165">在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-165">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="0ffc0-166">若要解决此问题，请在应用程序启动时设置一次驱动器模式。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-166">To workaround this issue, set drive mode once at the beginning of the application.</span></span> 

### <a name="application-already-running-1244550"></a><span data-ttu-id="0ffc0-167">已处于运行状态的应用程序 (1244550)</span><span class="sxs-lookup"><span data-stu-id="0ffc0-167">Application already running (1244550)</span></span> 
<span data-ttu-id="0ffc0-168">如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-168">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="0ffc0-169">解决方法：将默认启动应用更改为不希望部署的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-169">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a><span data-ttu-id="0ffc0-170">BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃 (2199869)</span><span class="sxs-lookup"><span data-stu-id="0ffc0-170">BackgroundMediaPlayer.MessageReceivedFromForeground may crash (2199869)</span></span> 
<span data-ttu-id="0ffc0-171">以下代码行可能崩溃：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-171">The following line of code may crash:</span></span> 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

<span data-ttu-id="0ffc0-172">若要防止崩溃，请添加此代码，以便首先执行它：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-172">To prevent the crash, add this code so that it is executed first:</span></span>
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a><span data-ttu-id="0ffc0-173">Azure Active Directory 身份验证支持 (4266261)</span><span class="sxs-lookup"><span data-stu-id="0ffc0-173">Azure Active Directory Authentication Support (4266261)</span></span> 
<span data-ttu-id="0ffc0-174">Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-174">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="0ffc0-175">应用程序崩溃的 Shell 管理</span><span class="sxs-lookup"><span data-stu-id="0ffc0-175">Shell Management of Application Crashes</span></span>
<span data-ttu-id="0ffc0-176">IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-176">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="0ffc0-177">如果重新启动的应用程序继续崩溃，shell 将采用 failfast，这一系统关键进程可引起错误检测并重新启动以尝试恢复。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-177">If the restarted applications continue to crash, the shell will employ a failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="0ffc0-178">可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-178">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="0ffc0-179">下面捕获的是崩溃处理和重试逻辑：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-179">Crash handling and retry logic is captured below:</span></span>

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

<span data-ttu-id="0ffc0-180">等待延迟并重新启动应用。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-180">Wait for the delay and relaunch the app.</span></span>

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="0ffc0-181">Dragonboard SPI 以 4.8Mhz 的速度运行</span><span class="sxs-lookup"><span data-stu-id="0ffc0-181">Dragonboard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="0ffc0-182">Dragonboard 上的 SPI 将会忽略所请求的速度，并始终以 4.8 Mhz 的速度运行。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-182">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="0ffc0-183">Dragonboard 连接待机</span><span class="sxs-lookup"><span data-stu-id="0ffc0-183">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="0ffc0-184">默认情况下，连接待机在 Qualcomm Dragonboard 上未启用。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-184">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="0ffc0-185">若要在 DragonBoard 上启用连接待机，需将以下注册表项设置为“1”。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-185">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”.</span></span>


### <a name="time-synchronization"></a><span data-ttu-id="0ffc0-186">时间同步</span><span class="sxs-lookup"><span data-stu-id="0ffc0-186">Time synchronization</span></span>
<span data-ttu-id="0ffc0-187">如果时间同步失败或超时，可能是因为时间服务器无法访问或过于遥远，可以通过以下操作来添加额外的或本地的时间服务器。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-187">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
1. <span data-ttu-id="0ffc0-188">在设备的命令行（例如</span><span class="sxs-lookup"><span data-stu-id="0ffc0-188">From a command line on the device (eg.</span></span> <span data-ttu-id="0ffc0-189">SSH 和 Powershell）。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-189">SSH, Powershell).</span></span>
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. <span data-ttu-id="0ffc0-190">也可根据需要通过启动脚本或自定义运行时配置包（在创建映像过程中包括进来）将其添加到注册表中。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-190">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> 

### <a name="starting-the-ftp-server"></a><span data-ttu-id="0ffc0-191">启动 FTP 服务器</span><span class="sxs-lookup"><span data-stu-id="0ffc0-191">Starting the FTP Server</span></span> 
* <span data-ttu-id="0ffc0-192">若要运行一次 - 请使用 SSH\PS 登录，然后运行以下命令来启动 FTP：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-192">To run once - Login with SSH\PS and run this command to start FTP:</span></span>  

```
start ftpd.exe 
```

* <span data-ttu-id="0ffc0-193">若要在每次启动时运行，用户应创建计划程序任务 - 使用 SSH\PS 登录并创建计划程序任务：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-193">To run on every boot, users should create a scheduler task - Login with SSH\PS and create a scheduler task:</span></span>

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a><span data-ttu-id="0ffc0-194">更新的分区大小要求</span><span class="sxs-lookup"><span data-stu-id="0ffc0-194">Partition size requirements for Update</span></span> 
<span data-ttu-id="0ffc0-195">确保数据分区保持足够的空间来更新功能。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-195">Ensure data partition maintains sufficient space for update functionality.</span></span><span data-ttu-id="0ffc0-196">  我们建议保留 1GB 的可用空间来进行完整的功能更新。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-196">  We recommend 1GB free for full update functionality.</span></span> <span data-ttu-id="0ffc0-197"> 如果数据分区没有足够的空间，则在安装阶段中更新将会失败。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-197"> If Data partition does not have enough space, updates will fail in the installation phase.</span></span> 

### <a name="powershell-log-generation-on-iot-core"></a><span data-ttu-id="0ffc0-198">IoT 核心版上的 PowerShell 日志生成</span><span class="sxs-lookup"><span data-stu-id="0ffc0-198">PowerShell log generation on IoT Core</span></span> 
<span data-ttu-id="0ffc0-199">默认情况下，Iot 核心版上的 PowerShell 可能会生成日志文件，从而占用文件系统上的空间。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-199">PowerShell on Iot Core may generate log files by default taking up space on the filesystem.</span></span> <span data-ttu-id="0ffc0-200">虽然日志文件大小有限，但可能会占用空间，从而导致磁盘空间不足，此外还可能会导致更新失败。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-200">Although the log file sizes are limited they can take up space potentially resulting in a low disk space situation which, among other things, can result in updates failing.</span></span> <span data-ttu-id="0ffc0-201">每个 .evtx 事件日志文件的预定义大小上限为 20 MB。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-201">The .evtx event log files have a predefined maximum size of 20 MB each.</span></span> <span data-ttu-id="0ffc0-202">你可以通过注册表单独限制文件的大小上限。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-202">You  can individually limit files to have a different max size via registry.</span></span> <span data-ttu-id="0ffc0-203">例如，若要将 security.evtx 的最大上限设置为 10 MB，请输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-203">For example, To keep security.evtx at 10 MB max size:</span></span> 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a><span data-ttu-id="0ffc0-204">Schtasks 限制</span><span class="sxs-lookup"><span data-stu-id="0ffc0-204">Schtasks limitation</span></span>  
<span data-ttu-id="0ffc0-205">Schtasks 不支持使用 /xml 开关。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-205">Schtasks does not support using /xml switch.</span></span> <span data-ttu-id="0ffc0-206">例如：</span><span class="sxs-lookup"><span data-stu-id="0ffc0-206">For example:</span></span> 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
<span data-ttu-id="0ffc0-207">这会在 IoT 核心版上失败。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-207">This will fail on IoT Core.</span></span> <span data-ttu-id="0ffc0-208">运行命令将生成以下错误：错误：找不到指定的过程。</span><span class="sxs-lookup"><span data-stu-id="0ffc0-208">Running the command will generate the error: ERROR: The specified procedure could not be found.</span></span> 
