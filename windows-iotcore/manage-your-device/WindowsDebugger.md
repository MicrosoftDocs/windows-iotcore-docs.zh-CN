---
title: Windows 调试器
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 调试器调试 Windows IoT Core 设备。
keywords: windows iot, 调试程序, 调试, Windows 调试器, 设备, 工具
ms.openlocfilehash: e56f5ca837de79aaf0c36cf7d3c6ae6badf3fd16
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170275"
---
# <a name="windows-debugger-windbg"></a><span data-ttu-id="dda9f-104">Windows Debugger (WinDbg)</span><span class="sxs-lookup"><span data-stu-id="dda9f-104">Windows Debugger (WinDbg)</span></span>
<span data-ttu-id="dda9f-105">使用功能强大的 Windows 调试器 WinDbg 调试 Windows 10 IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="dda9f-105">Debug your Windows 10 IoT Core device using the powerful Windows debugger, WinDbg.</span></span>

<span data-ttu-id="dda9f-106">以下部分介绍如何成功将 WinDbg 连接到 Windows 10 IoT 核心版设备以实现调试目的。</span><span class="sxs-lookup"><span data-stu-id="dda9f-106">The following sections describe how to successfully connect with WinDbg to a Windows 10 IoT Core device for debugging purposes.</span></span>  <span data-ttu-id="dda9f-107">这包括描述设备上的必要软件设置以及物理硬件连接。</span><span class="sxs-lookup"><span data-stu-id="dda9f-107">This includes a description of the necessary software settings on the device as well as the physical hardware connections.</span></span>  

<span data-ttu-id="dda9f-108">WinDbg 是一个非常强大的调试程序，大多数 Windows 开发人员都对其了如指掌。</span><span class="sxs-lookup"><span data-stu-id="dda9f-108">WinDbg is a very powerful debugger that most Windows developers are familiar with.</span></span>  <span data-ttu-id="dda9f-109">但是，如果你还不熟悉，并且想要了解有关 WinDbg 的详细信息，请访问以下链接：</span><span class="sxs-lookup"><span data-stu-id="dda9f-109">However, if you are just getting started and would like to learn more about WinDbg, please visit the following links:</span></span>

