---
title: Arduino 接线移植指南
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解部署 Arduino 接线图项目时出现的修改和常见问题。
keywords: windows iot, Arduino, 布线, Visual Studio, 移植
ms.openlocfilehash: 9b1d54807c21a54d8186d7f7ddabc31f16d3dab3
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169987"
---
# <a name="arduino-wiring-porting-guide"></a>Arduino 接线移植指南

Arduino 接线草图和库可在 Visual Studio 内复制/粘贴到 Arduino 接线项目，并在 Raspberry Pi 2、Raspberry Pi 3 或 Minnowboard Max 上运行。 有时需要对这些文件稍作修改，以便使它们与 Windows 环境或你正在使用的板更兼容。 本指南将介绍这些修改以及部署 Arduino 布线项目时可能遇到的常见问题。

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

可以在[pins_arduino](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h)中找到预定义的 pin 名称, 并将其包含在每个 arduino 布线项目中, 但由于要为构建的硬件设置, 提供了不同的物理连接器 pin, 因此我们还提供了一个表此处说明每个设备的可用 pin 名称。

#### <a name="raspberry-pi-2-and-3"></a>Raspberry Pi 2 和 3

![引线关系图](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | 引脚定义 | 相应的引脚编号|
> |-------------|----------|
> | LED_BUILTIN | *板载 LED* |
> | GPIO * _where * 指 [0, 27]_ | *请参考引出线图* |
> | GCLK | 7 |
> | GEN * _where * 指 [0, 5]_ | \* 参阅引线关系图 |
> | SCL1 | 5 |
> | SDA1 | 3 |
> | CS0 (或 CE0 或 SS) | 24 |
> | CS1 (或 CE1) | 26 |
> | SCLK (或 SCK) | 23 |
> | MISO | 21 |
> | MOSI | 19 |
> | RXD | 10 |
> | TXD | 8 |

#### <a name="minnowboard-max"></a>Minnowboard Max

![引线关系图](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | 引脚定义 | 相应的引脚编号|
> |-------------|----------|
> | GPIO * _where * 指 [0, 9]_  | *请参考引出线图* |
> | SCL | 13 |
> | SDA | 15 |
> | CS0 (或 CE0 或 SS) | 5 |
> | SCLK (或 SCK)| 11 |
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

或者, 您可以将函数的整个实现移动到任何调用的上面。 这会导致同时声明和定义该函数。

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

### <a name="using-serialprint-and-serialprintln"></a>使用`Serial.print()`和`Serial.println()`

许多 Arduino 草图使用 `Serial` 将数据打印到串行控制台（如果打开）或写入串行线（USB 或 tx/rx）。 在以前版本的闪电 SDK 中, 不`Serial`包括硬件支持, 因此我们提供了`Log()`一个函数, 该函数将打印到 Visual Studio 中的 "调试器输出" 窗口。 `Serial.print*()`或者`Serial.write()`必须删除。

但是, 从_闪电 1.1.0_开始, 我们添加`Hardware Serial`了支持, 并`Serial.print*()`完全支持或`Serial.write()`函数。 因此, 如果您要复制为 Arduino 生成的草绘, 则不需要替换该草图的 Windows IoT 版本中的任何这些序列引用。

此外, 我们还扩展了`Serial.print()`和`Serial.println()`的功能, 以便在附加调试器时输出到调试器窗口-除了写入硬件串行 pin 外。
调试输出打印设置为默认值, 因为在读取输出后, 大多数用户都需要该输出。 但是, 也可以禁用该功能;例如, 为了提高性能, 只需`Serial.enablePrintDebugOutput(false);`调用即可在草图中禁用它。 若要重新启用, 请调用`Serial.enablePrintDebugOutput(true);`。 写入硬件串行端口不受这些调用的影响。

请注意, 不需要将任何外围设备连接到串行 pin (如 FTDI), 即可获取发送到调试器窗口的输出。 但是, 你需要确保在调试你的应用程序时调试器窗口处于打开状态。

![调试器输出](../media/ArduinoWiringPortingGuide/debugger_output.png)

已在[Windows IoT Core 项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472)上更新项目模板, 以允许使用现成的`Serial`硬件。 但是, 如果你的 Arduino 配应用程序已使用较旧的项目模板版本创建, 则需要 1) 将项目升级到最新的闪电 SDK, v 1.1.0 或更高版本, 并 2) 将所需的硬件串行设备功能添加到你的能够使用`Serial`的 appxmanifest.xml。

### <a name="hardware-serial-device-capability-requirements"></a>硬件串行设备功能要求

Windows 10 IoT Core 中的硬件串行功能要求向 AppX 清单添加设备功能声明。

在 "解决方案`Package.appxmanifest`资源管理器" 中键入文件名, 查找项目中的文件。 然后, 右键单击该文件, 然后选择 "打开方式 ..."。 选择 "XML (文本) 编辑器", 然后单击 "确定"。

![正在更新包。 appxmanifest.xml](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

在 appx 清单文件编辑器中, 将`serialcommunication` DeviceCapability 添加到你的项目中, 如以下 XML 代码片段所示:

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

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a>将项目升级到最新的闪电 SDK

Arduino 布线项目依赖于[闪电 SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning/)来实现所需的 Arduino 布线功能和声明, 并与闪电驱动程序建立接口。 最新的闪电 SDK 将包含最新的改进和 bug 修复。 若要升级到最新的闪电 SDK, 请执行以下步骤:

- 在解决方案资源管理器中, 右键单击你的项目, 然后单击 "管理 Nuget 包 ..."
- 在 NuGet 包管理器中, 切换到 "已安装" 选项卡。应会看到已安装的 ""
- 可用版本将在 "版本" combobox 内列出。
- 选择最新版本, 并单击 "更新" 更新您的包。
- 请注意, 若要升级到预发布版本, 请务必选中 "包括预发行版" 复选框。

![NuGet 包管理器](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
