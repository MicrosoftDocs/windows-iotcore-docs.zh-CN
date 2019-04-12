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
# <a name="release-notes-for-raspberry-pi-3b"></a><span data-ttu-id="9a995-104">在 Raspberry Pi 3B + 的发行说明</span><span class="sxs-lookup"><span data-stu-id="9a995-104">Release Notes for Raspberry Pi 3B+</span></span>

<span data-ttu-id="9a995-105">&copy; 2018 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="9a995-105">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="9a995-106">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="9a995-106">All rights reserved.</span></span>

> [!NOTE]
> <span data-ttu-id="9a995-107">此版本中的 Raspberry Pi 3B + 是不受支持的 technical preview。</span><span class="sxs-lookup"><span data-stu-id="9a995-107">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="9a995-108">已完成有限的验证和支持。</span><span class="sxs-lookup"><span data-stu-id="9a995-108">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="9a995-109">可找到当前发行[此处](https://www.microsoft.com/en-us/software-download/windowsiot)。</span><span class="sxs-lookup"><span data-stu-id="9a995-109">The current release can be found [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="9a995-110">为更好地评估体验和对于任何商业产品，请使用 Raspberry Pi 3B 或其他设备使用受支持的 Intel、 Qualcomm 或 NXP Soc。</span><span class="sxs-lookup"><span data-stu-id="9a995-110">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="9a995-111">解决问题的 Raspberry Pi 3B +，请参阅我们的故障排除指南，[此处](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)。</span><span class="sxs-lookup"><span data-stu-id="9a995-111">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

## <a name="whats-new-in-this-build"></a><span data-ttu-id="9a995-112">什么是此生成中的新增功能：</span><span class="sxs-lookup"><span data-stu-id="9a995-112">What's new in this build:</span></span> 
* <span data-ttu-id="9a995-113">一般性的 bug 修复</span><span class="sxs-lookup"><span data-stu-id="9a995-113">General bug fixes</span></span>

## <a name="known-issues-in-this-build"></a><span data-ttu-id="9a995-114">此版本中的已知问题：</span><span class="sxs-lookup"><span data-stu-id="9a995-114">Known issues in this build:</span></span>
* <span data-ttu-id="9a995-115">此映像仅适用于 RPi3B +，RPi2 上将不会启动。</span><span class="sxs-lookup"><span data-stu-id="9a995-115">This image is only meant for RPi3B+ and will not boot on RPi2.</span></span> 
* <span data-ttu-id="9a995-116">从 Visual Studio 的 F5 驱动程序部署不适用于 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="9a995-116">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span> 
* <span data-ttu-id="9a995-117">载入 WIFI 和蓝牙不适用于 RPI3B +。</span><span class="sxs-lookup"><span data-stu-id="9a995-117">Onboard WIFI and Bluetooth do not work on RPI3B+.</span></span> 
* <span data-ttu-id="9a995-118">上 RPi3B + 禁用了 Ft5406 触摸屏幕驱动程序。</span><span class="sxs-lookup"><span data-stu-id="9a995-118">Ft5406 touch screen driver is disabled on RPi3B+.</span></span> 
* <span data-ttu-id="9a995-119">禁用 SD 卡活动 LED。</span><span class="sxs-lookup"><span data-stu-id="9a995-119">SD card activity LED is disabled.</span></span> 


### <a name="display-resolution-is-monitor-is-disconnected"></a><span data-ttu-id="9a995-120">显示分辨率是断开连接监视器</span><span class="sxs-lookup"><span data-stu-id="9a995-120">Display resolution is monitor is disconnected</span></span>
<span data-ttu-id="9a995-121">Raspberry Pi 3B + 如果断开连接监视器可能维护显示分辨率。</span><span class="sxs-lookup"><span data-stu-id="9a995-121">The Raspberry Pi 3B+ may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="9a995-122">监视器 EDID 用于设置系统的解决方法，当其中一个连接。</span><span class="sxs-lookup"><span data-stu-id="9a995-122">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="9a995-123">当断开连接，固件默认为根目录中的 SD 卡 config.txt 中内容。</span><span class="sxs-lookup"><span data-stu-id="9a995-123">When disconnected, the firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 


### <a name="video-performance"></a><span data-ttu-id="9a995-124">视频的性能</span><span class="sxs-lookup"><span data-stu-id="9a995-124">Video performance</span></span>
<span data-ttu-id="9a995-125">在平台上的视频播放性能没有进行优化。</span><span class="sxs-lookup"><span data-stu-id="9a995-125">Video playback performance on the platform is not optimized.</span></span>  <span data-ttu-id="9a995-126">动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。</span><span class="sxs-lookup"><span data-stu-id="9a995-126">Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span>  

### <a name="camera-support"></a><span data-ttu-id="9a995-127">照相机支持</span><span class="sxs-lookup"><span data-stu-id="9a995-127">Camera support</span></span>
<span data-ttu-id="9a995-128">照相机外围设备的支持是有限的。</span><span class="sxs-lookup"><span data-stu-id="9a995-128">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="9a995-129">由于平台来支持 D3D 现代 USB USB 主控制器上要求很高的网络摄像头生成数据流中的限制不支持直接连接到载入照相机总线 PiCam 设备。</span><span class="sxs-lookup"><span data-stu-id="9a995-129">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span>  <span data-ttu-id="9a995-130">即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。</span><span class="sxs-lookup"><span data-stu-id="9a995-130">Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  


### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="9a995-131">鼠标指针在调试时消失</span><span class="sxs-lookup"><span data-stu-id="9a995-131">Mouse pointer disappears while debugging</span></span>
<span data-ttu-id="9a995-132">在某些情况下，鼠标指针部署或调试应用程序使用 Visual Studio 后不可见，请将鼠标指针应重新出现，如果使用键盘 （选项卡） (8038595) 的焦点更改。</span><span class="sxs-lookup"><span data-stu-id="9a995-132">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab) (8038595).</span></span>

