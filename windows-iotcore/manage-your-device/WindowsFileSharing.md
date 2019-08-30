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
# <a name="windows-file-sharing"></a>Windows 文件共享

可以使用 Windows 文件共享在设备之间传输文件。

## <a name="accessing-your-files-using-windows-file-sharing"></a>使用 Windows 文件共享访问你的文件
* Windows IoT 核心版设备上的文件共享服务器在设备启动时自动启动。  若要连接到它，需要你的设备的 IP 地址。  你可以在默认应用上找到该 IP 地址，该应用会在设备启动时启动。

    ![Windows IoT 核心版上的 DefaultApp](../media/WindowsFileSharing/DefaultApp.png)
    
* 有了 IP 后，在计算机上打开“文件资源管理器”并键入 `\\<TARGET_DEVICE>\c$`（其中 `<TARGET_DEVICE>` 是 Windows IoT 核心版设备的名称或 IP 地址），然后点击 Enter。  

如果出现提示，请输入你的管理员用户名和密码。 用户名应使用 Windows IoT 核心版设备的 IP 地址作为前缀。 例如：**用户名**`192.168.1.118\Administrator`  **密码:** `{your_password}`.

![文件资源管理器](../media/WindowsFileSharing/smb_file_explorer.png)

* 现在你可以使用 Windows 文件共享来访问设备上的文件。

## <a name="starting-and-stopping-the-file-sharing-server"></a>启动和停止文件共享服务器
* 通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md) 连接到你的设备。
* 默认情况下, 启动设备时, 将启动文件共享服务器。
* 若要停止文件共享服务器, 请键入`net stop Server /y`
* 若要启动文件共享服务器, 请键入`net start Server`

    ![服务器启动和停止](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a>在启动时禁用和启用文件共享服务器
* 通过 [PowerShell](../connect-your-device/powershell.md) 或 [SSH](../connect-your-device/ssh.md) 连接到你的设备。
* 默认情况下, 启动设备时, 将启动文件共享服务器。
* 若要禁用文件共享服务器, 使其不会在设备启动时启动, 请键入`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* 若要启用文件共享服务器以便在设备启动时启动, 请键入`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![服务器启用和禁用](../media/WindowsFileSharing/smb_enable_disable.png)
