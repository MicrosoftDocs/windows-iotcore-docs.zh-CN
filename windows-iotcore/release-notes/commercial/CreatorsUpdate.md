---
title: 创意者更新-生成15063
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 阅读并了解创意者更新中的新增功能。
keywords: windows iot, 创意者更新, 发行说明
ms.openlocfilehash: a8b8fc93d8c079b1b57bbe18f48ea0bc7082dcbe
ms.sourcegitcommit: 38de3aad11845248dac393ffc51b18c5596af4c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68155394"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a><span data-ttu-id="06e9d-104">Windows 10 IoT Core 的创意者更新发行说明</span><span class="sxs-lookup"><span data-stu-id="06e9d-104">Creators Update Release Notes for Windows 10 IoT Core</span></span>
<span data-ttu-id="06e9d-105">内部版本号15063。</span><span class="sxs-lookup"><span data-stu-id="06e9d-105">Build Number 15063.</span></span> <span data-ttu-id="06e9d-106">2017 年 4 月</span><span class="sxs-lookup"><span data-stu-id="06e9d-106">April 2017</span></span>

<span data-ttu-id="06e9d-107">Windows 10 IoT Core 允许开发嵌入或专用设备, 并且是针对小型设备构建 Windows 解决方案的 Oem 和开发人员的选择。</span><span class="sxs-lookup"><span data-stu-id="06e9d-107">Windows 10 IoT Core enables development of embedded or dedicated-purpose devices and is the choice for the OEMs and developers building Windows solutions for small devices.</span></span>

<span data-ttu-id="06e9d-108">本文档提供的信息补充了此版本的 Windows 10 IoT Core 的其他内容和文档。</span><span class="sxs-lookup"><span data-stu-id="06e9d-108">This document provides information that supplements other content and documentation for this release of Windows 10 IoT Core.</span></span>

<span data-ttu-id="06e9d-109">此版本中的包包含在基于 Intel Atom 多少的 Minnowboard 最大平台上安装 Windows 10 IoT Core 所需的工具和组件、基于 ARM Cortex-a9 A7 的 Raspberry Pi 2, 以及基于 Qualcomm Dragonboard 400 系列的 410C Snapdragon款.</span><span class="sxs-lookup"><span data-stu-id="06e9d-109">The packages within this release contain tools and components needed to install Windows 10 IoT Core on Minnowboard Max platform based on Intel Atom processers, Raspberry Pi 2 based on ARM Cortex A7, and Dragonboard 410c based on Qualcomm Snapdragon 400 series processors.</span></span>   

<span data-ttu-id="06e9d-110">合作伙伴可以使用[其他平台和处理器](../../learn-about-hardware/SoCsAndCustomBoards.md)。</span><span class="sxs-lookup"><span data-stu-id="06e9d-110">[Other platforms and processors](../../learn-about-hardware/SoCsAndCustomBoards.md) may be available from partners.</span></span>

## <a name="privacy-statement"></a><span data-ttu-id="06e9d-111">隐私声明</span><span class="sxs-lookup"><span data-stu-id="06e9d-111">Privacy Statement</span></span>

