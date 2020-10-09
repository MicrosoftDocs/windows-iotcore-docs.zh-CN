---
title: Creators Update - 版本 15063
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 阅读并了解 Creators Update 的新增内容（内部版本号 15063，2017 年 4 月）。 另请查看已知问题列表。
keywords: Windows IoT, Creators Update, 发行说明
ms.openlocfilehash: 0650bcbfdb84ead3c3a81269122049d3bb7c9cac
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91657363"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a><span data-ttu-id="e18d0-105">Windows 10 IoT 核心板的 Creators Update 的发行说明</span><span class="sxs-lookup"><span data-stu-id="e18d0-105">Creators Update Release Notes for Windows 10 IoT Core</span></span>
<span data-ttu-id="e18d0-106">内部版本号 15063。</span><span class="sxs-lookup"><span data-stu-id="e18d0-106">Build Number 15063.</span></span> <span data-ttu-id="e18d0-107">2017 年 4 月</span><span class="sxs-lookup"><span data-stu-id="e18d0-107">April 2017</span></span>

<span data-ttu-id="e18d0-108">Windows 10 IoT 核心版支持开发嵌入式设备或专用设备，适合 OEM 和开发人员用来为小型设备构建 Windows 解决方案。</span><span class="sxs-lookup"><span data-stu-id="e18d0-108">Windows 10 IoT Core enables development of embedded or dedicated-purpose devices and is the choice for the OEMs and developers building Windows solutions for small devices.</span></span>

<span data-ttu-id="e18d0-109">本文档旨在为此版本 Windows 10 IoT 核心版的其他内容和文档提供补充。</span><span class="sxs-lookup"><span data-stu-id="e18d0-109">This document provides information that supplements other content and documentation for this release of Windows 10 IoT Core.</span></span>

<span data-ttu-id="e18d0-110">此版本中的程序包包含在以下平台和处理器上安装 Windows 10 IoT 核心版所需的工具和组件：基于 Intel Atom 处理器的 Minnowboard Max 平台、基于 ARM Cortex A7 的 Raspberry Pi 2 以及基于 Qualcomm Snapdragon 400 系列处理器的 Dragonboard 410c。</span><span class="sxs-lookup"><span data-stu-id="e18d0-110">The packages within this release contain tools and components needed to install Windows 10 IoT Core on Minnowboard Max platform based on Intel Atom processors, Raspberry Pi 2 based on ARM Cortex A7, and Dragonboard 410c based on Qualcomm Snapdragon 400 series processors.</span></span>   

<span data-ttu-id="e18d0-111">[其他平台和处理器](../../learn-about-hardware/SoCsAndCustomBoards.md)可从相应合作伙伴处获得。</span><span class="sxs-lookup"><span data-stu-id="e18d0-111">[Other platforms and processors](../../learn-about-hardware/SoCsAndCustomBoards.md) may be available from partners.</span></span>

## <a name="privacy-statement"></a><span data-ttu-id="e18d0-112">隐私声明</span><span class="sxs-lookup"><span data-stu-id="e18d0-112">Privacy Statement</span></span>