### <a name="server-applications-with-softap"></a><span data-ttu-id="9a995-133">SoftAP 服务器应用程序</span><span class="sxs-lookup"><span data-stu-id="9a995-133">Server applications with SoftAP</span></span>
<span data-ttu-id="9a995-134">当使用 SoftAP 客户端将无法再访问由 UAP 应用公开的内容。</span><span class="sxs-lookup"><span data-stu-id="9a995-134">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span> <span data-ttu-id="9a995-135">提供通过 SoftAP UAP 应用程序必须从控制台设备 (8111807) 上进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="9a995-135">To expose UAP applications via SoftAP the following changes must be made from the console on the device (8111807):</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

<span data-ttu-id="9a995-136">重新启动。</span><span class="sxs-lookup"><span data-stu-id="9a995-136">Reboot.</span></span>

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="9a995-137">在预建 FFUs 传感器驱动程序冲突</span><span class="sxs-lookup"><span data-stu-id="9a995-137">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="9a995-138">提供 FFUs 中没有传感器驱动程序冲突。</span><span class="sxs-lookup"><span data-stu-id="9a995-138">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="9a995-139">远程传感器框架指南针、 磁力仪、 加速感应器和回转仪安装驱动程序。</span><span class="sxs-lookup"><span data-stu-id="9a995-139">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="9a995-140">用于访问这些应用程序中的 UWP Api 假设只是一个安装。</span><span class="sxs-lookup"><span data-stu-id="9a995-140">The UWP APIs for accessing these from an application assume just one is installed.</span></span> <span data-ttu-id="9a995-141">如果你正在开发以物理方式附加设备的驱动程序，Microsoft 上的远程驱动程序提供 FFUs 会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="9a995-141">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>  

<span data-ttu-id="9a995-142">若要解决此，可以通过连接到设备通过 SSH 或 Powershell 并使用工具 devcon.exe 通过键入删除远程传感器驱动程序删除冲突的驱动程序：</span><span class="sxs-lookup"><span data-stu-id="9a995-142">To solve for this, the conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing:</span></span> 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

<span data-ttu-id="9a995-143">远程传感器驱动程序不会影响创建 FFUs OEM。</span><span class="sxs-lookup"><span data-stu-id="9a995-143">The remote sensor driver does not affect OEM created FFUs.</span></span> 


### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="9a995-144">默认管理员用户名和密码</span><span class="sxs-lookup"><span data-stu-id="9a995-144">Default administrator user name and password</span></span>
<span data-ttu-id="9a995-145">默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。</span><span class="sxs-lookup"><span data-stu-id="9a995-145">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="9a995-146">这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。</span><span class="sxs-lookup"><span data-stu-id="9a995-146">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 

