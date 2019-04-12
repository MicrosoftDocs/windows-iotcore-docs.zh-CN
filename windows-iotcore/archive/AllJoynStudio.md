---
title: AllJoyn Studio
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解有关如何创建使用通用 Windows 平台 (UWP) AllJoyn Api 和 Visual Studio 2017 的 AllJoyn UWP 应用。
keywords: windows iot AllJoyn
ms.openlocfilehash: 5326873218c0126b918679308e3a8e08cdddf84c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510974"
---
> [!NOTE]
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。

# <a name="using-the-alljoyn-studio-extension"></a>使用 AllJoyn Studio 扩展

[AllSeen 联盟](https://allseenalliance.org/)创建 AllJoyn 来使物联网。 Windows 10 提供了 AllJoyn 本机内置于其平台，从而允许开发人员轻松地利用 AllJoyn 到"IoT-启用"Windows 10 应用。 本文将概述适用于 Windows 10 使用通用 Windows 平台 (UWP) AllJoyn Api 和 Visual Studio 2017 生成应用所需的步骤[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展。

## <a name="understanding-alljoyn-uwp-app-development"></a>了解 AllJoyn UWP 应用开发

三个主要组件构成 AllJoyn UWP 应用：

1. 应用程序布局和设计 （XAML 或 HTML） 和类组件 (C#，JavaScript 中， C++，或 VB)。
2. AllJoyn 核心 Api 中：AllJoyn Standard Client API (C) 和 Windows.Devices.AllJoyn API (WinRT) 在 Windows 10 SDK 中提供。
3. 一个或多个 UWP Windows 运行时组件 (从 AllJoyn 接口生成这段代码)。

下图显示了典型的 AllJoyn UWP 项目的体系结构：

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

启用 AllJoyn 的 UWP 应用可以是任一生产者 （实现和公开的接口，通常的设备），使用者 （使用接口，通常应用），或两者。 使用者和生成者共享相同的起始步骤，仅遵循中的实现详细信息。

## <a name="creating-an-alljoyn-enabled-uwp-app"></a>创建启用 AllJoyn 的 UWP 应用

请按照下列步骤来开发适用于 Windows 10 启用 AllJoyn 的 UWP 应用: （本文档后面的详细信息中所述）

1. 准备生成环境。
2. 确定哪些 AllJoyn 接口将使用，并获取或创建必需的自检 XML。
3. 创建 AllJoyn 的应用程序项目，然后选择用于代码生成的自检 XML 和所需的接口。
4. 在应用中使用从生成的 UWP Windows 运行时组件公开的 Api 实现制造者或 ponsumer 代码。
5. 生成 UI。

## <a name="preparing-your-build-environment"></a>准备生成环境

Windows 10 版本和相关的工具包括的所有资源，你将需要编写启用 AllJoyn 的 UWP 应用。

下面是你开始编写代码前的准备工作将需要：

* 安装[Windows 10](https://www.microsoft.com/windows/) PC 上
* 安装[Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) （不使用速成版）
* 下载[AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展从 Visual Studio 库。 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a>获取自检 XML AllJoyn 接口

有三种方法可以获取 AllJoyn 接口定义，将需要启动你的项目：

1. 从你在运行时的网络上存在 AllJoyn 生成者中提取自检 XML。
2. 获取自检 XML 文档;示例：[照明服务框架 (LSF) 文档](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf)从 AllSeen 联盟。
3. 创建你自己的自检 XML 符合 AllJoyn /[D 总线自检](http://dbus.freedesktop.org/doc/dbus-specification.html)格式。

这篇文章介绍前两种方法-AllJoyn® Studio 以本机方式支持查询网络 AllJoyn 生成者和提取其 XML，以及上传自检 XML 文件。  了解如何创建您自己[此处](AllJoynProducer.md)。

启用 AllJoyn 的 toaster 设备将用作此文章的示例。 此 toaster 公开控件启动和停止 toasting 序列、 设置"明暗度"，并通知时烧录 toast。

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

Toaster 公开以下 XML:

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

创建一个项目通常那样的方式：单击`File->New->New Project`开始。

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

而不是导航到 Windows 通用模板，选择使用扩展安装在目标语言的"AllJoyn 应用"模板。  将项目命名，选择要开始开发的文件位置。

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

立即选择后 AllJoyn 应用模板，Visual Studio 会要求您选择你想要在项目中包含 AllJoyn 接口。 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__从网络上的设备中提取接口__

如果找不到你的 AllJoyn 设备或网络上的接口，请按照[本指南](AllJoynTroubleshooting.md)进行故障排除。 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

若要查询公开的接口的网络，请在左侧面板中选择"生成者在网络上的"。 这会发现它们支持的接口的网络和列表上任何 AllJoyn 制造者。

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

选择想要在项目中包括的接口。  在这种情况下，我们仅使用的 toaster 接口，所以我们选择只是"org.alljoyn.example.Toaster"接口。

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

"操作"列说明了对该项目，显示新选择了接口的"添加"挂起的更改。 此处我们给出接口"ToasterLibrary"，将触发要应用的"重命名"操作的友好名称。

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__从文件加载 XML__

选择任意数量的自检 XML 文件通过"浏览"按钮以查看其包含的接口。

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

导航到并选择相应的 XML （在这里，我们正在使用 toaster.xml）。

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

一次 AllJoyn® Studio 会将 XML 加载，它将分析各种接口并说明中，包含允许您选择你想要支持哪些接口。

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

"操作"列说明了对该项目，显示新选择了接口的"添加"挂起的更改。

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

此处我们已选择包括"org.alljoyn.example.Toaster"接口，并为它"ToasterLibrary"的友好名称触发要应用的"重命名"操作。

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__添加和删除接口__

完成这些步骤后，生成的文件会自动添加到C++Windows 运行时组件与从更高版本和应用程序项目的引用添加的友好名称。  但是，根 Namespace 仍是同一个"org.alljoyn.example.Toaster"作为由接口定义。  访问这些组件的任何类需要具有该组件的根命名空间的"using"子句。

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_提示：生成的生成的组件现在即可从 IntelliSense 中获益。_

创建 AllJoyn 应用解决方案后，你始终可以返回并修改正在使用的接口。 从主菜单栏中，单击"AllJoyn-> 添加/删除接口..."若要启动的界面管理器。

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

在这里，您可以单击"浏览..."若要添加更多的 XML 文件，或取消选择现有的接口。 取消选中界面更新其操作"删除"，然后单击确定按钮删除从你的解决方案关联的 Windows 运行时组件。

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

查看解决方案资源管理器时，Windows 运行时组件已被删除。

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a>后续步骤

在实现 AllJoyn 功能时，始终为确保包括"Windows.Devices.AllJoyn"命名空间，以及你想要使用的接口中的命名空间。

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__实现 AllJoyn 使用者__

适用于接口生成的代码包含用于查找，然后控制生成者的观察程序和使用者类。 通过创建新 AllJoynBusAttachment 实现观察程序，初始化观察程序中的使用该 AllJoynBusAttachment，注册，以便观察程序查找制造者 （"Added"事件），然后启动观察程序。

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

ToasterWatcher_Added 事件，将触发观察程序查找生成者。  使用此事件注册一个使用者。 请注意，Visual Studio 将生成通过快速操作的必要外壳方法。

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

生成该方法将生成下面的命令行程序代码：

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

使用正确的逻辑的命令行程序代码中填充使注册使用者。

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

请注意，每次观察程序发现生成者时，将触发此事件。  如果你想要查找多个生成者，因为会有一个使用者为每个生成者保持使用者的数据的结构。

注册各种信号将发出制造者-属性已更改的事件信号是直接成员的使用者类，但其他信号 （如，开始使用前要生成这些事件的命令行程序代码的快速操作） 是信号类的成员。

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

使用使用者对象来读取和写入属性，以及调用方法。

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a>实现 AllJoyn 生成者

__实现服务__

生成者实现公开其接口的服务。  若要实现生成者，首先创建用于其服务的类。

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

将接口的命名空间添加到"using"语句，则继承的服务生成的 shell 接口并使用快速操作需要实现的类。

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

在这里，快速操作将填写必需的组件。

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

代码的所有必要部分现可正常工作，但您仍需要实现为每个方法和属性调用的实际逻辑。

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

我们采用 SetDarknessLevelAsync 作为示例，使用任务创建的成功结果。  如果失败，返回 ToasterSetDarknessLevelResult.CreateFailureResult()。

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

实现方法和属性调用，以完成该服务的其余部分。

__实现制造者__

创建生成者非常简单 – 创建新 AllJoynBusAttachment，初始化该 AllJoynBusAttachment 与生成者，初始化新创建的服务的创建者，然后启动生成者。

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

由于该服务包含大部分逻辑，剩下要实现的主要功能是将属性更改的信号和非状态事件的离散信号发送。  实现这些可根据需要通过方法调用。

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__详细信息__

如果你已正确完成所有本文档中的说明，已准备好开始编写 AllJoyn 代码应用程序中。

有关参考，请查看用于在 Microsoft 示例 github AllJoyn 通用 Windows 应用示例[AllJoyn 生产者](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)并[AllJoyn 使用者](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)。

有关如何创建 AllJoyn 应用的详细演练，请观看 AllJoyn 会话 623:

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

请注意，除非它们已经启用环回异常，例如通过 Windows 策略禁用 AllJoyn 同一台计算机上的两个 UWP 应用程序之间的通信正在直接通过 Visual Studio 部署。  启用环回例外的详细说明，请参阅[此处](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)。



