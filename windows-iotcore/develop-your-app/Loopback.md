---
title: 与本地主机通信
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: 了解如何通过启用本地主机环回使用两个进程创建的 TCP/IP 连接。
keywords: windows iot、 localhost、 环回、 UWP、 visual studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510616"
---
# <a name="communicating-with-localhost-loopback"></a><span data-ttu-id="27561-104">与本地主机 （环回） 进行通信</span><span class="sxs-lookup"><span data-stu-id="27561-104">Communicating with localhost (loopback)</span></span>

<span data-ttu-id="27561-105">在 Windows IoT Core，如果你想要创建运行在同一设备上的 2 个进程之间的 TCP/IP 连接，并且其中一种是 UWP 应用必须启用本地主机环回。</span><span class="sxs-lookup"><span data-stu-id="27561-105">On Windows IoT Core, if you want to create a TCP/IP connection between 2 processes running on the same device and one of them is a UWP app you must enable localhost loopback.</span></span>

## <a name="loopback-and-the-debugger"></a><span data-ttu-id="27561-106">Loopback 和调试器</span><span class="sxs-lookup"><span data-stu-id="27561-106">Loopback and the debugger</span></span> 
<span data-ttu-id="27561-107">默认情况下，在 Visual Studio 调试器下的运行，可以在出站环回自动仅适用于该调试会话。</span><span class="sxs-lookup"><span data-stu-id="27561-107">By default, running under the Visual Studio debugger enables outbound loopback automatically for that debug session only.</span></span><span data-ttu-id="27561-108">  您无需执行任何操作，只要启动项目的调试程序设置中选中的环回复选框。</span><span class="sxs-lookup"><span data-stu-id="27561-108">  You shouldn’t have to do anything as long as the loopback checkbox is checked in the debugger settings for your startup project.</span></span> <span data-ttu-id="27561-109"> 如果您想要实现的套接字侦听器则必须启用本地主机环回为入站连接 （见下文）。</span><span class="sxs-lookup"><span data-stu-id="27561-109"> If you want to implement a socket listener the you must enable localhost loopback for inbound connections (see below).</span></span>
 
## <a name="enabling-the-inbound-loopback-policy"></a><span data-ttu-id="27561-110">如果启用入站的环回策略</span><span class="sxs-lookup"><span data-stu-id="27561-110">Enabling the inbound loopback policy</span></span>
<span data-ttu-id="27561-111">本地主机的入站环回策略**Windows IoT Core**必须适用于 UWP 应用实现服务器启用。</span><span class="sxs-lookup"><span data-stu-id="27561-111">The localhost inbound loopback policy for **Windows IoT Core** must be enabled for UWP apps that implement servers.</span></span>  <span data-ttu-id="27561-112">此策略控制由以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="27561-112">This policy is controlled by the following registry key:</span></span>

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

<span data-ttu-id="27561-113">此 IoTInboundLoopbackPolicy 注册表项值必须设置为 dword: 00000001 启用。</span><span class="sxs-lookup"><span data-stu-id="27561-113">This IoTInboundLoopbackPolicy registry key value must be set to dword:00000001 to enable.</span></span> <span data-ttu-id="27561-114">如果您更改 IoTInboundLoopbackPolicy 注册表值，您必须重新启动计算机更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="27561-114">If you change the IoTInboundLoopbackPolicy registry value you must reboot for the change to take effect.</span></span><span data-ttu-id="27561-115">  应在默认情况下启用本地主机环回策略\*\*Windows IoT 核心版**</span><span class="sxs-lookup"><span data-stu-id="27561-115">  The localhost loopback policy should be enabled by default on \*\*Windows IoT Core**</span></span>

<span data-ttu-id="27561-116">若要验证的值是组执行以下命令上**Windows IoT Core**设备：</span><span class="sxs-lookup"><span data-stu-id="27561-116">To verify that the value is set execute the following command on the **Windows IoT Core** device:</span></span>

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

