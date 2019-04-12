---
title: 使用远程控制台应用程序调试调试应用
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/17
ms.topic: article
description: 了解如何在 Visual Studio 中的远程 IoT Core 控制台应用程序进行远程调试。
keywords: windows iot、 visual studio、 应用部署、 远程调试
ms.openlocfilehash: dc3afad193bc6356a5f897f386f5061adaf6bc01
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510766"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a>使用远程控制台应用程序调试调试应用

下面介绍了如何调试在 Visual Studio 中的远程 IoT Core 控制台应用程序：

* 首先，需要在 Windows IoT 核心版设备上设置远程调试器。 首先按照步骤[此处](AppDeployment.md)部署任何其他通用 Windows 应用程序在你的设备 （尝试 HelloWorld 项目）。 这会将所有必需的二进制文件复制到你的设备。 

* 若要在设备上启动远程调试器，打开您的 PC 上的 Web 浏览器并之指向`http://<device name/IP address>:8080`以启动[Windows Device Portal](../manage-your-device/DevicePortal.md)。 在凭据对话框中，使用默认的用户名和密码：`Administrator`，`p@ssw0rd`。 Windows 设备管理应启动并显示 Web 管理主屏幕。

* 现在导航到 Windows Device Portal 调试设置部分并单击开始按钮下启动 Visual Studio 远程调试器。 

    ![WindowsDevicePortalDebugSettings 启动远程调试器](../media/Console/device_portal_start_debugger.png)

* 这将弹出一个消息框并提供连接信息。 

*  在 Visual Studio 中，你可以通过编辑项目的属性配置你的目标（请确保所有突出显示的更改均适用于开发板的名称或 IP 地址）：

    ![控制台应用程序远程计算机项目设置](../media/Console/console_project_settings.png)
    
> [!NOTE]
> 如果你看不到上面的图像，请转到"解决方案资源管理器"上下文菜单中，转到"项目属性"。 你可以找到有关项目属性的详细信息[此处](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)。

> [!TIP]
> 你可以使用 IP 地址而不使用 Windows IoT 核心版设备名称。

* 项目配置需修改为启用部署。  为此，请从工具栏的“解决方案配置”下拉菜单中选择“配置管理器”，以打开配置管理器。

    ![ConsoleApplication SolutionConfiguration](../media/Console/configuration_management.png)

    在配置管理器中，确保已针对自己的项目配置选中了“部署”复选框（如果此选项处于禁用状态，则很可能是因为部署选项未全部输入到项目属性的“调试”选项卡中）

    ![控制台应用程序远程计算机项目设置](../media/Console/deploy_checkbox.png)

* 现在，我们可以随时部署到远程 Windows IoT 核心版设备。 只需按 F5 (或选择调试\|开始调试) 若要开始调试我们的应用程序。 你还可以使用生成\|部署解决方案，只需将应用程序部署而无需启动调试会话。

> [!NOTE]
> 从 Visual Studio 运行时，输出将不显示任何位置，但您将能够设置断点，请参阅变量值，等等。

* 若要停止应用，请按停止调试按钮 (或选择调试\|停止调试)。

* 你现在可以运行该应用程序。  只需打开的 PowerShell/SSH 连接。 (可以找到说明[在此处供 PowerShell](../connect-your-device/PowerShell.md)和[在此处供 SSH](../connect-your-device/SSH.md))，然后输入上面指定的远程命令。

    ![控制台应用程序输出](../media/Console/console_output.png)

* 完成后调试应用程序，请记住，在 Windows IoT Core 设备上停止远程调试器。 可以通过导航来调试 Windows Device Portal 设置部分并单击停止远程调试器按钮来执行此操作。

    ![WindowsDevicePortalDebugSettings 停止远程调试器](../media/Console/device_portal_stop_debugger.PNG)

