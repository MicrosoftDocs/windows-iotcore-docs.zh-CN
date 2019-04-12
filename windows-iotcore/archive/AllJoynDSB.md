---
title: AllJoyn 设备系统桥接概述
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解有关 AllJoyn 设备系统桥接，调整到 AllJoyn 生态系统的更广泛的互操作性的非 AllJoyn 设备的信息。
keywords: windows iot AllJoyn
ms.openlocfilehash: 305629867bb85600b314fc34de268c46d90ce6e7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510660"
---
> [!NOTE]
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。

# <a name="alljoyn-device-system-bridge"></a>AllJoyn 设备系统桥接

AllJoyn 提供开发人员可以灵活地使用各种平台和连接技术来构建 AllJoyn 生态系统的设备。  但是，许多设备制造商在其项目组合中具有现有设备的解决方案。 对于这些情况下，Microsoft 创建设备系统桥接 (DSB)。 DSB 调整非 AllJoyn AllJoyn 生态系统的设备，以便调整的设备可以与 AllJoyn 作为其公共语言进行互操作。 Microsoft DSB 支持家庭自动化系统，例如 Zigbee 和 Z 兴起，甚至可以支持工业生成自动化系统，例如 BACnet。  此外，源代码是可自定义以支持其他技术。

## <a name="how-dsb-works"></a>DSB 的工作原理

DSB 的关键功能是 AllJoyn 总线上创建的设备的虚拟表示。 因此这些设备，无论其本机连接或设备生态系统是什么，将出现，并且可作为 AllJoyn 的设备。 在下两个 DSBs 图，一个 Z 波形的一个用于 ZigBee 创建两个 Z 兴起和一个 ZigBee 设备的虚拟表示 AllJoyn 总线上。 与此 AllJoyn 上的所有设备站点可以相互通信。 因为 AllJoyn 总线上所有的 Z 批和 ZigBee 设备他们现在可以相互通信以及。

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

DSB 设计的另一个关键元素是它将需要对 AllJoyn 或非 AllJoyn 设备系统的任何更改。 所有必要的采用都在 DSB 中完成。

如图还显示了，没有从 AllJoyn 设备映射到非 AllJoyn 端。 DSB 旨在将设备纳入 AllJoyn 生态系统。 启用只有一种方式简化了开发。 它还可降低风险该 AllJoyn 可能较不安全的非 AllJoyn 设备系统变得削弱的安全功能。

## <a name="dsb-architecture"></a>DSB 体系结构

Microsoft 建议 DSB 体系结构包括三个主要组件，网络访问堆栈、 适配器和桥。 下图显示了此体系结构的高级别概述。

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a>Bridge
* 每个内部设备对象表示为 AllJoyn 设备，为每个设备的单独总线附件
* 设备会动态添加或删除从 AllJoyn 总线
* 配置管理设备的可见性和安全性
* 创建桥和适配器配置界面的总线附件
* 桥接代码是不可知的内部设备类型和任何类型的可重用

### <a name="adapter"></a>适配器
* 实例化和管理代表每个设备从非 AllJoyn 网络虚拟设备
* 设备架构转换为内部设备对象
* 管理网络资源，例如访问密钥，凭据

### <a name="network-access-stack"></a>网络访问堆栈
* 访问特定于非 AllJoyn 网络，例如 Z 批堆栈

## <a name="adapter-classes"></a>适配器类

下图显示在 Microsoft DSB 模板来创建需要进行桥接到 AllJoyn 的本机设备的抽象，开发人员将使用的类。 桥将使用适配器类的实例创建的每个设备的总线附件 Adapter.devices 列表中。
![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)

## <a name="special-handlers"></a>特殊的处理程序

AllJoyn 指定多个基本服务和标准接口框架，如 LSF、 HAE 或控制面板。 DSB 可以公开具有特殊的处理程序。 当前版本的 DSB 模板包含 LSF 和控制面板接口的实现。 开发人员将其代码连接到在桥中的 LSF 和控制面板接口的回调函数。

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a>DSB 资源

### <a name="visual-studio-dsb-template"></a>Visual Studio DSB 模板

Visual Studio DSB 模板是可以轻松地创建新 DSB 项目的 Visual Studio 的扩展。 项目将创建所有必要组件，如桥用于适配器和所有解决方案文件，以生成作为主或无外设设备 DSB shell 项目。 此 Visual Studio 扩展包含的本机和托管 AllJoyn 设备系统桥的模板。

从以下位置下载 DSB 模板：

* [用于 Visual Studio 2015 DSB 模板](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* [Visual Studio 2017 的 DSB 模板](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_DSB 模板也可以通过安装 Visual Studio 工具-> 扩展和更新...-> 联机-> 的"搜索"字段中键入"DSB"。_

[映射到 AllJoyn DSB 对象](AlljoynDsbApiGuide.md)文档介绍了关键的接口和方法用于生成 Alljoyn 系统桥接。

### <a name="sample-dsbs"></a>示例 DSBs

* [AllJoyn DSB 模拟适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * 本教程演示如何使用设备系统 Bridge 应用 IoT Core 设备模拟 BACnet 设备的连接。
* [AllJoyn DSB Z 批适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * 本教程演示如何使用设备系统 Bridge 应用将 IoT Core 设备连接到 Z 波形设备。
* [AllJoyn DSB GPIO 适配器教程C++](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * 本教程演示如何使用 AllJoyn 设备系统桥模板创建一个示例C++执行设备 GPIO 的应用。
* [AllJoyn DSB GPIO 适配器教程C#](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * 本教程演示如何使用 AllJoyn 设备系统桥模板来创建执行设备 GPIO 示例托管的应用。
* [AllJoyn DSB ZigBee 适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * 本教程演示如何使用设备系统 Bridge 应用将 IoT Core 设备连接到 ZigBee 设备。
* [AllJoyn DSB BACnet 适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * 本教程演示如何使用设备系统 Bridge 应用将 IoT Core 设备连接到 BACnet 设备。
* [AllJoyn.JS 教程](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * 本教程演示如何运行 AllJoyn.JS 由 Allseen 联盟为 Windows 10 应用程序开发的应用程序。 AllJoyn.JS 可以编写 JavaScript 将创建、 监视和控制 AllJoyn 的设备。
* [AllJoyn DSB OIC 适配器教程和示例](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * 本教程演示如何使用设备系统 Bridge 应用将 IoT Core 设备连接到 IoTivity/OIC 设备。