<span data-ttu-id="e18d0-113">可在[此处](https://go.microsoft.com/fwlink/?LinkId=506737)查看此 Windows 操作系统版本的隐私声明。</span><span class="sxs-lookup"><span data-stu-id="e18d0-113">The privacy statement for this version of the Windows operating system can be viewed [here](https://go.microsoft.com/fwlink/?LinkId=506737).</span></span>

## <a name="whats-new"></a><span data-ttu-id="e18d0-114">新增功能</span><span class="sxs-lookup"><span data-stu-id="e18d0-114">What's New</span></span>
* <span data-ttu-id="e18d0-115">Windows 10 IoT 核心版公共版本。</span><span class="sxs-lookup"><span data-stu-id="e18d0-115">Windows 10 IoT Core Public Release.</span></span> 
   * <span data-ttu-id="e18d0-116">支持 Azure 设备管理 - OEM 可以使用 Windows IoT Azure DM 客户端库向 Azure IoT 中心的连接设备添加设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="e18d0-116">Azure Device Management Support - OEMs can use the Windows IoT Azure DM client library to add device management capabilities to their Azure IoT hub connected devices.</span></span>
   * <span data-ttu-id="e18d0-117">支持更多处理器</span><span class="sxs-lookup"><span data-stu-id="e18d0-117">Additional Silicon Support</span></span>
      * <span data-ttu-id="e18d0-118">经证实，Windows 10 IoT 核心版支持以下处理器：Intel Joule、Intel Pentium N4200、Intel Celeron N3350、即将发布的 Atom x5-E39xx 处理器（以前称为 Apollo Lake）和 Raspberry Pi 3 SOM。</span><span class="sxs-lookup"><span data-stu-id="e18d0-118">Verified support for Windows 10 IoT Core on Intel Joule, Intel Pentium N4200, Intel Celeron N3350, upcoming Atom x5-E39xx processors (formerly Apollo Lake), and Raspberry Pi 3 SOMs.</span></span>
      * <span data-ttu-id="e18d0-119">Allwinner 已启用对使用 Allwinner A64 SoC 的 Pine 64 和 Banana Pi 设备的支持。</span><span class="sxs-lookup"><span data-stu-id="e18d0-119">Allwinner has enabled support for their Pine 64 and Banana Pi devices using the Allwinner A64 SoC.</span></span> 
   * <span data-ttu-id="e18d0-120">发现远程设备 - 无需任何特殊软件即可发现使用 Microsoft 帐户登录的设备。</span><span class="sxs-lookup"><span data-stu-id="e18d0-120">Discovering your Remote Devices - No special software is needed to discover your devices that are signed in with your Microsoft Account.</span></span>
   * <span data-ttu-id="e18d0-121">新增可用于振动、亮度、新式连接待机、电源管理、电池充电和 NFC（不含 HCE）的 UWP API 和控件。</span><span class="sxs-lookup"><span data-stu-id="e18d0-121">New UWP APIs And controls for vibration, brightness, modern connected standby, power management, battery charge  and NFC (w/o HCE).</span></span> 
   * <span data-ttu-id="e18d0-122">新增可用于 ARM PCIe、USB 功能模式、Wi-fi Direct 和 GPIO 中断计数 API 的总线和功能。</span><span class="sxs-lookup"><span data-stu-id="e18d0-122">New busses and capabilities for ARM PCIe, USB function mode, Wi-Fi Direct, and  GPIO interrupt counting API.</span></span> 
   * <span data-ttu-id="e18d0-123">新增重置/恢复、On-SOC PWM 和自动 USB 预配等嵌入式功能</span><span class="sxs-lookup"><span data-stu-id="e18d0-123">New Embedded features on Reset/Recovery, On-SOC PWM, and Automatic USB provisioning</span></span> 
   * <span data-ttu-id="e18d0-124">改进了以下工具：VS Code、新的 Windows 设备门户和 IoT 面板功能、VS 2017 支持。</span><span class="sxs-lookup"><span data-stu-id="e18d0-124">Improved Tools - VS Code, New Windows Device Portal, and IoT Dashboard features, VS 2017 support.</span></span>
   * <span data-ttu-id="e18d0-125">Windows IoT 核心版上的 Cortana - Cortana 现已在 Windows 10 IoT 核心版上可用。</span><span class="sxs-lookup"><span data-stu-id="e18d0-125">Cortana on Windows IoT Core - Cortana is now available on Windows 10 IoT Core.</span></span> <span data-ttu-id="e18d0-126">向 Cortana 询问一个问题。</span><span class="sxs-lookup"><span data-stu-id="e18d0-126">Ask Cortana a question.</span></span>
   * <span data-ttu-id="e18d0-127">IoT 仪表板改进 - 新增功能和稳定性错误修复</span><span class="sxs-lookup"><span data-stu-id="e18d0-127">IoT Dashboard Improvements - New features and stability bug fixes</span></span>
      * <span data-ttu-id="e18d0-128">适用于 Raspberry Pi 和 Minnowboard 的 Windows 预览体验成员预览版</span><span class="sxs-lookup"><span data-stu-id="e18d0-128">Windows Insider Preview builds for Raspberry Pi and Minnowboard</span></span> 
      * <span data-ttu-id="e18d0-129">使用 Windows IoT 远程客户端连接设备</span><span class="sxs-lookup"><span data-stu-id="e18d0-129">Connecting device using Windows IoT Remote Client</span></span> 
      * <span data-ttu-id="e18d0-130">发现设备中的 Ipv6 地址</span><span class="sxs-lookup"><span data-stu-id="e18d0-130">Ipv6 addresses in discovering devices</span></span> 
      * <span data-ttu-id="e18d0-131">提交反馈时上传设备日志</span><span class="sxs-lookup"><span data-stu-id="e18d0-131">Uploading device logs while submitting feedback</span></span>
   *  <span data-ttu-id="e18d0-132">新增高精度 GPIO API - 新的 API (Windows.Devices.Gpio.GpioInterruptBuffer) 可用于利用 GPIO 中断准确有效地测量脉冲宽度。</span><span class="sxs-lookup"><span data-stu-id="e18d0-132">New high precision GPIO APIs -  New APIs (Windows.Devices.Gpio.GpioInterruptBuffer) for precise and efficient measurement of pulse widths using GPIO interrupts.</span></span><span data-ttu-id="e18d0-133">  GPIO 提供程序包括新的中断缓冲接口，可实现应用程序（如旋转编码器和距离测量设备）的高精度中断计时</span><span class="sxs-lookup"><span data-stu-id="e18d0-133">  GPIO providers include new Interrupt Buffer interface to allow for high precision interrupt timing for applications like rotary encoders and distance measuring devices</span></span>
   * <span data-ttu-id="e18d0-134">Device Guard for IoT - 设备构建者现在可以完全锁定 IoT 设备，并获得高级恶意软件防护以防范未知的新恶意软件变体。</span><span class="sxs-lookup"><span data-stu-id="e18d0-134">Device Guard for IoT - Device builders can now fully lock down IoT devices and get advanced malware protection against new and unknown malware variants.</span></span><span data-ttu-id="e18d0-135">  实现方法如下：为设备上运行的获得许可的应用程序和驱动程序指定签名机构，同时禁止执行未知或不受信任的代码。</span><span class="sxs-lookup"><span data-stu-id="e18d0-135">  This can be done by specifying signing authorities for permissible applications and drivers that run on the device while disallowing execution of unknown or untrusted code.</span></span><span data-ttu-id="e18d0-136">  这意味着提高了防范恶意软件和零日攻击的安全性。</span><span class="sxs-lookup"><span data-stu-id="e18d0-136">  This means improved security against malware and zero-day attacks.</span></span> 
   * <span data-ttu-id="e18d0-137">其他更新包括：</span><span class="sxs-lookup"><span data-stu-id="e18d0-137">Other updates include:</span></span> 
      * <span data-ttu-id="e18d0-138">改进的更新支持</span><span class="sxs-lookup"><span data-stu-id="e18d0-138">Improved Update Support</span></span> 
      * <span data-ttu-id="e18d0-139">Azure 网关 SDK 支持</span><span class="sxs-lookup"><span data-stu-id="e18d0-139">Azure Gateway SDK support</span></span> 
      * <span data-ttu-id="e18d0-140">基于 USB 驱动器的自动预配</span><span class="sxs-lookup"><span data-stu-id="e18d0-140">USB drives based auto-provisioning</span></span> 
      * <span data-ttu-id="e18d0-141">设备门户重新设计</span><span class="sxs-lookup"><span data-stu-id="e18d0-141">Device Portal redesign</span></span> 
      * <span data-ttu-id="e18d0-142">64 位映像现在支持高达 16,384MB 的内存</span><span class="sxs-lookup"><span data-stu-id="e18d0-142">64-bit images now support up to 16,384 MB of memory</span></span> 
      * <span data-ttu-id="e18d0-143">WinRT Vibration API</span><span class="sxs-lookup"><span data-stu-id="e18d0-143">WinRT Vibration APIs</span></span> 
      * <span data-ttu-id="e18d0-144">改进的语言支持</span><span class="sxs-lookup"><span data-stu-id="e18d0-144">Improved language support</span></span> 
   * <span data-ttu-id="e18d0-145">杂项</span><span class="sxs-lookup"><span data-stu-id="e18d0-145">Miscellaneous</span></span>  
      * <span data-ttu-id="e18d0-146">已对默认的 BCD 设置进行了更改，以防止设备在恢复模式不存在时尝试启动到恢复模式。</span><span class="sxs-lookup"><span data-stu-id="e18d0-146">A change has been made to the default BCD settings to prevent devices from attempting to boot to recovery mode when recovery mode does not exist.</span></span> 
      * <span data-ttu-id="e18d0-147">IOT_POWER_SETTINGS 功能现在包含 powercfg.exe。</span><span class="sxs-lookup"><span data-stu-id="e18d0-147">IOT_POWER_SETTINGS feature now includes powercfg.exe.</span></span> <span data-ttu-id="e18d0-148">这适用于所有体系结构（ARM32、x86 和 x64）。</span><span class="sxs-lookup"><span data-stu-id="e18d0-148">This is available for all architectures (ARM32, x86, and x64).</span></span> 
      * <span data-ttu-id="e18d0-149">对 Applyupdate 进行了更改，添加了 blockrebooton/blockrebootoff 标志</span><span class="sxs-lookup"><span data-stu-id="e18d0-149">Changes were made to Applyupdate.exe to add the blockrebooton/blockrebootoff flags</span></span> 
      * <span data-ttu-id="e18d0-150">已将硬件通知 (hwnclx) 和 USB 函数 (usbfnclx) 的类扩展添加到默认 IoT 核心版映像</span><span class="sxs-lookup"><span data-stu-id="e18d0-150">The Class Extensions for Hardware Notification (hwnclx) and USB Function (usbfnclx) have been added to the default IoT Core images</span></span>

## <a name="known-issues"></a><span data-ttu-id="e18d0-151">已知问题</span><span class="sxs-lookup"><span data-stu-id="e18d0-151">Known Issues</span></span>

### <a name="raspberry-pi"></a><span data-ttu-id="e18d0-152">Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="e18d0-152">Raspberry Pi</span></span>  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a><span data-ttu-id="e18d0-153">Raspberry Pi 显示器分辨率（在监视器断开连接的情况下）</span><span class="sxs-lookup"><span data-stu-id="e18d0-153">Raspberry Pi Display Resolution if monitor is disconnected</span></span> 
<span data-ttu-id="e18d0-154">在监视器断开连接的情况下，Raspberry Pi 可能无法保持显示器分辨率。</span><span class="sxs-lookup"><span data-stu-id="e18d0-154">The Raspberry Pi may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="e18d0-155">在连接的情况下，监视器的 EDID 用于设置系统的分辨率。  </span><span class="sxs-lookup"><span data-stu-id="e18d0-155">The EDID of the monitor is used to set the resolution of the system when one is connected.  </span></span>
<span data-ttu-id="e18d0-156">断开连接时，Raspberry Pi 固件默认设置为 SD 卡根目录的 config.txt 中的值。</span><span class="sxs-lookup"><span data-stu-id="e18d0-156">When disconnected, the Raspberry Pi firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 

#### <a name="raspberry-pi-video-performance"></a><span data-ttu-id="e18d0-157">Raspberry Pi 视频性能</span><span class="sxs-lookup"><span data-stu-id="e18d0-157">Raspberry Pi Video Performance</span></span> 
<span data-ttu-id="e18d0-158">Raspberry Pi 平台上的视频播放性能尚未进行优化。</span><span class="sxs-lookup"><span data-stu-id="e18d0-158">Video playback performance on the Raspberry Pi platform has not been optimized.</span></span><span data-ttu-id="e18d0-159">  动态用户元素（包括基于 XAML 的下拉菜单）可能表现不出最佳性能。</span><span class="sxs-lookup"><span data-stu-id="e18d0-159">  Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span> 

#### <a name="raspberry-pi-camera-support"></a><span data-ttu-id="e18d0-160">Raspberry Pi 相机支持</span><span class="sxs-lookup"><span data-stu-id="e18d0-160">Raspberry Pi Camera Support</span></span> 
<span data-ttu-id="e18d0-161">包含 Raspberry Pi 设备的相机外围设备的 Windows 10 IoT 核心版支持受到限制。</span><span class="sxs-lookup"><span data-stu-id="e18d0-161">Windows 10 IoT Core support for camera peripheral devices with Raspberry Pi devices is limited.</span></span> <span data-ttu-id="e18d0-162">直接连接到板载相机总线的 PiCam 设备当前不受支持，因为它要求 GPU 服务，但由于 DirectX 驱动程序尚未实现，因此该服务当前在 Raspberry Pi 上不可用。</span><span class="sxs-lookup"><span data-stu-id="e18d0-162">The PiCam device directly connected to the onboard camera bus is not currently supported, as it requires GPU services that are not currently available on the Raspberry Pi because the DirectX driver is not implemented.</span></span> <span data-ttu-id="e18d0-163">现代 USB 摄像头可在 USB 主控制器上生成要求极度严苛的数据流。</span><span class="sxs-lookup"><span data-stu-id="e18d0-163">Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span><span data-ttu-id="e18d0-164">  即使摄像头结合使用低分辨率设置，还将需要其他 USB 微调和专用控件逻辑。</span><span class="sxs-lookup"><span data-stu-id="e18d0-164">  Even when used with low-resolution settings webcams will require additional USB fine-tuning and specialized control logic.</span></span>  

#### <a name="raspberry-pi-3-bluetooth-support"></a><span data-ttu-id="e18d0-165">Raspberry Pi 3 蓝牙支持</span><span class="sxs-lookup"><span data-stu-id="e18d0-165">Raspberry Pi 3 Bluetooth support</span></span> 
<span data-ttu-id="e18d0-166">Raspberry Pi3 内置蓝牙驱动程序仅支持低带宽设备</span><span class="sxs-lookup"><span data-stu-id="e18d0-166">The Raspberry Pi3 built-in Bluetooth driver only supports low-bandwidth devices</span></span>  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a><span data-ttu-id="e18d0-167">Raspberry Pi 2 上的串行端口用法和访问权限</span><span class="sxs-lookup"><span data-stu-id="e18d0-167">Serial Port Usage and Access on Raspberry Pi 2</span></span> 
<span data-ttu-id="e18d0-168">Raspberry Pi 2 支持通过 PL011 UART 串行传输通信。</span><span class="sxs-lookup"><span data-stu-id="e18d0-168">Raspberry Pi 2 supports the serial transport for communication through the PL011 UART.</span></span><span data-ttu-id="e18d0-169">  这是内核调试方案中的默认设置。</span><span class="sxs-lookup"><span data-stu-id="e18d0-169">  This is set by default in kernel debugging scenarios.</span></span><span data-ttu-id="e18d0-170">  应用程序或设备驱动程序可以使用 PL011 UART 在 PL011 设备驱动程序使用以下命令关闭调试程序的情况下发送和接收数据：   
`bcedit /set debug off`</span><span class="sxs-lookup"><span data-stu-id="e18d0-170">  An application or device driver can use the PL011 UART to send and receive data with the PL011 device driver turning off the debugger using the following command:   
`bcedit /set debug off`</span></span> 
 
### <a name="dragon-board"></a><span data-ttu-id="e18d0-171">Dragon Board</span><span class="sxs-lookup"><span data-stu-id="e18d0-171">Dragon Board</span></span> 

#### <a name="dragonboard-410c-shutdown"></a><span data-ttu-id="e18d0-172">Dragonboard 410c 关机</span><span class="sxs-lookup"><span data-stu-id="e18d0-172">Dragonboard 410c Shutdown</span></span> 
<span data-ttu-id="e18d0-173">在 DragonBoard 上，关机命令不会关闭开发板电源。</span><span class="sxs-lookup"><span data-stu-id="e18d0-173">On the DragonBoard, a shutdown command will not power off the board.</span></span> <span data-ttu-id="e18d0-174">系统将会重新启动。</span><span class="sxs-lookup"><span data-stu-id="e18d0-174">The system will restart.</span></span> <span data-ttu-id="e18d0-175">请通过断开电源连接来关闭开发板电源。</span><span class="sxs-lookup"><span data-stu-id="e18d0-175">Please power off the board by disconnecting the power.</span></span> 

#### <a name="dragon-board-headset--microphone-jack"></a><span data-ttu-id="e18d0-176">Dragon Board 耳机和麦克风插孔</span><span class="sxs-lookup"><span data-stu-id="e18d0-176">Dragon Board headset & microphone jack</span></span>  
<span data-ttu-id="e18d0-177">Dragonboard BSP 具有耳机插孔和麦克风插孔的驱动程序，但它在开发板上没有这两种插孔。</span><span class="sxs-lookup"><span data-stu-id="e18d0-177">The Dragonboard BSP has drivers for the headset jack and microphone jack, but it doesn't have either of these jacks on board.</span></span>  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a><span data-ttu-id="e18d0-178">Dragonboard SPI 以锁定速度运行</span><span class="sxs-lookup"><span data-stu-id="e18d0-178">Dragonboard SPI runs at lock speed</span></span>  
<span data-ttu-id="e18d0-179">Dragonboard 上的 SPI 将会忽略所请求的速度，并始终以预配置的速度运行。</span><span class="sxs-lookup"><span data-stu-id="e18d0-179">The SPI on the Dragonboard will ignore the requested speed and always run at a preconfigured speed.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="e18d0-180">Dragonboard 连接待机</span><span class="sxs-lookup"><span data-stu-id="e18d0-180">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="e18d0-181">默认情况下，连接待机在 Qualcomm Dragonboard 上未启用。</span><span class="sxs-lookup"><span data-stu-id="e18d0-181">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span><span data-ttu-id="e18d0-182">  若要在 DragonBoard 上启用连接待机，需要将以下注册表项设置为“1” 
</span><span class="sxs-lookup"><span data-stu-id="e18d0-182">  To enable Connected Standby on DragonBoard, the following registry key needs to be set to “1” 
</span></span><br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
<span data-ttu-id="e18d0-183">请注意，并非所有平台都支持 CS，因此这可能不适用于其他平台。</span><span class="sxs-lookup"><span data-stu-id="e18d0-183">Note that not all platforms have support for CS, so this may not work on other platforms.</span></span>    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a><span data-ttu-id="e18d0-184">Vibration API 在某些 Qualcomm 平台上可能不起作用</span><span class="sxs-lookup"><span data-stu-id="e18d0-184">Vibration API may not function on some Qualcomm platforms</span></span> 
<span data-ttu-id="e18d0-185">建议的解决方法是添加以下注册表项： 
</span><span class="sxs-lookup"><span data-stu-id="e18d0-185">The suggested workaround is to add the following registry key: 
</span></span><br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
<span data-ttu-id="e18d0-186">要在现有映像上进行确认/验证，请使用 SSH 或 PowerShell 连接并运行以下命令： 
</span><span class="sxs-lookup"><span data-stu-id="e18d0-186">For confirmation / verification on an existing image connect with SSH or PowerShell and run the following command: 
</span></span><br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a><span data-ttu-id="e18d0-187">MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="e18d0-187">MinnowBoard</span></span>  

#### <a name="minnowboard-max-firmware-update"></a><span data-ttu-id="e18d0-188">Minnowboard Max 固件更新</span><span class="sxs-lookup"><span data-stu-id="e18d0-188">Minnowboard Max Firmware Update</span></span> 
<span data-ttu-id="e18d0-189">除非固件是 0.92 版或更高版本，否则 MinnowBoard Max 不会启动。  </span><span class="sxs-lookup"><span data-stu-id="e18d0-189">The MinnowBoard Max will not boot unless the firmware is version 0.92 or later.  </span></span>
<span data-ttu-id="e18d0-190">MinnowBoard Max (MBM) 固件版本 0.93 可能存在网络连接故障。</span><span class="sxs-lookup"><span data-stu-id="e18d0-190">There may be network connectivity failures in MinnowBoard Max (MBM) firmware version 0.93.</span></span><span data-ttu-id="e18d0-191">   此问题已在固件版本 0.94 中解决。） 推荐的最低固件版本是“MinnowBoard MAX 0.94 32 位”。</span><span class="sxs-lookup"><span data-stu-id="e18d0-191">   The issue is fixed in firmware version 0.94.)  The minimum recommended version of the firmware is “MinnowBoard MAX 0.94 32-bit”.</span></span> <span data-ttu-id="e18d0-192">固件更新可从 [此处](https://go.microsoft.com/fwlink/?LinkId=708613)下载。</span><span class="sxs-lookup"><span data-stu-id="e18d0-192">Firmware updates can be downloaded from [here](https://go.microsoft.com/fwlink/?LinkId=708613).</span></span>
  
 
### <a name="all-platforms"></a><span data-ttu-id="e18d0-193">所有平台</span><span class="sxs-lookup"><span data-stu-id="e18d0-193">All Platforms</span></span> 

#### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="e18d0-194">调试时鼠标指针消失</span><span class="sxs-lookup"><span data-stu-id="e18d0-194">Mouse Pointer disappears while debugging</span></span> 
<span data-ttu-id="e18d0-195">在某些情况下，在使用 Visual Studio 部署或调试应用后，鼠标指针会变得不可见，此时如果使用键盘 (Tab) 更改焦点，鼠标指针就会重新显示</span><span class="sxs-lookup"><span data-stu-id="e18d0-195">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab)</span></span>  

