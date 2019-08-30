---
title: AllJoyn 制造者
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何通过学习和创作自检 XML 及其不同的功能来创建 AllJoyn 创建者。
keywords: windows iot, AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167395"
---
> [!NOTE]
> <span data-ttu-id="96e7b-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="96e7b-104">You are viewing archived documentation.</span></span> <span data-ttu-id="96e7b-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="96e7b-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="96e7b-106">如有问题, 请在 GitHub 上提出问题, 或在下面的评论中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="96e7b-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-producers"></a><span data-ttu-id="96e7b-107">AllJoyn 制造者</span><span class="sxs-lookup"><span data-stu-id="96e7b-107">AllJoyn Producers</span></span>

<span data-ttu-id="96e7b-108">通过[AllSeen 联盟](https://allseenalliance.org/)创建的 AllJoyn 提供了一个很好的框架, 用于在最近网络上建立连接的设备和应用, Windows 提供了在适用于 Visual Studio 的[alljoyn studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展的情况下使用 alljoyn 的最佳体验。</span><span class="sxs-lookup"><span data-stu-id="96e7b-108">AllJoyn, created by the [AllSeen Alliance](https://allseenalliance.org/), provides a great framework for making connected devices and apps on a proximal network, and Windows provides the best experience for using AllJoyn with the [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extension for Visual Studio.</span></span>  <span data-ttu-id="96e7b-109">虽然我们的工具为创建适用于创建者和使用者的应用程序, 但从头开始新的 AllJoyn 设备可能会令人费解。</span><span class="sxs-lookup"><span data-stu-id="96e7b-109">While our tools excel at creating apps for producers and consumers, starting a new AllJoyn device from scratch can be quite confusing.</span></span>

<span data-ttu-id="96e7b-110">如果你对下一个连接良好的设备或用于 tinker 和浏览的新玩具有看法, 则可能无法使用 AllSeen 联盟提供的标准接口之一。</span><span class="sxs-lookup"><span data-stu-id="96e7b-110">If you have an idea for the next great connected device or a new toy with which to tinker and explore, you may not be able to use one of the standard interfaces offered by the AllSeen Alliance.</span></span>  <span data-ttu-id="96e7b-111">如果是这样, 则需要创建全新的 AllJoyn 制造者。</span><span class="sxs-lookup"><span data-stu-id="96e7b-111">If so, then you need to create a brand new AllJoyn producer.</span></span>

<span data-ttu-id="96e7b-112">想要让新的 AllJoyn 制造者创作自己的自检 XML 的开发人员需要创作自己的 XML, 但创建自检 XML 需要使用者专业知识, 并为新开发人员提供重要的学习曲线。</span><span class="sxs-lookup"><span data-stu-id="96e7b-112">A developer wanting to make a new AllJoyn producer needs to author their own Introspection XML, but creating Introspection XML requires subject matter expertise and has a significant learning curve for new developers.</span></span>  <span data-ttu-id="96e7b-113">这 blogpost 将通过分解自检 XML 的各种组件、描述每个组件的用途和限制以及提供易学术语中的好示例, 来降低学习曲线。</span><span class="sxs-lookup"><span data-stu-id="96e7b-113">This blogpost will lower the learning curve by breaking down the various components of Introspection XML, describing the purpose and restrictions of each component, and providing good examples in approachable terms.</span></span>

## <a name="existing-documentation"></a><span data-ttu-id="96e7b-114">现有文档</span><span class="sxs-lookup"><span data-stu-id="96e7b-114">Existing documentation</span></span>

<span data-ttu-id="96e7b-115">粗略检查以下与此 blogpost 结合的资源应加速开发人员了解自检 XML:</span><span class="sxs-lookup"><span data-stu-id="96e7b-115">A cursory examination of the following resources combined with this blogpost should accelerate developer understanding of Introspection XML:</span></span>

1. <span data-ttu-id="96e7b-116">[Alljoyn 事件和操作 API 指南](https://allseenalliance.org/developers/develop/api-guide/events-and-actions)– alljoyn 实现细节和概述。</span><span class="sxs-lookup"><span data-stu-id="96e7b-116">[AllJoyn Events and Actions API Guide](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn implementation details and overview.</span></span>
2. <span data-ttu-id="96e7b-117">[Alljoyn Interface 审查板设计准则](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0)-适用于 ALLJOYN 自检 XML 的严格结构和规范。</span><span class="sxs-lookup"><span data-stu-id="96e7b-117">[AllJoyn Interface Review Board Design Guidelines](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) - stringent structuring and specification for AllJoyn Introspection XML.</span></span>
3. <span data-ttu-id="96e7b-118">[D 总线规范](http://dbus.freedesktop.org/doc/dbus-specification.html)–此规范中的自检 XML。</span><span class="sxs-lookup"><span data-stu-id="96e7b-118">[D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn bases Introspection XML on this specification.</span></span>

<span data-ttu-id="96e7b-119">__这三种类型的自检 XML__</span><span class="sxs-lookup"><span data-stu-id="96e7b-119">__The three types of Introspection XML__</span></span>

<span data-ttu-id="96e7b-120">当你细读 AllJoyn 文档时, 你会发现三种类型的自检 XML:</span><span class="sxs-lookup"><span data-stu-id="96e7b-120">As you peruse AllJoyn documentation, you will find three types of Introspection XML:</span></span>

1. <span data-ttu-id="96e7b-121">D 总线规范 XML: 开销较低, 与数据表示形式的类型格式进行进程间通信。</span><span class="sxs-lookup"><span data-stu-id="96e7b-121">D-Bus Specification XML: low-overhead, interprocess communication with a type format for data representation.</span></span>
2. <span data-ttu-id="96e7b-122">AllJoyn 自检 XML: 扩展了用于保存文本说明的 D 总线规范 XML 和 XML 标记, 同时还将 AllJoyn 原则应用于该规范。</span><span class="sxs-lookup"><span data-stu-id="96e7b-122">AllJoyn Introspection XML: extends D-Bus Specification XML with XML tags for holding textual descriptions while also applying AllJoyn principles to the specification.</span></span>
3. <span data-ttu-id="96e7b-123">扩展的 AllJoyn 自检 XML: 经典自检 XML 演化介绍了结构和字典的命名类型。</span><span class="sxs-lookup"><span data-stu-id="96e7b-123">Extended AllJoyn Introspection XML: evolution of classic Introspection XML introducing named types for structures and dictionaries.</span></span>

<span data-ttu-id="96e7b-124">AllJoyn Studio 当前支持 D 总线规范 XML 和 AllJoyn 自检 XML;此博客将指导如何创建和形成 AllJoyn 自检 XML。</span><span class="sxs-lookup"><span data-stu-id="96e7b-124">AllJoyn Studio currently supports D-Bus Specification XML and AllJoyn Introspection XML; this blog will dictate how to create and form AllJoyn Introspection XML.</span></span>  <span data-ttu-id="96e7b-125">AllSeen 联盟的接口审查委员会 (IRB) 使用新的扩展 AllJoyn 自检作为标准版报送的格式, 但在不久的将来, 将使用统一的自检 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="96e7b-125">The AllSeen Alliance's Interface Review Board (IRB) uses the new Extended AllJoyn Introspection as the format for formal submissions for standardization reviews but is working on a unified introspection XML format for the near future.</span></span>

## <a name="introspection-high-level-overview"></a><span data-ttu-id="96e7b-126">自检高级概述</span><span class="sxs-lookup"><span data-stu-id="96e7b-126">Introspection High Level Overview</span></span>

<span data-ttu-id="96e7b-127">每个 AllJoyn 制造者公开广告自检 XML, 该 XML 显示了生成者支持的功能 (如通过信号、属性和方法说明的接口)。</span><span class="sxs-lookup"><span data-stu-id="96e7b-127">Every AllJoyn producer publicly advertises an Introspection XML that surfaces the producer's supported functionality – interfaces as described via signals, properties and methods.</span></span>  <span data-ttu-id="96e7b-128">类似于 AllJoyn Studio 扩展中的代码生成解决方案, 它依赖自检 XML 来创建必要的代码以加速开发。</span><span class="sxs-lookup"><span data-stu-id="96e7b-128">Code Generation solutions, like the one in the AllJoyn Studio extension, rely on Introspection XML to create the necessary code to accelerate development.</span></span>  <span data-ttu-id="96e7b-129">自检 XML 以用户可读的非歧义方式描述了制造者的功能, 这样两个不同的制造商就可以使用 XML 来实现具有相同功能的生成者。</span><span class="sxs-lookup"><span data-stu-id="96e7b-129">Introspection XML describes the functionality of a producer in a non-ambiguous, human-readable way such that two different manufacturers can use the XML to implement a producer with the same functionality.</span></span>  <span data-ttu-id="96e7b-130">同一个令牌, 没有对 AllJoyn 制造者的事先了解的开发人员应能够基于其 XML 进行开发。</span><span class="sxs-lookup"><span data-stu-id="96e7b-130">By the same token, developers with no previous knowledge of an AllJoyn producer should be able to develop against that producer based on its XML.</span></span>

<span data-ttu-id="96e7b-131">__AllJoyn 接口__</span><span class="sxs-lookup"><span data-stu-id="96e7b-131">__AllJoyn Interfaces__</span></span>

<span data-ttu-id="96e7b-132">AllJoyn 实现此操作的方法是: 将自检 XML 分解为各种不同的 "接口", 表示行为和功能的不同逻辑分组。</span><span class="sxs-lookup"><span data-stu-id="96e7b-132">AllJoyn accomplishes this by breaking an Introspection XML into various "interfaces" that represent different logical groupings of behavior and capabilities.</span></span>  <span data-ttu-id="96e7b-133">使用反向 DNS 约定命名 AllJoyn 接口。</span><span class="sxs-lookup"><span data-stu-id="96e7b-133">AllJoyn interfaces are named using a reverse-DNS convention.</span></span> <span data-ttu-id="96e7b-134">例如, Contoso 公司 (拥有 contoso.com 域) 创建的接口 "Foo" 接口将编写为:</span><span class="sxs-lookup"><span data-stu-id="96e7b-134">For example, the interface "Foo" interface created by Contoso Ltd., which owns the contoso.com domain, would be written as:</span></span>

    <interface name="com.contoso.Foo">

<span data-ttu-id="96e7b-135">制造者可以实现任意数量的接口, 但必须实现其播发的接口的每个组件。</span><span class="sxs-lookup"><span data-stu-id="96e7b-135">A producer may implement any number of interfaces, but must implement every component of an interface that they advertise.</span></span>  <span data-ttu-id="96e7b-136">为了区分和扩展行为, AllJoyn 支持在现有接口层次结构方面创建新接口;即, `Foo.Bar` `com.contoso.Foo`定义类别下的项目的新功能, 但不会在接口上具有任何显式依赖项。 `com.contoso.Foo.Bar`</span><span class="sxs-lookup"><span data-stu-id="96e7b-136">In order to differentiate and extend behaviors, AllJoyn supports creating new interfaces with respect to an existing interface hierarchy; i.e. `com.contoso.Foo.Bar` defines new capabilities for things under the `Foo.Bar` category but doesn't have any explicit dependencies on the `com.contoso.Foo` interface.</span></span> 

<span data-ttu-id="96e7b-137">例如, 我们有两个接口: `com.contoso.Sensor`和`com.contoso.Sensor.Humidity` – "湿度" 逻辑落在 "传感器" 类别下。</span><span class="sxs-lookup"><span data-stu-id="96e7b-137">For an example, we have two interfaces: `com.contoso.Sensor` and `com.contoso.Sensor.Humidity` – "Humidity" logically falls under the "Sensor" category.</span></span>  <span data-ttu-id="96e7b-138">开发湿度制造者的人员可以选择仅`com.contoso.Sensor.Humdity`支持接口, 但也可以选择`com.contoso.Sensor`支持接口。</span><span class="sxs-lookup"><span data-stu-id="96e7b-138">Someone developing a Humidity producer could choose to support just the `com.contoso.Sensor.Humdity` interface, but they could also choose to support the `com.contoso.Sensor` interface.</span></span>  <span data-ttu-id="96e7b-139">无论如何, 如果它们公布一个接口, 则创建者必须支持其所有功能。</span><span class="sxs-lookup"><span data-stu-id="96e7b-139">Regardless, if they advertise an interface, then producers must support all of its functions.</span></span>

<span data-ttu-id="96e7b-140">`<description>`标记用于描述接口、功能和参数, 并可针对各种语言进行本地化。</span><span class="sxs-lookup"><span data-stu-id="96e7b-140">The `<description>` tag is used to describe interfaces, capabilities and arguments, and can be localized for various languages.</span></span>  <span data-ttu-id="96e7b-141">使用`<description>`标记的自由使用使得 XML 更易于理解, 并消除了歧义。</span><span class="sxs-lookup"><span data-stu-id="96e7b-141">Liberal use of the `<description>` tag makes the XML more understandable and removes ambiguity.</span></span>

<span data-ttu-id="96e7b-142">标准做法规定在接口上使用`org.alljoyn.Bus.Secure`批注来实现安全性和身份验证。</span><span class="sxs-lookup"><span data-stu-id="96e7b-142">Standard practice dictates the use of the `org.alljoyn.Bus.Secure` annotation on an interface to enable security and authentication.</span></span>  <span data-ttu-id="96e7b-143">对于强身份验证, 请使用预共享密钥 (PSK) 或证书密钥交换 (ECDSA)。</span><span class="sxs-lookup"><span data-stu-id="96e7b-143">For strong authentication, use a pre-shared key (PSK) or a certificate key exchange (ECDSA).</span></span>  <span data-ttu-id="96e7b-144">否则, "null" 身份验证成为默认行为。</span><span class="sxs-lookup"><span data-stu-id="96e7b-144">Otherwise, a "null" authentication becomes the default behavior.</span></span>  <span data-ttu-id="96e7b-145">**实际的身份验证机制发生在实现中, 而不是声明**。</span><span class="sxs-lookup"><span data-stu-id="96e7b-145">**The actual authentication mechanism happens in implementation, not the declaration**.</span></span> <span data-ttu-id="96e7b-146">此批注启用安全性, 但不指定所使用的安全类型或其实现方式。</span><span class="sxs-lookup"><span data-stu-id="96e7b-146">This annotation enables security but does not specify the type of security used or how it will be implemented.</span></span>

<span data-ttu-id="96e7b-147">___示例___</span><span class="sxs-lookup"><span data-stu-id="96e7b-147">___Example___</span></span>

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

<span data-ttu-id="96e7b-148">此示例演示设备公开的接口: `com.example.Door.PrivateDoor`。</span><span class="sxs-lookup"><span data-stu-id="96e7b-148">This example shows an interface exposed by a device: `com.example.Door.PrivateDoor`.</span></span> <span data-ttu-id="96e7b-149">在接口的作用域中, 唯一要注意的是, 在使用该接口时是否应保护通信, 而不是使用哪种类型的机制。</span><span class="sxs-lookup"><span data-stu-id="96e7b-149">In the scope of the interface, the only thing we're concerned about is whether communication should be secured when using that interface, not what type of mechanism is being used.</span></span>

<span data-ttu-id="96e7b-150">__接口功能__</span><span class="sxs-lookup"><span data-stu-id="96e7b-150">__Interface Capabilities__</span></span>

<span data-ttu-id="96e7b-151">接口声明其功能和三个接口成员: 方法、属性或信号。</span><span class="sxs-lookup"><span data-stu-id="96e7b-151">Interfaces declare their capabilities with three interface members: methods, properties, or signals.</span></span> <span data-ttu-id="96e7b-152">自检 XML 还支持描述附加功能或约束的批注。</span><span class="sxs-lookup"><span data-stu-id="96e7b-152">Introspection XML also supports annotations that describe additional functionality or constraints.</span></span>  <span data-ttu-id="96e7b-153">这些功能使用 UpperCamelCase 表示法, 而参数使用 lowerCamelCase 表示法。</span><span class="sxs-lookup"><span data-stu-id="96e7b-153">These capabilities use UpperCamelCase notation while arguments use lowerCamelCase notation.</span></span>

### <a name="argument-types"></a><span data-ttu-id="96e7b-154">参数类型</span><span class="sxs-lookup"><span data-stu-id="96e7b-154">Argument Types</span></span>

<span data-ttu-id="96e7b-155">接口成员发送和接收由 ASCII 类型代码表示的参数。</span><span class="sxs-lookup"><span data-stu-id="96e7b-155">Interface members send and receive arguments denoted by an ASCII type-code.</span></span>  <span data-ttu-id="96e7b-156">根据接口成员的类型, 可能会将参数从使用者 (方向 = "out") 或使用者发送到制造者 (方向 = "in")。</span><span class="sxs-lookup"><span data-stu-id="96e7b-156">Depending on the type of interface member, arguments may have be sent to the producer from the consumer (direction="out") or from the consumer to the producer (direction="in").</span></span>  <span data-ttu-id="96e7b-157">下表提供了常用类型的简要概述:</span><span class="sxs-lookup"><span data-stu-id="96e7b-157">The following table provides a brief overview of commonly used types:</span></span>

> | <span data-ttu-id="96e7b-158">*传统名称*</span><span class="sxs-lookup"><span data-stu-id="96e7b-158">*Conventional Name*</span></span> | <span data-ttu-id="96e7b-159">*类型代码*</span><span class="sxs-lookup"><span data-stu-id="96e7b-159">*Type-Code*</span></span> | <span data-ttu-id="96e7b-160">*用途*</span><span class="sxs-lookup"><span data-stu-id="96e7b-160">*Use*</span></span> |
> |----------------- |---------| --- |
> |<span data-ttu-id="96e7b-161">**变量**</span><span class="sxs-lookup"><span data-stu-id="96e7b-161">**BOOLEAN**</span></span> | <span data-ttu-id="96e7b-162">b</span><span class="sxs-lookup"><span data-stu-id="96e7b-162">b</span></span> | <span data-ttu-id="96e7b-163">表示 TRUE (1) 或 FALSE (0)。</span><span class="sxs-lookup"><span data-stu-id="96e7b-163">Represents TRUE (1) or FALSE (0).</span></span> <span data-ttu-id="96e7b-164">用于简单的二进制信息或状态。</span><span class="sxs-lookup"><span data-stu-id="96e7b-164">Used for simple binary information or states.</span></span> |
> |<span data-ttu-id="96e7b-165">**BYTE**</span><span class="sxs-lookup"><span data-stu-id="96e7b-165">**BYTE**</span></span> | <span data-ttu-id="96e7b-166">y</span><span class="sxs-lookup"><span data-stu-id="96e7b-166">y</span></span> | <span data-ttu-id="96e7b-167">介于0到255之间的整数值。</span><span class="sxs-lookup"><span data-stu-id="96e7b-167">Integer value from 0 to 255.</span></span> <span data-ttu-id="96e7b-168">处理较小的正数时使用。</span><span class="sxs-lookup"><span data-stu-id="96e7b-168">Used when dealing with small positive numbers.</span></span> |
> |<span data-ttu-id="96e7b-169">**UINT16**</span><span class="sxs-lookup"><span data-stu-id="96e7b-169">**UINT16**</span></span> | <span data-ttu-id="96e7b-170">q</span><span class="sxs-lookup"><span data-stu-id="96e7b-170">q</span></span> | <span data-ttu-id="96e7b-171">0到 2 ^ 16-1 之间的整数值</span><span class="sxs-lookup"><span data-stu-id="96e7b-171">Integer value from 0 to 2^16 - 1</span></span> |
> |<span data-ttu-id="96e7b-172">**UINT32**</span><span class="sxs-lookup"><span data-stu-id="96e7b-172">**UINT32**</span></span> | <span data-ttu-id="96e7b-173">形</span><span class="sxs-lookup"><span data-stu-id="96e7b-173">u</span></span> | <span data-ttu-id="96e7b-174">0到 2 ^ 32-1 之间的整数值</span><span class="sxs-lookup"><span data-stu-id="96e7b-174">Integer value from 0 to 2^32 - 1</span></span> |
> |<span data-ttu-id="96e7b-175">**UINT64**</span><span class="sxs-lookup"><span data-stu-id="96e7b-175">**UINT64**</span></span> | <span data-ttu-id="96e7b-176">的 VPN 连接下</span><span class="sxs-lookup"><span data-stu-id="96e7b-176">t</span></span> | <span data-ttu-id="96e7b-177">0到 2 ^ 64-1 之间的整数值</span><span class="sxs-lookup"><span data-stu-id="96e7b-177">Integer value from 0 to 2^64 - 1</span></span> |
> |<span data-ttu-id="96e7b-178">**INT16**</span><span class="sxs-lookup"><span data-stu-id="96e7b-178">**INT16**</span></span> | <span data-ttu-id="96e7b-179">n</span><span class="sxs-lookup"><span data-stu-id="96e7b-179">n</span></span> | <span data-ttu-id="96e7b-180">从– (2 ^ 15) 到 2 ^ 15-1 的整数值</span><span class="sxs-lookup"><span data-stu-id="96e7b-180">Integer value from –(2^15) to 2^15 - 1</span></span> |
> |<span data-ttu-id="96e7b-181">**INT32**</span><span class="sxs-lookup"><span data-stu-id="96e7b-181">**INT32**</span></span> | <span data-ttu-id="96e7b-182">图标</span><span class="sxs-lookup"><span data-stu-id="96e7b-182">i</span></span> | <span data-ttu-id="96e7b-183">从– (2 ^ 31) 到 2 ^ 31-1 的整数值</span><span class="sxs-lookup"><span data-stu-id="96e7b-183">Integer value from –(2^31) to 2^31 - 1</span></span> |
> |<span data-ttu-id="96e7b-184">**INT64**</span><span class="sxs-lookup"><span data-stu-id="96e7b-184">**INT64**</span></span> | <span data-ttu-id="96e7b-185">x</span><span class="sxs-lookup"><span data-stu-id="96e7b-185">x</span></span> | <span data-ttu-id="96e7b-186">从– (2 ^ 63) 到 2 ^ 63-1 的整数值</span><span class="sxs-lookup"><span data-stu-id="96e7b-186">Integer value from –(2^63) to 2^63 - 1</span></span> |
> |<span data-ttu-id="96e7b-187">**仔细**</span><span class="sxs-lookup"><span data-stu-id="96e7b-187">**DOUBLE**</span></span> | <span data-ttu-id="96e7b-188">d</span><span class="sxs-lookup"><span data-stu-id="96e7b-188">d</span></span> | <span data-ttu-id="96e7b-189">从– (2 ^ 127) 到 2 ^ 127-1 的精度浮点数</span><span class="sxs-lookup"><span data-stu-id="96e7b-189">Precision floating point numbers from –(2^127) to 2^127 - 1</span></span> |
> |<span data-ttu-id="96e7b-190">**类似**</span><span class="sxs-lookup"><span data-stu-id="96e7b-190">**STRING**</span></span> | <span data-ttu-id="96e7b-191">文件</span><span class="sxs-lookup"><span data-stu-id="96e7b-191">s</span></span> | <span data-ttu-id="96e7b-192">UTF-8 字符串</span><span class="sxs-lookup"><span data-stu-id="96e7b-192">UTF-8 string</span></span> |
 
<span data-ttu-id="96e7b-193">有关所有受支持类型的更详尽概述, 请参阅[此处](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448)。</span><span class="sxs-lookup"><span data-stu-id="96e7b-193">For a more exhaustive overview of all the supported types, see [here](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span></span>

<span data-ttu-id="96e7b-194">在撰写本文时, 尽可能使用 SI 单位, 并清楚地表示预期单位。</span><span class="sxs-lookup"><span data-stu-id="96e7b-194">As of this writing, use SI units where possible and clearly denote intended units.</span></span> <span data-ttu-id="96e7b-195">如果可能, 请选择对方案最严格的类型代码;例如, 如果你表示某个人的年龄 (年), 则使用 BYTE, 而不是 UINT16 或 INT16, 因为没有任何人将为负年龄或超过255岁。</span><span class="sxs-lookup"><span data-stu-id="96e7b-195">When possible, choose the type-code most restrictive to your scenario; e.g., if you are representing a person's age in years, then use BYTE, not UINT16 or INT16, since no one will be a negative age or more than 255 years old.</span></span>  <span data-ttu-id="96e7b-196">始终遵循最新的[AllJoyn 接口查看委员会 (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board)准则。</span><span class="sxs-lookup"><span data-stu-id="96e7b-196">Always follow the latest [AllJoyn Interface Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) guidelines.</span></span>

<span data-ttu-id="96e7b-197">下表汇总了常用单位:</span><span class="sxs-lookup"><span data-stu-id="96e7b-197">The following table summarizes common units:</span></span>


> |<span data-ttu-id="96e7b-198">*Quantity*</span><span class="sxs-lookup"><span data-stu-id="96e7b-198">*Quantity*</span></span> | <span data-ttu-id="96e7b-199">*单位*</span><span class="sxs-lookup"><span data-stu-id="96e7b-199">*Unit*</span></span>|
> |-------- | ---- |
> |<span data-ttu-id="96e7b-200">**绝对时间 (日期 & 时间)**</span><span class="sxs-lookup"><span data-stu-id="96e7b-200">**Absolute time (date & time)**</span></span> | <span data-ttu-id="96e7b-201">自 UNIX Epoch 以来的秒数 (00:00:00 年1月 1970 1 日)</span><span class="sxs-lookup"><span data-stu-id="96e7b-201">Seconds since UNIX Epoch (00:00:00 on January 1, 1970)</span></span> |
> |<span data-ttu-id="96e7b-202">**当天的时间**</span><span class="sxs-lookup"><span data-stu-id="96e7b-202">**Time of Day**</span></span> | <span data-ttu-id="96e7b-203">午夜后的秒数</span><span class="sxs-lookup"><span data-stu-id="96e7b-203">Seconds since midnight</span></span> |
> |<span data-ttu-id="96e7b-204">**时间间隔**</span><span class="sxs-lookup"><span data-stu-id="96e7b-204">**Time interval**</span></span> | <span data-ttu-id="96e7b-205">秒</span><span class="sxs-lookup"><span data-stu-id="96e7b-205">Seconds</span></span> |
> |<span data-ttu-id="96e7b-206">**带宽**</span><span class="sxs-lookup"><span data-stu-id="96e7b-206">**Bandwidth**</span></span> | <span data-ttu-id="96e7b-207">每秒位数</span><span class="sxs-lookup"><span data-stu-id="96e7b-207">Bits per second</span></span> |
> |<span data-ttu-id="96e7b-208">**数据大小**</span><span class="sxs-lookup"><span data-stu-id="96e7b-208">**Data size**</span></span> | <span data-ttu-id="96e7b-209">字节</span><span class="sxs-lookup"><span data-stu-id="96e7b-209">Bytes</span></span> |
 
### <a name="methods"></a><span data-ttu-id="96e7b-210">方法</span><span class="sxs-lookup"><span data-stu-id="96e7b-210">Methods</span></span>

<span data-ttu-id="96e7b-211">使用者调用方法来修改制造者的状态, 其名称应以动词开头, 因为它们表示对生成者执行操作的请求。</span><span class="sxs-lookup"><span data-stu-id="96e7b-211">Consumers call methods to modify the state of a producer, and their names should start with a verb because they represent requests for the producer to perform an action.</span></span>  <span data-ttu-id="96e7b-212">方法可能具有输入参数和输出参数;如果不需要发送任何返回消息, 则应用批注 "freedesktop. NoReply" ()。</span><span class="sxs-lookup"><span data-stu-id="96e7b-212">Methods may have input and output arguments; in the case that no return message needs to be sent, apply the annotation "org.freedesktop.DBus.Method.NoReply".</span></span>  <span data-ttu-id="96e7b-213">但是, AllJoyn 方法通常会返回 SuccessResult 或 FailureResult, 并向使用者提供有关方法调用的反馈。</span><span class="sxs-lookup"><span data-stu-id="96e7b-213">However, AllJoyn methods normally return a SuccessResult or a FailureResult, giving consumers feedback about the method call.</span></span>  <span data-ttu-id="96e7b-214">自变量的类型必须符合[D 总线规范](http://dbus.freedesktop.org/doc/dbus-specification.html)。</span><span class="sxs-lookup"><span data-stu-id="96e7b-214">The type of the arguments must comply with the [D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html).</span></span> 

<span data-ttu-id="96e7b-215">___示例 (为了方便起见, 不包括接口信息)___</span><span class="sxs-lookup"><span data-stu-id="96e7b-215">___Example (excluding interface information for convenience)___</span></span>

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

<span data-ttu-id="96e7b-216">*注意：在大多数情况下, 应使用属性而不是方法来访问制造者的状态 (例如, 使用颜色属性, 而不是 GetColor 方法)。*</span><span class="sxs-lookup"><span data-stu-id="96e7b-216">*Note: In most cases, properties should be used instead of methods to access a producer's state (e.g., use a Color property instead of a GetColor method).*</span></span>

### <a name="properties"></a><span data-ttu-id="96e7b-217">属性</span><span class="sxs-lookup"><span data-stu-id="96e7b-217">Properties</span></span>

<span data-ttu-id="96e7b-218">属性主要允许访问制造者的状态。</span><span class="sxs-lookup"><span data-stu-id="96e7b-218">Properties mainly allow access to a producer's state.</span></span>  <span data-ttu-id="96e7b-219">虽然在技术上, 属性具有 "读取"、"读写" 或 "写入" 访问值, 但状态修改功能通常属于方法–因此, 开发人员应尽量将属性设置为 "读取", 并仅在所表示的状态下使用 "readwrite"此属性与所有其他属性无关。</span><span class="sxs-lookup"><span data-stu-id="96e7b-219">While properties technically have access values of "read", "readwrite", or "write", state-modifying functionality generally belongs to methods – as such, developers should strive to keep properties as "read" and use "readwrite" only when the state represented by that property is independent of all other properties.</span></span>  <span data-ttu-id="96e7b-220">属性绝不应该只是 "write"-修改状态, 而不会观察到方法的角色。</span><span class="sxs-lookup"><span data-stu-id="96e7b-220">Properties should never be just "write" – modifying the state without observation is the role of methods.</span></span>

<span data-ttu-id="96e7b-221">当属性值发生更改时, 必须将属性批注到警报使用者 (可以选择, 属性可以从其父接口继承此注释)。</span><span class="sxs-lookup"><span data-stu-id="96e7b-221">Properties must be annotated to alert consumers when their values change (optionally, properties can inherit this annotation from its parent interface).</span></span>  <span data-ttu-id="96e7b-222">批注`org.freedesktop.DBus.Property.EmitsChangedSignal`可以有四个值:</span><span class="sxs-lookup"><span data-stu-id="96e7b-222">The annotation `org.freedesktop.DBus.Property.EmitsChangedSignal` can have four values:</span></span>

* <span data-ttu-id="96e7b-223">"true" –当属性发生更改时, 生成者将发出一个指示已更改属性和新值的信号。</span><span class="sxs-lookup"><span data-stu-id="96e7b-223">"true" – when the property changes, the producer will emit a signal denoting the changed property and the new value.</span></span> <span data-ttu-id="96e7b-224">用于经常使用的属性, 并需要积极的监督, 如 "LockState"。</span><span class="sxs-lookup"><span data-stu-id="96e7b-224">Used in properties that are frequently used and require active oversight, such as a "LockState" for a door.</span></span>
* <span data-ttu-id="96e7b-225">"无效" –当属性发生更改时, 制造者将发出一个指示已更改属性但不发出新值的信号。</span><span class="sxs-lookup"><span data-stu-id="96e7b-225">"invalidates" – when the property changes, the producer will emit a signal denoting the changed property but not the new value.</span></span> <span data-ttu-id="96e7b-226">用于不需要大量监督的属性 (例如衣服烘干机的 "WashMode") 或表示大量数据, 如容器。</span><span class="sxs-lookup"><span data-stu-id="96e7b-226">Used in properties that don't require heavy oversight (such as the "WashMode" of a clothes dryer) or represent a lot of data, such as a container.</span></span>
* <span data-ttu-id="96e7b-227">"false" –当属性更改时, 制造者不发出信号。</span><span class="sxs-lookup"><span data-stu-id="96e7b-227">"false" – when the property changes, the producer emits no signal.</span></span> <span data-ttu-id="96e7b-228">用于快速更新的属性中, 例如地铁的 "TransitCounter" 属性。</span><span class="sxs-lookup"><span data-stu-id="96e7b-228">Used in properties that update rapidly, such as a "TransitCounter" property on a subway turnstile tracking people boarding the subway.</span></span> <span data-ttu-id="96e7b-229">如果未指定, 则 AllJoyn 属性将此用作默认值。</span><span class="sxs-lookup"><span data-stu-id="96e7b-229">If unspecified, AllJoyn properties use this as default.</span></span>
* <span data-ttu-id="96e7b-230">"const" –属性永远不会更改值, 也不会发出更改的信号。</span><span class="sxs-lookup"><span data-stu-id="96e7b-230">"const" – the property will never change value and never emit a changed signal.</span></span> <span data-ttu-id="96e7b-231">这将在 AllJoyn 16.04 版中引入;在此之前, 请使用 "true"。</span><span class="sxs-lookup"><span data-stu-id="96e7b-231">This will be introduced in the AllJoyn 16.04 release; until then, use "true".</span></span>

<span data-ttu-id="96e7b-232">___示例___</span><span class="sxs-lookup"><span data-stu-id="96e7b-232">___Example___</span></span>

<span data-ttu-id="96e7b-233">在前面的示例中, 我们已将 XML 修改为包含属性 (为简洁起见, 不包括方法)。</span><span class="sxs-lookup"><span data-stu-id="96e7b-233">Expanding upon the previous example, we have modified the XML to include properties (excluding the methods for brevity).</span></span>

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

### <a name="signals"></a><span data-ttu-id="96e7b-234">信号</span><span class="sxs-lookup"><span data-stu-id="96e7b-234">Signals</span></span>

<span data-ttu-id="96e7b-235">使用信号, 通过查询制造者来向使用者通知事件无法确定。</span><span class="sxs-lookup"><span data-stu-id="96e7b-235">Use signals to inform consumers of an event that they could not determine by querying the producer.</span></span>  <span data-ttu-id="96e7b-236">门打开将通过具有 "true" EmitsChangedProperty 批注的生成者 DoorOpen 属性传达。</span><span class="sxs-lookup"><span data-stu-id="96e7b-236">A door opening would be conveyed through a producer's DoorOpen property with a "true" EmitsChangedProperty annotation.</span></span>  <span data-ttu-id="96e7b-237">但是, 通过门的某个人无法从任何属性更改中派生, 因此, 这会产生一个良好的单独信号。</span><span class="sxs-lookup"><span data-stu-id="96e7b-237">Someone passing through the door, however, cannot be derived from any property changes, so this would make a good standalone signal.</span></span>  <span data-ttu-id="96e7b-238">我们将这类事件称为 "无状态"。</span><span class="sxs-lookup"><span data-stu-id="96e7b-238">We refer to these kinds of events as "stateless".</span></span>  <span data-ttu-id="96e7b-239">由于信号从制造者到使用者是单向的, 因此它们只能包含 "out" 参数。</span><span class="sxs-lookup"><span data-stu-id="96e7b-239">Since signals are unidirectional from producer to consumer, they can only contain "out" arguments.</span></span>

<span data-ttu-id="96e7b-240">___示例___</span><span class="sxs-lookup"><span data-stu-id="96e7b-240">___Examples___</span></span> 

<span data-ttu-id="96e7b-241">(为方便起见, 不包括方法和属性):</span><span class="sxs-lookup"><span data-stu-id="96e7b-241">(excluding methods and properties for convenience):</span></span>

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

<span data-ttu-id="96e7b-242">由于信号具有这样的范围范围, 因此在生成者的 XML 中通常会出现少量的情况。</span><span class="sxs-lookup"><span data-stu-id="96e7b-242">Since signals have such a narrow scope, typically few appear in a producer's XML.</span></span>

### <a name="containers"></a><span data-ttu-id="96e7b-243">容器</span><span class="sxs-lookup"><span data-stu-id="96e7b-243">Containers</span></span>

<span data-ttu-id="96e7b-244">不要将多个参数合并为复杂集合, 如序列化的 JSON 字符串。</span><span class="sxs-lookup"><span data-stu-id="96e7b-244">Do not combine multiple arguments into a complex collection like a serialized JSON string.</span></span> <span data-ttu-id="96e7b-245">D 总线规范为数据容器 (结构、数组、变体和 DICT_ENTRY) 提供实用。</span><span class="sxs-lookup"><span data-stu-id="96e7b-245">The D-Bus specification makes affordances for containers of data – STRUCT, ARRAY, VARIANT, and DICT_ENTRY.</span></span>  <span data-ttu-id="96e7b-246">使用这些参数传递需要基本类型以上的参数。</span><span class="sxs-lookup"><span data-stu-id="96e7b-246">Use these to pass arguments that require more than basic types.</span></span>

<span data-ttu-id="96e7b-247">___变体___</span><span class="sxs-lookup"><span data-stu-id="96e7b-247">___VARIANT___</span></span>

<span data-ttu-id="96e7b-248">变体由类型 "v" 表示, 并且可以包含任何[一个完整类型](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type)。</span><span class="sxs-lookup"><span data-stu-id="96e7b-248">VARIANTs are denoted by the type "v" and can contain any [single complete type](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span></span> <span data-ttu-id="96e7b-249">但是, 应尽可能避免变量, 因为它们向 XML 定义增加了歧义。</span><span class="sxs-lookup"><span data-stu-id="96e7b-249">However, VARIANTs should be avoided whenever possible because they add ambiguity to XML definitions.</span></span>

<span data-ttu-id="96e7b-250">___STRUCT___</span><span class="sxs-lookup"><span data-stu-id="96e7b-250">___STRUCT___</span></span>

<span data-ttu-id="96e7b-251">结构使用 "(" 和 ")" 表示数据结构的开头和结尾–一种完整的类型。</span><span class="sxs-lookup"><span data-stu-id="96e7b-251">STRUCTs use "(" and ")" to denote the beginning and end of a data structure – a single complete type.</span></span>  <span data-ttu-id="96e7b-252">这些数据结构可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="96e7b-252">These data structures may be nested.</span></span>

<span data-ttu-id="96e7b-253">例如：</span><span class="sxs-lookup"><span data-stu-id="96e7b-253">Examples:</span></span>

<span data-ttu-id="96e7b-254">类型 "(iii)" 表示三个整数的结构;"(i (ii))" 表示整数和两个整数的结构的结构, 该结构不同于类型 "((ii) i)"。</span><span class="sxs-lookup"><span data-stu-id="96e7b-254">A type of "(iii)" denotes a structure of three integers; "(i(ii))" denotes a STRUCT of an integer and a STRUCT of two integers, which is distinct from the type "((ii)i)".</span></span>

<span data-ttu-id="96e7b-255">___组成___</span><span class="sxs-lookup"><span data-stu-id="96e7b-255">___ARRAY___</span></span>

<span data-ttu-id="96e7b-256">数组使用类型代码 "a", 后面必须有一个完整类型。</span><span class="sxs-lookup"><span data-stu-id="96e7b-256">ARRAYs use the type code "a" and must be followed by a single complete type.</span></span>  <span data-ttu-id="96e7b-257">数组没有设置长度, 因此它们类似于列表数据结构。</span><span class="sxs-lookup"><span data-stu-id="96e7b-257">ARRAYs do not have set lengths, so they are similar to a list data structure.</span></span> <span data-ttu-id="96e7b-258">数组表示一个完整类型。</span><span class="sxs-lookup"><span data-stu-id="96e7b-258">ARRAYs represent a single complete type.</span></span>

<span data-ttu-id="96e7b-259">例如：</span><span class="sxs-lookup"><span data-stu-id="96e7b-259">Examples:</span></span>

<span data-ttu-id="96e7b-260">"Ai" 类型表示整数的数组, 而 "aai" 表示整数数组的数组。</span><span class="sxs-lookup"><span data-stu-id="96e7b-260">A type of "ai" represents an ARRAY of integers, while "aai" represents an ARRAY of an ARRAY of integers.</span></span>  <span data-ttu-id="96e7b-261">数组也可以与结构一起使用: "a (ii)"。</span><span class="sxs-lookup"><span data-stu-id="96e7b-261">An ARRAY may be used with STRUCTs as well: "a(ii)".</span></span>

<span data-ttu-id="96e7b-262">___DICT_ENTRY___</span><span class="sxs-lookup"><span data-stu-id="96e7b-262">___DICT_ENTRY___</span></span>

<span data-ttu-id="96e7b-263">DICT_ENTRYs 函数类似于具有更大限制的结构: 它们使用 "{" 和 "}", 只能作为数组元素类型出现, 并且在大括号内必须正好有两个完整类型。</span><span class="sxs-lookup"><span data-stu-id="96e7b-263">DICT_ENTRYs function similar to a STRUCT with greater restrictions: they use "{" and "}", may only occur as an array element type, and must have exactly two complete types inside the curly braces.</span></span>  <span data-ttu-id="96e7b-264">第一种类型表示字典数据结构中的 "键", 第二种类型表示字典的键值对中的 "值"。</span><span class="sxs-lookup"><span data-stu-id="96e7b-264">The first type represents a "Key" in a dictionary data structure, and the second represents the "Value" in the dictionary's Key-Value pair.</span></span>  <span data-ttu-id="96e7b-265">密钥在字典中应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="96e7b-265">A Key should be unique in a dictionary.</span></span>

<span data-ttu-id="96e7b-266">例如：</span><span class="sxs-lookup"><span data-stu-id="96e7b-266">Example:</span></span>

<span data-ttu-id="96e7b-267">{Sy} 的一种类型表示字符串键和字节值的字典。</span><span class="sxs-lookup"><span data-stu-id="96e7b-267">A type of a{sy} denotes a dictionary of string KEYs and byte VALUEs.</span></span>  <span data-ttu-id="96e7b-268">将</span><span class="sxs-lookup"><span data-stu-id="96e7b-268">Use</span></span> <description> <span data-ttu-id="96e7b-269">用于描述有效密钥和值的标记。</span><span class="sxs-lookup"><span data-stu-id="96e7b-269">tags to describe valid keys and values.</span></span> 

<span data-ttu-id="96e7b-270">__最终示例和 ajxmlcop__</span><span class="sxs-lookup"><span data-stu-id="96e7b-270">__Final Example and ajxmlcop__</span></span>

<span data-ttu-id="96e7b-271">容器的概念改善了现有 XML 的功能, 并为新的有用接口成员提供途径。</span><span class="sxs-lookup"><span data-stu-id="96e7b-271">The concept of containers improves the capabilities of the existing XML as well as providing an avenue for new useful interface members.</span></span>

<span data-ttu-id="96e7b-272">编写完 XML 后, 请使用 ajxmlcop 命令行工具 (在 AllJoyn [git 源](https://git.allseenalliance.org/cgit/core/alljoyn.git/)或[此处](https://github.com/MS-brock/AllJoynToasterDemo)提供) 来验证 xml。</span><span class="sxs-lookup"><span data-stu-id="96e7b-272">Once you have finished writing your XML, use the ajxmlcop.exe command line tool (available at the AllJoyn [git source](https://git.allseenalliance.org/cgit/core/alljoyn.git/) or [here](https://github.com/MS-brock/AllJoynToasterDemo)) to validate the XML.</span></span>  <span data-ttu-id="96e7b-273">使用 ajxmlcop 作为输入参数 (例如, `C:\>ajxmlcop.exe doorExample.xml`) 来接收错误、警告和信息性消息。</span><span class="sxs-lookup"><span data-stu-id="96e7b-273">Use ajxmlcop.exe with your XML file as the input argument (e.g., `C:\>ajxmlcop.exe doorExample.xml`) to receive error, warning, and informational messages.</span></span>  <span data-ttu-id="96e7b-274">此工具提供了有关 XML 的结构和格式以及信号、属性和方法使用的有价值的反馈。</span><span class="sxs-lookup"><span data-stu-id="96e7b-274">This tool provides valuable feedback as to the structure and format of your XML and use of signals, properties, and methods.</span></span>

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

