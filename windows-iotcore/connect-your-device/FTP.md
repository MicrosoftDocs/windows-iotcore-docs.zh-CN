---
title: 文件传输协议
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用文件传输协议 (FTP) 在设备之间传输文件。
keywords: windows iot，FTP，文件传输协议，文件传输，设备
ms.openlocfilehash: 00705d6ff00603b8876803633a9c4c88d1ea9675
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230074"
---
# <a name="file-transfer-protocol"></a>文件传输协议
利用文件传输协议 (FTP) ，你可以在 Windows 10 IoT 核心版设备之间传输文件

> [!IMPORTANT]
> 建议通常将 FTP 用于开发人员简化初始开发过程。 不建议在零售设备中使用 FTP。

## <a name="starting-the-ftp-server-on-your-device"></a>启动设备上的 FTP 服务器
* 默认情况下，在 IoT 核心设备上禁用 FTP 服务器。  若要在设备上启动 FTP 服务器，首先需要通过 [PowerShell](../connect-your-device/PowerShell.md) 或 [SSH](../connect-your-device/SSH.md)连接到设备。
* 键入 `start C:\Windows\System32\ftpd.exe`
* 可以通过键入来检查服务器是否正在运行 `tlist` ，这将列出所有正在运行的进程。  如果 FTP 服务器正在运行，则应 `ftpd.exe` 在列表中看到。

![FTP 启动](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-device"></a>停止设备上的 FTP 服务器<a name="stopftp"/>
* 若要在 IoT Core 设备上停止 FTP 服务器，首先需要通过 [PowerShell](../connect-your-device/PowerShell.md) 或 [SSH](../connect-your-device/SSH.md)连接到设备。
* 如果使用 PowerShell 进行连接，请键入 `kill -processname ftpd*` 以停止 FTP 进程。

![FTP PowerShell 停止](../media/ftp/ftp_kill_powershell.png)

* 如果使用 SSH 进行连接，请键入 `kill ftpd*` 以停止 FTP 进程。

![FTP SSH 停止](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a>通过 FTP 访问文件
* IoT Core 设备上的 FTP 服务器在启动时自动启动。  若要连接到它，你需要设备的 IP 地址。  你可以在默认应用上查找设备启动时启动的 IP 地址。

![Windows IoT 核心上的 defaultapp.osd](../media/ftp/DefaultApp.png)

* 获得 IP 后，在电脑上打开 **文件资源管理器** 并键入 `ftp://<TARGET_DEVICE>` ，其中 `<TARGET_DEVICE>` 是设备的名称或 IP 地址，然后按 Enter。  如果出现提示，请输入管理员用户名和密码。

![FTP 资源管理器](../media/ftp/ftp_explorer.png)

* 现在，可以通过 FTP 访问设备上的文件。

## <a name="changing-the-root-ftp-directory"></a>更改根 FTP 目录
* 默认情况下，FTP 服务器显示设备的根目录 C：中的所有文件夹 \\ 。  若要更改根目录，请执行相同的步骤来启动 FTP 服务器，只需将根目录作为参数传入。
* 若要更改它，请先通过 [PowerShell](../connect-your-device/PowerShell.md) 或 [SSH](../connect-your-device/SSH.md)连接到你的设备。
* 如果 FTP 进程已在运行，则[停止](#stopftp)该进程。
* 键入 `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>` ，其中 `<PATH_TO_DIRECTORY>` 是要设置为根目录的目录的绝对路径，例如 `C:\Users\DefaultAccount` 。

![FTP 开头参数](../media/ftp/ftp_start_parameter.png)

现在，当你通过 FTP 连接到设备时，你将看到你设置的根目录的内容。

![包含新根目录的 FTP 资源管理器](../media/ftp/ftp_explorer_parameter.png)

若要使此更改为永久性更改，你需要添加对的调用， `start ftpd.exe <PATH_TO_DIRECTORY>` 其中 `<PATH_TO_DIRECTORY>` 是要设置为根目录的目录的绝对路径（例如 `C:\Data\Users\DefaultAccount` OEMCustomization）并将其放入 `C:\Windows\System32`
