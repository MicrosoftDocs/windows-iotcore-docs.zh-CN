---
title: 开发前台应用程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解 IoT Core 支持的语言和应用类型。
keywords: windows iot, 语言, 应用类型, UWP, 受支持
ms.openlocfilehash: e0eb046ba874e8433e7632d3f88a63a90b88fa2b
ms.sourcegitcommit: 8a197111b5b7814b924d77dfea5f9d38760d4288
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2019
ms.locfileid: "67627395"
---
# <a name="developing-foreground-applications"></a>开发前台应用程序
了解 Windows 10 IoT Core 支持的语言, 以及 IoT Core 支持的 UWP 和非 UWP 应用类型。


> [!NOTE]
> 在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。

## <a name="application-types"></a>应用程序类型
___

### <a name="universal-windows-platform-uwp-apps"></a>通用 Windows 平台 (UWP) 应用
IoT Core 是一个以 UWP 为中心的操作系统, UWP 应用是其主要的应用类型。

通用 Windows 平台 (UWP) 是跨 Windows 10 的所有版本 (包括 Windows 10 IoT Core) 的通用应用平台。  UWP 是 Windows 运行时 (WinRT) 的演变。 可在[此处](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)找到有关 UWP 的详细信息和概述。

Visual Studio 是用于为 IoT 核心编写 UWP 应用的主要工具。 可在[此处](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs)找到有关 Visual Studio 的兼容性要求的详细列表。


### <a name="traditional-uwp-apps"></a>传统 UWP 应用
UWP 应用只需在 IoT Core 上工作, 就像在其他 Windows 10 版本上一样。 在 Visual Studio 中, 简单的空白 Xaml 应用程序将正确部署到 IoT Core 设备, 就像在手机或 Windows 10 电脑上一样。 IoT 核心完全支持所有标准 UWP 语言和项目模板。

传统 UWP 应用模型中添加了一些内容来支持 IoT 方案, 任何利用这些方案的 UWP 应用都需要将相应信息添加到其清单中。 特别是, 需要将 "iot" 命名空间添加到这些标准 UWP 应用的清单中。 

在清单的属性中, 需要定义 iot xmlns, 并将其添加到 IgnorableNamespaces 列表中。 <Package> 最终 xml 应如下所示: 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a>后台应用
除了传统的 UI 应用外, IoT Core 还添加了一个名为 "后台应用程序" 的新 UWP 应用类型。 这些应用程序不具有 UI 组件, 而是具有实现 "IBackgroundTask" 接口的类。 然后, 它们将该类注册为 "StartupTask" 以在系统启动时运行。 由于它们仍是 UWP 应用程序, 因此它们可以访问同一组 Api 并支持同一语言的。 唯一的区别是没有 UI 入口点。

每种类型的 IBackgroundTask 均获取其自己的资源策略。 此限制通常是为了改进设备上的电池寿命和计算机资源, 这些应用程序是前景 UI 应用程序的辅助组件。 在 IoT 设备上, 后台应用通常是设备的主要功能, 因此这些 StartupTasks 获取了在其他设备上镜像前景 UI 应用的资源策略。

下面的示例演示生成使 LED 闪烁的C#后台应用程序所需的代码:

```C#
namespace BlinkyHeadlessCS
{
    public sealed class StartupTask : IBackgroundTask
    {
        BackgroundTaskDeferral deferral;
        private GpioPinValue value = GpioPinValue.High;
        private const int LED_PIN = 5;
        private GpioPin pin;
        private ThreadPoolTimer timer;

        public void Run(IBackgroundTaskInstance taskInstance)        {
            deferral = taskInstance.GetDeferral();
            InitGPIO();
            timer = ThreadPoolTimer.CreatePeriodicTimer(Timer_Tick, TimeSpan.FromMilliseconds(500));

        }
        private void InitGPIO()
        {
            pin = GpioController.GetDefault().OpenPin(LED_PIN);
            pin.Write(GpioPinValue.High);
            pin.SetDriveMode(GpioPinDriveMode.Output);
        }

        private void Timer_Tick(ThreadPoolTimer timer)
        {
            value = (value == GpioPinValue.High) ? GpioPinValue.Low : GpioPinValue.High;
            pin.Write(value);
        }
    }
}
```

