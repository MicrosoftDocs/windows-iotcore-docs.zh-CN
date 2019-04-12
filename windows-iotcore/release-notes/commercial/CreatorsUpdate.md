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
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a><span data-ttu-id="d55fa-104">创意者更新的 Windows 10 IoT 核心版发行说明</span><span class="sxs-lookup"><span data-stu-id="d55fa-104">Creators Update Release Notes for Windows 10 IoT Core</span></span>
<span data-ttu-id="d55fa-105">内部版本 15063 版本号。</span><span class="sxs-lookup"><span data-stu-id="d55fa-105">Build Number 15063.</span></span> <span data-ttu-id="d55fa-106">2017 年 4 月</span><span class="sxs-lookup"><span data-stu-id="d55fa-106">April 2017</span></span>

<span data-ttu-id="d55fa-107">Windows 10 IoT Core 支持的嵌入式或专用用途设备的开发，Oem 和构建小型设备的 Windows 解决方案的开发人员的选择。</span><span class="sxs-lookup"><span data-stu-id="d55fa-107">Windows 10 IoT Core enables development of embedded or dedicated-purpose devices and is the choice for the OEMs and developers building Windows solutions for small devices.</span></span>

<span data-ttu-id="d55fa-108">本文档提供补充其他内容和文档，了解此版本的 Windows 10 IoT 核心版的信息。</span><span class="sxs-lookup"><span data-stu-id="d55fa-108">This document provides information that supplements other content and documentation for this release of Windows 10 IoT Core.</span></span>

<span data-ttu-id="d55fa-109">此版本中的包包含工具和组件需要 Minnowboard 最大平台基于 Intel Atom 处理器基于 ARM Cortex A7 和 Dragonboard 410 c 基于 Qualcomm Snapdragon 400 系列的 Raspberry Pi 2 上安装 Windows 10 IoT 核心版处理器。</span><span class="sxs-lookup"><span data-stu-id="d55fa-109">The packages within this release contain tools and components needed to install Windows 10 IoT Core on Minnowboard Max platform based on Intel Atom processers, Raspberry Pi 2 based on ARM Cortex A7, and Dragonboard 410c based on Qualcomm Snapdragon 400 series processors.</span></span>   

<span data-ttu-id="d55fa-110">[其他平台和处理器](../../learn-about-hardware/SoCsAndCustomBoards.md)可以由合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="d55fa-110">[Other platforms and processors](../../learn-about-hardware/SoCsAndCustomBoards.md) may be available from partners.</span></span>

## <a name="privacy-statement"></a><span data-ttu-id="d55fa-111">隐私声明</span><span class="sxs-lookup"><span data-stu-id="d55fa-111">Privacy Statement</span></span>

