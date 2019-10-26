---
title: Arduino 接线项目指南
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows IoT Core 创建、设置和部署 Arduino 接线图项目。
keywords: windows iot，Arduino，Arduino 布线，闪电性能，Visual Studio
ms.openlocfilehash: 17dc35174cc6aca7074183875e69202fc36dd9bc
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918121"
---
# <a name="arduino-wiring-project-guide"></a>Arduino 接线项目指南

> [!IMPORTANT]
> Windows 10 IoT 团队不再主动维护 Arduino。

本指南将指导你使用 Windows IoT Core 创建、设置和部署 Arduino 接线图项目。

Arduino 接线图使用 Windows IoT 闪电 DMAP 驱动程序，利用熟悉的、易于使用的 Arduino 布线 API：使用直接内存映射的驱动程序，提供显著的[性能速度](../develop-your-app/LightningPerformance.md)。 可以将 Arduino 草图和库复制 & 粘贴到 IoT 核心 Arduino 布线项目，并在支持的 IoT 核心设备上运行它们，包括 Raspberry Pi2、3和 Minnowboard Max！ 有关详细信息，请参阅本页的 "开发" 部分。

## <a name="install-the-microsoft-iot-templates"></a>安装 Microsoft IoT 模板

> [!NOTE]
> 下载 VS 2015 以访问 Arduino 接线模板-VS 2017 和更高版本上不支持这些模板。

我们提供了一个 Visual Studio 扩展，该扩展将为 Arduino 接线项目以及其他 Microsoft IoT 项目类型自动安装 VS 模板。 

- 转到 [Windows IoT 核心版项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472)来从 Visual Studio 库下载该扩展！
- 安装扩展，并重新启动 Visual Studio （如果已打开）

## <a name="change-the-default-controller-driver"></a>更改默认控制器驱动程序

你将需要运行直接内存映射驱动程序来编写 Arduino 接线解决方案！ 有关说明，请参考 [Lightning 设置指南](../develop-your-app/LightningSetup.md)！

## <a name="develop"></a>开发
完成 "[示例" 页](https://developer.microsoft.com/en-us/windows/iot/samples)上的 "布线" 示例之一，或生成自己的项目！ 将列出我们创建的任何使用 Arduino 接线编写的示例，如下所示： [Blinky（接线）](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring)。 适用于 IoT 项目的经典“Hello World”项目 Blinky 是适合作为你的第一个项目的良好起点！

### <a name="create-a-new-project"></a>创建一个新项目
1. 打开 Visual Studio。

2. 选择 "文件-> 新建-> 项目 ..."

3. 从显示的对话框中，选择：  
视觉C++ > Windows > Windows iot core-> 适用于 Windows iot 核心的 Arduino 配应用程序  
（可能显示为）  
Visual C++ -> Windows iot core-适用于 Windows iot 核心 > Arduino 接线应用程序 


![应用创建](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a>移植

已仔细实现 Arduino 接线 API，以便你可以将库和草图复制/粘贴到 Arduino 接线项目中。 尽管如此，在某些情况下，你可能需要对草图或库进行轻微修改。 我们创建了一个易于遵循的 [Arduino 接线移植指南](ArduinoWiringPortingGuide.md)来涵盖这些潜在问题。

## <a name="build-and-deploy"></a>生成和部署

- 在 Visual Studio 中，确保选择“远程计算机”作为你的部署目标。
- 此外，请确保将体系结构设置为与正在运行项目的板匹配。 对于 Raspberry Pi 2 或3，选择 "ARM"，为 "Minnowboard Max" 选择 "x86"。

![远程计算机](../media/ArduinoWiring/wiringapp_remotemachine.png)

- 在 Visual Studio 中打开在“调试”上下文菜单中找到的解决方案属性。

![解决方案属性](../media/ArduinoWiring/wiringapp_properties.png)

- 找到设备的 IP 地址或计算机名称。 使用 Windows 10 IoT 核心仪表板应用程序或将设备挂接到监视器。
- 在“计算机名称”字段中键入远程计算机的计算机名称（默认为 minwinpc）或 IP 地址。 如果你已将设备命名为“minwinpc”以外的某个名称，请在登录框中改用该名称。
- 确保 Authentican 类型为：通用（未加密的协议）

![解决方案属性](../media/ArduinoWiring/wiringapp_properties2.png)

- 按 F5 在设备上生成并部署项目。
