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
> <span data-ttu-id="8d6e6-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-104">You are viewing archived documentation.</span></span> <span data-ttu-id="8d6e6-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="8d6e6-106">如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-device-system-bridge"></a><span data-ttu-id="8d6e6-107">AllJoyn 设备系统桥接</span><span class="sxs-lookup"><span data-stu-id="8d6e6-107">AllJoyn Device System Bridge</span></span>

<span data-ttu-id="8d6e6-108">AllJoyn 提供开发人员可以灵活地使用各种平台和连接技术来构建 AllJoyn 生态系统的设备。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-108">AllJoyn provides developers with the flexibility to use a wide range of platforms and connection technologies to build  devices for the AllJoyn ecosystem.</span></span>  <span data-ttu-id="8d6e6-109">但是，许多设备制造商在其项目组合中具有现有设备的解决方案。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-109">However, many device makers have existing device solutions in their portfolios.</span></span> <span data-ttu-id="8d6e6-110">对于这些情况下，Microsoft 创建设备系统桥接 (DSB)。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-110">For these situations, Microsoft created the Device System Bridge (DSB).</span></span> <span data-ttu-id="8d6e6-111">DSB 调整非 AllJoyn AllJoyn 生态系统的设备，以便调整的设备可以与 AllJoyn 作为其公共语言进行互操作。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-111">The DSB adapts non-AllJoyn devices to the AllJoyn ecosystem so that the adapted devices can interoperate with AllJoyn as their common language.</span></span> <span data-ttu-id="8d6e6-112">Microsoft DSB 支持家庭自动化系统，例如 Zigbee 和 Z 兴起，甚至可以支持工业生成自动化系统，例如 BACnet。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-112">Microsoft DSB’s support home automation systems such as Zigbee, and Z-Wave, and can even support industrial building automation systems such as BACnet.</span></span>  <span data-ttu-id="8d6e6-113">此外，源代码是可自定义以支持其他技术。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-113">Additionally, the source code is available for customization to support other technologies</span></span>

## <a name="how-dsb-works"></a><span data-ttu-id="8d6e6-114">DSB 的工作原理</span><span class="sxs-lookup"><span data-stu-id="8d6e6-114">How DSB works</span></span>

<span data-ttu-id="8d6e6-115">DSB 的关键功能是 AllJoyn 总线上创建的设备的虚拟表示。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-115">The key capability of a DSB is to create a virtual representation of devices on the AllJoyn bus.</span></span> <span data-ttu-id="8d6e6-116">因此这些设备，无论其本机连接或设备生态系统是什么，将出现，并且可作为 AllJoyn 的设备。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-116">So these devices, whatever their native connectivity or device ecosystem is, will appear and be accessible as AllJoyn devices.</span></span> <span data-ttu-id="8d6e6-117">在下两个 DSBs 图，一个 Z 波形的一个用于 ZigBee 创建两个 Z 兴起和一个 ZigBee 设备的虚拟表示 AllJoyn 总线上。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-117">In the picture below two DSBs , one for Z-Wave and one for ZigBee create virtual representation of the two Z-Wave and the one ZigBee devices on the AllJoyn bus.</span></span> <span data-ttu-id="8d6e6-118">与此 AllJoyn 上的所有设备站点可以相互通信。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-118">With this all devices on the AllJoyn site can communicate with each other.</span></span> <span data-ttu-id="8d6e6-119">因为 AllJoyn 总线上所有的 Z 批和 ZigBee 设备他们现在可以相互通信以及。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-119">Because the Z-Wave and ZigBee devices all on the AllJoyn bus they now can communicate with each other as well.</span></span>

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

<span data-ttu-id="8d6e6-121">DSB 设计的另一个关键元素是它将需要对 AllJoyn 或非 AllJoyn 设备系统的任何更改。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-121">Another key element of the DSB design is that it will not require any changes to the AllJoyn or non-AllJoyn device system.</span></span> <span data-ttu-id="8d6e6-122">所有必要的采用都在 DSB 中完成。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-122">All necessary adoptions are done in the DSB.</span></span>

