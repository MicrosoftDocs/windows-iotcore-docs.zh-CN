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
# <a name="file-transfer-protocol"></a>文件传输协议
文件传输协议 (FTP)，可从 Windows 10 IoT Core 设备来回传输文件

> [!IMPORTANT]
> 对于开发人员能够轻松地完成初始开发过程，通常建议 FTP。 我们不建议在零售设备中使用 FTP。

## <a name="starting-the-ftp-server-on-your-device"></a>在你的设备上启动 FTP 服务器
* 默认情况下，在 IoT Core 设备上禁用 FTP 服务器。  若要在设备上启动 FTP 服务器，首先你需要连接到你的设备通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)。
* 在任务栏的搜索框中键入 `start C:\Windows\System32\ftpd.exe`
* 你可以通过键入 `tlist` 检查该服务器是否正在运行，这将列出所有运行中的进程。  如果 FTP 服务器正在运行，你应该能在该列表中看到 `ftpd.exe`。

![FTP 启动](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a>停止在你的设备上运行 FTP 服务器<a name="stopftp"/>
* 若要停止 IoT Core 设备上的 FTP 服务器，首先需要连接到你的设备通过[PowerShell](../connect-your-device/PowerShell.md)或[SSH](../connect-your-device/SSH.md)。
* 如果使用 PowerShell 进行连接，请键入 `kill -processname ftpd*` 以停止 FTP 进程。

![FTP PowerShell 停止](../media/ftp/ftp_kill_powershell.png)

* 如果使用 SSH 进行连接，请键入 `kill ftpd*` 以停止 FTP 进程。

![FTP SSH 停止](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a>通过 FTP 访问你的文件
* IoT Core 设备上的 FTP 服务器上启动会自动启动。  若要连接到它，需要你的设备的 IP 地址。  你可以在默认应用上找到该 IP 地址，该应用会在设备启动时启动。

![Windows IoT 核心版上的 DefaultApp](../media/ftp/DefaultApp.png)

* IP 后，打开**文件资源管理器**上您的 PC 和类型`ftp://<TARGET_DEVICE>`，其中`<TARGET_DEVICE>`是名称或 IP 地址的设备，然后按的 Enter。  如果出现提示，请输入你的管理员用户名和密码。

![FTP 资源管理器](../media/ftp/ftp_explorer.png)

* 现在，你可以通过 FTP 访问你的设备上的文件。

## <a name="changing-the-root-ftp-directory"></a>更改 FTP 根目录
* 默认情况下，FTP 服务器所显示的设备的根目录 c： 中的所有文件夹\\。  若要更改的根目录，请执行相同的步骤来启动 FTP 服务器，只需要传递作为参数的根目录中。
* 若要更改它，请先通过 [PowerShell](../connect-your-device/PowerShell.md) 或 [SSH](../connect-your-device/SSH.md) 连接到你的设备。
* 如果 FTP 进程已在运行，请[停止](#stopftp)该进程。
* 键入 `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`，其中 `<PATH_TO_DIRECTORY>` 是要设置为根目录的目录的绝对路径，例如 `C:\Users\DefaultAccount`。

![带有参数的 FTP 启动](../media/ftp/ftp_start_parameter.png)

现在当你连接到你的设备通过 FTP，会看到设置的根目录的内容。

![具有新的根目录的 FTP 资源管理器](../media/ftp/ftp_explorer_parameter.png)

若要进行此更改永久，需要添加对的调用`start ftpd.exe <PATH_TO_DIRECTORY>`其中`<PATH_TO_DIRECTORY>`是你想要将设置为根目录，例如的目录的绝对路径`C:\Data\Users\DefaultAccount`到 OEMCustomization.cmd 并将其放在 `C:\Windows\System32`
