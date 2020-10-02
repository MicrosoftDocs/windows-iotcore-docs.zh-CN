---
title: Arduino 布线指南
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解部署 Arduino 接线图项目时出现的修改和常见问题。
keywords: windows iot，Arduino，布线，Visual Studio，移植
ms.openlocfilehash: 9f96c8e5b8b799690d31e1cd75574533773c0eaf
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655933"
---
# <a name="arduino-wiring-porting-guide"></a>Arduino 布线指南

可以将 Arduino 布线和库复制/粘贴到 Visual Studio 中的 Arduino 布线项目，并在 Raspberry Pi 2 上运行，Raspberry Pi 3 或 Minnowboard Max。 有时需要对这些文件进行少量的修改，以便使它们更兼容于 Windows 环境或您正在使用的板。 本指南将介绍这些修改以及部署 Arduino 布线项目时可能遇到的常见问题。

## <a name="porting"></a>移植

### <a name="updating-pins"></a>正在更新 Pin

它可能不会说，但许多草图和库 (特别是对于 arduino 的防护板，) 可能包含对 Arduino 设备的特定连接器针脚的引用。 你需要自定义草图，以便为你正在使用的设备和所使用的配置使用合适的连接器 pin。

Arduino 接线最终需要引用 "pin" 的任何功能的物理连接器 pin 号。 您可以直接使用这些数字，但我们还提供了一些预定义的 pin 名称，这些名称对应于特定板上的连接器 pin。

例如，Raspberry Pi 2 和3上的物理连接器引脚29也称为 `GPIO5` 。 可以使用以下命令之一，将 GPIO 引脚5设置为 Raspberry Pi 2 和3上的高状态：
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

或

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

可以在 [pins_arduino](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) 中找到预定义的 pin 名称，并将其包含在每个 arduino 布线项目中，但由于要生成的硬件设置，还可以使用不同的物理连接器 pin，我们还在此处提供了一个表，用于说明每个设备的可用 pin 名称。

#### <a name="raspberry-pi-2-and-3"></a>Raspberry Pi 2 和 3

