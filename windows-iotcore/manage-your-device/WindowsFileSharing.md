---
title: Windows 文件共享
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 文件共享在设备之间传输文件。
keywords: windows iot，文件传输，文件共享，windows 文件共享
ms.openlocfilehash: bd21300fc25f2cde644f0ba24418805edbd5e955
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655253"
---
# <a name="windows-file-sharing"></a><span data-ttu-id="7a390-104">Windows 文件共享</span><span class="sxs-lookup"><span data-stu-id="7a390-104">Windows file sharing</span></span>

<span data-ttu-id="7a390-105">可以使用 Windows 文件共享在设备之间传输文件。</span><span class="sxs-lookup"><span data-stu-id="7a390-105">You can use Windows file sharing to transfer files to and from your device.</span></span>

## <a name="accessing-your-files-using-windows-file-sharing"></a><span data-ttu-id="7a390-106">使用 Windows 文件共享来访问文件</span><span class="sxs-lookup"><span data-stu-id="7a390-106">Accessing your files using Windows file sharing</span></span>
* <span data-ttu-id="7a390-107">Windows IoT Core 设备上的文件共享服务器在启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="7a390-107">The file sharing server on your Windows IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="7a390-108">若要连接到它，你需要设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="7a390-108">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="7a390-109">你可以在默认应用上查找设备启动时启动的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="7a390-109">You can find the IP address on the default app that boots when your device starts.</span></span>

    ![Windows IoT Core 上的 Defaultapp.osd](../media/WindowsFileSharing/DefaultApp.png)
    
* <span data-ttu-id="7a390-111">获得 IP 后，在计算机上打开 **文件资源管理器** 并键入 `\\<TARGET_DEVICE>\c$` ，其中 `<TARGET_DEVICE>` 是 Windows IoT 核心设备的名称或 IP 地址，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="7a390-111">Once you have the IP, open up **File Explorer** on your computer and type `\\<TARGET_DEVICE>\c$`, where `<TARGET_DEVICE>` is either the name or the IP Address of your Windows IoT Core device, then hit Enter.</span></span>  

<span data-ttu-id="7a390-112">如果出现提示，请输入管理员用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="7a390-112">Enter your administrator username and password if prompted.</span></span> <span data-ttu-id="7a390-113">用户名应带有 Windows IoT 核心设备的 IP 地址前缀。</span><span class="sxs-lookup"><span data-stu-id="7a390-113">The username should be prefixed with the IP Address of your Windows IoT Core device.</span></span> <span data-ttu-id="7a390-114">示例： **Username：** `192.168.1.118\Administrator` **Password：** `{your_password}` 。  </span><span class="sxs-lookup"><span data-stu-id="7a390-114">Example: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.</span></span>

![文件资源管理器](../media/WindowsFileSharing/smb_file_explorer.png)

* <span data-ttu-id="7a390-116">现在，你可以使用 Windows 文件共享来访问设备上的文件。</span><span class="sxs-lookup"><span data-stu-id="7a390-116">Now you can access the files on your device using Windows file sharing.</span></span>

## <a name="starting-and-stopping-the-file-sharing-server"></a><span data-ttu-id="7a390-117">启动和停止文件共享服务器</span><span class="sxs-lookup"><span data-stu-id="7a390-117">Starting and stopping the file sharing server</span></span>
* <span data-ttu-id="7a390-118">通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md)连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="7a390-118">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="7a390-119">默认情况下，启动设备时，将启动文件共享服务器。</span><span class="sxs-lookup"><span data-stu-id="7a390-119">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="7a390-120">若要停止文件共享服务器，请键入 `net stop Server /y`</span><span class="sxs-lookup"><span data-stu-id="7a390-120">To stop the file sharing  server, type `net stop Server /y`</span></span>
* <span data-ttu-id="7a390-121">若要启动文件共享服务器，请键入 `net start Server`</span><span class="sxs-lookup"><span data-stu-id="7a390-121">To start the file sharing  server, type `net start Server`</span></span>

    ![服务器启动和停止](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a><span data-ttu-id="7a390-123">在启动时禁用和启用文件共享服务器</span><span class="sxs-lookup"><span data-stu-id="7a390-123">Disabling and enabling the file sharing server on startup</span></span>
* <span data-ttu-id="7a390-124">通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md)连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="7a390-124">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="7a390-125">默认情况下，启动设备时，将启动文件共享服务器。</span><span class="sxs-lookup"><span data-stu-id="7a390-125">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="7a390-126">若要禁用文件共享服务器，使其不会在设备启动时启动，请键入 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span><span class="sxs-lookup"><span data-stu-id="7a390-126">To disable the file sharing  server so that it does not start when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span></span>
* <span data-ttu-id="7a390-127">若要启用文件共享服务器，以便在设备启动时启动，请键入 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span><span class="sxs-lookup"><span data-stu-id="7a390-127">To enable the file sharing server, so that starts when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span></span>

    ![服务器启用禁用](../media/WindowsFileSharing/smb_enable_disable.png)