<span data-ttu-id="8d6e6-123">如图还显示了，没有从 AllJoyn 设备映射到非 AllJoyn 端。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-123">As the picture also shows, there is no mapping from AllJoyn devices to the non-AllJoyn side.</span></span> <span data-ttu-id="8d6e6-124">DSB 旨在将设备纳入 AllJoyn 生态系统。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-124">The objective of the DSB is to bring devices into the AllJoyn ecosystem.</span></span> <span data-ttu-id="8d6e6-125">启用只有一种方式简化了开发。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-125">Enabling only one way simplifies the development.</span></span> <span data-ttu-id="8d6e6-126">它还可降低风险该 AllJoyn 可能较不安全的非 AllJoyn 设备系统变得削弱的安全功能。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-126">It also reduces the risk that AllJoyn security capabilities become weakened by the potentially less secure non-AllJoyn device system.</span></span>

## <a name="dsb-architecture"></a><span data-ttu-id="8d6e6-127">DSB 体系结构</span><span class="sxs-lookup"><span data-stu-id="8d6e6-127">DSB Architecture</span></span>

<span data-ttu-id="8d6e6-128">Microsoft 建议 DSB 体系结构包括三个主要组件，网络访问堆栈、 适配器和桥。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-128">The Microsoft proposed DSB architecture consists of three main components, Network Access Stack, Adapter and Bridge.</span></span> <span data-ttu-id="8d6e6-129">下图显示了此体系结构的高级别概述。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-129">The picture below shows the high level overview of this architecture.</span></span>

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a><span data-ttu-id="8d6e6-131">Bridge</span><span class="sxs-lookup"><span data-stu-id="8d6e6-131">Bridge</span></span>
* <span data-ttu-id="8d6e6-132">每个内部设备对象表示为 AllJoyn 设备，为每个设备的单独总线附件</span><span class="sxs-lookup"><span data-stu-id="8d6e6-132">Represents each internal device object as AllJoyn device, separate bus attachment for each device</span></span>
* <span data-ttu-id="8d6e6-133">设备会动态添加或删除从 AllJoyn 总线</span><span class="sxs-lookup"><span data-stu-id="8d6e6-133">Devices are dynamically added to or removed from the AllJoyn bus</span></span>
* <span data-ttu-id="8d6e6-134">配置管理设备的可见性和安全性</span><span class="sxs-lookup"><span data-stu-id="8d6e6-134">Configuration manages device visibility and security</span></span>
* <span data-ttu-id="8d6e6-135">创建桥和适配器配置界面的总线附件</span><span class="sxs-lookup"><span data-stu-id="8d6e6-135">Creates bus attachment for bridge and adapter configuration interface</span></span>
* <span data-ttu-id="8d6e6-136">桥接代码是不可知的内部设备类型和任何类型的可重用</span><span class="sxs-lookup"><span data-stu-id="8d6e6-136">Bridge code is agnostic to internal device types and reusable for any type</span></span>

### <a name="adapter"></a><span data-ttu-id="8d6e6-137">适配器</span><span class="sxs-lookup"><span data-stu-id="8d6e6-137">Adapter</span></span>
* <span data-ttu-id="8d6e6-138">实例化和管理代表每个设备从非 AllJoyn 网络虚拟设备</span><span class="sxs-lookup"><span data-stu-id="8d6e6-138">Instantiates and manages virtual devices on behalf of each device from the non-AllJoyn network</span></span>
* <span data-ttu-id="8d6e6-139">设备架构转换为内部设备对象</span><span class="sxs-lookup"><span data-stu-id="8d6e6-139">Translates device schemas into internal device objects</span></span>
* <span data-ttu-id="8d6e6-140">管理网络资源，例如访问密钥，凭据</span><span class="sxs-lookup"><span data-stu-id="8d6e6-140">Manages network resources, e.g. access keys, credentials</span></span>

### <a name="network-access-stack"></a><span data-ttu-id="8d6e6-141">网络访问堆栈</span><span class="sxs-lookup"><span data-stu-id="8d6e6-141">Network Access Stack</span></span>
* <span data-ttu-id="8d6e6-142">访问特定于非 AllJoyn 网络，例如 Z 批堆栈</span><span class="sxs-lookup"><span data-stu-id="8d6e6-142">Access to non-AllJoyn Network specific , e.g. Z-Wave stack</span></span>