### <a name="volume-controls"></a><span data-ttu-id="9a995-147">音量控件</span><span class="sxs-lookup"><span data-stu-id="9a995-147">Volume controls</span></span>
<span data-ttu-id="9a995-148">依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。</span><span class="sxs-lookup"><span data-stu-id="9a995-148">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

### <a name="usb-keyboards"></a><span data-ttu-id="9a995-149">USB 键盘</span><span class="sxs-lookup"><span data-stu-id="9a995-149">USB keyboards</span></span>
<span data-ttu-id="9a995-150">某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。</span><span class="sxs-lookup"><span data-stu-id="9a995-150">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="9a995-151">使用其他键盘或鼠标。</span><span class="sxs-lookup"><span data-stu-id="9a995-151">Use a different keyboard or mouse.</span></span> <span data-ttu-id="9a995-152">可以在文档中找到的已验证的外围设备列表[此处](http://go.microsoft.com/fwlink/?LinkId=619428)。</span><span class="sxs-lookup"><span data-stu-id="9a995-152">A list of validated peripheral devices can be found in the documentation [here](http://go.microsoft.com/fwlink/?LinkId=619428).</span></span>
 
### <a name="screen-orientation"></a><span data-ttu-id="9a995-153">屏幕方向</span><span class="sxs-lookup"><span data-stu-id="9a995-153">Screen orientation</span></span>
<span data-ttu-id="9a995-154">在通用应用程序中可能不遵循设置为"纵向"方向。</span><span class="sxs-lookup"><span data-stu-id="9a995-154">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="9a995-155">引用具有 AllJoyn 模板适配器</span><span class="sxs-lookup"><span data-stu-id="9a995-155">Referencing adapters with AllJoyn templates</span></span>
<span data-ttu-id="9a995-156">尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。</span><span class="sxs-lookup"><span data-stu-id="9a995-156">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="9a995-157">若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。</span><span class="sxs-lookup"><span data-stu-id="9a995-157">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a><span data-ttu-id="9a995-158">在 Windows 10 IoT Core 上的 WiFi 直接限制</span><span class="sxs-lookup"><span data-stu-id="9a995-158">WiFi Direct limitations on Windows 10 IoT Core</span></span>
1. <span data-ttu-id="9a995-159">Windows 10 IoT 核心版设备必须是连接的设备 – 它不会为广告设备与另一台设备发起连接。</span><span class="sxs-lookup"><span data-stu-id="9a995-159">The Windows 10 IoT Core device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
2. <span data-ttu-id="9a995-160">必须使用高级配对。</span><span class="sxs-lookup"><span data-stu-id="9a995-160">Advanced pairing must be used.</span></span>  <span data-ttu-id="9a995-161">示例应用演示了如何在连接前使用高级配对 API 对设备进行配对。</span><span class="sxs-lookup"><span data-stu-id="9a995-161">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
3. <span data-ttu-id="9a995-162">并非所有无线适配器都支持 WLAN Direct。</span><span class="sxs-lookup"><span data-stu-id="9a995-162">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="9a995-163">我们已测试并验证“Realtek RTL8188EU 无线 LAN 802.11n USB 2.0 网络适配器”有效，但其他适配器可能不受支持。</span><span class="sxs-lookup"><span data-stu-id="9a995-163">We have tested and validated that the "Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter" works, but other adapters may not be supported.</span></span> 

### <a name="non-default-drive-mode-3890679"></a><span data-ttu-id="9a995-164">非默认驱动器模式 (3890679)</span><span class="sxs-lookup"><span data-stu-id="9a995-164">Non-default drive mode (3890679)</span></span> 
<span data-ttu-id="9a995-165">在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。</span><span class="sxs-lookup"><span data-stu-id="9a995-165">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="9a995-166">解决此问题，一次在应用程序的开始处设置驱动器模式。</span><span class="sxs-lookup"><span data-stu-id="9a995-166">To workaround this issue, set drive mode once at the beginning of the application.</span></span> 

### <a name="application-already-running-1244550"></a><span data-ttu-id="9a995-167">已处于运行状态的应用程序 (1244550)</span><span class="sxs-lookup"><span data-stu-id="9a995-167">Application already running (1244550)</span></span> 
<span data-ttu-id="9a995-168">如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。</span><span class="sxs-lookup"><span data-stu-id="9a995-168">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="9a995-169">解决方法：将默认启动应用更改为不希望部署的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9a995-169">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a><span data-ttu-id="9a995-170">BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃 (2199869)</span><span class="sxs-lookup"><span data-stu-id="9a995-170">BackgroundMediaPlayer.MessageReceivedFromForeground may crash (2199869)</span></span> 
<span data-ttu-id="9a995-171">以下代码行可能崩溃：</span><span class="sxs-lookup"><span data-stu-id="9a995-171">The following line of code may crash:</span></span> 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

<span data-ttu-id="9a995-172">若要防止在发生崩溃，添加以下代码，以便首先执行：</span><span class="sxs-lookup"><span data-stu-id="9a995-172">To prevent the crash, add this code so that it is executed first:</span></span>
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a><span data-ttu-id="9a995-173">Azure Active Directory 身份验证支持 (4266261)</span><span class="sxs-lookup"><span data-stu-id="9a995-173">Azure Active Directory Authentication Support (4266261)</span></span> 
<span data-ttu-id="9a995-174">Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。</span><span class="sxs-lookup"><span data-stu-id="9a995-174">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="9a995-175">命令行程序管理的应用程序崩溃</span><span class="sxs-lookup"><span data-stu-id="9a995-175">Shell Management of Application Crashes</span></span>
<span data-ttu-id="9a995-176">IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="9a995-176">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="9a995-177">如果重新启动应用程序继续崩溃，shell 将采用故障快速报警 – 系统关键进程会导致错误检测和恢复以尝试重新启动。</span><span class="sxs-lookup"><span data-stu-id="9a995-177">If the restarted applications continue to crash, the shell will employ a failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="9a995-178">可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="9a995-178">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="9a995-179">下面被捕获崩溃处理和重试逻辑：</span><span class="sxs-lookup"><span data-stu-id="9a995-179">Crash handling and retry logic is captured below:</span></span>

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

<span data-ttu-id="9a995-180">等待延迟，然后重新启动该应用程序。</span><span class="sxs-lookup"><span data-stu-id="9a995-180">Wait for the delay and relaunch the app.</span></span>

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="9a995-181">Dragonboard SPI 运行 4.8 mhz</span><span class="sxs-lookup"><span data-stu-id="9a995-181">Dragonboard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="9a995-182">Dragonboard 上的 SPI 将会忽略所请求的速度，并始终以 4.8 Mhz 的速度运行。</span><span class="sxs-lookup"><span data-stu-id="9a995-182">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="9a995-183">Dragonboard 连接待机状态</span><span class="sxs-lookup"><span data-stu-id="9a995-183">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="9a995-184">不，默认情况下，Qualcomm Dragonboard 启用连接待机状态。</span><span class="sxs-lookup"><span data-stu-id="9a995-184">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="9a995-185">若要启用连接待机 DragonBoard 上需要以下注册表项设置为"1"。</span><span class="sxs-lookup"><span data-stu-id="9a995-185">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”.</span></span>


### <a name="time-synchronization"></a><span data-ttu-id="9a995-186">时间同步</span><span class="sxs-lookup"><span data-stu-id="9a995-186">Time synchronization</span></span>
<span data-ttu-id="9a995-187">如果时间同步失败或超时这可能是由于无法访问或远距离时间服务器，可以执行以下要添加其他或本地时间服务器。</span><span class="sxs-lookup"><span data-stu-id="9a995-187">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
1. <span data-ttu-id="9a995-188">从命令行 （例如在设备上。</span><span class="sxs-lookup"><span data-stu-id="9a995-188">From a command line on the device (eg.</span></span> <span data-ttu-id="9a995-189">SSH，Powershell)。</span><span class="sxs-lookup"><span data-stu-id="9a995-189">SSH, Powershell).</span></span>
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. <span data-ttu-id="9a995-190">也可能会对通过启动脚本注册表这些新增功能或自定义运行时配置包包含必要时在映像创建过程的一部分。</span><span class="sxs-lookup"><span data-stu-id="9a995-190">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> 