<span data-ttu-id="06e9d-112">可在[此处](http://go.microsoft.com/fwlink/?LinkId=506737)查看此 Windows 操作系统版本的隐私声明。</span><span class="sxs-lookup"><span data-stu-id="06e9d-112">The privacy statement for this version of the Windows operating system can be viewed [here](http://go.microsoft.com/fwlink/?LinkId=506737).</span></span>

## <a name="whats-new"></a><span data-ttu-id="06e9d-113">新增功能</span><span class="sxs-lookup"><span data-stu-id="06e9d-113">What's New</span></span>
* <span data-ttu-id="06e9d-114">Windows 10 IoT Core 公有版。</span><span class="sxs-lookup"><span data-stu-id="06e9d-114">Windows 10 IoT Core Public Release.</span></span> 
   * <span data-ttu-id="06e9d-115">Azure 设备管理支持-Oem 可以使用 Windows IoT Azure DM 客户端库向其 Azure IoT 中心连接的设备添加设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="06e9d-115">Azure Device Management Support - OEMs can use the Windows IoT Azure DM client library to add device management capabilities to their Azure IoT hub connected devices.</span></span>
   * <span data-ttu-id="06e9d-116">额外硅支持</span><span class="sxs-lookup"><span data-stu-id="06e9d-116">Additional Silicon Support</span></span>
      * <span data-ttu-id="06e9d-117">验证了对 Intel Joule、Intel Pentium N4200、Intel 赛扬 N3350、即将发布的 Atom x5-E39xx 处理器 (以前称为 Apollo Lake) 和 Raspberry Pi 3 SOMs 的 Windows 10 IoT Core 的支持。</span><span class="sxs-lookup"><span data-stu-id="06e9d-117">Verified support for Windows 10 IoT Core on Intel Joule, Intel Pentium N4200, Intel Celeron N3350, upcoming Atom x5-E39xx processors (formerly Apollo Lake) and Raspberry Pi 3 SOMs.</span></span>
      * <span data-ttu-id="06e9d-118">Allwinner 已使用 Allwinner A64 SoC 为其松树64和香蕉 Pi 设备启用了支持。</span><span class="sxs-lookup"><span data-stu-id="06e9d-118">Allwinner has enabled support for their Pine 64 and Banana Pi devices using the Allwinner A64 SoC.</span></span> 
   * <span data-ttu-id="06e9d-119">发现你的远程设备-发现你的设备已登录到你的 Microsoft 帐户无需任何特殊软件。</span><span class="sxs-lookup"><span data-stu-id="06e9d-119">Discovering your Remote Devices - No special software is needed to discover your devices that are signed in with your Microsoft Account.</span></span>
   * <span data-ttu-id="06e9d-120">新的 UWP Api 和控件, 适用于振动、亮度、新式连接待机、电源管理、电池电量和 NFC (w/o HCE)。</span><span class="sxs-lookup"><span data-stu-id="06e9d-120">New UWP APIs And controls for vibration, brightness, modern connected standby, power management, battery charge  and NFC (w/o HCE).</span></span> 
   * <span data-ttu-id="06e9d-121">ARM PCIe、USB 功能模式、Wi-fi Direct 和 GPIO 中断计数 API 的新总线和功能。</span><span class="sxs-lookup"><span data-stu-id="06e9d-121">New busses and capabilities for ARM PCIe, USB function mode, Wi-Fi Direct and  GPIO interrupt counting API.</span></span> 
   * <span data-ttu-id="06e9d-122">重置/恢复上的新嵌入功能, On SOC PWM 和自动 USB 预配</span><span class="sxs-lookup"><span data-stu-id="06e9d-122">New Embedded features on Reset/Recovery, On-SOC PWM and Automatic USB provisioning</span></span> 
   * <span data-ttu-id="06e9d-123">改进的工具-VS Code、新的 Windows 设备门户和 IoT 面板功能, VS 2017 支持。</span><span class="sxs-lookup"><span data-stu-id="06e9d-123">Improved Tools - VS Code, New Windows Device Portal and IoT Dashboard features, VS 2017 support.</span></span>
   * <span data-ttu-id="06e9d-124">Windows IoT Core 上的 cortana-Cortana 现在在 Windows 10 IoT Core 上可用。</span><span class="sxs-lookup"><span data-stu-id="06e9d-124">Cortana on Windows IoT Core - Cortana is now available on Windows 10 IoT Core.</span></span> <span data-ttu-id="06e9d-125">向 Cortana 询问一个问题。</span><span class="sxs-lookup"><span data-stu-id="06e9d-125">Ask Cortana a question.</span></span>
   * <span data-ttu-id="06e9d-126">IoT 面板改进-新增功能和稳定性错误修复</span><span class="sxs-lookup"><span data-stu-id="06e9d-126">IoT Dashboard Improvements - New features and stability bug fixes</span></span>
      * <span data-ttu-id="06e9d-127">适用于 Raspberry Pi 和 Minnowboard 的 Windows 预览体验版预览版</span><span class="sxs-lookup"><span data-stu-id="06e9d-127">Windows Insider Preview builds for Raspberry Pi and Minnowboard</span></span> 
      * <span data-ttu-id="06e9d-128">使用 Windows IoT 远程客户端连接设备</span><span class="sxs-lookup"><span data-stu-id="06e9d-128">Connecting device using Windows IoT Remote Client</span></span> 
      * <span data-ttu-id="06e9d-129">发现设备中的 Ipv6 地址</span><span class="sxs-lookup"><span data-stu-id="06e9d-129">Ipv6 addresses in discovering devices</span></span> 
      * <span data-ttu-id="06e9d-130">提交反馈时上载设备日志</span><span class="sxs-lookup"><span data-stu-id="06e9d-130">Uploading device logs while submitting feedback</span></span>
   *  <span data-ttu-id="06e9d-131">新的高精度 GPIO Api-新 Api (GpioInterruptBuffer), 用于使用 GPIO 中断准确有效地测量脉冲宽度。</span><span class="sxs-lookup"><span data-stu-id="06e9d-131">New high precision GPIO APIs -  New APIs (Windows.Devices.Gpio.GpioInterruptBuffer) for precise and efficient measurement of pulse widths using GPIO interrupts.</span></span><span data-ttu-id="06e9d-132">  GPIO 提供程序包括新的中断缓冲接口, 以允许应用程序 (如旋转编码器和距离测量设备) 的高精度中断计时</span><span class="sxs-lookup"><span data-stu-id="06e9d-132">  GPIO providers include new Interrupt Buffer interface to allow for high precision interrupt timing for applications like rotary encoders and distance measuring devices</span></span>
   * <span data-ttu-id="06e9d-133">Device Guard for IoT-设备构建者现在可以完全锁定 IoT 设备, 并针对新的未知恶意软件变种获取高级恶意软件防护。</span><span class="sxs-lookup"><span data-stu-id="06e9d-133">Device Guard for IoT - Device builders can now fully lock down IoT devices and get advanced malware protection against new and unknown malware variants.</span></span><span data-ttu-id="06e9d-134">  为此, 可以为在设备上运行的允许的应用程序和驱动程序指定签名颁发机构, 同时禁止执行未知或不受信任的代码。</span><span class="sxs-lookup"><span data-stu-id="06e9d-134">  This can be done by specifying signing authorities for permissible applications and drivers that run on the device while disallowing execution of unknown or untrusted code.</span></span><span data-ttu-id="06e9d-135">  这意味着提高了对恶意软件和零天攻击的安全性。</span><span class="sxs-lookup"><span data-stu-id="06e9d-135">  This means improved security against malware and zero day attacks.</span></span> 
   * <span data-ttu-id="06e9d-136">其他更新包括:</span><span class="sxs-lookup"><span data-stu-id="06e9d-136">Other updates include:</span></span> 
      * <span data-ttu-id="06e9d-137">改进了更新支持</span><span class="sxs-lookup"><span data-stu-id="06e9d-137">Improved Update Support</span></span> 
      * <span data-ttu-id="06e9d-138">Azure 网关 SDK 支持</span><span class="sxs-lookup"><span data-stu-id="06e9d-138">Azure Gateway SDK support</span></span> 
      * <span data-ttu-id="06e9d-139">基于 USB 驱动器的自动预配</span><span class="sxs-lookup"><span data-stu-id="06e9d-139">USB drive based auto-provisioning</span></span> 
      * <span data-ttu-id="06e9d-140">设备门户重新设计</span><span class="sxs-lookup"><span data-stu-id="06e9d-140">Device Portal redesign</span></span> 
      * <span data-ttu-id="06e9d-141">64位映像现在最多支持 16384 MB 的内存</span><span class="sxs-lookup"><span data-stu-id="06e9d-141">64-bit images now supports up to 16,384 MB of memory</span></span> 
      * <span data-ttu-id="06e9d-142">WinRT 振动 Api</span><span class="sxs-lookup"><span data-stu-id="06e9d-142">WinRT Vibration APIs</span></span> 
      * <span data-ttu-id="06e9d-143">改进的语言支持</span><span class="sxs-lookup"><span data-stu-id="06e9d-143">Improved language support</span></span> 
   * <span data-ttu-id="06e9d-144">其他</span><span class="sxs-lookup"><span data-stu-id="06e9d-144">Miscellaneous</span></span>  
      * <span data-ttu-id="06e9d-145">已对默认的 BCD 设置进行了更改, 以防止设备在恢复模式不存在时尝试启动到恢复模式。</span><span class="sxs-lookup"><span data-stu-id="06e9d-145">A change has been made to the default BCD settings to prevent devices from attempting to boot to recovery mode when recovery mode does not exist.</span></span> 
      * <span data-ttu-id="06e9d-146">IOT_POWER_SETTINGS 功能现在包含 powercfg。</span><span class="sxs-lookup"><span data-stu-id="06e9d-146">IOT_POWER_SETTINGS feature now includes powercfg.exe.</span></span> <span data-ttu-id="06e9d-147">这适用于所有体系结构 (ARM32、x86 和 x64)。</span><span class="sxs-lookup"><span data-stu-id="06e9d-147">This is available for all architectures (ARM32, x86 and x64).</span></span> 
      * <span data-ttu-id="06e9d-148">对 Applyupdate 进行了更改以添加 blockrebooton/blockrebootoff 标志</span><span class="sxs-lookup"><span data-stu-id="06e9d-148">Changes were made to Applyupdate.exe to add the blockrebooton/blockrebootoff flags</span></span> 
      * <span data-ttu-id="06e9d-149">已将硬件通知 (hwnclx) 和 USB 函数 (usbfnclx) 的类扩展添加到默认 IoT Core 映像</span><span class="sxs-lookup"><span data-stu-id="06e9d-149">The Class Extensions for Hardware Notification (hwnclx) and USB Function (usbfnclx) have been added to the default IoT Core images</span></span>

## <a name="known-issues"></a><span data-ttu-id="06e9d-150">已知问题</span><span class="sxs-lookup"><span data-stu-id="06e9d-150">Known Issues</span></span>

### <a name="raspberry-pi"></a><span data-ttu-id="06e9d-151">Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="06e9d-151">Raspberry Pi</span></span>  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a><span data-ttu-id="06e9d-152">Raspberry Pi 显示器分辨率（在监视器断开连接的情况下）</span><span class="sxs-lookup"><span data-stu-id="06e9d-152">Raspberry Pi Display Resolution if monitor is disconnected</span></span> 
<span data-ttu-id="06e9d-153">在监视器断开连接的情况下，Raspberry Pi 可能无法保持显示器分辨率。</span><span class="sxs-lookup"><span data-stu-id="06e9d-153">The Raspberry Pi may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="06e9d-154">监视器的 EDID 用于在连接到系统时设置系统的分辨率。  </span><span class="sxs-lookup"><span data-stu-id="06e9d-154">The EDID of the monitor is used to set the resolution of the system when one is connected.  </span></span>
<span data-ttu-id="06e9d-155">断开连接时，Raspberry Pi 固件默认设置为 SD 卡根目录的 config.txt 中的值。</span><span class="sxs-lookup"><span data-stu-id="06e9d-155">When disconnected, the Raspberry Pi firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 

#### <a name="raspberry-pi-video-performance"></a><span data-ttu-id="06e9d-156">Raspberry Pi 视频性能</span><span class="sxs-lookup"><span data-stu-id="06e9d-156">Raspberry Pi Video Performance</span></span> 
<span data-ttu-id="06e9d-157">Raspberry Pi 平台上的视频播放性能尚未进行优化。</span><span class="sxs-lookup"><span data-stu-id="06e9d-157">Video playback performance on the Raspberry Pi platform has not been optimized.</span></span><span data-ttu-id="06e9d-158">  动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。</span><span class="sxs-lookup"><span data-stu-id="06e9d-158">  Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span> 

#### <a name="raspberry-pi-camera-support"></a><span data-ttu-id="06e9d-159">Raspberry Pi 相机支持</span><span class="sxs-lookup"><span data-stu-id="06e9d-159">Raspberry Pi Camera Support</span></span> 
<span data-ttu-id="06e9d-160">Windows 10 IoT 核心支持, 适用于 Raspberry Pi 设备的相机外设设备受到限制。</span><span class="sxs-lookup"><span data-stu-id="06e9d-160">Windows 10 IoT Core support for camera peripheral devices with Raspberry Pi devices is limited.</span></span> <span data-ttu-id="06e9d-161">当前不支持直接连接到板载相机总线的 PiCam 设备, 因为它需要在 Raspberry Pi 上当前不可用的 GPU 服务, 因为未实现 DirectX 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="06e9d-161">The PiCam device directly connected to the onboard camera bus is not currently supported, as it requires GPU services that are not currently available on the Raspberry Pi because the DirectX driver is not implemented.</span></span> <span data-ttu-id="06e9d-162">现代 USB 摄像头可在 USB 主控制器上生成要求极度严苛的数据流。</span><span class="sxs-lookup"><span data-stu-id="06e9d-162">Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span><span data-ttu-id="06e9d-163">  即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。</span><span class="sxs-lookup"><span data-stu-id="06e9d-163">  Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  

#### <a name="raspberry-pi-3-bluetooth-support"></a><span data-ttu-id="06e9d-164">Raspberry Pi 3 蓝牙支持</span><span class="sxs-lookup"><span data-stu-id="06e9d-164">Raspberry Pi 3 Bluetooth support</span></span> 
<span data-ttu-id="06e9d-165">Raspberry Pi3 内置蓝牙驱动程序仅支持低带宽设备</span><span class="sxs-lookup"><span data-stu-id="06e9d-165">The Raspberry Pi3 built-in Bluetooth driver only supports low bandwidth devices</span></span>  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a><span data-ttu-id="06e9d-166">Raspberry Pi 2 上的串行端口使用和访问</span><span class="sxs-lookup"><span data-stu-id="06e9d-166">Serial Port Usage and Access on Raspberry Pi 2</span></span> 
<span data-ttu-id="06e9d-167">Raspberry Pi 2 支持通过 PL011 UART 串行传输通信。</span><span class="sxs-lookup"><span data-stu-id="06e9d-167">Raspberry Pi 2 supports the serial transport for communication through the PL011 UART.</span></span><span data-ttu-id="06e9d-168">  这是内核调试方案中的默认设置。</span><span class="sxs-lookup"><span data-stu-id="06e9d-168">  This is set by default in kernel debugging scenarios.</span></span><span data-ttu-id="06e9d-169">  通过使用以下命令, 应用程序或设备驱动程序可以使用 PL011 UART 来发送和接收数据, 并使用 PL011 设备驱动程序关闭调试器:   
`bcedit /set debug off`</span><span class="sxs-lookup"><span data-stu-id="06e9d-169">  An application or device driver can use the PL011 UART to send and receive data with the PL011 device driver turning off the debugger using the following command:   
`bcedit /set debug off`</span></span> 
 
### <a name="dragon-board"></a><span data-ttu-id="06e9d-170">龙板</span><span class="sxs-lookup"><span data-stu-id="06e9d-170">Dragon Board</span></span> 

#### <a name="dragonboard-410c-shutdown"></a><span data-ttu-id="06e9d-171">Dragonboard 410c 关机</span><span class="sxs-lookup"><span data-stu-id="06e9d-171">Dragonboard 410c Shutdown</span></span> 
<span data-ttu-id="06e9d-172">在 DragonBoard 上，关机命令不会关闭开发板电源。</span><span class="sxs-lookup"><span data-stu-id="06e9d-172">On the DragonBoard, a shutdown command will not power off the board.</span></span> <span data-ttu-id="06e9d-173">系统将会重新启动。</span><span class="sxs-lookup"><span data-stu-id="06e9d-173">The system will restart.</span></span> <span data-ttu-id="06e9d-174">请通过断开电源连接来关闭开发板电源。</span><span class="sxs-lookup"><span data-stu-id="06e9d-174">Please power off the board by disconnecting the power.</span></span> 

#### <a name="dragon-board-headset--microphone-jack"></a><span data-ttu-id="06e9d-175">Dragon Board 耳机和麦克风插孔</span><span class="sxs-lookup"><span data-stu-id="06e9d-175">Dragon Board headset & microphone jack</span></span>  
<span data-ttu-id="06e9d-176">Dragonboard BSP 具有耳机插孔和麦克风插孔的驱动程序，但它在开发板上没有这两种插孔。</span><span class="sxs-lookup"><span data-stu-id="06e9d-176">The Dragonboard BSP has drivers for the headset jack and microphone jack, but it doesn't have either of these jacks on board.</span></span>  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a><span data-ttu-id="06e9d-177">Dragonboard SPI 以 lock 速度运行</span><span class="sxs-lookup"><span data-stu-id="06e9d-177">Dragonboard SPI runs at lock speed</span></span>  
<span data-ttu-id="06e9d-178">Dragonboard 上的 SPI 将忽略请求的速度, 并始终以预配置的速度运行。</span><span class="sxs-lookup"><span data-stu-id="06e9d-178">The SPI on the Dragonboard will ignore the requested speed and always run at a preconfigured speed.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="06e9d-179">Dragonboard 连接待机</span><span class="sxs-lookup"><span data-stu-id="06e9d-179">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="06e9d-180">默认情况下，连接待机在 Qualcomm Dragonboard 上未启用。</span><span class="sxs-lookup"><span data-stu-id="06e9d-180">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span><span data-ttu-id="06e9d-181">  若要在 DragonBoard 上启用连接备用, 需要将以下注册表项设置为 "1" 
</span><span class="sxs-lookup"><span data-stu-id="06e9d-181">  To enable Connected Standby on DragonBoard the following registry key needs to be set to “1” 
</span></span><br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
<span data-ttu-id="06e9d-182">请注意, 并非所有平台都支持 CS, 因此这可能在其他平台上不起作用。</span><span class="sxs-lookup"><span data-stu-id="06e9d-182">Note that not all platforms have support for CS, so this may not work on other platforms.</span></span>    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a><span data-ttu-id="06e9d-183">振动 API 在某些 Qualcomm 平台上可能不起作用</span><span class="sxs-lookup"><span data-stu-id="06e9d-183">Vibration API may not function on some Qualcomm platforms</span></span> 
<span data-ttu-id="06e9d-184">建议的解决方法是添加以下注册表项: 
</span><span class="sxs-lookup"><span data-stu-id="06e9d-184">The suggested workaround is to add the following registry key: 
</span></span><br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
<span data-ttu-id="06e9d-185">对于使用 SSH 或 PowerShell 进行的现有映像连接确认/验证, 请运行以下命令: 
</span><span class="sxs-lookup"><span data-stu-id="06e9d-185">For confirmation / verification on an existing image connect with SSH or PowerShell and run the following command: 
</span></span><br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a><span data-ttu-id="06e9d-186">MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="06e9d-186">MinnowBoard</span></span>  

#### <a name="minnowboard-max-firmware-update"></a><span data-ttu-id="06e9d-187">Minnowboard 最大固件更新</span><span class="sxs-lookup"><span data-stu-id="06e9d-187">Minnowboard Max Firmware Update</span></span> 
<span data-ttu-id="06e9d-188">除非固件为092或更高版本, 否则不会启动 MinnowBoard Max。  </span><span class="sxs-lookup"><span data-stu-id="06e9d-188">The MinnowBoard Max will not boot unless the firmware is version .092 or later.  </span></span>
<span data-ttu-id="06e9d-189">MinnowBoard Max (MBM) 固件版本0.93 可能存在网络连接故障。</span><span class="sxs-lookup"><span data-stu-id="06e9d-189">There may be network connectivity failures in MinnowBoard Max (MBM) firmware version 0.93.</span></span><span data-ttu-id="06e9d-190">   此问题已在固件版本0.94 中解决。) 最小建议固件版本为 "MinnowBoard MAX 0.94 32-bit"。</span><span class="sxs-lookup"><span data-stu-id="06e9d-190">   The issue is fixed in firmware version 0.94.)  The minimum recommended version of the firmware is “MinnowBoard MAX 0.94 32-bit”.</span></span> <span data-ttu-id="06e9d-191">可从 [此处](http://go.microsoft.com/fwlink/?LinkId=708613)下载固件更新。</span><span class="sxs-lookup"><span data-stu-id="06e9d-191">Firmware updates can be downloaded from [here](http://go.microsoft.com/fwlink/?LinkId=708613).</span></span>
  
 
### <a name="all-platforms"></a><span data-ttu-id="06e9d-192">所有平台</span><span class="sxs-lookup"><span data-stu-id="06e9d-192">All Platforms</span></span> 

#### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="06e9d-193">调试时鼠标指针消失</span><span class="sxs-lookup"><span data-stu-id="06e9d-193">Mouse Pointer disappears while debugging</span></span> 
<span data-ttu-id="06e9d-194">在某些情况下, 在使用 Visual Studio 部署或调试应用程序后不会显示鼠标指针, 如果使用键盘 (选项卡) 更改焦点, 则会重新显示鼠标指针</span><span class="sxs-lookup"><span data-stu-id="06e9d-194">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab)</span></span>  

