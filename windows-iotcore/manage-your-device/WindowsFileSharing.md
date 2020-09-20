---
title: Windows 文件共享
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 文件共享在设备之间传输文件。
keywords: windows iot，文件传输，文件共享，windows 文件共享
ms.openlocfilehash: bc96208e892118d6a837b552d03287f37c799001
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782399"
---
# <a name="windows-file-sharing"></a>Windows 文件共享

可以使用 Windows 文件共享在设备之间传输文件。

## <a name="accessing-your-files-using-windows-file-sharing"></a>使用 Windows 文件共享来访问文件
* Windows IoT Core 设备上的文件共享服务器在启动时自动启动。  若要连接到它，你需要设备的 IP 地址。  你可以在默认应用上查找设备启动时启动的 IP 地址。

    ![Windows IoT Core 上的 Defaultapp.osd](../media/WindowsFileSharing/DefaultApp.png)
    
* 获得 IP 后，在计算机上打开 **文件资源管理器** 并键入 `\\<TARGET_DEVICE>\c$` ，其中 `<TARGET_DEVICE>` 是 Windows IoT 核心设备的名称或 IP 地址，然后按 Enter。  

如果出现提示，请输入管理员用户名和密码。 用户名应带有 Windows IoT 核心设备的 IP 地址前缀。 示例： **Username：** `192.168.1.118\Administrator` **Password：** `{your_password}` 。  

![文件资源管理器](../media/WindowsFileSharing/smb_file_explorer.png)

* 现在，你可以使用 Windows 文件共享来访问设备上的文件。

## <a name="starting-and-stopping-the-file-sharing-server"></a>启动和停止文件共享服务器
* 通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md)连接到你的设备。
* 默认情况下，启动设备时，将启动文件共享服务器。
* 若要停止文件共享服务器，请键入 `net stop Server /y`
* 若要启动文件共享服务器，请键入 `net start Server`

    ![服务器启动和停止](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a>在启动时禁用和启用文件共享服务器
* 通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md)连接到你的设备。
* 默认情况下，启动设备时，将启动文件共享服务器。
* 若要禁用文件共享服务器，使其不会在设备启动时启动，请键入 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* 若要启用文件共享服务器，以便在设备启动时启动，请键入 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![服务器启用禁用](../media/WindowsFileSharing/smb_enable_disable.png)
