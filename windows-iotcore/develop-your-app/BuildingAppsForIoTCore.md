---
title: 前台应用程序开发
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解有关语言和 IoT Core 支持的应用类型。
keywords: windows iot、 语言、 应用程序类型，UWP，支持
ms.openlocfilehash: 7d330ff2961ba83d969861bbecd1536b02a4833a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510945"
---
# <a name="developing-foreground-applications"></a>前台应用程序开发
了解有关 Windows 10 IoT 核心版，以及 UWP 支持的语言和支持 IoT Core 的非 UWP 应用程序类型。


> [!NOTE]
> 部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。

## <a name="application-types"></a>应用程序类型
___

### <a name="universal-windows-platform-uwp-apps"></a>通用 Windows 平台 (UWP) 应用
IoT Core 是 UWP 为中心的 OS 和 UWP 应用是其主应用程序类型。

通用 Windows 平台 (UWP) 是一个通用应用平台跨所有版本的 Windows 10，包括 Windows 10 IoT Core。  UWP 是一种演变，Windows 运行时 (WinRT)。 您可以找到详细信息和简要介绍了如何 UWP[此处](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)。

Visual Studio 是用于编写 UWP 应用，用于 IoT 核心版，并在常规的主要工具。 您可以找到 Visual Studio 的兼容性要求的详细的列表[此处](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs)。


### <a name="traditional-uwp-apps"></a>传统的 UWP 应用
UWP 应用仅适用于 IoT 核心版，与它们在其他 Windows 10 版本上。 简单的、 空白的 Xaml 应用程序，在 Visual Studio 中将正确地将部署到 IoT Core 设备就像在手机或 Windows 10 电脑上一样。 在 IoT Core 上完全支持所有标准 UWP 语言和项目模板。

有几个添加到传统 UWP 应用的模型，以支持 IoT 方案，充分利用其任何 UWP 应用将需要添加到其清单中的相应信息。 特别是"iot"命名空间必须添加到这些标准的 UWP 应用的清单。 

内部<Package>属性的清单，您需要定义 iot xmlns 并将其添加到 IgnorableNamespaces 列表。 最终的 xml 应如下所示： 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a>后台应用
除了传统的应用 UI 中，IoT 核心版添加了一个称为"后台应用程序"的新 UWP 应用程序类型。 这些应用程序不具有 UI 组件，但改为已实现"IBackgroundTask"接口的类。 然后，他们将该类注册为"StartupTask"在系统启动运行。 因为它们仍是 UWP 应用，他们有权访问同一组 Api，并支持从相同的语言。 唯一区别是，没有任何 UI 入口点。

每种类型的 IBackgroundTask 获取自己的资源策略。 这是通常限制，以提高在设备上的电池寿命和计算机资源这些后台应用程序所在的前景色 UI 应用程序的次要组件。 IoT 设备上的后台应用程序通常是设备的主要功能并使这些 StartupTasks 获取资源策略，反映在其他设备上的前景色 UI 应用程序。

下面的示例显示了代码生成所需C#会使 LED 闪烁的后台应用程序：

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

您可以找到后台应用程序的详细信息[此处](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)。

### <a name="non-uwp-apps"></a>非 UWP 应用
IoT Core 支持某些传统的 Win32 应用程序类型，例如 Win32 控制台应用程序和 NT 服务。 这些应用的创建和运行相同的方式与在 Windows 10 桌面版上。 此外，还有 IoT CoreC++控制台项目模板，使其轻松地构建此类应用程序使用 Visual Studio。

有两个主要限制这些非 UWP 应用程序：
1. *旧的 Win32 UI 支持：* IoT 核心版不包含要创建经典 (HWND) Windows Api。 旧方法，如 CreateWindow() 和 CreateWindowEx() 或处理 Windows 句柄 (Hwnd) 的任何其他方法不可用。 随后，在 IoT Core 上不支持取决于包括 MFC、 Windows 窗体和 WPF 中，此类 Api 的框架
2. *C++仅限应用：* 目前，仅C++开发 IoT Core 上的 Win32 应用程序支持。

## <a name="programming-languages"></a>编程语言
___

IoT Core 支持各种编程语言。

### <a name="in-box-languages"></a>框中的语言
传统 UWP 语言随附于 Visual Studio 中默认情况下的支持。 所有的框中语言支持 UI 和后台应用程序
 
* 语言
  * C#
  * C++
  * Javascript
  * Visual Basic

### <a name="arduino-wiring"></a>Arduino 接线
 Arduino 布线要求的"Windows IoT Core 项目模板"从 Visual Studio 下载**工具-> 扩展和更新**管理器。  Arduino 连接支持仅后台应用程序。 您还可以构建*Windows 运行时组件*使用C#， C++，或 Visual Basic，然后从任何其他语言中引用这些库。

### <a name="c-and-visual-basic-vb"></a>C#和 Visual Basic (VB)
C#和 VB 同时支持作为 UWP 应用，并有权访问的部分的.net Framework 可用于 UWP 应用程序。 它们支持使用 Xaml 以及后台应用程序构建的 UI 应用程序。 您还可以构建*Windows 运行时组件*，可以使用从其他受支持的语言。

示例：


* [C#灾难从天而降无外设的完整文档](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground)
* [C#仅灾难从天而降无外设代码](https://github.com/ms-iot/samples/tree/develop/HelloBlinkyBackground/CS)
* [VB 灾难从天而降无外设的代码仅限](https://github.com/ms-iot/samples/tree/develop/HelloBlinkyBackground/VB)
* [C#灾难从天而降 UI 应用](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)


### <a name="javascript"></a>Javascript
您可以使用 Javascript 构建 UI 和后台应用程序。 UI 应用程序的工作的方式与它们在所有 UWP 版本执行类似。 背景应用 IoT 核心版的新增功能，但会非常简单。 下面的示例代码显示的输出*JS 新项目模板*:

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a>C++
使用C++应用程序，以及 UWP 背景项目可以生成 Xaml 或 DirectX UI 并*非 UI* Win32 应用。

示例：

* [灾难从天而降无外设](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [灾难从天而降讲述的内容](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [控制台应用程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus)

> [!NOTE]
> 对于那些规划中编写自己的应用程序C++，将需要检查 UWPC++在下载时的复选框。

![C++用于 Visual Studio](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a>Arduino 接线
使用 Arduino 绑定支持可以构建应用在 arduino 开发绑定为许多常用的组件和外围设备的 IoT 生态系统中。

我们[Arduino 连接项目向导](../learn-about-hardware/ArduinoWiringProjectGuide.md)提供有关如何完成设置以构建这些应用程序的完整说明。 以下链接和复制的示例将帮助你开始构建你自己的。  您甚至可以[生成 WinRT 组件中 Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky)然后可以使用从其他语言。 

*灾难从天而降示例代码*完整[示例代码和文档](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB)位于我们的示例页，您可以发现下面的完整代码：

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
