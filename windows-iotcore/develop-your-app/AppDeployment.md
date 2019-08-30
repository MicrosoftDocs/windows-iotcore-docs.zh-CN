---
title: 使用 Visual Studio 部署应用
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Visual Studio 远程调试功能部署应用。
keywords: windows iot, visual studio, 应用部署, 远程调试
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533354"
---
# <a name="deploying-an-app-with-visual-studio"></a>使用 Visual Studio 部署应用

使用 Visual Studio 部署和调试应用程序很简单。 我们将使用**远程调试**功能将应用程序部署到本地连接的 Windows 10 IoT Core 设备。 

> [!NOTE]
> 在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。

> [!NOTE]
> 若要使用远程调试, IoT Core 设备必须首先连接到与开发计算机相同的本地网络, 并在网络上允许 UDP/TCP 通信。 如果有疑问, 请检查是否存在允许的网络流量。 有关说明, 请参阅[连接到设备](../connect-your-device/SetupWiFi.md)。

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a>将应用部署到 Windows 10 IoT Core 设备

1. 应用程序在 Visual Studio 中打开后，在工具栏下拉列表中设置体系结构。 如果要生成 Minnowboard Max, 请选择`x86`。 如果要生成 Raspberry Pi 2、Raspberry Pi 3 或 Dragonboard, 请选择`ARM`。

2. 接下来, 在 Visual Studio 工具栏中, 单击`Local Machine`下拉列表并选择。 `Remote Machine`

![Visual Studio 中的远程计算机](../media/AppDeployment/remote-vs.png)

3. 此时，Visual Studio 将显示“远程连接”对话框。 如果你以前使用[PowerShell](../connect-your-device/PowerShell.md)为你的设备设置唯一名称, 则可以在此处输入该名称 (在此示例中, 我们使用的是**设备**)。 否则，使用 Windows IoT 核心版设备的 IP 地址。

4. 输入设备名称/ip 后, 选择`Universal (Unencrypted Protocol)` "身份验证模式", 然后单击 "**选择**"。 

![通用身份验证模式](../media/AppDeployment/remote-connections.png)

可通过导航到项目属性（在解决方案资源管理器中选择“属性”）并在左侧选择 `Debug` 选项卡来验证或修改这些值：

![“调试”选项卡](../media/AppDeployment/debug-tab.png)

5. 现在我们已准备好部署。 只需按 F5（或依次选择“调试”|“启动调试”）即可开始调试应用。 你应看到该应用程序出现在设备屏幕上。

6. 部署完成后，可设置断点、查看变量值等。若要停止应用, 请按 "停止调试" 按钮 (或选择 "调试" |停止调试)。

7. 成功部署和调试 UWP 应用程序后, 创建发布版本-将 Visual Studio 工具栏配置下拉列表从`Debug`更改为。 `Release`  现在，可通过依次选择“生成”|“重新生成解决方案”和“生成”|“部署解决方案”，生成应用并将其部署到设备。
