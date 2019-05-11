---
title: 使用 Visual Studio 部署应用
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Visual Studio 远程调试功能部署应用。
keywords: windows iot、 visual studio、 应用部署、 远程调试
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533354"
---
# <a name="deploying-an-app-with-visual-studio"></a>使用 Visual Studio 部署应用

使用 Visual Studio 部署和调试应用程序很简单。 我们将使用**远程调试**功能将应用部署到本地连接的 Windows 10 IoT Core 设备。 

> [!NOTE]
> 部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。

> [!NOTE]
> 若要使用远程调试，必须首先将 IoT Core 设备连接到进行开发的电脑与位于同一本地网络，应在网络上允许 UDP/TCP 通信。 如果在有任何疑问，请与您的 IT 上允许的网络流量。 请参阅[连接到的设备](../connect-your-device/SetupWiFi.md)有关的说明。

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a>将应用部署到 Windows 10 IoT Core 设备

1. 应用程序在 Visual Studio 中打开后，在工具栏下拉列表中设置体系结构。 如果您正在构建的 Minnowboard 最大，则选择`x86`。 如果您正在构建为 Raspberry Pi 2、 Raspberry Pi 3 或 Dragonboard，选择`ARM`。

2. 接下来，在 Visual Studio 工具栏中，单击`Local Machine`下拉列表中，然后选择`Remote Machine`。

![在 Visual Studio 中的远程计算机](../media/AppDeployment/remote-vs.png)

3. 此时，Visual Studio 将显示“远程连接”对话框。 如果以前使用过[PowerShell](../connect-your-device/PowerShell.md)若要设置你的设备的唯一名称，您可以在此处输入 (在此示例中，我们使用**我的设备**)。 否则，使用 Windows IoT 核心版设备的 IP 地址。

4. 输入设备名称/IP 后选择`Universal (Unencrypted Protocol)`身份验证模式，然后单击**选择**。 

![通用身份验证模式](../media/AppDeployment/remote-connections.png)

可通过导航到项目属性（在解决方案资源管理器中选择“属性”）并在左侧选择 `Debug` 选项卡来验证或修改这些值：

![“调试”选项卡](../media/AppDeployment/debug-tab.png)

5. 现在我们已准备好部署。 只需按 F5（或依次选择“调试”|“启动调试”）即可开始调试应用。 你应该会看到你的设备的屏幕上显示应用。

6. 部署完成后，可设置断点、查看变量值等。若要停止应用程序按停止调试按钮 (或选择调试 |停止调试）。

7. 已成功部署和调试 UWP 应用程序，创建的发布版本的后更改 Visual Studio 工具栏配置下拉列表从`Debug`到`Release`。  现在，可通过依次选择“生成”|“重新生成解决方案”和“生成”|“部署解决方案”，生成应用并将其部署到设备。