![引线关系图](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | 固定定义 | 对应的 Pin 号|
> |-------------|----------|
> | LED_BUILTIN | *板载 LED* |
> | GPIO * _where * 指 [0，27]_ | *请参阅引线关系图* |
> | GCLK | 7 |
> | GEN * _where * 指 [0，5]_ | * 参阅引线关系图 |
> | SCL1 | 5 |
> | SDA1 | 3 |
> | CS0 (或 CE0 或 SS)  | 24 |
> | CS1 (或 CE1)  | 26 |
> | SCLK (或 SCK)  | 23 |
> | MISO | 21 |
> | MOSI | 19 |
> | RXD | 10 |
> | TXD | 8 |

#### <a name="minnowboard-max"></a>Minnowboard Max

![引线关系图1](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | 固定定义 | 对应的 Pin 号|
> |-------------|----------|
> | GPIO * _where * 指 [0，9]_  | *请参阅引线关系图* |
> | SCL | 13 |
> | SDA | 15 |
> | CS0 (或 CE0 或 SS)  | 5 |
> | SCLK (或 SCK) | 11 |
> | MISO |7 |
> | MOSI | 9 |
> | CTS1 | 10 |
> | RTS1 | 12 |
> | RX1 | 8 |
> | TX1 | 6 |
> | RX2 | 19 |
> | TX2 | 17 |


## <a name="common-problems"></a>常见问题

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a>Visual Studio 中找不到 "Arduino 接线图应用程序" Visual C++ 项目模板

**原因**：未安装适用于 Visual Studio 的 Windows IoT 项目模板扩展。

**解决方案**：必须安装适用于 Windows IoT 项目模板的 Visual studio 扩展，然后才能在 Visual studio 中创建 Arduino 接线图项目。 转到 [Windows IoT Core 项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472) 以从 Visual Studio 库中下载扩展！

### <a name="error-identifier-not-found-when-calling-a-function"></a>错误：调用函数时出现 "找不到标识符"

**原因**：调用未在文档中声明的函数时，在链接器过程中会出现此错误。

**解决方案**：在 c + + 中，所有函数都必须在调用之前声明。 如果您在草图文件中定义了一个新函数，则该函数的声明或整个实现都必须在任何尝试调用它的任何尝试 (通常在文档) 的顶部。

**示例**：

下面的代码块将引发错误 "' myFunction '：找不到标识符"

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

有两种解决方案。 首先，可以在任何调用上声明函数。 通常，此声明在文件顶部进行。

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

或者，您可以将函数的整个实现移动到任何调用的上面。 这会同时同时声明和定义函数。

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

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a>在初始化时，解决方案会无限期挂起

存在一个已知问题，可能会导致 c + + 解决方案在初始化时挂起 (死锁) 。 如果您发现您的解决方案看似始终挂起，并且您无法使用调试程序 "中断" 到安装程序 ( # A1 或 ( 循环中的任何语句，则可能会遇到这种类型的问题 Arduino 接线图。

**原因**：正在创建对象或调用函数，这会导致在解决方案完成初始化之前出现 asyncronous 操作。 这可能是由对象的构造函数调用 API 函数（如）引起的 `pinMode` 。

**解决方案**：将任何对象构造函数和函数调用从代码的初始化部分移到块中 `setup()` 。

**示例 1**：

此草拟的执行将调用一个函数，该函数在 `setPinModes()` 解决方案自身初始化之前被调用。 解决方案似乎会执行，但会无限期挂起。

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

解决方案如下所示，我们只是将执行操作移 `setPinModes()` 到了 `setup()` 函数：

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

在调用之前，该草绘在堆栈上创建一个对象 `setup()` 。 因为对象 `pinMode` 在其构造函数中调用，这也会导致死锁。 这是一种不常见的问题，但可能会发生某些库中的对象 (如 Arduino `LiquidCrystal` 库) 。

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

解决方案如下。 我们已将对象更改为对象指针，并将对象的初始化移到 `setup()` 。

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

### <a name="using-serialprint-and-serialprintln"></a>使用 `Serial.print()` 和 `Serial.println()`

许多 Arduino 草绘使用 `Serial` 将数据打印到串行控制台 (如果打开) 或写入到 (USB 或 tx/rx) 的串行行。
在以前版本的闪电 SDK 中， `Serial` 不包括硬件支持，因此我们提供了一个 `Log()` 函数，该函数将打印到 Visual Studio 中的 "调试器输出" 窗口。 `Serial.print*()` 或者 `Serial.write()` 必须删除。

但是，从 _闪电 1.1.0_开始，我们添加了 `Hardware Serial` 支持，并 `Serial.print*()` `Serial.write()` 完全支持或函数。 因此，如果您要复制为 Arduino 生成的草绘，则不需要替换该草图的 Windows IoT 版本中的任何这些序列引用。

此外，我们还扩展了和的 `Serial.print()` 功能 `Serial.println()` ，以便在附加调试器时输出到调试器窗口-除了写入硬件串行 pin 外。
调试输出打印设置为默认值，因为在读取输出后，大多数用户都需要该输出。 但是，也可以禁用该功能;例如，为了提高性能，只需调用 `Serial.enablePrintDebugOutput(false);` 即可在草图中禁用它。 若要重新启用，请调用 `Serial.enablePrintDebugOutput(true);` 。 写入硬件串行端口不受这些调用的影响。

请注意，不需要将任何外围设备连接到串行 pin （如 FTDI），即可获取发送到调试器窗口的输出。 但是，你需要确保在调试你的应用程序时调试器窗口处于打开状态。

![调试器输出](../media/ArduinoWiringPortingGuide/debugger_output.png)

已在 [Windows IoT Core 项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472) 上更新项目模板，以允许使用现成的硬件 `Serial` 。 但是，如果你的 Arduino 配应用程序已使用较旧的项目模板版本创建，则需要) 将项目升级到最新的闪电 SDK、v 1.1.0 或更高版本，并 2) 将所需的硬件串行设备功能添加到你的 Appxmanifest.xml，以便能够使用 `Serial` 。

### <a name="hardware-serial-device-capability-requirements"></a>硬件串行设备功能要求

Windows 10 IoT Core 中的硬件串行功能要求向 AppX 清单添加设备功能声明。

在 `Package.appxmanifest` "解决方案资源管理器" 中键入文件名，查找项目中的文件。 然后，右键单击该文件，然后选择 "打开方式 ..."。 选择 "XML (文本) 编辑器"，然后单击 "确定"。

![正在更新包。 appxmanifest.xml](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

在 appx 清单文件编辑器中，将 `serialcommunication` DeviceCapability 添加到你的项目中，如以下 XML 代码片段所示：

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

Arduino 布线项目依赖于 [闪电 SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) 来实现所需的 Arduino 布线功能和声明，并与闪电驱动程序建立接口。 最新的闪电 SDK 将包含最新的改进和 bug 修复。 若要升级到最新的闪电 SDK，请执行以下步骤：

- 在解决方案资源管理器中，右键单击你的项目，然后单击 "管理 Nuget 包 ..."
- 在 NuGet 包管理器中，切换到 "已安装" 选项卡。应会看到已安装的 ""
- 可用版本将在 "版本" combobox 内列出。
- 选择最新版本，并单击 "更新" 更新您的包。
- 请注意，若要升级到预发布版本，请务必选中 "包括预发行版" 复选框。

![NuGet 包管理器](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
