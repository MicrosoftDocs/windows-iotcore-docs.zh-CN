---
title: Arduino 接线移植指南
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何修改和部署 Arduino 绑定项目时出现的常见问题。
keywords: windows iot，Arduino，布线，Visual Studio 中，移植
ms.openlocfilehash: 9b1d54807c21a54d8186d7f7ddabc31f16d3dab3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510648"
---
# <a name="arduino-wiring-porting-guide"></a>Arduino 接线移植指南

Arduino 接线草图和库可在 Visual Studio 内复制/粘贴到 Arduino 接线项目，并在 Raspberry Pi 2、Raspberry Pi 3 或 Minnowboard Max 上运行。 有时需要对这些文件稍作修改，以便使它们与 Windows 环境或你正在使用的板更兼容。 本指南将涉及这些修改以及部署 Arduino 绑定项目时可能会遇到的常见问题。

## <a name="porting"></a>移植

### <a name="updating-pins"></a>更新引脚

不言而喻，许多草图和库（尤其是用于 Arduino 防护的草图和库）可能包含对 Arduino 设备的特定连接器引脚的引用。 你将要自定义你的草图来针对你正在处理的设备和你正在使用的配置使用相应的连接器引脚。

Arduino 接线最终需要引用“引脚”的任何函数的物理连接器引脚编号。 你可以直接使用这些编号，不过我们还提供了一些对应于特定板上的连接器引脚的预定义引脚名称。

例如，Raspberry Pi 2 和 3 上的物理连接器引脚 29 也称为 `GPIO5`。 你可以通过使用以下任一命令在 Raspberry Pi 2 和 3 上将 GPIO 引脚 5 设置为 HIGH 状态：
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

或

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

预定义的固定名称可在[pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) ，因此包含在 arduino 开发绑定每个项目中，但由于将有不同的物理连接器插针可用具体取决于你正在为创建硬件设置，我们决定此外包含此处的表来描述哪个 pin 名称均可用时为每个设备。

#### <a name="raspberry-pi-2-and-3"></a>Raspberry Pi 2 和 3

