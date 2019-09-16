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
> <span data-ttu-id="e4e17-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="e4e17-104">You are viewing archived documentation.</span></span> <span data-ttu-id="e4e17-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="e4e17-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="e4e17-106">如有问题，请在 GitHub 上提出问题，或在下面的评论中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="e4e17-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-device-system-bridge"></a><span data-ttu-id="e4e17-107">AllJoyn 设备系统桥</span><span class="sxs-lookup"><span data-stu-id="e4e17-107">AllJoyn Device System Bridge</span></span>

<span data-ttu-id="e4e17-108">AllJoyn 使开发人员可以灵活地使用多种平台和连接技术来构建 AllJoyn 生态系统的设备。</span><span class="sxs-lookup"><span data-stu-id="e4e17-108">AllJoyn provides developers with the flexibility to use a wide range of platforms and connection technologies to build  devices for the AllJoyn ecosystem.</span></span>  <span data-ttu-id="e4e17-109">但是，许多设备制造商在其阵容中都有现有的设备解决方案。</span><span class="sxs-lookup"><span data-stu-id="e4e17-109">However, many device makers have existing device solutions in their portfolios.</span></span> <span data-ttu-id="e4e17-110">在这些情况下，Microsoft 创建了设备系统桥（DSB）。</span><span class="sxs-lookup"><span data-stu-id="e4e17-110">For these situations, Microsoft created the Device System Bridge (DSB).</span></span> <span data-ttu-id="e4e17-111">DSB 将非 AllJoyn 设备调整到了 AllJoyn 生态系统，以便改编后的设备可与 AllJoyn 互操作，作为其公共语言。</span><span class="sxs-lookup"><span data-stu-id="e4e17-111">The DSB adapts non-AllJoyn devices to the AllJoyn ecosystem so that the adapted devices can interoperate with AllJoyn as their common language.</span></span> <span data-ttu-id="e4e17-112">Microsoft DSB 支持家庭自动化系统（如 Zigbee）和 Z-波浪，甚至还支持工业构建自动化系统，例如 BACnet。</span><span class="sxs-lookup"><span data-stu-id="e4e17-112">Microsoft DSB’s support home automation systems such as Zigbee, and Z-Wave, and can even support industrial building automation systems such as BACnet.</span></span>  <span data-ttu-id="e4e17-113">此外，可以自定义源代码以支持其他技术</span><span class="sxs-lookup"><span data-stu-id="e4e17-113">Additionally, the source code is available for customization to support other technologies</span></span>

## <a name="how-dsb-works"></a><span data-ttu-id="e4e17-114">DSB 的工作原理</span><span class="sxs-lookup"><span data-stu-id="e4e17-114">How DSB works</span></span>

<span data-ttu-id="e4e17-115">DSB 的主要功能是在 AllJoyn 总线上创建设备的虚拟表示形式。</span><span class="sxs-lookup"><span data-stu-id="e4e17-115">The key capability of a DSB is to create a virtual representation of devices on the AllJoyn bus.</span></span> <span data-ttu-id="e4e17-116">因此，这些设备的本机连接或设备生态系统都将显示并可作为 AllJoyn 设备进行访问。</span><span class="sxs-lookup"><span data-stu-id="e4e17-116">So these devices, whatever their native connectivity or device ecosystem is, will appear and be accessible as AllJoyn devices.</span></span> <span data-ttu-id="e4e17-117">在下图中，有两个 DSBs，一个用于 Z 波浪，另一个用于 ZigBee 创建两个 Z 波的虚拟表示形式，以及一个 ZigBee 设备在 AllJoyn 总线上的虚拟表示。</span><span class="sxs-lookup"><span data-stu-id="e4e17-117">In the picture below two DSBs , one for Z-Wave and one for ZigBee create virtual representation of the two Z-Wave and the one ZigBee devices on the AllJoyn bus.</span></span> <span data-ttu-id="e4e17-118">在 AllJoyn 站点上，所有设备都可以相互通信。</span><span class="sxs-lookup"><span data-stu-id="e4e17-118">With this all devices on the AllJoyn site can communicate with each other.</span></span> <span data-ttu-id="e4e17-119">因为在 AllJoyn 总线上，ZigBee 设备的所有设备现在都可以相互通信。</span><span class="sxs-lookup"><span data-stu-id="e4e17-119">Because the Z-Wave and ZigBee devices all on the AllJoyn bus they now can communicate with each other as well.</span></span>

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

