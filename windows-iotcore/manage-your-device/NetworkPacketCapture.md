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
# <a name="network-packet-capture"></a><span data-ttu-id="a7d93-104">网络数据包捕获</span><span class="sxs-lookup"><span data-stu-id="a7d93-104">Network packet capture</span></span>

<span data-ttu-id="a7d93-105">可以使用[Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226)可以捕获、 显示和分析协议消息传送你的 Windows 10 IoT Core 设备上的流量。</span><span class="sxs-lookup"><span data-stu-id="a7d93-105">You can use [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) to capture, display, and analyze protocol messaging traffic on your Windows 10 IoT Core device.</span></span>

![消息分析器](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a><span data-ttu-id="a7d93-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="a7d93-107">Prerequisites</span></span>

<span data-ttu-id="a7d93-108">使用 PowerShell 连接 (步骤 1 到 8 中所述[PowerShell](../connect-your-device/PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="a7d93-108">Working PowerShell Connection (Step 1 to 8 described at [PowerShell](../connect-your-device/PowerShell.md).</span></span>

## <a name="set-up-your-device"></a><span data-ttu-id="a7d93-109">设置你的设备</span><span class="sxs-lookup"><span data-stu-id="a7d93-109">Set up your device</span></span>

<span data-ttu-id="a7d93-110">若要连接到你的设备使用 Message Analyzer，您需要首先重命名你的设备。</span><span class="sxs-lookup"><span data-stu-id="a7d93-110">In order to connect to your device using Message Analyzer, you need to first rename your device.</span></span>  <span data-ttu-id="a7d93-111">这可以通过[SSH](../connect-your-device/SSH.md)或[PowerShell](../connect-your-device/PowerShell.md)使用`setcomputername`命令。</span><span class="sxs-lookup"><span data-stu-id="a7d93-111">This can be done through [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/PowerShell.md) using the `setcomputername` command.</span></span>

![PowerShell 重命名设备](../media/NetworkPacketCapture/powershell-rename-device.png)

<span data-ttu-id="a7d93-113">重命名你的设备后，重新启动设备以应用更改后的名称。</span><span class="sxs-lookup"><span data-stu-id="a7d93-113">After you rename your device, reboot the device to apply the name change.</span></span>

## <a name="turn-off-the-firewall"></a><span data-ttu-id="a7d93-114">关闭防火墙</span><span class="sxs-lookup"><span data-stu-id="a7d93-114">Turn off the firewall</span></span>

<span data-ttu-id="a7d93-115">连接到你使用 PowerShell 或 ssh 连接的设备并运行以下命令以禁用防火墙。</span><span class="sxs-lookup"><span data-stu-id="a7d93-115">Connect to your device using PowerShell or SSH and run the following command to disable the firewall.</span></span>
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a><span data-ttu-id="a7d93-116">连接到你的设备使用 Message Analyzer</span><span class="sxs-lookup"><span data-stu-id="a7d93-116">Connect to your device using Message Analyzer</span></span>

<span data-ttu-id="a7d93-117">现在，你的设备设置了，让我们使用 Microsoft Message Analyzer 的与其连接。</span><span class="sxs-lookup"><span data-stu-id="a7d93-117">Now that your device is set up, let's connect to it using Microsoft Message Analyzer.</span></span>

1. <span data-ttu-id="a7d93-118">下载[Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226)。</span><span class="sxs-lookup"><span data-stu-id="a7d93-118">Download the [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226).</span></span>
2. <span data-ttu-id="a7d93-119">打开消息分析器。</span><span class="sxs-lookup"><span data-stu-id="a7d93-119">Open Message Analyzer.</span></span>
3. <span data-ttu-id="a7d93-120">单击`New Session`。</span><span class="sxs-lookup"><span data-stu-id="a7d93-120">Click on `New Session`.</span></span>

    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. <span data-ttu-id="a7d93-122">在打开的窗口，单击`Live Trace`按钮。</span><span class="sxs-lookup"><span data-stu-id="a7d93-122">In the window that opens, click on the `Live Trace` button.</span></span>
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. <span data-ttu-id="a7d93-124">单击`Edit...`按钮。</span><span class="sxs-lookup"><span data-stu-id="a7d93-124">Click on the `Edit...` button.</span></span>
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. <span data-ttu-id="a7d93-126">Localhost 替换为你的 IoT 设备的名称，并输入管理员用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="a7d93-126">Replace Localhost with the name of your IoT device, and enter the administrator user name and password.</span></span>  <span data-ttu-id="a7d93-127">然后单击“`OK`”。</span><span class="sxs-lookup"><span data-stu-id="a7d93-127">Then click `OK`.</span></span>
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. <span data-ttu-id="a7d93-129">单击`Select a trace scenario`下拉列表中，然后选择`Local Network Interfaces`。</span><span class="sxs-lookup"><span data-stu-id="a7d93-129">Click on the `Select a trace scenario` dropdown and select `Local Network Interfaces`.</span></span>
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. <span data-ttu-id="a7d93-131">单击`Start`按钮。</span><span class="sxs-lookup"><span data-stu-id="a7d93-131">Click the `Start` button.</span></span>
9. <span data-ttu-id="a7d93-132">您应该可以看到在设备上经过的网络接口的消息。</span><span class="sxs-lookup"><span data-stu-id="a7d93-132">You should start to see the messages going through the network interfaces on your device.</span></span>
    ![消息分析器](../media/NetworkPacketCapture/message-analyzer.png)
10. <span data-ttu-id="a7d93-134">启动 Message Analyzer 通过跟踪后，还可以在你的设备中查看数据包捕获驱动程序中的 ETW 消息[web 界面](DevicePortal.md)。</span><span class="sxs-lookup"><span data-stu-id="a7d93-134">After you start the trace through Message Analyzer, you can also view the ETW messages from the packet capture driver in your device's [web interface](DevicePortal.md).</span></span>  <span data-ttu-id="a7d93-135">要执行此操作，请转到 web 界面中选择 ETW 选项卡`Microsoft-Windows-NDIS-PacketCapture`从`Registered providers`下拉列表菜单单击`Enable`按钮。</span><span class="sxs-lookup"><span data-stu-id="a7d93-135">To do this, go to the ETW tab of the web interface, select `Microsoft-Windows-NDIS-PacketCapture` from the `Registered providers` dropdown menu and click the `Enable` button.</span></span>
    ![消息分析器](../media/NetworkPacketCapture/web-etw.png)    
