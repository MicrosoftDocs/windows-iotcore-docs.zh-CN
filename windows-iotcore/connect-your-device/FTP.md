---
title: 文件传输协议
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用文件传输协议 (FTP) 在设备之间传输文件。
keywords: windows iot, FTP, 文件传输协议, 文件传输, 设备
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169142"
---
# <a name="file-transfer-protocol"></a><span data-ttu-id="e6773-104">文件传输协议</span><span class="sxs-lookup"><span data-stu-id="e6773-104">File Transfer Protocol</span></span>
<span data-ttu-id="e6773-105">通过文件传输协议 (FTP), 可以在 Windows 10 IoT 核心设备之间传输文件</span><span class="sxs-lookup"><span data-stu-id="e6773-105">The File Transfer Protocol (FTP) allows you to transfer files to and from your Windows 10 IoT Core device</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6773-106">建议通常将 FTP 用于开发人员简化初始开发过程。</span><span class="sxs-lookup"><span data-stu-id="e6773-106">FTP is recommended generally for developers to ease the initial development process.</span></span> <span data-ttu-id="e6773-107">不建议在零售设备中使用 FTP。</span><span class="sxs-lookup"><span data-stu-id="e6773-107">We do not recommend using FTP in retail devices.</span></span>

## <a name="starting-the-ftp-server-on-your-device"></a><span data-ttu-id="e6773-108">在你的设备上启动 FTP 服务器</span><span class="sxs-lookup"><span data-stu-id="e6773-108">Starting the FTP server on your device</span></span>
* <span data-ttu-id="e6773-109">默认情况下, 在 IoT 核心设备上禁用 FTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="e6773-109">By default, the FTP server is disabled on your IoT Core device.</span></span>  <span data-ttu-id="e6773-110">若要在设备上启动 FTP 服务器, 首先需要通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)连接到设备。</span><span class="sxs-lookup"><span data-stu-id="e6773-110">In order to start the FTP server on your device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="e6773-111">Type `start C:\Windows\System32\ftpd.exe`</span><span class="sxs-lookup"><span data-stu-id="e6773-111">Type `start C:\Windows\System32\ftpd.exe`</span></span>
* <span data-ttu-id="e6773-112">你可以通过键入 `tlist` 检查该服务器是否正在运行，这将列出所有运行中的进程。</span><span class="sxs-lookup"><span data-stu-id="e6773-112">You can check that the server is running by typing `tlist`, which will list all the running processes.</span></span>  <span data-ttu-id="e6773-113">如果 FTP 服务器正在运行，你应该能在该列表中看到 `ftpd.exe`。</span><span class="sxs-lookup"><span data-stu-id="e6773-113">If the FTP server is running, you should see `ftpd.exe` in the list.</span></span>

![FTP 启动](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a><span data-ttu-id="e6773-115">停止在你的设备上运行 FTP 服务器<a name="stopftp"/></span><span class="sxs-lookup"><span data-stu-id="e6773-115">Stopping the FTP server on your device<a name="stopftp"/></span></span>
* <span data-ttu-id="e6773-116">若要在 IoT Core 设备上停止 FTP 服务器, 首先需要通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)连接到设备。</span><span class="sxs-lookup"><span data-stu-id="e6773-116">In order to stop the FTP server on your IoT Core device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="e6773-117">如果使用 PowerShell 进行连接，请键入 `kill -processname ftpd*` 以停止 FTP 进程。</span><span class="sxs-lookup"><span data-stu-id="e6773-117">If you connected using PowerShell, type `kill -processname ftpd*` to stop the FTP process.</span></span>

![FTP PowerShell 停止](../media/ftp/ftp_kill_powershell.png)

* <span data-ttu-id="e6773-119">如果使用 SSH 进行连接，请键入 `kill ftpd*` 以停止 FTP 进程。</span><span class="sxs-lookup"><span data-stu-id="e6773-119">If you connected using SSH, type `kill ftpd*` to stop the FTP process.</span></span>

