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
ms.openlocfilehash: 6655cf5e8584a9c7046301cda24b10348a704d6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510638"
---
> [!NOTE]
> <span data-ttu-id="f11be-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="f11be-104">You are viewing archived documentation.</span></span> <span data-ttu-id="f11be-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="f11be-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="f11be-106">如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="f11be-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn"></a><span data-ttu-id="f11be-107">AllJoyn</span><span class="sxs-lookup"><span data-stu-id="f11be-107">AllJoyn</span></span>

<span data-ttu-id="f11be-108">AllJoyn 支持物联网。</span><span class="sxs-lookup"><span data-stu-id="f11be-108">AllJoyn empowers the Internet of Things.</span></span> <span data-ttu-id="f11be-109">AllJoyn 定义了设备和应用程序互相发现和通信的通用协议，而不考虑传输技术、平台或制造商。</span><span class="sxs-lookup"><span data-stu-id="f11be-109">AllJoyn defines a common protocol for devices and applications to discover and communicate with each other regardless of transport technology, platform or manufacturer.</span></span>  <span data-ttu-id="f11be-110">AllJoyn 是由 [AllSeen 联盟](https://allseenalliance.org/)推动的一种开源标准，该组织是一个致力于支持物联网中的数十亿设备、服务和应用程序进行互操作的跨行业联合会。</span><span class="sxs-lookup"><span data-stu-id="f11be-110">AllJoyn is an open source standard driven by the [AllSeen Alliance](https://allseenalliance.org/), a cross-industry consortium dedicated to enabling the interoperability of billions of devices, services and applications for the Internet of Things.</span></span>

<span data-ttu-id="f11be-111">Microsoft 在 2014 年加入了 AllSeen 联盟，并在 Windows 10 中将 Alliance 添加为核心组件。</span><span class="sxs-lookup"><span data-stu-id="f11be-111">Microsoft joined the AllSeen Alliance in 2014 and added AllJoyn as a core component in Windows 10.</span></span> <span data-ttu-id="f11be-112">使用内置的 [AllJoyn API](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx)，开发人员可以自由编写可在任何 Windows 10 设备上运行的支持 AllJoyn 的应用程序，包括 PC、平板电脑、手机、Xbox 以及使用 Windows IoT 核心版的设备。</span><span class="sxs-lookup"><span data-stu-id="f11be-112">With the built-in [AllJoyn APIs](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx), developers are free to write AllJoyn capable applications that run on any of the Windows 10 devices including PCs, tablets, phones, Xbox as well as devices using Windows IoT Core.</span></span> <span data-ttu-id="f11be-113">除了对 AllJoyn 的平台支持，Microsoft 还发布了 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)，它是一款通过将代码生成与现成应用程序模板结合来加快 AllJoyn 开发的 Visual Studio 扩展。</span><span class="sxs-lookup"><span data-stu-id="f11be-113">In addition to the platform support for AllJoyn, Microsoft released [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286), a Visual Studio extension that accelerates AllJoyn development by combining code generation with ready-made application templates.</span></span> <span data-ttu-id="f11be-114">AllJoyn Studio 使开发人员无需进行繁琐的设置和配置即可从 AllJoyn 的强大功能中受益。</span><span class="sxs-lookup"><span data-stu-id="f11be-114">AllJoyn Studio allows developers to benefit from the power of AllJoyn without the hassle of set-up and configuration.</span></span>

<span data-ttu-id="f11be-115">对 AllJoyn 感到兴奋？</span><span class="sxs-lookup"><span data-stu-id="f11be-115">Excited about AllJoyn?</span></span> <span data-ttu-id="f11be-116">请查看[此](AllJoynStudio.md)博客文章来了解如何开始在 Windows 上使用 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="f11be-116">Have a look at [this](AllJoynStudio.md) blog post on how to get started with AllJoyn on Windows.</span></span>


## <a name="developer-resources-and-tools"></a><span data-ttu-id="f11be-117">开发人员资源和工具</span><span class="sxs-lookup"><span data-stu-id="f11be-117">Developer Resources and Tools</span></span>