* <span data-ttu-id="dda9f-110">[Windows 调试工具](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="dda9f-110">[Debugging Tools for Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)</span></span> 

* <span data-ttu-id="dda9f-111">[Windows 调试入门](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="dda9f-111">[Getting Started with Windows Debugging](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)</span></span> 

* <span data-ttu-id="dda9f-112">[使用 WinDbg 进行故障转储分析](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="dda9f-112">[Crash Dump Analysis Using WinDbg](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)</span></span> 


## <a name="minnowboard-max-mbm"></a><span data-ttu-id="dda9f-113">MinnowBoard Max (MBM)</span><span class="sxs-lookup"><span data-stu-id="dda9f-113">MinnowBoard Max (MBM)</span></span> 

<span data-ttu-id="dda9f-114">可以使用网络连接将 MinnowBoard 连接到最大设备。</span><span class="sxs-lookup"><span data-stu-id="dda9f-114">You can connect WinDbg to the MinnowBoard Max device using a network connection.</span></span>

### <a name="setup-network-connection"></a><span data-ttu-id="dda9f-115">设置网络连接</span><span class="sxs-lookup"><span data-stu-id="dda9f-115">Setup network connection</span></span>

<span data-ttu-id="dda9f-116">若要在网络上使用 WinDbg 启用内核调试, 请确保:</span><span class="sxs-lookup"><span data-stu-id="dda9f-116">In order to enable kernel debugging with WinDbg over a network, ensure that:</span></span>

* <span data-ttu-id="dda9f-117">将以太网电缆连接到网络上的 MinnowBoard Max 设备</span><span class="sxs-lookup"><span data-stu-id="dda9f-117">An Ethernet cable is connected to MinnowBoard Max device to your network</span></span> 

* <span data-ttu-id="dda9f-118">MinnowBoard Max 设备在你的网络中具有有效的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="dda9f-118">The MinnowBoard Max device has a valid IP address in your network</span></span>

* <span data-ttu-id="dda9f-119">通过[PowerShell](../connect-your-device/PowerShell.md)与 MinnowBoard Max 设备建立活动连接</span><span class="sxs-lookup"><span data-stu-id="dda9f-119">An active connection to the MinnowBoard Max device via [PowerShell](../connect-your-device/PowerShell.md)</span></span> 

<span data-ttu-id="dda9f-120">使用 active PowerShell 连接, 对 MinnowBoard Max 执行以下命令, 以启用通过网络进行调试。</span><span class="sxs-lookup"><span data-stu-id="dda9f-120">Using the active PowerShell connection, execute the following commands on the MinnowBoard Max to enable debugging over the network.</span></span>

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * <span data-ttu-id="dda9f-121">此命令可通过网络启用调试。</span><span class="sxs-lookup"><span data-stu-id="dda9f-121">This command enables debugging over the network.</span></span>  <span data-ttu-id="dda9f-122">此外，它还可指定将要运行 WinDbg (DEV_PC_IP_ADDRESS) 的电脑的 IP 地址、用于连接的网络端口号 (PORT_NUM)，以及用于区分多个连接的唯一密钥 (KEY)</span><span class="sxs-lookup"><span data-stu-id="dda9f-122">Additionally, it specifies the IP address of the PC where WinDbg will be running (DEV_PC_IP_ADDRESS), the network port number to use for the connection (PORT_NUM), and a unique key to be used to differentiate multiple connections (KEY)</span></span> 

    * <span data-ttu-id="dda9f-123">对于 PORT_NUM 和 KEY，可使用以下值作为示例：分别是 50045 和 1.2.3.4，尽管你可以根据需要更改它们</span><span class="sxs-lookup"><span data-stu-id="dda9f-123">For PORT_NUM and KEY, you can use the following values as examples: 50045 and 1.2.3.4 respectively, although you are free to change them as you see fit</span></span>
    
* `bcdedit -debug on`

    * <span data-ttu-id="dda9f-124">此命令将在设备上打开调试</span><span class="sxs-lookup"><span data-stu-id="dda9f-124">This command turns on debugging on the device</span></span> 

* <span data-ttu-id="dda9f-125">在开发人员电脑上, 用前面步骤中提供的 PORT_NUM 和密钥值启动 WinDbg, 如下所示:`"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span><span class="sxs-lookup"><span data-stu-id="dda9f-125">On the developer PC, start WinDbg with the PORT_NUM and the KEY values provided in the previous steps as follows: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span></span>

> [!NOTE]
> <span data-ttu-id="dda9f-126">如果你安装了任何 Windows 工具包, 你可能会发现`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`</span><span class="sxs-lookup"><span data-stu-id="dda9f-126">If you have any of the Windows kits installed, you may find WinDbg under `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`</span></span>

* <span data-ttu-id="dda9f-127">重新启动 IoTCore 设备以重新连接到调试器</span><span class="sxs-lookup"><span data-stu-id="dda9f-127">Reboot the IoTCore device to reconnect to the debugger</span></span>

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a><span data-ttu-id="dda9f-128">Raspberry Pi 2 或 3（RPi2 或 RPi3）</span><span class="sxs-lookup"><span data-stu-id="dda9f-128">Raspberry Pi 2 or 3 (RPi2 or RPi3)</span></span> 

<span data-ttu-id="dda9f-129">可使用串行连接将 WinDbg 连接到 Raspberry Pi 2 或 3。</span><span class="sxs-lookup"><span data-stu-id="dda9f-129">You can connect WinDbg to the Raspberry Pi 2 or 3 using a serial connection.</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="dda9f-130">设置串行连接</span><span class="sxs-lookup"><span data-stu-id="dda9f-130">Setup serial connection</span></span>

<span data-ttu-id="dda9f-131">若要在串行连接上使用 WinDbg 启用内核调试, 请确保:</span><span class="sxs-lookup"><span data-stu-id="dda9f-131">In order to enable kernel debugging with WinDbg over a serial connection, ensure that:</span></span>

* <span data-ttu-id="dda9f-132">你具有调试电缆，例如 [Adafruit](https://www.adafruit.com/product/954) 或 [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105) 中的 USB-to-TTL 的串行电缆。</span><span class="sxs-lookup"><span data-stu-id="dda9f-132">You have a debug cable such as the USB-to-TTL Serial Cable from [Adafruit](https://www.adafruit.com/product/954) or [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105).</span></span> 

* <span data-ttu-id="dda9f-133">将 Raspberry Pi 2 或3设备连接到网络的以太网电缆或活动 WiFi (对于 SSH 或 PowerShell 等 IP 连接)</span><span class="sxs-lookup"><span data-stu-id="dda9f-133">An Ethernet cable or active WiFi connecting your Raspberry Pi 2 or 3 device to your network (for IP connections like SSH or PowerShell)</span></span>

* <span data-ttu-id="dda9f-134">Raspberry Pi 2 或3设备在网络中具有有效的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="dda9f-134">The Raspberry Pi 2 or 3 device has a valid IP address in your network</span></span>

* <span data-ttu-id="dda9f-135">通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)与 Raspberry Pi 2 或3设备建立活动连接</span><span class="sxs-lookup"><span data-stu-id="dda9f-135">An active connection to the Raspberry Pi 2 or 3 device via [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md)</span></span>

<span data-ttu-id="dda9f-136">对于内核调试连接, 将在 Raspberry Pi 2 或3设备上使用 UART0。</span><span class="sxs-lookup"><span data-stu-id="dda9f-136">UART0 will be used on the Raspberry Pi 2 or 3 device for the kernel debugging connection.</span></span>  <span data-ttu-id="dda9f-137">下面介绍了 Raspberry Pi 2 或 3 的 PIN 映射以及串行电缆：</span><span class="sxs-lookup"><span data-stu-id="dda9f-137">The following shows the pin mappings for the Raspberry Pi 2 or 3 as well as the serial cables:</span></span> 

        Raspberry Pi 2 or 3 pins:
            Pin #6 : GND
            Pin #8 : UART0 TX (3.3V)
            pin #10: UART0 RX (3.3V)

        Adafruit Cable:
            Black  : GND
            White  : RX  (3.3V)
            Green  : TX  (3.3V)
            Red    : PWR (5.0V NOT USED) <- DO NOT CONNECT!!
        
        FTDI Cable:
            Black  : GND
            Brown  : CTS (NOT USED)
            Red    : PWR (5.0V NOT USED) <- DO NOT CONNECT!!
            Orange : TX  (3.3V)
            Yellow : RX  (3.3V)
            Green  : RTS (NOT USED)
            
<span data-ttu-id="dda9f-138">进行正确的串行连接的基本思想是，记住当一台设备使用其 TX 传输数据时，另一台设备使用其 RX 接收该数据。</span><span class="sxs-lookup"><span data-stu-id="dda9f-138">The basic idea for making the correct serial connections is to remember that while one device uses its TX to transmit data, the other device uses its RX to receive the data.</span></span>  <span data-ttu-id="dda9f-139">下面列出了推荐的连接:</span><span class="sxs-lookup"><span data-stu-id="dda9f-139">Recommended connections are listed below:</span></span>

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> <span data-ttu-id="dda9f-140">不再创建 EFIESP 联接。</span><span class="sxs-lookup"><span data-stu-id="dda9f-140">The EFIESP junction is no longer created.</span></span> <span data-ttu-id="dda9f-141">你必须自行装载, 你可以使用 mountvol 命令来获取 GUID。</span><span class="sxs-lookup"><span data-stu-id="dda9f-141">You'll have to mount it yourself,you can use mountvol command to get the GUID.</span></span>
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

<span data-ttu-id="dda9f-142">使用活动的 PowerShell 连接, 在 Raspberry Pi 2 或3设备上执行以下命令, 以启用通过串行连接进行调试。</span><span class="sxs-lookup"><span data-stu-id="dda9f-142">Using the active PowerShell connection, execute the following commands on the Raspberry Pi 2 or 3 device to enable debugging over the serial connection.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * <span data-ttu-id="dda9f-143">上述命令可启用用于调试的串行连接</span><span class="sxs-lookup"><span data-stu-id="dda9f-143">The above command enables the serial connection for debugging</span></span>
    * <span data-ttu-id="dda9f-144">Raspberry Pi 2 或 3 波特率已硬编码到 921600，因此无需指定它</span><span class="sxs-lookup"><span data-stu-id="dda9f-144">The baud-rate for the Raspberry Pi 2 or 3 is hard-coded to 921600, so you don't have to specify it</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * <span data-ttu-id="dda9f-145">此命令将在设备上打开调试</span><span class="sxs-lookup"><span data-stu-id="dda9f-145">This command turns on debugging on the device</span></span> 

<span data-ttu-id="dda9f-146">在开发人员电脑上, 获取在系统中为 USB 到 TTL 电缆分配的 COM 端口号端口。</span><span class="sxs-lookup"><span data-stu-id="dda9f-146">On the developer PC, get the COM port number PORT assigned in the system for the USB-to-TTL cable.</span></span> <span data-ttu-id="dda9f-147">这会在 "端口 (COM & LPT)" 下的设备管理器中使用。</span><span class="sxs-lookup"><span data-stu-id="dda9f-147">This will be available in Device Manager under "Ports (COM & LPT)".</span></span>

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * <span data-ttu-id="dda9f-148">用端口号开始 WinDbg</span><span class="sxs-lookup"><span data-stu-id="dda9f-148">Start WinDbg with the PORT number</span></span>
    
> [!NOTE]
> <span data-ttu-id="dda9f-149">如果你安装了任何 Windows 工具包, 你可能会发现`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`</span><span class="sxs-lookup"><span data-stu-id="dda9f-149">If you have any of the Windows kits installed, you may find WinDbg under `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`</span></span>

* <span data-ttu-id="dda9f-150">重新启动 IoTCore 设备以重新连接到调试器</span><span class="sxs-lookup"><span data-stu-id="dda9f-150">Reboot the IoTCore device to reconnect to the debugger</span></span>


## <a name="dragonboard-db"></a><span data-ttu-id="dda9f-151">DragonBoard (DB)</span><span class="sxs-lookup"><span data-stu-id="dda9f-151">DragonBoard (DB)</span></span> 
___

<span data-ttu-id="dda9f-152">可以使用串行或 USB 连接将 WinDbg 连接到 DragonBoard。</span><span class="sxs-lookup"><span data-stu-id="dda9f-152">You can connect WinDbg to the DragonBoard using a serial or USB connection.</span></span>

<span data-ttu-id="dda9f-153">使用 active PowerShell 或 SSH 连接到 DragonBoard, 执行以下命令以启用调试。</span><span class="sxs-lookup"><span data-stu-id="dda9f-153">Using the active PowerShell or SSH connection to your DragonBoard, execute the following commands to enable debugging.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * <span data-ttu-id="dda9f-154">启用调试器</span><span class="sxs-lookup"><span data-stu-id="dda9f-154">Enables the debugger</span></span>

### <a name="setup-usb-connection"></a><span data-ttu-id="dda9f-155">设置 USB 连接</span><span class="sxs-lookup"><span data-stu-id="dda9f-155">Setup USB connection</span></span>
<span data-ttu-id="dda9f-156">默认情况下, 在测试映像中配置 USB 调试器设置。</span><span class="sxs-lookup"><span data-stu-id="dda9f-156">By default the USB debugger settings are configured in the test images.</span></span> 

> [!NOTE]
> <span data-ttu-id="dda9f-157">启用 USB 内核调试器后, DragonBoard 设备上的 USB 端口可能不起作用 (即键盘, usb 以太网可能不起作用)。</span><span class="sxs-lookup"><span data-stu-id="dda9f-157">Once USB kernel debugger is on, USB ports on the DragonBoard device might not work (i.e. keyboard, usb ethernet might not work).</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="dda9f-158">设置串行连接</span><span class="sxs-lookup"><span data-stu-id="dda9f-158">Setup serial connection</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * <span data-ttu-id="dda9f-159">配置串行端口</span><span class="sxs-lookup"><span data-stu-id="dda9f-159">Configures the serial port</span></span>

* <span data-ttu-id="dda9f-160">重新启动 IoTCore 设备以重新连接到调试器</span><span class="sxs-lookup"><span data-stu-id="dda9f-160">Reboot the IoTCore device to reconnect to the debugger</span></span>
