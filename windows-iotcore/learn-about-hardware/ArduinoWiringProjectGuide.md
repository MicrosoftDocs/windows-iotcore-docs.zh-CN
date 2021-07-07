---
title: Arduino 布线 Project 指南
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows IoT 核心创建、设置和部署 Arduino 布线项目。
keywords: windows iot，Arduino，Arduino 布线，闪电性能，Visual Studio
ms.openlocfilehash: cbfa71b1264623ef0af399e3dd4b4b61fc4cb799
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228873"
---
# <a name="arduino-wiring-project-guide"></a>Arduino 布线 Project 指南

> [!IMPORTANT]
> Windows 10 IoT 团队不再主动维护 Arduino。

本指南将指导你使用 Windows IoT 核心来创建、设置和部署 Arduino 接线图项目。

Arduino 接线图使用 Windows IoT 闪电 DMAP 驱动程序，使用熟悉、易于使用的 Arduino 布线 API：使用直接内存映射的驱动程序，可提供显著的[性能速度](../develop-your-app/LightningPerformance.md)。 可以将 Arduino 草图和库复制 & 粘贴到 IoT 核心 Arduino 布线项目，并在支持的 IoT 核心设备上运行它们，包括 Raspberry Pi2、3和 Minnowboard Max！ 有关详细信息，请参阅本页的 "开发" 部分。

## <a name="install-the-microsoft-iot-templates"></a>安装 Microsoft IoT 模板

> [!NOTE]
> 下载 VS 2015 以访问 Arduino 接线模板-VS 2017 和更高版本上不支持这些模板。

我们提供了一个 Visual Studio 扩展，该扩展将自动为 Arduino 接线项目和其他 Microsoft IoT 项目类型安装 VS 模板。

- 转到[Windows IoT Core Project 模板扩展 "页](https://go.microsoft.com/fwlink/?linkid=847472)，从 Visual Studio 库下载该扩展！
- 安装扩展，并重新启动 Visual Studio 如果已打开）

## <a name="change-the-default-controller-driver"></a>更改默认控制器驱动程序

你将需要运行直接内存映射驱动程序来编写 Arduino 布线解决方案！ 有关说明，请参阅 [闪电安装指南](../develop-your-app/LightningSetup.md) ！

## <a name="develop"></a>开发
完成 " [示例" 页](https://developer.microsoft.com/en-us/windows/iot/samples)上的 "布线" 示例之一，或生成自己的项目！ 我们使用 Arduino 布线编写的任何示例将如下所示： [Blinky (布线) ](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring)。 Blinky 是 IoT 项目的 cononical "Hello World" 项目，是第一个项目的入门教程！

### <a name="create-a-new-project"></a>创建新 Project
1. 打开 Visual Studio。

2. 选择 "文件-> >" Project .。。

3. 从显示的对话框中，选择：  
Visual C++ > Windows-> Windows iot core-> iot core Windows Arduino 布线应用程序  
 (可能会显示为)   
Visual C++ > Windows iot 核心-> 用于 Windows IoT 核心的 Arduino 布线应用程序


![应用创建](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a>移植

已仔细实现 Arduino 布线 API，使您能够将库和草图复制/粘贴到 Arduino 布线项目。 然而，在某些情况下，可能需要对您的草图或库做出少量的修改。 我们已经创建了一个易于遵循的 [Arduino 布线指南](ArduinoWiringPortingGuide.md) ，以涵盖这些潜在问题。

## <a name="build-and-deploy"></a>生成和部署

- 在 Visual Studio 中，请确保选择 "远程计算机" 作为部署目标。
- 此外，请确保将体系结构设置为与正在运行项目的板匹配。 对于 Raspberry Pi 2 或3，选择 "ARM"，为 "Minnowboard Max" 选择 "x86"。

![远程计算机](../media/ArduinoWiring/wiringapp_remotemachine.png)

- 打开在 Visual Studio 的 "调试" 上下文菜单中找到的解决方案属性。

![解决方案属性](../media/ArduinoWiring/wiringapp_properties.png)

- 找到设备的 IP 地址或计算机名称。 使用 Windows 10 IoT 核心版仪表板应用程序或将设备挂接到监视器。
- 默认情况下，键入计算机名称 (minwinpc) 或远程计算机的 IP 地址设置为 "计算机名" 字段。 如果将设备重命名为 "minwinpc" 以外的其他内容，请在登录框中改用该名称。
- 确保 Authentican 类型为：通用 (未加密协议) 

![解决方案属性1](../media/ArduinoWiring/wiringapp_properties2.png)

- 按 F5 在设备上生成并部署项目。