#### <a name="server-applications-with-softap"></a><span data-ttu-id="06e9d-195">服务器应用程序与 SoftAP</span><span class="sxs-lookup"><span data-stu-id="06e9d-195">Server Applications with SoftAP</span></span>  
<span data-ttu-id="06e9d-196">使用 SoftAP 客户端时, 客户端将无法访问 UAP 应用公开的内容。  </span><span class="sxs-lookup"><span data-stu-id="06e9d-196">When using the SoftAP clients will not be able to access content exposed by UAP apps.  </span></span>
<span data-ttu-id="06e9d-197">若要通过 SoftAP 公开 UAP 应用程序, 必须从设备上的控制台进行以下更改:  
</span><span class="sxs-lookup"><span data-stu-id="06e9d-197">To expose UAP applications via SoftAP the following changes must be made from the console on the device :  
</span></span><br>
`reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 `
<br>
`checknetisolation loopbackexempt -a -n=<AppID for SoftAP App>`
<br>
`checknetisolation loopbackexempt -a -n=<AppID for Additional App> `
<br>
`For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym`
<br>
`Reboot`

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="06e9d-198">在预先构建的 FFU 中出现传感器驱动程序冲突</span><span class="sxs-lookup"><span data-stu-id="06e9d-198">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="06e9d-199">在提供的 FFU 中存在传感器驱动程序冲突。</span><span class="sxs-lookup"><span data-stu-id="06e9d-199">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="06e9d-200">Remote Sensor Framework 可为指南针、磁力计、加速计和陀螺仪安装驱动程序。</span><span class="sxs-lookup"><span data-stu-id="06e9d-200">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="06e9d-201">从应用程序访问这些项目的 UWP API 会假定只安装了其中 1 项。</span><span class="sxs-lookup"><span data-stu-id="06e9d-201">The UWP APIs for accessing these from an application assume just 1 is installed.</span></span> <span data-ttu-id="06e9d-202">如果要开发用于物理连接的设备的驱动程序, Microsoft 提供的 FFUs 上的远程驱动程序将发生冲突。  </span><span class="sxs-lookup"><span data-stu-id="06e9d-202">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.  </span></span>
<span data-ttu-id="06e9d-203">解决方案：通过 SSH 或 PowerShell 连接到设备, 并通过键入 "ROOT\REMOTESENSORDRIVER" 删除 @ "\*" 来删除远程传感器驱动程序, 可以删除冲突的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="06e9d-203">Resolution: The conflicting driver can be removed by connecting to the device via SSH or PowerShell and using the tool devcon.exe to remove the remote sensor driver by typing “devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*”.</span></span> <span data-ttu-id="06e9d-204">远程传感器驱动程序不影响 OEM 创建的 FFU。</span><span class="sxs-lookup"><span data-stu-id="06e9d-204">The remote sensor driver does not affect OEM created FFUs.</span></span> 
 
#### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="06e9d-205">默认管理员用户名和密码</span><span class="sxs-lookup"><span data-stu-id="06e9d-205">Default Administrator User Name and Password</span></span> 
<span data-ttu-id="06e9d-206">默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。</span><span class="sxs-lookup"><span data-stu-id="06e9d-206">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="06e9d-207">这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。</span><span class="sxs-lookup"><span data-stu-id="06e9d-207">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 
 
#### <a name="volume-controls"></a><span data-ttu-id="06e9d-208">音量控件</span><span class="sxs-lookup"><span data-stu-id="06e9d-208">Volume Controls</span></span> 
<span data-ttu-id="06e9d-209">依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。</span><span class="sxs-lookup"><span data-stu-id="06e9d-209">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 
 
#### <a name="usb-keyboards"></a><span data-ttu-id="06e9d-210">USB 键盘</span><span class="sxs-lookup"><span data-stu-id="06e9d-210">USB Keyboards</span></span>  
<span data-ttu-id="06e9d-211">某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。</span><span class="sxs-lookup"><span data-stu-id="06e9d-211">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="06e9d-212">使用其他键盘或鼠标。</span><span class="sxs-lookup"><span data-stu-id="06e9d-212">Use a different keyboard or mouse.</span></span> <span data-ttu-id="06e9d-213">可在[此处](../../learn-about-hardware/HardwareCompatList.md)找到已验证的外围设备的列表。</span><span class="sxs-lookup"><span data-stu-id="06e9d-213">A list of validated peripheral devices can be found [here](../../learn-about-hardware/HardwareCompatList.md).</span></span>  
 
