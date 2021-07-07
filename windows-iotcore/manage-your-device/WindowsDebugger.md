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
# <a name="windows-debugger-windbg"></a>Windows 调试器 (WinDbg)
使用功能强大的 Windows 10 IoT 核心版调试器 WinDbg 调试Windows设备。

以下部分介绍如何使用 WinDbg 成功连接到Windows 10 IoT 核心版设备进行调试。  这包括对设备上必需的软件设置以及物理硬件连接的说明。  

WinDbg 是一种非常强大的调试器，Windows开发人员熟悉的调试器。  但是，如果你刚开始操作，并且想了解有关 WinDbg 的更多信息，请访问以下链接：

* [Windows 调试工具](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)

* [Windows 调试入门](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)

* [使用 WinDbg 进行故障转储分析](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)


## <a name="minnowboard-max-mbm"></a>MinnowBoard Max (MBM) 

可以使用网络连接将 WinDbg 连接到 MinnowBoard Max 设备。

### <a name="setup-network-connection"></a>设置网络连接

若要通过网络启用 WinDbg 的内核调试，请确保：

* 以太网电缆连接到 MinnowBoard Max 设备连接到网络

* MinnowBoard Max 设备在网络中具有有效的 IP 地址

* 通过 PowerShell 与 MinnowBoard Max 设备建立 [的活动连接](../connect-your-device/PowerShell.md)

使用活动的 PowerShell 连接，在 MinnowBoard Max 上执行以下命令，以启用网络调试。

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>`

    * 此命令允许通过网络进行调试。  此外，它还指定运行 WinDbg 的电脑的 IP 地址 (DEV_PC_IP_ADDRESS) 用于连接 (PORT_NUM) 的网络端口号，以及用于区分多个连接的唯一密钥 (KEY) 

    * 对于 PORT_NUM 和 KEY，可以使用以下值作为示例：分别为 50045 和 1.2.3.4，尽管你可随意更改它们

* `bcdedit -debug on`

    * 此命令在设备上启用调试

* 在开发人员电脑上，使用 PORT_NUM和前面步骤中提供的 KEY 值启动 WinDbg，如下所示： `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`

> [!NOTE]
> 如果安装了任何 Windows工具包，则可能会发现 WinDbg 在`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* 重新启动 IoTCore 设备以重新连接到调试器

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a>Raspberry Pi 2 或 3 (RPi2 或 RPi3) 

可以使用串行连接将 WinDbg 连接到 Raspberry Pi 2 或 3。

### <a name="setup-serial-connection"></a>设置串行连接

若要通过串行连接启用 WinDbg 的内核调试，请确保：

* 你有一条调试电缆，例如 [Adafruit](https://www.adafruit.com/product/954) 或 [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105)中的 USB 到 TTL 串行电缆。

* 将 Raspberry Pi 2 或 3 设备连接到网络连接的以太网电缆或活动 WiFi (SSH 或 PowerShell) 

* Raspberry Pi 2 或 3 设备在网络中具有有效的 IP 地址

* 通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)与 Raspberry Pi 2 或 3 设备建立的活动连接

UART0 将在 Raspberry Pi 2 或 3 设备上用于内核调试连接。  下面显示了 Raspberry Pi 2 或 3 的引脚映射以及串行电缆：
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
进行正确的串行连接的基本思路是记住，一台设备使用其 TX 传输数据，而另一台设备使用其 RX 接收数据。  下面列出了建议的连接：
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
> 不再创建 EFIESP 交接点。 你必须自己装载它，可以使用 mountvol 命令获取 GUID。
`mkdir C:\EFIESP`
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}`

使用活动的 PowerShell 连接，在 Raspberry Pi 2 或 3 设备上执行以下命令，以启用通过串行连接进行调试。

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial`

    * 上述命令启用用于调试的串行连接
    * Raspberry Pi 2 或 3 的波特率硬编码为 921600，因此不必指定它

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * 此命令在设备上启用调试

在开发人员电脑上，获取系统中为 USB 到 TTL 电缆分配的 COM 端口号端口。 这将在"端口 设备管理器 COM (LPT &"下) 。

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600`

    * 使用端口号启动 WinDbg

> [!NOTE]
> 如果安装了任何 Windows工具包，则可能会发现 WinDbg 在`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* 重新启动 IoTCore 设备以重新连接到调试器


## <a name="dragonboard-db"></a>DragonBoard (DB) 
___

可以使用串行或 USB 连接将 WinDbg 连接到 DragonBoard。

使用与 DragonBoard 的活动 PowerShell 或 SSH 连接，执行以下命令以启用调试。

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * 启用调试器

### <a name="setup-usb-connection"></a>设置 USB 连接
默认情况下，USB 调试器设置在测试映像中配置。

> [!NOTE]
> 打开 USB 内核调试器后，DragonBoard (上的 USB 端口可能无法工作，即，usb 以太网可能无法) 。

### <a name="setup-serial-connection"></a>设置串行连接

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * 配置串行端口

* 重新启动 IoTCore 设备以重新连接到调试器