<span data-ttu-id="e4e17-121">DSB 设计的另一个关键元素是不需要对 AllJoyn 或非 AllJoyn 设备系统进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="e4e17-121">Another key element of the DSB design is that it will not require any changes to the AllJoyn or non-AllJoyn device system.</span></span> <span data-ttu-id="e4e17-122">所有必需的采用都在 DSB 中完成。</span><span class="sxs-lookup"><span data-stu-id="e4e17-122">All necessary adoptions are done in the DSB.</span></span>

<span data-ttu-id="e4e17-123">如图中所示，没有从 AllJoyn 设备到非 AllJoyn 端的映射。</span><span class="sxs-lookup"><span data-stu-id="e4e17-123">As the picture also shows, there is no mapping from AllJoyn devices to the non-AllJoyn side.</span></span> <span data-ttu-id="e4e17-124">DSB 的目标是将设备引入到 AllJoyn 生态系统中。</span><span class="sxs-lookup"><span data-stu-id="e4e17-124">The objective of the DSB is to bring devices into the AllJoyn ecosystem.</span></span> <span data-ttu-id="e4e17-125">仅启用一种方法可简化开发。</span><span class="sxs-lookup"><span data-stu-id="e4e17-125">Enabling only one way simplifies the development.</span></span> <span data-ttu-id="e4e17-126">它还降低了 AllJoyn 安全功能被可能不太安全的非 AllJoyn 设备系统削弱的风险。</span><span class="sxs-lookup"><span data-stu-id="e4e17-126">It also reduces the risk that AllJoyn security capabilities become weakened by the potentially less secure non-AllJoyn device system.</span></span>

## <a name="dsb-architecture"></a><span data-ttu-id="e4e17-127">DSB 体系结构</span><span class="sxs-lookup"><span data-stu-id="e4e17-127">DSB Architecture</span></span>

<span data-ttu-id="e4e17-128">Microsoft 建议的 DSB 体系结构由三个主要组件组成：网络访问堆栈、适配器和桥。</span><span class="sxs-lookup"><span data-stu-id="e4e17-128">The Microsoft proposed DSB architecture consists of three main components, Network Access Stack, Adapter and Bridge.</span></span> <span data-ttu-id="e4e17-129">下图显示了此体系结构的高级概述。</span><span class="sxs-lookup"><span data-stu-id="e4e17-129">The picture below shows the high level overview of this architecture.</span></span>

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a><span data-ttu-id="e4e17-131">Bridge</span><span class="sxs-lookup"><span data-stu-id="e4e17-131">Bridge</span></span>
* <span data-ttu-id="e4e17-132">将每个内部设备对象表示为 AllJoyn 设备，为每个设备提供单独的总线连接</span><span class="sxs-lookup"><span data-stu-id="e4e17-132">Represents each internal device object as AllJoyn device, separate bus attachment for each device</span></span>
* <span data-ttu-id="e4e17-133">设备在 AllJoyn 总线上动态添加或删除</span><span class="sxs-lookup"><span data-stu-id="e4e17-133">Devices are dynamically added to or removed from the AllJoyn bus</span></span>
* <span data-ttu-id="e4e17-134">配置管理设备的可见性和安全性</span><span class="sxs-lookup"><span data-stu-id="e4e17-134">Configuration manages device visibility and security</span></span>
* <span data-ttu-id="e4e17-135">为桥和适配器配置接口创建总线附加</span><span class="sxs-lookup"><span data-stu-id="e4e17-135">Creates bus attachment for bridge and adapter configuration interface</span></span>
* <span data-ttu-id="e4e17-136">桥代码对于内部设备类型不可知，任何类型都可重复使用</span><span class="sxs-lookup"><span data-stu-id="e4e17-136">Bridge code is agnostic to internal device types and reusable for any type</span></span>

