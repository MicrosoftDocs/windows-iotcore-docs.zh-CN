---
title: 文件传输协议
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用文件传输协议 (FTP) 传输到和从你的设备的文件。
keywords: windows iot、 FTP、 文件传输协议、 文件传输、 设备
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510709"
---
# <a name="file-transfer-protocol"></a><span data-ttu-id="2a05b-104">文件传输协议</span><span class="sxs-lookup"><span data-stu-id="2a05b-104">File Transfer Protocol</span></span>
<span data-ttu-id="2a05b-105">文件传输协议 (FTP)，可从 Windows 10 IoT Core 设备来回传输文件</span><span class="sxs-lookup"><span data-stu-id="2a05b-105">The File Transfer Protocol (FTP) allows you to transfer files to and from your Windows 10 IoT Core device</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a05b-106">对于开发人员能够轻松地完成初始开发过程，通常建议 FTP。</span><span class="sxs-lookup"><span data-stu-id="2a05b-106">FTP is recommended generally for developers to ease the initial development process.</span></span> <span data-ttu-id="2a05b-107">我们不建议在零售设备中使用 FTP。</span><span class="sxs-lookup"><span data-stu-id="2a05b-107">We do not recommend using FTP in retail devices.</span></span>

## <a name="starting-the-ftp-server-on-your-device"></a><span data-ttu-id="2a05b-108">在你的设备上启动 FTP 服务器</span><span class="sxs-lookup"><span data-stu-id="2a05b-108">Starting the FTP server on your device</span></span>
* <span data-ttu-id="2a05b-109">默认情况下，在 IoT Core 设备上禁用 FTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="2a05b-109">By default, the FTP server is disabled on your IoT Core device.</span></span>  <span data-ttu-id="2a05b-110">若要在设备上启动 FTP 服务器，首先你需要连接到你的设备通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)。</span><span class="sxs-lookup"><span data-stu-id="2a05b-110">In order to start the FTP server on your device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="2a05b-111">在任务栏的搜索框中键入</span><span class="sxs-lookup"><span data-stu-id="2a05b-111">Type</span></span> `start C:\Windows\System32\ftpd.exe`
* <span data-ttu-id="2a05b-112">你可以通过键入 `tlist` 检查该服务器是否正在运行，这将列出所有运行中的进程。</span><span class="sxs-lookup"><span data-stu-id="2a05b-112">You can check that the server is running by typing `tlist`, which will list all the running processes.</span></span>  <span data-ttu-id="2a05b-113">如果 FTP 服务器正在运行，你应该能在该列表中看到 `ftpd.exe`。</span><span class="sxs-lookup"><span data-stu-id="2a05b-113">If the FTP server is running, you should see `ftpd.exe` in the list.</span></span>

![FTP 启动](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a><span data-ttu-id="2a05b-115">停止在你的设备上运行 FTP 服务器<a name="stopftp"/></span><span class="sxs-lookup"><span data-stu-id="2a05b-115">Stopping the FTP server on your device<a name="stopftp"/></span></span>
* <span data-ttu-id="2a05b-116">若要停止 IoT Core 设备上的 FTP 服务器，首先需要连接到你的设备通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)。</span><span class="sxs-lookup"><span data-stu-id="2a05b-116">In order to stop the FTP server on your IoT Core device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="2a05b-117">如果使用 PowerShell 进行连接，请键入 `kill -processname ftpd*` 以停止 FTP 进程。</span><span class="sxs-lookup"><span data-stu-id="2a05b-117">If you connected using PowerShell, type `kill -processname ftpd*` to stop the FTP process.</span></span>

![FTP PowerShell 停止](../media/ftp/ftp_kill_powershell.png)

* <span data-ttu-id="2a05b-119">如果使用 SSH 进行连接，请键入 `kill ftpd*` 以停止 FTP 进程。</span><span class="sxs-lookup"><span data-stu-id="2a05b-119">If you connected using SSH, type `kill ftpd*` to stop the FTP process.</span></span>