![引出线关系图](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | 引脚定义 | 相应的引脚编号|
> |-------------|----------|
> | LED_BUILTIN | *板载 LED* |
> | GPIO *_其中 * 指的是 [0，27]_ | *请参阅引出线图* |
> | GCLK | 7 |
> | 常规 *_其中 * 指的是 [0，5]_ | * 请参阅引出线图 |
> | SCL1 | 5 |
> | SDA1 | 3 |
> | CS0 （或 CE0 或 SS） | 24 |
> | CS1 （或 CE1） | 26 |
> | SCLK （或 SCK） | 23 |
> | MISO | 21 |
> | MOSI | 19 |
> | RXD | 10 |
> | TXD | 8 |

#### <a name="minnowboard-max"></a>Minnowboard Max

![引出线关系图](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | 引脚定义 | 相应的引脚编号|
> |-------------|----------|
> | GPIO *_其中 * 指的是 [0，9]_  | *请参阅引出线图* |
> | SCL | 13 |
> | SDA | 15 |
> | CS0 （或 CE0 或 SS） | 5 |
> | SCLK （或 SCK）| 11 |
> | MISO |7 |
> | MOSI | 9 |
> | CTS1 | 10 |
> | RTS1 | 12 |
> | RX1 | 8 |
> | TX1 | 6 |
> | RX2 | 19 |
> | TX2 | 17 |


## <a name="common-problems"></a>常见问题

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a>在 Visual Studio 中找不到“Arduino 接线应用程序”Visual C++ 项目模板

**原因**：未安装适用于 Visual Studio 的 Windows IoT 项目模板扩展。

**解决方案**：你必须先安装适用于 Windows IoT 项目模板的 Visual Studio 扩展才能在 Visual Studio 中创建 Arduino 接线项目。 转到 [Windows IoT 核心版项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472)来从 Visual Studio 库下载该扩展！

### <a name="error-identifier-not-found-when-calling-a-function"></a>错误：在调用某个函数时“找不到标识符”

**原因**：当调用尚未在文档中声明的函数时，在链接器过程中会发生此错误。

**解决方案**：在 C++ 中，所有函数都必须在调用前进行声明。 如果你已在草图文件中定义了新函数，该函数的声明或完整实现必须在任何调用它的尝试上方（通常在文档顶部）。

**示例**：

以下代码块将引发错误“‘myFunction’：找不到标识符”

```
void setup()
{

}

void loop()
{
    myFunction();
}

void myFunction()
{
    //do something
}
```

有两种解决方案。 首先，你可以在任何调用上方声明该函数。 通常，此声明在文件顶部完成。

```C++
// Declare function here
void myFunction();

void setup()
{

}

void loop()
{
    myFunction();
}

// And, define the function here
void myFunction()
{
    //do something
}
```

或者，您可以移动整个实现上述任何调用函数。 这会导致同时声明和定义该函数。

```C++
void setup()
{
}

void myFunction()
{
    //do something
}

void loop()
{
    myFunction();
}
```

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a>我的解决方案在初始化时无限期挂起

存在可能导致 C++ 解决方案在初始化时无限期挂起（死锁）的已知问题。 如果你发现你的解决方案看起来永久挂起，并且你无法使用调试器“闯入”Arduino 接线应用程序的 setup() 或 loop() 部分中的任何声明，则可能遇到此类型的问题。

**原因**：在解决方案完成初始化前创建了某个对象或调用了某个函数，从而导致异步操作。 这可能由对象的构造函数调用 `pinMode` 等 API 函数所导致。

**解决方案**：将任何对象构造函数和函数调用从代码的初始化部分中移开，并移到 `setup()` 块中。

**示例 1**：

在解决方案本身完成初始化前，此草图的执行会调用称为 `setPinModes()` 的函数。 解决方案将显示为执行，但会无限期挂起。

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized = setPinModes();

void setup()
{

}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

解决方案如下，我们仅仅将 `setPinModes()` 的执行移到 `setup()` 函数：

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized;

void setup()
{
    initialized = setPinModes();
}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

**示例 2**：

在调用 `setup()` 前，此草图的执行会在堆栈上创建一个对象。 由于对象在其构造函数中调用 `pinMode`，这还会导致死锁。 这不是常见问题，但可能在来自某些库（如 Arduino `LiquidCrystal` 库）的对象上发生。

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject myObject;

void setup()
{
}

void loop()
{
    myObject.doSomething();
}
```

解决方案如下。 我们已将对象更改为对象指针，并将对象的初始化移到了 `setup()`。

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject *myObject;

void setup()
{
    myObject = new MyObject();
}

void loop()
{
    myObject->doSomething();
}
```

### <a name="using-serialprint-and-serialprintln"></a>使用`Serial.print()`和 `Serial.println()`

许多 Arduino 草图使用 `Serial` 将数据打印到串行控制台（如果打开）或写入串行线（USB 或 tx/rx）。 在先前版本的闪电形 SDK，硬件`Serial`支持却未包括在内，因此我们提供`Log()`函数，该类将打印到调试器输出窗口 Visual Studio 中的。 `Serial.print*()` 或`Serial.write()`要被删除。

但是，从开始_闪电 SDK v1.1.0_，我们添加了`Hardware Serial`支持，并且两个`Serial.print*()`或`Serial.write()`完全支持函数。 因此，如果要复制生成的 Arduino 草图，您不需要替换这些串行中任何引用该草图的 Windows IoT 版本。

此外，我们已扩展的功能`Serial.print()`和`Serial.println()`、 附加调试器-除了写入硬件串行引脚时输出到调试器窗口。
调试输出打印设为读取输出是大多数用户希望何时以来默认值运行其草图。 但是，也; 禁用该功能例如为了提高性能，只需调用`Serial.enablePrintDebugOutput(false);`若要禁用在你的草图。 若要重新启用它，请调用`Serial.enablePrintDebugOutput(true);`。 这些调用不会影响硬件串行引脚写入。

请注意，不需要将任何外围设备附加到你串行引脚如 FTDI，若要获取输出发送到调试器窗口。 但是，你将需要确保在调试器窗口处于打开状态正在调试你的应用程序。

![调试程序输出](../media/ArduinoWiringPortingGuide/debugger_output.png)

已在上更新的项目模板[Windows IoT Core 项目模板扩展页](https://go.microsoft.com/fwlink/?linkid=847472)若要启用使用硬件`Serial`现成的。 但是，如果您 Arduino 绑定的应用程序已创建使用较旧的项目模板版本，你将需要 1） 将项目升级到最新的闪电形 SDK，v1.1.0 或更高版本，以及 2） 添加到所需的硬件串行设备功能在若要能够使用的 AppxManifest `Serial`。

### <a name="hardware-serial-device-capability-requirements"></a>硬件串行设备的功能要求

Windows 10 IoT 核心版中的硬件串行功能要求使用设备功能声明添加到 AppX 清单。

找到文件`Package.appxmanifest`在项目中，通过在解决方案资源管理器中键入文件名称。 然后，右键单击该文件并选择打开方式...。 选择 XML （文本） 编辑器并单击确定。

![正在更新 Package.appxmanifest](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

在 appx 清单文件编辑器中，添加`serialcommunication`DeviceCapability 到你的项目如以下 XML 代码片段中所示：

```xml
<Capabilities>
  <Capability Name="internetClient" />

  <!-- General Arduino Wiring required capabilities -->
  <iot:Capability Name="lowLevelDevices" />
  <DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>

  <!-- The serialcommunication capability is required to access Hardware Serial. --> 
  <DeviceCapability Name="serialcommunication">
    <Device Id="any">
      <Function Type="name:serialPort"/>
    </Device>
  </DeviceCapability>

</Capabilities>
```

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a>将项目升级到最新的闪电形 SDK

Arduino 绑定项目依赖于[闪电 SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning/)实现所需的 Arduino 绑定功能和声明以及使用闪电驱动程序的接口。 最新的闪电形 SDK 将包含最新改进和 bug 修复。 若要升级到最新的闪电形 SDK，请按照下列步骤：

- 在解决方案资源管理器，右键单击您的项目，然后单击管理 Nuget 包...
- 在 NuGet 包管理器中，转到已安装选项卡。你应看到安装了 Microsoft.IoT.Lightning 程序包
- 将版本组合框内，列出可用的版本。
- 选择最新版本，然后单击更新来更新包。
- 请注意，若要升级到的预发布版本，请确保选中包括预发行版复选框以及。

![NuGet 包管理器](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