#### <a name="screen-orientation"></a><span data-ttu-id="06e9d-214">屏幕方向</span><span class="sxs-lookup"><span data-stu-id="06e9d-214">Screen Orientation</span></span> 
<span data-ttu-id="06e9d-215">在通用应用中将方向设置为 "纵向" 可能不起作用</span><span class="sxs-lookup"><span data-stu-id="06e9d-215">Setting the orientation to “Portrait” may not be honored in a Universal App</span></span> 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="06e9d-216">使用 AllJoyn 模板引用适配器</span><span class="sxs-lookup"><span data-stu-id="06e9d-216">Referencing Adapters with AllJoyn Templates</span></span> 
<span data-ttu-id="06e9d-217">尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。</span><span class="sxs-lookup"><span data-stu-id="06e9d-217">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span><span data-ttu-id="06e9d-218">  若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。</span><span class="sxs-lookup"><span data-stu-id="06e9d-218">  To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span> 

#### <a name="non-default-drive-mode"></a><span data-ttu-id="06e9d-219">非默认驱动器模式</span><span class="sxs-lookup"><span data-stu-id="06e9d-219">Non-default drive mode</span></span>  
<span data-ttu-id="06e9d-220">在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。</span><span class="sxs-lookup"><span data-stu-id="06e9d-220">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="06e9d-221">解决方法：在应用程序开端处设置一次驱动器模式。</span><span class="sxs-lookup"><span data-stu-id="06e9d-221">WORKAROUND: Set drive mode once at the beginning of the application.</span></span> 
 
