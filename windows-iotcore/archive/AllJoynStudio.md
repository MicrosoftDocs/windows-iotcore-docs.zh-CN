---
title: AllJoyn Studio
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何使用通用 Windows 平台 (UWP) AllJoyn Api 和 Visual Studio 2017 创建 AllJoyn UWP 应用。
keywords: windows iot, AllJoyn
ms.openlocfilehash: 5326873218c0126b918679308e3a8e08cdddf84c
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168298"
---
> [!NOTE]
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题, 请在 GitHub 上提出问题, 或在下面的评论中留下反馈。

# <a name="using-the-alljoyn-studio-extension"></a>使用 AllJoyn Studio 扩展

[AllSeen 联盟](https://allseenalliance.org/)创建了 AllJoyn 来帮助物联网。 Windows 10 将 AllJoyn 内置于其平台上, 使开发人员能够轻松利用 AllJoyn 到 Windows 10 应用的 "IoT 启用"。 本文将概述使用通用 Windows 平台 (UWP) AllJoyn Api 和 Visual Studio 2017 [Alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展生成适用于 Windows 10 的应用程序所需的步骤。

## <a name="understanding-alljoyn-uwp-app-development"></a>了解 AllJoyn UWP 应用开发

以下三个主要组件构成了 AllJoyn UWP 应用:

1. 应用布局和设计 (XAML 或 HTML) 和类组件 (C#、JavaScript、 C++或 VB)。
2. AllJoyn 核心 Api:Windows 10 SDK 中提供了 AllJoyn 标准客户端 API (C) 和 Windows. AllJoyn API (WinRT)。
3. 一个或多个 UWP Windows 运行时组件 (从 AllJoyn 接口生成此代码)。

下图显示了典型的 AllJoyn UWP 项目的体系结构:

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

启用了 AllJoyn 的 UWP 应用可以是发生器 (实现和公开接口, 通常是设备)、使用者 (使用接口, 通常为应用), 或同时使用两者。 使用者和制造者共享相同的开始步骤, 仅在实现细节中进行拆分。

## <a name="creating-an-alljoyn-enabled-uwp-app"></a>创建启用了 AllJoyn 的 UWP 应用

按照以下步骤来开发适用于 Windows 10 的启用了 AllJoyn 的 UWP 应用: (本文档稍后将详细说明)

1. 准备生成环境。
2. 确定将使用哪些 AllJoyn 接口, 并获取或创建必要的自检 XML。
3. 创建一个 AllJoyn 应用项目, 然后选择 "自检 XML" 和所需的接口以生成代码。
4. 使用从生成的 UWP Windows 运行时组件公开的 Api 在应用中实现制造者或 ponsumer 代码。
5. 构建用户界面。

## <a name="preparing-your-build-environment"></a>准备生成环境

Windows 10 内部版本和相关工具包括编写启用了 AllJoyn 的 UWP 应用所需的所有资源。

下面是在开始编写代码之前需要执行的操作:

* 在电脑上安装[Windows 10](https://www.microsoft.com/windows/)
* 安装[Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (请勿使用 Express edition)
* 从 Visual Studio 库下载[AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展。 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a>获取用于 AllJoyn 接口的自检 XML

可以通过三种方式获取用于启动项目的 AllJoyn 接口定义:

1. 在运行时从网络中的 AllJoyn 制造商提取自检 XML。
2. 从文档中获取自检 XML;实例AllSeen 联盟中的[照明服务框架 (LSF) 文档](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf)。
3. 创建你自己的自检 XML, 该 XML 符合 AllJoyn/[D-总线自检](http://dbus.freedesktop.org/doc/dbus-specification.html)格式。

本文介绍了前两种方法: AllJoyn® Studio 以本机方式支持查询用于 AllJoyn 创建者的网络并提取其 XML, 并上传自检 XML 文件。  了解如何在[此处](AllJoynProducer.md)创建自己的。

启用了 AllJoyn 的 toaster 设备将充当此文章的示例。 此 toaster 公开用于启动和停止烤序列的控件、设置 "明暗度" 以及在 toast 焦时发出通知。

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

Toaster 公开了以下 XML:

``` xml
<node name="/toaster">
  <interface name="org.alljoyn.example.Toaster">
    <annotation name="org.alljoyn.Bus.Secure" value="true"/>
    <description language="en">Example interface for controlling a toaster appliance</description>
    <description language="fr">Interface Exemple de commande d'un appareil de grille-pain</description>
    <property name="Version" type="q" access="read">
      <description>Interface version</description>
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="const"/>
    </property>
    <signal name="ToastBurnt" sessioncast="true">
      <description language="en">Toast is burnt</description>
      <description language="fr">Toast est brûlé</description>
    </signal>
    <method name="StartToasting">
      <description language="en">Start toasting</description>
      <description language="fr">Lancer grillage</description>
    </method>
    <method name="StopToasting">
      <description language="en">Stop toasting</description>
      <description language="fr">Arrêtez de grillage</description>
    </method>
    <property name="DarknessLevel" type="y" access="readwrite">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">Toasting darkness level</description>
      <description language="fr">Grillage niveau de l'obscurité</description>
    </property>
  </interface>
</node>
```

## <a name="creating-an-alljoyn-project"></a>创建 AllJoyn 项目

按通常的方式创建项目:单击`File->New->New Project` "开始"。

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

选择与扩展一起安装的目标语言的 "AllJoyn 应用" 模板, 而不是导航到 Windows 通用模板。  命名项目, 然后选择要开始开发的文件位置。

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

选择 AllJoyn 应用模板之后, Visual Studio 会要求你选择要包括在项目中的 AllJoyn 接口。 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__从网络上的设备提取接口__

如果在网络上找不到 AllJoyn 设备或接口, 请按照[本指南](AllJoynTroubleshooting.md)进行故障排除。 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

若要查询网络中是否有公开的接口, 请在左侧面板中选择 "网络上的创建者"。 这会在网络上找到任何 AllJoyn 制造者, 并列出它们支持的接口。

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

选择要在项目中包括的接口。  在这种情况下, 我们仅使用 toaster 接口, 因此只选择 "Toaster" 接口。

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

"操作" 列描述了对项目的挂起的更改, 并为新选择的接口显示 "添加"。 这里, 我们为接口提供了 "ToasterLibrary" 的友好名称, 这会触发要应用的 "重命名" 操作。

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__从文件加载 XML__

通过 "浏览" 按钮选择任意数量的自检 XML 文件, 以查看其包含的接口。

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

导航到并选择相应的 XML (此处使用的是 toaster)。

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

在 AllJoyn® Studio 加载 XML 后, 它将分析中包含的各种接口和说明, 使您可以选择要支持的接口。

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

"操作" 列描述了对项目的挂起的更改, 并为新选择的接口显示 "添加"。

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

在这里, 我们选择了包含 "Toaster" 接口, 并为其提供了一个友好名称 "ToasterLibrary", 触发要应用的 "重命名" 操作。

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__添加和移除接口__

完成这些步骤后, 生成的文件会自动添加到具有C++上述友好名称的 Windows 运行时组件中, 并作为对应用程序项目的引用添加。  但是, 根命名空间仍与接口定义的 "Toaster" 相同。  访问这些组件的任何类都需要为组件的根命名空间使用 "using" 子句。

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_提示立即生成生成的组件, 以便从 IntelliSense 中获益。_

创建了 AllJoyn 应用解决方案后, 你始终可以返回并修改所使用的接口。 在主菜单栏中, 单击 "AllJoyn-> 添加/删除接口 ..."启动接口管理器。

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

在此处, 你可以单击 "浏览 ..."添加更多 XML 文件或取消选择现有接口。 取消选择某个接口会将其操作更新为 "删除", 单击 "确定" 按钮可从解决方案中删除关联的 Windows 运行时组件。

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

查看解决方案资源管理器, Windows 运行时组件已删除。

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a>后续步骤

实现 AllJoyn 功能时, 请始终确保包含 "Windows. AllJoyn" 命名空间以及要使用的接口中的命名空间。

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__实现 AllJoyn 使用者__

为接口生成的代码包含用于查找并控制制造者的观察程序和使用者类。 通过创建新的 AllJoynBusAttachment 来实现观察程序, 使用该 AllJoynBusAttachment 初始化观察程序, 注册观察程序找到一个生成者 ("添加" 事件), 然后启动观察程序。

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

每当观察程序找到生成者时, ToasterWatcher_Added 事件就会触发。  使用此事件来注册使用者。 请注意, Visual Studio 将通过快速操作生成必要的 shell 方法。

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

生成方法会生成以下 shell 代码:

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

使用正确的逻辑填充 shell 代码允许注册使用者。

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

请注意, 每次观察程序发现一个生成者时, 都会触发此事件。  如果希望找到多个创建者, 请保留使用者的数据结构, 因为每个制造者都有一个使用者。

为制造者发出的各种信号注册事件–属性更改信号是使用者类的直接成员, 而其他信号是信号类的成员 (正如之前一样, 请使用快速操作为这些事件生成 shell 代码)。

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

使用使用者对象可以读取和写入属性, 还可以调用方法。

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a>实现 AllJoyn 制造者

__实现服务__

发生器实现公开其接口的服务。  若要实现发生器, 请首先为其服务创建一个类。

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

将接口的命名空间添加到 "using" 语句, 然后继承为服务生成的 shell 接口, 并使用 Quick 操作来实现类。

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

在这里, 快速操作会填写必要的组件。

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

代码的所有必需部分都可以正常工作, 但仍需实现每个方法和属性调用的实际逻辑。

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

采用 SetDarknessLevelAsync 作为示例, 我们使用任务来创建成功的结果。  如果失败, 则返回 ToasterSetDarknessLevelResult. CreateFailureResult ()。

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

实现方法和属性调用的其余部分以完成服务。

__实现制造者__

创建制造者非常简单–创建一个新的 AllJoynBusAttachment, 使用该 AllJoynBusAttachment 初始化一个创建者, 为制造者初始化新创建的服务, 然后启动创建者。

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

由于服务包含大部分逻辑, 要实现的主要功能是为非状态事件发送属性更改和离散信号的信号。  根据需要通过方法调用实现这些方法。

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__详细信息__

如果已正确完成本文档中的所有说明, 则可以开始在应用程序中编写 AllJoyn 代码。

有关参考, 请参阅 Microsoft 示例 GitHub 上的 AllJoyn 通用 Windows 应用示例, 获取[Alljoyn 制造](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)者和[alljoyn 使用者](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)。

有关如何创建 AllJoyn 应用的详细演练, 请观看 AllJoyn 会话 623:

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

请注意, 在同一台计算机上的两个 UWP 应用之间进行的 AllJoyn 通信将被 Windows 策略禁用, 除非它们启用了环回异常, 如从 Visual Studio 直接部署时。  有关启用环回豁免的详细说明, 请参阅[此处](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)。