<span data-ttu-id="d55fa-112">可以查看此版本的 Windows 操作系统的隐私声明[此处](http://go.microsoft.com/fwlink/?LinkId=506737)。</span><span class="sxs-lookup"><span data-stu-id="d55fa-112">The privacy statement for this version of the Windows operating system can be viewed [here](http://go.microsoft.com/fwlink/?LinkId=506737).</span></span>

## <a name="whats-new"></a><span data-ttu-id="d55fa-113">新增功能</span><span class="sxs-lookup"><span data-stu-id="d55fa-113">What's New</span></span>
* <span data-ttu-id="d55fa-114">Windows 10 IoT 核心版公开发行版。</span><span class="sxs-lookup"><span data-stu-id="d55fa-114">Windows 10 IoT Core Public Release.</span></span> 
   * <span data-ttu-id="d55fa-115">Azure 设备管理支持的 Oem 可以使用 Windows IoT Azure DM 客户端库以将设备管理功能添加到其 Azure IoT 中心连接设备。</span><span class="sxs-lookup"><span data-stu-id="d55fa-115">Azure Device Management Support - OEMs can use the Windows IoT Azure DM client library to add device management capabilities to their Azure IoT hub connected devices.</span></span>
   * <span data-ttu-id="d55fa-116">其他硅支持</span><span class="sxs-lookup"><span data-stu-id="d55fa-116">Additional Silicon Support</span></span>
      * <span data-ttu-id="d55fa-117">验证对 Intel Joule，Intel Pentium N4200，Intel Celeron N3350 即将发布 Atom x5 E39xx 处理器 (以前称为 Apollo Lake) 上的 Windows 10 IoT Core 的支持和 Raspberry Pi 3 Som。</span><span class="sxs-lookup"><span data-stu-id="d55fa-117">Verified support for Windows 10 IoT Core on Intel Joule, Intel Pentium N4200, Intel Celeron N3350, upcoming Atom x5-E39xx processors (formerly Apollo Lake) and Raspberry Pi 3 SOMs.</span></span>
      * <span data-ttu-id="d55fa-118">Allwinner 具有启用了对使用 Allwinner A64 SoC.其松树 64 和香蕉 Pi 设备</span><span class="sxs-lookup"><span data-stu-id="d55fa-118">Allwinner has enabled support for their Pine 64 and Banana Pi devices using the Allwinner A64 SoC.</span></span> 
   * <span data-ttu-id="d55fa-119">发现发现你已使用你的 Microsoft 帐户登录的设备所需的远程设备的任何特殊软件。</span><span class="sxs-lookup"><span data-stu-id="d55fa-119">Discovering your Remote Devices - No special software is needed to discover your devices that are signed in with your Microsoft Account.</span></span>
   * <span data-ttu-id="d55fa-120">有关振动、 亮度、 现代连接的待机、 电源管理、 电池电量和 NFC （不带百 HCE) 的新 UWP Api 和控件。</span><span class="sxs-lookup"><span data-stu-id="d55fa-120">New UWP APIs And controls for vibration, brightness, modern connected standby, power management, battery charge  and NFC (w/o HCE).</span></span> 
   * <span data-ttu-id="d55fa-121">新总线和 ARM PCIe USB 函数模式、 Wi-Fi Direct 和 GPIO 中断计数 API 的功能。</span><span class="sxs-lookup"><span data-stu-id="d55fa-121">New busses and capabilities for ARM PCIe, USB function mode, Wi-Fi Direct and  GPIO interrupt counting API.</span></span> 
   * <span data-ttu-id="d55fa-122">重置/恢复、 在 SOC PWM 和自动 USB 预配新的嵌入功能</span><span class="sxs-lookup"><span data-stu-id="d55fa-122">New Embedded features on Reset/Recovery, On-SOC PWM and Automatic USB provisioning</span></span> 
   * <span data-ttu-id="d55fa-123">改进了的工具的 VS Code 中，新 Windows Device Portal 和 IoT 仪表板功能，VS 2017 支持。</span><span class="sxs-lookup"><span data-stu-id="d55fa-123">Improved Tools - VS Code, New Windows Device Portal and IoT Dashboard features, VS 2017 support.</span></span>
   * <span data-ttu-id="d55fa-124">在 Windows IoT Core-Cortana Cortana 现可在 Windows 10 IoT 核心版上。</span><span class="sxs-lookup"><span data-stu-id="d55fa-124">Cortana on Windows IoT Core - Cortana is now available on Windows 10 IoT Core.</span></span> <span data-ttu-id="d55fa-125">向 Cortana 提问。</span><span class="sxs-lookup"><span data-stu-id="d55fa-125">Ask Cortana a question.</span></span>
   * <span data-ttu-id="d55fa-126">IoT 仪表板的改进的新功能和稳定性 bug 修复</span><span class="sxs-lookup"><span data-stu-id="d55fa-126">IoT Dashboard Improvements - New features and stability bug fixes</span></span>
      * <span data-ttu-id="d55fa-127">Windows Insider Preview 内部版本为 Raspberry Pi 和 Minnowboard</span><span class="sxs-lookup"><span data-stu-id="d55fa-127">Windows Insider Preview builds for Raspberry Pi and Minnowboard</span></span> 
      * <span data-ttu-id="d55fa-128">使用 Windows IoT 远程客户端的设备连接</span><span class="sxs-lookup"><span data-stu-id="d55fa-128">Connecting device using Windows IoT Remote Client</span></span> 
      * <span data-ttu-id="d55fa-129">Ipv6 地址中发现的设备</span><span class="sxs-lookup"><span data-stu-id="d55fa-129">Ipv6 addresses in discovering devices</span></span> 
      * <span data-ttu-id="d55fa-130">设备日志上传提交反馈时</span><span class="sxs-lookup"><span data-stu-id="d55fa-130">Uploading device logs while submitting feedback</span></span>
   *  <span data-ttu-id="d55fa-131">新的高精度 GPIO Api-使用 GPIO pulse 宽度的精确和高效测量的新 Api (Windows.Devices.Gpio.GpioInterruptBuffer) 会中断。</span><span class="sxs-lookup"><span data-stu-id="d55fa-131">New high precision GPIO APIs -  New APIs (Windows.Devices.Gpio.GpioInterruptBuffer) for precise and efficient measurement of pulse widths using GPIO interrupts.</span></span><span data-ttu-id="d55fa-132">  GPIO 提供程序包括新的中断缓冲区接口，以便计时拨号式编码器和距离测量设备等应用程序的高精度中断</span><span class="sxs-lookup"><span data-stu-id="d55fa-132">  GPIO providers include new Interrupt Buffer interface to allow for high precision interrupt timing for applications like rotary encoders and distance measuring devices</span></span>
   * <span data-ttu-id="d55fa-133">IoT-设备构建者现在可以完全锁定的设备保护 IoT 设备并获取高级恶意软件防护针对新的和未知恶意软件变体。</span><span class="sxs-lookup"><span data-stu-id="d55fa-133">Device Guard for IoT - Device builders can now fully lock down IoT devices and get advanced malware protection against new and unknown malware variants.</span></span><span data-ttu-id="d55fa-134">  这可以通过指定的允许的应用程序和驱动程序在设备上运行时不允许执行未知或不受信任代码签名颁发机构。</span><span class="sxs-lookup"><span data-stu-id="d55fa-134">  This can be done by specifying signing authorities for permissible applications and drivers that run on the device while disallowing execution of unknown or untrusted code.</span></span><span data-ttu-id="d55fa-135">  这意味着，改进了的安全性，以防止恶意软件和零时差攻击。</span><span class="sxs-lookup"><span data-stu-id="d55fa-135">  This means improved security against malware and zero day attacks.</span></span> 
   * <span data-ttu-id="d55fa-136">其他更新包括：</span><span class="sxs-lookup"><span data-stu-id="d55fa-136">Other updates include:</span></span> 
      * <span data-ttu-id="d55fa-137">改进的更新支持</span><span class="sxs-lookup"><span data-stu-id="d55fa-137">Improved Update Support</span></span> 
      * <span data-ttu-id="d55fa-138">Azure 网关 SDK 支持</span><span class="sxs-lookup"><span data-stu-id="d55fa-138">Azure Gateway SDK support</span></span> 
      * <span data-ttu-id="d55fa-139">USB 驱动器基于自动预配</span><span class="sxs-lookup"><span data-stu-id="d55fa-139">USB drive based auto-provisioning</span></span> 
      * <span data-ttu-id="d55fa-140">设备门户重新设计</span><span class="sxs-lookup"><span data-stu-id="d55fa-140">Device Portal redesign</span></span> 
      * <span data-ttu-id="d55fa-141">64 位映像现在支持最多 16384 MB 的内存</span><span class="sxs-lookup"><span data-stu-id="d55fa-141">64-bit images now supports up to 16,384 MB of memory</span></span> 
      * <span data-ttu-id="d55fa-142">WinRT 振动 Api</span><span class="sxs-lookup"><span data-stu-id="d55fa-142">WinRT Vibration APIs</span></span> 
      * <span data-ttu-id="d55fa-143">改进了语言支持</span><span class="sxs-lookup"><span data-stu-id="d55fa-143">Improved language support</span></span> 
   * <span data-ttu-id="d55fa-144">其他</span><span class="sxs-lookup"><span data-stu-id="d55fa-144">Miscellaneous</span></span>  
      * <span data-ttu-id="d55fa-145">已更改为默认 BCD 设置以防止设备尝试恢复模式下不存在时启动到恢复模式。</span><span class="sxs-lookup"><span data-stu-id="d55fa-145">A change has been made to the default BCD settings to prevent devices from attempting to boot to recovery mode when recovery mode does not exist.</span></span> 
      * <span data-ttu-id="d55fa-146">IOT_POWER_SETTINGS 功能现在包括 powercfg.exe。</span><span class="sxs-lookup"><span data-stu-id="d55fa-146">IOT_POWER_SETTINGS feature now includes powercfg.exe.</span></span> <span data-ttu-id="d55fa-147">此功能适用于所有体系结构 (ARM32，x86 和 x64)。</span><span class="sxs-lookup"><span data-stu-id="d55fa-147">This is available for all architectures (ARM32, x86 and x64).</span></span> 
      * <span data-ttu-id="d55fa-148">对进行了更改 Applyupdate.exe 添加 blockrebooton/blockrebootoff 标志</span><span class="sxs-lookup"><span data-stu-id="d55fa-148">Changes were made to Applyupdate.exe to add the blockrebooton/blockrebootoff flags</span></span> 
      * <span data-ttu-id="d55fa-149">硬件通知 (hwnclx) 和 USB 函数 (usbfnclx) 的类扩展已添加到默认映像 IoT 核心版</span><span class="sxs-lookup"><span data-stu-id="d55fa-149">The Class Extensions for Hardware Notification (hwnclx) and USB Function (usbfnclx) have been added to the default IoT Core images</span></span>

