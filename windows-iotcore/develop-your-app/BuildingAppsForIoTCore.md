---
title: 前台应用程序开发
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解有关语言和 IoT Core 支持的应用类型。
keywords: windows iot、 语言、 应用程序类型，UWP，支持
ms.openlocfilehash: e0eb046ba874e8433e7632d3f88a63a90b88fa2b
ms.sourcegitcommit: 8a197111b5b7814b924d77dfea5f9d38760d4288
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2019
ms.locfileid: "67627395"
---
# <a name="developing-foreground-applications"></a><span data-ttu-id="26a44-104">前台应用程序开发</span><span class="sxs-lookup"><span data-stu-id="26a44-104">Developing foreground applications</span></span>
<span data-ttu-id="26a44-105">了解有关 Windows 10 IoT 核心版，以及 UWP 支持的语言和支持 IoT Core 的非 UWP 应用程序类型。</span><span class="sxs-lookup"><span data-stu-id="26a44-105">Learn about the languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported on IoT Core.</span></span>


> [!NOTE]
> <span data-ttu-id="26a44-106">在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="26a44-106">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="application-types"></a><span data-ttu-id="26a44-107">应用程序类型</span><span class="sxs-lookup"><span data-stu-id="26a44-107">Application Types</span></span>
___

### <a name="universal-windows-platform-uwp-apps"></a><span data-ttu-id="26a44-108">通用 Windows 平台 (UWP) 应用</span><span class="sxs-lookup"><span data-stu-id="26a44-108">Universal Windows Platform (UWP) Apps</span></span>
<span data-ttu-id="26a44-109">IoT Core 是 UWP 为中心的 OS 和 UWP 应用是其主应用程序类型。</span><span class="sxs-lookup"><span data-stu-id="26a44-109">IoT Core is a UWP centric OS and UWP apps are its primary app type.</span></span>

