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
> <span data-ttu-id="1caf7-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="1caf7-104">You are viewing archived documentation.</span></span> <span data-ttu-id="1caf7-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="1caf7-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="1caf7-106">如有问题, 请在 GitHub 上提出问题, 或在下面的评论中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="1caf7-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="using-the-alljoyn-studio-extension"></a><span data-ttu-id="1caf7-107">使用 AllJoyn Studio 扩展</span><span class="sxs-lookup"><span data-stu-id="1caf7-107">Using the AllJoyn Studio Extension</span></span>

<span data-ttu-id="1caf7-108">[AllSeen 联盟](https://allseenalliance.org/)创建了 AllJoyn 来帮助物联网。</span><span class="sxs-lookup"><span data-stu-id="1caf7-108">The [AllSeen Alliance](https://allseenalliance.org/) created AllJoyn to empower the Internet of Things.</span></span> <span data-ttu-id="1caf7-109">Windows 10 将 AllJoyn 内置于其平台上, 使开发人员能够轻松利用 AllJoyn 到 Windows 10 应用的 "IoT 启用"。</span><span class="sxs-lookup"><span data-stu-id="1caf7-109">Windows 10 has AllJoyn built natively into its platform, allowing developers to easily take advantage of AllJoyn to "IoT-enable" your Windows 10 apps.</span></span> <span data-ttu-id="1caf7-110">本文将概述使用通用 Windows 平台 (UWP) AllJoyn Api 和 Visual Studio 2017 [Alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展生成适用于 Windows 10 的应用程序所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="1caf7-110">This article will outline the steps required to build apps for Windows 10 using the Universal Windows Platform (UWP) AllJoyn APIs and the Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension.</span></span>

## <a name="understanding-alljoyn-uwp-app-development"></a><span data-ttu-id="1caf7-111">了解 AllJoyn UWP 应用开发</span><span class="sxs-lookup"><span data-stu-id="1caf7-111">Understanding AllJoyn UWP App Development</span></span>

<span data-ttu-id="1caf7-112">以下三个主要组件构成了 AllJoyn UWP 应用:</span><span class="sxs-lookup"><span data-stu-id="1caf7-112">Three major components form AllJoyn UWP apps:</span></span>

1. <span data-ttu-id="1caf7-113">应用布局和设计 (XAML 或 HTML) 和类组件 (C#、JavaScript、 C++或 VB)。</span><span class="sxs-lookup"><span data-stu-id="1caf7-113">App layout and design (XAML or HTML) and class components (C#, JavaScript, C++, or VB).</span></span>
2. <span data-ttu-id="1caf7-114">AllJoyn 核心 Api:Windows 10 SDK 中提供了 AllJoyn 标准客户端 API (C) 和 Windows. AllJoyn API (WinRT)。</span><span class="sxs-lookup"><span data-stu-id="1caf7-114">The AllJoyn core APIs: AllJoyn Standard Client API (C) and Windows.Devices.AllJoyn API (WinRT)  available in the Windows 10 SDK.</span></span>
3. <span data-ttu-id="1caf7-115">一个或多个 UWP Windows 运行时组件 (从 AllJoyn 接口生成此代码)。</span><span class="sxs-lookup"><span data-stu-id="1caf7-115">One or more UWP Windows Runtime Components (the  generates this code from AllJoyn interfaces).</span></span>

<span data-ttu-id="1caf7-116">下图显示了典型的 AllJoyn UWP 项目的体系结构:</span><span class="sxs-lookup"><span data-stu-id="1caf7-116">The following diagram shows the architecture of a typical AllJoyn UWP project:</span></span>

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

<span data-ttu-id="1caf7-118">启用了 AllJoyn 的 UWP 应用可以是发生器 (实现和公开接口, 通常是设备)、使用者 (使用接口, 通常为应用), 或同时使用两者。</span><span class="sxs-lookup"><span data-stu-id="1caf7-118">AllJoyn-enabled UWP apps can be either producers  (implement and expose interfaces, typically a device ), consumers (use interfaces, typically apps), or both.</span></span> <span data-ttu-id="1caf7-119">使用者和制造者共享相同的开始步骤, 仅在实现细节中进行拆分。</span><span class="sxs-lookup"><span data-stu-id="1caf7-119">Consumers and producers share the same starting steps, only diverging in the implementation details.</span></span>

## <a name="creating-an-alljoyn-enabled-uwp-app"></a><span data-ttu-id="1caf7-120">创建启用了 AllJoyn 的 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="1caf7-120">Creating an AllJoyn-enabled UWP app</span></span>

<span data-ttu-id="1caf7-121">按照以下步骤来开发适用于 Windows 10 的启用了 AllJoyn 的 UWP 应用: (本文档稍后将详细说明)</span><span class="sxs-lookup"><span data-stu-id="1caf7-121">Follow these steps to develop AllJoyn-enabled UWP apps for Windows 10: (explained in detail later in this document)</span></span>

1. <span data-ttu-id="1caf7-122">准备生成环境。</span><span class="sxs-lookup"><span data-stu-id="1caf7-122">Prepare your build environment.</span></span>
2. <span data-ttu-id="1caf7-123">确定将使用哪些 AllJoyn 接口, 并获取或创建必要的自检 XML。</span><span class="sxs-lookup"><span data-stu-id="1caf7-123">Determine which AllJoyn interfaces will be used, and obtain or create necessary Introspection XML.</span></span>
3. <span data-ttu-id="1caf7-124">创建一个 AllJoyn 应用项目, 然后选择 "自检 XML" 和所需的接口以生成代码。</span><span class="sxs-lookup"><span data-stu-id="1caf7-124">Create an AllJoyn App project then select Introspection XML and desired Interfaces for code generation.</span></span>
4. <span data-ttu-id="1caf7-125">使用从生成的 UWP Windows 运行时组件公开的 Api 在应用中实现制造者或 ponsumer 代码。</span><span class="sxs-lookup"><span data-stu-id="1caf7-125">Implement producer or ponsumer code in your app using APIs exposed from the generated UWP Windows Runtime Components.</span></span>
5. <span data-ttu-id="1caf7-126">构建用户界面。</span><span class="sxs-lookup"><span data-stu-id="1caf7-126">Build your UI.</span></span>

## <a name="preparing-your-build-environment"></a><span data-ttu-id="1caf7-127">准备生成环境</span><span class="sxs-lookup"><span data-stu-id="1caf7-127">Preparing your Build Environment</span></span>

<span data-ttu-id="1caf7-128">Windows 10 内部版本和相关工具包括编写启用了 AllJoyn 的 UWP 应用所需的所有资源。</span><span class="sxs-lookup"><span data-stu-id="1caf7-128">The Windows 10 build and related tools include all of the resources that you'll need to write AllJoyn-enabled UWP apps.</span></span>

<span data-ttu-id="1caf7-129">下面是在开始编写代码之前需要执行的操作:</span><span class="sxs-lookup"><span data-stu-id="1caf7-129">Here's what you'll need to do before you get started writing code:</span></span>

* <span data-ttu-id="1caf7-130">在电脑上安装[Windows 10](https://www.microsoft.com/windows/)</span><span class="sxs-lookup"><span data-stu-id="1caf7-130">Install [Windows 10](https://www.microsoft.com/windows/) on a PC</span></span>
* <span data-ttu-id="1caf7-131">安装[Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (请勿使用 Express edition)</span><span class="sxs-lookup"><span data-stu-id="1caf7-131">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (do NOT use an  Express edition)</span></span>
* <span data-ttu-id="1caf7-132">从 Visual Studio 库下载[AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展。</span><span class="sxs-lookup"><span data-stu-id="1caf7-132">Download the [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension from the Visual Studio Gallery.</span></span> 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a><span data-ttu-id="1caf7-133">获取用于 AllJoyn 接口的自检 XML</span><span class="sxs-lookup"><span data-stu-id="1caf7-133">Obtaining Introspection XML for AllJoyn Interfaces</span></span>

<span data-ttu-id="1caf7-134">可以通过三种方式获取用于启动项目的 AllJoyn 接口定义:</span><span class="sxs-lookup"><span data-stu-id="1caf7-134">There are three ways that you can obtain the AllJoyn interface  definitions that you will need to start your project:</span></span>

1. <span data-ttu-id="1caf7-135">在运行时从网络中的 AllJoyn 制造商提取自检 XML。</span><span class="sxs-lookup"><span data-stu-id="1caf7-135">Extract the Introspection XML from AllJoyn Producers present on your network at runtime.</span></span>
2. <span data-ttu-id="1caf7-136">从文档中获取自检 XML;实例AllSeen 联盟中的[照明服务框架 (LSF) 文档](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf)。</span><span class="sxs-lookup"><span data-stu-id="1caf7-136">Obtain the Introspection XML from documentation ; example: [Lighting Service Framework (LSF) documentation](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) from the AllSeen Alliance.</span></span>
3. <span data-ttu-id="1caf7-137">创建你自己的自检 XML, 该 XML 符合 AllJoyn/[D-总线自检](http://dbus.freedesktop.org/doc/dbus-specification.html)格式。</span><span class="sxs-lookup"><span data-stu-id="1caf7-137">Create your own Introspection XML that is compliant with the AllJoyn/[D-Bus introspection](http://dbus.freedesktop.org/doc/dbus-specification.html) format.</span></span>

<span data-ttu-id="1caf7-138">本文介绍了前两种方法: AllJoyn® Studio 以本机方式支持查询用于 AllJoyn 创建者的网络并提取其 XML, 并上传自检 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1caf7-138">This article covers the first two ways - AllJoyn® Studio natively supports querying the network for AllJoyn producers and extracting their XML as well as uploading Introspection XML files.</span></span>  <span data-ttu-id="1caf7-139">了解如何在[此处](AllJoynProducer.md)创建自己的。</span><span class="sxs-lookup"><span data-stu-id="1caf7-139">Learn how to create your own [here](AllJoynProducer.md).</span></span>

<span data-ttu-id="1caf7-140">启用了 AllJoyn 的 toaster 设备将充当此文章的示例。</span><span class="sxs-lookup"><span data-stu-id="1caf7-140">An AllJoyn-enabled toaster device will serve as the example for this post.</span></span> <span data-ttu-id="1caf7-141">此 toaster 公开用于启动和停止烤序列的控件、设置 "明暗度" 以及在 toast 焦时发出通知。</span><span class="sxs-lookup"><span data-stu-id="1caf7-141">This toaster exposes controls for starting and stopping the toasting sequence, setting the "darkness", and notifications when the toast is burnt.</span></span>

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

<span data-ttu-id="1caf7-143">Toaster 公开了以下 XML:</span><span class="sxs-lookup"><span data-stu-id="1caf7-143">The toaster exposes the following XML:</span></span>

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

## <a name="creating-an-alljoyn-project"></a><span data-ttu-id="1caf7-144">创建 AllJoyn 项目</span><span class="sxs-lookup"><span data-stu-id="1caf7-144">Creating an AllJoyn Project</span></span>

<span data-ttu-id="1caf7-145">按通常的方式创建项目:单击`File->New->New Project` "开始"。</span><span class="sxs-lookup"><span data-stu-id="1caf7-145">Create a Project the way you normally would: Click `File->New->New Project` to begin.</span></span>

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

<span data-ttu-id="1caf7-147">选择与扩展一起安装的目标语言的 "AllJoyn 应用" 模板, 而不是导航到 Windows 通用模板。</span><span class="sxs-lookup"><span data-stu-id="1caf7-147">Instead of navigating to a Windows Universal Template, select the "AllJoyn App" Template for your target language which was installed with the Extension.</span></span>  <span data-ttu-id="1caf7-148">命名项目, 然后选择要开始开发的文件位置。</span><span class="sxs-lookup"><span data-stu-id="1caf7-148">Name your project and choose a file location to begin developing.</span></span>

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

<span data-ttu-id="1caf7-150">选择 AllJoyn 应用模板之后, Visual Studio 会要求你选择要包括在项目中的 AllJoyn 接口。</span><span class="sxs-lookup"><span data-stu-id="1caf7-150">Immediately after selecting an AllJoyn App Template, Visual Studio will ask you to select the AllJoyn Interfaces you would like to include in your Project.</span></span> 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

<span data-ttu-id="1caf7-152">__从网络上的设备提取接口__</span><span class="sxs-lookup"><span data-stu-id="1caf7-152">__Extracting interfaces from a device on the network__</span></span>

<span data-ttu-id="1caf7-153">如果在网络上找不到 AllJoyn 设备或接口, 请按照[本指南](AllJoynTroubleshooting.md)进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="1caf7-153">If you cannot find your AllJoyn device or interface on the network, follow [this guide](AllJoynTroubleshooting.md) to troubleshoot.</span></span> 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

<span data-ttu-id="1caf7-155">若要查询网络中是否有公开的接口, 请在左侧面板中选择 "网络上的创建者"。</span><span class="sxs-lookup"><span data-stu-id="1caf7-155">To query your network for exposed interfaces, select the "Producers on the network" in the left-hand panel.</span></span> <span data-ttu-id="1caf7-156">这会在网络上找到任何 AllJoyn 制造者, 并列出它们支持的接口。</span><span class="sxs-lookup"><span data-stu-id="1caf7-156">This will find any AllJoyn producer on the network and list the interfaces they support.</span></span>

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

<span data-ttu-id="1caf7-158">选择要在项目中包括的接口。</span><span class="sxs-lookup"><span data-stu-id="1caf7-158">Select the interfaces you would like to inlude in your project.</span></span>  <span data-ttu-id="1caf7-159">在这种情况下, 我们仅使用 toaster 接口, 因此只选择 "Toaster" 接口。</span><span class="sxs-lookup"><span data-stu-id="1caf7-159">In this case, we are only using the toaster interface, so we select just the "org.alljoyn.example.Toaster" interface.</span></span>

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

<span data-ttu-id="1caf7-161">"操作" 列描述了对项目的挂起的更改, 并为新选择的接口显示 "添加"。</span><span class="sxs-lookup"><span data-stu-id="1caf7-161">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span> <span data-ttu-id="1caf7-162">这里, 我们为接口提供了 "ToasterLibrary" 的友好名称, 这会触发要应用的 "重命名" 操作。</span><span class="sxs-lookup"><span data-stu-id="1caf7-162">Here we have given the interface a friendly name of "ToasterLibrary", which triggers the "Rename" action to be applied.</span></span>

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

<span data-ttu-id="1caf7-164">__从文件加载 XML__</span><span class="sxs-lookup"><span data-stu-id="1caf7-164">__Loading an XML from a File__</span></span>

<span data-ttu-id="1caf7-165">通过 "浏览" 按钮选择任意数量的自检 XML 文件, 以查看其包含的接口。</span><span class="sxs-lookup"><span data-stu-id="1caf7-165">Choose any number of Introspection XML files via the "Browse" button to see their contained Interface(s).</span></span>

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

<span data-ttu-id="1caf7-167">导航到并选择相应的 XML (此处使用的是 toaster)。</span><span class="sxs-lookup"><span data-stu-id="1caf7-167">Navigate to and select the appropriate XML (here, we are using toaster.xml).</span></span>

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

<span data-ttu-id="1caf7-169">在 AllJoyn® Studio 加载 XML 后, 它将分析中包含的各种接口和说明, 使您可以选择要支持的接口。</span><span class="sxs-lookup"><span data-stu-id="1caf7-169">Once AllJoyn® Studio loads the XML, it will parse the various Interfaces and the descriptions contained within, allowing you select which Interfaces you would like to support.</span></span>

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

<span data-ttu-id="1caf7-171">"操作" 列描述了对项目的挂起的更改, 并为新选择的接口显示 "添加"。</span><span class="sxs-lookup"><span data-stu-id="1caf7-171">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span>

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

<span data-ttu-id="1caf7-173">在这里, 我们选择了包含 "Toaster" 接口, 并为其提供了一个友好名称 "ToasterLibrary", 触发要应用的 "重命名" 操作。</span><span class="sxs-lookup"><span data-stu-id="1caf7-173">Here we have chosen to include the "org.alljoyn.example.Toaster" Interface and have given it a friendly name of "ToasterLibrary", triggering the "Rename" action to be applied.</span></span>

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

<span data-ttu-id="1caf7-175">__添加和移除接口__</span><span class="sxs-lookup"><span data-stu-id="1caf7-175">__Adding and Removing Interfaces__</span></span>

<span data-ttu-id="1caf7-176">完成这些步骤后, 生成的文件会自动添加到具有C++上述友好名称的 Windows 运行时组件中, 并作为对应用程序项目的引用添加。</span><span class="sxs-lookup"><span data-stu-id="1caf7-176">After completing these steps, the generated files are automatically added to a C++ Windows Runtime Component with the friendly name from above and added as a Reference to the application Project.</span></span>  <span data-ttu-id="1caf7-177">但是, 根命名空间仍与接口定义的 "Toaster" 相同。</span><span class="sxs-lookup"><span data-stu-id="1caf7-177">However, the Root Namespace is still the same "org.alljoyn.example.Toaster" as defined by the interface.</span></span>  <span data-ttu-id="1caf7-178">访问这些组件的任何类都需要为组件的根命名空间使用 "using" 子句。</span><span class="sxs-lookup"><span data-stu-id="1caf7-178">Any classes that access these components need to have a "using" clause for the component's root namespace.</span></span>

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

<span data-ttu-id="1caf7-180">_提示立即生成生成的组件, 以便从 IntelliSense 中获益。_</span><span class="sxs-lookup"><span data-stu-id="1caf7-180">_TIP: Build the generated components now in order to benefit from IntelliSense._</span></span>

<span data-ttu-id="1caf7-181">创建了 AllJoyn 应用解决方案后, 你始终可以返回并修改所使用的接口。</span><span class="sxs-lookup"><span data-stu-id="1caf7-181">After you have created your AllJoyn App solution, you can always go back and modify the interfaces you are using.</span></span> <span data-ttu-id="1caf7-182">在主菜单栏中, 单击 "AllJoyn-> 添加/删除接口 ..."启动接口管理器。</span><span class="sxs-lookup"><span data-stu-id="1caf7-182">From the main menu bar, click "AllJoyn->Add/Remove Interfaces..." to launch the Interface manager.</span></span>

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

<span data-ttu-id="1caf7-184">在此处, 你可以单击 "浏览 ..."添加更多 XML 文件或取消选择现有接口。</span><span class="sxs-lookup"><span data-stu-id="1caf7-184">From here, you may click "Browse..." to add more XML files, or de-select existing Interface(s).</span></span> <span data-ttu-id="1caf7-185">取消选择某个接口会将其操作更新为 "删除", 单击 "确定" 按钮可从解决方案中删除关联的 Windows 运行时组件。</span><span class="sxs-lookup"><span data-stu-id="1caf7-185">De-selecting an Interface updates its Action to "Remove", and clicking the Ok button removes the associated Windows Runtime Component from your solution.</span></span>

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

<span data-ttu-id="1caf7-187">查看解决方案资源管理器, Windows 运行时组件已删除。</span><span class="sxs-lookup"><span data-stu-id="1caf7-187">Looking at the Solution Explorer, the Windows Runtime Component has been removed.</span></span>

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a><span data-ttu-id="1caf7-189">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1caf7-189">Next Steps</span></span>

<span data-ttu-id="1caf7-190">实现 AllJoyn 功能时, 请始终确保包含 "Windows. AllJoyn" 命名空间以及要使用的接口中的命名空间。</span><span class="sxs-lookup"><span data-stu-id="1caf7-190">When implementing AllJoyn functionality, always be sure to include the "Windows.Devices.AllJoyn" namespace as well as the namespace from the interface you want to use.</span></span>

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

<span data-ttu-id="1caf7-192">__实现 AllJoyn 使用者__</span><span class="sxs-lookup"><span data-stu-id="1caf7-192">__Implementing an AllJoyn Consumer__</span></span>

<span data-ttu-id="1caf7-193">为接口生成的代码包含用于查找并控制制造者的观察程序和使用者类。</span><span class="sxs-lookup"><span data-stu-id="1caf7-193">The code generated for the interfaces contains a watcher and consumer class used to find and then control a producer.</span></span> <span data-ttu-id="1caf7-194">通过创建新的 AllJoynBusAttachment 来实现观察程序, 使用该 AllJoynBusAttachment 初始化观察程序, 注册观察程序找到一个生成者 ("添加" 事件), 然后启动观察程序。</span><span class="sxs-lookup"><span data-stu-id="1caf7-194">Implement the watcher by creating a new AllJoynBusAttachment, initialize the watcher with that AllJoynBusAttachment, register for the watcher finding a producer (the "Added" event), then start the watcher.</span></span>

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

<span data-ttu-id="1caf7-196">每当观察程序找到生成者时, ToasterWatcher_Added 事件就会触发。</span><span class="sxs-lookup"><span data-stu-id="1caf7-196">The ToasterWatcher_Added event triggers whenever the watcher finds a producer.</span></span>  <span data-ttu-id="1caf7-197">使用此事件来注册使用者。</span><span class="sxs-lookup"><span data-stu-id="1caf7-197">Use this event to register a consumer.</span></span> <span data-ttu-id="1caf7-198">请注意, Visual Studio 将通过快速操作生成必要的 shell 方法。</span><span class="sxs-lookup"><span data-stu-id="1caf7-198">Note that Visual Studio will generate the necessary shell method through the Quick Actions.</span></span>

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

<span data-ttu-id="1caf7-200">生成方法会生成以下 shell 代码:</span><span class="sxs-lookup"><span data-stu-id="1caf7-200">Generating the method produces the following shell code:</span></span>

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

<span data-ttu-id="1caf7-202">使用正确的逻辑填充 shell 代码允许注册使用者。</span><span class="sxs-lookup"><span data-stu-id="1caf7-202">Filling in the shell code with the correct logic enables registering the consumer.</span></span>

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

<span data-ttu-id="1caf7-204">请注意, 每次观察程序发现一个生成者时, 都会触发此事件。</span><span class="sxs-lookup"><span data-stu-id="1caf7-204">Note that this event triggers every time the watcher discovers a producer.</span></span>  <span data-ttu-id="1caf7-205">如果希望找到多个创建者, 请保留使用者的数据结构, 因为每个制造者都有一个使用者。</span><span class="sxs-lookup"><span data-stu-id="1caf7-205">If you expect to find multiple producers, keep a data structure of the consumer as there will be one consumer for each producer.</span></span>

<span data-ttu-id="1caf7-206">为制造者发出的各种信号注册事件–属性更改信号是使用者类的直接成员, 而其他信号是信号类的成员 (正如之前一样, 请使用快速操作为这些事件生成 shell 代码)。</span><span class="sxs-lookup"><span data-stu-id="1caf7-206">Register events for the various signals the producer will emit – property changed signals are direct members of the consumer class, but other signals are members of the Signals class (just as before, use the Quick Actions to generate the shell code for these events).</span></span>

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

<span data-ttu-id="1caf7-208">使用使用者对象可以读取和写入属性, 还可以调用方法。</span><span class="sxs-lookup"><span data-stu-id="1caf7-208">Use the consumer object to read and write properties as well as call methods.</span></span>

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a><span data-ttu-id="1caf7-210">实现 AllJoyn 制造者</span><span class="sxs-lookup"><span data-stu-id="1caf7-210">Implementing an AllJoyn Producer</span></span>

<span data-ttu-id="1caf7-211">__实现服务__</span><span class="sxs-lookup"><span data-stu-id="1caf7-211">__Implementing the Service__</span></span>

<span data-ttu-id="1caf7-212">发生器实现公开其接口的服务。</span><span class="sxs-lookup"><span data-stu-id="1caf7-212">Producers implement a service that expose their interfaces.</span></span>  <span data-ttu-id="1caf7-213">若要实现发生器, 请首先为其服务创建一个类。</span><span class="sxs-lookup"><span data-stu-id="1caf7-213">To implement a producer, first create a class for its service.</span></span>

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

<span data-ttu-id="1caf7-215">将接口的命名空间添加到 "using" 语句, 然后继承为服务生成的 shell 接口, 并使用 Quick 操作来实现类。</span><span class="sxs-lookup"><span data-stu-id="1caf7-215">Add the namespace for the interface to the "using" statements, then inherit the shell interface generated for the service and use the Quick Action to implement the class.</span></span>

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

<span data-ttu-id="1caf7-217">在这里, 快速操作会填写必要的组件。</span><span class="sxs-lookup"><span data-stu-id="1caf7-217">From here, the Quick Action will fill in the necessary components.</span></span>

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

<span data-ttu-id="1caf7-219">代码的所有必需部分都可以正常工作, 但仍需实现每个方法和属性调用的实际逻辑。</span><span class="sxs-lookup"><span data-stu-id="1caf7-219">All the necessary parts of the code are ready to function, but you still need to implement the actual logic for each method and property call.</span></span>

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

<span data-ttu-id="1caf7-221">采用 SetDarknessLevelAsync 作为示例, 我们使用任务来创建成功的结果。</span><span class="sxs-lookup"><span data-stu-id="1caf7-221">Taking the SetDarknessLevelAsync as an example, we use a task to create a success result.</span></span>  <span data-ttu-id="1caf7-222">如果失败, 则返回 ToasterSetDarknessLevelResult. CreateFailureResult ()。</span><span class="sxs-lookup"><span data-stu-id="1caf7-222">In case of failure, return ToasterSetDarknessLevelResult.CreateFailureResult().</span></span>

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

<span data-ttu-id="1caf7-224">实现方法和属性调用的其余部分以完成服务。</span><span class="sxs-lookup"><span data-stu-id="1caf7-224">Implement the rest of the method and property calls to finish the service.</span></span>

<span data-ttu-id="1caf7-225">__实现制造者__</span><span class="sxs-lookup"><span data-stu-id="1caf7-225">__Implementing the Producer__</span></span>

<span data-ttu-id="1caf7-226">创建制造者非常简单–创建一个新的 AllJoynBusAttachment, 使用该 AllJoynBusAttachment 初始化一个创建者, 为制造者初始化新创建的服务, 然后启动创建者。</span><span class="sxs-lookup"><span data-stu-id="1caf7-226">Creating the producer is straightforward – create a new AllJoynBusAttachment, initialize a producer with that AllJoynBusAttachment, initialize the newly created service for the producer, then start the producer.</span></span>

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

<span data-ttu-id="1caf7-228">由于服务包含大部分逻辑, 要实现的主要功能是为非状态事件发送属性更改和离散信号的信号。</span><span class="sxs-lookup"><span data-stu-id="1caf7-228">Since the service contains the majority of the logic, the main functionality left to implement is to send the signals for property changes and discrete signals for non-state events.</span></span>  <span data-ttu-id="1caf7-229">根据需要通过方法调用实现这些方法。</span><span class="sxs-lookup"><span data-stu-id="1caf7-229">Implement these as necessary through method calls.</span></span>

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

<span data-ttu-id="1caf7-231">__详细信息__</span><span class="sxs-lookup"><span data-stu-id="1caf7-231">__More Information__</span></span>

<span data-ttu-id="1caf7-232">如果已正确完成本文档中的所有说明, 则可以开始在应用程序中编写 AllJoyn 代码。</span><span class="sxs-lookup"><span data-stu-id="1caf7-232">If you've completed all of the instructions in this document correctly, you are ready to start writing AllJoyn code in your app.</span></span>

<span data-ttu-id="1caf7-233">有关参考, 请参阅 Microsoft 示例 GitHub 上的 AllJoyn 通用 Windows 应用示例, 获取[Alljoyn 制造](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)者和[alljoyn 使用者](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)。</span><span class="sxs-lookup"><span data-stu-id="1caf7-233">For reference, please look to the AllJoyn Universal Windows Apps samples on the Microsoft Sample GitHub for [AllJoyn Producers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) and [AllJoyn Consumers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span></span>

<span data-ttu-id="1caf7-234">有关如何创建 AllJoyn 应用的详细演练, 请观看 AllJoyn 会话 623:</span><span class="sxs-lookup"><span data-stu-id="1caf7-234">For a detailed walkthrough of how to create an AllJoyn app, please watch the AllJoyn session 623:</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

<span data-ttu-id="1caf7-235">请注意, 在同一台计算机上的两个 UWP 应用之间进行的 AllJoyn 通信将被 Windows 策略禁用, 除非它们启用了环回异常, 如从 Visual Studio 直接部署时。</span><span class="sxs-lookup"><span data-stu-id="1caf7-235">Note that AllJoyn communication between two UWP apps on the same machine is disabled by Windows policy unless they have enabled a loopback exception, such as when being directly deployed from Visual Studio.</span></span>  <span data-ttu-id="1caf7-236">有关启用环回豁免的详细说明, 请参阅[此处](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1caf7-236">For detailed instructions on enabling loopback exemption, see [here](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>