**<span data-ttu-id="f11be-118">设备系统桥接</span><span class="sxs-lookup"><span data-stu-id="f11be-118">Device System Bridge</span></span>**

<span data-ttu-id="f11be-119">AllJoyn [设备系统网桥](AllJoynDSB.md)支持非 AllJoyn 设备使用 AllJoyn 作为其公共语言与 AllJoyn 生态系统进行交互。</span><span class="sxs-lookup"><span data-stu-id="f11be-119">AllJoyn [Device System Bridge](AllJoynDSB.md) enables non-AllJoyn devices to interact with the AllJoyn ecosystem using AllJoyn as their common language.</span></span>

<span data-ttu-id="f11be-120">功能：</span><span class="sxs-lookup"><span data-stu-id="f11be-120">Features:</span></span>
* <span data-ttu-id="f11be-121">为适配器公开的每个非 AllJoyn 设备创建虚拟设备</span><span class="sxs-lookup"><span data-stu-id="f11be-121">Creates virtual devices for each non-AllJoyn device exposed by Adapter</span></span>
* <span data-ttu-id="f11be-122">从适配器设备自动生成运行时接口</span><span class="sxs-lookup"><span data-stu-id="f11be-122">Automated runtime interface generation from Adapter device</span></span>
* <span data-ttu-id="f11be-123">支持 LSF，控制面板基本服务，可扩展添加更多服务</span><span class="sxs-lookup"><span data-stu-id="f11be-123">Supports LSF, Control Panel base services, extensible to add more services</span></span>
* <span data-ttu-id="f11be-124">适用于桌面 UI 应用程序和 Windows IoT 启动任务的通用应用模板（C#、C++）</span><span class="sxs-lookup"><span data-stu-id="f11be-124">Universal app templates (C#, C++), for Desktop UI applications and Windows IoT startup tasks</span></span>
* <span data-ttu-id="f11be-125">以开源方式提供</span><span class="sxs-lookup"><span data-stu-id="f11be-125">Available as open source</span></span>

<span data-ttu-id="f11be-126">有关更多详细信息，请参阅[设备系统网桥页面](AllJoynDSB.md)。</span><span class="sxs-lookup"><span data-stu-id="f11be-126">More details can be found on the [Device System Bridge page](AllJoynDSB.md).</span></span>


**<span data-ttu-id="f11be-127">AllJoyn Studio</span><span class="sxs-lookup"><span data-stu-id="f11be-127">AllJoyn Studio</span></span>**

