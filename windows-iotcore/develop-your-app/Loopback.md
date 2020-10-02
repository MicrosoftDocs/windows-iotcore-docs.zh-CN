---
title: 与 Localhost 通信
author: paulmon
ms.author: riameser
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何通过启用 localhost 环回来创建包含两个进程的 TCP/IP 连接。
keywords: windows iot，localhost，环回，UWP，visual studio
ms.openlocfilehash: b1edec04959e5d0ca8beb9bc0061f97c143b8cca
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656203"
---
# <a name="communicating-with-localhost-loopback"></a><span data-ttu-id="66c14-104">与 localhost (环回) 通信</span><span class="sxs-lookup"><span data-stu-id="66c14-104">Communicating with localhost (loopback)</span></span>

<span data-ttu-id="66c14-105">在 Windows IoT Core 上，如果要在同一设备上运行的两个进程之间创建 TCP/IP 连接，并且其中一个是 UWP 应用，则必须启用 localhost 环回。</span><span class="sxs-lookup"><span data-stu-id="66c14-105">On Windows IoT Core, if you want to create a TCP/IP connection between two processes running on the same device and one of them is a UWP app you must enable localhost loopback.</span></span>

## <a name="loopback-and-the-debugger"></a><span data-ttu-id="66c14-106">环回和调试器</span><span class="sxs-lookup"><span data-stu-id="66c14-106">Loopback and the debugger</span></span> 
<span data-ttu-id="66c14-107">默认情况下，在 Visual Studio 调试器下运行仅为该调试会话自动启用出站环回。</span><span class="sxs-lookup"><span data-stu-id="66c14-107">By default, running under the Visual Studio debugger enables outbound loopback automatically for that debug session only.</span></span><span data-ttu-id="66c14-108">你不必执行任何操作，只要在启动项目的调试器设置中选中了环回复选框。</span><span class="sxs-lookup"><span data-stu-id="66c14-108">  You shouldn’t have to do anything as long as the loopback checkbox is checked in the debugger settings for your startup project.</span></span> <span data-ttu-id="66c14-109">如果要实现套接字侦听器，必须为入站连接启用 localhost 环回 (参阅下面) 。</span><span class="sxs-lookup"><span data-stu-id="66c14-109"> If you want to implement a socket listener, you must enable localhost loopback for inbound connections (see below).</span></span>

## <a name="enabling-the-inbound-loopback-policy"></a><span data-ttu-id="66c14-110">启用入站环回策略</span><span class="sxs-lookup"><span data-stu-id="66c14-110">Enabling the inbound loopback policy</span></span>
<span data-ttu-id="66c14-111">对于实现服务器的 UWP 应用，必须启用 **Windows IoT Core** 的 localhost 入站环回策略。</span><span class="sxs-lookup"><span data-stu-id="66c14-111">The localhost inbound loopback policy for **Windows IoT Core** must be enabled for UWP apps that implement servers.</span></span>  <span data-ttu-id="66c14-112">此策略由以下注册表项控制：</span><span class="sxs-lookup"><span data-stu-id="66c14-112">This policy is controlled by the following registry key:</span></span>
```
        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001
```
<span data-ttu-id="66c14-113">此 IoTInboundLoopbackPolicy 注册表项值必须设置为 dword：00000001，才能启用。</span><span class="sxs-lookup"><span data-stu-id="66c14-113">This IoTInboundLoopbackPolicy registry key value must be set to dword:00000001 to enable.</span></span> <span data-ttu-id="66c14-114">如果更改 IoTInboundLoopbackPolicy 注册表值，则必须重新启动才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="66c14-114">If you change the IoTInboundLoopbackPolicy registry value, you must reboot for the change to take effect.</span></span><span data-ttu-id="66c14-115">默认情况下，在**Windows IoT Core**上启用 localhost 环回策略</span><span class="sxs-lookup"><span data-stu-id="66c14-115">  The localhost loopback policy should be enabled by default on **Windows IoT Core**</span></span>

<span data-ttu-id="66c14-116">若要验证是否已设置该值，请在 **Windows IoT Core** 设备上执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="66c14-116">To verify that the value is set, execute the following command on the **Windows IoT Core** device:</span></span>
```
        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy
```
<span data-ttu-id="66c14-117">若要启用策略，请在 **Windows IoT Core** 设备上执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="66c14-117">To enable the policy, execute the following command on the **Windows IoT Core** device:</span></span>
```
        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
```

