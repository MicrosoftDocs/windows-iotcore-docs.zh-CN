---
title: 将应用连接到云
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何将应用连接到云。
keywords: windows iot，云，Azure，Azure IoT 中心
ms.openlocfilehash: 3f7f50ba87e269fa8ac958f80affbd2fd0af5c53
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510881"
---
# <a name="connect-your-app-to-the-cloud"></a>将应用连接到云

本循序渐进指南将允许你以自己熟悉 Windows 10 IoT 核心版、 设置你的设备并创建第一个应用程序连接到 Azure IoT 中心。

## <a name="step-1-prepare-your-device"></a>第 1 步：准备你的设备

您可以找到有关如何准备你的设备上的说明[获取启动页](https://developer.microsoft.com/en-us/windows/iot/getstarted)请确保您[设置 TPM 的设备](../connect-to-cloud/ConnectDeviceToCloud.md)

## <a name="step-2-install-visual-studio-2017-and-tools"></a>步骤 2：安装 Visual Studio 2017 和工具

安装[Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271)。 可以安装任意版本的 Visual Studio 中，包括免费的 Community 版本。

请务必选择**通用 Windows 应用开发工具**，编写 Windows 10 应用所需的组件：

![通用 Windows 应用开发工具](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a>步骤 3:安装 Azure IoT 中心的连接的服务

Azure IoT 中心的 Visual Studio 扩展的连接的服务，可连接并开始在一分钟内使用 Azure IoT 中心进行交互。

可以安装中的扩展插件[VS 库](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)。

## <a name="step-4-create-a-visual-studio-uwp-solution"></a>步骤 4：创建 Visual Studio UWP 解决方案

若要创建的 UWP 解决方案在 Visual Studio 中，在**文件**菜单上，单击**新建**然后**项目**:

![创建新项目](../media/ConnectAppToCloud/new_project_menu.png)

在出现新建项目对话框中选择**空白应用 (通用 Windows) Visual C#** 。 为项目名称 （例如 **MyFirstIoTCoreApp**):

![新建解决方案对话框](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a>使用适用于 Azure IoT 中心的连接服务连接到 Azure IoT 中心

请按照中的说明[连接服务工具](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)以将项目连接到 Azure IoT 中心。 此工具将生成两个函数`SendDeviceToCloudMessageAsync`和`ReceiveCloudToDeviceMessageAsync`，可以在应用中任意位置调用。 根据需要，您可以修改这些函数。  