<span data-ttu-id="27561-117">若要启用该策略执行以下命令上**Windows IoT Core**设备：</span><span class="sxs-lookup"><span data-stu-id="27561-117">To enable the policy execute the following command on the **Windows IoT Core** device:</span></span>

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a><span data-ttu-id="27561-118">UWP 应用程序的启用环回</span><span class="sxs-lookup"><span data-stu-id="27561-118">Enabling loopback for a UWP application</span></span>
<span data-ttu-id="27561-119">在启用环回应用程序之前，你将需要包系列名称。</span><span class="sxs-lookup"><span data-stu-id="27561-119">Before you can enable loopback for an application you will need the package family name.</span></span>  <span data-ttu-id="27561-120">可以通过运行安装的应用程序中找到包系列名称**iotstartup 列表**。</span><span class="sxs-lookup"><span data-stu-id="27561-120">You can find the package family name for an installed application by running **iotstartup list**.</span></span>  <span data-ttu-id="27561-121">如果**iotstartup 列表**应用程序的条目是 IoTCoreDefaultApp\_1w720vyc4ccym ！应用程序然后包系列名称是 IoTCoreDefaultApp\_1w720vyc4ccym</span><span class="sxs-lookup"><span data-stu-id="27561-121">If the **iotstartup list** entry for the application is IoTCoreDefaultApp\_1w720vyc4ccym!App then the package family name is IoTCoreDefaultApp\_1w720vyc4ccym</span></span>

<span data-ttu-id="27561-122">若要启用用于客户端连接的环回`CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`。</span><span class="sxs-lookup"><span data-stu-id="27561-122">To enable loopback for client connections use `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.</span></span>  <span data-ttu-id="27561-123">CheckNetIsolation.exe 将配置应用程序和退出的环回。</span><span class="sxs-lookup"><span data-stu-id="27561-123">CheckNetIsolation.exe will configure loopback for the application and exit.</span></span> <span data-ttu-id="27561-124">这将使应用程序以进行出站连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="27561-124">This will enable the application to make outbound connections to a server.</span></span>

<span data-ttu-id="27561-125">例如：</span><span class="sxs-lookup"><span data-stu-id="27561-125">Example:</span></span> `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

<span data-ttu-id="27561-126">若要启用的服务器应用程序接收的入站的连接，请使用`CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`。</span><span class="sxs-lookup"><span data-stu-id="27561-126">To enable a server application to receive inbound connections use `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`.</span></span> <span data-ttu-id="27561-127">与出站连接配置中，不同的入站的连接需要 CheckNetIsolation.exe 运行服务器应用程序正在接收的连接时，持续。</span><span class="sxs-lookup"><span data-stu-id="27561-127">Unlike outbound connection configuration, inbound connections require CheckNetIsolation.exe to run continuously while the server application is receiving connections.</span></span><span data-ttu-id="27561-128">  这需要更高版本低于 10.0.14393 的 OS 生成。</span><span class="sxs-lookup"><span data-stu-id="27561-128">  This requires an OS build newer than 10.0.14393.</span></span>

<span data-ttu-id="27561-129">例如：</span><span class="sxs-lookup"><span data-stu-id="27561-129">Example:</span></span> `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

<span data-ttu-id="27561-130">在启动时自动运行 CheckNetIsolation.exe 的最佳方式是使用 schtasks.exe:</span><span class="sxs-lookup"><span data-stu-id="27561-130">The best way to run CheckNetIsolation.exe automatically on startup is to use schtasks.exe:</span></span> `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

<span data-ttu-id="27561-131">在重新启动时应为能够验证该 checknetisolation.exe 运行通过使用 tlist.exe 或[Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)</span><span class="sxs-lookup"><span data-stu-id="27561-131">Upon rebooting you should be able to verify that checknetisolation.exe is running by using tlist.exe or [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)</span></span>
