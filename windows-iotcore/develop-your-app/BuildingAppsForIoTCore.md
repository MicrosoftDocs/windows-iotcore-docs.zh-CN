---
title: 开发前台应用程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 IoT Core 支持的语言和应用类型。
keywords: windows iot，语言，应用类型，UWP，受支持
ms.openlocfilehash: 6b748561ff26ae7b48bfb444589b84408dc01421
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656443"
---
# <a name="developing-foreground-applications"></a><span data-ttu-id="8a488-104">开发前台应用程序</span><span class="sxs-lookup"><span data-stu-id="8a488-104">Developing foreground applications</span></span>
<span data-ttu-id="8a488-105">了解 Windows 10 IoT Core 支持的语言，以及 IoT Core 支持的 UWP 和非 UWP 应用类型。</span><span class="sxs-lookup"><span data-stu-id="8a488-105">Learn about the languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported on IoT Core.</span></span>


> [!NOTE]
> <span data-ttu-id="8a488-106">在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="8a488-106">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="application-types"></a><span data-ttu-id="8a488-107">应用程序类型</span><span class="sxs-lookup"><span data-stu-id="8a488-107">Application Types</span></span>
___

### <a name="universal-windows-platform-uwp-apps"></a><span data-ttu-id="8a488-108">通用 Windows 平台 (UWP) 应用</span><span class="sxs-lookup"><span data-stu-id="8a488-108">Universal Windows Platform (UWP) Apps</span></span>
<span data-ttu-id="8a488-109">IoT 核心是一个以 UWP 为中心的操作系统，UWP 应用是其主要的应用类型。</span><span class="sxs-lookup"><span data-stu-id="8a488-109">IoT Core is a UWP-centric OS and UWP apps are its primary app type.</span></span>

