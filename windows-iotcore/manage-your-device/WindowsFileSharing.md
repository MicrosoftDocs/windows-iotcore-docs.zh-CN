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
# <a name="windows-file-sharing"></a>Windows文件共享

可以使用文件共享Windows向/从设备传输文件。

## <a name="accessing-your-files-using-windows-file-sharing"></a>使用文件共享Windows访问文件
* IoT Core Windows上的文件共享服务器在启动时自动启动。  若要连接到它，需要设备的 IP 地址。  可以在设备启动时启动的默认应用上找到 IP 地址。

    ![IoT 核心Windows DefaultApp](../media/WindowsFileSharing/DefaultApp.png)
    
* 获得 IP 后，在计算机上 **文件资源管理器，** 键入 ，其中 是 Windows IoT 核心设备的名称或 IP 地址， `\\<TARGET_DEVICE>\c$` `<TARGET_DEVICE>` 然后按 Enter。  

如果系统提示，请输入管理员用户名和密码。 用户名的前缀应为 IoT 核心Windows IP 地址。 示例：**用户名：** `192.168.1.118\Administrator` **密码：。** `{your_password}`  

![文件资源管理器](../media/WindowsFileSharing/smb_file_explorer.png)

* 现在，可以使用文件共享访问Windows文件。

## <a name="starting-and-stopping-the-file-sharing-server"></a>启动和停止文件共享服务器
* 连接[PowerShell](../connect-your-device/powershell.md)或[SSH](../connect-your-device/ssh.md)连接到设备。
* 默认情况下，文件共享服务器在设备启动时启动。
* 若要停止文件共享服务器，请键入 `net stop Server /y`
* 若要启动文件共享服务器，请键入 `net start Server`

    ![服务器启动和停止](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a>启动时禁用和启用文件共享服务器
* 连接[PowerShell](../connect-your-device/powershell.md)或[SSH](../connect-your-device/ssh.md)连接到设备。
* 默认情况下，文件共享服务器在设备启动时启动。
* 若要禁用文件共享服务器，以便它不会在设备启动时启动，请键入 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* 若要启用文件共享服务器，以便设备启动时启动，请键入 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![服务器启用禁用](../media/WindowsFileSharing/smb_enable_disable.png)