![FTP SSH 停止](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a><span data-ttu-id="2a05b-121">通过 FTP 访问你的文件</span><span class="sxs-lookup"><span data-stu-id="2a05b-121">Accessing your files over FTP</span></span>
* <span data-ttu-id="2a05b-122">IoT Core 设备上的 FTP 服务器上启动会自动启动。</span><span class="sxs-lookup"><span data-stu-id="2a05b-122">The FTP server on your IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="2a05b-123">若要连接到它，需要你的设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="2a05b-123">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="2a05b-124">你可以在默认应用上找到该 IP 地址，该应用会在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="2a05b-124">You can find the IP address on the default app that boots when your device starts.</span></span>

![Windows IoT 核心版上的 DefaultApp](../media/ftp/DefaultApp.png)

* <span data-ttu-id="2a05b-126">IP 后，打开**文件资源管理器**上您的 PC 和类型`ftp://<TARGET_DEVICE>`，其中`<TARGET_DEVICE>`是名称或 IP 地址的设备，然后按的 Enter。</span><span class="sxs-lookup"><span data-stu-id="2a05b-126">Once you have the IP, open up **File Explorer** on your PC and type `ftp://<TARGET_DEVICE>`, where `<TARGET_DEVICE>` is either the name or the IP address of your device, then hit Enter.</span></span>  <span data-ttu-id="2a05b-127">如果出现提示，请输入你的管理员用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="2a05b-127">Enter your administrator username and password if prompted.</span></span>

![FTP 资源管理器](../media/ftp/ftp_explorer.png)

* <span data-ttu-id="2a05b-129">现在，你可以通过 FTP 访问你的设备上的文件。</span><span class="sxs-lookup"><span data-stu-id="2a05b-129">Now you can access the files on your device through FTP.</span></span>

## <a name="changing-the-root-ftp-directory"></a><span data-ttu-id="2a05b-130">更改 FTP 根目录</span><span class="sxs-lookup"><span data-stu-id="2a05b-130">Changing the root FTP directory</span></span>
* <span data-ttu-id="2a05b-131">默认情况下，FTP 服务器所显示的设备的根目录 c： 中的所有文件夹\\。</span><span class="sxs-lookup"><span data-stu-id="2a05b-131">By default the FTP server displays all the folders in the device's root directory C:\\.</span></span>  <span data-ttu-id="2a05b-132">若要更改的根目录，请执行相同的步骤来启动 FTP 服务器，只需要传递作为参数的根目录中。</span><span class="sxs-lookup"><span data-stu-id="2a05b-132">In order to change the root directory, follow the same steps to start the FTP server, except you need to pass in the root directory as a parameter.</span></span>
* <span data-ttu-id="2a05b-133">若要更改它，请先通过 [PowerShell](../connect-your-device/PowerShell.md) 或 [SSH](../connect-your-device/SSH.md) 连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="2a05b-133">In order to change it, first connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="2a05b-134">如果 FTP 进程已在运行，请[停止](#stopftp)该进程。</span><span class="sxs-lookup"><span data-stu-id="2a05b-134">[Stop](#stopftp) the FTP process if it's already running.</span></span>
* <span data-ttu-id="2a05b-135">键入 `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`，其中 `<PATH_TO_DIRECTORY>` 是要设置为根目录的目录的绝对路径，例如 `C:\Users\DefaultAccount`。</span><span class="sxs-lookup"><span data-stu-id="2a05b-135">Type `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Users\DefaultAccount`.</span></span>

![带有参数的 FTP 启动](../media/ftp/ftp_start_parameter.png)

<span data-ttu-id="2a05b-137">现在当你连接到你的设备通过 FTP，会看到设置的根目录的内容。</span><span class="sxs-lookup"><span data-stu-id="2a05b-137">Now when you connect to your device through FTP, you will see the contents of the root directory you set.</span></span>

![具有新的根目录的 FTP 资源管理器](../media/ftp/ftp_explorer_parameter.png)

<span data-ttu-id="2a05b-139">若要进行此更改永久，需要添加对的调用`start ftpd.exe <PATH_TO_DIRECTORY>`其中`<PATH_TO_DIRECTORY>`是你想要将设置为根目录，例如的目录的绝对路径`C:\Data\Users\DefaultAccount`到 OEMCustomization.cmd 并将其放在</span><span class="sxs-lookup"><span data-stu-id="2a05b-139">In order to make this change permanent, you need to add a call to `start ftpd.exe <PATH_TO_DIRECTORY>` where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Data\Users\DefaultAccount` to OEMCustomization.cmd and place it in</span></span> `C:\Windows\System32`
