---
title: AllJoyn 概述
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解有关 AllJoyn、 一种常见协议为 IoT 设备和它如何实现其他扩展和使用 Windows IoT 的功能。
keywords: windows iot AllJoyn
ms.openlocfilehash: 6b558680d479c71b6b8a22d34d03b04e5cbdbd76
ms.sourcegitcommit: 0f46b7b5c15906a6c82b847ffcd9f4d2674f9fd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226827"
---
> [!NOTE]
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题，备选方法，是面向 AllJoyn 的应用层 IoT 协议是[打开连接 Foundation](https://openconnectivity.org)。 OCF 规范的标准实现 Iotivity-可以找到 Windows 支持 Iotivity[此处](https://wiki.iotivity.org/windows)。

# <a name="alljoyn"></a>AllJoyn

AllJoyn 支持物联网。 AllJoyn 定义了设备和应用程序互相发现和通信的通用协议，而不考虑传输技术、平台或制造商。  AllJoyn 是由 [AllSeen 联盟](https://allseenalliance.org/)推动的一种开源标准，该组织是一个致力于支持物联网中的数十亿设备、服务和应用程序进行互操作的跨行业联合会。

Microsoft 在 2014 年加入了 AllSeen 联盟，并在 Windows 10 中将 Alliance 添加为核心组件。 使用内置的 [AllJoyn API](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx)，开发人员可以自由编写可在任何 Windows 10 设备上运行的支持 AllJoyn 的应用程序，包括 PC、平板电脑、手机、Xbox 以及使用 Windows IoT 核心版的设备。 除了对 AllJoyn 的平台支持，Microsoft 还发布了 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)，它是一款通过将代码生成与现成应用程序模板结合来加快 AllJoyn 开发的 Visual Studio 扩展。 AllJoyn Studio 使开发人员无需进行繁琐的设置和配置即可从 AllJoyn 的强大功能中受益。

对 AllJoyn 感到兴奋？ 请查看[此](AllJoynStudio.md)博客文章来了解如何开始在 Windows 上使用 AllJoyn。


## <a name="developer-resources-and-tools"></a>开发人员资源和工具

**设备系统网桥**

AllJoyn [设备系统网桥](AllJoynDSB.md)支持非 AllJoyn 设备使用 AllJoyn 作为其公共语言与 AllJoyn 生态系统进行交互。

功能：
* 为适配器公开的每个非 AllJoyn 设备创建虚拟设备
* 从适配器设备自动生成运行时接口
* 支持 LSF，控制面板基本服务，可扩展添加更多服务
* 适用于桌面 UI 应用程序和 Windows IoT 启动任务的通用应用模板（C#、C++）
* 以开源方式提供

有关更多详细信息，请参阅[设备系统网桥页面](AllJoynDSB.md)。


**AllJoyn Studio**

[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 是由 Microsoft 开发的 Visual Studio 扩展，用于通过将代码生成和 WinRT API 与自动项目管理和现成应用程序模板结合来加快 AllJoyn® 开发。 它使开发人员无需进行繁琐的设置和配置即可从 AllJoyn 的强大功能中受益。

功能：
* 通用应用模板（C#、JavaScript、C++、Visual Basic）
* 自动引用管理和项目配置
* 在解决方案中添加/删除接口
* 通过 AllJoyn® 菜单轻松访问项目管理
* 从自检 XML 文件加载接口
* 从 network1 上的创建器发现接口

AllJoyn Studio 可以通过安装 Visual Studio 工具-> 扩展和更新... -> 联机-> 的"搜索"字段中键入"AllJoyn"

提供了有关如何使用 AllJoyn Studio 的更多详细信息[此处](AllJoynStudio.md)。

**IoT 资源管理器为 AllJoyn （AllJoyn 的资源管理器） 的**

AllJoyn 的 IoT 资源管理器（以前称为 AllJoyn 资源管理器）是 Windows 通用应用程序，用于与本地邻近网络上的 AllJoyn 设备进行交互。 开发人员可以列出所有可用的 AllJoyn 设备、检查其接口和对象结构，以及接收信号、设置和获取属性并调用方法。

* [AllJoyn 的 IoT 资源管理器应用商店应用](https://www.microsoft.com/store/apps/9nblggh6gpxl)：这是官方应用商店应用所在的位置。
* [AllJoyn 资源管理器 1.0.1.11（早期版本）](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip)：此 zip 包含要旁加载到开发人员的计算机上的 AllJoyn 资源管理器 AppX 捆绑包。 这是针对 AllJoyn 应用程序的以前发布版本的 IoT 资源管理器。
* [AllJoyn 资源管理器设置指南](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf)：此 pdf 包含有关如何部署 AllJoyn 资源管理器的文档。
* [AllJoyn 资源管理器用户指南](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf)：此 pdf 包含有关如何使用 AllJoyn 资源管理器的文档。


### <a name="additional-resources"></a>其他资源

* [使用 AllJoyn Studio 扩展](AllJoynStudio.md)
* [AllJoyn 创建器和编写 AllJoyn 自检](AllJoynProducer.md)
* [Windows 10 的 AllJoyn 疑难解答](AllJoynTroubleshooting.md)

**视频**

* [//build 2015 AllJoyn 技术研讨会](https://channel9.msdn.com/Events/Build/2015/2-623)
* [WinHEC 2015 AllJoyn 技术研讨会](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

**示例**

* [AllJoyn 创建器](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [AllJoyn 使用器](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [AllJoyn UWP 示例 (MSDN)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

**参考**

* [Windows 10 中的 AllJoyn API (MSDN)](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [AllJoyn 体系结构详细信息（Allseen 联盟）](https://allseenalliance.org/developers/learn/)
* [AllJoyn 开发人员资源（Allseen 联盟）](https://allseenalliance.org/developers/develop/)
* [AllJoyn C API 参考手册（Allseen 联盟）](https://allseenalliance.org/docs/api/c/index.html)