### <a name="starting-the-ftp-server"></a><span data-ttu-id="9a995-191">启动 FTP 服务器</span><span class="sxs-lookup"><span data-stu-id="9a995-191">Starting the FTP Server</span></span> 
* <span data-ttu-id="9a995-192">若要运行一次-使用 SSH\PS 登录并运行以下命令以启动 FTP:</span><span class="sxs-lookup"><span data-stu-id="9a995-192">To run once - Login with SSH\PS and run this command to start FTP:</span></span>  

```
start ftpd.exe 
```

* <span data-ttu-id="9a995-193">若要在每次启动上运行，用户应创建计划程序任务-使用 SSH\PS 登录并创建计划程序任务：</span><span class="sxs-lookup"><span data-stu-id="9a995-193">To run on every boot, users should create a scheduler task - Login with SSH\PS and create a scheduler task:</span></span>

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a><span data-ttu-id="9a995-194">更新的分区大小要求</span><span class="sxs-lookup"><span data-stu-id="9a995-194">Partition size requirements for Update</span></span> 
<span data-ttu-id="9a995-195">请确保数据分区将保持足够的空间用于更新功能。</span><span class="sxs-lookup"><span data-stu-id="9a995-195">Ensure data partition maintains sufficient space for update functionality.</span></span><span data-ttu-id="9a995-196">  我们建议 1 gb 的可用空间的完整更新功能。</span><span class="sxs-lookup"><span data-stu-id="9a995-196">  We recommend 1GB free for full update functionality.</span></span> <span data-ttu-id="9a995-197"> 如果数据分区不具有足够的空间，更新将在安装阶段中失败。</span><span class="sxs-lookup"><span data-stu-id="9a995-197"> If Data partition does not have enough space, updates will fail in the installation phase.</span></span> 