## <a name="known-issues"></a><span data-ttu-id="d55fa-150">已知问题</span><span class="sxs-lookup"><span data-stu-id="d55fa-150">Known Issues</span></span>

### <a name="raspberry-pi"></a><span data-ttu-id="d55fa-151">Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="d55fa-151">Raspberry Pi</span></span>  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a><span data-ttu-id="d55fa-152">Raspberry Pi 的显示分辨率如果断开连接监视器</span><span class="sxs-lookup"><span data-stu-id="d55fa-152">Raspberry Pi Display Resolution if monitor is disconnected</span></span> 
<span data-ttu-id="d55fa-153">在 Raspberry Pi 如果断开连接监视器不能保持显示分辨率。</span><span class="sxs-lookup"><span data-stu-id="d55fa-153">The Raspberry Pi may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="d55fa-154">监视器 EDID 用于设置系统的解决方法，当其中一个连接。</span><span class="sxs-lookup"><span data-stu-id="d55fa-154">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span>  
<span data-ttu-id="d55fa-155">当断开连接，Raspberry Pi 固件默认为根目录中的 SD 卡 config.txt 中内容。</span><span class="sxs-lookup"><span data-stu-id="d55fa-155">When disconnected, the Raspberry Pi firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 

#### <a name="raspberry-pi-video-performance"></a><span data-ttu-id="d55fa-156">Raspberry Pi 视频性能</span><span class="sxs-lookup"><span data-stu-id="d55fa-156">Raspberry Pi Video Performance</span></span> 
<span data-ttu-id="d55fa-157">Raspberry Pi 平台上的视频播放性能尚未进行优化。</span><span class="sxs-lookup"><span data-stu-id="d55fa-157">Video playback performance on the Raspberry Pi platform has not been optimized.</span></span><span data-ttu-id="d55fa-158">  动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。</span><span class="sxs-lookup"><span data-stu-id="d55fa-158">  Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span> 

