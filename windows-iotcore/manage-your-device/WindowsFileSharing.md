---
title: Windows 文件共享
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用Windows文件共享向/从设备传输文件。
keywords: windows iot， 文件传输， 文件共享， Windows 文件共享
ms.openlocfilehash: 84a75244cc1348e0a733c385bb0f20742e0fa273
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229444"
---
# <a name="windows-file-sharing"></a><span data-ttu-id="f5095-104">Windows文件共享</span><span class="sxs-lookup"><span data-stu-id="f5095-104">Windows file sharing</span></span>

<span data-ttu-id="f5095-105">可以使用文件共享Windows向/从设备传输文件。</span><span class="sxs-lookup"><span data-stu-id="f5095-105">You can use Windows file sharing to transfer files to and from your device.</span></span>

## <a name="accessing-your-files-using-windows-file-sharing"></a><span data-ttu-id="f5095-106">使用文件共享Windows访问文件</span><span class="sxs-lookup"><span data-stu-id="f5095-106">Accessing your files using Windows file sharing</span></span>
* <span data-ttu-id="f5095-107">IoT Core Windows上的文件共享服务器在启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="f5095-107">The file sharing server on your Windows IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="f5095-108">若要连接到它，需要设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f5095-108">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="f5095-109">可以在设备启动时启动的默认应用上找到 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f5095-109">You can find the IP address on the default app that boots when your device starts.</span></span>

    ![IoT 核心Windows DefaultApp](../media/WindowsFileSharing/DefaultApp.png)
    
* <span data-ttu-id="f5095-111">获得 IP 后，在计算机上 **文件资源管理器，** 键入 ，其中 是 Windows IoT 核心设备的名称或 IP 地址， `\\<TARGET_DEVICE>\c$` `<TARGET_DEVICE>` 然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="f5095-111">Once you have the IP, open up **File Explorer** on your computer and type `\\<TARGET_DEVICE>\c$`, where `<TARGET_DEVICE>` is either the name or the IP Address of your Windows IoT Core device, then hit Enter.</span></span>  

<span data-ttu-id="f5095-112">如果系统提示，请输入管理员用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="f5095-112">Enter your administrator username and password if prompted.</span></span> <span data-ttu-id="f5095-113">用户名的前缀应为 IoT 核心Windows IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f5095-113">The username should be prefixed with the IP Address of your Windows IoT Core device.</span></span> <span data-ttu-id="f5095-114">示例：**用户名：** `192.168.1.118\Administrator` **密码：。** `{your_password}`  </span><span class="sxs-lookup"><span data-stu-id="f5095-114">Example: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.</span></span>

![文件资源管理器](../media/WindowsFileSharing/smb_file_explorer.png)

* <span data-ttu-id="f5095-116">现在，可以使用文件共享访问Windows文件。</span><span class="sxs-lookup"><span data-stu-id="f5095-116">Now you can access the files on your device using Windows file sharing.</span></span>

## <a name="starting-and-stopping-the-file-sharing-server"></a><span data-ttu-id="f5095-117">启动和停止文件共享服务器</span><span class="sxs-lookup"><span data-stu-id="f5095-117">Starting and stopping the file sharing server</span></span>
* <span data-ttu-id="f5095-118">连接[PowerShell](../connect-your-device/powershell.md)或[SSH](../connect-your-device/ssh.md)连接到设备。</span><span class="sxs-lookup"><span data-stu-id="f5095-118">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="f5095-119">默认情况下，文件共享服务器在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="f5095-119">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="f5095-120">若要停止文件共享服务器，请键入 `net stop Server /y`</span><span class="sxs-lookup"><span data-stu-id="f5095-120">To stop the file sharing  server, type `net stop Server /y`</span></span>
* <span data-ttu-id="f5095-121">若要启动文件共享服务器，请键入 `net start Server`</span><span class="sxs-lookup"><span data-stu-id="f5095-121">To start the file sharing  server, type `net start Server`</span></span>

    ![服务器启动和停止](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a><span data-ttu-id="f5095-123">启动时禁用和启用文件共享服务器</span><span class="sxs-lookup"><span data-stu-id="f5095-123">Disabling and enabling the file sharing server on startup</span></span>
* <span data-ttu-id="f5095-124">连接[PowerShell](../connect-your-device/powershell.md)或[SSH](../connect-your-device/ssh.md)连接到设备。</span><span class="sxs-lookup"><span data-stu-id="f5095-124">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="f5095-125">默认情况下，文件共享服务器在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="f5095-125">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="f5095-126">若要禁用文件共享服务器，以便它不会在设备启动时启动，请键入 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span><span class="sxs-lookup"><span data-stu-id="f5095-126">To disable the file sharing  server so that it does not start when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span></span>
* <span data-ttu-id="f5095-127">若要启用文件共享服务器，以便设备启动时启动，请键入 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span><span class="sxs-lookup"><span data-stu-id="f5095-127">To enable the file sharing server, so that starts when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span></span>

    ![服务器启用禁用](../media/WindowsFileSharing/smb_enable_disable.png)
