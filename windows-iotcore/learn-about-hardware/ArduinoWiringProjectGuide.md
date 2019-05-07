---
title: Arduino 接线项目指南
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何创建、 设置和使用 Windows IoT Core Arduino 绑定项目的部署。
keywords: windows iot，Arduino，Arduino 配线、 闪电般的性能，Visual Studio
ms.openlocfilehash: 7c5e51efd20de014af4533587fbe6f210140b793
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744812"
---
# <a name="arduino-wiring-project-guide"></a>Arduino 接线项目指南

> [!IMPORTANT]
> Windows 10 IoT 团队正在不再主动维护 arduino 开发。

本指南将引导完成创建、 设置和使用 Windows IoT Core Arduino 绑定项目的部署。

Arduino 绑定项目利用熟悉的、 易于使用 Arduino 连接 API 与 Windows IoT 闪电 DMAP 驱动程序： 使用直接内存映射提供重要的驱动程序[性能速度](../develop-your-app/LightningPerformance.md)。 可以复制和粘贴到 IoT Core Arduino 绑定项目的 Arduino 草图和库并运行其支持 IoT Core 上设备，包括 Raspberry Pi2，3 和 Minnowboard 最大值 ！ 请参阅此页获取详细信息开发部分。

## <a name="install-the-microsoft-iot-templates"></a>安装 Microsoft IoT 模板

> [!NOTE]
> 下载 VS 2015 访问 Arduino 绑定模板-这些模板是支持 VS 2017 及更高版本不受距离限制。

我们提供了一个 Visual Studio 扩展，该扩展将为 Arduino 接线项目以及其他 Microsoft IoT 项目类型自动安装 VS 模板。 

- 转到 [Windows IoT 核心版项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472)来从 Visual Studio 库下载该扩展！
- 安装扩展，然后重新启动 Visual Studio，如果之前已打开

## <a name="change-the-default-controller-driver"></a>更改默认控制器驱动程序

你将需要运行直接内存映射驱动程序来编写 Arduino 接线解决方案！ 有关说明，请参考 [Lightning 设置指南](../develop-your-app/LightningSetup.md)！

## <a name="develop"></a>开发
在完成其中一个"绑定"示例[示例页](https://developer.microsoft.com/en-us/windows/iot/samples)，或生成你自己的项目 ！ 将列出我们创建的任何使用 Arduino 接线编写的示例，如下所示：[Blinky（接线）](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring)。 适用于 IoT 项目的经典“Hello World”项目 Blinky 是适合作为你的第一个项目的良好起点！

### <a name="create-a-new-project"></a>创建一个新项目
1. 打开 Visual Studio。

2. 选择文件-> 新建-> 项目...

3. 从显示的对话框中，选择：  
Visual C++ -> Windows-> Windows IoT Core-> Arduino 绑定适用于 Windows IoT Core 的应用程序  
(可能会改为显示为)  
Visual C++ -> Windows IoT Core-> Arduino 绑定适用于 Windows IoT Core 的应用程序 


![创建应用](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a>移植

已仔细实现 Arduino 接线 API，以便你可以将库和草图复制/粘贴到 Arduino 接线项目中。 尽管如此，在某些情况下，你可能需要对草图或库进行轻微修改。 我们创建了一个易于遵循的 [Arduino 接线移植指南](ArduinoWiringPortingGuide.md)来涵盖这些潜在问题。

## <a name="build-and-deploy"></a>生成和部署

- 在 Visual Studio 中，确保选择“远程计算机”作为你的部署目标。
- 此外，请确保该体系结构设置为匹配的看板运行你的项目。 Raspberry Pi 2 或 3 中，选择"ARM"和对于 Minnowboard 最大值，请选择"x86"。

![远程计算机](../media/ArduinoWiring/wiringapp_remotemachine.png)

- 在 Visual Studio 中打开在“调试”上下文菜单中找到的解决方案属性。

![解决方案属性](../media/ArduinoWiring/wiringapp_properties.png)

- 找到你的设备的 IP 地址或计算机名称。 使用 Windows 10 IoT 核心版仪表板应用程序，或者将挂接到你的设备到监视器。
- 在“计算机名称”字段中键入远程计算机的计算机名称（默认为 minwinpc）或 IP 地址。 如果你已将设备命名为“minwinpc”以外的某个名称，请在登录框中改用该名称。
- 请确保 Authentican 类型是：通用 （未加密的协议）

![解决方案属性](../media/ArduinoWiring/wiringapp_properties2.png)

- 按 F5 以生成和部署你的设备上的项目。