可在[此处](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)找到有关后台应用的详细信息。

### <a name="non-uwp-apps"></a>非 UWP 应用
IoT 核心支持某些传统的 Win32 应用类型, 如 Win32 控制台应用和 NT 服务。 这些应用的构建和运行方式与在 Windows 10 桌面上的运行方式相同。 此外, 还有一个 IoT Core C++控制台项目模板, 可以使用 Visual Studio 轻松生成此类应用。

对于这些非 UWP 应用程序, 有两个主要限制:
1. *无旧版 Win32 UI 支持:* IoT Core 不包含用于创建经典 (HWND) 窗口的 Api。 传统方法 (如 CreateWindow () 和 CreateWindowEx ()) 或处理 Windows 句柄 (Hwnd) 的任何其他方法均不可用。 随后, 在 IoT Core 上不支持依赖于此类 Api 的框架 (包括 MFC、Windows 窗体和 WPF)
2. *C++仅适用于应用:* 目前, 仅C++支持在 IoT Core 上开发 Win32 应用。

## <a name="programming-languages"></a>编程语言
___

IoT 核心支持多种编程语言。

### <a name="in-box-languages"></a>内置语言
默认情况下, 传统的 UWP 语言附带了 Visual Studio 支持。 所有内置语言都支持 UI 和后台应用程序
 
* 语言
  * C#
  * C++
  * Javascript
  * Visual Basic

### <a name="arduino-wiring"></a>Arduino 接线
 Arduino 接线需要从 Visual Studio**工具-> 扩展和更新**管理器下载 "Windows IoT 核心项目模板"。  Arduino 布线仅支持后台应用程序。 你还可以使用C#、 C++或 Visual Basic 生成*Windows 运行时组件*, 然后从任何其他语言中引用这些库。

### <a name="c-and-visual-basic-vb"></a>C#和 Visual Basic (VB)
C#和 VB 都支持作为 UWP 应用, 并且可以访问可用于 UWP 应用程序的 .Net Framework 的一部分。 它们支持通过 Xaml 和后台应用程序生成的 UI 应用。 你还可以构建可用于其他支持的语言的*Windows 运行时组件*。

范例


* [C#Blinky 无外设](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CS)
* [VB Blinky 无外设](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB)
* [C#Blinky UI 应用](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/CS)


### <a name="javascript"></a>Javascript
可以使用 Javascript 来构建 UI 和后台应用。 UI 应用的工作方式与在所有 UWP 版本上的工作方式相同。 后台应用是 IoT Core 的新应用, 但非常简单。 下面的示例代码演示了*JS New 项目模板*的输出:

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a>C++
利用C++ , 你可以构建 Xaml 或 DirectX UI 应用以及 UWP 背景项目和*非 UI* Win32 应用。

范例

* [Blinky 无外设](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [Blinky 头](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [控制台应用](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus/CPP)

> [!NOTE]
> 对于计划在中C++编写应用程序的用户, 需要在下载时选中 UWP C++复选框。

![C++对于 Visual Studio](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a>Arduino 接线
通过 Arduino 接线支持, 你可以在 Arduino 接线中为 IoT 生态系统中的许多常用组件和外设构建应用。

我们的[Arduino 布线项目指南](../learn-about-hardware/ArduinoWiringProjectGuide.md)提供了有关如何建立这些应用的完整说明。 下面复制和链接的示例可帮助你开始构建自己的。  甚至可以[在 Arduino 中构建](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky)可用于其他语言的 WinRT 组件。 

*Blinky 示例代码*示例页上提供了完整的[示例代码和文档](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky), 你可以在下面找到完整的代码:

```C++
void setup()
{
    // put your setup code here, to run once:

    pinMode(GPIO5, OUTPUT);
}

void loop()
{
    // put your main code here, to run repeatedly:

    digitalWrite(GPIO5, LOW);
    delay(500);
    digitalWrite(GPIO5, HIGH);
    delay(500);
}
```
