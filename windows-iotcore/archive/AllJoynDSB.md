---
title: AllJoyn 设备系统桥概述
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解 AllJoyn 设备系统桥，它可将非 AllJoyn 设备调整到 AllJoyn 生态系统以实现更广泛的互操作性。
keywords: windows iot，AllJoyn
ms.openlocfilehash: 305629867bb85600b314fc34de268c46d90ce6e7
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167927"
---
> [!NOTE]
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题，请在 GitHub 上提出问题，或在下面的评论中留下反馈。

# <a name="alljoyn-device-system-bridge"></a>AllJoyn 设备系统桥

AllJoyn 使开发人员可以灵活地使用多种平台和连接技术来构建 AllJoyn 生态系统的设备。  但是，许多设备制造商在其阵容中都有现有的设备解决方案。 在这些情况下，Microsoft 创建了设备系统桥（DSB）。 DSB 将非 AllJoyn 设备调整到了 AllJoyn 生态系统，以便改编后的设备可与 AllJoyn 互操作，作为其公共语言。 Microsoft DSB 支持家庭自动化系统（如 Zigbee）和 Z-波浪，甚至还支持工业构建自动化系统，例如 BACnet。  此外，可以自定义源代码以支持其他技术

## <a name="how-dsb-works"></a>DSB 的工作原理

DSB 的主要功能是在 AllJoyn 总线上创建设备的虚拟表示形式。 因此，这些设备的本机连接或设备生态系统都将显示并可作为 AllJoyn 设备进行访问。 在下图中，有两个 DSBs，一个用于 Z 波浪，另一个用于 ZigBee 创建两个 Z 波的虚拟表示形式，以及一个 ZigBee 设备在 AllJoyn 总线上的虚拟表示。 在 AllJoyn 站点上，所有设备都可以相互通信。 因为在 AllJoyn 总线上，ZigBee 设备的所有设备现在都可以相互通信。

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

DSB 设计的另一个关键元素是不需要对 AllJoyn 或非 AllJoyn 设备系统进行任何更改。 所有必需的采用都在 DSB 中完成。

如图中所示，没有从 AllJoyn 设备到非 AllJoyn 端的映射。 DSB 的目标是将设备引入到 AllJoyn 生态系统中。 仅启用一种方法可简化开发。 它还降低了 AllJoyn 安全功能被可能不太安全的非 AllJoyn 设备系统削弱的风险。

## <a name="dsb-architecture"></a>DSB 体系结构

Microsoft 建议的 DSB 体系结构由三个主要组件组成：网络访问堆栈、适配器和桥。 下图显示了此体系结构的高级概述。

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a>Bridge
* 将每个内部设备对象表示为 AllJoyn 设备，为每个设备提供单独的总线连接
* 设备在 AllJoyn 总线上动态添加或删除
* 配置管理设备的可见性和安全性
* 为桥和适配器配置接口创建总线附加
* 桥代码对于内部设备类型不可知，任何类型都可重复使用

### <a name="adapter"></a>适配器
* 从非 AllJoyn 网络代表每台设备实例化和管理虚拟设备
* 将设备架构转换为内部设备对象
* 管理网络资源，例如访问密钥、凭据

### <a name="network-access-stack"></a>网络访问堆栈
* 访问特定于非 AllJoyn 网络的权限，例如，Z 波浪堆栈

## <a name="adapter-classes"></a>适配器类

下图显示了开发人员将在 Microsoft DSB 模板中使用的类，以创建需要桥接为 AllJoyn 的本机设备的抽象。 桥将使用适配器类的实例在 "适配器" 列表中为每个设备创建总线附件。
![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)

## <a name="special-handlers"></a>特殊处理程序

AllJoyn 指定多个基本服务和标准接口框架，如 LSF、HAE 或控制面板。 DSB 可以公开具有特殊处理程序的。 DSB 模板的当前版本包含 "LSF" 和 "控制面板" 接口的实现。 开发人员将其代码连接到桥中的 LSF 和控制面板接口的回调函数。

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a>DSB 资源

### <a name="visual-studio-dsb-template"></a>Visual Studio DSB 模板

Visual Studio DSB 模板是 Visual Studio 的扩展，可让你轻松地创建新的 DSB 项目。 该项目将创建所有必要的组件，如 Bridge、用于适配器的 shell 项目和所有解决方案文件，以将 DSB 构建为头或无外设设备。 此 Visual Studio 扩展包含本机和托管的 AllJoyn 设备系统桥接模板。

从以下位置下载 DSB 模板：

* [Visual Studio 2015 的 DSB 模板](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* 还可以通过 "搜索" 字段类型 "DSB" 中 Visual Studio Tools > 扩展和更新 ...-> Online-> 安装[Visual Studio 2017 DSB 模板](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
的 DSB 模板。

将[DSB 对象映射到 alljoyn](AlljoynDsbApiGuide.md)文档介绍用于构建 Alljoyn 系统桥的关键接口和方法。

### <a name="sample-dsbs"></a>示例 DSBs

* [AllJoyn DSB 模拟适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * 本教程介绍如何使用设备系统桥应用将 IoT Core 设备连接到模拟 BACnet 设备。
* [AllJoyn DSB Z 波适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * 本教程介绍如何使用设备系统桥应用将 IoT 核心设备连接到 Z-a 设备。
* [AllJoyn DSB GPIO 适配器教程C++](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * 本教程演示如何使用 AllJoyn 设备系统桥模板来创建一个试验设备 GPIO C++的示例应用。
* [AllJoyn DSB GPIO 适配器教程C#](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * 本教程演示如何使用 "AllJoyn 设备系统桥" 模板来创建一个试验设备 GPIO 的示例托管应用程序。
* [AllJoyn DSB ZigBee 适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * 本教程介绍如何使用设备系统桥应用将 IoT Core 设备连接到 ZigBee 设备。
* [AllJoyn DSB BACnet 适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * 本教程介绍如何使用设备系统桥应用将 IoT Core 设备连接到 BACnet 设备。
* [AllJoyn 教程](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * 本教程介绍如何将 Allseen 联盟开发的 AllJoyn 应用程序作为 Windows 10 应用程序运行。 AllJoyn 允许编写 JavaScript 来创建、监视和控制 AllJoyn 设备。
* [AllJoyn DSB OIC 适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * 本教程介绍如何使用设备系统桥应用将 IoT Core 设备连接到 IoTivity/OIC 设备。
