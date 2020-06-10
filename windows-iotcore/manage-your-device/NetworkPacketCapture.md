---
title: 网络数据包捕获
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Microsoft Message Analyzer 启用网络数据包捕获
keywords: windows iot，网络数据包，网络数据包捕获，Microsoft Message Analyzer，PowerShell
ms.openlocfilehash: 2eaca4b71cb00f054ede9c8b159892b9f15c9296
ms.sourcegitcommit: b0ca7e5487469edf5bf199493be71604f3bd3fcd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84563384"
---
# <a name="network-packet-capture"></a><span data-ttu-id="4d99a-104">网络数据包捕获</span><span class="sxs-lookup"><span data-stu-id="4d99a-104">Network packet capture</span></span>

## <a name="note---microsoft-message-analyzer-has-been-deprecated-information-contained-below-is-for-archival-reference-only"></a><span data-ttu-id="4d99a-105">注意-Microsoft Message Analyzer 已[弃用](https://docs.microsoft.com/openspecs/blog/ms-winintbloglp/dd98b93c-0a75-4eb0-b92e-e760c502394f)。</span><span class="sxs-lookup"><span data-stu-id="4d99a-105">NOTE - Microsoft Message Analyzer has been [deprecated](https://docs.microsoft.com/openspecs/blog/ms-winintbloglp/dd98b93c-0a75-4eb0-b92e-e760c502394f).</span></span> <span data-ttu-id="4d99a-106">下面包含的信息仅用于存档引用。</span><span class="sxs-lookup"><span data-stu-id="4d99a-106">Information contained below is for archival reference only.</span></span>

<span data-ttu-id="4d99a-107">可以使用[Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226)来捕获、显示和分析 Windows 10 IoT Core 设备上的协议消息传送流量。</span><span class="sxs-lookup"><span data-stu-id="4d99a-107">You can use [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226) to capture, display, and analyze protocol messaging traffic on your Windows 10 IoT Core device.</span></span>