<span data-ttu-id="8a488-110">通用 Windows 平台 (UWP) 是所有版本的 Windows 10 中的通用应用平台，包括 Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="8a488-110">Universal Windows Platform (UWP) is a common app platform across all version of Windows 10, including Windows 10 IoT Core.</span></span>  <span data-ttu-id="8a488-111">UWP 是 Windows 运行时 (WinRT) 的演变。</span><span class="sxs-lookup"><span data-stu-id="8a488-111">UWP is an evolution of Windows Runtime (WinRT).</span></span> <span data-ttu-id="8a488-112">可在 [此处](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)找到有关 UWP 的详细信息和概述。</span><span class="sxs-lookup"><span data-stu-id="8a488-112">You can find more information and an overview to UWP [here](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span></span>

<span data-ttu-id="8a488-113">Visual Studio 是用于为 IoT 核心编写 UWP 应用的主要工具。</span><span class="sxs-lookup"><span data-stu-id="8a488-113">Visual Studio is the primary tool for writing UWP apps for IoT Core and in general.</span></span> <span data-ttu-id="8a488-114">可在 [此处](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs)找到有关 Visual Studio 的兼容性要求的详细列表。</span><span class="sxs-lookup"><span data-stu-id="8a488-114">You can find a detailed listing of the compatibility requirements for Visual Studio [here](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).</span></span>


### <a name="traditional-uwp-apps"></a><span data-ttu-id="8a488-115">传统 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="8a488-115">Traditional UWP Apps</span></span>
<span data-ttu-id="8a488-116">UWP 应用只需在 IoT Core 上工作，就像在其他 Windows 10 版本上一样。</span><span class="sxs-lookup"><span data-stu-id="8a488-116">UWP apps just work on IoT Core, just as they do on other Windows 10 editions.</span></span> <span data-ttu-id="8a488-117">在 Visual Studio 中，简单的空白 Xaml 应用程序将正确部署到 IoT Core 设备，就像在手机或 Windows 10 电脑上一样。</span><span class="sxs-lookup"><span data-stu-id="8a488-117">A simple, blank Xaml app in Visual Studio will properly deploy to your IoT Core device just as it would on a phone or Windows 10 PC.</span></span> <span data-ttu-id="8a488-118">IoT 核心完全支持所有标准 UWP 语言和项目模板。</span><span class="sxs-lookup"><span data-stu-id="8a488-118">All of the standard UWP languages and project templates are fully supported on IoT Core.</span></span>

<span data-ttu-id="8a488-119">传统 UWP 应用模型中添加了一些内容来支持 IoT 方案，任何利用这些方案的 UWP 应用都需要将相应信息添加到其清单中。</span><span class="sxs-lookup"><span data-stu-id="8a488-119">There are a few additions to the traditional UWP app-model to support IoT scenarios and any UWP app that takes advantage of them will need the corresponding information added to their manifest.</span></span> <span data-ttu-id="8a488-120">特别是，需要将 "iot" 命名空间添加到这些标准 UWP 应用的清单中。</span><span class="sxs-lookup"><span data-stu-id="8a488-120">In particular, the "iot" namespace needs to be added to the manifest of these standard UWP apps.</span></span> 

<span data-ttu-id="8a488-121">在 <Package> 清单的属性中，需要定义 iot xmlns，并将其添加到 IgnorableNamespaces 列表中。</span><span class="sxs-lookup"><span data-stu-id="8a488-121">Inside the <Package> attribute of the manifest, you need to define the iot xmlns and add it to the IgnorableNamespaces list.</span></span> <span data-ttu-id="8a488-122">最终 xml 应如下所示：</span><span class="sxs-lookup"><span data-stu-id="8a488-122">The final xml should look like this:</span></span> 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a><span data-ttu-id="8a488-123">后台应用</span><span class="sxs-lookup"><span data-stu-id="8a488-123">Background Apps</span></span>
<span data-ttu-id="8a488-124">除了传统的 UI 应用外，IoT Core 还添加了一个名为 "后台应用程序" 的新 UWP 应用类型。</span><span class="sxs-lookup"><span data-stu-id="8a488-124">In addition to the traditional UI apps, IoT Core has added a new UWP app type called "Background Applications".</span></span> <span data-ttu-id="8a488-125">这些应用程序不具有 UI 组件，而是具有实现 "IBackgroundTask" 接口的类。</span><span class="sxs-lookup"><span data-stu-id="8a488-125">These applications do not have a UI component, but instead have a class that implements the "IBackgroundTask" interface.</span></span> <span data-ttu-id="8a488-126">然后，它们将该类注册为 "StartupTask" 以在系统启动时运行。</span><span class="sxs-lookup"><span data-stu-id="8a488-126">They then register that class as a "StartupTask" to run at system boot.</span></span> <span data-ttu-id="8a488-127">由于它们仍是 UWP 应用程序，因此它们可以访问同一组 Api 并支持同一语言的。</span><span class="sxs-lookup"><span data-stu-id="8a488-127">Since they are still UWP apps, they have access to the same set of APIs and are supported from the same language.</span></span> <span data-ttu-id="8a488-128">唯一的区别是没有 UI 入口点。</span><span class="sxs-lookup"><span data-stu-id="8a488-128">The only difference is that there is no UI entry point.</span></span>

<span data-ttu-id="8a488-129">每种类型的 IBackgroundTask 均获取其自己的资源策略。</span><span class="sxs-lookup"><span data-stu-id="8a488-129">Each type of IBackgroundTask gets its own resource policy.</span></span> <span data-ttu-id="8a488-130">此限制通常是为了改进设备上的电池寿命和计算机资源，这些应用程序是前景 UI 应用程序的辅助组件。</span><span class="sxs-lookup"><span data-stu-id="8a488-130">This is usually restrictive to improve battery life and machine resources on devices where these background apps are secondary components of foreground UI apps.</span></span> <span data-ttu-id="8a488-131">在 IoT 设备上，后台应用通常是设备的主要功能，因此这些 StartupTasks 获取了在其他设备上镜像前景 UI 应用的资源策略。</span><span class="sxs-lookup"><span data-stu-id="8a488-131">On IoT devices, Background Apps are often the primary function of the device and so these StartupTasks get a resource policy that mirrors foreground UI apps on other devices.</span></span>

<span data-ttu-id="8a488-132">下面的示例演示生成闪烁 LED 所需的 c # 后台应用程序所需的代码：</span><span class="sxs-lookup"><span data-stu-id="8a488-132">The following sample shows the code necessary to build a C# Background App that blinks an LED:</span></span>

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

<span data-ttu-id="8a488-133">可在 [此处](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)找到有关后台应用的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8a488-133">You can find in-depth information on Background apps [here](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

### <a name="non-uwp-apps"></a><span data-ttu-id="8a488-134">非 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="8a488-134">Non-UWP Apps</span></span>
<span data-ttu-id="8a488-135">IoT 核心支持某些传统的 Win32 应用类型，如 Win32 控制台应用和 NT 服务。</span><span class="sxs-lookup"><span data-stu-id="8a488-135">IoT Core supports certain traditional Win32 app types such as Win32 Console Apps and NT Services.</span></span> <span data-ttu-id="8a488-136">这些应用的构建和运行方式与在 Windows 10 桌面上的运行方式相同。</span><span class="sxs-lookup"><span data-stu-id="8a488-136">These apps are built and run the same way as on Windows 10 Desktop.</span></span> <span data-ttu-id="8a488-137">此外，还提供了一个 IoT 核心 c + + 控制台项目模板，可以使用 Visual Studio 轻松生成此类应用。</span><span class="sxs-lookup"><span data-stu-id="8a488-137">Additionally, there is an IoT Core C++ Console project template to make it easy to build such apps using Visual Studio.</span></span>

<span data-ttu-id="8a488-138">对于这些非 UWP 应用程序，有两个主要限制：</span><span class="sxs-lookup"><span data-stu-id="8a488-138">There are two main limitations on these non-UWP applications:</span></span>
1. <span data-ttu-id="8a488-139">*无旧版 WIN32 UI 支持：* IoT Core 不包含用于创建经典 (HWND) Windows 的 Api。</span><span class="sxs-lookup"><span data-stu-id="8a488-139">*No legacy Win32 UI support:* IoT Core does not contain APIs to create classic (HWND) Windows.</span></span> <span data-ttu-id="8a488-140">旧式方法（例如 ( # A1 和 CreateWindowEx ( # A3）或处理 Windows 的任何其他方法 (Hwnd) 不可用。</span><span class="sxs-lookup"><span data-stu-id="8a488-140">Legacy methods such as CreateWindow() and CreateWindowEx() or any other methods that deal with Windows handles (HWNDs) are not available.</span></span> <span data-ttu-id="8a488-141">随后，在 IoT Core 上不支持依赖于此类 Api 的框架（包括 MFC、Windows 窗体和 WPF）</span><span class="sxs-lookup"><span data-stu-id="8a488-141">Subsequently, frameworks that depend on such APIs including MFC, Windows Forms and WPF, are not supported on IoT Core</span></span>
2. <span data-ttu-id="8a488-142">*仅限 c + + 应用：* 目前，仅支持 c + + 来开发 IoT Core 上的 Win32 应用程序。</span><span class="sxs-lookup"><span data-stu-id="8a488-142">*C++ Apps Only:* Currently, only C++ is supported for developing Win32 apps on IoT Core.</span></span>

## <a name="programming-languages"></a><span data-ttu-id="8a488-143">编程语言</span><span class="sxs-lookup"><span data-stu-id="8a488-143">Programming Languages</span></span>
___

<span data-ttu-id="8a488-144">IoT 核心支持多种编程语言。</span><span class="sxs-lookup"><span data-stu-id="8a488-144">IoT Core supports a wide range of programming languages.</span></span>

### <a name="in-box-languages"></a><span data-ttu-id="8a488-145">内置语言</span><span class="sxs-lookup"><span data-stu-id="8a488-145">In-Box languages</span></span>
<span data-ttu-id="8a488-146">默认情况下，传统的 UWP 语言附带了 Visual Studio 支持。</span><span class="sxs-lookup"><span data-stu-id="8a488-146">Traditional UWP languages ship with support in Visual Studio by default.</span></span> <span data-ttu-id="8a488-147">所有内置语言都支持 UI 和后台应用程序</span><span class="sxs-lookup"><span data-stu-id="8a488-147">All of the In-Box languages support both UI and Background Applications</span></span>
 
* <span data-ttu-id="8a488-148">语言</span><span class="sxs-lookup"><span data-stu-id="8a488-148">Languages</span></span>
  * <span data-ttu-id="8a488-149">C#</span><span class="sxs-lookup"><span data-stu-id="8a488-149">C#</span></span>
  * <span data-ttu-id="8a488-150">C++</span><span class="sxs-lookup"><span data-stu-id="8a488-150">C++</span></span>
  * <span data-ttu-id="8a488-151">JavaScript</span><span class="sxs-lookup"><span data-stu-id="8a488-151">JavaScript</span></span>
  * <span data-ttu-id="8a488-152">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8a488-152">Visual Basic</span></span>

### <a name="arduino-wiring"></a><span data-ttu-id="8a488-153">Arduino 布线</span><span class="sxs-lookup"><span data-stu-id="8a488-153">Arduino Wiring</span></span>
 <span data-ttu-id="8a488-154">Arduino 接线需要从 Visual Studio **工具->扩展和更新** 管理器下载 "Windows IoT 核心项目模板"。</span><span class="sxs-lookup"><span data-stu-id="8a488-154">Arduino Wiring requires the download of the "Windows IoT Core Project Templates" from the Visual Studio **Tools->Extensions and Updates** manager.</span></span>  <span data-ttu-id="8a488-155">Arduino 布线仅支持后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="8a488-155">Arduino Wiring supports only Background Applications.</span></span> <span data-ttu-id="8a488-156">你还可以使用 c #、c + + 或 Visual Basic 生成 *Windows 运行时组件* ，然后从任何其他语言中引用这些库。</span><span class="sxs-lookup"><span data-stu-id="8a488-156">You can also build *Windows Runtime Components* using C#, C++, or Visual Basic and then reference those libraries from any other language.</span></span>

### <a name="c-and-visual-basic-vb"></a><span data-ttu-id="8a488-157">C # 和 Visual Basic (VB) </span><span class="sxs-lookup"><span data-stu-id="8a488-157">C# and Visual Basic (VB)</span></span>
<span data-ttu-id="8a488-158">C # 和 VB 同时作为 UWP 应用提供支持，并有权访问可用于 UWP 应用程序的 .NET Framework 部分。</span><span class="sxs-lookup"><span data-stu-id="8a488-158">C# and VB are both supported as UWP apps and have access to the portion of the .NET Framework available to UWP applications.</span></span> <span data-ttu-id="8a488-159">它们支持通过 Xaml 和后台应用程序生成的 UI 应用。</span><span class="sxs-lookup"><span data-stu-id="8a488-159">They support UI apps built with Xaml as well as Background Apps.</span></span> <span data-ttu-id="8a488-160">你还可以构建可用于其他支持的语言的 *Windows 运行时组件* 。</span><span class="sxs-lookup"><span data-stu-id="8a488-160">You can also build *Windows Runtime Components* that can be used from other supported languages.</span></span>

<span data-ttu-id="8a488-161">示例：</span><span class="sxs-lookup"><span data-stu-id="8a488-161">Samples:</span></span>


* [<span data-ttu-id="8a488-162">C # Blinky 无外设</span><span class="sxs-lookup"><span data-stu-id="8a488-162">C# Blinky Headless</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CS)
* [<span data-ttu-id="8a488-163">VB Blinky 无外设</span><span class="sxs-lookup"><span data-stu-id="8a488-163">VB Blinky Headless</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB)
* [<span data-ttu-id="8a488-164">C # Blinky UI 应用</span><span class="sxs-lookup"><span data-stu-id="8a488-164">C# Blinky UI App</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/CS)


### <a name="javascript"></a><span data-ttu-id="8a488-165">JavaScript</span><span class="sxs-lookup"><span data-stu-id="8a488-165">JavaScript</span></span>
<span data-ttu-id="8a488-166">可以使用 JavaScript 来构建 UI 和后台应用。</span><span class="sxs-lookup"><span data-stu-id="8a488-166">You can use JavaScript to build both UI and Background Apps.</span></span> <span data-ttu-id="8a488-167">UI 应用的工作方式与在所有 UWP 版本上的工作方式相同。</span><span class="sxs-lookup"><span data-stu-id="8a488-167">The UI apps work the same way they do on all UWP editions.</span></span> <span data-ttu-id="8a488-168">后台应用是 IoT Core 的新应用，但很简单。</span><span class="sxs-lookup"><span data-stu-id="8a488-168">The Background Apps are new for IoT Core but are simple.</span></span> <span data-ttu-id="8a488-169">下面的示例代码演示了 *JS New 项目模板*的输出：</span><span class="sxs-lookup"><span data-stu-id="8a488-169">The following sample code shows the output of the *JS New Project Template*:</span></span>

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a><span data-ttu-id="8a488-170">C++</span><span class="sxs-lookup"><span data-stu-id="8a488-170">C++</span></span>
<span data-ttu-id="8a488-171">通过 c + +，你可以构建 Xaml 或 DirectX UI 应用，还可以构建 UWP 背景项目和 *非 UI* Win32 应用。</span><span class="sxs-lookup"><span data-stu-id="8a488-171">With C++ you can build Xaml or DirectX UI apps, as well as UWP Background projects and *non-UI* Win32 apps.</span></span>

<span data-ttu-id="8a488-172">示例：</span><span class="sxs-lookup"><span data-stu-id="8a488-172">Samples:</span></span>

* [<span data-ttu-id="8a488-173">Blinky 无外设</span><span class="sxs-lookup"><span data-stu-id="8a488-173">Blinky Headless</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [<span data-ttu-id="8a488-174">Blinky 头</span><span class="sxs-lookup"><span data-stu-id="8a488-174">Blinky Headed</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [<span data-ttu-id="8a488-175">控制台应用</span><span class="sxs-lookup"><span data-stu-id="8a488-175">Console App</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus/CPP)

> [!NOTE]
> <span data-ttu-id="8a488-176">对于计划用 c + + 编写应用程序的用户，需要在下载时选中 "UWP c + +" 复选框。</span><span class="sxs-lookup"><span data-stu-id="8a488-176">For those who are planning to write their app in C++, you'll need to check the UWP C++ checkbox upon downloading.</span></span>

![适用于 Visual Studio 的 c + +](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a><span data-ttu-id="8a488-178">Arduino 布线</span><span class="sxs-lookup"><span data-stu-id="8a488-178">Arduino Wiring</span></span>
<span data-ttu-id="8a488-179">通过 Arduino 接线支持，你可以在 Arduino 接线中为 IoT 生态系统中的许多常用组件和外设构建应用。</span><span class="sxs-lookup"><span data-stu-id="8a488-179">With Arduino Wiring support you can build apps in Arduino Wiring for many popular components and peripherals in the IoT ecosystem.</span></span>

<span data-ttu-id="8a488-180">我们的 [Arduino 布线项目指南](../learn-about-hardware/ArduinoWiringProjectGuide.md) 提供了有关如何建立这些应用的完整说明。</span><span class="sxs-lookup"><span data-stu-id="8a488-180">Our [Arduino Wiring Project Guide](../learn-about-hardware/ArduinoWiringProjectGuide.md) provides full instructions on how to get set up to build these apps.</span></span> <span data-ttu-id="8a488-181">下面复制和链接的示例可帮助你开始构建自己的。</span><span class="sxs-lookup"><span data-stu-id="8a488-181">The samples copied and linked below will help you get started building your own.</span></span>  <span data-ttu-id="8a488-182">甚至可以 [在 Arduino 中构建](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) 可用于其他语言的 WinRT 组件。</span><span class="sxs-lookup"><span data-stu-id="8a488-182">You can even [build WinRT components in Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) that can then be used from other languages.</span></span> 

<span data-ttu-id="8a488-183">*Blinky 示例代码* 示例页上提供了完整的 [示例代码和文档](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) ，你可以在下面找到完整的代码：</span><span class="sxs-lookup"><span data-stu-id="8a488-183">*Blinky Sample Code* The full [sample code and docs](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) are available on our samples page and you can find the full code below:</span></span>

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
