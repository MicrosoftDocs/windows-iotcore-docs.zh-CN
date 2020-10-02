---
title: Arduino 布线项目指南
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows IoT Core 创建、设置和部署 Arduino 接线图项目。
keywords: windows iot，Arduino，Arduino 布线，闪电性能，Visual Studio
ms.openlocfilehash: f97d8515b0cd16e2dfda5a8903733c960d91599d
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655883"
---
# <a name="arduino-wiring-project-guide"></a><span data-ttu-id="85269-104">Arduino 布线项目指南</span><span class="sxs-lookup"><span data-stu-id="85269-104">Arduino Wiring Project Guide</span></span>

> [!IMPORTANT]
> <span data-ttu-id="85269-105">Windows 10 IoT 团队不再主动维护 Arduino。</span><span class="sxs-lookup"><span data-stu-id="85269-105">The Windows 10 IoT team is no longer actively maintaining Arduino.</span></span>

<span data-ttu-id="85269-106">本指南将指导你使用 Windows IoT Core 创建、设置和部署 Arduino 接线图项目。</span><span class="sxs-lookup"><span data-stu-id="85269-106">This guide will walk through the creation, setup, and deployment of an Arduino Wiring project using Windows IoT Core.</span></span>

<span data-ttu-id="85269-107">Arduino 接线图使用 Windows IoT 闪电 DMAP 驱动程序，利用熟悉的、易于使用的 Arduino 布线 API：使用直接内存映射的驱动程序，提供显著的 [性能速度](../develop-your-app/LightningPerformance.md)。</span><span class="sxs-lookup"><span data-stu-id="85269-107">Arduino Wiring projects utilize the familiar, easy to use Arduino Wiring API with Windows IoT Lightning DMAP driver: a driver using direct memory mapping to provide significant [performance speeds](../develop-your-app/LightningPerformance.md).</span></span> <span data-ttu-id="85269-108">可以将 Arduino 草图和库复制 & 粘贴到 IoT 核心 Arduino 布线项目，并在支持的 IoT 核心设备上运行它们，包括 Raspberry Pi2、3和 Minnowboard Max！</span><span class="sxs-lookup"><span data-stu-id="85269-108">You can copy & paste Arduino sketches and libraries into your IoT Core Arduino Wiring projects and run them on supported IoT Core devices, including Raspberry Pi2, 3 and Minnowboard Max!</span></span> <span data-ttu-id="85269-109">有关详细信息，请参阅本页的 "开发" 部分。</span><span class="sxs-lookup"><span data-stu-id="85269-109">See the develop section of this page for more information.</span></span>

## <a name="install-the-microsoft-iot-templates"></a><span data-ttu-id="85269-110">安装 Microsoft IoT 模板</span><span class="sxs-lookup"><span data-stu-id="85269-110">Install the Microsoft IoT Templates</span></span>

> [!NOTE]
> <span data-ttu-id="85269-111">下载 VS 2015 以访问 Arduino 接线模板-VS 2017 和更高版本上不支持这些模板。</span><span class="sxs-lookup"><span data-stu-id="85269-111">Download VS 2015 to access Arduino Wiring templates - these templates are no loner supported on VS 2017 and beyond.</span></span>

<span data-ttu-id="85269-112">我们提供了一个 Visual Studio 扩展，该扩展将自动为 Arduino 接线项目和其他 Microsoft IoT 项目类型安装 VS 模板。</span><span class="sxs-lookup"><span data-stu-id="85269-112">We've provided a Visual Studio extension which will automatically install a VS template for the Arduino Wiring projects as well as other Microsoft IoT project types.</span></span>

