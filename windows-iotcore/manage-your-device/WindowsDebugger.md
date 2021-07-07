---
title: Windows 调试器
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 调试器来调试 Windows IoT Core 设备。
keywords: windows iot， 调试器， 调试， Windows调试器， 设备， 工具
ms.openlocfilehash: 56d88181b766ed8cfbe96d567086c32b33d3bfb1
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228703"
---
# <a name="windows-debugger-windbg"></a><span data-ttu-id="09815-104">Windows 调试器 (WinDbg)</span><span class="sxs-lookup"><span data-stu-id="09815-104">Windows Debugger (WinDbg)</span></span>
<span data-ttu-id="09815-105">使用功能强大的 Windows 10 IoT 核心版调试器 WinDbg 调试Windows设备。</span><span class="sxs-lookup"><span data-stu-id="09815-105">Debug your Windows 10 IoT Core device using the powerful Windows debugger, WinDbg.</span></span>

<span data-ttu-id="09815-106">以下部分介绍如何使用 WinDbg 成功连接到Windows 10 IoT 核心版设备进行调试。</span><span class="sxs-lookup"><span data-stu-id="09815-106">The following sections describe how to successfully connect with WinDbg to a Windows 10 IoT Core device for debugging purposes.</span></span>  <span data-ttu-id="09815-107">这包括对设备上必需的软件设置以及物理硬件连接的说明。</span><span class="sxs-lookup"><span data-stu-id="09815-107">This includes a description of the necessary software settings on the device as well as the physical hardware connections.</span></span>  

<span data-ttu-id="09815-108">WinDbg 是一种非常强大的调试器，Windows开发人员熟悉的调试器。</span><span class="sxs-lookup"><span data-stu-id="09815-108">WinDbg is a very powerful debugger that most Windows developers are familiar with.</span></span>  <span data-ttu-id="09815-109">但是，如果你刚开始操作，并且想了解有关 WinDbg 的更多信息，请访问以下链接：</span><span class="sxs-lookup"><span data-stu-id="09815-109">However, if you are just getting started and would like to learn more about WinDbg, please visit the following links:</span></span>