## <a name="enabling-loopback-for-a-uwp-application"></a><span data-ttu-id="66c14-118">为 UWP 应用程序启用环回</span><span class="sxs-lookup"><span data-stu-id="66c14-118">Enabling loopback for a UWP application</span></span>
<span data-ttu-id="66c14-119">你需要包系列名称，然后才能为应用程序启用环回。</span><span class="sxs-lookup"><span data-stu-id="66c14-119">Before you can enable loopback for an application, you will need the package family name.</span></span>  <span data-ttu-id="66c14-120">可以通过运行 **iotstartup 列表**来查找已安装应用程序的包系列名称。</span><span class="sxs-lookup"><span data-stu-id="66c14-120">You can find the package family name for an installed application by running **iotstartup list**.</span></span>  <span data-ttu-id="66c14-121">如果应用程序的 **iotstartup 列表** 项为 IoTCoreDefaultApp \_ 1w720vyc4ccym！应用 then 包系列名称是 IoTCoreDefaultApp \_ 1w720vyc4ccym</span><span class="sxs-lookup"><span data-stu-id="66c14-121">If the **iotstartup list** entry for the application is IoTCoreDefaultApp\_1w720vyc4ccym!App then the package family name is IoTCoreDefaultApp\_1w720vyc4ccym</span></span>

<span data-ttu-id="66c14-122">若要为客户端连接启用环回，请使用 `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>` 。</span><span class="sxs-lookup"><span data-stu-id="66c14-122">To enable loopback for client connections use `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.</span></span>  <span data-ttu-id="66c14-123">CheckNetIsolation.exe 将为应用程序配置环回，并退出。</span><span class="sxs-lookup"><span data-stu-id="66c14-123">CheckNetIsolation.exe will configure loopback for the application and exit.</span></span> <span data-ttu-id="66c14-124">这将使应用程序能够与服务器建立出站连接。</span><span class="sxs-lookup"><span data-stu-id="66c14-124">This will enable the application to make outbound connections to a server.</span></span>

<span data-ttu-id="66c14-125">示例：`CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`</span><span class="sxs-lookup"><span data-stu-id="66c14-125">Example: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`</span></span>

<span data-ttu-id="66c14-126">若要使服务器应用程序能够接收入站连接，请使用 `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>` 。</span><span class="sxs-lookup"><span data-stu-id="66c14-126">To enable a server application to receive inbound connections use `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`.</span></span> <span data-ttu-id="66c14-127">与出站连接配置不同，入站连接需要 CheckNetIsolation.exe 在服务器应用程序接收连接时连续运行。</span><span class="sxs-lookup"><span data-stu-id="66c14-127">Unlike outbound connection configuration, inbound connections require CheckNetIsolation.exe to run continuously while the server application is receiving connections.</span></span><span data-ttu-id="66c14-128">这要求使用比10.0.14393 更高的操作系统版本。</span><span class="sxs-lookup"><span data-stu-id="66c14-128">  This requires an OS build newer than 10.0.14393.</span></span>

<span data-ttu-id="66c14-129">示例：`CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`</span><span class="sxs-lookup"><span data-stu-id="66c14-129">Example: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`</span></span>

<span data-ttu-id="66c14-130">在启动时自动运行 CheckNetIsolation.exe 的最佳方式是使用 schtasks.exe： `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`</span><span class="sxs-lookup"><span data-stu-id="66c14-130">The best way to run CheckNetIsolation.exe automatically on startup is to use schtasks.exe: `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`</span></span>

<span data-ttu-id="66c14-131">重新启动后，应该能够使用 tlist.exe 或[Windows 设备门户](https://developer.microsoft.com/windows/iot/docs/deviceportal)验证 checknetisolation.exe 正在运行</span><span class="sxs-lookup"><span data-stu-id="66c14-131">Upon rebooting, you should be able to verify that checknetisolation.exe is running by using tlist.exe or [Windows Device Portal](https://developer.microsoft.com/windows/iot/docs/deviceportal)</span></span>