#### <a name="server-applications-with-softap"></a><span data-ttu-id="e18d0-196">服务器应用程序与 SoftAP</span><span class="sxs-lookup"><span data-stu-id="e18d0-196">Server Applications with SoftAP</span></span>  
<span data-ttu-id="e18d0-197">使用 SoftAP 时，客户端将无法访问 UAP 应用公开的内容。  </span><span class="sxs-lookup"><span data-stu-id="e18d0-197">When using the SoftAP, clients will not be able to access content exposed by UAP apps.  </span></span>
<span data-ttu-id="e18d0-198">若要通过 SoftAP 公开 UAP 应用程序，必须通过设备上的控制台进行以下更改：  
</span><span class="sxs-lookup"><span data-stu-id="e18d0-198">To expose UAP applications via SoftAP the following changes must be made from the console on the device :  
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

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="e18d0-199">在预先构建的 FFU 中出现传感器驱动程序冲突</span><span class="sxs-lookup"><span data-stu-id="e18d0-199">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="e18d0-200">在提供的 FFU 中存在传感器驱动程序冲突。</span><span class="sxs-lookup"><span data-stu-id="e18d0-200">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="e18d0-201">Remote Sensor Framework 可为指南针、磁力计、加速计和陀螺仪安装驱动程序。</span><span class="sxs-lookup"><span data-stu-id="e18d0-201">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer, and Gyro.</span></span> <span data-ttu-id="e18d0-202">从应用程序访问这些项目的 UWP API 会假定只安装了其中 1 项。</span><span class="sxs-lookup"><span data-stu-id="e18d0-202">The UWP APIs for accessing these from an application assume just 1 is installed.</span></span> <span data-ttu-id="e18d0-203">如果你为通过物理方式连接的设备开发驱动程序，则 Microsoft 提供的 FFU 上的远程驱动程序会产生冲突。  </span><span class="sxs-lookup"><span data-stu-id="e18d0-203">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.  </span></span>
<span data-ttu-id="e18d0-204">分辨率：可以删除发生冲突的驱动程序，方法是：通过 SSH 或 PowerShell 连接到设备，然后键入“devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*”，使用 devcon.exe 工具删除远程传感器驱动程序。</span><span class="sxs-lookup"><span data-stu-id="e18d0-204">Resolution: The conflicting driver can be removed by connecting to the device via SSH or PowerShell and using the tool devcon.exe to remove the remote sensor driver by typing “devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*”.</span></span> <span data-ttu-id="e18d0-205">远程传感器驱动程序不影响 OEM 创建的 FFU。</span><span class="sxs-lookup"><span data-stu-id="e18d0-205">The remote sensor driver does not affect OEM created FFUs.</span></span> 
 
#### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="e18d0-206">默认管理员用户名和密码</span><span class="sxs-lookup"><span data-stu-id="e18d0-206">Default Administrator User Name and Password</span></span> 
<span data-ttu-id="e18d0-207">默认的管理员用户名和密码已硬编码在 Windows 10 IoT 核心版映像中。</span><span class="sxs-lookup"><span data-stu-id="e18d0-207">The default administrator user name and password are hard-coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="e18d0-208">这使设备具有安全风险，因此在更改密码之前，请不要向开放的 Internet 连接公开此信息。</span><span class="sxs-lookup"><span data-stu-id="e18d0-208">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 
 
#### <a name="volume-controls"></a><span data-ttu-id="e18d0-209">音量控件</span><span class="sxs-lookup"><span data-stu-id="e18d0-209">Volume Controls</span></span> 
<span data-ttu-id="e18d0-210">依赖于 Windows 系统更改系统音量的 USB 麦克风和扬声器的硬件音量控件当前在 Windows 10 IoT 核心版上不受支持。</span><span class="sxs-lookup"><span data-stu-id="e18d0-210">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 
 
#### <a name="usb-keyboards"></a><span data-ttu-id="e18d0-211">USB 键盘</span><span class="sxs-lookup"><span data-stu-id="e18d0-211">USB Keyboards</span></span>  
<span data-ttu-id="e18d0-212">某些 USB 键盘和鼠标可能无法在 IoT 核心版上工作。</span><span class="sxs-lookup"><span data-stu-id="e18d0-212">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="e18d0-213">使用其他键盘或鼠标。</span><span class="sxs-lookup"><span data-stu-id="e18d0-213">Use a different keyboard or mouse.</span></span> <span data-ttu-id="e18d0-214">在[此处](../../learn-about-hardware/HardwareCompatList.md)可用找到已验证的外围设备列表。</span><span class="sxs-lookup"><span data-stu-id="e18d0-214">A list of validated peripheral devices can be found [here](../../learn-about-hardware/HardwareCompatList.md).</span></span>  
 