#### <a name="raspberry-pi-camera-support"></a><span data-ttu-id="d55fa-159">Raspberry Pi 相机支持</span><span class="sxs-lookup"><span data-stu-id="d55fa-159">Raspberry Pi Camera Support</span></span> 
<span data-ttu-id="d55fa-160">与 Raspberry Pi 设备相机外围设备的 Windows 10 IoT Core 支持是有限的。</span><span class="sxs-lookup"><span data-stu-id="d55fa-160">Windows 10 IoT Core support for camera peripheral devices with Raspberry Pi devices is limited.</span></span> <span data-ttu-id="d55fa-161">直接连接到载入照相机总线 PiCam 设备是当前不支持，因为它需要将 Raspberry Pi 上当前无效，因为未实现的 DirectX 驱动程序的 GPU 服务。</span><span class="sxs-lookup"><span data-stu-id="d55fa-161">The PiCam device directly connected to the onboard camera bus is not currently supported, as it requires GPU services that are not currently available on the Raspberry Pi because the DirectX driver is not implemented.</span></span> <span data-ttu-id="d55fa-162">现代 USB 摄像头可在 USB 主控制器上生成要求极度严苛的数据流。</span><span class="sxs-lookup"><span data-stu-id="d55fa-162">Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span><span data-ttu-id="d55fa-163">  即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。</span><span class="sxs-lookup"><span data-stu-id="d55fa-163">  Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  

#### <a name="raspberry-pi-3-bluetooth-support"></a><span data-ttu-id="d55fa-164">Raspberry Pi 3 蓝牙支持</span><span class="sxs-lookup"><span data-stu-id="d55fa-164">Raspberry Pi 3 Bluetooth support</span></span> 
<span data-ttu-id="d55fa-165">Raspberry Pi3 内置的蓝牙驱动程序仅支持带宽较低的设备</span><span class="sxs-lookup"><span data-stu-id="d55fa-165">The Raspberry Pi3 built-in Bluetooth driver only supports low bandwidth devices</span></span>  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a><span data-ttu-id="d55fa-166">串行端口使用情况和 Raspberry Pi 2 上的访问</span><span class="sxs-lookup"><span data-stu-id="d55fa-166">Serial Port Usage and Access on Raspberry Pi 2</span></span> 
<span data-ttu-id="d55fa-167">Raspberry Pi 2 支持通过 PL011 UART 串行传输通信。</span><span class="sxs-lookup"><span data-stu-id="d55fa-167">Raspberry Pi 2 supports the serial transport for communication through the PL011 UART.</span></span><span data-ttu-id="d55fa-168">  这是内核调试方案中的默认设置。</span><span class="sxs-lookup"><span data-stu-id="d55fa-168">  This is set by default in kernel debugging scenarios.</span></span><span data-ttu-id="d55fa-169">  应用程序或设备驱动程序可以使用 PL011 UART 在 PL011 设备驱动程序使用以下命令关闭调试程序的情况下发送和接收数据：</span><span class="sxs-lookup"><span data-stu-id="d55fa-169">  An application or device driver can use the PL011 UART to send and receive data with the PL011 device driver turning off the debugger using the following command:</span></span>   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a><span data-ttu-id="d55fa-170">龙板</span><span class="sxs-lookup"><span data-stu-id="d55fa-170">Dragon Board</span></span> 

#### <a name="dragonboard-410c-shutdown"></a><span data-ttu-id="d55fa-171">Dragonboard 410c 关机</span><span class="sxs-lookup"><span data-stu-id="d55fa-171">Dragonboard 410c Shutdown</span></span> 
<span data-ttu-id="d55fa-172">在 DragonBoard 上，关机命令不会关闭开发板电源。</span><span class="sxs-lookup"><span data-stu-id="d55fa-172">On the DragonBoard, a shutdown command will not power off the board.</span></span> <span data-ttu-id="d55fa-173">系统将会重新启动。</span><span class="sxs-lookup"><span data-stu-id="d55fa-173">The system will restart.</span></span> <span data-ttu-id="d55fa-174">请通过断开电源连接来关闭开发板电源。</span><span class="sxs-lookup"><span data-stu-id="d55fa-174">Please power off the board by disconnecting the power.</span></span> 