#### <a name="application-already-running"></a><span data-ttu-id="06e9d-222">已处于运行状态的应用程序</span><span class="sxs-lookup"><span data-stu-id="06e9d-222">Application already running</span></span>  
<span data-ttu-id="06e9d-223">如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。</span><span class="sxs-lookup"><span data-stu-id="06e9d-223">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="06e9d-224">解决方法：将默认启动应用更改为不希望部署的应用程序。</span><span class="sxs-lookup"><span data-stu-id="06e9d-224">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a><span data-ttu-id="06e9d-225">BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃</span><span class="sxs-lookup"><span data-stu-id="06e9d-225">BackgroundMediaPlayer.MessageReceivedFromForeground may crash</span></span>  
<span data-ttu-id="06e9d-226">以下代码行可能会崩溃: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`。</span><span class="sxs-lookup"><span data-stu-id="06e9d-226">The following line of code may crash: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`.</span></span>
<br>
<span data-ttu-id="06e9d-227">若要防止发生崩溃, 请添加以下代码, 使其首先执行`var player = BackgroundMediaPlayer.Current;`</span><span class="sxs-lookup"><span data-stu-id="06e9d-227">To prevent the crash, add this code so that it is executed first `var player = BackgroundMediaPlayer.Current;`</span></span> 
 