### <a name="adapter"></a><span data-ttu-id="e4e17-137">适配器</span><span class="sxs-lookup"><span data-stu-id="e4e17-137">Adapter</span></span>
* <span data-ttu-id="e4e17-138">从非 AllJoyn 网络代表每台设备实例化和管理虚拟设备</span><span class="sxs-lookup"><span data-stu-id="e4e17-138">Instantiates and manages virtual devices on behalf of each device from the non-AllJoyn network</span></span>
* <span data-ttu-id="e4e17-139">将设备架构转换为内部设备对象</span><span class="sxs-lookup"><span data-stu-id="e4e17-139">Translates device schemas into internal device objects</span></span>
* <span data-ttu-id="e4e17-140">管理网络资源，例如访问密钥、凭据</span><span class="sxs-lookup"><span data-stu-id="e4e17-140">Manages network resources, e.g. access keys, credentials</span></span>

### <a name="network-access-stack"></a><span data-ttu-id="e4e17-141">网络访问堆栈</span><span class="sxs-lookup"><span data-stu-id="e4e17-141">Network Access Stack</span></span>
* <span data-ttu-id="e4e17-142">访问特定于非 AllJoyn 网络的权限，例如，Z 波浪堆栈</span><span class="sxs-lookup"><span data-stu-id="e4e17-142">Access to non-AllJoyn Network specific , e.g. Z-Wave stack</span></span>

## <a name="adapter-classes"></a><span data-ttu-id="e4e17-143">适配器类</span><span class="sxs-lookup"><span data-stu-id="e4e17-143">Adapter Classes</span></span>

<span data-ttu-id="e4e17-144">下图显示了开发人员将在 Microsoft DSB 模板中使用的类，以创建需要桥接为 AllJoyn 的本机设备的抽象。</span><span class="sxs-lookup"><span data-stu-id="e4e17-144">The diagram below show the classes developers will use in the Microsoft DSB template to create an abstraction of the native devices that need to be bridged into AllJoyn.</span></span> <span data-ttu-id="e4e17-145">桥将使用适配器类的实例在 "适配器" 列表中为每个设备创建总线附件。</span><span class="sxs-lookup"><span data-stu-id="e4e17-145">The Bridge will use the instance of the adapter class to create the bus attachments for each device in the Adapter.devices list.</span></span>
<span data-ttu-id="e4e17-146">![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)</span><span class="sxs-lookup"><span data-stu-id="e4e17-146">![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)</span></span>

## <a name="special-handlers"></a><span data-ttu-id="e4e17-147">特殊处理程序</span><span class="sxs-lookup"><span data-stu-id="e4e17-147">Special Handlers</span></span>

<span data-ttu-id="e4e17-148">AllJoyn 指定多个基本服务和标准接口框架，如 LSF、HAE 或控制面板。</span><span class="sxs-lookup"><span data-stu-id="e4e17-148">AllJoyn specifies several base services and standard interfaces frameworks such as LSF, HAE or Control Panel.</span></span> <span data-ttu-id="e4e17-149">DSB 可以公开具有特殊处理程序的。</span><span class="sxs-lookup"><span data-stu-id="e4e17-149">The DSB can exposes those with special handlers.</span></span> <span data-ttu-id="e4e17-150">DSB 模板的当前版本包含 "LSF" 和 "控制面板" 接口的实现。</span><span class="sxs-lookup"><span data-stu-id="e4e17-150">The current release of the DSB template contains implementations of the LSF and Control Panel interfaces.</span></span> <span data-ttu-id="e4e17-151">开发人员将其代码连接到桥中的 LSF 和控制面板接口的回调函数。</span><span class="sxs-lookup"><span data-stu-id="e4e17-151">Developers will connect their code to the callback functions for LSF and Control Panel interfaces in the bridge.</span></span>

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a><span data-ttu-id="e4e17-153">DSB 资源</span><span class="sxs-lookup"><span data-stu-id="e4e17-153">DSB Resources</span></span>