- <span data-ttu-id="85269-113">转到 [Windows IoT Core 项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472) 以从 Visual Studio 库中下载扩展！</span><span class="sxs-lookup"><span data-stu-id="85269-113">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>
- <span data-ttu-id="85269-114">安装扩展，并重新启动 Visual Studio （如果已打开）</span><span class="sxs-lookup"><span data-stu-id="85269-114">Install the extension and restart Visual Studio if it was already open</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="85269-115">更改默认控制器驱动程序</span><span class="sxs-lookup"><span data-stu-id="85269-115">Change the Default Controller Driver</span></span>

<span data-ttu-id="85269-116">你将需要运行直接内存映射驱动程序来编写 Arduino 布线解决方案！</span><span class="sxs-lookup"><span data-stu-id="85269-116">You will need to be running the Direct Memory Mapped Driver to write Arduino Wiring solutions!</span></span> <span data-ttu-id="85269-117">有关说明，请参阅 [闪电安装指南](../develop-your-app/LightningSetup.md) ！</span><span class="sxs-lookup"><span data-stu-id="85269-117">Refer to the [Lightning Setup Guide](../develop-your-app/LightningSetup.md) for instructions!</span></span>

## <a name="develop"></a><span data-ttu-id="85269-118">开发</span><span class="sxs-lookup"><span data-stu-id="85269-118">Develop</span></span>
<span data-ttu-id="85269-119">完成 " [示例" 页](https://developer.microsoft.com/en-us/windows/iot/samples)上的 "布线" 示例之一，或生成自己的项目！</span><span class="sxs-lookup"><span data-stu-id="85269-119">Complete one of the "Wiring" samples on the [Samples Page](https://developer.microsoft.com/en-us/windows/iot/samples), or build your own project!</span></span> <span data-ttu-id="85269-120">我们使用 Arduino 布线编写的任何示例将如下所示： [Blinky (布线) ](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring)。</span><span class="sxs-lookup"><span data-stu-id="85269-120">Any of the samples we've created that are written using Arduino Wiring will be listed like so: [Blinky (Wiring)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span></span> <span data-ttu-id="85269-121">Blinky 是 IoT 项目的 cononical "Hello World" 项目，是第一个项目的入门教程！</span><span class="sxs-lookup"><span data-stu-id="85269-121">Blinky, the cononical "Hello World" project for IoT projects, is a great place to start for your first project!</span></span>

### <a name="create-a-new-project"></a><span data-ttu-id="85269-122">创建新项目</span><span class="sxs-lookup"><span data-stu-id="85269-122">Create a new Project</span></span>
1. <span data-ttu-id="85269-123">打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="85269-123">Open Visual Studio.</span></span>

2. <span data-ttu-id="85269-124">选择 "文件-> 新建-> 项目 ..."</span><span class="sxs-lookup"><span data-stu-id="85269-124">Select File -> New -> Project...</span></span>

3. <span data-ttu-id="85269-125">从显示的对话框中，选择：</span><span class="sxs-lookup"><span data-stu-id="85269-125">From the dialogue that appears, choose:</span></span>  
<span data-ttu-id="85269-126">Visual C++ > windows-> Windows IoT 核心-> 适用于 Windows IoT 核心的 Arduino 布线应用程序</span><span class="sxs-lookup"><span data-stu-id="85269-126">Visual C++ -> Windows -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span>  
<span data-ttu-id="85269-127"> (可能会显示为) </span><span class="sxs-lookup"><span data-stu-id="85269-127">(might appear instead as)</span></span>  
<span data-ttu-id="85269-128">Visual C++ > Windows IoT Core-> 适用于 Windows IoT 核心的 Arduino 配应用程序</span><span class="sxs-lookup"><span data-stu-id="85269-128">Visual C++ -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span>


![应用创建](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a><span data-ttu-id="85269-130">移植</span><span class="sxs-lookup"><span data-stu-id="85269-130">Porting</span></span>

<span data-ttu-id="85269-131">已仔细实现 Arduino 布线 API，使您能够将库和草图复制/粘贴到 Arduino 布线项目。</span><span class="sxs-lookup"><span data-stu-id="85269-131">The Arduino Wiring API has been carefully implemented to make it possible to copy/paste your libraries and sketches into an Arduino Wiring project.</span></span> <span data-ttu-id="85269-132">然而，在某些情况下，可能需要对您的草图或库做出少量的修改。</span><span class="sxs-lookup"><span data-stu-id="85269-132">Nevertheless there are, in some circumstances, slight modifications you may have to make to your sketches or libraries.</span></span> <span data-ttu-id="85269-133">我们已经创建了一个易于遵循的 [Arduino 布线指南](ArduinoWiringPortingGuide.md) ，以涵盖这些潜在问题。</span><span class="sxs-lookup"><span data-stu-id="85269-133">We've created an easy to follow [Arduino Wiring Porting Guide](ArduinoWiringPortingGuide.md) to cover these potential issues.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="85269-134">生成和部署</span><span class="sxs-lookup"><span data-stu-id="85269-134">Build and Deploy</span></span>

- <span data-ttu-id="85269-135">在 Visual Studio 中，确保已选择 "远程计算机" 作为部署目标。</span><span class="sxs-lookup"><span data-stu-id="85269-135">In Visual Studio, make sure "Remote Machine" is selected as your deployment target.</span></span>
- <span data-ttu-id="85269-136">此外，请确保将体系结构设置为与正在运行项目的板匹配。</span><span class="sxs-lookup"><span data-stu-id="85269-136">Also, make sure the  architecture is set to match the board you're running your project on.</span></span> <span data-ttu-id="85269-137">对于 Raspberry Pi 2 或3，选择 "ARM"，为 "Minnowboard Max" 选择 "x86"。</span><span class="sxs-lookup"><span data-stu-id="85269-137">For Raspberry Pi 2 or 3 choose "ARM" and for Minnowboard Max, choose "x86".</span></span>

![远程计算机](../media/ArduinoWiring/wiringapp_remotemachine.png)

- <span data-ttu-id="85269-139">打开在 Visual Studio 的 "调试" 上下文菜单中找到的解决方案属性。</span><span class="sxs-lookup"><span data-stu-id="85269-139">Open the solution properties found on the Debug context menu in Visual Studio.</span></span>

![解决方案属性](../media/ArduinoWiring/wiringapp_properties.png)

- <span data-ttu-id="85269-141">找到设备的 IP 地址或计算机名称。</span><span class="sxs-lookup"><span data-stu-id="85269-141">locate the IP address or machine name of your device.</span></span> <span data-ttu-id="85269-142">使用 Windows 10 IoT 核心仪表板应用程序或将设备挂接到监视器。</span><span class="sxs-lookup"><span data-stu-id="85269-142">Either use the Windows 10 IoT Core Dashboard application or hook up your device to a monitor.</span></span>
- <span data-ttu-id="85269-143">默认情况下，键入计算机名称 (minwinpc) 或远程计算机的 IP 地址设置为 "计算机名" 字段。</span><span class="sxs-lookup"><span data-stu-id="85269-143">Type the machine name (minwinpc by default) or the IP address of the remote machine into the 'machine name' field.</span></span> <span data-ttu-id="85269-144">如果将设备重命名为 "minwinpc" 以外的其他内容，请在登录框中改用该名称。</span><span class="sxs-lookup"><span data-stu-id="85269-144">If you have renamed your device to something besides 'minwinpc' use that name in the login box instead.</span></span>
- <span data-ttu-id="85269-145">确保 Authentican 类型为：通用 (未加密协议) </span><span class="sxs-lookup"><span data-stu-id="85269-145">Ensure the Authentican Type is: Universal (Unencrypted Protocol)</span></span>

![解决方案属性1](../media/ArduinoWiring/wiringapp_properties2.png)

- <span data-ttu-id="85269-147">按 F5 在设备上生成并部署项目。</span><span class="sxs-lookup"><span data-stu-id="85269-147">Press F5 to build and deploy your project on your device.</span></span>