### <a name="powershell-log-generation-on-iot-core"></a><span data-ttu-id="9a995-198">在 IoT Core 上的 PowerShell 日志生成</span><span class="sxs-lookup"><span data-stu-id="9a995-198">PowerShell log generation on IoT Core</span></span> 
<span data-ttu-id="9a995-199">在 Iot Core 上的 PowerShell 可能会占用文件系统上的空间的默认情况下生成日志文件。</span><span class="sxs-lookup"><span data-stu-id="9a995-199">PowerShell on Iot Core may generate log files by default taking up space on the filesystem.</span></span> <span data-ttu-id="9a995-200">但日志文件大小受到的限制可能占用空间可能会导致磁盘空间不足的空间这种，此外，可能会导致更新失败情况。</span><span class="sxs-lookup"><span data-stu-id="9a995-200">Although the log file sizes are limited they can take up space potentially resulting in a low disk space situation which, among other things, can result in updates failing.</span></span> <span data-ttu-id="9a995-201">扩展名为.evtx 事件日志文件具有预定义的最大大小的 20 MB。</span><span class="sxs-lookup"><span data-stu-id="9a995-201">The .evtx event log files have a predefined maximum size of 20 MB each.</span></span> <span data-ttu-id="9a995-202">您可以单独限制文件通过注册表有不同的最大大小。</span><span class="sxs-lookup"><span data-stu-id="9a995-202">You  can individually limit files to have a different max size via registry.</span></span> <span data-ttu-id="9a995-203">例如，若要使 security.evtx 保持 10 MB 最大大小：</span><span class="sxs-lookup"><span data-stu-id="9a995-203">For example, To keep security.evtx at 10 MB max size:</span></span> 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a><span data-ttu-id="9a995-204">Schtasks 限制</span><span class="sxs-lookup"><span data-stu-id="9a995-204">Schtasks limitation</span></span>  
<span data-ttu-id="9a995-205">Schtasks 不支持使用 /xml 开关。</span><span class="sxs-lookup"><span data-stu-id="9a995-205">Schtasks does not support using /xml switch.</span></span> <span data-ttu-id="9a995-206">例如：</span><span class="sxs-lookup"><span data-stu-id="9a995-206">For example:</span></span> 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
<span data-ttu-id="9a995-207">这将在 IoT Core 上失败。</span><span class="sxs-lookup"><span data-stu-id="9a995-207">This will fail on IoT Core.</span></span> <span data-ttu-id="9a995-208">运行该命令将生成错误：错误：找不到指定的过程。</span><span class="sxs-lookup"><span data-stu-id="9a995-208">Running the command will generate the error: ERROR: The specified procedure could not be found.</span></span> 
