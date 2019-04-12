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
> <span data-ttu-id="6951c-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="6951c-104">You are viewing archived documentation.</span></span> <span data-ttu-id="6951c-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="6951c-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="6951c-106">如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="6951c-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="using-the-alljoyn-studio-extension"></a><span data-ttu-id="6951c-107">使用 AllJoyn Studio 扩展</span><span class="sxs-lookup"><span data-stu-id="6951c-107">Using the AllJoyn Studio Extension</span></span>

<span data-ttu-id="6951c-108">[AllSeen 联盟](https://allseenalliance.org/)创建 AllJoyn 来使物联网。</span><span class="sxs-lookup"><span data-stu-id="6951c-108">The [AllSeen Alliance](https://allseenalliance.org/) created AllJoyn to empower the Internet of Things.</span></span> <span data-ttu-id="6951c-109">Windows 10 提供了 AllJoyn 本机内置于其平台，从而允许开发人员轻松地利用 AllJoyn 到"IoT-启用"Windows 10 应用。</span><span class="sxs-lookup"><span data-stu-id="6951c-109">Windows 10 has AllJoyn built natively into its platform, allowing developers to easily take advantage of AllJoyn to "IoT-enable" your Windows 10 apps.</span></span> <span data-ttu-id="6951c-110">本文将概述适用于 Windows 10 使用通用 Windows 平台 (UWP) AllJoyn Api 和 Visual Studio 2017 生成应用所需的步骤[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展。</span><span class="sxs-lookup"><span data-stu-id="6951c-110">This article will outline the steps required to build apps for Windows 10 using the Universal Windows Platform (UWP) AllJoyn APIs and the Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension.</span></span>

## <a name="understanding-alljoyn-uwp-app-development"></a><span data-ttu-id="6951c-111">了解 AllJoyn UWP 应用开发</span><span class="sxs-lookup"><span data-stu-id="6951c-111">Understanding AllJoyn UWP App Development</span></span>

<span data-ttu-id="6951c-112">三个主要组件构成 AllJoyn UWP 应用：</span><span class="sxs-lookup"><span data-stu-id="6951c-112">Three major components form AllJoyn UWP apps:</span></span>

1. <span data-ttu-id="6951c-113">应用程序布局和设计 （XAML 或 HTML） 和类组件 (C#，JavaScript 中， C++，或 VB)。</span><span class="sxs-lookup"><span data-stu-id="6951c-113">App layout and design (XAML or HTML) and class components (C#, JavaScript, C++, or VB).</span></span>
2. <span data-ttu-id="6951c-114">AllJoyn 核心 Api 中：AllJoyn Standard Client API (C) 和 Windows.Devices.AllJoyn API (WinRT) 在 Windows 10 SDK 中提供。</span><span class="sxs-lookup"><span data-stu-id="6951c-114">The AllJoyn core APIs: AllJoyn Standard Client API (C) and Windows.Devices.AllJoyn API (WinRT)  available in the Windows 10 SDK.</span></span>
3. <span data-ttu-id="6951c-115">一个或多个 UWP Windows 运行时组件 (从 AllJoyn 接口生成这段代码)。</span><span class="sxs-lookup"><span data-stu-id="6951c-115">One or more UWP Windows Runtime Components (the  generates this code from AllJoyn interfaces).</span></span>

<span data-ttu-id="6951c-116">下图显示了典型的 AllJoyn UWP 项目的体系结构：</span><span class="sxs-lookup"><span data-stu-id="6951c-116">The following diagram shows the architecture of a typical AllJoyn UWP project:</span></span>

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

<span data-ttu-id="6951c-118">启用 AllJoyn 的 UWP 应用可以是任一生产者 （实现和公开的接口，通常的设备），使用者 （使用接口，通常应用），或两者。</span><span class="sxs-lookup"><span data-stu-id="6951c-118">AllJoyn-enabled UWP apps can be either producers  (implement and expose interfaces, typically a device ), consumers (use interfaces, typically apps), or both.</span></span> <span data-ttu-id="6951c-119">使用者和生成者共享相同的起始步骤，仅遵循中的实现详细信息。</span><span class="sxs-lookup"><span data-stu-id="6951c-119">Consumers and producers share the same starting steps, only diverging in the implementation details.</span></span>

## <a name="creating-an-alljoyn-enabled-uwp-app"></a><span data-ttu-id="6951c-120">创建启用 AllJoyn 的 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="6951c-120">Creating an AllJoyn-enabled UWP app</span></span>

<span data-ttu-id="6951c-121">请按照下列步骤来开发适用于 Windows 10 启用 AllJoyn 的 UWP 应用: （本文档后面的详细信息中所述）</span><span class="sxs-lookup"><span data-stu-id="6951c-121">Follow these steps to develop AllJoyn-enabled UWP apps for Windows 10: (explained in detail later in this document)</span></span>

1. <span data-ttu-id="6951c-122">准备生成环境。</span><span class="sxs-lookup"><span data-stu-id="6951c-122">Prepare your build environment.</span></span>
2. <span data-ttu-id="6951c-123">确定哪些 AllJoyn 接口将使用，并获取或创建必需的自检 XML。</span><span class="sxs-lookup"><span data-stu-id="6951c-123">Determine which AllJoyn interfaces will be used, and obtain or create necessary Introspection XML.</span></span>
3. <span data-ttu-id="6951c-124">创建 AllJoyn 的应用程序项目，然后选择用于代码生成的自检 XML 和所需的接口。</span><span class="sxs-lookup"><span data-stu-id="6951c-124">Create an AllJoyn App project then select Introspection XML and desired Interfaces for code generation.</span></span>
4. <span data-ttu-id="6951c-125">在应用中使用从生成的 UWP Windows 运行时组件公开的 Api 实现制造者或 ponsumer 代码。</span><span class="sxs-lookup"><span data-stu-id="6951c-125">Implement producer or ponsumer code in your app using APIs exposed from the generated UWP Windows Runtime Components.</span></span>
5. <span data-ttu-id="6951c-126">生成 UI。</span><span class="sxs-lookup"><span data-stu-id="6951c-126">Build your UI.</span></span>

## <a name="preparing-your-build-environment"></a><span data-ttu-id="6951c-127">准备生成环境</span><span class="sxs-lookup"><span data-stu-id="6951c-127">Preparing your Build Environment</span></span>

<span data-ttu-id="6951c-128">Windows 10 版本和相关的工具包括的所有资源，你将需要编写启用 AllJoyn 的 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="6951c-128">The Windows 10 build and related tools include all of the resources that you'll need to write AllJoyn-enabled UWP apps.</span></span>

<span data-ttu-id="6951c-129">下面是你开始编写代码前的准备工作将需要：</span><span class="sxs-lookup"><span data-stu-id="6951c-129">Here's what you'll need to do before you get started writing code:</span></span>

* <span data-ttu-id="6951c-130">安装[Windows 10](https://www.microsoft.com/windows/) PC 上</span><span class="sxs-lookup"><span data-stu-id="6951c-130">Install [Windows 10](https://www.microsoft.com/windows/) on a PC</span></span>
* <span data-ttu-id="6951c-131">安装[Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) （不使用速成版）</span><span class="sxs-lookup"><span data-stu-id="6951c-131">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (do NOT use an  Express edition)</span></span>
* <span data-ttu-id="6951c-132">下载[AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展从 Visual Studio 库。</span><span class="sxs-lookup"><span data-stu-id="6951c-132">Download the [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension from the Visual Studio Gallery.</span></span> 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a><span data-ttu-id="6951c-133">获取自检 XML AllJoyn 接口</span><span class="sxs-lookup"><span data-stu-id="6951c-133">Obtaining Introspection XML for AllJoyn Interfaces</span></span>

<span data-ttu-id="6951c-134">有三种方法可以获取 AllJoyn 接口定义，将需要启动你的项目：</span><span class="sxs-lookup"><span data-stu-id="6951c-134">There are three ways that you can obtain the AllJoyn interface  definitions that you will need to start your project:</span></span>

1. <span data-ttu-id="6951c-135">从你在运行时的网络上存在 AllJoyn 生成者中提取自检 XML。</span><span class="sxs-lookup"><span data-stu-id="6951c-135">Extract the Introspection XML from AllJoyn Producers present on your network at runtime.</span></span>
2. <span data-ttu-id="6951c-136">获取自检 XML 文档;示例：[照明服务框架 (LSF) 文档](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf)从 AllSeen 联盟。</span><span class="sxs-lookup"><span data-stu-id="6951c-136">Obtain the Introspection XML from documentation ; example: [Lighting Service Framework (LSF) documentation](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) from the AllSeen Alliance.</span></span>
3. <span data-ttu-id="6951c-137">创建你自己的自检 XML 符合 AllJoyn /[D 总线自检](http://dbus.freedesktop.org/doc/dbus-specification.html)格式。</span><span class="sxs-lookup"><span data-stu-id="6951c-137">Create your own Introspection XML that is compliant with the AllJoyn/[D-Bus introspection](http://dbus.freedesktop.org/doc/dbus-specification.html) format.</span></span>

<span data-ttu-id="6951c-138">这篇文章介绍前两种方法-AllJoyn® Studio 以本机方式支持查询网络 AllJoyn 生成者和提取其 XML，以及上传自检 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="6951c-138">This article covers the first two ways - AllJoyn® Studio natively supports querying the network for AllJoyn producers and extracting their XML as well as uploading Introspection XML files.</span></span>  <span data-ttu-id="6951c-139">了解如何创建您自己[此处](AllJoynProducer.md)。</span><span class="sxs-lookup"><span data-stu-id="6951c-139">Learn how to create your own [here](AllJoynProducer.md).</span></span>

<span data-ttu-id="6951c-140">启用 AllJoyn 的 toaster 设备将用作此文章的示例。</span><span class="sxs-lookup"><span data-stu-id="6951c-140">An AllJoyn-enabled toaster device will serve as the example for this post.</span></span> <span data-ttu-id="6951c-141">此 toaster 公开控件启动和停止 toasting 序列、 设置"明暗度"，并通知时烧录 toast。</span><span class="sxs-lookup"><span data-stu-id="6951c-141">This toaster exposes controls for starting and stopping the toasting sequence, setting the "darkness", and notifications when the toast is burnt.</span></span>

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

<span data-ttu-id="6951c-143">Toaster 公开以下 XML:</span><span class="sxs-lookup"><span data-stu-id="6951c-143">The toaster exposes the following XML:</span></span>

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

## <a name="creating-an-alljoyn-project"></a><span data-ttu-id="6951c-144">创建 AllJoyn 项目</span><span class="sxs-lookup"><span data-stu-id="6951c-144">Creating an AllJoyn Project</span></span>

<span data-ttu-id="6951c-145">创建一个项目通常那样的方式：单击`File->New->New Project`开始。</span><span class="sxs-lookup"><span data-stu-id="6951c-145">Create a Project the way you normally would: Click `File->New->New Project` to begin.</span></span>

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

<span data-ttu-id="6951c-147">而不是导航到 Windows 通用模板，选择使用扩展安装在目标语言的"AllJoyn 应用"模板。</span><span class="sxs-lookup"><span data-stu-id="6951c-147">Instead of navigating to a Windows Universal Template, select the "AllJoyn App" Template for your target language which was installed with the Extension.</span></span>  <span data-ttu-id="6951c-148">将项目命名，选择要开始开发的文件位置。</span><span class="sxs-lookup"><span data-stu-id="6951c-148">Name your project and choose a file location to begin developing.</span></span>

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

<span data-ttu-id="6951c-150">立即选择后 AllJoyn 应用模板，Visual Studio 会要求您选择你想要在项目中包含 AllJoyn 接口。</span><span class="sxs-lookup"><span data-stu-id="6951c-150">Immediately after selecting an AllJoyn App Template, Visual Studio will ask you to select the AllJoyn Interfaces you would like to include in your Project.</span></span> 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__<span data-ttu-id="6951c-152">从网络上的设备中提取接口</span><span class="sxs-lookup"><span data-stu-id="6951c-152">Extracting interfaces from a device on the network</span></span>__

<span data-ttu-id="6951c-153">如果找不到你的 AllJoyn 设备或网络上的接口，请按照[本指南](AllJoynTroubleshooting.md)进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="6951c-153">If you cannot find your AllJoyn device or interface on the network, follow [this guide](AllJoynTroubleshooting.md) to troubleshoot.</span></span> 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

<span data-ttu-id="6951c-155">若要查询公开的接口的网络，请在左侧面板中选择"生成者在网络上的"。</span><span class="sxs-lookup"><span data-stu-id="6951c-155">To query your network for exposed interfaces, select the "Producers on the network" in the left-hand panel.</span></span> <span data-ttu-id="6951c-156">这会发现它们支持的接口的网络和列表上任何 AllJoyn 制造者。</span><span class="sxs-lookup"><span data-stu-id="6951c-156">This will find any AllJoyn producer on the network and list the interfaces they support.</span></span>

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

<span data-ttu-id="6951c-158">选择想要在项目中包括的接口。</span><span class="sxs-lookup"><span data-stu-id="6951c-158">Select the interfaces you would like to inlude in your project.</span></span>  <span data-ttu-id="6951c-159">在这种情况下，我们仅使用的 toaster 接口，所以我们选择只是"org.alljoyn.example.Toaster"接口。</span><span class="sxs-lookup"><span data-stu-id="6951c-159">In this case, we are only using the toaster interface, so we select just the "org.alljoyn.example.Toaster" interface.</span></span>

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

<span data-ttu-id="6951c-161">"操作"列说明了对该项目，显示新选择了接口的"添加"挂起的更改。</span><span class="sxs-lookup"><span data-stu-id="6951c-161">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span> <span data-ttu-id="6951c-162">此处我们给出接口"ToasterLibrary"，将触发要应用的"重命名"操作的友好名称。</span><span class="sxs-lookup"><span data-stu-id="6951c-162">Here we have given the interface a friendly name of "ToasterLibrary", which triggers the "Rename" action to be applied.</span></span>

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__<span data-ttu-id="6951c-164">从文件加载 XML</span><span class="sxs-lookup"><span data-stu-id="6951c-164">Loading an XML from a File</span></span>__

<span data-ttu-id="6951c-165">选择任意数量的自检 XML 文件通过"浏览"按钮以查看其包含的接口。</span><span class="sxs-lookup"><span data-stu-id="6951c-165">Choose any number of Introspection XML files via the "Browse" button to see their contained Interface(s).</span></span>

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

<span data-ttu-id="6951c-167">导航到并选择相应的 XML （在这里，我们正在使用 toaster.xml）。</span><span class="sxs-lookup"><span data-stu-id="6951c-167">Navigate to and select the appropriate XML (here, we are using toaster.xml).</span></span>

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

<span data-ttu-id="6951c-169">一次 AllJoyn® Studio 会将 XML 加载，它将分析各种接口并说明中，包含允许您选择你想要支持哪些接口。</span><span class="sxs-lookup"><span data-stu-id="6951c-169">Once AllJoyn® Studio loads the XML, it will parse the various Interfaces and the descriptions contained within, allowing you select which Interfaces you would like to support.</span></span>

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

<span data-ttu-id="6951c-171">"操作"列说明了对该项目，显示新选择了接口的"添加"挂起的更改。</span><span class="sxs-lookup"><span data-stu-id="6951c-171">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span>

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

<span data-ttu-id="6951c-173">此处我们已选择包括"org.alljoyn.example.Toaster"接口，并为它"ToasterLibrary"的友好名称触发要应用的"重命名"操作。</span><span class="sxs-lookup"><span data-stu-id="6951c-173">Here we have chosen to include the "org.alljoyn.example.Toaster" Interface and have given it a friendly name of "ToasterLibrary", triggering the "Rename" action to be applied.</span></span>

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__<span data-ttu-id="6951c-175">添加和删除接口</span><span class="sxs-lookup"><span data-stu-id="6951c-175">Adding and Removing Interfaces</span></span>__

<span data-ttu-id="6951c-176">完成这些步骤后，生成的文件会自动添加到C++Windows 运行时组件与从更高版本和应用程序项目的引用添加的友好名称。</span><span class="sxs-lookup"><span data-stu-id="6951c-176">After completing these steps, the generated files are automatically added to a C++ Windows Runtime Component with the friendly name from above and added as a Reference to the application Project.</span></span>  <span data-ttu-id="6951c-177">但是，根 Namespace 仍是同一个"org.alljoyn.example.Toaster"作为由接口定义。</span><span class="sxs-lookup"><span data-stu-id="6951c-177">However, the Root Namespace is still the same "org.alljoyn.example.Toaster" as defined by the interface.</span></span>  <span data-ttu-id="6951c-178">访问这些组件的任何类需要具有该组件的根命名空间的"using"子句。</span><span class="sxs-lookup"><span data-stu-id="6951c-178">Any classes that access these components need to have a "using" clause for the component's root namespace.</span></span>

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_<span data-ttu-id="6951c-180">提示：生成的生成的组件现在即可从 IntelliSense 中获益。</span><span class="sxs-lookup"><span data-stu-id="6951c-180">TIP: Build the generated components now in order to benefit from IntelliSense.</span></span>_

<span data-ttu-id="6951c-181">创建 AllJoyn 应用解决方案后，你始终可以返回并修改正在使用的接口。</span><span class="sxs-lookup"><span data-stu-id="6951c-181">After you have created your AllJoyn App solution, you can always go back and modify the interfaces you are using.</span></span> <span data-ttu-id="6951c-182">从主菜单栏中，单击"AllJoyn-> 添加/删除接口..."若要启动的界面管理器。</span><span class="sxs-lookup"><span data-stu-id="6951c-182">From the main menu bar, click "AllJoyn->Add/Remove Interfaces..." to launch the Interface manager.</span></span>

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

<span data-ttu-id="6951c-184">在这里，您可以单击"浏览..."若要添加更多的 XML 文件，或取消选择现有的接口。</span><span class="sxs-lookup"><span data-stu-id="6951c-184">From here, you may click "Browse..." to add more XML files, or de-select existing Interface(s).</span></span> <span data-ttu-id="6951c-185">取消选中界面更新其操作"删除"，然后单击确定按钮删除从你的解决方案关联的 Windows 运行时组件。</span><span class="sxs-lookup"><span data-stu-id="6951c-185">De-selecting an Interface updates its Action to "Remove", and clicking the Ok button removes the associated Windows Runtime Component from your solution.</span></span>

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

<span data-ttu-id="6951c-187">查看解决方案资源管理器时，Windows 运行时组件已被删除。</span><span class="sxs-lookup"><span data-stu-id="6951c-187">Looking at the Solution Explorer, the Windows Runtime Component has been removed.</span></span>

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a><span data-ttu-id="6951c-189">后续步骤</span><span class="sxs-lookup"><span data-stu-id="6951c-189">Next Steps</span></span>

<span data-ttu-id="6951c-190">在实现 AllJoyn 功能时，始终为确保包括"Windows.Devices.AllJoyn"命名空间，以及你想要使用的接口中的命名空间。</span><span class="sxs-lookup"><span data-stu-id="6951c-190">When implementing AllJoyn functionality, always be sure to include the "Windows.Devices.AllJoyn" namespace as well as the namespace from the interface you want to use.</span></span>

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__<span data-ttu-id="6951c-192">实现 AllJoyn 使用者</span><span class="sxs-lookup"><span data-stu-id="6951c-192">Implementing an AllJoyn Consumer</span></span>__

<span data-ttu-id="6951c-193">适用于接口生成的代码包含用于查找，然后控制生成者的观察程序和使用者类。</span><span class="sxs-lookup"><span data-stu-id="6951c-193">The code generated for the interfaces contains a watcher and consumer class used to find and then control a producer.</span></span> <span data-ttu-id="6951c-194">通过创建新 AllJoynBusAttachment 实现观察程序，初始化观察程序中的使用该 AllJoynBusAttachment，注册，以便观察程序查找制造者 （"Added"事件），然后启动观察程序。</span><span class="sxs-lookup"><span data-stu-id="6951c-194">Implement the watcher by creating a new AllJoynBusAttachment, initialize the watcher with that AllJoynBusAttachment, register for the watcher finding a producer (the "Added" event), then start the watcher.</span></span>

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

<span data-ttu-id="6951c-196">ToasterWatcher_Added 事件，将触发观察程序查找生成者。</span><span class="sxs-lookup"><span data-stu-id="6951c-196">The ToasterWatcher_Added event triggers whenever the watcher finds a producer.</span></span>  <span data-ttu-id="6951c-197">使用此事件注册一个使用者。</span><span class="sxs-lookup"><span data-stu-id="6951c-197">Use this event to register a consumer.</span></span> <span data-ttu-id="6951c-198">请注意，Visual Studio 将生成通过快速操作的必要外壳方法。</span><span class="sxs-lookup"><span data-stu-id="6951c-198">Note that Visual Studio will generate the necessary shell method through the Quick Actions.</span></span>

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

<span data-ttu-id="6951c-200">生成该方法将生成下面的命令行程序代码：</span><span class="sxs-lookup"><span data-stu-id="6951c-200">Generating the method produces the following shell code:</span></span>

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

<span data-ttu-id="6951c-202">使用正确的逻辑的命令行程序代码中填充使注册使用者。</span><span class="sxs-lookup"><span data-stu-id="6951c-202">Filling in the shell code with the correct logic enables registering the consumer.</span></span>

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

<span data-ttu-id="6951c-204">请注意，每次观察程序发现生成者时，将触发此事件。</span><span class="sxs-lookup"><span data-stu-id="6951c-204">Note that this event triggers every time the watcher discovers a producer.</span></span>  <span data-ttu-id="6951c-205">如果你想要查找多个生成者，因为会有一个使用者为每个生成者保持使用者的数据的结构。</span><span class="sxs-lookup"><span data-stu-id="6951c-205">If you expect to find multiple producers, keep a data structure of the consumer as there will be one consumer for each producer.</span></span>

<span data-ttu-id="6951c-206">注册各种信号将发出制造者-属性已更改的事件信号是直接成员的使用者类，但其他信号 （如，开始使用前要生成这些事件的命令行程序代码的快速操作） 是信号类的成员。</span><span class="sxs-lookup"><span data-stu-id="6951c-206">Register events for the various signals the producer will emit – property changed signals are direct members of the consumer class, but other signals are members of the Signals class (just as before, use the Quick Actions to generate the shell code for these events).</span></span>

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

<span data-ttu-id="6951c-208">使用使用者对象来读取和写入属性，以及调用方法。</span><span class="sxs-lookup"><span data-stu-id="6951c-208">Use the consumer object to read and write properties as well as call methods.</span></span>

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a><span data-ttu-id="6951c-210">实现 AllJoyn 生成者</span><span class="sxs-lookup"><span data-stu-id="6951c-210">Implementing an AllJoyn Producer</span></span>

__<span data-ttu-id="6951c-211">实现服务</span><span class="sxs-lookup"><span data-stu-id="6951c-211">Implementing the Service</span></span>__

<span data-ttu-id="6951c-212">生成者实现公开其接口的服务。</span><span class="sxs-lookup"><span data-stu-id="6951c-212">Producers implement a service that expose their interfaces.</span></span>  <span data-ttu-id="6951c-213">若要实现生成者，首先创建用于其服务的类。</span><span class="sxs-lookup"><span data-stu-id="6951c-213">To implement a producer, first create a class for its service.</span></span>

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

<span data-ttu-id="6951c-215">将接口的命名空间添加到"using"语句，则继承的服务生成的 shell 接口并使用快速操作需要实现的类。</span><span class="sxs-lookup"><span data-stu-id="6951c-215">Add the namespace for the interface to the "using" statements, then inherit the shell interface generated for the service and use the Quick Action to implement the class.</span></span>

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

<span data-ttu-id="6951c-217">在这里，快速操作将填写必需的组件。</span><span class="sxs-lookup"><span data-stu-id="6951c-217">From here, the Quick Action will fill in the necessary components.</span></span>

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

<span data-ttu-id="6951c-219">代码的所有必要部分现可正常工作，但您仍需要实现为每个方法和属性调用的实际逻辑。</span><span class="sxs-lookup"><span data-stu-id="6951c-219">All the necessary parts of the code are ready to function, but you still need to implement the actual logic for each method and property call.</span></span>

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

<span data-ttu-id="6951c-221">我们采用 SetDarknessLevelAsync 作为示例，使用任务创建的成功结果。</span><span class="sxs-lookup"><span data-stu-id="6951c-221">Taking the SetDarknessLevelAsync as an example, we use a task to create a success result.</span></span>  <span data-ttu-id="6951c-222">如果失败，返回 ToasterSetDarknessLevelResult.CreateFailureResult()。</span><span class="sxs-lookup"><span data-stu-id="6951c-222">In case of failure, return ToasterSetDarknessLevelResult.CreateFailureResult().</span></span>

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

<span data-ttu-id="6951c-224">实现方法和属性调用，以完成该服务的其余部分。</span><span class="sxs-lookup"><span data-stu-id="6951c-224">Implement the rest of the method and property calls to finish the service.</span></span>

__<span data-ttu-id="6951c-225">实现制造者</span><span class="sxs-lookup"><span data-stu-id="6951c-225">Implementing the Producer</span></span>__

<span data-ttu-id="6951c-226">创建生成者非常简单 – 创建新 AllJoynBusAttachment，初始化该 AllJoynBusAttachment 与生成者，初始化新创建的服务的创建者，然后启动生成者。</span><span class="sxs-lookup"><span data-stu-id="6951c-226">Creating the producer is straightforward – create a new AllJoynBusAttachment, initialize a producer with that AllJoynBusAttachment, initialize the newly created service for the producer, then start the producer.</span></span>

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

<span data-ttu-id="6951c-228">由于该服务包含大部分逻辑，剩下要实现的主要功能是将属性更改的信号和非状态事件的离散信号发送。</span><span class="sxs-lookup"><span data-stu-id="6951c-228">Since the service contains the majority of the logic, the main functionality left to implement is to send the signals for property changes and discrete signals for non-state events.</span></span>  <span data-ttu-id="6951c-229">实现这些可根据需要通过方法调用。</span><span class="sxs-lookup"><span data-stu-id="6951c-229">Implement these as necessary through method calls.</span></span>

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__<span data-ttu-id="6951c-231">详细信息</span><span class="sxs-lookup"><span data-stu-id="6951c-231">More Information</span></span>__

<span data-ttu-id="6951c-232">如果你已正确完成所有本文档中的说明，已准备好开始编写 AllJoyn 代码应用程序中。</span><span class="sxs-lookup"><span data-stu-id="6951c-232">If you've completed all of the instructions in this document correctly, you are ready to start writing AllJoyn code in your app.</span></span>

<span data-ttu-id="6951c-233">有关参考，请查看用于在 Microsoft 示例 github AllJoyn 通用 Windows 应用示例[AllJoyn 生产者](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)并[AllJoyn 使用者](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)。</span><span class="sxs-lookup"><span data-stu-id="6951c-233">For reference, please look to the AllJoyn Universal Windows Apps samples on the Microsoft Sample GitHub for [AllJoyn Producers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) and [AllJoyn Consumers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span></span>

<span data-ttu-id="6951c-234">有关如何创建 AllJoyn 应用的详细演练，请观看 AllJoyn 会话 623:</span><span class="sxs-lookup"><span data-stu-id="6951c-234">For a detailed walkthrough of how to create an AllJoyn app, please watch the AllJoyn session 623:</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

<span data-ttu-id="6951c-235">请注意，除非它们已经启用环回异常，例如通过 Windows 策略禁用 AllJoyn 同一台计算机上的两个 UWP 应用程序之间的通信正在直接通过 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="6951c-235">Note that AllJoyn communication between two UWP apps on the same machine is disabled by Windows policy unless they have enabled a loopback exception, such as when being directly deployed from Visual Studio.</span></span>  <span data-ttu-id="6951c-236">启用环回例外的详细说明，请参阅[此处](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6951c-236">For detailed instructions on enabling loopback exemption, see [here](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>



