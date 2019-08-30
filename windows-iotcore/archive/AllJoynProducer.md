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
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题, 请在 GitHub 上提出问题, 或在下面的评论中留下反馈。

# <a name="alljoyn-producers"></a>AllJoyn 制造者

通过[AllSeen 联盟](https://allseenalliance.org/)创建的 AllJoyn 提供了一个很好的框架, 用于在最近网络上建立连接的设备和应用, Windows 提供了在适用于 Visual Studio 的[alljoyn studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)扩展的情况下使用 alljoyn 的最佳体验。  虽然我们的工具为创建适用于创建者和使用者的应用程序, 但从头开始新的 AllJoyn 设备可能会令人费解。

如果你对下一个连接良好的设备或用于 tinker 和浏览的新玩具有看法, 则可能无法使用 AllSeen 联盟提供的标准接口之一。  如果是这样, 则需要创建全新的 AllJoyn 制造者。

想要让新的 AllJoyn 制造者创作自己的自检 XML 的开发人员需要创作自己的 XML, 但创建自检 XML 需要使用者专业知识, 并为新开发人员提供重要的学习曲线。  这 blogpost 将通过分解自检 XML 的各种组件、描述每个组件的用途和限制以及提供易学术语中的好示例, 来降低学习曲线。

## <a name="existing-documentation"></a>现有文档

粗略检查以下与此 blogpost 结合的资源应加速开发人员了解自检 XML:

1. [Alljoyn 事件和操作 API 指南](https://allseenalliance.org/developers/develop/api-guide/events-and-actions)– alljoyn 实现细节和概述。
2. [Alljoyn Interface 审查板设计准则](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0)-适用于 ALLJOYN 自检 XML 的严格结构和规范。
3. [D 总线规范](http://dbus.freedesktop.org/doc/dbus-specification.html)–此规范中的自检 XML。

__这三种类型的自检 XML__

当你细读 AllJoyn 文档时, 你会发现三种类型的自检 XML:

1. D 总线规范 XML: 开销较低, 与数据表示形式的类型格式进行进程间通信。
2. AllJoyn 自检 XML: 扩展了用于保存文本说明的 D 总线规范 XML 和 XML 标记, 同时还将 AllJoyn 原则应用于该规范。
3. 扩展的 AllJoyn 自检 XML: 经典自检 XML 演化介绍了结构和字典的命名类型。

AllJoyn Studio 当前支持 D 总线规范 XML 和 AllJoyn 自检 XML;此博客将指导如何创建和形成 AllJoyn 自检 XML。  AllSeen 联盟的接口审查委员会 (IRB) 使用新的扩展 AllJoyn 自检作为标准版报送的格式, 但在不久的将来, 将使用统一的自检 XML 格式。

## <a name="introspection-high-level-overview"></a>自检高级概述

每个 AllJoyn 制造者公开广告自检 XML, 该 XML 显示了生成者支持的功能 (如通过信号、属性和方法说明的接口)。  类似于 AllJoyn Studio 扩展中的代码生成解决方案, 它依赖自检 XML 来创建必要的代码以加速开发。  自检 XML 以用户可读的非歧义方式描述了制造者的功能, 这样两个不同的制造商就可以使用 XML 来实现具有相同功能的生成者。  同一个令牌, 没有对 AllJoyn 制造者的事先了解的开发人员应能够基于其 XML 进行开发。

__AllJoyn 接口__

AllJoyn 实现此操作的方法是: 将自检 XML 分解为各种不同的 "接口", 表示行为和功能的不同逻辑分组。  使用反向 DNS 约定命名 AllJoyn 接口。 例如, Contoso 公司 (拥有 contoso.com 域) 创建的接口 "Foo" 接口将编写为:

    <interface name="com.contoso.Foo">

制造者可以实现任意数量的接口, 但必须实现其播发的接口的每个组件。  为了区分和扩展行为, AllJoyn 支持在现有接口层次结构方面创建新接口;即, `Foo.Bar` `com.contoso.Foo`定义类别下的项目的新功能, 但不会在接口上具有任何显式依赖项。 `com.contoso.Foo.Bar` 

例如, 我们有两个接口: `com.contoso.Sensor`和`com.contoso.Sensor.Humidity` – "湿度" 逻辑落在 "传感器" 类别下。  开发湿度制造者的人员可以选择仅`com.contoso.Sensor.Humdity`支持接口, 但也可以选择`com.contoso.Sensor`支持接口。  无论如何, 如果它们公布一个接口, 则创建者必须支持其所有功能。

`<description>`标记用于描述接口、功能和参数, 并可针对各种语言进行本地化。  使用`<description>`标记的自由使用使得 XML 更易于理解, 并消除了歧义。

标准做法规定在接口上使用`org.alljoyn.Bus.Secure`批注来实现安全性和身份验证。  对于强身份验证, 请使用预共享密钥 (PSK) 或证书密钥交换 (ECDSA)。  否则, "null" 身份验证成为默认行为。  **实际的身份验证机制发生在实现中, 而不是声明**。 此批注启用安全性, 但不指定所使用的安全类型或其实现方式。

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

此示例演示设备公开的接口: `com.example.Door.PrivateDoor`。 在接口的作用域中, 唯一要注意的是, 在使用该接口时是否应保护通信, 而不是使用哪种类型的机制。

__接口功能__

接口声明其功能和三个接口成员: 方法、属性或信号。 自检 XML 还支持描述附加功能或约束的批注。  这些功能使用 UpperCamelCase 表示法, 而参数使用 lowerCamelCase 表示法。

### <a name="argument-types"></a>参数类型

接口成员发送和接收由 ASCII 类型代码表示的参数。  根据接口成员的类型, 可能会将参数从使用者 (方向 = "out") 或使用者发送到制造者 (方向 = "in")。  下表提供了常用类型的简要概述:

> | *传统名称* | *类型代码* | *用途* |
> |----------------- |---------| --- |
> |**变量** | b | 表示 TRUE (1) 或 FALSE (0)。 用于简单的二进制信息或状态。 |
> |**BYTE** | y | 介于0到255之间的整数值。 处理较小的正数时使用。 |
> |**UINT16** | q | 0到 2 ^ 16-1 之间的整数值 |
> |**UINT32** | 形 | 0到 2 ^ 32-1 之间的整数值 |
> |**UINT64** | 的 VPN 连接下 | 0到 2 ^ 64-1 之间的整数值 |
> |**INT16** | n | 从– (2 ^ 15) 到 2 ^ 15-1 的整数值 |
> |**INT32** | 图标 | 从– (2 ^ 31) 到 2 ^ 31-1 的整数值 |
> |**INT64** | x | 从– (2 ^ 63) 到 2 ^ 63-1 的整数值 |
> |**仔细** | d | 从– (2 ^ 127) 到 2 ^ 127-1 的精度浮点数 |
> |**类似** | 文件 | UTF-8 字符串 |
 
有关所有受支持类型的更详尽概述, 请参阅[此处](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448)。

在撰写本文时, 尽可能使用 SI 单位, 并清楚地表示预期单位。 如果可能, 请选择对方案最严格的类型代码;例如, 如果你表示某个人的年龄 (年), 则使用 BYTE, 而不是 UINT16 或 INT16, 因为没有任何人将为负年龄或超过255岁。  始终遵循最新的[AllJoyn 接口查看委员会 (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board)准则。

下表汇总了常用单位:


> |*Quantity* | *单位*|
> |-------- | ---- |
> |**绝对时间 (日期 & 时间)** | 自 UNIX Epoch 以来的秒数 (00:00:00 年1月 1970 1 日) |
> |**当天的时间** | 午夜后的秒数 |
> |**时间间隔** | 秒 |
> |**带宽** | 每秒位数 |
> |**数据大小** | 字节 |
 
### <a name="methods"></a>方法

使用者调用方法来修改制造者的状态, 其名称应以动词开头, 因为它们表示对生成者执行操作的请求。  方法可能具有输入参数和输出参数;如果不需要发送任何返回消息, 则应用批注 "freedesktop. NoReply" ()。  但是, AllJoyn 方法通常会返回 SuccessResult 或 FailureResult, 并向使用者提供有关方法调用的反馈。  自变量的类型必须符合[D 总线规范](http://dbus.freedesktop.org/doc/dbus-specification.html)。 

___示例 (为了方便起见, 不包括接口信息)___

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

*注意：在大多数情况下, 应使用属性而不是方法来访问制造者的状态 (例如, 使用颜色属性, 而不是 GetColor 方法)。*

### <a name="properties"></a>属性

属性主要允许访问制造者的状态。  虽然在技术上, 属性具有 "读取"、"读写" 或 "写入" 访问值, 但状态修改功能通常属于方法–因此, 开发人员应尽量将属性设置为 "读取", 并仅在所表示的状态下使用 "readwrite"此属性与所有其他属性无关。  属性绝不应该只是 "write"-修改状态, 而不会观察到方法的角色。

当属性值发生更改时, 必须将属性批注到警报使用者 (可以选择, 属性可以从其父接口继承此注释)。  批注`org.freedesktop.DBus.Property.EmitsChangedSignal`可以有四个值:

* "true" –当属性发生更改时, 生成者将发出一个指示已更改属性和新值的信号。 用于经常使用的属性, 并需要积极的监督, 如 "LockState"。
* "无效" –当属性发生更改时, 制造者将发出一个指示已更改属性但不发出新值的信号。 用于不需要大量监督的属性 (例如衣服烘干机的 "WashMode") 或表示大量数据, 如容器。
* "false" –当属性更改时, 制造者不发出信号。 用于快速更新的属性中, 例如地铁的 "TransitCounter" 属性。 如果未指定, 则 AllJoyn 属性将此用作默认值。
* "const" –属性永远不会更改值, 也不会发出更改的信号。 这将在 AllJoyn 16.04 版中引入;在此之前, 请使用 "true"。

___示例___

在前面的示例中, 我们已将 XML 修改为包含属性 (为简洁起见, 不包括方法)。

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

使用信号, 通过查询制造者来向使用者通知事件无法确定。  门打开将通过具有 "true" EmitsChangedProperty 批注的生成者 DoorOpen 属性传达。  但是, 通过门的某个人无法从任何属性更改中派生, 因此, 这会产生一个良好的单独信号。  我们将这类事件称为 "无状态"。  由于信号从制造者到使用者是单向的, 因此它们只能包含 "out" 参数。

___示例___ 

(为方便起见, 不包括方法和属性):

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

由于信号具有这样的范围范围, 因此在生成者的 XML 中通常会出现少量的情况。

### <a name="containers"></a>容器

不要将多个参数合并为复杂集合, 如序列化的 JSON 字符串。 D 总线规范为数据容器 (结构、数组、变体和 DICT_ENTRY) 提供实用。  使用这些参数传递需要基本类型以上的参数。

___变体___

变体由类型 "v" 表示, 并且可以包含任何[一个完整类型](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type)。 但是, 应尽可能避免变量, 因为它们向 XML 定义增加了歧义。

___STRUCT___

结构使用 "(" 和 ")" 表示数据结构的开头和结尾–一种完整的类型。  这些数据结构可以嵌套。

例如：

类型 "(iii)" 表示三个整数的结构;"(i (ii))" 表示整数和两个整数的结构的结构, 该结构不同于类型 "((ii) i)"。

___组成___

数组使用类型代码 "a", 后面必须有一个完整类型。  数组没有设置长度, 因此它们类似于列表数据结构。 数组表示一个完整类型。

例如：

"Ai" 类型表示整数的数组, 而 "aai" 表示整数数组的数组。  数组也可以与结构一起使用: "a (ii)"。

___DICT_ENTRY___

DICT_ENTRYs 函数类似于具有更大限制的结构: 它们使用 "{" 和 "}", 只能作为数组元素类型出现, 并且在大括号内必须正好有两个完整类型。  第一种类型表示字典数据结构中的 "键", 第二种类型表示字典的键值对中的 "值"。  密钥在字典中应该是唯一的。

例如：

{Sy} 的一种类型表示字符串键和字节值的字典。  将 <description> 用于描述有效密钥和值的标记。 

__最终示例和 ajxmlcop__

容器的概念改善了现有 XML 的功能, 并为新的有用接口成员提供途径。

编写完 XML 后, 请使用 ajxmlcop 命令行工具 (在 AllJoyn [git 源](https://git.allseenalliance.org/cgit/core/alljoyn.git/)或[此处](https://github.com/MS-brock/AllJoynToasterDemo)提供) 来验证 xml。  使用 ajxmlcop 作为输入参数 (例如, `C:\>ajxmlcop.exe doorExample.xml`) 来接收错误、警告和信息性消息。  此工具提供了有关 XML 的结构和格式以及信号、属性和方法使用的有价值的反馈。

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

