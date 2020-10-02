---
title: Windows 调试器
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 调试器调试 Windows IoT Core 设备。
keywords: windows iot，调试程序，调试，Windows 调试器，设备，工具
ms.openlocfilehash: f2175f3c4fd7f36ce4f9d2e57e8fa101315f3dab
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655243"
---
# <a name="windows-debugger-windbg"></a>Windows 调试器 (WinDbg)
使用功能强大的 Windows 调试器 WinDbg 调试 Windows 10 IoT Core 设备。

以下部分介绍了如何将 WinDbg 成功连接到 Windows 10 IoT Core 设备，以便进行调试。  这包括设备上所需的软件设置以及物理硬件连接的说明。  

WinDbg 是非常强大的调试器，大多数 Windows 开发人员都非常熟悉。  不过，如果你刚开始，想要了解有关 WinDbg 的详细信息，请访问以下链接：

* [Windows 调试工具](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)

* [Windows 调试入门](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)

* [使用 WinDbg 进行故障转储分析](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)


## <a name="minnowboard-max-mbm"></a>MinnowBoard Max (MBM) 

可以使用网络连接将 MinnowBoard 连接到最大设备。

### <a name="setup-network-connection"></a>设置网络连接

若要在网络上使用 WinDbg 启用内核调试，请确保：

* 将以太网电缆连接到网络上的 MinnowBoard Max 设备

* MinnowBoard Max 设备在你的网络中具有有效的 IP 地址

* 通过[PowerShell](../connect-your-device/PowerShell.md)与 MinnowBoard Max 设备建立活动连接

使用 active PowerShell 连接，对 MinnowBoard Max 执行以下命令，以启用通过网络进行调试。

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>`

    * 此命令启用通过网络进行调试。  此外，它还指定 (DEV_PC_IP_ADDRESS) 的 PC 的 IP 地址、用于连接 (PORT_NUM) 的网络端口号，以及用于区分多个连接 (密钥的唯一密钥) 

    * 对于 PORT_NUM 和 KEY，你可以使用以下值作为示例：分别为50045和1.2.3.4，但你可以根据自己的需要随时对其进行更改

* `bcdedit -debug on`

    * 此命令将在设备上启用调试

* 在开发人员电脑上，用前面步骤中提供的 PORT_NUM 和键值启动 WinDbg，如下所示： `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`

> [!NOTE]
> 如果你安装了任何 Windows 工具包，你可能会发现 `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* 重新启动 IoTCore 设备以重新连接到调试器

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a>Raspberry Pi 2 或 3 (RPi2 或 RPi3) 

可以使用串行连接将 WinDbg 连接到 Raspberry Pi 2 或3。

### <a name="setup-serial-connection"></a>设置串行连接

若要在串行连接上使用 WinDbg 启用内核调试，请确保：

* 有一个调试电缆，如来自 [Adafruit](https://www.adafruit.com/product/954) 或 [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105)的 USB 到 TTL 串行电缆。

* 将 Raspberry Pi 2 或3设备连接到网络的以太网电缆或活动 WiFi (用于 IP 连接，如 SSH 或 PowerShell) 

* Raspberry Pi 2 或3设备在网络中具有有效的 IP 地址

* 通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)与 Raspberry Pi 2 或3设备建立活动连接

对于内核调试连接，将在 Raspberry Pi 2 或3设备上使用 UART0。  下面显示了 Raspberry Pi 2 或3以及串行电缆的 pin 映射：
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
建立正确的串行连接的基本思路是，在一个设备使用其 TX 传输数据时，另一个设备会使用其 RX 来接收数据。  下面列出了推荐的连接：
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
> 不再创建 EFIESP 联接。 你必须自行装载，你可以使用 mountvol 命令来获取 GUID。
`mkdir C:\EFIESP`
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}`

使用活动的 PowerShell 连接，在 Raspberry Pi 2 或3设备上执行以下命令，以启用通过串行连接进行调试。

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial`

    * 上述命令启用串行连接以进行调试
    * Raspberry Pi 2 或3的波特率硬编码为921600，因此您无需指定它

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * 此命令将在设备上启用调试

在开发人员电脑上，获取在系统中为 USB 到 TTL 电缆分配的 COM 端口号端口。 这将在 "端口 (COM & LPT) " 下设备管理器。

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600`

    * 用端口号开始 WinDbg

> [!NOTE]
> 如果你安装了任何 Windows 工具包，你可能会发现 `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* 重新启动 IoTCore 设备以重新连接到调试器


## <a name="dragonboard-db"></a>DragonBoard (DB) 
___

可以使用串行或 USB 连接将 WinDbg 连接到 DragonBoard。

使用 active PowerShell 或 SSH 连接到 DragonBoard，执行以下命令以启用调试。

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * 启用调试器

### <a name="setup-usb-connection"></a>设置 USB 连接
默认情况下，在测试映像中配置 USB 调试器设置。

> [!NOTE]
> 启用 USB 内核调试器后，DragonBoard 设备上的 USB 端口可能无法工作 (例如键盘，usb 以太网可能无法) 。

### <a name="setup-serial-connection"></a>设置串行连接

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * 配置串行端口

* 重新启动 IoTCore 设备以重新连接到调试器
