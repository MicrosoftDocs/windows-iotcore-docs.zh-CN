---
title: Windows 调试器
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 调试器来调试 Windows IoT Core 设备。
keywords: windows iot，调试器，调试时，Windows 调试器、 设备、 工具
ms.openlocfilehash: e56f5ca837de79aaf0c36cf7d3c6ae6badf3fd16
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510869"
---
# <a name="windows-debugger-windbg"></a>Windows Debugger (WinDbg)
使用功能强大的 Windows 调试器 WinDbg 调试 Windows 10 IoT 核心版设备。

以下部分介绍如何成功将 WinDbg 连接到 Windows 10 IoT 核心版设备以实现调试目的。  这包括描述设备上的必要软件设置以及物理硬件连接。  

WinDbg 是一个非常强大的调试程序，大多数 Windows 开发人员都对其了如指掌。  但是，如果你还不熟悉，并且想要了解有关 WinDbg 的详细信息，请访问以下链接：

* [Windows 调试工具](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx) 

* [Windows 调试入门](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx) 

* [故障转储分析使用 WinDbg](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx) 


## <a name="minnowboard-max-mbm"></a>MinnowBoard Max (MBM) 

您可以连接到使用网络连接的 MinnowBoard 最大设备 WinDbg。

### <a name="setup-network-connection"></a>设置网络连接

若要启用使用 WinDbg 通过网络进行内核调试，请确保：

* 以太网电缆连接到 MinnowBoard 最大到您的网络设备 

* MinnowBoard 最大设备在网络中具有有效的 IP 地址

* 与通过 MinnowBoard 最大设备的活动连接[PowerShell](../connect-your-device/PowerShell.md) 

使用活动的 PowerShell 连接，MinnowBoard 最大值以启用调试通过网络上执行以下命令。

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * 此命令可通过网络启用调试。  此外，它还可指定将要运行 WinDbg (DEV_PC_IP_ADDRESS) 的电脑的 IP 地址、用于连接的网络端口号 (PORT_NUM)，以及用于区分多个连接的唯一密钥 (KEY) 

    * 对于 PORT_NUM 和 KEY，可使用以下值作为示例：分别是 50045 和 1.2.3.4，尽管你可以根据需要更改它们
    
* `bcdedit -debug on`

    * 此命令将在设备上打开调试 

* 开发人员电脑，WinDbg PORT_NUM 和开始，如下所示的上一步骤中提供的密钥值： `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`

> [!NOTE]
> 如果您有任何安装的 Windows 工具包，您可能会发现在 WinDbg
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* 重新启动 IoTCore 设备重新连接到调试器

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a>Raspberry Pi 2 或 3（RPi2 或 RPi3） 

可使用串行连接将 WinDbg 连接到 Raspberry Pi 2 或 3。

### <a name="setup-serial-connection"></a>设置串行连接

若要启用内核调试与 WinDbg 通过串行连接，请确保：

* 你具有调试电缆，例如 [Adafruit](https://www.adafruit.com/product/954) 或 [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105) 中的 USB-to-TTL 的串行电缆。 

* 以太网电缆或活动的 WiFi 连接到您的网络 （用于 IP 连接 SSH 或 PowerShell 等） 在 Raspberry Pi 2 或 3 个设备

* Raspberry Pi 2 或 3 个设备在网络中具有有效的 IP 地址

* 活动连接到 Raspberry Pi 2 或 3 个设备通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)

将 Raspberry Pi 2 或 3 适用于内核调试连接设备上使用 UART0。  下面介绍了 Raspberry Pi 2 或 3 的 PIN 映射以及串行电缆： 

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
            
进行正确的串行连接的基本思想是，记住当一台设备使用其 TX 传输数据时，另一台设备使用其 RX 接收该数据。  下面列出了建议的连接：

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> 不能再创建 EFIESP 交接点。 您必须自己装载，可以使用 mountvol 命令要获取 GUID。
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

使用活动的 PowerShell 连接，Raspberry Pi 2 或 3 个设备以启用调试通过串行连接上执行以下命令。

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * 上述命令可启用用于调试的串行连接
    * Raspberry Pi 2 或 3 波特率已硬编码到 921600，因此无需指定它

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * 此命令将在设备上打开调试 

开发人员电脑，获取 COM 端口分配到 TTL USB 电缆系统中的数字端口。 这将在设备管理器中"（COM 和 LPT） 端口"下提供。

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * 启动 WinDbg 时端口号
    
> [!NOTE]
> 如果您有任何安装的 Windows 工具包，您可能会发现在 WinDbg
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* 重新启动 IoTCore 设备重新连接到调试器


## <a name="dragonboard-db"></a>DragonBoard (DB) 
___

你可以连接到使用串行或 USB 连接 DragonBoard WinDbg。

使用活动的 PowerShell 或 SSH 连接到你 DragonBoard，执行以下命令以启用调试。

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * 使调试器

### <a name="setup-usb-connection"></a>安装 USB 连接
默认情况下测试映像中配置 USB 调试程序设置。 

> [!NOTE]
> 在 USB 内核调试程序后，DragonBoard 设备上的 USB 端口可能无法工作 （即键盘，usb 以太网可能不起作用）。

### <a name="setup-serial-connection"></a>设置串行连接

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * 配置的串行端口

* 重新启动 IoTCore 设备重新连接到调试器