<span data-ttu-id="f11be-128">[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 是由 Microsoft 开发的 Visual Studio 扩展，用于通过将代码生成和 WinRT API 与自动项目管理和现成应用程序模板结合来加快 AllJoyn® 开发。</span><span class="sxs-lookup"><span data-stu-id="f11be-128">[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) is an extension to Visual Studio developed by Microsoft that accelerates AllJoyn® development by combining code generation and the WinRT API with automated project management and ready-made application templates.</span></span> <span data-ttu-id="f11be-129">它使开发人员无需进行繁琐的设置和配置即可从 AllJoyn 的强大功能中受益。</span><span class="sxs-lookup"><span data-stu-id="f11be-129">It allows developers to benefit from the power of AllJoyn without the hassle of set-up and configuration.</span></span>

<span data-ttu-id="f11be-130">功能：</span><span class="sxs-lookup"><span data-stu-id="f11be-130">Features:</span></span>
* <span data-ttu-id="f11be-131">通用应用模板（C#、JavaScript、C++、Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f11be-131">Universal app templates (C#, JavaScript, C++, Visual Basic)</span></span>
* <span data-ttu-id="f11be-132">自动引用管理和项目配置</span><span class="sxs-lookup"><span data-stu-id="f11be-132">Automated reference management and project configuration</span></span>
* <span data-ttu-id="f11be-133">在解决方案中添加/删除接口</span><span class="sxs-lookup"><span data-stu-id="f11be-133">Adding/removing interfaces to/from a solution</span></span>
* <span data-ttu-id="f11be-134">通过 AllJoyn® 菜单轻松访问项目管理</span><span class="sxs-lookup"><span data-stu-id="f11be-134">Easy access to project management via the AllJoyn® menu</span></span>
* <span data-ttu-id="f11be-135">从自检 XML 文件加载接口</span><span class="sxs-lookup"><span data-stu-id="f11be-135">Loading interfaces from introspection XML file(s)</span></span>
* <span data-ttu-id="f11be-136">从 network1 上的创建器发现接口</span><span class="sxs-lookup"><span data-stu-id="f11be-136">Discovering interfaces from producer(s) on the network1</span></span>

<span data-ttu-id="f11be-137">AllJoyn Studio 可以通过安装 Visual Studio 工具-> 扩展和更新...</span><span class="sxs-lookup"><span data-stu-id="f11be-137">AllJoyn Studio can be installed through Visual Studio Tools -> Extensions and Updates …</span></span> <span data-ttu-id="f11be-138">-> 联机-> 的"搜索"字段中键入"AllJoyn"</span><span class="sxs-lookup"><span data-stu-id="f11be-138">-> Online -> In the "Search" field type "AllJoyn"</span></span>

<span data-ttu-id="f11be-139">提供了有关如何使用 AllJoyn Studio 的更多详细信息[此处](AllJoynStudio.md)。</span><span class="sxs-lookup"><span data-stu-id="f11be-139">More detail about how to use AllJoyn Studio are available [here](AllJoynStudio.md).</span></span>

**<span data-ttu-id="f11be-140">IoT 资源管理器为 AllJoyn （AllJoyn 的资源管理器） 的</span><span class="sxs-lookup"><span data-stu-id="f11be-140">IoT Explorer for AllJoyn (AllJoyn Explorer)</span></span>**

<span data-ttu-id="f11be-141">AllJoyn 的 IoT 资源管理器（以前称为 AllJoyn 资源管理器）是 Windows 通用应用程序，用于与本地邻近网络上的 AllJoyn 设备进行交互。</span><span class="sxs-lookup"><span data-stu-id="f11be-141">The IoT Explorer for AllJoyn (previously known as AllJoyn Explorer) is a Windows Universal Application for interacting with AllJoyn devices on the local proximity network.</span></span> <span data-ttu-id="f11be-142">开发人员可以列出所有可用的 AllJoyn 设备、检查其接口和对象结构，以及接收信号、设置和获取属性并调用方法。</span><span class="sxs-lookup"><span data-stu-id="f11be-142">Developers can list all available AllJoyn devices, inspect their interface and object structure, as well as receive signals, set and get properties, and call methods.</span></span>

* <span data-ttu-id="f11be-143">[AllJoyn 的 IoT 资源管理器应用商店应用](https://www.microsoft.com/store/apps/9nblggh6gpxl)：这是官方应用商店应用所在的位置。</span><span class="sxs-lookup"><span data-stu-id="f11be-143">[IoT Explorer for AllJoyn Store App](https://www.microsoft.com/store/apps/9nblggh6gpxl): This is the official store app location.</span></span>
* <span data-ttu-id="f11be-144">[AllJoyn 资源管理器 1.0.1.11（早期版本）](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip)：此 zip 包含要旁加载到开发人员的计算机上的 AllJoyn 资源管理器 AppX 捆绑包。</span><span class="sxs-lookup"><span data-stu-id="f11be-144">[AllJoyn Explorer 1.0.1.11 (previous release)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): This zip contains the AllJoyn Explorer AppX bundle to be side-loaded on a developer machine.</span></span> <span data-ttu-id="f11be-145">这是针对 AllJoyn 应用程序的以前发布版本的 IoT 资源管理器。</span><span class="sxs-lookup"><span data-stu-id="f11be-145">This is a previously released version of the IoT Explorer for AllJoyn application.</span></span>
* <span data-ttu-id="f11be-146">[AllJoyn 资源管理器设置指南](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf)：此 pdf 包含有关如何部署 AllJoyn 资源管理器的文档。</span><span class="sxs-lookup"><span data-stu-id="f11be-146">[AllJoyn Explorer Setup Guide](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): This pdf contains the documentation for how to deploy the AllJoyn Explorer.</span></span>
* <span data-ttu-id="f11be-147">[AllJoyn 资源管理器用户指南](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf)：此 pdf 包含有关如何使用 AllJoyn 资源管理器的文档。</span><span class="sxs-lookup"><span data-stu-id="f11be-147">[AllJoyn Explorer User Guide](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): This pdf contains the documentation for how to use the AllJoyn Explorer.</span></span>


### <a name="additional-resources"></a><span data-ttu-id="f11be-148">其他资源</span><span class="sxs-lookup"><span data-stu-id="f11be-148">Additional Resources</span></span>

* [<span data-ttu-id="f11be-149">使用 AllJoyn Studio 扩展</span><span class="sxs-lookup"><span data-stu-id="f11be-149">Using the AllJoyn Studio extension</span></span>](AllJoynStudio.md)
* [<span data-ttu-id="f11be-150">AllJoyn 生成者和创作 AllJoyn 自检</span><span class="sxs-lookup"><span data-stu-id="f11be-150">AllJoyn Producer and Authoring AllJoyn Introspection</span></span>](AllJoynProducer.md)
* [<span data-ttu-id="f11be-151">使用 Windows 10 的故障排除 AllJoyn</span><span class="sxs-lookup"><span data-stu-id="f11be-151">Troubleshooting AllJoyn with Windows 10</span></span>](AllJoynTroubleshooting.md)

**<span data-ttu-id="f11be-152">视频</span><span class="sxs-lookup"><span data-stu-id="f11be-152">Videos</span></span>**

* [<span data-ttu-id="f11be-153">生成 2015 AllJoyn 技术会话</span><span class="sxs-lookup"><span data-stu-id="f11be-153">//build 2015 AllJoyn Technical Session</span></span>](https://channel9.msdn.com/Events/Build/2015/2-623)
* [<span data-ttu-id="f11be-154">WinHEC 2015 AllJoyn 技术会话</span><span class="sxs-lookup"><span data-stu-id="f11be-154">WinHEC 2015 AllJoyn Technical Session</span></span>](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

**<span data-ttu-id="f11be-155">示例</span><span class="sxs-lookup"><span data-stu-id="f11be-155">Samples</span></span>**

* [<span data-ttu-id="f11be-156">AllJoyn 生成者</span><span class="sxs-lookup"><span data-stu-id="f11be-156">AllJoyn Producers</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [<span data-ttu-id="f11be-157">AllJoyn 使用者</span><span class="sxs-lookup"><span data-stu-id="f11be-157">AllJoyn Consumers</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [<span data-ttu-id="f11be-158">AllJoyn UWP 示例 (MSDN)</span><span class="sxs-lookup"><span data-stu-id="f11be-158">AllJoyn UWP Samples (MSDN)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

**<span data-ttu-id="f11be-159">参考</span><span class="sxs-lookup"><span data-stu-id="f11be-159">Reference</span></span>**

* [<span data-ttu-id="f11be-160">Windows 10 (MSDN) 中的 AllJoyn Api</span><span class="sxs-lookup"><span data-stu-id="f11be-160">AllJoyn APIs in Windows 10 (MSDN)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [<span data-ttu-id="f11be-161">AllJoyn 体系结构详细信息 （Allseen 联盟）</span><span class="sxs-lookup"><span data-stu-id="f11be-161">AllJoyn Architecture Details (Allseen Alliance)</span></span>](https://allseenalliance.org/developers/learn/)
* [<span data-ttu-id="f11be-162">AllJoyn 开发人员资源 （Allseen 联盟）</span><span class="sxs-lookup"><span data-stu-id="f11be-162">AllJoyn Developer Resources (Allseen Alliance)</span></span>](https://allseenalliance.org/developers/develop/)
* [<span data-ttu-id="f11be-163">AllJoyn C API 参考手册 （Allseen 联盟）</span><span class="sxs-lookup"><span data-stu-id="f11be-163">AllJoyn C API Reference Manual (Allseen Alliance)</span></span>](https://allseenalliance.org/docs/api/c/index.html)

