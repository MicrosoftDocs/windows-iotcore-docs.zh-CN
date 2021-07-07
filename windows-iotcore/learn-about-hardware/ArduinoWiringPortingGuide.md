---
title: Arduino 布线指南
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解部署 Arduino 接线图项目时出现的修改和常见问题。
keywords: windows iot，Arduino，布线，Visual Studio，移植
ms.openlocfilehash: 2f874e6fb1c22382fefde2b3480bd40b4824faf9
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229684"
---
# <a name="arduino-wiring-porting-guide"></a>Arduino 布线指南

可以将 Arduino 布线和库复制/粘贴到 Visual Studio 内的 Arduino 接线图，并在 Raspberry Pi 2 上运行，Raspberry Pi 3 或 Minnowboard Max。 有时需要对这些文件进行少量的修改，以便使它们与 Windows 环境或您正在使用的板更兼容。 本指南将介绍这些修改以及部署 Arduino 布线项目时可能遇到的常见问题。

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

**原因**：未安装适用于 Visual Studio 的 Windows IoT Project 模板扩展。

**解决方案**：必须先安装 Windows IoT Project 模板的 Visual Studio 扩展，然后才能在 Visual Studio 中创建 Arduino 接线图项目。 转到[Windows IoT Core Project 模板扩展 "页](https://go.microsoft.com/fwlink/?linkid=847472)，从 Visual Studio 库下载该扩展！

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

存在一个已知问题，可能会导致 c + + 解决方案在初始化时挂起 (死锁) 。 如果你发现你的解决方案看似始终挂起，并且你无法使用调试程序 "中断" 到安装 () 或循环 () Arduino 布线应用程序的任何语句，则可能会遇到这种类型的问题。

**原因**：正在创建对象或调用函数，这会导致在解决方案完成初始化之前出现 asyncronous 操作。 这可能是由对象的构造函数调用 API 函数（如）引起的 `pinMode` 。

**解决方案**：将任何对象构造函数和函数调用从代码的初始化部分移到块中 `setup()` 。

**示例 1**：

此草图的执行调用在初始化 `setPinModes()` 解决方案本身之前调用的函数。 该解决方案似乎要执行，但会无限期挂起。

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

解决方案如下，我们只需将 的执行 `setPinModes()` 移动到 `setup()` 函数：

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

此草图的执行在调用 之前在堆栈 `setup()` 上创建一个对象。 由于 对象在其 `pinMode` 构造函数中调用 ，因此也会导致死锁。 这是一个不常见的问题，但某些库（如 Arduino 库 (）中的对象 `LiquidCrystal`) 。

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

解决方案如下。 我们已将 对象更改为对象指针，并且将 对象的初始化移动到 `setup()` 。

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

许多 Arduino 草图使用 将数据打印到串行控制台 (如果打开) ，或者将数据写入 USB 或 `Serial` tx/rx (串行) 。
在早期版本的 Lightning SDK 中，未包括硬件支持，因此，我们提供了一个函数，该函数将输出到 Visual Studio `Serial` `Log()` 中的调试器输出窗口。 `Serial.print*()` 或 `Serial.write()` 必须删除。

但是，从 _Lightning SDK v1.1.0_ 开始，我们添加了支持，并且完全支持 或 `Hardware Serial` `Serial.print*()` `Serial.write()` 函数。 因此，如果要复制为 Arduino 构建的草图，则无需替换该草图的 Windows IoT 版本中的任何串行引用。

此外，除了写入硬件串行引脚，我们还扩展了 和 的功能，以在附加调试器时输出到调试 `Serial.print()` `Serial.println()` 器窗口。
调试输出打印设置为默认值，因为读取该输出是大多数用户在运行其草图时需要的输出。 但是，该功能也可以禁用;例如，若要提高性能，只需调用 以 `Serial.enablePrintDebugOutput(false);` 在草图中禁用它。 若要重新启用它，请调用 `Serial.enablePrintDebugOutput(true);` 。 写入硬件串行引脚不受这些调用的影响。

请注意，无需将任何外围设备附加到串行引脚（如 FTDI）中，就无需将输出发送到调试器窗口。 但是，需要在调试应用程序时确保调试器窗口已打开。

![调试器输出](../media/ArduinoWiringPortingGuide/debugger_output.png)

项目模板已在 Windows [IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) Project 模板扩展页上更新，以启用"硬件 `Serial` "开箱即用。 但是，如果 Arduino 布线应用程序已使用较旧的项目模板版本创建，则需要 1) 将项目升级到最新的 Lightning SDK、v1.1.0 或更高版本，以及 2) 将所需的硬件串行设备功能添加到 AppxManifest 才能使用 `Serial` 。

### <a name="hardware-serial-device-capability-requirements"></a>硬件串行设备功能要求

应用程序中的硬件串行Windows 10 IoT 核心版需要添加到 AppX 清单的设备功能声明。

在解决方案 `Package.appxmanifest` 资源管理器中键入文件名，找到项目中的文件。 然后，右键单击该文件，然后选择"打开时..."。 选择"XML (文本) 编辑器"，然后单击"确定"。

![更新 Package.appxmanifest](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

在 appx 清单文件编辑器中，将 `serialcommunication` DeviceCapability 添加到项目，如以下 XML 代码片段所示：

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

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a>将项目升级到最新的 Lightning SDK

Arduino 布线项目依赖于 Lightning [SDK Nuget](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) 包来实现所需的 Arduino 布线函数和声明，以及与闪电驱动程序的接口。 最新的 Lightning SDK 将包含最新的改进和 bug 修复。 若要升级到最新的 Lightning SDK，请执行以下步骤：

- 在解决方案资源管理器，右键单击项目，然后单击"管理 Nuget 包..."
- 在NuGet 程序包管理器，转到"已安装"选项卡。应会看到已安装 Microsoft.IoT.Lightning 包
- 可用版本将在"版本"组合框内列出。
- 选择最新版本，然后单击"更新"以更新包。
- 请注意，若要升级到预发行版本，请确保也选中"包括预发行版本"复选框。

![NuGet包管理器](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
