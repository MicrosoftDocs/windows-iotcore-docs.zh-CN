---
title: 使用远程控制台应用调试调试应用
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/17
ms.topic: article
description: 了解如何在 Visual Studio 中远程调试 IoT 核心控制台应用程序。
keywords: windows iot, visual studio, 应用部署, 远程调试
ms.openlocfilehash: dc3afad193bc6356a5f897f386f5061adaf6bc01
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170526"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a>使用远程控制台应用调试调试应用

下面介绍如何在 Visual Studio 中远程调试 IoT 核心控制台应用程序:

* 首先，需要在 Windows IoT 核心版设备上设置远程调试器。 首先, 请按照[此处](AppDeployment.md)的步骤在设备上部署任何其他通用 Windows 应用程序 (尝试 HelloWorld 项目)。 这会将所有必需的二进制文件复制到你的设备。 

* 若要在设备上启动远程调试器, 请在电脑上打开 Web 浏览器, 并将`http://<device name/IP address>:8080`其指向以启动[Windows 设备门户](../manage-your-device/DevicePortal.md)。 在凭据对话框中，使用默认的用户名和密码：`Administrator`，`p@ssw0rd`。 Windows 设备管理应启动并显示 Web 管理主屏幕。

* 现在, 导航到 Windows 设备门户的 "调试设置" 部分, 然后单击 "开始 Visual Studio 远程调试器下的" 开始 "按钮。 

    ![WindowsDevicePortalDebugSettings 启动远程调试器](../media/Console/device_portal_start_debugger.png)

* 这将弹出一个消息框并提供连接信息。 

*  在 Visual Studio 中，你可以通过编辑项目的属性配置你的目标（请确保所有突出显示的更改均适用于开发板的名称或 IP 地址）：

    ![控制台应用程序远程计算机项目设置](../media/Console/console_project_settings.png)
    
> [!NOTE]
> 如果未看到上述图像, 请前往上下文菜单中的 "解决方案资源管理器", 并进入 "项目属性"。 可在[此处](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)找到有关项目属性的详细信息。

> [!TIP]
> 你可以使用 IP 地址而不使用 Windows IoT 核心版设备名称。

* 项目配置需修改为启用部署。  为此，请从工具栏的“解决方案配置”下拉菜单中选择“配置管理器”，以打开配置管理器。

    ![控制台应用程序 SolutionConfiguration](../media/Console/configuration_management.png)

    在配置管理器中，确保已针对自己的项目配置选中了“部署”复选框（如果此选项处于禁用状态，则很可能是因为部署选项未全部输入到项目属性的“调试”选项卡中）

    ![控制台应用程序远程计算机项目设置](../media/Console/deploy_checkbox.png)

* 现在，我们可以随时部署到远程 Windows IoT 核心版设备。 只需按 F5 (或选择\| "调试" "开始调试") 即可开始调试应用程序。 你还可以使用生成\|部署解决方案来部署应用程序, 而无需启动调试会话。

> [!NOTE]
> 在 Visual Studio 中运行时, 输出将不会显示在任何位置, 但你将能够设置断点、查看变量值等。

* 若要停止应用, 请按 "停止调试" 按钮 (或选择 "调试\| " "停止调试")。

* 你现在可以运行该应用程序。  只需打开 PowerShell/SSH 连接 ([对于 PowerShell](../connect-your-device/PowerShell.md) , 可以在此处找到有关[SSH](../connect-your-device/SSH.md)的说明), 然后输入前面指定的远程命令。

    ![控制台应用程序输出](../media/Console/console_output.png)

* 调试完应用程序后, 请记得在 Windows IoT Core 设备上停止远程调试器。 要执行此操作, 可以导航到 Windows 设备门户的 "调试设置" 部分, 然后单击 "停止远程调试器" 按钮。

    ![WindowsDevicePortalDebugSettings 停止远程调试器](../media/Console/device_portal_stop_debugger.PNG)

