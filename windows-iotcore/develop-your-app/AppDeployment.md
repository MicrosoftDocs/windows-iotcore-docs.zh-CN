---
title: 使用 Visual Studio 部署应用
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Visual Studio 远程调试功能部署应用。
keywords: windows iot、 visual studio、 应用部署、 远程调试
ms.openlocfilehash: 218cbf43a1b63a517091b80315f327954b3eae5a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510853"
---
# <a name="deploying-an-app-with-visual-studio"></a>使用 Visual Studio 部署应用

使用 Visual Studio 部署和调试应用程序很简单。 我们将使用**远程调试**功能将应用部署到本地连接的 Windows 10 IoT Core 设备。 

> [!NOTE]
> 部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。

> [!NOTE]
> 为了使用远程调试，IoT 核心版设备必须首先连接到与开发电脑相同的本地网络。  
>请参阅[连接到的设备](../connect-your-device/SetupWiFi.md)说明。

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a>部署C#应用到 Windows 10 IoT Core 设备 
___

1. 应用程序在 Visual Studio 中打开后，在工具栏下拉列表中设置体系结构。 如果您正在构建的 Minnowboard 最大值，则选择`x86`。 如果您正在构建为 Raspberry Pi 2、 Raspberry Pi 3 或 Dragonboard，选择`ARM`。

2. 接下来，在 Visual Studio 工具栏中，单击`Local Machine`下拉列表中，然后选择`Remote Machine`。

![在 Visual Studio 中的远程计算机](../media/AppDeployment/cs-remote-machine-debugging.png)

3. 此时，Visual Studio 将显示“远程连接”对话框。 如果以前使用过[PowerShell](../connect-your-device/PowerShell.md)若要设置你的设备的唯一名称，您可以在此处输入 (在此示例中，我们使用**我的设备**)。 否则，使用 Windows IoT 核心版设备的 IP 地址。

4. 输入设备名称/IP 后选择`Universal (Unencrypted Protocol)`身份验证模式，然后单击**选择**。 

![通用身份验证模式](../media/AppDeployment/cs-remote-connections.png)

可通过导航到项目属性（在解决方案资源管理器中选择“属性”）并在左侧选择 `Debug` 选项卡来验证或修改这些值：

![“调试”选项卡](../media/AppDeployment/cs-debug-project-properties.png)

5. 现在我们已准备好部署。 只需按 F5 (或选择调试\|开始调试) 若要开始调试我们的应用程序。 你应该会看到你的设备的屏幕上显示应用。

6. 部署完成后，可设置断点、查看变量值等。若要停止应用程序按停止调试按钮 (或选择调试\|停止调试)。

7. 已成功部署和调试 UWP 应用程序，创建的发布版本的后更改 Visual Studio 工具栏配置下拉列表从`Debug`到`Release`。  现在可以生成，并将应用部署到你的设备，通过选择生成\|重新生成解决方案和生成\|部署解决方案。

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a>部署C++应用到 Windows 10 IoT Core 设备

1. 应用程序在 Visual Studio 中打开后，在工具栏下拉列表中设置体系结构。 如果您正在构建的 Minnowboard 最大值，则选择`86`。 如果你要针对 Raspberry Pi 2 或 3 进行生成，请选择 `ARM`。

2. 接下来，在 Visual Studio 工具栏中，单击`Local Machine`下拉列表中，然后选择 `Remote Machine`

![在 Visual Studio 中的本地计算机](../media/AppDeployment/cpp-remote-machine-debugging.png)

3. 接下来，在“解决方案资源管理器”窗格中，右键单击该项目。 选择“属性”。 

![在 Visual Studio 中的属性](../media/AppDeployment/cpp-project-properties.png)

4. 在“配置属性”->“调试”下，修改以下字段：

    * **计算机名**：如果以前曾使用 PowerShell 设置设备的唯一名称，可在此处输入该名称（在此示例中，我们使用的是 **my-device**）。 否则，使用 Windows IoT 核心版设备的 IP 地址。
    * **身份验证模式**：设置为“通用(未加密协议)”
    
![通用身份验证模式](../media/AppDeployment/cpp-debug-project-properties.png)

5. 现在我们已准备好部署。 只需按 F5 (或选择调试\|开始调试) 若要开始调试我们的应用程序。 应该可以看到应用出现在 Windows IoT 核心版设备屏幕上。

6. 部署完成后，可设置断点、查看变量值等。若要停止应用，请按停止调试按钮 (或选择调试\|停止调试)。

7. 具有成功部署并调试 UWP 应用程序中，创建一个发布版本-更改 Visual Studio 工具栏配置下拉列表从`Debug`到`Release`。  现在可以生成，并将应用部署到你的设备，通过选择生成\|重新生成解决方案和生成\|部署解决方案。