#### <a name="azure-active-directory-authentication-support"></a><span data-ttu-id="06e9d-228">Azure Active Directory 身份验证支持</span><span class="sxs-lookup"><span data-stu-id="06e9d-228">Azure Active Directory Authentication Support</span></span>  
<span data-ttu-id="06e9d-229">Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。</span><span class="sxs-lookup"><span data-stu-id="06e9d-229">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  
 
#### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="06e9d-230">应用程序崩溃的 Shell 管理</span><span class="sxs-lookup"><span data-stu-id="06e9d-230">Shell Management of Application Crashes</span></span> 
<span data-ttu-id="06e9d-231">IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="06e9d-231">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span><span data-ttu-id="06e9d-232">  如果重新启动的应用程序仍然崩溃, shell 将使用 __failfast –导致错误检查的系统关键过程, 并在尝试恢复时重新启动。</span><span class="sxs-lookup"><span data-stu-id="06e9d-232">  If the restarted applications continue to crash, the shell will employ a __failfast – a system critical process that causes a bug check and reboot in an attempt to recover.</span></span><span data-ttu-id="06e9d-233">  可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="06e9d-233">  Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   

<span data-ttu-id="06e9d-234">下面捕获的是崩溃处理和重试逻辑：</span><span class="sxs-lookup"><span data-stu-id="06e9d-234">Crash handing and retry logic is captured below:</span></span> 

<span data-ttu-id="06e9d-235">Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig (或 ForegroundAppConfig)</span><span class="sxs-lookup"><span data-stu-id="06e9d-235">Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed)</span></span> 
* <span data-ttu-id="06e9d-236">Qword: "FailureResetIntervalMs" –应用必须成功运行的时间长度, 才能将出现的故障重置为0。</span><span class="sxs-lookup"><span data-stu-id="06e9d-236">Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0.</span></span> <span data-ttu-id="06e9d-237">–默认值为 0x00000000000493E0 = = 5 分钟。</span><span class="sxs-lookup"><span data-stu-id="06e9d-237">– default is 0x00000000000493E0 == 5 minutes.</span></span> 
* <span data-ttu-id="06e9d-238">Qword: "BaseRetryDelayMs"--等待时间系数。</span><span class="sxs-lookup"><span data-stu-id="06e9d-238">Qword:"BaseRetryDelayMs"  -- wait time coefficient.</span></span><span data-ttu-id="06e9d-239">  默认值为 0xa。</span><span class="sxs-lookup"><span data-stu-id="06e9d-239">  Default is 0xa.</span></span>
* <span data-ttu-id="06e9d-240">Dword:"MaxFailureCount"。</span><span class="sxs-lookup"><span data-stu-id="06e9d-240">Dword:"MaxFailureCount".</span></span> <span data-ttu-id="06e9d-241">默认值为10。</span><span class="sxs-lookup"><span data-stu-id="06e9d-241">Default is 10.</span></span>
* <span data-ttu-id="06e9d-242">DWord:"FallbackExponentNumerator"，默认值为 31。</span><span class="sxs-lookup"><span data-stu-id="06e9d-242">DWord:"FallbackExponentNumerator", default is 31.</span></span>
* <span data-ttu-id="06e9d-243">Dword: "FallbackExponentDenominator", 默认值为20。</span><span class="sxs-lookup"><span data-stu-id="06e9d-243">Dword:"FallbackExponentDenominator", default is 20.</span></span>
 
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
 
