---
title: 网络数据包捕获
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Microsoft Message Analyzer 启用网络数据包捕获
keywords: windows iot，网络数据包，网络数据包捕获，Microsoft Message Analyzer，PowerShell
ms.openlocfilehash: 20f280623fc8919a5ebd3b015ece7d29dbe40cb5
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721654"
---
# <a name="network-packet-capture"></a><span data-ttu-id="4dd5c-104">网络数据包捕获</span><span class="sxs-lookup"><span data-stu-id="4dd5c-104">Network packet capture</span></span>

<span data-ttu-id="4dd5c-105">可以使用[Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226)来捕获、显示和分析 Windows 10 IoT Core 设备上的协议消息传送流量。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-105">You can use [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226) to capture, display, and analyze protocol messaging traffic on your Windows 10 IoT Core device.</span></span>

![消息分析器](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a><span data-ttu-id="4dd5c-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="4dd5c-107">Prerequisites</span></span>

<span data-ttu-id="4dd5c-108">工作 PowerShell 连接（ [powershell](../connect-your-device/PowerShell.md)中介绍的步骤1到8。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-108">Working PowerShell Connection (Step 1 to 8 described at [PowerShell](../connect-your-device/PowerShell.md).</span></span>

## <a name="set-up-your-device"></a><span data-ttu-id="4dd5c-109">设置设备</span><span class="sxs-lookup"><span data-stu-id="4dd5c-109">Set up your device</span></span>

<span data-ttu-id="4dd5c-110">若要使用 Message Analyzer 连接到设备，需要先重命名设备。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-110">In order to connect to your device using Message Analyzer, you need to first rename your device.</span></span>  <span data-ttu-id="4dd5c-111">可以 使用`setcomputername`命令通过[SSH](../connect-your-device/SSH.md)或 [PowerShell](../connect-your-device/PowerShell.md) 完成此操作。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-111">This can be done through [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/PowerShell.md) using the `setcomputername` command.</span></span>

![PowerShell 重命名设备](../media/NetworkPacketCapture/powershell-rename-device.png)

<span data-ttu-id="4dd5c-113">重命名设备后，重新启动设备以应用名称更改。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-113">After you rename your device, reboot the device to apply the name change.</span></span>

## <a name="turn-off-the-firewall"></a><span data-ttu-id="4dd5c-114">关闭防火墙</span><span class="sxs-lookup"><span data-stu-id="4dd5c-114">Turn off the firewall</span></span>

<span data-ttu-id="4dd5c-115">使用 PowerShell 或 SSH 连接到设备，并运行以下命令以禁用防火墙。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-115">Connect to your device using PowerShell or SSH and run the following command to disable the firewall.</span></span>
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a><span data-ttu-id="4dd5c-116">使用消息分析器连接到设备</span><span class="sxs-lookup"><span data-stu-id="4dd5c-116">Connect to your device using Message Analyzer</span></span>

<span data-ttu-id="4dd5c-117">设置设备后，让我们使用 Microsoft Message Analyzer 连接到它。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-117">Now that your device is set up, let's connect to it using Microsoft Message Analyzer.</span></span>

1. <span data-ttu-id="4dd5c-118">下载[Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226)。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-118">Download the [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226).</span></span>
2. <span data-ttu-id="4dd5c-119">打开 Message Analyzer。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-119">Open Message Analyzer.</span></span>
3. <span data-ttu-id="4dd5c-120">单击 `New Session`。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-120">Click on `New Session`.</span></span>

    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. <span data-ttu-id="4dd5c-122">在打开的窗口中，单击 "`Live Trace`" 按钮。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-122">In the window that opens, click on the `Live Trace` button.</span></span>
    <span data-ttu-id="4dd5c-123">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span><span class="sxs-lookup"><span data-stu-id="4dd5c-123">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span></span>
5. <span data-ttu-id="4dd5c-124">单击 "`Edit...`" 按钮。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-124">Click on the `Edit...` button.</span></span>
    <span data-ttu-id="4dd5c-125">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span><span class="sxs-lookup"><span data-stu-id="4dd5c-125">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span></span>
6. <span data-ttu-id="4dd5c-126">将 Localhost 替换为 IoT 设备的名称，并输入管理员用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-126">Replace Localhost with the name of your IoT device, and enter the administrator user name and password.</span></span>  <span data-ttu-id="4dd5c-127">然后单击“`OK`”。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-127">Then click `OK`.</span></span>
    <span data-ttu-id="4dd5c-128">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span><span class="sxs-lookup"><span data-stu-id="4dd5c-128">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span></span>
7. <span data-ttu-id="4dd5c-129">单击 `Select a trace scenario` 下拉列表，然后选择 "`Local Network Interfaces`"。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-129">Click on the `Select a trace scenario` dropdown and select `Local Network Interfaces`.</span></span>
    <span data-ttu-id="4dd5c-130">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span><span class="sxs-lookup"><span data-stu-id="4dd5c-130">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span></span>
8. <span data-ttu-id="4dd5c-131">单击 `Start` 按钮。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-131">Click the `Start` button.</span></span>
9. <span data-ttu-id="4dd5c-132">应该会看到消息通过设备上的网络接口。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-132">You should start to see the messages going through the network interfaces on your device.</span></span>
    <span data-ttu-id="4dd5c-133">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)</span><span class="sxs-lookup"><span data-stu-id="4dd5c-133">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)</span></span>
10. <span data-ttu-id="4dd5c-134">通过 Message Analyzer 启动跟踪后，还可以在设备的[web 界面](DevicePortal.md)中查看数据包捕获驱动程序的 ETW 消息。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-134">After you start the trace through Message Analyzer, you can also view the ETW messages from the packet capture driver in your device's [web interface](DevicePortal.md).</span></span>  <span data-ttu-id="4dd5c-135">为此，请在 web 界面的 "ETW" 选项卡上，从 "`Registered providers`" 下拉菜单中选择 "`Microsoft-Windows-NDIS-PacketCapture`"，然后单击 "`Enable`" 按钮。</span><span class="sxs-lookup"><span data-stu-id="4dd5c-135">To do this, go to the ETW tab of the web interface, select `Microsoft-Windows-NDIS-PacketCapture` from the `Registered providers` dropdown menu and click the `Enable` button.</span></span>
    <span data-ttu-id="4dd5c-136">![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)</span><span class="sxs-lookup"><span data-stu-id="4dd5c-136">![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)</span></span>    