## <a name="adapter-classes"></a><span data-ttu-id="8d6e6-143">适配器类</span><span class="sxs-lookup"><span data-stu-id="8d6e6-143">Adapter Classes</span></span>

<span data-ttu-id="8d6e6-144">下图显示在 Microsoft DSB 模板来创建需要进行桥接到 AllJoyn 的本机设备的抽象，开发人员将使用的类。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-144">The diagram below show the classes developers will use in the Microsoft DSB template to create an abstraction of the native devices that need to be bridged into AllJoyn.</span></span> <span data-ttu-id="8d6e6-145">桥将使用适配器类的实例创建的每个设备的总线附件 Adapter.devices 列表中。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-145">The Bridge will use the instance of the adapter class to create the bus attachments for each device in the Adapter.devices list.</span></span>
![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)

## <a name="special-handlers"></a><span data-ttu-id="8d6e6-147">特殊的处理程序</span><span class="sxs-lookup"><span data-stu-id="8d6e6-147">Special Handlers</span></span>

<span data-ttu-id="8d6e6-148">AllJoyn 指定多个基本服务和标准接口框架，如 LSF、 HAE 或控制面板。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-148">AllJoyn specifies several base services and standard interfaces frameworks such as LSF, HAE or Control Panel.</span></span> <span data-ttu-id="8d6e6-149">DSB 可以公开具有特殊的处理程序。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-149">The DSB can exposes those with special handlers.</span></span> <span data-ttu-id="8d6e6-150">当前版本的 DSB 模板包含 LSF 和控制面板接口的实现。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-150">The current release of the DSB template contains implementations of the LSF and Control Panel interfaces.</span></span> <span data-ttu-id="8d6e6-151">开发人员将其代码连接到在桥中的 LSF 和控制面板接口的回调函数。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-151">Developers will connect their code to the callback functions for LSF and Control Panel interfaces in the bridge.</span></span>

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a><span data-ttu-id="8d6e6-153">DSB 资源</span><span class="sxs-lookup"><span data-stu-id="8d6e6-153">DSB Resources</span></span>

### <a name="visual-studio-dsb-template"></a><span data-ttu-id="8d6e6-154">Visual Studio DSB 模板</span><span class="sxs-lookup"><span data-stu-id="8d6e6-154">Visual Studio DSB Template</span></span>

<span data-ttu-id="8d6e6-155">Visual Studio DSB 模板是可以轻松地创建新 DSB 项目的 Visual Studio 的扩展。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-155">Visual Studio DSB Template is an extension to Visual Studio that lets you easily create new DSB projects.</span></span> <span data-ttu-id="8d6e6-156">项目将创建所有必要组件，如桥用于适配器和所有解决方案文件，以生成作为主或无外设设备 DSB shell 项目。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-156">The project will create all the necessary components such as the Bridge, a shell project for the adapter and all solution files to build the DSB as headed or headless device.</span></span> <span data-ttu-id="8d6e6-157">此 Visual Studio 扩展包含的本机和托管 AllJoyn 设备系统桥的模板。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-157">This Visual Studio extension contains both the Native and Managed AllJoyn Device System Bridge templates.</span></span>

<span data-ttu-id="8d6e6-158">从以下位置下载 DSB 模板：</span><span class="sxs-lookup"><span data-stu-id="8d6e6-158">Download DSB Template from these locations:</span></span>

