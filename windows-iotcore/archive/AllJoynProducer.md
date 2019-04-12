---
title: AllJoyn 生成者
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何通过了解和创作自检 XML 和其不同的功能使 AllJoyn 制造者。
keywords: windows iot AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510749"
---
> [!NOTE]
> <span data-ttu-id="14b95-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="14b95-104">You are viewing archived documentation.</span></span> <span data-ttu-id="14b95-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="14b95-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="14b95-106">如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="14b95-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-producers"></a><span data-ttu-id="14b95-107">AllJoyn 生成者</span><span class="sxs-lookup"><span data-stu-id="14b95-107">AllJoyn Producers</span></span>

<span data-ttu-id="14b95-108">AllJoyn，パ[AllSeen 联盟](https://allseenalliance.org/)，提供了非常棒的框架，用于使已连接的设备和 proximal 网络和 Windows 上的应用程序提供了使用与 AllJoyn 的最佳体验[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)适用于 Visual Studio 扩展。</span><span class="sxs-lookup"><span data-stu-id="14b95-108">AllJoyn, created by the [AllSeen Alliance](https://allseenalliance.org/), provides a great framework for making connected devices and apps on a proximal network, and Windows provides the best experience for using AllJoyn with the [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extension for Visual Studio.</span></span>  <span data-ttu-id="14b95-109">尽管我们的工具擅长于创建生产者和使用者应用程序，从零开始的新 AllJoyn 设备可能非常令人困惑。</span><span class="sxs-lookup"><span data-stu-id="14b95-109">While our tools excel at creating apps for producers and consumers, starting a new AllJoyn device from scratch can be quite confusing.</span></span>

<span data-ttu-id="14b95-110">如果你有建议下一步好连接的设备或用来修补程序和浏览新玩具，可能无法使用其中一个 AllSeen 联盟所提供的标准接口。</span><span class="sxs-lookup"><span data-stu-id="14b95-110">If you have an idea for the next great connected device or a new toy with which to tinker and explore, you may not be able to use one of the standard interfaces offered by the AllSeen Alliance.</span></span>  <span data-ttu-id="14b95-111">如果是这样，然后您需要创建全新的 AllJoyn 制造者。</span><span class="sxs-lookup"><span data-stu-id="14b95-111">If so, then you need to create a brand new AllJoyn producer.</span></span>

<span data-ttu-id="14b95-112">开发人员想要使新 AllJoyn 生成者需要创作自己的自检 XML，但创建自检 XML 需要专业知识和为新开发人员具有重要的学习曲线。</span><span class="sxs-lookup"><span data-stu-id="14b95-112">A developer wanting to make a new AllJoyn producer needs to author their own Introspection XML, but creating Introspection XML requires subject matter expertise and has a significant learning curve for new developers.</span></span>  <span data-ttu-id="14b95-113">这篇博客文章将降低学习难度，通过分解自检 XML 的各种组件，描述的用途和限制每个组件，并在易上手的术语提供很好的示例。</span><span class="sxs-lookup"><span data-stu-id="14b95-113">This blogpost will lower the learning curve by breaking down the various components of Introspection XML, describing the purpose and restrictions of each component, and providing good examples in approachable terms.</span></span>

## <a name="existing-documentation"></a><span data-ttu-id="14b95-114">现有文档</span><span class="sxs-lookup"><span data-stu-id="14b95-114">Existing documentation</span></span>

<span data-ttu-id="14b95-115">对以下资源结合这篇博客文章的粗略检查应加速开发人员了解自检 XML:</span><span class="sxs-lookup"><span data-stu-id="14b95-115">A cursory examination of the following resources combined with this blogpost should accelerate developer understanding of Introspection XML:</span></span>

1. <span data-ttu-id="14b95-116">[AllJoyn 事件和操作 API 指南](https://allseenalliance.org/developers/develop/api-guide/events-and-actions)– AllJoyn 实现的详细信息和概述。</span><span class="sxs-lookup"><span data-stu-id="14b95-116">[AllJoyn Events and Actions API Guide](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn implementation details and overview.</span></span>
2. <span data-ttu-id="14b95-117">[AllJoyn 接口查看板设计准则](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0)-严格结构化和 AllJoyn 自检 XML 的规范。</span><span class="sxs-lookup"><span data-stu-id="14b95-117">[AllJoyn Interface Review Board Design Guidelines](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) - stringent structuring and specification for AllJoyn Introspection XML.</span></span>
3. <span data-ttu-id="14b95-118">[D 总线规范](http://dbus.freedesktop.org/doc/dbus-specification.html)– AllJoyn 基础此规范执行自检 XML。</span><span class="sxs-lookup"><span data-stu-id="14b95-118">[D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn bases Introspection XML on this specification.</span></span>

__<span data-ttu-id="14b95-119">三种类型的自检 XML</span><span class="sxs-lookup"><span data-stu-id="14b95-119">The three types of Introspection XML</span></span>__

<span data-ttu-id="14b95-120">作为您细读 AllJoyn 文档，你会发现三种类型的自检 XML:</span><span class="sxs-lookup"><span data-stu-id="14b95-120">As you peruse AllJoyn documentation, you will find three types of Introspection XML:</span></span>

1. <span data-ttu-id="14b95-121">与数据表示形式的类型格式的 D 总线规范 XML： 开销较低、 进程间通信。</span><span class="sxs-lookup"><span data-stu-id="14b95-121">D-Bus Specification XML: low-overhead, interprocess communication with a type format for data representation.</span></span>
2. <span data-ttu-id="14b95-122">AllJoyn 自检 XML： 通过 D 总线规范 XML 的用于保存时还将 AllJoyn 原则应用于该规范的文字说明的 XML 标记扩展了。</span><span class="sxs-lookup"><span data-stu-id="14b95-122">AllJoyn Introspection XML: extends D-Bus Specification XML with XML tags for holding textual descriptions while also applying AllJoyn principles to the specification.</span></span>
3. <span data-ttu-id="14b95-123">扩展 AllJoyn 自检 XML： 经典自检 XML 引入的发展进行命名的结构和字典类型。</span><span class="sxs-lookup"><span data-stu-id="14b95-123">Extended AllJoyn Introspection XML: evolution of classic Introspection XML introducing named types for structures and dictionaries.</span></span>

<span data-ttu-id="14b95-124">AllJoyn Studio 当前支持 D 总线规范 XML 和 AllJoyn 自检 XML;此博客将决定如何创建和窗体 AllJoyn 自检 XML。</span><span class="sxs-lookup"><span data-stu-id="14b95-124">AllJoyn Studio currently supports D-Bus Specification XML and AllJoyn Introspection XML; this blog will dictate how to create and form AllJoyn Introspection XML.</span></span>  <span data-ttu-id="14b95-125">AllSeen 联盟接口查看板 (IRB) 使用新的扩展 AllJoyn 自检作为格式以标准化的意见的正式提交但正在努力不久的将来统一的自检 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="14b95-125">The AllSeen Alliance's Interface Review Board (IRB) uses the new Extended AllJoyn Introspection as the format for formal submissions for standardization reviews but is working on a unified introspection XML format for the near future.</span></span>

## <a name="introspection-high-level-overview"></a><span data-ttu-id="14b95-126">自检高级别概述</span><span class="sxs-lookup"><span data-stu-id="14b95-126">Introspection High Level Overview</span></span>

<span data-ttu-id="14b95-127">每个 AllJoyn 制造者公开公布自检 XML 呈现生成者的受支持的功能 – 接口作为所述通过信号、 属性和方法。</span><span class="sxs-lookup"><span data-stu-id="14b95-127">Every AllJoyn producer publicly advertises an Introspection XML that surfaces the producer's supported functionality – interfaces as described via signals, properties and methods.</span></span>  <span data-ttu-id="14b95-128">代码生成解决方案，如所示 AllJoyn Studio 扩展中，依赖于自检 XML 创建必要的代码以加快开发速度。</span><span class="sxs-lookup"><span data-stu-id="14b95-128">Code Generation solutions, like the one in the AllJoyn Studio extension, rely on Introspection XML to create the necessary code to accelerate development.</span></span>  <span data-ttu-id="14b95-129">这样，两个不同的制造商可以使用 XML 来实现制造者具有相同功能，自检 XML 的非不明确的可读的方式描述的功能的生成者。</span><span class="sxs-lookup"><span data-stu-id="14b95-129">Introspection XML describes the functionality of a producer in a non-ambiguous, human-readable way such that two different manufacturers can use the XML to implement a producer with the same functionality.</span></span>  <span data-ttu-id="14b95-130">通过相同的令牌，AllJoyn 制造者没有上一个熟悉的开发人员应该能够针对该生成者根据其 XML 进行开发。</span><span class="sxs-lookup"><span data-stu-id="14b95-130">By the same token, developers with no previous knowledge of an AllJoyn producer should be able to develop against that producer based on its XML.</span></span>

__<span data-ttu-id="14b95-131">AllJoyn Interfaces</span><span class="sxs-lookup"><span data-stu-id="14b95-131">AllJoyn Interfaces</span></span>__

<span data-ttu-id="14b95-132">AllJoyn 通过分解为各种"接口"表示不同的行为和功能的逻辑分组的自检 XML 完成此操作。</span><span class="sxs-lookup"><span data-stu-id="14b95-132">AllJoyn accomplishes this by breaking an Introspection XML into various "interfaces" that represent different logical groupings of behavior and capabilities.</span></span>  <span data-ttu-id="14b95-133">使用反向 DNS 约定命名 AllJoyn 接口。</span><span class="sxs-lookup"><span data-stu-id="14b95-133">AllJoyn interfaces are named using a reverse-DNS convention.</span></span> <span data-ttu-id="14b95-134">例如，Contoso Ltd.，后者拥有 contoso.com 域，通过创建的接口"Foo"界面将写为：</span><span class="sxs-lookup"><span data-stu-id="14b95-134">For example, the interface "Foo" interface created by Contoso Ltd., which owns the contoso.com domain, would be written as:</span></span>

    <interface name="com.contoso.Foo">

<span data-ttu-id="14b95-135">生成者可能会实现任何数量的接口，但必须实现一个接口，它们将播发的每个组件。</span><span class="sxs-lookup"><span data-stu-id="14b95-135">A producer may implement any number of interfaces, but must implement every component of an interface that they advertise.</span></span>  <span data-ttu-id="14b95-136">为了区分和扩展行为，AllJoyn 支持与现有的接口层次结构; 创建新接口即`com.contoso.Foo.Bar`定义的情况下的新功能`Foo.Bar`类别，但没有任何显式依赖关系`com.contoso.Foo`接口。</span><span class="sxs-lookup"><span data-stu-id="14b95-136">In order to differentiate and extend behaviors, AllJoyn supports creating new interfaces with respect to an existing interface hierarchy; i.e. `com.contoso.Foo.Bar` defines new capabilities for things under the `Foo.Bar` category but doesn't have any explicit dependencies on the `com.contoso.Foo` interface.</span></span> 

<span data-ttu-id="14b95-137">有关示例，我们有两个接口：`com.contoso.Sensor`和`com.contoso.Sensor.Humidity`–"湿度"逻辑上属于"传感器"类别下。</span><span class="sxs-lookup"><span data-stu-id="14b95-137">For an example, we have two interfaces: `com.contoso.Sensor` and `com.contoso.Sensor.Humidity` – "Humidity" logically falls under the "Sensor" category.</span></span>  <span data-ttu-id="14b95-138">有人开发湿度制造者可以选择以支持只需`com.contoso.Sensor.Humdity`接口，但它们还可以选择以支持`com.contoso.Sensor`接口。</span><span class="sxs-lookup"><span data-stu-id="14b95-138">Someone developing a Humidity producer could choose to support just the `com.contoso.Sensor.Humdity` interface, but they could also choose to support the `com.contoso.Sensor` interface.</span></span>  <span data-ttu-id="14b95-139">无论如何，如果他们在广告接口，然后生成者必须支持其所有功能。</span><span class="sxs-lookup"><span data-stu-id="14b95-139">Regardless, if they advertise an interface, then producers must support all of its functions.</span></span>

<span data-ttu-id="14b95-140">`<description>`标记用于描述接口、 功能和自变量，并可本地化为多种语言。</span><span class="sxs-lookup"><span data-stu-id="14b95-140">The `<description>` tag is used to describe interfaces, capabilities and arguments, and can be localized for various languages.</span></span>  <span data-ttu-id="14b95-141">自由使用`<description>`标记使 XML 更易于理解，并删除二义性。</span><span class="sxs-lookup"><span data-stu-id="14b95-141">Liberal use of the `<description>` tag makes the XML more understandable and removes ambiguity.</span></span>

<span data-ttu-id="14b95-142">标准做法将指示使用`org.alljoyn.Bus.Secure`实现安全和身份验证的接口上的批注。</span><span class="sxs-lookup"><span data-stu-id="14b95-142">Standard practice dictates the use of the `org.alljoyn.Bus.Secure` annotation on an interface to enable security and authentication.</span></span>  <span data-ttu-id="14b95-143">对于强身份验证，使用预共享的密钥 (PSK) 或证书密钥交换 (ECDSA)。</span><span class="sxs-lookup"><span data-stu-id="14b95-143">For strong authentication, use a pre-shared key (PSK) or a certificate key exchange (ECDSA).</span></span>  <span data-ttu-id="14b95-144">否则，"null"身份验证将成为默认行为。</span><span class="sxs-lookup"><span data-stu-id="14b95-144">Otherwise, a "null" authentication becomes the default behavior.</span></span>  <span data-ttu-id="14b95-145">**在实现中，不能是声明发生实际的身份验证机制**。</span><span class="sxs-lookup"><span data-stu-id="14b95-145">**The actual authentication mechanism happens in implementation, not the declaration**.</span></span> <span data-ttu-id="14b95-146">此批注可以启用安全保护，但未指定使用的安全类型或它的实现方式。</span><span class="sxs-lookup"><span data-stu-id="14b95-146">This annotation enables security but does not specify the type of security used or how it will be implemented.</span></span>

___<span data-ttu-id="14b95-147">示例</span><span class="sxs-lookup"><span data-stu-id="14b95-147">Example</span></span>___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <annotation name="org.allJoyn.Bus.Secure" value="true" />
 
    <description language="en">
 
      Private interface for a Door the consumer owns. 
 
    </description>
 
  </interface>
 
</node>
```

<span data-ttu-id="14b95-148">此示例显示了由设备公开的接口： `com.example.Door.PrivateDoor`。</span><span class="sxs-lookup"><span data-stu-id="14b95-148">This example shows an interface exposed by a device: `com.example.Door.PrivateDoor`.</span></span> <span data-ttu-id="14b95-149">在接口的范围内，我们所关注的唯一操作是机制的使用该接口，未使用哪种类型时，是否应受保护的通信。</span><span class="sxs-lookup"><span data-stu-id="14b95-149">In the scope of the interface, the only thing we're concerned about is whether communication should be secured when using that interface, not what type of mechanism is being used.</span></span>

__<span data-ttu-id="14b95-150">界面功能</span><span class="sxs-lookup"><span data-stu-id="14b95-150">Interface Capabilities</span></span>__

<span data-ttu-id="14b95-151">接口声明三个接口成员使用其功能： 方法、 属性或信号。</span><span class="sxs-lookup"><span data-stu-id="14b95-151">Interfaces declare their capabilities with three interface members: methods, properties, or signals.</span></span> <span data-ttu-id="14b95-152">自检 XML 还支持批注来描述其他功能或约束。</span><span class="sxs-lookup"><span data-stu-id="14b95-152">Introspection XML also supports annotations that describe additional functionality or constraints.</span></span>  <span data-ttu-id="14b95-153">这些功能使用 UpperCamelCase 表示法，而自变量使用 lowerCamelCase 表示法。</span><span class="sxs-lookup"><span data-stu-id="14b95-153">These capabilities use UpperCamelCase notation while arguments use lowerCamelCase notation.</span></span>

### <a name="argument-types"></a><span data-ttu-id="14b95-154">参数类型</span><span class="sxs-lookup"><span data-stu-id="14b95-154">Argument Types</span></span>

<span data-ttu-id="14b95-155">接口成员发送和接收参数为由一个 ASCII 类型代码。</span><span class="sxs-lookup"><span data-stu-id="14b95-155">Interface members send and receive arguments denoted by an ASCII type-code.</span></span>  <span data-ttu-id="14b95-156">根据接口成员的类型，自变量可能已被发送到制造者从使用者 (方向 ="out") 或从使用者流向生成者 (方向 ="in")。</span><span class="sxs-lookup"><span data-stu-id="14b95-156">Depending on the type of interface member, arguments may have be sent to the producer from the consumer (direction="out") or from the consumer to the producer (direction="in").</span></span>  <span data-ttu-id="14b95-157">下表提供了常用的类型的简要概述：</span><span class="sxs-lookup"><span data-stu-id="14b95-157">The following table provides a brief overview of commonly used types:</span></span>

> | *<span data-ttu-id="14b95-158">传统的名称</span><span class="sxs-lookup"><span data-stu-id="14b95-158">Conventional Name</span></span>* | *<span data-ttu-id="14b95-159">Type-Code</span><span class="sxs-lookup"><span data-stu-id="14b95-159">Type-Code</span></span>* | *<span data-ttu-id="14b95-160">将</span><span class="sxs-lookup"><span data-stu-id="14b95-160">Use</span></span>* |
> |----------------- |---------| --- |
> |**<span data-ttu-id="14b95-161">一个布尔值</span><span class="sxs-lookup"><span data-stu-id="14b95-161">BOOLEAN</span></span>** | <span data-ttu-id="14b95-162">b</span><span class="sxs-lookup"><span data-stu-id="14b95-162">b</span></span> | <span data-ttu-id="14b95-163">表示 TRUE (1) 或 FALSE (0)。</span><span class="sxs-lookup"><span data-stu-id="14b95-163">Represents TRUE (1) or FALSE (0).</span></span> <span data-ttu-id="14b95-164">用于简单的二进制信息或状态。</span><span class="sxs-lookup"><span data-stu-id="14b95-164">Used for simple binary information or states.</span></span> |
> |**<span data-ttu-id="14b95-165">BYTE</span><span class="sxs-lookup"><span data-stu-id="14b95-165">BYTE</span></span>** | <span data-ttu-id="14b95-166">y</span><span class="sxs-lookup"><span data-stu-id="14b95-166">y</span></span> | <span data-ttu-id="14b95-167">介于 0 到 255 之间的整数值。</span><span class="sxs-lookup"><span data-stu-id="14b95-167">Integer value from 0 to 255.</span></span> <span data-ttu-id="14b95-168">在处理小正数和负数时使用。</span><span class="sxs-lookup"><span data-stu-id="14b95-168">Used when dealing with small positive numbers.</span></span> |
> |**<span data-ttu-id="14b95-169">UINT16</span><span class="sxs-lookup"><span data-stu-id="14b95-169">UINT16</span></span>** | <span data-ttu-id="14b95-170">q</span><span class="sxs-lookup"><span data-stu-id="14b95-170">q</span></span> | <span data-ttu-id="14b95-171">整数值从 0 到 2 ^16 1</span><span class="sxs-lookup"><span data-stu-id="14b95-171">Integer value from 0 to 2^16 - 1</span></span> |
> |**<span data-ttu-id="14b95-172">UINT32</span><span class="sxs-lookup"><span data-stu-id="14b95-172">UINT32</span></span>** | <span data-ttu-id="14b95-173">u</span><span class="sxs-lookup"><span data-stu-id="14b95-173">u</span></span> | <span data-ttu-id="14b95-174">整数值从 0 到 2 ^32-1</span><span class="sxs-lookup"><span data-stu-id="14b95-174">Integer value from 0 to 2^32 - 1</span></span> |
> |**<span data-ttu-id="14b95-175">UINT64</span><span class="sxs-lookup"><span data-stu-id="14b95-175">UINT64</span></span>** | <span data-ttu-id="14b95-176">的 VPN 连接下</span><span class="sxs-lookup"><span data-stu-id="14b95-176">t</span></span> | <span data-ttu-id="14b95-177">整数值从 0 到 2 ^64-1</span><span class="sxs-lookup"><span data-stu-id="14b95-177">Integer value from 0 to 2^64 - 1</span></span> |
> |**<span data-ttu-id="14b95-178">INT16</span><span class="sxs-lookup"><span data-stu-id="14b95-178">INT16</span></span>** | <span data-ttu-id="14b95-179">n</span><span class="sxs-lookup"><span data-stu-id="14b95-179">n</span></span> | <span data-ttu-id="14b95-180">从 –(2^15) 的整数值为 2 ^15-1</span><span class="sxs-lookup"><span data-stu-id="14b95-180">Integer value from –(2^15) to 2^15 - 1</span></span> |
> |**<span data-ttu-id="14b95-181">INT32</span><span class="sxs-lookup"><span data-stu-id="14b95-181">INT32</span></span>** | <span data-ttu-id="14b95-182">图标</span><span class="sxs-lookup"><span data-stu-id="14b95-182">i</span></span> | <span data-ttu-id="14b95-183">从 –(2^31) 的整数值为 2 ^31-1</span><span class="sxs-lookup"><span data-stu-id="14b95-183">Integer value from –(2^31) to 2^31 - 1</span></span> |
> |**<span data-ttu-id="14b95-184">INT64</span><span class="sxs-lookup"><span data-stu-id="14b95-184">INT64</span></span>** | <span data-ttu-id="14b95-185">x</span><span class="sxs-lookup"><span data-stu-id="14b95-185">x</span></span> | <span data-ttu-id="14b95-186">从 –(2^63) 的整数值为 2 ^63-1</span><span class="sxs-lookup"><span data-stu-id="14b95-186">Integer value from –(2^63) to 2^63 - 1</span></span> |
> |**<span data-ttu-id="14b95-187">双精度</span><span class="sxs-lookup"><span data-stu-id="14b95-187">DOUBLE</span></span>** | <span data-ttu-id="14b95-188">d</span><span class="sxs-lookup"><span data-stu-id="14b95-188">d</span></span> | <span data-ttu-id="14b95-189">精度浮点数从 –(2^127) 到 2 ^127 1</span><span class="sxs-lookup"><span data-stu-id="14b95-189">Precision floating point numbers from –(2^127) to 2^127 - 1</span></span> |
> |**<span data-ttu-id="14b95-190">STRING</span><span class="sxs-lookup"><span data-stu-id="14b95-190">STRING</span></span>** | <span data-ttu-id="14b95-191">文件</span><span class="sxs-lookup"><span data-stu-id="14b95-191">s</span></span> | <span data-ttu-id="14b95-192">Utf-8 字符串</span><span class="sxs-lookup"><span data-stu-id="14b95-192">UTF-8 string</span></span> |
 
<span data-ttu-id="14b95-193">有关所有受支持的类型的更详尽概述，请参阅[此处](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448)。</span><span class="sxs-lookup"><span data-stu-id="14b95-193">For a more exhaustive overview of all the supported types, see [here](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span></span>

<span data-ttu-id="14b95-194">撰写本文时，尽可能使用 SI 单位和清楚地表示预期的单位。</span><span class="sxs-lookup"><span data-stu-id="14b95-194">As of this writing, use SI units where possible and clearly denote intended units.</span></span> <span data-ttu-id="14b95-195">如果可能，请选择类型代码的限制性最强到你的方案;例如，如果你代表一个人的年龄的年数，然后使用字节、 不 UINT16 或 INT16，因为任何人都不负年龄或多个到 255 岁。</span><span class="sxs-lookup"><span data-stu-id="14b95-195">When possible, choose the type-code most restrictive to your scenario; e.g., if you are representing a person's age in years, then use BYTE, not UINT16 or INT16, since no one will be a negative age or more than 255 years old.</span></span>  <span data-ttu-id="14b95-196">最新版本，应始终遵循[AllJoyn 接口查看板 (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board)指导原则。</span><span class="sxs-lookup"><span data-stu-id="14b95-196">Always follow the latest [AllJoyn Interface Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) guidelines.</span></span>

<span data-ttu-id="14b95-197">下表总结了常见的单位：</span><span class="sxs-lookup"><span data-stu-id="14b95-197">The following table summarizes common units:</span></span>


> |*<span data-ttu-id="14b95-198">数量</span><span class="sxs-lookup"><span data-stu-id="14b95-198">Quantity</span></span>* | *<span data-ttu-id="14b95-199">单位</span><span class="sxs-lookup"><span data-stu-id="14b95-199">Unit</span></span>*|
> |-------- | ---- |
> |**<span data-ttu-id="14b95-200">绝对时间 （日期和时间）</span><span class="sxs-lookup"><span data-stu-id="14b95-200">Absolute time (date & time)</span></span>** | <span data-ttu-id="14b95-201">自 UNIX epoch 起经过的秒 (00: 00:00 自 1970 年 1 月 1 日)</span><span class="sxs-lookup"><span data-stu-id="14b95-201">Seconds since UNIX Epoch (00:00:00 on January 1, 1970)</span></span> |
> |**<span data-ttu-id="14b95-202">当天的时间</span><span class="sxs-lookup"><span data-stu-id="14b95-202">Time of Day</span></span>** | <span data-ttu-id="14b95-203">自午夜以来的秒</span><span class="sxs-lookup"><span data-stu-id="14b95-203">Seconds since midnight</span></span> |
> |**<span data-ttu-id="14b95-204">时间间隔</span><span class="sxs-lookup"><span data-stu-id="14b95-204">Time interval</span></span>** | <span data-ttu-id="14b95-205">秒</span><span class="sxs-lookup"><span data-stu-id="14b95-205">Seconds</span></span> |
> |**<span data-ttu-id="14b95-206">带宽</span><span class="sxs-lookup"><span data-stu-id="14b95-206">Bandwidth</span></span>** | <span data-ttu-id="14b95-207">每秒位数</span><span class="sxs-lookup"><span data-stu-id="14b95-207">Bits per second</span></span> |
> |**<span data-ttu-id="14b95-208">数据大小</span><span class="sxs-lookup"><span data-stu-id="14b95-208">Data size</span></span>** | <span data-ttu-id="14b95-209">字节</span><span class="sxs-lookup"><span data-stu-id="14b95-209">Bytes</span></span> |
 
### <a name="methods"></a><span data-ttu-id="14b95-210">方法</span><span class="sxs-lookup"><span data-stu-id="14b95-210">Methods</span></span>

<span data-ttu-id="14b95-211">使用者调用方法以修改状态的生成者，并且其名称应以动词开头，因为它们代表生成者执行操作的请求。</span><span class="sxs-lookup"><span data-stu-id="14b95-211">Consumers call methods to modify the state of a producer, and their names should start with a verb because they represent requests for the producer to perform an action.</span></span>  <span data-ttu-id="14b95-212">方法可能具有输入和输出自变量;在没有返回消息需要发送的情况下，将应用的批注"org.freedesktop.DBus.Method.NoReply"。</span><span class="sxs-lookup"><span data-stu-id="14b95-212">Methods may have input and output arguments; in the case that no return message needs to be sent, apply the annotation "org.freedesktop.DBus.Method.NoReply".</span></span>  <span data-ttu-id="14b95-213">但是，AllJoyn 方法通常返回 SuccessResult 或 FailureResult，让使用者反馈有关方法调用。</span><span class="sxs-lookup"><span data-stu-id="14b95-213">However, AllJoyn methods normally return a SuccessResult or a FailureResult, giving consumers feedback about the method call.</span></span>  <span data-ttu-id="14b95-214">参数的类型必须符合[D 总线规范](http://dbus.freedesktop.org/doc/dbus-specification.html)。</span><span class="sxs-lookup"><span data-stu-id="14b95-214">The type of the arguments must comply with the [D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html).</span></span> 

___<span data-ttu-id="14b95-215">示例 （不包括为方便起见接口信息）</span><span class="sxs-lookup"><span data-stu-id="14b95-215">Example (excluding interface information for convenience)</span></span>___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!-- Method showing arguments with only directions in -->
 
    <method name="SetPasscode">
 
      <description language="en">
 
        Allows owner of the door to change the code needed to unlock it.
 
      </description>
 
      <argument name="currentPasscode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="newPasscode" type="u" direction="in">
 
        <description language="en">
 
          New code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!-- Method showing both arguments in and out -->
 
    <method name="UnlockDoor">
 
      <description language="en">
 
        Allows guests with the code to unlock the door.
 
      </description>
 
      <argument name="passcode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="welcomeMessage" type="s" direction="out">
 
        <description language="en">
 
          Message from the owner of the door.
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
</node>
```

*<span data-ttu-id="14b95-216">注意：在大多数情况下，属性应该用于而不是方法访问生成者的状态 （例如，而不是 GetColor 方法使用的颜色属性）。</span><span class="sxs-lookup"><span data-stu-id="14b95-216">Note: In most cases, properties should be used instead of methods to access a producer's state (e.g., use a Color property instead of a GetColor method).</span></span>*

### <a name="properties"></a><span data-ttu-id="14b95-217">属性</span><span class="sxs-lookup"><span data-stu-id="14b95-217">Properties</span></span>

<span data-ttu-id="14b95-218">属性主要是允许访问生成者的状态。</span><span class="sxs-lookup"><span data-stu-id="14b95-218">Properties mainly allow access to a producer's state.</span></span>  <span data-ttu-id="14b95-219">虽然属性从技术上讲的访问值为"读取"、"readwrite"或"写入"，状态修改功能通常属于方法 – 这种情况下，开发人员应尽可能将属性保留为"读取"和"readwrite"仅当使用状态表示该属性是独立于所有其他属性。</span><span class="sxs-lookup"><span data-stu-id="14b95-219">While properties technically have access values of "read", "readwrite", or "write", state-modifying functionality generally belongs to methods – as such, developers should strive to keep properties as "read" and use "readwrite" only when the state represented by that property is independent of all other properties.</span></span>  <span data-ttu-id="14b95-220">属性应永远不会是只是"写入"-修改而无需观察状态是方法的角色。</span><span class="sxs-lookup"><span data-stu-id="14b95-220">Properties should never be just "write" – modifying the state without observation is the role of methods.</span></span>

<span data-ttu-id="14b95-221">其值更改时，必须对警报的使用者进行批注的属性 （或者，属性可以继承此批注及其父接口）。</span><span class="sxs-lookup"><span data-stu-id="14b95-221">Properties must be annotated to alert consumers when their values change (optionally, properties can inherit this annotation from its parent interface).</span></span>  <span data-ttu-id="14b95-222">批注`org.freedesktop.DBus.Property.EmitsChangedSignal`可以有四个值：</span><span class="sxs-lookup"><span data-stu-id="14b95-222">The annotation `org.freedesktop.DBus.Property.EmitsChangedSignal` can have four values:</span></span>

* <span data-ttu-id="14b95-223">"true"– 当属性更改，生成者将发出信号表示已更改的属性和新值。</span><span class="sxs-lookup"><span data-stu-id="14b95-223">"true" – when the property changes, the producer will emit a signal denoting the changed property and the new value.</span></span> <span data-ttu-id="14b95-224">使用中经常使用，需要 active 监督，如门"LockState"的属性。</span><span class="sxs-lookup"><span data-stu-id="14b95-224">Used in properties that are frequently used and require active oversight, such as a "LockState" for a door.</span></span>
* <span data-ttu-id="14b95-225">"使"– 当属性更改，生成者将发出信号表示已更改的属性，但不是新值。</span><span class="sxs-lookup"><span data-stu-id="14b95-225">"invalidates" – when the property changes, the producer will emit a signal denoting the changed property but not the new value.</span></span> <span data-ttu-id="14b95-226">属性不需要大量监督 （如"WashMode"衣服干燥器的) 或表示大量的数据，如容器中使用。</span><span class="sxs-lookup"><span data-stu-id="14b95-226">Used in properties that don't require heavy oversight (such as the "WashMode" of a clothes dryer) or represent a lot of data, such as a container.</span></span>
* <span data-ttu-id="14b95-227">"false"– 当属性更改，生成者发出没有信号。</span><span class="sxs-lookup"><span data-stu-id="14b95-227">"false" – when the property changes, the producer emits no signal.</span></span> <span data-ttu-id="14b95-228">在更新速度快，如跟踪人乘客地铁地铁门上的"TransitCounter"属性的属性中使用。</span><span class="sxs-lookup"><span data-stu-id="14b95-228">Used in properties that update rapidly, such as a "TransitCounter" property on a subway turnstile tracking people boarding the subway.</span></span> <span data-ttu-id="14b95-229">如果未指定，AllJoyn 属性将使用此为默认值。</span><span class="sxs-lookup"><span data-stu-id="14b95-229">If unspecified, AllJoyn properties use this as default.</span></span>
* <span data-ttu-id="14b95-230">"const"– 该属性将永远不会更改值并永远不会发出已更改的信号。</span><span class="sxs-lookup"><span data-stu-id="14b95-230">"const" – the property will never change value and never emit a changed signal.</span></span> <span data-ttu-id="14b95-231">这将是 AllJoyn 16.04 版本; 中引入到那时，使用"true"。</span><span class="sxs-lookup"><span data-stu-id="14b95-231">This will be introduced in the AllJoyn 16.04 release; until then, use "true".</span></span>

___<span data-ttu-id="14b95-232">示例</span><span class="sxs-lookup"><span data-stu-id="14b95-232">Example</span></span>___

<span data-ttu-id="14b95-233">基于前面的示例扩展，我们进行了修改 XML 以包括属性 （不包括为简洁起见方法）。</span><span class="sxs-lookup"><span data-stu-id="14b95-233">Expanding upon the previous example, we have modified the XML to include properties (excluding the methods for brevity).</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Read property that sends a signal when the value changes -->
 
    <property name="IsLocked" type="b" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door may freely lock and unlock the door.
 
      </description>
 
    </property>  
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!—- Read-only property that never sends a signal and never changes -->
 
    <property name="Owner" type="s" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door is public knowledge.
 
      </description>
 
    </property>
 
  </interface>
 
</node>
```

### <a name="signals"></a><span data-ttu-id="14b95-234">信号</span><span class="sxs-lookup"><span data-stu-id="14b95-234">Signals</span></span>

<span data-ttu-id="14b95-235">使用信号以通知使用者通过查询生成者无法确定的事件。</span><span class="sxs-lookup"><span data-stu-id="14b95-235">Use signals to inform consumers of an event that they could not determine by querying the producer.</span></span>  <span data-ttu-id="14b95-236">将通过使用"true"EmitsChangedProperty 批注的生成者的 DoorOpen 属性传达门打开。</span><span class="sxs-lookup"><span data-stu-id="14b95-236">A door opening would be conveyed through a producer's DoorOpen property with a "true" EmitsChangedProperty annotation.</span></span>  <span data-ttu-id="14b95-237">某人通过门，但是，不能从派生的任何属性更改，因此这将使好独立信号。</span><span class="sxs-lookup"><span data-stu-id="14b95-237">Someone passing through the door, however, cannot be derived from any property changes, so this would make a good standalone signal.</span></span>  <span data-ttu-id="14b95-238">我们之所以将这些类型的事件为"无状态"。</span><span class="sxs-lookup"><span data-stu-id="14b95-238">We refer to these kinds of events as "stateless".</span></span>  <span data-ttu-id="14b95-239">由于信号是从生成者到使用者是单向的它们可以仅包含"out"参数。</span><span class="sxs-lookup"><span data-stu-id="14b95-239">Since signals are unidirectional from producer to consumer, they can only contain "out" arguments.</span></span>

___<span data-ttu-id="14b95-240">示例</span><span class="sxs-lookup"><span data-stu-id="14b95-240">Examples</span></span>___ 

<span data-ttu-id="14b95-241">（不包括方法和属性，为方便起见:）</span><span class="sxs-lookup"><span data-stu-id="14b95-241">(excluding methods and properties for convenience):</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Signals may contain arguments about non-state information -->
 
    <signal name="ThresholdCrossed" sessioncast="true">
 
      <description>
 
        Signal to notify owner whenever anyone passes through the door.
 
      </description>
 
      <argument name="crossedInward" type="b" direction="out">
 
        If true, someone entered; if false, someone left.
 
      </argument>
 
    </signal>
 
  </interface>
 
</node>
```

<span data-ttu-id="14b95-242">由于信号有此类窄的范围，通常很少出现在生成者的 XML。</span><span class="sxs-lookup"><span data-stu-id="14b95-242">Since signals have such a narrow scope, typically few appear in a producer's XML.</span></span>

### <a name="containers"></a><span data-ttu-id="14b95-243">容器</span><span class="sxs-lookup"><span data-stu-id="14b95-243">Containers</span></span>

<span data-ttu-id="14b95-244">不执行操作将多个自变量组合到一系列复杂类似于序列化的 JSON 字符串。</span><span class="sxs-lookup"><span data-stu-id="14b95-244">Do not combine multiple arguments into a complex collection like a serialized JSON string.</span></span> <span data-ttu-id="14b95-245">D 总线规范可用于容器的数据 – 结构、 数组、 变体和 DICT_ENTRY 等。</span><span class="sxs-lookup"><span data-stu-id="14b95-245">The D-Bus specification makes affordances for containers of data – STRUCT, ARRAY, VARIANT, and DICT_ENTRY.</span></span>  <span data-ttu-id="14b95-246">使用这些设备需要多个基本类型的参数传递。</span><span class="sxs-lookup"><span data-stu-id="14b95-246">Use these to pass arguments that require more than basic types.</span></span>

___<span data-ttu-id="14b95-247">变体</span><span class="sxs-lookup"><span data-stu-id="14b95-247">VARIANT</span></span>___

<span data-ttu-id="14b95-248">变体类型"v"表示，并且可以包含任何[单一完整类型](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type)。</span><span class="sxs-lookup"><span data-stu-id="14b95-248">VARIANTs are denoted by the type "v" and can contain any [single complete type](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span></span> <span data-ttu-id="14b95-249">但是，变体应尽可能避免因为它们将不明确添加到 XML 定义。</span><span class="sxs-lookup"><span data-stu-id="14b95-249">However, VARIANTs should be avoided whenever possible because they add ambiguity to XML definitions.</span></span>

___<span data-ttu-id="14b95-250">结构</span><span class="sxs-lookup"><span data-stu-id="14b95-250">STRUCT</span></span>___

<span data-ttu-id="14b95-251">结构使用"（"和"）"来表示的开头和结尾的一种数据结构 – 单个完整的类型。</span><span class="sxs-lookup"><span data-stu-id="14b95-251">STRUCTs use "(" and ")" to denote the beginning and end of a data structure – a single complete type.</span></span>  <span data-ttu-id="14b95-252">可以嵌套这些数据结构。</span><span class="sxs-lookup"><span data-stu-id="14b95-252">These data structures may be nested.</span></span>

<span data-ttu-id="14b95-253">示例：</span><span class="sxs-lookup"><span data-stu-id="14b95-253">Examples:</span></span>

<span data-ttu-id="14b95-254">一种类型的"(iii)"表示三个整数; 的结构"(i(ii))"表示一个整数的结构和两个整数的结构不同于类型"((ii) 我)"。</span><span class="sxs-lookup"><span data-stu-id="14b95-254">A type of "(iii)" denotes a structure of three integers; "(i(ii))" denotes a STRUCT of an integer and a STRUCT of two integers, which is distinct from the type "((ii)i)".</span></span>

___<span data-ttu-id="14b95-255">数组</span><span class="sxs-lookup"><span data-stu-id="14b95-255">ARRAY</span></span>___

<span data-ttu-id="14b95-256">数组使用的类型代码"a"和后面必须有一个完整的类型。</span><span class="sxs-lookup"><span data-stu-id="14b95-256">ARRAYs use the type code "a" and must be followed by a single complete type.</span></span>  <span data-ttu-id="14b95-257">数组不具有组长度，因此它们是类似于列表数据结构。</span><span class="sxs-lookup"><span data-stu-id="14b95-257">ARRAYs do not have set lengths, so they are similar to a list data structure.</span></span> <span data-ttu-id="14b95-258">数组表示一个完整的类型。</span><span class="sxs-lookup"><span data-stu-id="14b95-258">ARRAYs represent a single complete type.</span></span>

<span data-ttu-id="14b95-259">示例：</span><span class="sxs-lookup"><span data-stu-id="14b95-259">Examples:</span></span>

<span data-ttu-id="14b95-260">一种类型的"ai"表示为整数数组，而"aai"表示一个整数数组的数组。</span><span class="sxs-lookup"><span data-stu-id="14b95-260">A type of "ai" represents an ARRAY of integers, while "aai" represents an ARRAY of an ARRAY of integers.</span></span>  <span data-ttu-id="14b95-261">一个数组，可能会与结构也使用:"a(ii)"。</span><span class="sxs-lookup"><span data-stu-id="14b95-261">An ARRAY may be used with STRUCTs as well: "a(ii)".</span></span>

___<span data-ttu-id="14b95-262">DICT_ENTRY</span><span class="sxs-lookup"><span data-stu-id="14b95-262">DICT_ENTRY</span></span>___

<span data-ttu-id="14b95-263">DICT_ENTRYs 函数类似于结构，它有更多的限制： 他们使用"{"和"}"，仅可能是为数组元素类型，并且必须具有完全完成大括号内的类型的两个。</span><span class="sxs-lookup"><span data-stu-id="14b95-263">DICT_ENTRYs function similar to a STRUCT with greater restrictions: they use "{" and "}", may only occur as an array element type, and must have exactly two complete types inside the curly braces.</span></span>  <span data-ttu-id="14b95-264">第一种类型表示 dictionary 数据结构，在"密钥"，第二个表示字典的键 / 值对中的"值"。</span><span class="sxs-lookup"><span data-stu-id="14b95-264">The first type represents a "Key" in a dictionary data structure, and the second represents the "Value" in the dictionary's Key-Value pair.</span></span>  <span data-ttu-id="14b95-265">键应为唯一在字典中。</span><span class="sxs-lookup"><span data-stu-id="14b95-265">A Key should be unique in a dictionary.</span></span>

<span data-ttu-id="14b95-266">例如：</span><span class="sxs-lookup"><span data-stu-id="14b95-266">Example:</span></span>

<span data-ttu-id="14b95-267">一种类型的 {sy} 表示字符串键和字节值的字典。</span><span class="sxs-lookup"><span data-stu-id="14b95-267">A type of a{sy} denotes a dictionary of string KEYs and byte VALUEs.</span></span>  <span data-ttu-id="14b95-268">将</span><span class="sxs-lookup"><span data-stu-id="14b95-268">Use</span></span> <description> <span data-ttu-id="14b95-269">若要描述有效的键和值的标记。</span><span class="sxs-lookup"><span data-stu-id="14b95-269">tags to describe valid keys and values.</span></span> 

__<span data-ttu-id="14b95-270">最后一个示例和 ajxmlcop</span><span class="sxs-lookup"><span data-stu-id="14b95-270">Final Example and ajxmlcop</span></span>__

<span data-ttu-id="14b95-271">容器的概念改进了现有的 XML，以及为新的有用的接口成员提供一种途径的功能。</span><span class="sxs-lookup"><span data-stu-id="14b95-271">The concept of containers improves the capabilities of the existing XML as well as providing an avenue for new useful interface members.</span></span>

<span data-ttu-id="14b95-272">完成编写 XML 后，使用 ajxmlcop.exe 命令行工具 (可在 AllJoyn [git 源](https://git.allseenalliance.org/cgit/core/alljoyn.git/)或[此处](https://github.com/MS-brock/AllJoynToasterDemo)) 来验证 XML。</span><span class="sxs-lookup"><span data-stu-id="14b95-272">Once you have finished writing your XML, use the ajxmlcop.exe command line tool (available at the AllJoyn [git source](https://git.allseenalliance.org/cgit/core/alljoyn.git/) or [here](https://github.com/MS-brock/AllJoynToasterDemo)) to validate the XML.</span></span>  <span data-ttu-id="14b95-273">Ajxmlcop.exe 使用 XML 文件用作输入参数 (例如， `C:\>ajxmlcop.exe doorExample.xml`) 来接收错误、 警告和信息性消息。</span><span class="sxs-lookup"><span data-stu-id="14b95-273">Use ajxmlcop.exe with your XML file as the input argument (e.g., `C:\>ajxmlcop.exe doorExample.xml`) to receive error, warning, and informational messages.</span></span>  <span data-ttu-id="14b95-274">此工具提供有价值反馈的结构和 XML 的格式和用法的信号、 属性和方法。</span><span class="sxs-lookup"><span data-stu-id="14b95-274">This tool provides valuable feedback as to the structure and format of your XML and use of signals, properties, and methods.</span></span>

``` xml
<node>
  <interface name="com.example.Door.PrivateDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door.  Private interface that can only be used by the producer’s owner.
    </description>
    <method name="SetPasscode">
      <description language="en">
        Change the code needed to unlock the door.
      </description>
      <argument name="currentPasscode" type="u" direction="in">
        <description language="en">
          Current code needed to unlock door
        </description>
      </argument>
      <argument name="newPasscode" type="u" direction="in">
        <description language="en">
          New code needed to unlock door
        </description>
      </argument>
    </method>
    <method name="UpdateGuestRatings">
      <description language="en">
        Update the list of guests and their personality scores.
      </description>
      <annotation name="org.freedesktop.DBus.Method.NoReply" value="true" />
      <argument name="guestName" type="s">
        <description language="en">
          The name of the guest being entered.
        </description>
      </argument>
      <argument name="qualityScores" type="a{sy}">
        <description language="en">
          DICTIONARY[Key:(string)guestQuality, Value:(byte)score]
          KEYs: "Friendly", "Social", "Punctual" 
          VALUEs: [0-10]
          The qualities of the guest, scored appropriately. If the guestName matches an existing entry, this updates that entry.
        </description>
      </argument>
    </method>
    <method name="SetDoorSecurity">
      <description language="en">
        Close and lock the door or unlock the door.
      </description>
      <argument name="secured" type="b" direction="in">
        <description language="en">
          If TRUE, shut and lock the door.
          If FALSE, unlock the door.
        </description>
      </argument>
    </method>
    <property name="MessageBook" type="a(ss)" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="invalidates"/>
      <description language="en">
        (struct)[(string)guestName, (string)message]
        A list of names of people and the messages they have left.
      </description>
    </property>
    <property name="GuestRatings" type="a(sa{sy})" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        ARRAY[(string)guestName, DICTIONARY(Key:(string)guestQuality, Value:(byte)score)]
        KEYs: "Friendly", "Social", "Punctual"
        VALUEs: [0-10]
        A collection of the previous guests and their scored qualities.
      </description>
    </property>
    <property name="IsLocked" type="b" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">
        Owner of the door may freely lock and unlock the door.
      </description>
    </property>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <signal name="ThresholdCrossed" sessioncast="true">
      <description>
        Signal to notify owner whenever anyone passes through the door.
      </description>
      <argument name="crossedInwards" type="b" direction="out">
        If true, someone entered; if false, someone left.
      </argument>    
    </signal>
  </interface>
  <interface name="com.example.Door.PublicDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door. Public interface that can be used by any consumer.
    </description>
    <method name="UnlockDoor">
      <description language="en">
        Allows guests with the code to unlock the door.
      </description>
      <argument name="passcode" type="u" direction="in">
        <description language="en">
          Current code (00000000 to 99999999) needed to unlock door
        </description>
      </argument>
      <argument name="welcomeMessage" type="s" direction="out">
        <description language="en">
          Message from the owner of the door.
        </description>
      </argument>
    </method>
    <method name="LeaveMessage">
      <description language="en">
        Leave a message for the owner of the door.
      </description>
      <argument name="guestName" type="s" direction="in">
        <description language="en">
          Name of guest leaving a message
        </description>
      </argument>
      <argument name="message" type="s" direction="in">
        <description language="en">
          Message left for owner of the door
        </description>
      </argument>
    </method>
    <method name="AnnouncePresence">
      <description language="en">
        Send a message to the owner of the door.
      </description>
      <argument name="announcingGuest" type="s" direction="in">
        <description language="en">
          Name of the guest announcing their presence.
        </description>
      </argument>
      <argument name="forcefulnessOfAnnouncment" type="y" direction="in">
        <description language="en">
          Degree to which the guest attempts to make their presence known, on bounds [1:10], where 1 is softly and 10 is aggressively.
        </description>
      </argument>
    </method>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <property name="Owner" type="s" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Owner of the door is public knowledge.
      </description>
    </property>
  </interface>
</node>
```

