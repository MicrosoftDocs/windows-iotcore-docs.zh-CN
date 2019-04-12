---
title: Windows 文件共享
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解有关如何使用 Windows 文件共享来传输文件与你的设备。
keywords: windows iot、 文件传输、 文件共享，windows 文件共享
ms.openlocfilehash: 00dc17ded4b9c4fbea05faca794766f965d0632a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59511011"
---
# <a name="windows-file-sharing"></a><span data-ttu-id="37f51-104">Windows 文件共享</span><span class="sxs-lookup"><span data-stu-id="37f51-104">Windows file sharing</span></span>

<span data-ttu-id="37f51-105">可以使用 Windows 文件共享传输到和从你的设备的文件。</span><span class="sxs-lookup"><span data-stu-id="37f51-105">You can use Windows file sharing to transfer files to and from your device.</span></span>

## <a name="accessing-your-files-using-windows-file-sharing"></a><span data-ttu-id="37f51-106">使用 Windows 文件共享访问你的文件</span><span class="sxs-lookup"><span data-stu-id="37f51-106">Accessing your files using Windows file sharing</span></span>
* <span data-ttu-id="37f51-107">Windows IoT 核心版设备上的文件共享服务器在设备启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="37f51-107">The file sharing server on your Windows IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="37f51-108">若要连接到它，需要你的设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="37f51-108">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="37f51-109">你可以在默认应用上找到该 IP 地址，该应用会在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="37f51-109">You can find the IP address on the default app that boots when your device starts.</span></span>

    ![Windows IoT 核心版上的 DefaultApp](../media/WindowsFileSharing/DefaultApp.png)
    
* <span data-ttu-id="37f51-111">有了 IP 后，在计算机上打开“文件资源管理器”并键入 `\\<TARGET_DEVICE>\c$`（其中 `<TARGET_DEVICE>` 是 Windows IoT 核心版设备的名称或 IP 地址），然后点击 Enter。</span><span class="sxs-lookup"><span data-stu-id="37f51-111">Once you have the IP, open up **File Explorer** on your computer and type `\\<TARGET_DEVICE>\c$`, where `<TARGET_DEVICE>` is either the name or the IP Address of your Windows IoT Core device, then hit Enter.</span></span>  

<span data-ttu-id="37f51-112">如果出现提示，请输入你的管理员用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="37f51-112">Enter your administrator username and password if prompted.</span></span> <span data-ttu-id="37f51-113">用户名应使用 Windows IoT 核心版设备的 IP 地址作为前缀。</span><span class="sxs-lookup"><span data-stu-id="37f51-113">The username should be prefixed with the IP Address of your Windows IoT Core device.</span></span> <span data-ttu-id="37f51-114">例如：**用户名：**`192.168.1.118\Administrator`  **密码：** `{your_password}`。</span><span class="sxs-lookup"><span data-stu-id="37f51-114">Example: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.</span></span>

![文件资源管理器](../media/WindowsFileSharing/smb_file_explorer.png)

* <span data-ttu-id="37f51-116">现在你可以使用 Windows 文件共享来访问设备上的文件。</span><span class="sxs-lookup"><span data-stu-id="37f51-116">Now you can access the files on your device using Windows file sharing.</span></span>

## <a name="starting-and-stopping-the-file-sharing-server"></a><span data-ttu-id="37f51-117">启动和停止文件共享服务器</span><span class="sxs-lookup"><span data-stu-id="37f51-117">Starting and stopping the file sharing server</span></span>
* <span data-ttu-id="37f51-118">通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md) 连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="37f51-118">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="37f51-119">默认情况下的文件共享服务器启动时启动设备。</span><span class="sxs-lookup"><span data-stu-id="37f51-119">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="37f51-120">若要停止的文件共享服务器，请键入</span><span class="sxs-lookup"><span data-stu-id="37f51-120">To stop the file sharing  server, type</span></span> `net stop Server /y`
* <span data-ttu-id="37f51-121">若要启动的文件共享服务器，请键入</span><span class="sxs-lookup"><span data-stu-id="37f51-121">To start the file sharing  server, type</span></span> `net start Server`

    ![服务器启动和停止](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a><span data-ttu-id="37f51-123">在启动时禁用和启用文件共享服务器</span><span class="sxs-lookup"><span data-stu-id="37f51-123">Disabling and enabling the file sharing server on startup</span></span>
* <span data-ttu-id="37f51-124">通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md) 连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="37f51-124">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="37f51-125">默认情况下的文件共享服务器启动时启动设备。</span><span class="sxs-lookup"><span data-stu-id="37f51-125">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="37f51-126">若要禁用文件共享服务器，以便它不会启动设备启动后，请键入</span><span class="sxs-lookup"><span data-stu-id="37f51-126">To disable the file sharing  server so that it does not start when the device starts, type</span></span> `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* <span data-ttu-id="37f51-127">若要启用文件共享服务器，因此，当设备启动时启动，请键入</span><span class="sxs-lookup"><span data-stu-id="37f51-127">To enable the file sharing  server so that starts when the device starts, type</span></span> `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![服务器启用和禁用](../media/WindowsFileSharing/smb_enable_disable.png)
