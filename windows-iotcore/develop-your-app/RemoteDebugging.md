---
title: 使用远程控制台应用调试来调试应用
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在 Visual Studio 中远程调试 IoT 核心控制台应用程序。
keywords: windows iot，visual studio，应用部署，远程调试
ms.openlocfilehash: 3c07e78ca9a73f38f56f9c762ebe98057daf3981
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229794"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a>使用远程控制台应用调试来调试应用

下面是在 Visual Studio 中远程调试 IoT 核心控制台应用程序的方法：

* 首先需要在 Windows IoT 核心设备上设置远程调试器。 首先，请按照[此处](AppDeployment.md)的步骤在设备上部署任何其他通用 Windows 应用程序 (尝试 HelloWorld 项目) 。 这会将所有必需的二进制文件复制到设备。

* 若要在设备上启动远程调试器，请在电脑上打开 Web 浏览器，并将其指向 `http://<device name/IP address>:8080` 以启动[Windows 设备门户](../manage-your-device/DevicePortal.md)。 在 "凭据" 对话框中，使用默认的 "用户名" 和 "密码： `Administrator` " `p@ssw0rd` 。 Windows设备管理应启动并显示 web 管理主屏幕。

* 现在，导航到 Windows 设备门户的 "调试设置" 部分，然后单击 "启动 Visual Studio 远程调试器下的" 开始 "按钮。

    ![WindowsDevicePortalDebugSettings 启动远程调试器](../media/Console/device_portal_start_debugger.png)

* 此时将显示一个消息框，并向你显示连接信息。

*  在 Visual Studio 中，你可以通过编辑项目属性来配置目标 (确保将所有突出显示的更改设置为适用于你的板名称或 IP 地址) ：

    ![控制台应用程序远程计算机 Project 设置](../media/Console/console_project_settings.png)

> [!NOTE]
> 如果未看到上述图像，请前往上下文菜单中的 "解决方案资源管理器"，并进入 "Project 属性"。 有关项目属性的详细信息，请参阅 [此处] (https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017&preserve-view=true 。

> [!TIP]
> 你可以使用 IP 地址而不是 Windows IoT 核心设备名称。

* 需要修改项目配置才能启用部署。  为此，请通过从工具栏上的 "解决方案配置" 下拉菜单中选择 "配置管理器" 来打开 Configuration Manager。

    ![控制台应用程序 SolutionConfiguration](../media/Console/configuration_management.png)

    在 Configuration Manager 中，确保为你的项目配置选择 "部署" 复选框 (如果禁用此选项，则可能尚未将部署选项完全输入到项目属性的 "调试" 选项卡中) 

    ![控制台应用程序远程计算机 Project 设置1](../media/Console/deploy_checkbox.png)

* 现在，我们已准备好部署到远程 Windows IoT 核心设备。 只需按 F5 (或选择 "调试&quot; &quot; \| 开始调试") 即可开始调试应用程序。 你还可以使用生成 \| 部署解决方案来部署应用程序，而无需启动调试会话。

> [!NOTE]
> 从 Visual Studio 运行时，输出将不会显示在任何位置，但你将能够设置断点、查看变量值等。

* 若要停止应用，请按 "停止调试" 按钮 (或选择 "调试" " \| 停止调试") 。

* 你现在可以运行该应用程序。  只需打开 PowerShell/SSH 连接 (就可以在 [此处找到适用](../connect-your-device/PowerShell.md) 于 PowerShell [) 的](../connect-your-device/SSH.md) 说明，并输入前面指定的远程命令。

    ![控制台应用程序输出](../media/Console/console_output.png)

* 调试完应用程序后，请记得在 Windows IoT 核心设备上停止远程调试器。 为此，可以导航到 Windows 设备门户的 "调试设置" 部分，然后单击 "停止远程调试器" 按钮。

    ![WindowsDevicePortalDebugSettings 停止远程调试器](../media/Console/device_portal_stop_debugger.PNG)