![消息分析器](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a><span data-ttu-id="4d99a-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="4d99a-109">Prerequisites</span></span>

<span data-ttu-id="4d99a-110">工作 PowerShell 连接（ [powershell](../connect-your-device/PowerShell.md)中介绍的步骤1到8。</span><span class="sxs-lookup"><span data-stu-id="4d99a-110">Working PowerShell Connection (Step 1 to 8 described at [PowerShell](../connect-your-device/PowerShell.md).</span></span>

## <a name="set-up-your-device"></a><span data-ttu-id="4d99a-111">设置设备</span><span class="sxs-lookup"><span data-stu-id="4d99a-111">Set up your device</span></span>

<span data-ttu-id="4d99a-112">若要使用 Message Analyzer 连接到设备，需要先重命名设备。</span><span class="sxs-lookup"><span data-stu-id="4d99a-112">In order to connect to your device using Message Analyzer, you need to first rename your device.</span></span>  <span data-ttu-id="4d99a-113">可以使用命令通过[SSH](../connect-your-device/SSH.md)或[PowerShell](../connect-your-device/PowerShell.md)完成此操作 `setcomputername` 。</span><span class="sxs-lookup"><span data-stu-id="4d99a-113">This can be done through [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/PowerShell.md) using the `setcomputername` command.</span></span>

![PowerShell 重命名设备](../media/NetworkPacketCapture/powershell-rename-device.png)

<span data-ttu-id="4d99a-115">重命名设备后，重新启动设备以应用名称更改。</span><span class="sxs-lookup"><span data-stu-id="4d99a-115">After you rename your device, reboot the device to apply the name change.</span></span>

## <a name="turn-off-the-firewall"></a><span data-ttu-id="4d99a-116">关闭防火墙</span><span class="sxs-lookup"><span data-stu-id="4d99a-116">Turn off the firewall</span></span>

<span data-ttu-id="4d99a-117">使用 PowerShell 或 SSH 连接到设备，并运行以下命令以禁用防火墙。</span><span class="sxs-lookup"><span data-stu-id="4d99a-117">Connect to your device using PowerShell or SSH and run the following command to disable the firewall.</span></span>
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a><span data-ttu-id="4d99a-118">使用消息分析器连接到设备</span><span class="sxs-lookup"><span data-stu-id="4d99a-118">Connect to your device using Message Analyzer</span></span>

<span data-ttu-id="4d99a-119">设置设备后，让我们使用 Microsoft Message Analyzer 连接到它。</span><span class="sxs-lookup"><span data-stu-id="4d99a-119">Now that your device is set up, let's connect to it using Microsoft Message Analyzer.</span></span>

1. <span data-ttu-id="4d99a-120">下载[Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226)。</span><span class="sxs-lookup"><span data-stu-id="4d99a-120">Download the [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226).</span></span>
2. <span data-ttu-id="4d99a-121">打开 Message Analyzer。</span><span class="sxs-lookup"><span data-stu-id="4d99a-121">Open Message Analyzer.</span></span>
3. <span data-ttu-id="4d99a-122">单击 `New Session`。</span><span class="sxs-lookup"><span data-stu-id="4d99a-122">Click on `New Session`.</span></span>

    ![消息分析器](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. <span data-ttu-id="4d99a-124">在打开的窗口中，单击 "" `Live Trace` 按钮。</span><span class="sxs-lookup"><span data-stu-id="4d99a-124">In the window that opens, click on the `Live Trace` button.</span></span>
    <span data-ttu-id="4d99a-125">![消息分析器](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span><span class="sxs-lookup"><span data-stu-id="4d99a-125">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span></span>
5. <span data-ttu-id="4d99a-126">单击“”`Edit...`按钮。</span><span class="sxs-lookup"><span data-stu-id="4d99a-126">Click on the `Edit...` button.</span></span>
    <span data-ttu-id="4d99a-127">![消息分析器](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span><span class="sxs-lookup"><span data-stu-id="4d99a-127">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span></span>
6. <span data-ttu-id="4d99a-128">将 Localhost 替换为 IoT 设备的名称，并输入管理员用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="4d99a-128">Replace Localhost with the name of your IoT device, and enter the administrator user name and password.</span></span>  <span data-ttu-id="4d99a-129">然后单击 `OK` 。</span><span class="sxs-lookup"><span data-stu-id="4d99a-129">Then click `OK`.</span></span>
    <span data-ttu-id="4d99a-130">![消息分析器](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span><span class="sxs-lookup"><span data-stu-id="4d99a-130">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span></span>
7. <span data-ttu-id="4d99a-131">单击 `Select a trace scenario` 下拉列表并选择 `Local Network Interfaces` 。</span><span class="sxs-lookup"><span data-stu-id="4d99a-131">Click on the `Select a trace scenario` dropdown and select `Local Network Interfaces`.</span></span>
    <span data-ttu-id="4d99a-132">![消息分析器](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span><span class="sxs-lookup"><span data-stu-id="4d99a-132">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span></span>
8. <span data-ttu-id="4d99a-133">单击“`Start`”按钮。</span><span class="sxs-lookup"><span data-stu-id="4d99a-133">Click the `Start` button.</span></span>
9. <span data-ttu-id="4d99a-134">应该会看到消息通过设备上的网络接口。</span><span class="sxs-lookup"><span data-stu-id="4d99a-134">You should start to see the messages going through the network interfaces on your device.</span></span>
    <span data-ttu-id="4d99a-135">![消息分析器](../media/NetworkPacketCapture/message-analyzer.png)</span><span class="sxs-lookup"><span data-stu-id="4d99a-135">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)</span></span>
10. <span data-ttu-id="4d99a-136">通过 Message Analyzer 启动跟踪后，还可以在设备的[web 界面](DevicePortal.md)中查看数据包捕获驱动程序的 ETW 消息。</span><span class="sxs-lookup"><span data-stu-id="4d99a-136">After you start the trace through Message Analyzer, you can also view the ETW messages from the packet capture driver in your device's [web interface](DevicePortal.md).</span></span>  <span data-ttu-id="4d99a-137">为此，请在 web 界面的 "ETW" 选项卡上， `Microsoft-Windows-NDIS-PacketCapture` 从下拉菜单中选择， `Registered providers` 然后单击 "" `Enable` 按钮。</span><span class="sxs-lookup"><span data-stu-id="4d99a-137">To do this, go to the ETW tab of the web interface, select `Microsoft-Windows-NDIS-PacketCapture` from the `Registered providers` dropdown menu and click the `Enable` button.</span></span>
    <span data-ttu-id="4d99a-138">![消息分析器](../media/NetworkPacketCapture/web-etw.png)</span><span class="sxs-lookup"><span data-stu-id="4d99a-138">![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)</span></span>    