#### <a name="screen-orientation"></a><span data-ttu-id="e18d0-215">屏幕方向</span><span class="sxs-lookup"><span data-stu-id="e18d0-215">Screen Orientation</span></span> 
<span data-ttu-id="e18d0-216">将方向设置为“纵向”在通用应用中可能不受支持</span><span class="sxs-lookup"><span data-stu-id="e18d0-216">Setting the orientation to “Portrait” may not be honored in a Universal App</span></span> 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="e18d0-217">使用 AllJoyn 模板引用适配器</span><span class="sxs-lookup"><span data-stu-id="e18d0-217">Referencing Adapters with AllJoyn Templates</span></span> 
<span data-ttu-id="e18d0-218">尝试向 AllJoyn 适配器项目添加引用可能会在使用特定 SDK 版本时导致错误。</span><span class="sxs-lookup"><span data-stu-id="e18d0-218">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span><span data-ttu-id="e18d0-219">  若要解决这些错误，请更改 Visual Studio 的目标平台，以匹配当前的 SDK 版本，然后重新加载项目。</span><span class="sxs-lookup"><span data-stu-id="e18d0-219">  To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span> 

#### <a name="non-default-drive-mode"></a><span data-ttu-id="e18d0-220">非默认驱动器模式</span><span class="sxs-lookup"><span data-stu-id="e18d0-220">Non-default drive mode</span></span>  
<span data-ttu-id="e18d0-221">在 Raspberry Pi 和 Dragonboard 上，从非默认驱动器模式切换到其他非默认驱动器模式可能会在 GPIO 引脚上产生故障。</span><span class="sxs-lookup"><span data-stu-id="e18d0-221">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="e18d0-222">解决方法：在应用程序开端处设置一次驱动器模式。</span><span class="sxs-lookup"><span data-stu-id="e18d0-222">WORKAROUND: Set drive mode once at the beginning of the application.</span></span> 
 
