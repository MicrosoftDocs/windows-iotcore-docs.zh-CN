---
title: 网络数据包捕获
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Microsoft Message Analyzer 以启用网络数据包捕获
keywords: windows iot、 网络数据包、 网络数据包捕获，Microsoft Message Analyzer，PowerShell
ms.openlocfilehash: 1880b6502099c50653e9e60ebc3d4ff3cd926450
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510710"
---
# <a name="network-packet-capture"></a>网络数据包捕获

可以使用[Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226)可以捕获、 显示和分析协议消息传送你的 Windows 10 IoT Core 设备上的流量。

![消息分析器](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a>先决条件

使用 PowerShell 连接 (步骤 1 到 8 中所述[PowerShell](../connect-your-device/PowerShell.md)。

## <a name="set-up-your-device"></a>设置你的设备

若要连接到你的设备使用 Message Analyzer，您需要首先重命名你的设备。  这可以通过[SSH](../connect-your-device/SSH.md)或[PowerShell](../connect-your-device/PowerShell.md)使用`setcomputername`命令。

![PowerShell 重命名设备](../media/NetworkPacketCapture/powershell-rename-device.png)

重命名你的设备后，重新启动设备以应用更改后的名称。

## <a name="turn-off-the-firewall"></a>关闭防火墙

连接到你使用 PowerShell 或 ssh 连接的设备并运行以下命令以禁用防火墙。
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a>连接到你的设备使用 Message Analyzer

现在，你的设备设置了，让我们使用 Microsoft Message Analyzer 的与其连接。

1. 下载[Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226)。
2. 打开消息分析器。
3. 单击`New Session`。

    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. 在打开的窗口，单击`Live Trace`按钮。
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. 单击`Edit...`按钮。
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. Localhost 替换为你的 IoT 设备的名称，并输入管理员用户名和密码。  然后单击“`OK`”。
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. 单击`Select a trace scenario`下拉列表中，然后选择`Local Network Interfaces`。
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. 单击`Start`按钮。
9. 您应该可以看到在设备上经过的网络接口的消息。
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer.png)
10. 启动 Message Analyzer 通过跟踪后，还可以在你的设备中查看数据包捕获驱动程序中的 ETW 消息[web 界面](DevicePortal.md)。  要执行此操作，请转到 web 界面中选择 ETW 选项卡`Microsoft-Windows-NDIS-PacketCapture`从`Registered providers`下拉列表菜单单击`Enable`按钮。
    ![消息分析器](../media/NetworkPacketCapture/web-etw.png)    