#### <a name="dragon-board-headset--microphone-jack"></a><span data-ttu-id="d55fa-175">龙板耳机和麦克风插孔</span><span class="sxs-lookup"><span data-stu-id="d55fa-175">Dragon Board headset & microphone jack</span></span>  
<span data-ttu-id="d55fa-176">Dragonboard BSP 具有耳机插孔和麦克风插孔的驱动程序，但它在开发板上没有这两种插孔。</span><span class="sxs-lookup"><span data-stu-id="d55fa-176">The Dragonboard BSP has drivers for the headset jack and microphone jack, but it doesn't have either of these jacks on board.</span></span>  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a><span data-ttu-id="d55fa-177">锁的速度运行 Dragonboard SPI</span><span class="sxs-lookup"><span data-stu-id="d55fa-177">Dragonboard SPI runs at lock speed</span></span>  
<span data-ttu-id="d55fa-178">上 Dragonboard SPI 将忽略所请求的速度，并始终以预配置的速度运行。</span><span class="sxs-lookup"><span data-stu-id="d55fa-178">The SPI on the Dragonboard will ignore the requested speed and always run at a preconfigured speed.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="d55fa-179">Dragonboard 连接待机状态</span><span class="sxs-lookup"><span data-stu-id="d55fa-179">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="d55fa-180">不，默认情况下，Qualcomm Dragonboard 启用连接待机状态。</span><span class="sxs-lookup"><span data-stu-id="d55fa-180">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span><span data-ttu-id="d55fa-181">  若要启用连接待机 DragonBoard 上的以下注册表项需要设置为"1"</span><span class="sxs-lookup"><span data-stu-id="d55fa-181">  To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”</span></span> 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
<span data-ttu-id="d55fa-182">请注意，不是所有平台支持为 CS，因此这不可能在其他平台上工作。</span><span class="sxs-lookup"><span data-stu-id="d55fa-182">Note that not all platforms have support for CS, so this may not work on other platforms.</span></span>    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a><span data-ttu-id="d55fa-183">在某些 Qualcomm 平台上可能无法正常振动 API</span><span class="sxs-lookup"><span data-stu-id="d55fa-183">Vibration API may not function on some Qualcomm platforms</span></span> 
<span data-ttu-id="d55fa-184">建议的解决方法是将添加以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="d55fa-184">The suggested workaround is to add the following registry key:</span></span> 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
<span data-ttu-id="d55fa-185">确认 / 验证现有的映像上使用 SSH 或 PowerShell 连接并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d55fa-185">For confirmation / verification on an existing image connect with SSH or PowerShell and run the following command:</span></span> 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a><span data-ttu-id="d55fa-186">MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="d55fa-186">MinnowBoard</span></span>  

#### <a name="minnowboard-max-firmware-update"></a><span data-ttu-id="d55fa-187">Minnowboard 最大固件更新</span><span class="sxs-lookup"><span data-stu-id="d55fa-187">Minnowboard Max Firmware Update</span></span> 
<span data-ttu-id="d55fa-188">除非固件版本.092，否则将不会启动 MinnowBoard 最大或更高版本。</span><span class="sxs-lookup"><span data-stu-id="d55fa-188">The MinnowBoard Max will not boot unless the firmware is version .092 or later.</span></span>  
<span data-ttu-id="d55fa-189">可能存在网络连接故障中 MinnowBoard 最大值 (MBM) 固件版本 0.93。</span><span class="sxs-lookup"><span data-stu-id="d55fa-189">There may be network connectivity failures in MinnowBoard Max (MBM) firmware version 0.93.</span></span><span data-ttu-id="d55fa-190">   问题被固定的固件版本 0.94。） 最小建议的固件的版本是"MinnowBoard 最大 0.94 32-bit"。</span><span class="sxs-lookup"><span data-stu-id="d55fa-190">   The issue is fixed in firmware version 0.94.)  The minimum recommended version of the firmware is “MinnowBoard MAX 0.94 32-bit”.</span></span> <span data-ttu-id="d55fa-191">可以从下载固件更新 [此处](http://go.microsoft.com/fwlink/?LinkId=708613)。</span><span class="sxs-lookup"><span data-stu-id="d55fa-191">Firmware updates can be downloaded from [here](http://go.microsoft.com/fwlink/?LinkId=708613).</span></span>
  
 
### <a name="all-platforms"></a><span data-ttu-id="d55fa-192">所有平台</span><span class="sxs-lookup"><span data-stu-id="d55fa-192">All Platforms</span></span> 

#### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="d55fa-193">鼠标指针在调试时消失</span><span class="sxs-lookup"><span data-stu-id="d55fa-193">Mouse Pointer disappears while debugging</span></span> 
<span data-ttu-id="d55fa-194">在某些情况下，鼠标指针在部署或调试应用程序使用 Visual Studio 后不可见，如果使用键盘 (Tab) 的焦点更改鼠标指针应会重新出现</span><span class="sxs-lookup"><span data-stu-id="d55fa-194">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab)</span></span>  