#### <a name="time-synchronization"></a><span data-ttu-id="06e9d-244">时间同步</span><span class="sxs-lookup"><span data-stu-id="06e9d-244">Time Synchronization</span></span>  
<span data-ttu-id="06e9d-245">如果时间同步失败或超时，可能是因为时间服务器无法访问或过于遥远，可以通过以下操作来添加额外的或本地的时间服务器。</span><span class="sxs-lookup"><span data-stu-id="06e9d-245">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
* <span data-ttu-id="06e9d-246">在设备的命令行（例如</span><span class="sxs-lookup"><span data-stu-id="06e9d-246">From a command line on the device (eg.</span></span> <span data-ttu-id="06e9d-247">SSH, PowerShell)  w32tm/config/syncfromflags: manual/manualpeerlist: "1.pool.ntp.org 2. 其他 ..."</span><span class="sxs-lookup"><span data-stu-id="06e9d-247">SSH, PowerShell)  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span></span> 
* <span data-ttu-id="06e9d-248">如果需要, 还可以通过启动脚本或作为映像创建过程的一部分包含的自定义运行时配置包, 将这些添加到注册表中。 </span><span class="sxs-lookup"><span data-stu-id="06e9d-248">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed. </span></span>
<span data-ttu-id="06e9d-249">有关更多详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="06e9d-249">For more details, see:</span></span> 
* <span data-ttu-id="06e9d-250">[向映像添加文件和注册表设置](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="06e9d-250">[Add a file and a registry setting to an image](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)</span></span>
* [<span data-ttu-id="06e9d-251">Windows 10 IoT Core 映像创建</span><span class="sxs-lookup"><span data-stu-id="06e9d-251">Windows 10 IoT Core Image Creation</span></span>](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a><span data-ttu-id="06e9d-252">启动 FTP 服务器</span><span class="sxs-lookup"><span data-stu-id="06e9d-252">Starting the FTP Server</span></span> 
<span data-ttu-id="06e9d-253">默认情况下, 在启动时, FTP 服务器不再运行 
</span><span class="sxs-lookup"><span data-stu-id="06e9d-253">The FTP Server no longer runs by default at start-up 
</span></span><br>
<span data-ttu-id="06e9d-254">运行一次: 
`Login with SSH\PS`运行以下命令以启动 FTP:  
 `start ftpd.exe`    </span><span class="sxs-lookup"><span data-stu-id="06e9d-254">To run once: 
`Login with SSH\PS` Run this command to start FTP:  
`start ftpd.exe`    </span></span>
<span data-ttu-id="06e9d-255">若要在每个启动用户上运行, 应创建计划程序任务。</span><span class="sxs-lookup"><span data-stu-id="06e9d-255">To run on every boot users should create a scheduler task.</span></span> 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a><span data-ttu-id="06e9d-256">版权信息</span><span class="sxs-lookup"><span data-stu-id="06e9d-256">Copyright Information</span></span> 

<span data-ttu-id="06e9d-257">© Microsoft。</span><span class="sxs-lookup"><span data-stu-id="06e9d-257">© Microsoft.</span></span> <span data-ttu-id="06e9d-258">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="06e9d-258">All rights reserved.</span></span> 
 
<span data-ttu-id="06e9d-259">本文档按原样提供。</span><span class="sxs-lookup"><span data-stu-id="06e9d-259">This document is provided “as-is”.</span></span><span data-ttu-id="06e9d-260">  本文档中表达的信息和视图 (包括 URL 和其他 Internet 网站引用) 可能会更改, 恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="06e9d-260">  Information and views expressed in this document, including URL and other Internet Web site references may change without notice.</span></span> 

<span data-ttu-id="06e9d-261">此处所述的某些示例仅用于进行说明，是虚构的。</span><span class="sxs-lookup"><span data-stu-id="06e9d-261">Some examples depicted herein are provided for illustration only and are fictitious.</span></span><span data-ttu-id="06e9d-262">  不存在任何实际关联或联系，请勿妄加推断。</span><span class="sxs-lookup"><span data-stu-id="06e9d-262">  No real association or connection is intended or should be inferred.</span></span>  

<span data-ttu-id="06e9d-263">本文档不提供任何 Microsoft 产品中任何知识产权的任何法律权利。</span><span class="sxs-lookup"><span data-stu-id="06e9d-263">This document does not provide any legal rights to any intellectual property in any Microsoft product.</span></span><span data-ttu-id="06e9d-264">  本文档可用于内部、参考目的。</span><span class="sxs-lookup"><span data-stu-id="06e9d-264">  This document may be used for internal, references purposes.</span></span> 
  
<span data-ttu-id="06e9d-265">Microsoft 不作任何明示或默示的保证。</span><span class="sxs-lookup"><span data-stu-id="06e9d-265">Microsoft makes no warranties, express or implied.</span></span>  

<span data-ttu-id="06e9d-266">有关商标字产品的列表, 请参阅 Microsoft 商标。</span><span class="sxs-lookup"><span data-stu-id="06e9d-266">Please refer to Microsoft Trademarks for a list of trademarked products.</span></span> 

<span data-ttu-id="06e9d-267">所有其他商标的所有权属于其各自所有者。</span><span class="sxs-lookup"><span data-stu-id="06e9d-267">All other trademarks are property of their respective owners.</span></span>  

<span data-ttu-id="06e9d-268">UPnP ™ 是 UPnP™ Implementers Corporation 的认证标记。</span><span class="sxs-lookup"><span data-stu-id="06e9d-268">UPnP™ is a certification mark of the UPnP™ Implementers Corporation.</span></span> 

<span data-ttu-id="06e9d-269">蓝牙®是由蓝牙 SIG, Inc. 拥有的商标。美国和授权给 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="06e9d-269">Bluetooth® is a trademark owned by Bluetooth SIG, Inc. USA and licensed to Microsoft Corporation.</span></span> 

<span data-ttu-id="06e9d-270">Intel 是 Intel Corporation 的注册商标。</span><span class="sxs-lookup"><span data-stu-id="06e9d-270">Intel is a registered trademark of Intel Corporation.</span></span> 

<span data-ttu-id="06e9d-271">Itanium 是 Intel Corporation 的注册商标。</span><span class="sxs-lookup"><span data-stu-id="06e9d-271">Itanium is a registered trademark of Intel Corporation.</span></span>
 
<span data-ttu-id="06e9d-272">本软件的某些部分基于 MCSA 马赛克, 由美国大学伊利诺斯州大学的超级计算中心应用程序开发, 由美国应用程序开发, 并按与 Urbana-champaign, Inc. 的许可协议一起分发。</span><span class="sxs-lookup"><span data-stu-id="06e9d-272">Portions of this software are based on MCSA Mosaic, developed by the National Center for Supercomputing Applications at the University of Illinois at Urbana-Champaign, distributed under a licensing agreement with Spyglass, Inc.</span></span> 

<span data-ttu-id="06e9d-273">此产品包含的安全软件是从 RSA Data Security, Inc. 授权的。</span><span class="sxs-lookup"><span data-stu-id="06e9d-273">This product contains security software licensed from RSA Data Security, Inc.</span></span> 
