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
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。

# <a name="alljoyn-producers"></a>AllJoyn 生成者

AllJoyn，パ[AllSeen 联盟](https://allseenalliance.org/)，提供了非常棒的框架，用于使已连接的设备和 proximal 网络和 Windows 上的应用程序提供了使用与 AllJoyn 的最佳体验[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)适用于 Visual Studio 扩展。  尽管我们的工具擅长于创建生产者和使用者应用程序，从零开始的新 AllJoyn 设备可能非常令人困惑。

如果你有建议下一步好连接的设备或用来修补程序和浏览新玩具，可能无法使用其中一个 AllSeen 联盟所提供的标准接口。  如果是这样，然后您需要创建全新的 AllJoyn 制造者。

开发人员想要使新 AllJoyn 生成者需要创作自己的自检 XML，但创建自检 XML 需要专业知识和为新开发人员具有重要的学习曲线。  这篇博客文章将降低学习难度，通过分解自检 XML 的各种组件，描述的用途和限制每个组件，并在易上手的术语提供很好的示例。

## <a name="existing-documentation"></a>现有文档

对以下资源结合这篇博客文章的粗略检查应加速开发人员了解自检 XML:

1. [AllJoyn 事件和操作 API 指南](https://allseenalliance.org/developers/develop/api-guide/events-and-actions)– AllJoyn 实现的详细信息和概述。
2. [AllJoyn 接口查看板设计准则](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0)-严格结构化和 AllJoyn 自检 XML 的规范。
3. [D 总线规范](http://dbus.freedesktop.org/doc/dbus-specification.html)– AllJoyn 基础此规范执行自检 XML。

__三种类型的自检 XML__

作为您细读 AllJoyn 文档，你会发现三种类型的自检 XML:

1. 与数据表示形式的类型格式的 D 总线规范 XML： 开销较低、 进程间通信。
2. AllJoyn 自检 XML： 通过 D 总线规范 XML 的用于保存时还将 AllJoyn 原则应用于该规范的文字说明的 XML 标记扩展了。
3. 扩展 AllJoyn 自检 XML： 经典自检 XML 引入的发展进行命名的结构和字典类型。

AllJoyn Studio 当前支持 D 总线规范 XML 和 AllJoyn 自检 XML;此博客将决定如何创建和窗体 AllJoyn 自检 XML。  AllSeen 联盟接口查看板 (IRB) 使用新的扩展 AllJoyn 自检作为格式以标准化的意见的正式提交但正在努力不久的将来统一的自检 XML 格式。

## <a name="introspection-high-level-overview"></a>自检高级别概述

每个 AllJoyn 制造者公开公布自检 XML 呈现生成者的受支持的功能 – 接口作为所述通过信号、 属性和方法。  代码生成解决方案，如所示 AllJoyn Studio 扩展中，依赖于自检 XML 创建必要的代码以加快开发速度。  这样，两个不同的制造商可以使用 XML 来实现制造者具有相同功能，自检 XML 的非不明确的可读的方式描述的功能的生成者。  通过相同的令牌，AllJoyn 制造者没有上一个熟悉的开发人员应该能够针对该生成者根据其 XML 进行开发。

__AllJoyn Interfaces__

AllJoyn 通过分解为各种"接口"表示不同的行为和功能的逻辑分组的自检 XML 完成此操作。  使用反向 DNS 约定命名 AllJoyn 接口。 例如，Contoso Ltd.，后者拥有 contoso.com 域，通过创建的接口"Foo"界面将写为：

    <interface name="com.contoso.Foo">

生成者可能会实现任何数量的接口，但必须实现一个接口，它们将播发的每个组件。  为了区分和扩展行为，AllJoyn 支持与现有的接口层次结构; 创建新接口即`com.contoso.Foo.Bar`定义的情况下的新功能`Foo.Bar`类别，但没有任何显式依赖关系`com.contoso.Foo`接口。 

有关示例，我们有两个接口：`com.contoso.Sensor`和`com.contoso.Sensor.Humidity`–"湿度"逻辑上属于"传感器"类别下。  有人开发湿度制造者可以选择以支持只需`com.contoso.Sensor.Humdity`接口，但它们还可以选择以支持`com.contoso.Sensor`接口。  无论如何，如果他们在广告接口，然后生成者必须支持其所有功能。

`<description>`标记用于描述接口、 功能和自变量，并可本地化为多种语言。  自由使用`<description>`标记使 XML 更易于理解，并删除二义性。

标准做法将指示使用`org.alljoyn.Bus.Secure`实现安全和身份验证的接口上的批注。  对于强身份验证，使用预共享的密钥 (PSK) 或证书密钥交换 (ECDSA)。  否则，"null"身份验证将成为默认行为。  **在实现中，不能是声明发生实际的身份验证机制**。 此批注可以启用安全保护，但未指定使用的安全类型或它的实现方式。

___示例___

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

此示例显示了由设备公开的接口： `com.example.Door.PrivateDoor`。 在接口的范围内，我们所关注的唯一操作是机制的使用该接口，未使用哪种类型时，是否应受保护的通信。

__界面功能__

接口声明三个接口成员使用其功能： 方法、 属性或信号。 自检 XML 还支持批注来描述其他功能或约束。  这些功能使用 UpperCamelCase 表示法，而自变量使用 lowerCamelCase 表示法。

### <a name="argument-types"></a>参数类型

接口成员发送和接收参数为由一个 ASCII 类型代码。  根据接口成员的类型，自变量可能已被发送到制造者从使用者 (方向 ="out") 或从使用者流向生成者 (方向 ="in")。  下表提供了常用的类型的简要概述：

> | *传统的名称* | *Type-Code* | *将* |
> |----------------- |---------| --- |
> |**一个布尔值** | b | 表示 TRUE (1) 或 FALSE (0)。 用于简单的二进制信息或状态。 |
> |**BYTE** | y | 介于 0 到 255 之间的整数值。 在处理小正数和负数时使用。 |
> |**UINT16** | q | 整数值从 0 到 2 ^16 1 |
> |**UINT32** | u | 整数值从 0 到 2 ^32-1 |
> |**UINT64** | 的 VPN 连接下 | 整数值从 0 到 2 ^64-1 |
> |**INT16** | n | 从 –(2^15) 的整数值为 2 ^15-1 |
> |**INT32** | 图标 | 从 –(2^31) 的整数值为 2 ^31-1 |
> |**INT64** | x | 从 –(2^63) 的整数值为 2 ^63-1 |
> |**双精度** | d | 精度浮点数从 –(2^127) 到 2 ^127 1 |
> |**STRING** | 文件 | Utf-8 字符串 |
 
有关所有受支持的类型的更详尽概述，请参阅[此处](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448)。

撰写本文时，尽可能使用 SI 单位和清楚地表示预期的单位。 如果可能，请选择类型代码的限制性最强到你的方案;例如，如果你代表一个人的年龄的年数，然后使用字节、 不 UINT16 或 INT16，因为任何人都不负年龄或多个到 255 岁。  最新版本，应始终遵循[AllJoyn 接口查看板 (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board)指导原则。

下表总结了常见的单位：


> |*数量* | *单位*|
> |-------- | ---- |
> |**绝对时间 （日期和时间）** | 自 UNIX epoch 起经过的秒 (00: 00:00 自 1970 年 1 月 1 日) |
> |**当天的时间** | 自午夜以来的秒 |
> |**时间间隔** | 秒 |
> |**带宽** | 每秒位数 |
> |**数据大小** | 字节 |
 
### <a name="methods"></a>方法

使用者调用方法以修改状态的生成者，并且其名称应以动词开头，因为它们代表生成者执行操作的请求。  方法可能具有输入和输出自变量;在没有返回消息需要发送的情况下，将应用的批注"org.freedesktop.DBus.Method.NoReply"。  但是，AllJoyn 方法通常返回 SuccessResult 或 FailureResult，让使用者反馈有关方法调用。  参数的类型必须符合[D 总线规范](http://dbus.freedesktop.org/doc/dbus-specification.html)。 

___示例 （不包括为方便起见接口信息）___

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

*注意：在大多数情况下，属性应该用于而不是方法访问生成者的状态 （例如，而不是 GetColor 方法使用的颜色属性）。*

### <a name="properties"></a>属性

属性主要是允许访问生成者的状态。  虽然属性从技术上讲的访问值为"读取"、"readwrite"或"写入"，状态修改功能通常属于方法 – 这种情况下，开发人员应尽可能将属性保留为"读取"和"readwrite"仅当使用状态表示该属性是独立于所有其他属性。  属性应永远不会是只是"写入"-修改而无需观察状态是方法的角色。

其值更改时，必须对警报的使用者进行批注的属性 （或者，属性可以继承此批注及其父接口）。  批注`org.freedesktop.DBus.Property.EmitsChangedSignal`可以有四个值：

* "true"– 当属性更改，生成者将发出信号表示已更改的属性和新值。 使用中经常使用，需要 active 监督，如门"LockState"的属性。
* "使"– 当属性更改，生成者将发出信号表示已更改的属性，但不是新值。 属性不需要大量监督 （如"WashMode"衣服干燥器的) 或表示大量的数据，如容器中使用。
* "false"– 当属性更改，生成者发出没有信号。 在更新速度快，如跟踪人乘客地铁地铁门上的"TransitCounter"属性的属性中使用。 如果未指定，AllJoyn 属性将使用此为默认值。
* "const"– 该属性将永远不会更改值并永远不会发出已更改的信号。 这将是 AllJoyn 16.04 版本; 中引入到那时，使用"true"。

___示例___

基于前面的示例扩展，我们进行了修改 XML 以包括属性 （不包括为简洁起见方法）。

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

### <a name="signals"></a>信号

使用信号以通知使用者通过查询生成者无法确定的事件。  将通过使用"true"EmitsChangedProperty 批注的生成者的 DoorOpen 属性传达门打开。  某人通过门，但是，不能从派生的任何属性更改，因此这将使好独立信号。  我们之所以将这些类型的事件为"无状态"。  由于信号是从生成者到使用者是单向的它们可以仅包含"out"参数。

___示例___ 

（不包括方法和属性，为方便起见:）

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

由于信号有此类窄的范围，通常很少出现在生成者的 XML。

### <a name="containers"></a>容器

不执行操作将多个自变量组合到一系列复杂类似于序列化的 JSON 字符串。 D 总线规范可用于容器的数据 – 结构、 数组、 变体和 DICT_ENTRY 等。  使用这些设备需要多个基本类型的参数传递。

___变体___

变体类型"v"表示，并且可以包含任何[单一完整类型](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type)。 但是，变体应尽可能避免因为它们将不明确添加到 XML 定义。

___结构___

结构使用"（"和"）"来表示的开头和结尾的一种数据结构 – 单个完整的类型。  可以嵌套这些数据结构。

示例：

一种类型的"(iii)"表示三个整数; 的结构"(i(ii))"表示一个整数的结构和两个整数的结构不同于类型"((ii) 我)"。

___数组___

数组使用的类型代码"a"和后面必须有一个完整的类型。  数组不具有组长度，因此它们是类似于列表数据结构。 数组表示一个完整的类型。

示例：

一种类型的"ai"表示为整数数组，而"aai"表示一个整数数组的数组。  一个数组，可能会与结构也使用:"a(ii)"。

___DICT_ENTRY___

DICT_ENTRYs 函数类似于结构，它有更多的限制： 他们使用"{"和"}"，仅可能是为数组元素类型，并且必须具有完全完成大括号内的类型的两个。  第一种类型表示 dictionary 数据结构，在"密钥"，第二个表示字典的键 / 值对中的"值"。  键应为唯一在字典中。

例如：

一种类型的 {sy} 表示字符串键和字节值的字典。  将 <description> 若要描述有效的键和值的标记。 

__最后一个示例和 ajxmlcop__

容器的概念改进了现有的 XML，以及为新的有用的接口成员提供一种途径的功能。

完成编写 XML 后，使用 ajxmlcop.exe 命令行工具 (可在 AllJoyn [git 源](https://git.allseenalliance.org/cgit/core/alljoyn.git/)或[此处](https://github.com/MS-brock/AllJoynToasterDemo)) 来验证 XML。  Ajxmlcop.exe 使用 XML 文件用作输入参数 (例如， `C:\>ajxmlcop.exe doorExample.xml`) 来接收错误、 警告和信息性消息。  此工具提供有价值反馈的结构和 XML 的格式和用法的信号、 属性和方法。

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