#### <a name="application-already-running"></a><span data-ttu-id="e18d0-223">已处于运行状态的应用程序</span><span class="sxs-lookup"><span data-stu-id="e18d0-223">Application already running</span></span>  
<span data-ttu-id="e18d0-224">如果默认启动应用也从 Visual Studio 部署，则该应用可能会跟自身发生冲突。</span><span class="sxs-lookup"><span data-stu-id="e18d0-224">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="e18d0-225">解决方法：将默认启动应用更改为不希望部署的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e18d0-225">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a><span data-ttu-id="e18d0-226">BackgroundMediaPlayer.MessageReceivedFromForeground 可能会崩溃</span><span class="sxs-lookup"><span data-stu-id="e18d0-226">BackgroundMediaPlayer.MessageReceivedFromForeground may crash</span></span>  
<span data-ttu-id="e18d0-227">以下代码行可能崩溃：`BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`。</span><span class="sxs-lookup"><span data-stu-id="e18d0-227">The following line of code may crash: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`.</span></span>
<br>
<span data-ttu-id="e18d0-228">若要防止崩溃，请添加此代码，以便首先执行它 `var player = BackgroundMediaPlayer.Current;`</span><span class="sxs-lookup"><span data-stu-id="e18d0-228">To prevent the crash, add this code so that it is executed first `var player = BackgroundMediaPlayer.Current;`</span></span> 
 
#### <a name="azure-active-directory-authentication-support"></a><span data-ttu-id="e18d0-229">Azure Active Directory 身份验证支持</span><span class="sxs-lookup"><span data-stu-id="e18d0-229">Azure Active Directory Authentication Support</span></span>  
<span data-ttu-id="e18d0-230">Azure Active Directory 身份验证库在 Windows 10 IoT 核心版上不可用。</span><span class="sxs-lookup"><span data-stu-id="e18d0-230">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  
 
#### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="e18d0-231">应用程序崩溃的 Shell 管理</span><span class="sxs-lookup"><span data-stu-id="e18d0-231">Shell Management of Application Crashes</span></span> 
<span data-ttu-id="e18d0-232">IoT 核心版的 shell 基础结构用于监视设备中运行的 APPX 类型的应用程序是否崩溃，并且会在发生崩溃时重新启动这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="e18d0-232">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span><span data-ttu-id="e18d0-233">  如果重新启动的应用程序继续崩溃，shell 将采用 __failfast 这一系统关键进程，可引起错误检测并重新启动以尝试恢复。</span><span class="sxs-lookup"><span data-stu-id="e18d0-233">  If the restarted applications continue to crash, the shell will employ a __failfast – a system critical process that causes a bug check and reboot in an attempt to recover.</span></span><span data-ttu-id="e18d0-234">  可比较逻辑和处理用于有外设配置中的后台任务和前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="e18d0-234">  Comparable logic and handling are used to background tasks and foreground applications in a headed configuration.</span></span>   

<span data-ttu-id="e18d0-235">下面捕获的是崩溃处理和重试逻辑：</span><span class="sxs-lookup"><span data-stu-id="e18d0-235">Crash handing and retry logic are captured below:</span></span> 

<span data-ttu-id="e18d0-236">Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig（或适用于外设的 ForegroundAppConfig）</span><span class="sxs-lookup"><span data-stu-id="e18d0-236">Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed)</span></span> 
* <span data-ttu-id="e18d0-237">Qword:"FailureResetIntervalMs"：为了将出现的故障重置为 0，应用需要成功运行的时长。</span><span class="sxs-lookup"><span data-stu-id="e18d0-237">Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0.</span></span> <span data-ttu-id="e18d0-238">（默认值为 0x00000000000493E0 == 5 分钟。）</span><span class="sxs-lookup"><span data-stu-id="e18d0-238">– default is 0x00000000000493E0 == 5 minutes.</span></span> 
* <span data-ttu-id="e18d0-239">Qword:"BaseRetryDelayMs"：等待时间系数。</span><span class="sxs-lookup"><span data-stu-id="e18d0-239">Qword:"BaseRetryDelayMs"  -- wait time coefficient.</span></span><span data-ttu-id="e18d0-240">  默认值为 0xa。</span><span class="sxs-lookup"><span data-stu-id="e18d0-240">  Default is 0xa.</span></span>
* <span data-ttu-id="e18d0-241">Dword:"MaxFailureCount"。</span><span class="sxs-lookup"><span data-stu-id="e18d0-241">Dword:"MaxFailureCount".</span></span> <span data-ttu-id="e18d0-242">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="e18d0-242">Default is 10.</span></span>
* <span data-ttu-id="e18d0-243">DWord:"FallbackExponentNumerator"，默认值为 31。</span><span class="sxs-lookup"><span data-stu-id="e18d0-243">DWord:"FallbackExponentNumerator", default is 31.</span></span>
* <span data-ttu-id="e18d0-244">Dword:"FallbackExponentDenominator"，默认值为 20。</span><span class="sxs-lookup"><span data-stu-id="e18d0-244">Dword:"FallbackExponentDenominator", default is 20.</span></span>
 
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
 
#### <a name="time-synchronization"></a><span data-ttu-id="e18d0-245">时间同步</span><span class="sxs-lookup"><span data-stu-id="e18d0-245">Time Synchronization</span></span>  
<span data-ttu-id="e18d0-246">如果时间同步失败或超时，可能是因为时间服务器无法访问或过于遥远，可以通过以下操作来添加额外的或本地的时间服务器。</span><span class="sxs-lookup"><span data-stu-id="e18d0-246">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
* <span data-ttu-id="e18d0-247">在设备的命令行（例如</span><span class="sxs-lookup"><span data-stu-id="e18d0-247">From a command line on the device (eg.</span></span> <span data-ttu-id="e18d0-248">SSH、Powershell）  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span><span class="sxs-lookup"><span data-stu-id="e18d0-248">SSH, PowerShell)  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span></span> 
* <span data-ttu-id="e18d0-249">也可根据需要通过启动脚本或自定义运行时配置包（在创建映像过程中包括进来）将其添加到注册表中。 </span><span class="sxs-lookup"><span data-stu-id="e18d0-249">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed. </span></span>
<span data-ttu-id="e18d0-250">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="e18d0-250">For more information, see:</span></span> 
* <span data-ttu-id="e18d0-251">[将文件和注册表设置添加到映像](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="e18d0-251">[Add a file and a registry setting to an image](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)</span></span>
* [<span data-ttu-id="e18d0-252">Windows 10 IoT 核心板映像创建</span><span class="sxs-lookup"><span data-stu-id="e18d0-252">Windows 10 IoT Core Image Creation</span></span>](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a><span data-ttu-id="e18d0-253">启动 FTP 服务器</span><span class="sxs-lookup"><span data-stu-id="e18d0-253">Starting the FTP Server</span></span> 
<span data-ttu-id="e18d0-254">FTP 服务器不再在启动时默认运行。</span><span class="sxs-lookup"><span data-stu-id="e18d0-254">The FTP Server no longer runs by default at start-up.</span></span>

<span data-ttu-id="e18d0-255">要运行一次，请使用 SSH\PS 登录。</span><span class="sxs-lookup"><span data-stu-id="e18d0-255">To run once, sign in with SSH\PS.</span></span>

<span data-ttu-id="e18d0-256">运行以下命令来启动 FTP： `start ftpd.exe`</span><span class="sxs-lookup"><span data-stu-id="e18d0-256">Run this command to start FTP: `start ftpd.exe`</span></span>

<span data-ttu-id="e18d0-257">若要在每次启动时运行，用户应创建一项计划程序任务。</span><span class="sxs-lookup"><span data-stu-id="e18d0-257">To run on every boot, users should create a scheduler task.</span></span> <span data-ttu-id="e18d0-258">请使用 SSH\PS 登录，然后创建一项计划程序任务：</span><span class="sxs-lookup"><span data-stu-id="e18d0-258">Sign in with SSH\PS and create a scheduler task:</span></span>

```cmd
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart
schtasks /run /tn “IoTFTPD”
```

## <a name="copyright-information"></a><span data-ttu-id="e18d0-259">版权信息</span><span class="sxs-lookup"><span data-stu-id="e18d0-259">Copyright Information</span></span> 

<span data-ttu-id="e18d0-260">© Microsoft。</span><span class="sxs-lookup"><span data-stu-id="e18d0-260">© Microsoft.</span></span> <span data-ttu-id="e18d0-261">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="e18d0-261">All rights reserved.</span></span> 
 
<span data-ttu-id="e18d0-262">本文档按原样提供。</span><span class="sxs-lookup"><span data-stu-id="e18d0-262">This document is provided “as-is”.</span></span><span data-ttu-id="e18d0-263">  本文档中表达的信息和视图（包括 URL 和其他 Internet 网站引用）如有更改，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="e18d0-263">  Information and views expressed in this document, including URL and other Internet Web site references may change without notice.</span></span> 

<span data-ttu-id="e18d0-264">本书中提及的一些示例仅用于说明，纯属虚构。</span><span class="sxs-lookup"><span data-stu-id="e18d0-264">Some examples depicted herein are provided for illustration only and are fictitious.</span></span><span data-ttu-id="e18d0-265">不存在任何实际关联或联系，请勿妄加推断。</span><span class="sxs-lookup"><span data-stu-id="e18d0-265">  No real association or connection is intended or should be inferred.</span></span>  

<span data-ttu-id="e18d0-266">本文档未提供针对任何 Microsoft 产品的任何知识产权的任何法律权限。</span><span class="sxs-lookup"><span data-stu-id="e18d0-266">This document does not provide any legal rights to any intellectual property in any Microsoft product.</span></span><span data-ttu-id="e18d0-267">  本文档仅供内部参考。</span><span class="sxs-lookup"><span data-stu-id="e18d0-267">  This document may be used for internal, references purposes.</span></span> 
  
<span data-ttu-id="e18d0-268">Microsoft 不做任何明示或暗示的担保。</span><span class="sxs-lookup"><span data-stu-id="e18d0-268">Microsoft makes no warranties, express or implied.</span></span>  

<span data-ttu-id="e18d0-269">有关有商标的产品列表，请参阅 Microsoft 商标。</span><span class="sxs-lookup"><span data-stu-id="e18d0-269">Please refer to Microsoft Trademarks for a list of trademarked products.</span></span> 

<span data-ttu-id="e18d0-270">所有其他商标均为其各自所有者的财产。</span><span class="sxs-lookup"><span data-stu-id="e18d0-270">All other trademarks are property of their respective owners.</span></span>  

<span data-ttu-id="e18d0-271">UPnP ™ 是 UPnP™ Implementers Corporation 的认证标记。</span><span class="sxs-lookup"><span data-stu-id="e18d0-271">UPnP™ is a certification mark of the UPnP™ Implementers Corporation.</span></span> 

<span data-ttu-id="e18d0-272">Bluetooth® 是美国 Bluetooth SIG, Inc. 拥有的商标，并已向 Microsoft Corporation 授予了许可证。</span><span class="sxs-lookup"><span data-stu-id="e18d0-272">Bluetooth® is a trademark owned by Bluetooth SIG, Inc. USA and licensed to Microsoft Corporation.</span></span> 

<span data-ttu-id="e18d0-273">Intel 是 Intel Corporation 的注册商标。</span><span class="sxs-lookup"><span data-stu-id="e18d0-273">Intel is a registered trademark of Intel Corporation.</span></span> 

<span data-ttu-id="e18d0-274">Itanium 是 Intel Corporation 的注册商标。</span><span class="sxs-lookup"><span data-stu-id="e18d0-274">Itanium is a registered trademark of Intel Corporation.</span></span>
 
<span data-ttu-id="e18d0-275">本软件的某些部分基于 MCSA Mosaic，并由伊利诺伊大学厄巴纳-香槟分校的国家超级计算应用中心开发，按照与 Spyglass, Inc. 签订的许可协议进行分发。</span><span class="sxs-lookup"><span data-stu-id="e18d0-275">Portions of this software are based on MCSA Mosaic, developed by the National Center for Supercomputing Applications at the University of Illinois at Urbana-Champaign, distributed under a licensing agreement with Spyglass, Inc.</span></span> 

<span data-ttu-id="e18d0-276">本产品包含 RSA Data Security, Inc 授予许可证的安全软件。</span><span class="sxs-lookup"><span data-stu-id="e18d0-276">This product contains security software licensed from RSA Data Security, Inc.</span></span> 