### <a name="visual-studio-dsb-template"></a><span data-ttu-id="e4e17-154">Visual Studio DSB 模板</span><span class="sxs-lookup"><span data-stu-id="e4e17-154">Visual Studio DSB Template</span></span>

<span data-ttu-id="e4e17-155">Visual Studio DSB 模板是 Visual Studio 的扩展，可让你轻松地创建新的 DSB 项目。</span><span class="sxs-lookup"><span data-stu-id="e4e17-155">Visual Studio DSB Template is an extension to Visual Studio that lets you easily create new DSB projects.</span></span> <span data-ttu-id="e4e17-156">该项目将创建所有必要的组件，如 Bridge、用于适配器的 shell 项目和所有解决方案文件，以将 DSB 构建为头或无外设设备。</span><span class="sxs-lookup"><span data-stu-id="e4e17-156">The project will create all the necessary components such as the Bridge, a shell project for the adapter and all solution files to build the DSB as headed or headless device.</span></span> <span data-ttu-id="e4e17-157">此 Visual Studio 扩展包含本机和托管的 AllJoyn 设备系统桥接模板。</span><span class="sxs-lookup"><span data-stu-id="e4e17-157">This Visual Studio extension contains both the Native and Managed AllJoyn Device System Bridge templates.</span></span>

<span data-ttu-id="e4e17-158">从以下位置下载 DSB 模板：</span><span class="sxs-lookup"><span data-stu-id="e4e17-158">Download DSB Template from these locations:</span></span>

