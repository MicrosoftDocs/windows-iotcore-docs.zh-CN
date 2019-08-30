---
title: Windows 文件共享
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 文件共享在设备之间传输文件。
keywords: windows iot, 文件传输, 文件共享, windows 文件共享
ms.openlocfilehash: 00dc17ded4b9c4fbea05faca794766f965d0632a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170333"
---
# <a name="windows-file-sharing"></a><span data-ttu-id="3198c-104">Windows 文件共享</span><span class="sxs-lookup"><span data-stu-id="3198c-104">Windows file sharing</span></span>

<span data-ttu-id="3198c-105">可以使用 Windows 文件共享在设备之间传输文件。</span><span class="sxs-lookup"><span data-stu-id="3198c-105">You can use Windows file sharing to transfer files to and from your device.</span></span>

## <a name="accessing-your-files-using-windows-file-sharing"></a><span data-ttu-id="3198c-106">使用 Windows 文件共享访问你的文件</span><span class="sxs-lookup"><span data-stu-id="3198c-106">Accessing your files using Windows file sharing</span></span>
* <span data-ttu-id="3198c-107">Windows IoT 核心版设备上的文件共享服务器在设备启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="3198c-107">The file sharing server on your Windows IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="3198c-108">若要连接到它，需要你的设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3198c-108">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="3198c-109">你可以在默认应用上找到该 IP 地址，该应用会在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="3198c-109">You can find the IP address on the default app that boots when your device starts.</span></span>

    ![Windows IoT 核心版上的 DefaultApp](../media/WindowsFileSharing/DefaultApp.png)
    
* <span data-ttu-id="3198c-111">有了 IP 后，在计算机上打开“文件资源管理器”并键入 `\\<TARGET_DEVICE>\c$`（其中 `<TARGET_DEVICE>` 是 Windows IoT 核心版设备的名称或 IP 地址），然后点击 Enter。</span><span class="sxs-lookup"><span data-stu-id="3198c-111">Once you have the IP, open up **File Explorer** on your computer and type `\\<TARGET_DEVICE>\c$`, where `<TARGET_DEVICE>` is either the name or the IP Address of your Windows IoT Core device, then hit Enter.</span></span>  

<span data-ttu-id="3198c-112">如果出现提示，请输入你的管理员用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="3198c-112">Enter your administrator username and password if prompted.</span></span> <span data-ttu-id="3198c-113">用户名应使用 Windows IoT 核心版设备的 IP 地址作为前缀。</span><span class="sxs-lookup"><span data-stu-id="3198c-113">The username should be prefixed with the IP Address of your Windows IoT Core device.</span></span> <span data-ttu-id="3198c-114">例如：**用户名**`192.168.1.118\Administrator`  **密码:** `{your_password}`.</span><span class="sxs-lookup"><span data-stu-id="3198c-114">Example: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.</span></span>

![文件资源管理器](../media/WindowsFileSharing/smb_file_explorer.png)

* <span data-ttu-id="3198c-116">现在你可以使用 Windows 文件共享来访问设备上的文件。</span><span class="sxs-lookup"><span data-stu-id="3198c-116">Now you can access the files on your device using Windows file sharing.</span></span>

## <a name="starting-and-stopping-the-file-sharing-server"></a><span data-ttu-id="3198c-117">启动和停止文件共享服务器</span><span class="sxs-lookup"><span data-stu-id="3198c-117">Starting and stopping the file sharing server</span></span>
* <span data-ttu-id="3198c-118">通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md) 连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="3198c-118">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="3198c-119">默认情况下, 启动设备时, 将启动文件共享服务器。</span><span class="sxs-lookup"><span data-stu-id="3198c-119">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="3198c-120">若要停止文件共享服务器, 请键入`net stop Server /y`</span><span class="sxs-lookup"><span data-stu-id="3198c-120">To stop the file sharing  server, type `net stop Server /y`</span></span>
* <span data-ttu-id="3198c-121">若要启动文件共享服务器, 请键入`net start Server`</span><span class="sxs-lookup"><span data-stu-id="3198c-121">To start the file sharing  server, type `net start Server`</span></span>

    ![服务器启动和停止](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a><span data-ttu-id="3198c-123">在启动时禁用和启用文件共享服务器</span><span class="sxs-lookup"><span data-stu-id="3198c-123">Disabling and enabling the file sharing server on startup</span></span>
* <span data-ttu-id="3198c-124">通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md) 连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="3198c-124">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="3198c-125">默认情况下, 启动设备时, 将启动文件共享服务器。</span><span class="sxs-lookup"><span data-stu-id="3198c-125">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="3198c-126">若要禁用文件共享服务器, 使其不会在设备启动时启动, 请键入`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span><span class="sxs-lookup"><span data-stu-id="3198c-126">To disable the file sharing  server so that it does not start when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span></span>
* <span data-ttu-id="3198c-127">若要启用文件共享服务器以便在设备启动时启动, 请键入`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span><span class="sxs-lookup"><span data-stu-id="3198c-127">To enable the file sharing  server so that starts when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span></span>

    ![服务器启用和禁用](../media/WindowsFileSharing/smb_enable_disable.png)