* [<span data-ttu-id="8d6e6-159">用于 Visual Studio 2015 DSB 模板</span><span class="sxs-lookup"><span data-stu-id="8d6e6-159">DSB Template for Visual Studio 2015</span></span>](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* <span data-ttu-id="8d6e6-160">[Visual Studio 2017 的 DSB 模板](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_DSB 模板也可以通过安装 Visual Studio 工具-> 扩展和更新...-> 联机-> 的"搜索"字段中键入"DSB"。_</span><span class="sxs-lookup"><span data-stu-id="8d6e6-160">[DSB Template for Visual Studio 2017](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_DSB Template can also be installed through Visual Studio Tools -> Extensions and Updates … -> Online -> In the "Search" field type "DSB"._</span></span>

<span data-ttu-id="8d6e6-161">[映射到 AllJoyn DSB 对象](AlljoynDsbApiGuide.md)文档介绍了关键的接口和方法用于生成 Alljoyn 系统桥接。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-161">The [Mapping DSB Objects to AllJoyn](AlljoynDsbApiGuide.md) document describes the key interfaces and methods used to build the Alljoyn System Bridge.</span></span>

### <a name="sample-dsbs"></a><span data-ttu-id="8d6e6-162">示例 DSBs</span><span class="sxs-lookup"><span data-stu-id="8d6e6-162">Sample DSBs</span></span>

* [<span data-ttu-id="8d6e6-163">AllJoyn DSB 模拟适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="8d6e6-163">AllJoyn DSB Mock Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * <span data-ttu-id="8d6e6-164">本教程演示如何使用设备系统 Bridge 应用 IoT Core 设备模拟 BACnet 设备的连接。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-164">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to mock BACnet devices.</span></span>
* [<span data-ttu-id="8d6e6-165">AllJoyn DSB Z 批适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="8d6e6-165">AllJoyn DSB Z-Wave Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * <span data-ttu-id="8d6e6-166">本教程演示如何使用设备系统 Bridge 应用将 IoT Core 设备连接到 Z 波形设备。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-166">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to Z-Wave devices.</span></span>
* [<span data-ttu-id="8d6e6-167">AllJoyn DSB GPIO 适配器教程C++</span><span class="sxs-lookup"><span data-stu-id="8d6e6-167">AllJoyn DSB GPIO Adapter Tutorial C++</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * <span data-ttu-id="8d6e6-168">本教程演示如何使用 AllJoyn 设备系统桥模板创建一个示例C++执行设备 GPIO 的应用。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-168">This tutorial demonstrates how to use the AllJoyn Device System Bridge template to create a sample C++ app that exercises the device GPIO.</span></span>
* [<span data-ttu-id="8d6e6-169">AllJoyn DSB GPIO 适配器教程C#</span><span class="sxs-lookup"><span data-stu-id="8d6e6-169">AllJoyn DSB GPIO Adapter Tutorial C#</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * <span data-ttu-id="8d6e6-170">本教程演示如何使用 AllJoyn 设备系统桥模板来创建执行设备 GPIO 示例托管的应用。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-170">This tutorial demonstrates how to use the AllJoyn Device System Bridge template to create a sample managed app that exercises the device GPIO.</span></span>
* [<span data-ttu-id="8d6e6-171">AllJoyn DSB ZigBee 适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="8d6e6-171">AllJoyn DSB ZigBee Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * <span data-ttu-id="8d6e6-172">本教程演示如何使用设备系统 Bridge 应用将 IoT Core 设备连接到 ZigBee 设备。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-172">This tutorial shows how to use the Device System Bridge app to connect your IoT Core devices to ZigBee devices.</span></span>
* [<span data-ttu-id="8d6e6-173">AllJoyn DSB BACnet 适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="8d6e6-173">AllJoyn DSB BACnet Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * <span data-ttu-id="8d6e6-174">本教程演示如何使用设备系统 Bridge 应用将 IoT Core 设备连接到 BACnet 设备。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-174">This tutorial shows how to use the Device System Bridge app to connect your IoT Core devices to BACnet devices.</span></span>
* [<span data-ttu-id="8d6e6-175">AllJoyn.JS 教程</span><span class="sxs-lookup"><span data-stu-id="8d6e6-175">AllJoyn.JS Tutorial</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * <span data-ttu-id="8d6e6-176">本教程演示如何运行 AllJoyn.JS 由 Allseen 联盟为 Windows 10 应用程序开发的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-176">This tutorial shows how to run AllJoyn.JS application developed by Allseen Alliance as a Windows 10 application.</span></span> <span data-ttu-id="8d6e6-177">AllJoyn.JS 可以编写 JavaScript 将创建、 监视和控制 AllJoyn 的设备。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-177">AllJoyn.JS allows you to write JavaScript to create, monitor and control AllJoyn devices.</span></span>
* [<span data-ttu-id="8d6e6-178">AllJoyn DSB OIC 适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="8d6e6-178">AllJoyn DSB OIC Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * <span data-ttu-id="8d6e6-179">本教程演示如何使用设备系统 Bridge 应用将 IoT Core 设备连接到 IoTivity/OIC 设备。</span><span class="sxs-lookup"><span data-stu-id="8d6e6-179">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to IoTivity/OIC devices.</span></span>
