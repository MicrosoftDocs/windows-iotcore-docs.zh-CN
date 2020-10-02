---
title: 网络数据包捕获
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Microsoft Message Analyzer 启用网络数据包捕获
keywords: windows iot，网络数据包，网络数据包捕获，Microsoft Message Analyzer，PowerShell
ms.openlocfilehash: fae796716e8dc5b4b51de0273a55e96a209476a1
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655553"
---
# <a name="network-packet-capture"></a>网络数据包捕获

> [!NOTE]
> Microsoft Message Analyzer 已 [弃用](https://docs.microsoft.com/openspecs/blog/ms-winintbloglp/dd98b93c-0a75-4eb0-b92e-e760c502394f)。 下面包含的信息仅用于存档引用。

可以使用 [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226) 来捕获、显示和分析 Windows 10 IoT Core 设备上的协议消息传送流量。

![消息分析器](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a>必备条件

[Powershell](../connect-your-device/PowerShell.md)中介绍的工作 powershell 连接 (步骤1到步骤8。

## <a name="set-up-your-device"></a>设置设备

若要使用 Message Analyzer 连接到设备，需要先重命名设备。  可以使用命令通过 [SSH](../connect-your-device/SSH.md) 或 [PowerShell](../connect-your-device/PowerShell.md) 完成此操作 `setcomputername` 。

![PowerShell 重命名设备](../media/NetworkPacketCapture/powershell-rename-device.png)

重命名设备后，重新启动设备以应用名称更改。

## <a name="turn-off-the-firewall"></a>关闭防火墙

使用 PowerShell 或 SSH 连接到设备，并运行以下命令以禁用防火墙。
```    
    netsh advfirewall set allprofiles state off
```    
## <a name="connect-to-your-device-using-message-analyzer"></a>使用消息分析器连接到设备

设置设备后，让我们使用 Microsoft Message Analyzer 连接到它。

1. 下载 [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226)。
2. 打开 Message Analyzer。
3. 单击 `New Session`。

    ![消息分析器1](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. 在打开的窗口中，单击 "" `Live Trace` 按钮。
    ![消息分析器2](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. 单击“”`Edit...`按钮。
    ![消息分析器3](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. 将 Localhost 替换为 IoT 设备的名称，并输入管理员用户名和密码。  然后单击 `OK` 。
    ![消息分析器4](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. 单击 `Select a trace scenario` 下拉列表并选择 `Local Network Interfaces` 。
    ![消息分析器5](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. 单击“`Start`”按钮。
9. 应该会看到消息通过设备上的网络接口。
    ![消息分析器6](../media/NetworkPacketCapture/message-analyzer.png)
10. 通过 Message Analyzer 启动跟踪后，还可以在设备的 [web 界面](DevicePortal.md)中查看数据包捕获驱动程序的 ETW 消息。  为此，请在 web 界面的 "ETW" 选项卡上， `Microsoft-Windows-NDIS-PacketCapture` 从下拉菜单中选择， `Registered providers` 然后单击 "" `Enable` 按钮。
    ![消息分析器7](../media/NetworkPacketCapture/web-etw.png)    