#### <a name="server-applications-with-softap"></a><span data-ttu-id="d55fa-195">SoftAP 服务器应用程序</span><span class="sxs-lookup"><span data-stu-id="d55fa-195">Server Applications with SoftAP</span></span>  
<span data-ttu-id="d55fa-196">当使用 SoftAP 客户端将无法再访问由 UAP 应用公开的内容。</span><span class="sxs-lookup"><span data-stu-id="d55fa-196">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span>  
<span data-ttu-id="d55fa-197">提供通过 SoftAP UAP 应用程序必须从设备上的控制台进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="d55fa-197">To expose UAP applications via SoftAP the following changes must be made from the console on the device :</span></span>  
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

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="d55fa-198">在预建 FFUs 传感器驱动程序冲突</span><span class="sxs-lookup"><span data-stu-id="d55fa-198">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="d55fa-199">提供 FFUs 中没有传感器驱动程序冲突。</span><span class="sxs-lookup"><span data-stu-id="d55fa-199">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="d55fa-200">远程传感器框架指南针、 磁力仪、 加速感应器和回转仪安装驱动程序。</span><span class="sxs-lookup"><span data-stu-id="d55fa-200">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="d55fa-201">用于访问这些应用程序中的 UWP Api 假定安装了只是 1。</span><span class="sxs-lookup"><span data-stu-id="d55fa-201">The UWP APIs for accessing these from an application assume just 1 is installed.</span></span> <span data-ttu-id="d55fa-202">如果你正在开发以物理方式附加设备的驱动程序，Microsoft 上的远程驱动程序提供 FFUs 会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="d55fa-202">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>  
<span data-ttu-id="d55fa-203">解决方案：可以通过连接到设备通过 SSH 或 PowerShell 并使用工具 devcon.exe 通过键入删除远程传感器驱动程序删除冲突的驱动程序"devcon.exe 删除 @"ROOT\REMOTESENSORDRIVER \*"。</span><span class="sxs-lookup"><span data-stu-id="d55fa-203">Resolution: The conflicting driver can be removed by connecting to the device via SSH or PowerShell and using the tool devcon.exe to remove the remote sensor driver by typing “devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*”.</span></span> <span data-ttu-id="d55fa-204">远程传感器驱动程序不会影响创建 FFUs OEM。</span><span class="sxs-lookup"><span data-stu-id="d55fa-204">The remote sensor driver does not affect OEM created FFUs.</span></span> 
 
#### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="d55fa-205">默认管理员用户名和密码</span><span class="sxs-lookup"><span data-stu-id="d55fa-205">Default Administrator User Name and Password</span></span> 
<span data-ttu-id="d55fa-206">默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。</span><span class="sxs-lookup"><span data-stu-id="d55fa-206">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="d55fa-207">这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。</span><span class="sxs-lookup"><span data-stu-id="d55fa-207">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 
 
#### <a name="volume-controls"></a><span data-ttu-id="d55fa-208">音量控件</span><span class="sxs-lookup"><span data-stu-id="d55fa-208">Volume Controls</span></span> 
<span data-ttu-id="d55fa-209">依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。</span><span class="sxs-lookup"><span data-stu-id="d55fa-209">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 
 
#### <a name="usb-keyboards"></a><span data-ttu-id="d55fa-210">USB 键盘</span><span class="sxs-lookup"><span data-stu-id="d55fa-210">USB Keyboards</span></span>  
<span data-ttu-id="d55fa-211">某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。</span><span class="sxs-lookup"><span data-stu-id="d55fa-211">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="d55fa-212">使用其他键盘或鼠标。</span><span class="sxs-lookup"><span data-stu-id="d55fa-212">Use a different keyboard or mouse.</span></span> <span data-ttu-id="d55fa-213">可以找到已验证的外围设备的列表[此处](../../learn-about-hardware/HardwareCompatList.md)。</span><span class="sxs-lookup"><span data-stu-id="d55fa-213">A list of validated peripheral devices can be found [here](../../learn-about-hardware/HardwareCompatList.md).</span></span>  
 
#### <a name="screen-orientation"></a><span data-ttu-id="d55fa-214">屏幕方向</span><span class="sxs-lookup"><span data-stu-id="d55fa-214">Screen Orientation</span></span> 
<span data-ttu-id="d55fa-215">设置为"纵向"方向可能不会采用中通用的应用程序</span><span class="sxs-lookup"><span data-stu-id="d55fa-215">Setting the orientation to “Portrait” may not be honored in a Universal App</span></span> 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="d55fa-216">使用 AllJoyn 模板引用适配器</span><span class="sxs-lookup"><span data-stu-id="d55fa-216">Referencing Adapters with AllJoyn Templates</span></span> 
<span data-ttu-id="d55fa-217">尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。</span><span class="sxs-lookup"><span data-stu-id="d55fa-217">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span><span data-ttu-id="d55fa-218">  若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。</span><span class="sxs-lookup"><span data-stu-id="d55fa-218">  To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span> 

#### <a name="non-default-drive-mode"></a><span data-ttu-id="d55fa-219">非默认驱动器模式</span><span class="sxs-lookup"><span data-stu-id="d55fa-219">Non-default drive mode</span></span>  
<span data-ttu-id="d55fa-220">在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。</span><span class="sxs-lookup"><span data-stu-id="d55fa-220">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="d55fa-221">解决方法：在应用程序开端处设置一次驱动器模式。</span><span class="sxs-lookup"><span data-stu-id="d55fa-221">WORKAROUND: Set drive mode once at the beginning of the application.</span></span> 
 
#### <a name="application-already-running"></a><span data-ttu-id="d55fa-222">已在运行的应用程序</span><span class="sxs-lookup"><span data-stu-id="d55fa-222">Application already running</span></span>  
<span data-ttu-id="d55fa-223">如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。</span><span class="sxs-lookup"><span data-stu-id="d55fa-223">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="d55fa-224">解决方法：将默认启动应用更改为不希望部署的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d55fa-224">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a><span data-ttu-id="d55fa-225">BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃</span><span class="sxs-lookup"><span data-stu-id="d55fa-225">BackgroundMediaPlayer.MessageReceivedFromForeground may crash</span></span>  
<span data-ttu-id="d55fa-226">以下代码行可能会崩溃： `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`。</span><span class="sxs-lookup"><span data-stu-id="d55fa-226">The following line of code may crash: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`.</span></span>
<br>
<span data-ttu-id="d55fa-227">若要防止在发生崩溃，添加此代码，以便首先执行</span><span class="sxs-lookup"><span data-stu-id="d55fa-227">To prevent the crash, add this code so that it is executed first</span></span> `var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a><span data-ttu-id="d55fa-228">Azure Active Directory 身份验证支持</span><span class="sxs-lookup"><span data-stu-id="d55fa-228">Azure Active Directory Authentication Support</span></span>  
<span data-ttu-id="d55fa-229">Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。</span><span class="sxs-lookup"><span data-stu-id="d55fa-229">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  
 
#### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="d55fa-230">命令行程序管理的应用程序崩溃</span><span class="sxs-lookup"><span data-stu-id="d55fa-230">Shell Management of Application Crashes</span></span> 
<span data-ttu-id="d55fa-231">IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="d55fa-231">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span><span data-ttu-id="d55fa-232">  如果重新启动应用程序继续崩溃，shell 将采用 __failfast – 系统关键进程导致的 bug 检查和恢复以尝试重新启动。</span><span class="sxs-lookup"><span data-stu-id="d55fa-232">  If the restarted applications continue to crash, the shell will employ a __failfast – a system critical process that causes a bug check and reboot in an attempt to recover.</span></span><span data-ttu-id="d55fa-233">  可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="d55fa-233">  Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   

<span data-ttu-id="d55fa-234">下面捕获的是崩溃处理和重试逻辑：</span><span class="sxs-lookup"><span data-stu-id="d55fa-234">Crash handing and retry logic is captured below:</span></span> 

<span data-ttu-id="d55fa-235">Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig （或对于 ForegroundAppConfig 讲述的内容）</span><span class="sxs-lookup"><span data-stu-id="d55fa-235">Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed)</span></span> 
* <span data-ttu-id="d55fa-236">Qword:"FailureResetIntervalMs"– 时间应用的长度必须运行成功重置为 0 出现故障。</span><span class="sxs-lookup"><span data-stu-id="d55fa-236">Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0.</span></span> <span data-ttu-id="d55fa-237">-默认值是 0x00000000000493E0 = = 5 分钟。</span><span class="sxs-lookup"><span data-stu-id="d55fa-237">– default is 0x00000000000493E0 == 5 minutes.</span></span> 
* <span data-ttu-id="d55fa-238">Qword:"BaseRetryDelayMs"-等待时间系数。</span><span class="sxs-lookup"><span data-stu-id="d55fa-238">Qword:"BaseRetryDelayMs"  -- wait time coefficient.</span></span><span data-ttu-id="d55fa-239">  默认值为 0xa。</span><span class="sxs-lookup"><span data-stu-id="d55fa-239">  Default is 0xa.</span></span>
* <span data-ttu-id="d55fa-240">Dword:"MaxFailureCount"。</span><span class="sxs-lookup"><span data-stu-id="d55fa-240">Dword:"MaxFailureCount".</span></span> <span data-ttu-id="d55fa-241">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="d55fa-241">Default is 10.</span></span>
* <span data-ttu-id="d55fa-242">DWord:"FallbackExponentNumerator"，默认值为 31。</span><span class="sxs-lookup"><span data-stu-id="d55fa-242">DWord:"FallbackExponentNumerator", default is 31.</span></span>
* <span data-ttu-id="d55fa-243">Dword:"FallbackExponentDenominator"默认值为 20。</span><span class="sxs-lookup"><span data-stu-id="d55fa-243">Dword:"FallbackExponentDenominator", default is 20.</span></span>
 
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
 