* [<span data-ttu-id="e4e17-159">Visual Studio 2015 的 DSB 模板</span><span class="sxs-lookup"><span data-stu-id="e4e17-159">DSB Template for Visual Studio 2015</span></span>](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* <span data-ttu-id="e4e17-160">还可以通过 "搜索" 字段类型 "DSB" 中 Visual Studio Tools > 扩展和更新 ...-> Online-> 安装[Visual Studio 2017 DSB 模板](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
的 DSB 模板。</span><span class="sxs-lookup"><span data-stu-id="e4e17-160">[DSB Template for Visual Studio 2017](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_DSB Template can also be installed through Visual Studio Tools -> Extensions and Updates … -> Online -> In the "Search" field type "DSB"._</span></span>

<span data-ttu-id="e4e17-161">将[DSB 对象映射到 alljoyn](AlljoynDsbApiGuide.md)文档介绍用于构建 Alljoyn 系统桥的关键接口和方法。</span><span class="sxs-lookup"><span data-stu-id="e4e17-161">The [Mapping DSB Objects to AllJoyn](AlljoynDsbApiGuide.md) document describes the key interfaces and methods used to build the Alljoyn System Bridge.</span></span>

### <a name="sample-dsbs"></a><span data-ttu-id="e4e17-162">示例 DSBs</span><span class="sxs-lookup"><span data-stu-id="e4e17-162">Sample DSBs</span></span>

* [<span data-ttu-id="e4e17-163">AllJoyn DSB 模拟适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="e4e17-163">AllJoyn DSB Mock Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * <span data-ttu-id="e4e17-164">本教程介绍如何使用设备系统桥应用将 IoT Core 设备连接到模拟 BACnet 设备。</span><span class="sxs-lookup"><span data-stu-id="e4e17-164">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to mock BACnet devices.</span></span>
* [<span data-ttu-id="e4e17-165">AllJoyn DSB Z 波适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="e4e17-165">AllJoyn DSB Z-Wave Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * <span data-ttu-id="e4e17-166">本教程介绍如何使用设备系统桥应用将 IoT 核心设备连接到 Z-a 设备。</span><span class="sxs-lookup"><span data-stu-id="e4e17-166">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to Z-Wave devices.</span></span>
* [<span data-ttu-id="e4e17-167">AllJoyn DSB GPIO 适配器教程C++</span><span class="sxs-lookup"><span data-stu-id="e4e17-167">AllJoyn DSB GPIO Adapter Tutorial C++</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * <span data-ttu-id="e4e17-168">本教程演示如何使用 AllJoyn 设备系统桥模板来创建一个试验设备 GPIO C++的示例应用。</span><span class="sxs-lookup"><span data-stu-id="e4e17-168">This tutorial demonstrates how to use the AllJoyn Device System Bridge template to create a sample C++ app that exercises the device GPIO.</span></span>
* [<span data-ttu-id="e4e17-169">AllJoyn DSB GPIO 适配器教程C#</span><span class="sxs-lookup"><span data-stu-id="e4e17-169">AllJoyn DSB GPIO Adapter Tutorial C#</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * <span data-ttu-id="e4e17-170">本教程演示如何使用 "AllJoyn 设备系统桥" 模板来创建一个试验设备 GPIO 的示例托管应用程序。</span><span class="sxs-lookup"><span data-stu-id="e4e17-170">This tutorial demonstrates how to use the AllJoyn Device System Bridge template to create a sample managed app that exercises the device GPIO.</span></span>
* [<span data-ttu-id="e4e17-171">AllJoyn DSB ZigBee 适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="e4e17-171">AllJoyn DSB ZigBee Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * <span data-ttu-id="e4e17-172">本教程介绍如何使用设备系统桥应用将 IoT Core 设备连接到 ZigBee 设备。</span><span class="sxs-lookup"><span data-stu-id="e4e17-172">This tutorial shows how to use the Device System Bridge app to connect your IoT Core devices to ZigBee devices.</span></span>
* [<span data-ttu-id="e4e17-173">AllJoyn DSB BACnet 适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="e4e17-173">AllJoyn DSB BACnet Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * <span data-ttu-id="e4e17-174">本教程介绍如何使用设备系统桥应用将 IoT Core 设备连接到 BACnet 设备。</span><span class="sxs-lookup"><span data-stu-id="e4e17-174">This tutorial shows how to use the Device System Bridge app to connect your IoT Core devices to BACnet devices.</span></span>
* [<span data-ttu-id="e4e17-175">AllJoyn 教程</span><span class="sxs-lookup"><span data-stu-id="e4e17-175">AllJoyn.JS Tutorial</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * <span data-ttu-id="e4e17-176">本教程介绍如何将 Allseen 联盟开发的 AllJoyn 应用程序作为 Windows 10 应用程序运行。</span><span class="sxs-lookup"><span data-stu-id="e4e17-176">This tutorial shows how to run AllJoyn.JS application developed by Allseen Alliance as a Windows 10 application.</span></span> <span data-ttu-id="e4e17-177">AllJoyn 允许编写 JavaScript 来创建、监视和控制 AllJoyn 设备。</span><span class="sxs-lookup"><span data-stu-id="e4e17-177">AllJoyn.JS allows you to write JavaScript to create, monitor and control AllJoyn devices.</span></span>
* [<span data-ttu-id="e4e17-178">AllJoyn DSB OIC 适配器教程和示例</span><span class="sxs-lookup"><span data-stu-id="e4e17-178">AllJoyn DSB OIC Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * <span data-ttu-id="e4e17-179">本教程介绍如何使用设备系统桥应用将 IoT Core 设备连接到 IoTivity/OIC 设备。</span><span class="sxs-lookup"><span data-stu-id="e4e17-179">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to IoTivity/OIC devices.</span></span>