<span data-ttu-id="26a44-110">通用 Windows 平台 (UWP) 是一个通用应用平台跨所有版本的 Windows 10，包括 Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="26a44-110">Universal Windows Platform (UWP) is a common app platform across all version of Windows 10, including Windows 10 IoT Core.</span></span>  <span data-ttu-id="26a44-111">UWP 是一种演变，Windows 运行时 (WinRT)。</span><span class="sxs-lookup"><span data-stu-id="26a44-111">UWP is an evolution of Windows Runtime (WinRT).</span></span> <span data-ttu-id="26a44-112">您可以找到详细信息和简要介绍了如何 UWP[此处](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)。</span><span class="sxs-lookup"><span data-stu-id="26a44-112">You can find more information and an overview to UWP [here](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span></span>

<span data-ttu-id="26a44-113">Visual Studio 是用于编写 UWP 应用，用于 IoT 核心版，并在常规的主要工具。</span><span class="sxs-lookup"><span data-stu-id="26a44-113">Visual Studio is the primary tool for writing UWP apps for IoT Core and in general.</span></span> <span data-ttu-id="26a44-114">您可以找到 Visual Studio 的兼容性要求的详细的列表[此处](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs)。</span><span class="sxs-lookup"><span data-stu-id="26a44-114">You can find a detailed listing of the compatibility requirements for Visual Studio [here](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).</span></span>


### <a name="traditional-uwp-apps"></a><span data-ttu-id="26a44-115">传统的 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="26a44-115">Traditional UWP Apps</span></span>
<span data-ttu-id="26a44-116">UWP 应用仅适用于 IoT 核心版，与它们在其他 Windows 10 版本上。</span><span class="sxs-lookup"><span data-stu-id="26a44-116">UWP apps just work on IoT Core, just as they do on other Windows 10 editions.</span></span> <span data-ttu-id="26a44-117">简单的、 空白的 Xaml 应用程序，在 Visual Studio 中将正确地将部署到 IoT Core 设备就像在手机或 Windows 10 电脑上一样。</span><span class="sxs-lookup"><span data-stu-id="26a44-117">A simple, blank Xaml app in Visual Studio will properly deploy to your IoT Core device just as it would on a phone or Windows 10 PC.</span></span> <span data-ttu-id="26a44-118">在 IoT Core 上完全支持所有标准 UWP 语言和项目模板。</span><span class="sxs-lookup"><span data-stu-id="26a44-118">All of the standard UWP languages and project templates are fully supported on IoT Core.</span></span>

<span data-ttu-id="26a44-119">有几个添加到传统 UWP 应用的模型，以支持 IoT 方案，充分利用其任何 UWP 应用将需要添加到其清单中的相应信息。</span><span class="sxs-lookup"><span data-stu-id="26a44-119">There are a few additions to the traditional UWP app-model to support IoT scenarios and any UWP app that takes advantage of them will need the corresponding information added to their manifest.</span></span> <span data-ttu-id="26a44-120">特别是"iot"命名空间必须添加到这些标准的 UWP 应用的清单。</span><span class="sxs-lookup"><span data-stu-id="26a44-120">In particular the "iot" namespace needs to be added to the manifest of these standard UWP apps.</span></span> 

<span data-ttu-id="26a44-121">内部<Package>属性的清单，您需要定义 iot xmlns 并将其添加到 IgnorableNamespaces 列表。</span><span class="sxs-lookup"><span data-stu-id="26a44-121">Inside the <Package> attribute of the manifest, you need to define the iot xmlns and add it to the IgnorableNamespaces list.</span></span> <span data-ttu-id="26a44-122">最终的 xml 应如下所示：</span><span class="sxs-lookup"><span data-stu-id="26a44-122">The final xml should look like this:</span></span> 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a><span data-ttu-id="26a44-123">后台应用</span><span class="sxs-lookup"><span data-stu-id="26a44-123">Background Apps</span></span>
<span data-ttu-id="26a44-124">除了传统的应用 UI 中，IoT 核心版添加了一个称为"后台应用程序"的新 UWP 应用程序类型。</span><span class="sxs-lookup"><span data-stu-id="26a44-124">In addition to the traditional UI apps, IoT Core has added a new UWP app type called "Background Applications".</span></span> <span data-ttu-id="26a44-125">这些应用程序不具有 UI 组件，但改为已实现"IBackgroundTask"接口的类。</span><span class="sxs-lookup"><span data-stu-id="26a44-125">These applications do not have a UI component, but instead have a class that implements the "IBackgroundTask" interface.</span></span> <span data-ttu-id="26a44-126">然后，他们将该类注册为"StartupTask"在系统启动运行。</span><span class="sxs-lookup"><span data-stu-id="26a44-126">They then register that class as a "StartupTask" to run at system boot.</span></span> <span data-ttu-id="26a44-127">因为它们仍是 UWP 应用，他们有权访问同一组 Api，并支持从相同的语言。</span><span class="sxs-lookup"><span data-stu-id="26a44-127">Since they are still UWP apps, they have access to the same set of APIs and are supported from the same language.</span></span> <span data-ttu-id="26a44-128">唯一区别是，没有任何 UI 入口点。</span><span class="sxs-lookup"><span data-stu-id="26a44-128">The only difference is that there is no UI entry point.</span></span>

<span data-ttu-id="26a44-129">每种类型的 IBackgroundTask 获取自己的资源策略。</span><span class="sxs-lookup"><span data-stu-id="26a44-129">Each type of IBackgroundTask gets its own resource policy.</span></span> <span data-ttu-id="26a44-130">这是通常限制，以提高在设备上的电池寿命和计算机资源这些后台应用程序所在的前景色 UI 应用程序的次要组件。</span><span class="sxs-lookup"><span data-stu-id="26a44-130">This is usually restrictive to improve battery life and machine resources on devices where these background apps are secondary components of foreground UI apps.</span></span> <span data-ttu-id="26a44-131">IoT 设备上的后台应用程序通常是设备的主要功能并使这些 StartupTasks 获取资源策略，反映在其他设备上的前景色 UI 应用程序。</span><span class="sxs-lookup"><span data-stu-id="26a44-131">On IoT devices, Background Apps are often the primary function of the device and so these StartupTasks get a resource policy that mirrors foreground UI apps on other devices.</span></span>

<span data-ttu-id="26a44-132">下面的示例显示了代码生成所需C#会使 LED 闪烁的后台应用程序：</span><span class="sxs-lookup"><span data-stu-id="26a44-132">The following sample shows the code necessary to build a C# Background App that blinks an LED:</span></span>

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

<span data-ttu-id="26a44-133">您可以找到后台应用程序的详细信息[此处](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)。</span><span class="sxs-lookup"><span data-stu-id="26a44-133">You can find in-depth information on Background apps [here](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

### <a name="non-uwp-apps"></a><span data-ttu-id="26a44-134">非 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="26a44-134">Non-UWP Apps</span></span>
<span data-ttu-id="26a44-135">IoT Core 支持某些传统的 Win32 应用程序类型，例如 Win32 控制台应用程序和 NT 服务。</span><span class="sxs-lookup"><span data-stu-id="26a44-135">IoT Core supports certain traditional Win32 app types such as Win32 Console Apps and NT Services.</span></span> <span data-ttu-id="26a44-136">这些应用的创建和运行相同的方式与在 Windows 10 桌面版上。</span><span class="sxs-lookup"><span data-stu-id="26a44-136">These apps are built and run the same way as on Windows 10 Desktop.</span></span> <span data-ttu-id="26a44-137">此外，还有 IoT CoreC++控制台项目模板，使其轻松地构建此类应用程序使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="26a44-137">Additionally, there is an IoT Core C++ Console project template to make it easy to build such apps using Visual Studio.</span></span>

<span data-ttu-id="26a44-138">有两个主要限制这些非 UWP 应用程序：</span><span class="sxs-lookup"><span data-stu-id="26a44-138">There are two main limitations on these non-UWP applications:</span></span>
1. <span data-ttu-id="26a44-139">*旧的 Win32 UI 支持：* IoT 核心版不包含要创建经典 (HWND) Windows Api。</span><span class="sxs-lookup"><span data-stu-id="26a44-139">*No legacy Win32 UI support:* IoT Core does not contain APIs to create classic (HWND) Windows.</span></span> <span data-ttu-id="26a44-140">旧方法，如 CreateWindow() 和 CreateWindowEx() 或处理 Windows 句柄 (Hwnd) 的任何其他方法不可用。</span><span class="sxs-lookup"><span data-stu-id="26a44-140">Legacy methods such as CreateWindow() and CreateWindowEx() or any other methods that deal with Windows handles (HWNDs) are not available.</span></span> <span data-ttu-id="26a44-141">随后，在 IoT Core 上不支持取决于包括 MFC、 Windows 窗体和 WPF 中，此类 Api 的框架</span><span class="sxs-lookup"><span data-stu-id="26a44-141">Subsequently, frameworks that depend on such APIs including MFC, Windows Forms and WPF, are not supported on IoT Core</span></span>
2. <span data-ttu-id="26a44-142">*C++仅限应用：* 目前，仅C++开发 IoT Core 上的 Win32 应用程序支持。</span><span class="sxs-lookup"><span data-stu-id="26a44-142">*C++ Apps Only:* Currently, only C++ is supported for developing Win32 apps on IoT Core.</span></span>

## <a name="programming-languages"></a><span data-ttu-id="26a44-143">编程语言</span><span class="sxs-lookup"><span data-stu-id="26a44-143">Programming Languages</span></span>
___

<span data-ttu-id="26a44-144">IoT Core 支持各种编程语言。</span><span class="sxs-lookup"><span data-stu-id="26a44-144">IoT Core supports a wide range of programming languages.</span></span>

### <a name="in-box-languages"></a><span data-ttu-id="26a44-145">框中的语言</span><span class="sxs-lookup"><span data-stu-id="26a44-145">In-Box languages</span></span>
<span data-ttu-id="26a44-146">传统 UWP 语言随附于 Visual Studio 中默认情况下的支持。</span><span class="sxs-lookup"><span data-stu-id="26a44-146">Traditional UWP languages ship with support in Visual Studio by default.</span></span> <span data-ttu-id="26a44-147">所有的框中语言支持 UI 和后台应用程序</span><span class="sxs-lookup"><span data-stu-id="26a44-147">All of the In-Box languages support both UI and Background Applications</span></span>
 
* <span data-ttu-id="26a44-148">语言</span><span class="sxs-lookup"><span data-stu-id="26a44-148">Languages</span></span>
  * <span data-ttu-id="26a44-149">C#</span><span class="sxs-lookup"><span data-stu-id="26a44-149">C#</span></span>
  * <span data-ttu-id="26a44-150">C++</span><span class="sxs-lookup"><span data-stu-id="26a44-150">C++</span></span>
  * <span data-ttu-id="26a44-151">Javascript</span><span class="sxs-lookup"><span data-stu-id="26a44-151">Javascript</span></span>
  * <span data-ttu-id="26a44-152">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26a44-152">Visual Basic</span></span>

### <a name="arduino-wiring"></a><span data-ttu-id="26a44-153">Arduino 接线</span><span class="sxs-lookup"><span data-stu-id="26a44-153">Arduino Wiring</span></span>
 <span data-ttu-id="26a44-154">Arduino 布线要求的"Windows IoT Core 项目模板"从 Visual Studio 下载**工具-> 扩展和更新**管理器。</span><span class="sxs-lookup"><span data-stu-id="26a44-154">Arduino Wiring requires the download of the "Windows IoT Core Project Templates" from the Visual Studio **Tools->Extensions and Updates** manager.</span></span>  <span data-ttu-id="26a44-155">Arduino 连接支持仅后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="26a44-155">Arduino Wiring supports only Background Applications.</span></span> <span data-ttu-id="26a44-156">您还可以构建*Windows 运行时组件*使用C#， C++，或 Visual Basic，然后从任何其他语言中引用这些库。</span><span class="sxs-lookup"><span data-stu-id="26a44-156">You can also build *Windows Runtime Components* using C#, C++, or Visual Basic and then reference those libraries from any other language.</span></span>

### <a name="c-and-visual-basic-vb"></a><span data-ttu-id="26a44-157">C#和 Visual Basic (VB)</span><span class="sxs-lookup"><span data-stu-id="26a44-157">C# and Visual Basic (VB)</span></span>
<span data-ttu-id="26a44-158">C#和 VB 同时支持作为 UWP 应用，并有权访问的部分的.net Framework 可用于 UWP 应用程序。</span><span class="sxs-lookup"><span data-stu-id="26a44-158">C# and VB are both supported as UWP apps and have access to the portion of the .Net Framework available to UWP applications.</span></span> <span data-ttu-id="26a44-159">它们支持使用 Xaml 以及后台应用程序构建的 UI 应用程序。</span><span class="sxs-lookup"><span data-stu-id="26a44-159">They support UI apps built with Xaml as well as Background Apps.</span></span> <span data-ttu-id="26a44-160">您还可以构建*Windows 运行时组件*，可以使用从其他受支持的语言。</span><span class="sxs-lookup"><span data-stu-id="26a44-160">You can also build *Windows Runtime Components* that can be used from other supported languages.</span></span>

<span data-ttu-id="26a44-161">示例：</span><span class="sxs-lookup"><span data-stu-id="26a44-161">Samples:</span></span>


* [<span data-ttu-id="26a44-162">C#灾难从天而降无外设</span><span class="sxs-lookup"><span data-stu-id="26a44-162">C# Blinky Headless</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CS)
* [<span data-ttu-id="26a44-163">VB 灾难从天而降无外设</span><span class="sxs-lookup"><span data-stu-id="26a44-163">VB Blinky Headless</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB)
* [<span data-ttu-id="26a44-164">C#灾难从天而降 UI 应用</span><span class="sxs-lookup"><span data-stu-id="26a44-164">C# Blinky UI App</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/CS)


### <a name="javascript"></a><span data-ttu-id="26a44-165">Javascript</span><span class="sxs-lookup"><span data-stu-id="26a44-165">Javascript</span></span>
<span data-ttu-id="26a44-166">您可以使用 Javascript 构建 UI 和后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="26a44-166">You can use Javascript to build both UI and Background Apps.</span></span> <span data-ttu-id="26a44-167">UI 应用程序的工作的方式与它们在所有 UWP 版本执行类似。</span><span class="sxs-lookup"><span data-stu-id="26a44-167">The UI apps work the same way they do on all UWP editions.</span></span> <span data-ttu-id="26a44-168">背景应用 IoT 核心版的新增功能，但会非常简单。</span><span class="sxs-lookup"><span data-stu-id="26a44-168">The Background Apps are new for IoT Core but are very simple.</span></span> <span data-ttu-id="26a44-169">下面的示例代码显示的输出*JS 新项目模板*:</span><span class="sxs-lookup"><span data-stu-id="26a44-169">The following sample code shows the output of a the *JS New Project Template*:</span></span>

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a><span data-ttu-id="26a44-170">C++</span><span class="sxs-lookup"><span data-stu-id="26a44-170">C++</span></span>
<span data-ttu-id="26a44-171">使用C++应用程序，以及 UWP 背景项目可以生成 Xaml 或 DirectX UI 并*非 UI* Win32 应用。</span><span class="sxs-lookup"><span data-stu-id="26a44-171">With C++ you can build Xaml or DirectX UI apps, as well as UWP Background projects and *non-UI* Win32 apps.</span></span>

<span data-ttu-id="26a44-172">示例：</span><span class="sxs-lookup"><span data-stu-id="26a44-172">Samples:</span></span>

* [<span data-ttu-id="26a44-173">灾难从天而降无外设</span><span class="sxs-lookup"><span data-stu-id="26a44-173">Blinky Headless</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [<span data-ttu-id="26a44-174">灾难从天而降讲述的内容</span><span class="sxs-lookup"><span data-stu-id="26a44-174">Blinky Headed</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [<span data-ttu-id="26a44-175">控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="26a44-175">Console App</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus/CPP)

> [!NOTE]
> <span data-ttu-id="26a44-176">对于那些规划中编写自己的应用程序C++，将需要检查 UWPC++在下载时的复选框。</span><span class="sxs-lookup"><span data-stu-id="26a44-176">For those who are planning to write their app in C++, you'll need to check the UWP C++ checkbox upon downloading.</span></span>

![C++用于 Visual Studio](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a><span data-ttu-id="26a44-178">Arduino 接线</span><span class="sxs-lookup"><span data-stu-id="26a44-178">Arduino Wiring</span></span>
<span data-ttu-id="26a44-179">使用 Arduino 绑定支持可以构建应用在 arduino 开发绑定为许多常用的组件和外围设备的 IoT 生态系统中。</span><span class="sxs-lookup"><span data-stu-id="26a44-179">With Arduino Wiring support you can build apps in Arduino Wiring for many popular components and peripherals in the IoT ecosystem.</span></span>

<span data-ttu-id="26a44-180">我们[Arduino 连接项目向导](../learn-about-hardware/ArduinoWiringProjectGuide.md)提供有关如何完成设置以构建这些应用程序的完整说明。</span><span class="sxs-lookup"><span data-stu-id="26a44-180">Our [Arduino Wiring Project Guide](../learn-about-hardware/ArduinoWiringProjectGuide.md) provides full instructions on how to get set up to build these apps.</span></span> <span data-ttu-id="26a44-181">以下链接和复制的示例将帮助你开始构建你自己的。</span><span class="sxs-lookup"><span data-stu-id="26a44-181">The samples copied and linked below will help you get started building your own.</span></span>  <span data-ttu-id="26a44-182">您甚至可以[生成 WinRT 组件中 Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky)然后可以使用从其他语言。</span><span class="sxs-lookup"><span data-stu-id="26a44-182">You can even [build WinRT components in Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) that can then be used from other languages.</span></span> 

<span data-ttu-id="26a44-183">*灾难从天而降示例代码*完整[示例代码和文档](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky)位于我们的示例页，您可以发现下面的完整代码：</span><span class="sxs-lookup"><span data-stu-id="26a44-183">*Blinky Sample Code* The full [sample code and docs](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) are available on our samples page and you can find the full code below:</span></span>

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
