---
title: 使用应用程序部署Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用远程调试功能Visual Studio应用。
keywords: windows iot， visual studio， 应用部署， 远程调试
ms.openlocfilehash: 57132a4c249e21d319d481077851ea8655b2740f
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229133"
---
# <a name="deploying-an-app-with-visual-studio"></a>使用应用程序部署Visual Studio

部署和调试应用程序非常简单，Visual Studio。 我们将使用远程 **调试** 功能将应用部署到本地连接Windows 10 IoT 核心版设备。 

> [!NOTE]
> 在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。

> [!NOTE]
> 若要使用远程调试，必须先将 IoT 核心设备连接到与开发电脑相同的本地网络，并且应在网络中允许 UDP/TCP 通信。 如果有疑问，请咨询 IT 部门，了解允许的网络流量。 有关 [说明，请参阅连接到](../connect-your-device/SetupWiFi.md) 设备。

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a>将应用部署到 Windows 10 IoT 核心版 设备

1. 在应用程序打开Visual Studio，在工具栏下拉列表中设置体系结构。 如果要为 Minnowboard Max 生成 ，请选择 `x86` 。 如果要为 Raspberry Pi 2、Raspberry Pi 3 或 Dragonboard 生成，请选择 `ARM` 。

2. 接下来，在Visual Studio工具栏中，单击 `Local Machine` 下拉列表并选择 `Remote Machine` 。

![远程计算机Visual Studio](../media/AppDeployment/remote-vs.png)

3. 此时，Visual Studio"远程 **连接"** 对话框。 如果以前使用 [PowerShell](../connect-your-device/PowerShell.md) 为设备设置唯一名称，可以在此处输入该名称 (本示例中，我们将使用我的 **设备**) 。 否则，请使用 IoT 核心Windows IP 地址。

4. 输入设备名称/IP 后，选择" `Universal (Unencrypted Protocol)` 身份验证模式"，然后单击"选择 **"。** 

![通用身份验证模式](../media/AppDeployment/remote-connections.png)

可以通过导航到项目属性来验证或修改这些值， (**选择"** 属性解决方案资源管理器) 并选择左侧 `Debug` 的选项卡：

![“调试”选项卡](../media/AppDeployment/debug-tab.png)

5. 现在，我们已准备好进行部署。 只需按 F5 (或选择"调试|启动调试) 开始调试应用。 应会看到应用在设备的屏幕上显示。

6. 部署后，可以设置断点、查看变量值等。若要停止应用，请按"停止调试"按钮 (或选择"调试|停止调试) 。

7. 成功部署和调试 UWP 应用程序后，创建发布版本 - 将Visual Studio工具栏配置下拉列表从 `Debug` 更改为 `Release` 。  现在，可以通过选择"生成应用"来生成应用，|重新生成解决方案和生成|部署解决方案。
