---
title: 将你的应用连接到云
ms.date: 08/28/2017
ms.topic: article
description: 将你的应用程序连接到云。 准备好你的设备，安装 VS and 连接的服务用于 Azure IoT 中心，创建 UWP 解决方案，然后连接到 Azure IoT 中心。
keywords: windows iot，cloud，Azure，Azure IoT 中心
ms.openlocfilehash: b35869201e44abd1c272ba36226174abd493d869
ms.sourcegitcommit: 05278f1a522ed498900ce15b98bdd4389b5dde55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88081342"
---
# <a name="connect-your-app-to-the-cloud"></a>将你的应用连接到云

此循序渐进指南将允许你熟悉 Windows 10 IoT Core、设置设备并创建连接到 Azure IoT 中心的第一个应用程序。

## <a name="step-1-prepare-your-device"></a>步骤1：准备设备

你可以在 "[入门" 页](https://developer.microsoft.com/en-us/windows/iot/getstarted)上找到有关如何准备设备的说明，请确保[预配设备的 TPM](../connect-to-cloud/ConnectDeviceToCloud.md)

## <a name="step-2-install-visual-studio-2017-and-tools"></a>步骤2：安装 Visual Studio 2017 和工具

安装[Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271)。 可以安装任意版本的 Visual Studio，包括免费的 Community 版。

请确保选择**通用 Windows 应用开发工具**，即编写应用所需的组件 Windows 10：

![通用 Windows 应用开发工具](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a>步骤3：安装 Azure IoT 中心的连接的服务

使用 Azure IoT 中心 Visual Studio 扩展的连接的服务，可以在不到一分钟的时间内连接和开始与 Azure IoT 中心交互。

你可以从[VS 库](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)中安装该扩展。

## <a name="step-4-create-a-visual-studio-uwp-solution"></a>步骤4：创建 Visual Studio UWP 解决方案

若要在 Visual Studio 中创建 UWP 解决方案，请在 "**文件**" 菜单上单击 "**新建**"，然后单击 "**项目**"：

![创建新项目](../media/ConnectAppToCloud/new_project_menu.png)

在出现的 "新建项目" 对话框中，选择 "**空白应用 (通用 Windows) Visual c #**"。 为项目指定名称 (e.x。 **MyFirstIoTCoreApp**) ：

![新建解决方案对话框](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a>使用 Azure IoT 中心的连接的服务连接到 Azure IoT 中心

按照[连接的服务工具](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)中的说明将项目连接到 Azure IoT 中心。 该工具将生成两个函数， `SendDeviceToCloudMessageAsync` 并且 `ReceiveCloudToDeviceMessageAsync` 可以在应用中的任意位置调用。 您可以根据需要修改这些函数。  