#### <a name="time-synchronization"></a><span data-ttu-id="d55fa-244">时间同步</span><span class="sxs-lookup"><span data-stu-id="d55fa-244">Time Synchronization</span></span>  
<span data-ttu-id="d55fa-245">如果时间同步失败或超时这可能是由于无法访问或远距离时间服务器，可以执行以下要添加其他或本地时间服务器。</span><span class="sxs-lookup"><span data-stu-id="d55fa-245">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
* <span data-ttu-id="d55fa-246">从命令行 （例如在设备上。</span><span class="sxs-lookup"><span data-stu-id="d55fa-246">From a command line on the device (eg.</span></span> <span data-ttu-id="d55fa-247">SSH, PowerShell)  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span><span class="sxs-lookup"><span data-stu-id="d55fa-247">SSH, PowerShell)  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span></span> 
* <span data-ttu-id="d55fa-248">也可能会对通过启动脚本注册表这些新增功能或自定义运行时配置包包含必要时在映像创建过程的一部分。</span><span class="sxs-lookup"><span data-stu-id="d55fa-248">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> 
<span data-ttu-id="d55fa-249">有关更多详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="d55fa-249">For more details, see:</span></span> 
* [<span data-ttu-id="d55fa-250">将文件和注册表设置添加到映像</span><span class="sxs-lookup"><span data-stu-id="d55fa-250">Add a file and a registry setting to an image</span></span>](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [<span data-ttu-id="d55fa-251">Windows 10 IoT 核心版映像创建</span><span class="sxs-lookup"><span data-stu-id="d55fa-251">Windows 10 IoT Core Image Creation</span></span>](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a><span data-ttu-id="d55fa-252">启动 FTP 服务器</span><span class="sxs-lookup"><span data-stu-id="d55fa-252">Starting the FTP Server</span></span> 
<span data-ttu-id="d55fa-253">FTP 服务器无法再运行默认情况下在启动时</span><span class="sxs-lookup"><span data-stu-id="d55fa-253">The FTP Server no longer runs by default at start-up</span></span> 
<br>
<span data-ttu-id="d55fa-254">若要运行一次： 
`Login with SSH\PS`运行以下命令以启动 FTP:</span><span class="sxs-lookup"><span data-stu-id="d55fa-254">To run once: 
`Login with SSH\PS` Run this command to start FTP:</span></span>  
`start ftpd.exe` 
  
<span data-ttu-id="d55fa-255">若要在每次启动上运行用户应创建计划程序任务。</span><span class="sxs-lookup"><span data-stu-id="d55fa-255">To run on every boot users should create a scheduler task.</span></span> 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a><span data-ttu-id="d55fa-256">版权信息</span><span class="sxs-lookup"><span data-stu-id="d55fa-256">Copyright Information</span></span> 

<span data-ttu-id="d55fa-257">© Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d55fa-257">© Microsoft.</span></span> <span data-ttu-id="d55fa-258">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="d55fa-258">All rights reserved.</span></span> 
 
<span data-ttu-id="d55fa-259">本文档按原样提供。</span><span class="sxs-lookup"><span data-stu-id="d55fa-259">This document is provided “as-is”.</span></span><span data-ttu-id="d55fa-260">  在此文档中，包括 URL 和其他 Internet 网站引用表达信息和观点可能会更改恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="d55fa-260">  Information and views expressed in this document, including URL and other Internet Web site references may change without notice.</span></span> 

<span data-ttu-id="d55fa-261">此处所述的某些示例仅用于进行说明，是虚构的。</span><span class="sxs-lookup"><span data-stu-id="d55fa-261">Some examples depicted herein are provided for illustration only and are fictitious.</span></span><span data-ttu-id="d55fa-262">  不存在任何实际关联或联系，请勿妄加推断。</span><span class="sxs-lookup"><span data-stu-id="d55fa-262">  No real association or connection is intended or should be inferred.</span></span>  

<span data-ttu-id="d55fa-263">本文档不提供任何 Microsoft 产品中的任何知识产权的任何法律权利。</span><span class="sxs-lookup"><span data-stu-id="d55fa-263">This document does not provide any legal rights to any intellectual property in any Microsoft product.</span></span><span data-ttu-id="d55fa-264">  本文档可用于内部参考目的。</span><span class="sxs-lookup"><span data-stu-id="d55fa-264">  This document may be used for internal, references purposes.</span></span> 
  
<span data-ttu-id="d55fa-265">Microsoft 不做任何明示或暗示的担保。</span><span class="sxs-lookup"><span data-stu-id="d55fa-265">Microsoft makes no warranties, express or implied.</span></span>  

<span data-ttu-id="d55fa-266">请参阅 Microsoft 商标商标字产品的列表。</span><span class="sxs-lookup"><span data-stu-id="d55fa-266">Please refer to Microsoft Trademarks for a list of trademarked products.</span></span> 

<span data-ttu-id="d55fa-267">所有其他商标的所有权属于其各自所有者。</span><span class="sxs-lookup"><span data-stu-id="d55fa-267">All other trademarks are property of their respective owners.</span></span>  

<span data-ttu-id="d55fa-268">UPnP ™ 是 UPnP™ Implementers Corporation 的认证标记。</span><span class="sxs-lookup"><span data-stu-id="d55fa-268">UPnP™ is a certification mark of the UPnP™ Implementers Corporation.</span></span> 

<span data-ttu-id="d55fa-269">Bluetooth® 是蓝牙 SIG，inc.的商标美国并授权 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="d55fa-269">Bluetooth® is a trademark owned by Bluetooth SIG, Inc. USA and licensed to Microsoft Corporation.</span></span> 

<span data-ttu-id="d55fa-270">Intel 是 Intel Corporation 的注册的商标。</span><span class="sxs-lookup"><span data-stu-id="d55fa-270">Intel is a registered trademark of Intel Corporation.</span></span> 

<span data-ttu-id="d55fa-271">Itanium 是 Intel Corporation 的注册的商标。</span><span class="sxs-lookup"><span data-stu-id="d55fa-271">Itanium is a registered trademark of Intel Corporation.</span></span>
 
<span data-ttu-id="d55fa-272">此软件的部分基于 MCSA 马赛克，at Urbana-champaign 的伊利诺伊大学的超级计算技术应用程序开发的国家/地区中心，分发与 Spyglass，Inc.的许可协议</span><span class="sxs-lookup"><span data-stu-id="d55fa-272">Portions of this software are based on MCSA Mosaic, developed by the National Center for Supercomputing Applications at the University of Illinois at Urbana-Champaign, distributed under a licensing agreement with Spyglass, Inc.</span></span> 

<span data-ttu-id="d55fa-273">本产品包含由 RSA Data Security，Inc.授权的安全软件</span><span class="sxs-lookup"><span data-stu-id="d55fa-273">This product contains security software licensed from RSA Data Security, Inc.</span></span> 
