---
title: AllJoyn 故障排除
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何排查 AllJoyn 技术，它利用此综合指南，其中包括已知的问题并解决设置问题。
keywords: windows iot AllJoyn
ms.openlocfilehash: 8b93242c8f583199ee5890c6d0d15985f9025175
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510663"
---
> [!NOTE]
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。

# <a name="alljoyn-troubleshooting"></a>AllJoyn 故障排除

[AllJoyn](https://allseenalliance.org/developers/learn)是一种技术，使 IoT 设备和应用程序发现和彼此交互。 由于 AllJoyn 专为 Windows 10 和 Windows 10 SDK，因此很容易地利用 AllJoyn 使用通用 Windows 平台 (UWP)。

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

这篇博客文章将帮助您配置 AllJoyn 网络和设备，而且还提供操作未按预期工作时，请遵循故障排除步骤。 本文主要侧重于将会启用 UWP AllJoyn 客户端应用程序 （AllJoyn 消费者） 和 AllJoyn 设备 （AllJoyn 生成者） 之间的通信。 启用与 UWP AllJoyn 生成者应用通信所需的许多相同的配置步骤，但更多详细信息将保留为将来的博客文章和文章。

### <a name="app-development-checklist"></a>应用程序开发清单

如果你正在编写适用于 Windows 10 的 UWP 应用，你应确保：

1. 已声明应用程序的清单 （请注意大小写） 中的 allJoyn 功能。
2. 已选择你将面向的特定体系结构。 （因为不能使用 Any CPU 构建 Windows 运行时组件，则需要在某些情况下，某些 Visual Studio 2017 的已知的问题生成）。

如果你正在编写不是基于 UWP 的应用程序，适用于 Windows 10 的应用或设备软件，则应该查看以下清单以确保与 Windows 10 中 AllJoyn 的兼容性：

1. 如果实现生成者，请确保关于接口和基于关于播发/发现的使用。 关于接口是[AllSeen 联盟网站上介绍了](https://allseenalliance.org/developers/learn/core/about-announcement/interface)。
2. 为获得最佳结果，使用 15.04 AllJoyn 基本代码，推出[下载部分](https://allseenalliance.org/developers/download)AllSeen 联盟网站。

### <a name="network-setup-and-troubleshooting"></a>网络设置和故障排除

对于 AllJoyn 设备能够发现和彼此交互，网络配置和设置每个设备必须满足以下：

1. 所有 AllJoyn 设备连接到同一网络和同一子网。
2. Windows 10 电脑："查找设备和内容"可用于与 AllJoyn （不适用于手机） 配合使用中的网络。

在 PC 上可用于跟踪路由命令 CMD 或 PowerShell 窗口中检查另一个计算机/设备是否位于同一子网，如下所示：

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

第一个数字输出此处是跃点，数目，因为该值是"1"这意味着两台计算机位于同一子网。

下面是典型的 AllJoyn 网络设置的示例。 在此示例中，所有显示的设备都可以是能够发现和使用 AllJoyn 假设它们位于同一子网彼此交互。

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

与 AllJoyn 设备将在 Windows 10 电脑连接到网络，需要单击"是"如果在网络上有关查找设备和电脑将显示一个对话框。 （注意：这不适用于联接来自 Windows 10 手机网络，因为没有任何此类对话框时）。

你还可以管理的 Wi-fi 设置中的"高级设置"页中的此设置，如下所示: （此页可能看起来稍有不同，具体取决于正在使用的 Windows 10 预览体验内部版本）

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

"查找设备和内容"切换应在的"开"位置中以启用 AllJoyn 功能。

对于现有网络连接，可以轻松地验证是否正确地通过运行"Get NetConnectionProfile"Powershell cmdlet 配置此选项。 （请注意，这不适用于 Windows 10 手机）。

Get NetConnectionProfile 输出示例：

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


如果"NetworkCategory"值为"Private"（如上所示），这表示你已经正确配置 AllJoyn 的网络连接。

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a>有关播发和故障排除与 Getajxml.exe 发现

对于 AllJoyn 制造者设备或应用程序可供检测的 Windows 10 UWP AllJoyn 的应用，必须正确地实现有关基于发现。 这可以轻松地验证 GetAjXml.exe 工具。 若要下载和使用情况与 GetAjXml.exe 相关的信息，请查看[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)。

下面显示了支持有关基于发现的示例设备的 GetAjXml.exe 输出：

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


在上述示例中，由于`Discovery   : About Announcement`已包括在内，将在此输出中，此 AllJoyn 制造者也可发现 Windows 10 AllJoyn UWP 应用。 如果没有为特定的 AllJoyn 制造者看到此输出，您需要调查设备 （生成者） 端上的发现实现。

### <a name="advanced-troubleshooting-with-etw-log-output"></a>使用 ETW 日志输出高级故障排除

事件跟踪 Windows (ETW) 可以帮助您获取高级的很多不同功能在 Windows 中的调试信息。 幸运的是 AllJoyn 是使用 ETW 日志记录支持，因此在本部分中我将介绍如何启用 ETW 日志记录，用于 AllJoyn，以及如何访问日志的功能之一。

1. 通过开始菜单搜索文本框中键入"事件日志"，启动事件查看器中，选择"查看事件日志"。
2. 在"视图"菜单中，请确保选中"显示分析和调试日志"。
3. 导航到"应用程序和服务日志 > Microsoft > Windows > AllJoyn"文件夹视图中的左侧导航中的树视图，并启用调试通道和操作通道。 （请参阅下面的屏幕截图中红色框）。
4. 再现 AllJoyn 遇到该问题。
5. 在正确的"操作"栏中，单击"刷新"，然后检查从左侧的导航栏中的"AllJoyn"文件夹下的运行和调试通道。

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

AllJoyn ETW 跟踪进行分区，如下所示：

- 调试通道：详细的非错误信息/跟踪
- 操作通道：错误跟踪，错误是只在操作通道上的输出

若要从 ETW 条目中提取信息，您可以右键单击某项给定的通道，在列表视图中，然后选择"复制"，然后是"复制详细信息作为文字"。 然后，将相应的文本粘贴到文本编辑器中，如果您将有详细信息，例如下面的示例：


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


此信息可帮助跟踪 AllJoyn 问题或帮助时向 Microsoft 或其他合作伙伴报告问题提供详细信息。 可以深入了解[ETW 跟踪和 MSDN 上的事件查看器](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx)。

### <a name="known-issues-and-limitations"></a>已知问题和限制

在 Windows 10 的 AllJoyn 的按设计限制：

- AllJoyn 路由器节点时没有应用程序正在运行 Windows 10 电脑上不是由 AllJoyn 设备或网络上的应用程序自动启动的。 通过运行命令"net start ajrouter"，可以从提升的命令提示符或 Powershell 会话中启动 Windows 10 路由器节点。
- AllJoyn UWP 应用无法发现或与其他 AllJoyn UWP 应用或 AllJoyn 在同一台计算机上运行的桌面应用程序进行交互。 这是适用于 UWP 应用在 Windows 10 中实现该应用程序隔离承诺的一部分。 
  - 如果部署基于 Visual Studio 的 AllJoyn UWP 应用，应用程序隔离应用隔离则跳过 （这称为"环回例外"） 该应用。 从 Visual Studio 部署的每个 UWP 应用将能够发现和，只要这些应用程序使用有关基于播发/发现与其他环回例外 UWP 应用和桌面应用程序进行交互。 如果以"嵌入模式"正在运行 Windows 10 IoT 核心版，将自动应用该环回例外，它并不是您需要进行配置。 你可以阅读更多有关环回例外[MSDN 上](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)。