![FTP SSH 停止](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a><span data-ttu-id="e6773-121">通过 FTP 访问文件</span><span class="sxs-lookup"><span data-stu-id="e6773-121">Accessing your files over FTP</span></span>
* <span data-ttu-id="e6773-122">IoT Core 设备上的 FTP 服务器在启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="e6773-122">The FTP server on your IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="e6773-123">若要连接到它，需要你的设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e6773-123">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="e6773-124">你可以在默认应用上找到该 IP 地址，该应用会在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="e6773-124">You can find the IP address on the default app that boots when your device starts.</span></span>

![Windows IoT 核心版上的 DefaultApp](../media/ftp/DefaultApp.png)

* <span data-ttu-id="e6773-126">获得 IP 后, 在电脑上打开**文件资源管理器**并键入`ftp://<TARGET_DEVICE>`, 其中`<TARGET_DEVICE>`是设备的名称或 IP 地址, 然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="e6773-126">Once you have the IP, open up **File Explorer** on your PC and type `ftp://<TARGET_DEVICE>`, where `<TARGET_DEVICE>` is either the name or the IP address of your device, then hit Enter.</span></span>  <span data-ttu-id="e6773-127">如果出现提示，请输入你的管理员用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="e6773-127">Enter your administrator username and password if prompted.</span></span>

![FTP 资源管理器](../media/ftp/ftp_explorer.png)

* <span data-ttu-id="e6773-129">现在，你可以通过 FTP 访问你的设备上的文件。</span><span class="sxs-lookup"><span data-stu-id="e6773-129">Now you can access the files on your device through FTP.</span></span>

## <a name="changing-the-root-ftp-directory"></a><span data-ttu-id="e6773-130">更改 FTP 根目录</span><span class="sxs-lookup"><span data-stu-id="e6773-130">Changing the root FTP directory</span></span>
* <span data-ttu-id="e6773-131">默认情况下, FTP 服务器显示设备的根目录 C:\\中的所有文件夹。</span><span class="sxs-lookup"><span data-stu-id="e6773-131">By default the FTP server displays all the folders in the device's root directory C:\\.</span></span>  <span data-ttu-id="e6773-132">若要更改根目录, 请执行相同的步骤来启动 FTP 服务器, 只需将根目录作为参数传入。</span><span class="sxs-lookup"><span data-stu-id="e6773-132">In order to change the root directory, follow the same steps to start the FTP server, except you need to pass in the root directory as a parameter.</span></span>
* <span data-ttu-id="e6773-133">若要更改它，请先通过 [PowerShell](../connect-your-device/PowerShell.md) 或 [SSH](../connect-your-device/SSH.md) 连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="e6773-133">In order to change it, first connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="e6773-134">如果 FTP 进程已在运行，请[停止](#stopftp)该进程。</span><span class="sxs-lookup"><span data-stu-id="e6773-134">[Stop](#stopftp) the FTP process if it's already running.</span></span>
* <span data-ttu-id="e6773-135">键入 `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`，其中 `<PATH_TO_DIRECTORY>` 是要设置为根目录的目录的绝对路径，例如 `C:\Users\DefaultAccount`。</span><span class="sxs-lookup"><span data-stu-id="e6773-135">Type `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Users\DefaultAccount`.</span></span>

![带有参数的 FTP 启动](../media/ftp/ftp_start_parameter.png)

<span data-ttu-id="e6773-137">现在, 当你通过 FTP 连接到设备时, 你将看到你设置的根目录的内容。</span><span class="sxs-lookup"><span data-stu-id="e6773-137">Now when you connect to your device through FTP, you will see the contents of the root directory you set.</span></span>

![具有新的根目录的 FTP 资源管理器](../media/ftp/ftp_explorer_parameter.png)

<span data-ttu-id="e6773-139">若要使此更改为永久性更改, 你需要添加对`start ftpd.exe <PATH_TO_DIRECTORY>`的调用, 其中`<PATH_TO_DIRECTORY>`是要设置为`C:\Data\Users\DefaultAccount`根目录的目录的绝对路径 (例如 OEMCustomization) 并将其放入`C:\Windows\System32`</span><span class="sxs-lookup"><span data-stu-id="e6773-139">In order to make this change permanent, you need to add a call to `start ftpd.exe <PATH_TO_DIRECTORY>` where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Data\Users\DefaultAccount` to OEMCustomization.cmd and place it in `C:\Windows\System32`</span></span>
