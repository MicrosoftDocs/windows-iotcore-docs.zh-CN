---
title: AllJoyn 故障排除
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何使用此综合指南介绍已知问题和故障排除设置来排查 AllJoyn 技术问题。
keywords: windows iot, AllJoyn
ms.openlocfilehash: 8b93242c8f583199ee5890c6d0d15985f9025175
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169937"
---
> [!NOTE]
> <span data-ttu-id="8d9ef-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-104">You are viewing archived documentation.</span></span> <span data-ttu-id="8d9ef-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="8d9ef-106">如有问题, 请在 GitHub 上提出问题, 或在下面的评论中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-troubleshooting"></a><span data-ttu-id="8d9ef-107">AllJoyn 故障排除</span><span class="sxs-lookup"><span data-stu-id="8d9ef-107">AllJoyn Troubleshooting</span></span>

<span data-ttu-id="8d9ef-108">[AllJoyn](https://allseenalliance.org/developers/learn)是一项技术, 使 IoT 设备和应用程序能够发现彼此并彼此交互。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-108">[AllJoyn](https://allseenalliance.org/developers/learn) is a technology that enables IoT devices and applications to discover and interact with each other.</span></span> <span data-ttu-id="8d9ef-109">由于 AllJoyn 内置于 Windows 10 和 Windows 10 SDK 中, 因此可以使用通用 Windows 平台 (UWP) 轻松地利用 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-109">Since AllJoyn is built into Windows 10 and the Windows 10 SDK, it's easy to take advantage of AllJoyn using the Universal Windows Platform (UWP).</span></span>

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

<span data-ttu-id="8d9ef-111">此博客文章将帮助你配置你的 AllJoyn 网络和设备, 并且还提供在不按预期工作时要执行的故障排除步骤。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-111">This blog post will help you configure your AllJoyn network and devices, and also provide troubleshooting steps to follow when things don't work as expected.</span></span> <span data-ttu-id="8d9ef-112">本文的主要重点是启用 UWP AllJoyn 客户端应用 (AllJoyn 使用者) 和 AllJoyn 设备 (AllJoyn 制造者) 之间的通信。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-112">The primary focus of this article will be enabling communication between UWP AllJoyn client apps (AllJoyn consumers) and AllJoyn devices (AllJoyn producers).</span></span> <span data-ttu-id="8d9ef-113">若要启用与 UWP AllJoyn 制造者应用的通信, 需要执行许多相同的配置步骤, 但会进一步详细了解未来的博客文章和文章。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-113">Many of the same configuration steps are required to enable communication with UWP AllJoyn Producer apps, but further details will be left to future blog posts and articles.</span></span>

### <a name="app-development-checklist"></a><span data-ttu-id="8d9ef-114">应用开发清单</span><span class="sxs-lookup"><span data-stu-id="8d9ef-114">App Development Checklist</span></span>

<span data-ttu-id="8d9ef-115">如果要编写适用于 Windows 10 的 UWP 应用, 应确保:</span><span class="sxs-lookup"><span data-stu-id="8d9ef-115">If you are writing UWP apps for Windows 10, you should make sure that:</span></span>

1. <span data-ttu-id="8d9ef-116">已在应用清单中声明了 "allJoyn" 功能 (注意大小写)。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-116">You've declared the 'allJoyn' capability in your app's manifest (note casing).</span></span>
2. <span data-ttu-id="8d9ef-117">你已选择要面向的特定体系结构。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-117">You've selected the specific architecture that you'll be targeting.</span></span> <span data-ttu-id="8d9ef-118">(在某些情况下是必需的, 因为不能使用 "Any CPU" 生成 Windows 运行时组件, 而某些 Visual Studio 2017 生成的已知问题)。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-118">(Required in some cases because Windows Runtime Components cannot be built using 'Any CPU', a known issue with some Visual Studio 2017 builds).</span></span>

<span data-ttu-id="8d9ef-119">如果要编写的应用或设备软件不是适用于 Windows 10 的基于 UWP 的应用程序, 则应查看以下检查表, 以确保与 Windows 10 中的 AllJoyn 兼容:</span><span class="sxs-lookup"><span data-stu-id="8d9ef-119">If you are writing an app or device software that is not a UWP-based application for Windows 10, you should review the following checklist to ensure compatibility with AllJoyn in Windows 10:</span></span>

1. <span data-ttu-id="8d9ef-120">如果实现制造者, 请确保使用 "关于" 接口和 "基于的播发/发现"。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-120">If implementing a Producer, ensure that the About interface and About-based advertisement/discovery are being used.</span></span> <span data-ttu-id="8d9ef-121">[AllSeen 联盟网站上介绍](https://allseenalliance.org/developers/learn/core/about-announcement/interface)了关于接口。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-121">The About interface is [documented at the AllSeen Alliance website](https://allseenalliance.org/developers/learn/core/about-announcement/interface).</span></span>
2. <span data-ttu-id="8d9ef-122">为获得最佳结果, 请使用 AllSeen 联盟网站上的 "[下载" 部分](https://allseenalliance.org/developers/download)中提供的 15.04 AllJoyn 基本代码。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-122">For best results, use the 15.04 AllJoyn code base, available in the [downloads section](https://allseenalliance.org/developers/download) of the AllSeen Alliance website.</span></span>

### <a name="network-setup-and-troubleshooting"></a><span data-ttu-id="8d9ef-123">网络设置和故障排除</span><span class="sxs-lookup"><span data-stu-id="8d9ef-123">Network Setup and Troubleshooting</span></span>

<span data-ttu-id="8d9ef-124">为了使 AllJoyn 设备能够彼此发现并彼此交互, 每个设备的网络配置和设置必须满足以下各项:</span><span class="sxs-lookup"><span data-stu-id="8d9ef-124">For AllJoyn devices to be able to discover and interact with each other, the network configuration and settings for each device must satisfy the following:</span></span>

1. <span data-ttu-id="8d9ef-125">所有 AllJoyn 设备都连接到同一网络, 并且位于同一子网中。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-125">All AllJoyn devices are connected to the same network, and are on the same subnet.</span></span>
2. <span data-ttu-id="8d9ef-126">Windows 10 电脑:为正在与 AllJoyn 一起使用的网络启用了 "查找设备和内容" (不适用于手机)。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-126">Windows 10 PC: "Find devices and content" is enabled for the network in use with AllJoyn (does not apply for Phone).</span></span>

<span data-ttu-id="8d9ef-127">在电脑上, 你可以使用 CMD 或 PowerShell 窗口中的 trace route 命令检查其他计算机/设备是否位于同一子网中, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="8d9ef-127">On a PC you can use the trace route command from a CMD or PowerShell window to check if another machine/device is on the same subnet as follows:</span></span>

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

<span data-ttu-id="8d9ef-128">此处的第一个数字输出为跃点数, 因为该值为 "1", 这意味着这两台计算机位于同一子网中。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-128">The first number output here is the number of hops, and since that value is "1" it means that both machines are on the same subnet.</span></span>

<span data-ttu-id="8d9ef-129">下面是典型的 AllJoyn 网络设置的示例。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-129">Below is an example of a typical AllJoyn network setup.</span></span> <span data-ttu-id="8d9ef-130">在此示例中, 所显示的所有设备都可以使用 AllJoyn 来发现和交互, 假设它们位于同一子网中。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-130">In this example, all of the devices shown would be able to discover and interact with each other using AllJoyn assuming they were on the same subnet.</span></span>

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

<span data-ttu-id="8d9ef-132">将 Windows 10 电脑连接到使用 AllJoyn 设备的网络时, 如果显示与查找网络上的设备和电脑有关的对话框, 则需要单击 "是"。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-132">When you connect your Windows 10 PC to the network with AllJoyn devices, you'll need to click "Yes" if a dialog is displayed regarding finding devices and PCs on the network.</span></span> <span data-ttu-id="8d9ef-133">（注意：当从 Windows 10 手机加入网络时, 此功能不适用, 因为没有此类对话框)。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-133">(Note: This does not apply when joining networks from Windows 10 Phone as there is no such dialog).</span></span>

<span data-ttu-id="8d9ef-134">你还可以在 Wi-fi 设置的 "高级设置" 页中管理此设置, 如下所示: (此页看上去可能略有不同, 具体取决于你正在使用的 Windows 10 内部版本生成)</span><span class="sxs-lookup"><span data-stu-id="8d9ef-134">You can also manage this setting in the "Advanced Settings" page in Wi-Fi settings as shown here: (this page may look slightly different depending on which Windows 10 Insider build you are using)</span></span>

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

<span data-ttu-id="8d9ef-136">"查找设备和内容" 的切换应位于 "打开" 位置, 以便启用 AllJoyn 功能。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-136">The toggle for "Find devices and content" should be in the "On" position in order to enable AllJoyn functionality.</span></span>

<span data-ttu-id="8d9ef-137">对于现有的网络连接, 可以通过运行 "NetConnectionProfile" Powershell cmdlet 轻松地验证是否正确配置了此选项。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-137">For existing network connections, you can easily validate whether this option is configured properly by running the "Get-NetConnectionProfile" Powershell cmdlet .</span></span> <span data-ttu-id="8d9ef-138">(请注意, 这不适用于 Windows 10 Phone)。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-138">(Note that this does not apply for Windows 10 Phone).</span></span>

<span data-ttu-id="8d9ef-139">NetConnectionProfile 输出示例:</span><span class="sxs-lookup"><span data-stu-id="8d9ef-139">Example Get-NetConnectionProfile output:</span></span>

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


<span data-ttu-id="8d9ef-140">如果 "NetworkCategory" 值为 "Private" (如上所示), 则表示你已正确配置用于 AllJoyn 的网络连接。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-140">If the "NetworkCategory" value is "Private" (as shown above), this indicates that you have a properly configured your network connection for AllJoyn.</span></span>

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a><span data-ttu-id="8d9ef-141">关于 Getajxml 的播发和故障排除发现</span><span class="sxs-lookup"><span data-stu-id="8d9ef-141">About Advertisement and Troubleshooting Discovery with Getajxml.exe</span></span>

<span data-ttu-id="8d9ef-142">对于要通过 Windows 10 UWP AllJoyn 应用发现的 AllJoyn 制造者设备或应用, 必须正确实现基于的发现。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-142">For AllJoyn producer devices or apps to be discoverable by Windows 10 UWP AllJoyn apps, About-based discovery must be properly implemented.</span></span> <span data-ttu-id="8d9ef-143">可以通过 GetAjXml 工具轻松地对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-143">This can be easily verified with the GetAjXml.exe tool.</span></span> <span data-ttu-id="8d9ef-144">若要查找与 GetAjXml 相关的下载和使用情况信息, 请查看[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-144">To find download and usage information related to GetAjXml.exe, check out [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).</span></span>

<span data-ttu-id="8d9ef-145">下面显示了支持基于发现的示例设备的 GetAjXml 输出:</span><span class="sxs-lookup"><span data-stu-id="8d9ef-145">The following shows GetAjXml.exe output for an example device that supports About-based discovery:</span></span>

    ----------------------------------------------------------------------
    Discovery   : About Announcement
    Manufacturer: Microsoft
    Model #     : 070773
    Device Name : Raspberry Pi Toaster
    Device ID   : 41d9a124-6913-40c5-a20a-9d1b20f8121b
    App Name   : Toaster Producer
          Bus Name                       Port Object Path
          ============================== ===== ===============================
          :3yZG_wu1.2                       25 /emergency
          :3yZG_wu1.2                       25 /info
          :3yZG_wu1.2                       25 /notificationDismisser
          :3yZG_wu1.2                       25 /notificationProducer
          :3yZG_wu1.2                       25 /toaster
          :3yZG_wu1.2                       25 /warning


<span data-ttu-id="8d9ef-146">在上面的示例中, `Discovery   : About Announcement`由于包含在此输出中, 因此可通过 Windows 10 alljoyn UWP 应用发现此 AllJoyn 制造者。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-146">In the above example, since `Discovery   : About Announcement` was included in this output, this AllJoyn producer will be discoverable by Windows 10 AllJoyn UWP apps.</span></span> <span data-ttu-id="8d9ef-147">如果看不到特定的 AllJoyn 制造者的输出, 需要在设备 (制造者) 端调查发现实现。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-147">If you don't see this output for a particular AllJoyn producer, you will need to investigate the discovery implementation on the device (Producer) side.</span></span>

### <a name="advanced-troubleshooting-with-etw-log-output"></a><span data-ttu-id="8d9ef-148">ETW 日志输出的高级故障排除</span><span class="sxs-lookup"><span data-stu-id="8d9ef-148">Advanced Troubleshooting with ETW Log Output</span></span>

<span data-ttu-id="8d9ef-149">Windows 事件跟踪 (ETW) 可帮助你获取 Windows 中许多不同功能的高级调试信息。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-149">Event Tracing for Windows (ETW) can help you get advanced debugging information for many different features in Windows.</span></span> <span data-ttu-id="8d9ef-150">幸好 AllJoyn 是支持 ETW 日志记录的一项功能, 因此在本部分中, 我将向您展示如何启用用于 AllJoyn 的 ETW 日志记录以及如何访问日志。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-150">Fortunately AllJoyn is one of the features with ETW logging support, so in this section I'll show you how to enable ETW logging for AllJoyn, and how to access logs.</span></span>

1. <span data-ttu-id="8d9ef-151">通过在 "开始菜单搜索" 文本框中键入 "事件日志" 来启动事件查看器, 选择 "查看事件日志"。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-151">Launch the Event Viewer by typing "Event Logs" into the Start Menu search textbox, select "View Event Logs".</span></span>
2. <span data-ttu-id="8d9ef-152">在 "视图" 菜单中, 确保选中 "显示分析和调试日志"。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-152">In the "View" menu, ensure that "Show Analytic and Debug Logs" is checked.</span></span>
3. <span data-ttu-id="8d9ef-153">在左侧导航栏中导航到文件夹视图中的 "应用程序和服务日志 > Microsoft > Windows > AllJoyn", 同时启用调试通道和操作通道。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-153">Navigate the tree view in the left navigation to "Applications and Services Logs > Microsoft > Windows > AllJoyn" in the folder view, and enable both the Debug channel and the Operational channel.</span></span> <span data-ttu-id="8d9ef-154">(请参阅下面的屏幕截图中的红框)。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-154">(see red box in screenshot below).</span></span>
4. <span data-ttu-id="8d9ef-155">再现您在 AllJoyn 中遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-155">Reproduce the problem that you are experiencing with AllJoyn.</span></span>
5. <span data-ttu-id="8d9ef-156">在右侧的 "操作" 栏中单击 "刷新", 然后从左侧导航栏中检查 "AllJoyn" 文件夹下的 "操作" 和 "调试" 通道。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-156">Click on "Refresh" in the right "Actions" bar, then check the Operational and Debug channels from the left navigation bar under the "AllJoyn" folder.</span></span>

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

<span data-ttu-id="8d9ef-158">AllJoyn ETW 跟踪的分区如下:</span><span class="sxs-lookup"><span data-stu-id="8d9ef-158">AllJoyn ETW traces are partitioned as follows:</span></span>

- <span data-ttu-id="8d9ef-159">调试通道:详细、非错误/信息性跟踪</span><span class="sxs-lookup"><span data-stu-id="8d9ef-159">Debug channel: Verbose, non-error/informational traces</span></span>
- <span data-ttu-id="8d9ef-160">操作通道:错误跟踪, 错误只是操作通道上的输出</span><span class="sxs-lookup"><span data-stu-id="8d9ef-160">Operational channel: Error traces, errors are only output on the operational channel</span></span>

<span data-ttu-id="8d9ef-161">若要从 ETW 条目中提取信息, 可以在列表视图中右键单击给定通道的条目, 然后选择 "复制", 然后选择 "复制详细信息作为文本"。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-161">In order to extract information from ETW entries, you can right-click on an entry in the list view for a given channel, and then select "Copy" and then "Copy Details as Text".</span></span> <span data-ttu-id="8d9ef-162">如果随后将相应的文本粘贴到文本编辑器中, 将获得如下所示的详细信息:</span><span class="sxs-lookup"><span data-stu-id="8d9ef-162">If you then paste the corresponding text into a text editor, you'll have detail like the example below:</span></span>


    Log Name:       Microsoft-Windows-AllJoyn/Operational
    Source:         Microsoft-Windows-AllJoyn
    Date:           6/1/2015 3:57:45 PM
    Event ID:     2
    Task Category: AJ
    Level:         Error
    Keywords:      (70368744177664),AJ
    User:         LOCAL SERVICE
    Computer:       <computer name>
     
    Description:
    AllJoyn encountered an error 0x902D in module UDP, file ..\udptransport.cc, at line number 10809. See the event user data for more information.
    Event Xml:
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
    <System>
       <Provider Name="Microsoft-Windows-AllJoyn" Guid="{2ED299D2-2F6B-411D-8D15-F4CC6FDE0C70}" />
        <EventID>2</EventID>
        <Version>0</Version>
        <Level>2</Level>
        <Task>1</Task>
        <Opcode>10</Opcode>
        <Keywords>0x8000400000000001</Keywords>
       <TimeCreated SystemTime="2015-06-01T22:57:45.626729500Z" />
        <EventRecordID>16</EventRecordID>
       <Correlation />
       <Execution ProcessID="1392" ThreadID="5768" />
       <Channel>Microsoft-Windows-AllJoyn/Operational</Channel>
        <Computer>computer name</Computer>
       <Security UserID="SID" />
    </System>
    <UserData>
       <AJErrorData xmlns="http://manifests.microsoft.com/win/2005/08/windows/alljoyn/events">
           <QStatus>0x902d</QStatus>
           <Message>UDPTransport::DisbleDiscovery(): Not running or stopping; exiting</Message>
           <Module>UDP</Module>
           <File>..\udptransport.cc</File>
           <Line>10809</Line>
        </AJErrorData>
    </UserData>
    </Event>


<span data-ttu-id="8d9ef-163">此信息可以帮助跟踪 AllJoyn 问题, 或在向 Microsoft 或其他合作伙伴报告问题时提供详细信息。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-163">This information can help track down AllJoyn issues, or assist in providing detail when reporting issues to Microsoft or other partners.</span></span> <span data-ttu-id="8d9ef-164">可[在 MSDN 上了解有关 ETW 跟踪和事件查看器的](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx)详细信息。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-164">You can learn more about [ETW traces and the Event Viewer on MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).</span></span>

### <a name="known-issues-and-limitations"></a><span data-ttu-id="8d9ef-165">已知问题和限制</span><span class="sxs-lookup"><span data-stu-id="8d9ef-165">Known Issues and Limitations</span></span>

<span data-ttu-id="8d9ef-166">Windows 10 中的 AllJoyn 的设计限制:</span><span class="sxs-lookup"><span data-stu-id="8d9ef-166">By-Design limitations for AllJoyn in Windows 10:</span></span>

- <span data-ttu-id="8d9ef-167">在 Windows 10 电脑上没有运行任何应用时, alljoyn 设备或网络上的应用不会自动启动 AllJoyn 路由器节点。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-167">The AllJoyn Router Node is not auto-started by AllJoyn devices or apps on the network when no apps are running on the Windows 10 PC.</span></span> <span data-ttu-id="8d9ef-168">通过运行 "net start ajrouter" 命令, 可以从提升的命令提示符或 Powershell 会话启动 Windows 10 路由器节点。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-168">The Windows 10 Router Node can be started from an elevated command prompt or Powershell session by running the command "net start ajrouter".</span></span>
- <span data-ttu-id="8d9ef-169">AllJoyn UWP 应用无法发现或与在同一台计算机上运行的其他 AllJoyn UWP 应用或 AllJoyn 桌面应用交互。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-169">AllJoyn UWP apps can't discover or interact with other AllJoyn UWP apps or AllJoyn desktop apps running on the same machine.</span></span> <span data-ttu-id="8d9ef-170">这是在适用于 UWP 应用的 Windows 10 中实施的应用程序隔离承诺的一部分。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-170">This is a part of the app isolation promise that is implemented in Windows 10 for UWP apps.</span></span> 
  - <span data-ttu-id="8d9ef-171">如果从 Visual Studio 部署 AllJoyn UWP 应用, 则会绕过应用隔离应用隔离 (称为 "环回例外")。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-171">If you deploy an AllJoyn UWP app from Visual Studio, app isolation app isolation is bypassed for that app (this is called a "loopback exemption ").</span></span> <span data-ttu-id="8d9ef-172">从 Visual Studio 部署的每个 UWP 应用程序都能够发现并与其他受回环的 UWP 应用和桌面应用进行交互, 只要这些应用使用的是基于的广告/发现。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-172">Each UWP app that is deployed from Visual Studio will be able to discover and interact with other loopback-exempt UWP apps and desktop apps as long as those apps use About-based advertisement/discovery.</span></span> <span data-ttu-id="8d9ef-173">如果正在 "嵌入模式" 下运行 Windows 10 IoT Core, 此环回例外会自动应用, 不是需要配置的内容。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-173">If you are running Windows 10 IoT Core in "Embedded Mode", this loopback exception is automatically applied, it's not something that you need to configure.</span></span> <span data-ttu-id="8d9ef-174">可[在 MSDN 上](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)阅读有关环回异常的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8d9ef-174">You can read more about loopback exceptions [on MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>