* <span data-ttu-id="09815-110">[Windows 调试工具](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="09815-110">[Debugging Tools for Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)</span></span>

* <span data-ttu-id="09815-111">[Windows 调试入门](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="09815-111">[Getting Started with Windows Debugging](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)</span></span>

* <span data-ttu-id="09815-112">[使用 WinDbg 进行故障转储分析](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="09815-112">[Crash Dump Analysis Using WinDbg](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)</span></span>


## <a name="minnowboard-max-mbm"></a><span data-ttu-id="09815-113">MinnowBoard Max (MBM) </span><span class="sxs-lookup"><span data-stu-id="09815-113">MinnowBoard Max (MBM)</span></span>

<span data-ttu-id="09815-114">可以使用网络连接将 WinDbg 连接到 MinnowBoard Max 设备。</span><span class="sxs-lookup"><span data-stu-id="09815-114">You can connect WinDbg to the MinnowBoard Max device using a network connection.</span></span>

### <a name="setup-network-connection"></a><span data-ttu-id="09815-115">设置网络连接</span><span class="sxs-lookup"><span data-stu-id="09815-115">Setup network connection</span></span>

<span data-ttu-id="09815-116">若要通过网络启用 WinDbg 的内核调试，请确保：</span><span class="sxs-lookup"><span data-stu-id="09815-116">In order to enable kernel debugging with WinDbg over a network, ensure that:</span></span>

* <span data-ttu-id="09815-117">以太网电缆连接到 MinnowBoard Max 设备连接到网络</span><span class="sxs-lookup"><span data-stu-id="09815-117">An Ethernet cable is connected to MinnowBoard Max device to your network</span></span>

* <span data-ttu-id="09815-118">MinnowBoard Max 设备在网络中具有有效的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="09815-118">The MinnowBoard Max device has a valid IP address in your network</span></span>

* <span data-ttu-id="09815-119">通过 PowerShell 与 MinnowBoard Max 设备建立 [的活动连接](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="09815-119">An active connection to the MinnowBoard Max device via [PowerShell](../connect-your-device/PowerShell.md)</span></span>

<span data-ttu-id="09815-120">使用活动的 PowerShell 连接，在 MinnowBoard Max 上执行以下命令，以启用网络调试。</span><span class="sxs-lookup"><span data-stu-id="09815-120">Using the active PowerShell connection, execute the following commands on the MinnowBoard Max to enable debugging over the network.</span></span>

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>`

    * <span data-ttu-id="09815-121">此命令允许通过网络进行调试。</span><span class="sxs-lookup"><span data-stu-id="09815-121">This command enables debugging over the network.</span></span>  <span data-ttu-id="09815-122">此外，它还指定运行 WinDbg 的电脑的 IP 地址 (DEV_PC_IP_ADDRESS) 用于连接 (PORT_NUM) 的网络端口号，以及用于区分多个连接的唯一密钥 (KEY) </span><span class="sxs-lookup"><span data-stu-id="09815-122">Additionally, it specifies the IP address of the PC where WinDbg will be running (DEV_PC_IP_ADDRESS), the network port number to use for the connection (PORT_NUM), and a unique key to be used to differentiate multiple connections (KEY)</span></span>

    * <span data-ttu-id="09815-123">对于 PORT_NUM 和 KEY，可以使用以下值作为示例：分别为 50045 和 1.2.3.4，尽管你可随意更改它们</span><span class="sxs-lookup"><span data-stu-id="09815-123">For PORT_NUM and KEY, you can use the following values as examples: 50045 and 1.2.3.4 respectively, although you are free to change them as you see fit</span></span>

* `bcdedit -debug on`

    * <span data-ttu-id="09815-124">此命令在设备上启用调试</span><span class="sxs-lookup"><span data-stu-id="09815-124">This command turns on debugging on the device</span></span>

* <span data-ttu-id="09815-125">在开发人员电脑上，使用 PORT_NUM和前面步骤中提供的 KEY 值启动 WinDbg，如下所示： `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span><span class="sxs-lookup"><span data-stu-id="09815-125">On the developer PC, start WinDbg with the PORT_NUM and the KEY values provided in the previous steps as follows: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span></span>

> [!NOTE]
> <span data-ttu-id="09815-126">如果安装了任何 Windows工具包，则可能会发现 WinDbg 在`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`</span><span class="sxs-lookup"><span data-stu-id="09815-126">If you have any of the Windows kits installed, you may find WinDbg under `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`</span></span>

* <span data-ttu-id="09815-127">重新启动 IoTCore 设备以重新连接到调试器</span><span class="sxs-lookup"><span data-stu-id="09815-127">Reboot the IoTCore device to reconnect to the debugger</span></span>

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a><span data-ttu-id="09815-128">Raspberry Pi 2 或 3 (RPi2 或 RPi3) </span><span class="sxs-lookup"><span data-stu-id="09815-128">Raspberry Pi 2 or 3 (RPi2 or RPi3)</span></span>

<span data-ttu-id="09815-129">可以使用串行连接将 WinDbg 连接到 Raspberry Pi 2 或 3。</span><span class="sxs-lookup"><span data-stu-id="09815-129">You can connect WinDbg to the Raspberry Pi 2 or 3 using a serial connection.</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="09815-130">设置串行连接</span><span class="sxs-lookup"><span data-stu-id="09815-130">Setup serial connection</span></span>

<span data-ttu-id="09815-131">若要通过串行连接启用 WinDbg 的内核调试，请确保：</span><span class="sxs-lookup"><span data-stu-id="09815-131">In order to enable kernel debugging with WinDbg over a serial connection, ensure that:</span></span>

* <span data-ttu-id="09815-132">你有一条调试电缆，例如 [Adafruit](https://www.adafruit.com/product/954) 或 [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105)中的 USB 到 TTL 串行电缆。</span><span class="sxs-lookup"><span data-stu-id="09815-132">You have a debug cable such as the USB-to-TTL Serial Cable from [Adafruit](https://www.adafruit.com/product/954) or [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105).</span></span>

* <span data-ttu-id="09815-133">将 Raspberry Pi 2 或 3 设备连接到网络连接的以太网电缆或活动 WiFi (SSH 或 PowerShell) </span><span class="sxs-lookup"><span data-stu-id="09815-133">An Ethernet cable or active WiFi connecting your Raspberry Pi 2 or 3 device to your network (for IP connections like SSH or PowerShell)</span></span>

* <span data-ttu-id="09815-134">Raspberry Pi 2 或 3 设备在网络中具有有效的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="09815-134">The Raspberry Pi 2 or 3 device has a valid IP address in your network</span></span>

* <span data-ttu-id="09815-135">通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)与 Raspberry Pi 2 或 3 设备建立的活动连接</span><span class="sxs-lookup"><span data-stu-id="09815-135">An active connection to the Raspberry Pi 2 or 3 device via [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md)</span></span>

<span data-ttu-id="09815-136">UART0 将在 Raspberry Pi 2 或 3 设备上用于内核调试连接。</span><span class="sxs-lookup"><span data-stu-id="09815-136">UART0 will be used on the Raspberry Pi 2 or 3 device for the kernel debugging connection.</span></span>  <span data-ttu-id="09815-137">下面显示了 Raspberry Pi 2 或 3 的引脚映射以及串行电缆：</span><span class="sxs-lookup"><span data-stu-id="09815-137">The following shows the pin mappings for the Raspberry Pi 2 or 3 as well as the serial cables:</span></span>
```
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
```         
<span data-ttu-id="09815-138">进行正确的串行连接的基本思路是记住，一台设备使用其 TX 传输数据，而另一台设备使用其 RX 接收数据。</span><span class="sxs-lookup"><span data-stu-id="09815-138">The basic idea for making the correct serial connections is to remember that while one device uses its TX to transmit data, the other device uses its RX to receive the data.</span></span>  <span data-ttu-id="09815-139">下面列出了建议的连接：</span><span class="sxs-lookup"><span data-stu-id="09815-139">Recommended connections are listed below:</span></span>
```
        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX)
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)

        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX)
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)
```
> [!NOTE]
> <span data-ttu-id="09815-140">不再创建 EFIESP 交接点。</span><span class="sxs-lookup"><span data-stu-id="09815-140">The EFIESP junction is no longer created.</span></span> <span data-ttu-id="09815-141">你必须自己装载它，可以使用 mountvol 命令获取 GUID。</span><span class="sxs-lookup"><span data-stu-id="09815-141">You'll have to mount it yourself,you can use mountvol command to get the GUID.</span></span>
`mkdir C:\EFIESP`
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}`

<span data-ttu-id="09815-142">使用活动的 PowerShell 连接，在 Raspberry Pi 2 或 3 设备上执行以下命令，以启用通过串行连接进行调试。</span><span class="sxs-lookup"><span data-stu-id="09815-142">Using the active PowerShell connection, execute the following commands on the Raspberry Pi 2 or 3 device to enable debugging over the serial connection.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial`

    * <span data-ttu-id="09815-143">上述命令启用用于调试的串行连接</span><span class="sxs-lookup"><span data-stu-id="09815-143">The above command enables the serial connection for debugging</span></span>
    * <span data-ttu-id="09815-144">Raspberry Pi 2 或 3 的波特率硬编码为 921600，因此不必指定它</span><span class="sxs-lookup"><span data-stu-id="09815-144">The baud-rate for the Raspberry Pi 2 or 3 is hard-coded to 921600, so you don't have to specify it</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * <span data-ttu-id="09815-145">此命令在设备上启用调试</span><span class="sxs-lookup"><span data-stu-id="09815-145">This command turns on debugging on the device</span></span>

<span data-ttu-id="09815-146">在开发人员电脑上，获取系统中为 USB 到 TTL 电缆分配的 COM 端口号端口。</span><span class="sxs-lookup"><span data-stu-id="09815-146">On the developer PC, get the COM port number PORT assigned in the system for the USB-to-TTL cable.</span></span> <span data-ttu-id="09815-147">这将在"端口 设备管理器 COM (LPT &"下) 。</span><span class="sxs-lookup"><span data-stu-id="09815-147">This will be available in Device Manager under "Ports (COM & LPT)".</span></span>

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600`

    * <span data-ttu-id="09815-148">使用端口号启动 WinDbg</span><span class="sxs-lookup"><span data-stu-id="09815-148">Start WinDbg with the PORT number</span></span>

> [!NOTE]
> <span data-ttu-id="09815-149">如果安装了任何 Windows工具包，则可能会发现 WinDbg 在`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`</span><span class="sxs-lookup"><span data-stu-id="09815-149">If you have any of the Windows kits installed, you may find WinDbg under `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`</span></span>

* <span data-ttu-id="09815-150">重新启动 IoTCore 设备以重新连接到调试器</span><span class="sxs-lookup"><span data-stu-id="09815-150">Reboot the IoTCore device to reconnect to the debugger</span></span>


## <a name="dragonboard-db"></a><span data-ttu-id="09815-151">DragonBoard (DB) </span><span class="sxs-lookup"><span data-stu-id="09815-151">DragonBoard (DB)</span></span>
___

<span data-ttu-id="09815-152">可以使用串行或 USB 连接将 WinDbg 连接到 DragonBoard。</span><span class="sxs-lookup"><span data-stu-id="09815-152">You can connect WinDbg to the DragonBoard using a serial or USB connection.</span></span>

<span data-ttu-id="09815-153">使用与 DragonBoard 的活动 PowerShell 或 SSH 连接，执行以下命令以启用调试。</span><span class="sxs-lookup"><span data-stu-id="09815-153">Using the active PowerShell or SSH connection to your DragonBoard, execute the following commands to enable debugging.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * <span data-ttu-id="09815-154">启用调试器</span><span class="sxs-lookup"><span data-stu-id="09815-154">Enables the debugger</span></span>

### <a name="setup-usb-connection"></a><span data-ttu-id="09815-155">设置 USB 连接</span><span class="sxs-lookup"><span data-stu-id="09815-155">Setup USB connection</span></span>
<span data-ttu-id="09815-156">默认情况下，USB 调试器设置在测试映像中配置。</span><span class="sxs-lookup"><span data-stu-id="09815-156">By default the USB debugger settings are configured in the test images.</span></span>

> [!NOTE]
> <span data-ttu-id="09815-157">打开 USB 内核调试器后，DragonBoard (上的 USB 端口可能无法工作，即，usb 以太网可能无法) 。</span><span class="sxs-lookup"><span data-stu-id="09815-157">Once USB kernel debugger is on, USB ports on the DragonBoard device might not work (i.e. keyboard, usb ethernet might not work).</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="09815-158">设置串行连接</span><span class="sxs-lookup"><span data-stu-id="09815-158">Setup serial connection</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * <span data-ttu-id="09815-159">配置串行端口</span><span class="sxs-lookup"><span data-stu-id="09815-159">Configures the serial port</span></span>

* <span data-ttu-id="09815-160">重新启动 IoTCore 设备以重新连接到调试器</span><span class="sxs-lookup"><span data-stu-id="09815-160">Reboot the IoTCore device to reconnect to the debugger</span></span>
