---
title: Arduino 接线项目指南
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何创建、 设置和使用 Windows IoT Core Arduino 绑定项目的部署。
keywords: windows iot，Arduino，Arduino 配线、 闪电般的性能，Visual Studio
ms.openlocfilehash: baa904d1d5f23db15fd1dacd05c749449dc91213
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510761"
---
# <a name="arduino-wiring-project-guide"></a><span data-ttu-id="24bd8-104">Arduino 接线项目指南</span><span class="sxs-lookup"><span data-stu-id="24bd8-104">Arduino Wiring Project Guide</span></span>

<span data-ttu-id="24bd8-105">本指南将引导完成创建、 设置和使用 Windows IoT Core Arduino 绑定项目的部署。</span><span class="sxs-lookup"><span data-stu-id="24bd8-105">This guide will walk through the creation, setup, and deployment of an Arduino Wiring project using Windows IoT Core.</span></span>

<span data-ttu-id="24bd8-106">Arduino 绑定项目利用熟悉的、 易于使用 Arduino 连接 API 与 Windows IoT 闪电 DMAP 驱动程序： 使用直接内存映射提供重要的驱动程序[性能速度](../develop-your-app/LightningPerformance.md)。</span><span class="sxs-lookup"><span data-stu-id="24bd8-106">Arduino Wiring projects utilize the familiar, easy to use Arduino Wiring API with Windows IoT Lightning DMAP driver: a driver using direct memory mapping to provide significant [performance speeds](../develop-your-app/LightningPerformance.md).</span></span> <span data-ttu-id="24bd8-107">可以复制和粘贴到 IoT Core Arduino 绑定项目的 Arduino 草图和库并运行其支持 IoT Core 上设备，包括 Raspberry Pi2，3 和 Minnowboard 最大值 ！</span><span class="sxs-lookup"><span data-stu-id="24bd8-107">You can copy & paste Arduino sketches and libraries into your IoT Core Arduino Wiring projects and run them on supported IoT Core devices, including Raspberry Pi2, 3 and Minnowboard Max!</span></span> <span data-ttu-id="24bd8-108">请参阅此页获取详细信息开发部分。</span><span class="sxs-lookup"><span data-stu-id="24bd8-108">See the develop section of this page for more information.</span></span>

## <a name="install-the-microsoft-iot-templates"></a><span data-ttu-id="24bd8-109">安装 Microsoft IoT 模板</span><span class="sxs-lookup"><span data-stu-id="24bd8-109">Install the Microsoft IoT Templates</span></span>

<span data-ttu-id="24bd8-110">我们提供了一个 Visual Studio 扩展，该扩展将为 Arduino 接线项目以及其他 Microsoft IoT 项目类型自动安装 VS 模板。</span><span class="sxs-lookup"><span data-stu-id="24bd8-110">We've provided a Visual Studio extension which will automatically install a VS template for the Arduino Wiring projects as well as other Microsoft IoT project types.</span></span> 

- <span data-ttu-id="24bd8-111">转到 [Windows IoT 核心版项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472)来从 Visual Studio 库下载该扩展！</span><span class="sxs-lookup"><span data-stu-id="24bd8-111">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>
- <span data-ttu-id="24bd8-112">安装扩展，然后重新启动 Visual Studio，如果之前已打开</span><span class="sxs-lookup"><span data-stu-id="24bd8-112">Install the extension and restart Visual Studio if it was already open</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="24bd8-113">更改默认控制器驱动程序</span><span class="sxs-lookup"><span data-stu-id="24bd8-113">Change the Default Controller Driver</span></span>

<span data-ttu-id="24bd8-114">你将需要运行直接内存映射驱动程序来编写 Arduino 接线解决方案！</span><span class="sxs-lookup"><span data-stu-id="24bd8-114">You will need to be running the Direct Memory Mapped Driver to write Arduino Wiring solutions!</span></span> <span data-ttu-id="24bd8-115">有关说明，请参考 [Lightning 设置指南](../develop-your-app/LightningSetup.md)！</span><span class="sxs-lookup"><span data-stu-id="24bd8-115">Refer to the [Lightning Setup Guide](../develop-your-app/LightningSetup.md) for instructions!</span></span>

## <a name="develop"></a><span data-ttu-id="24bd8-116">开发</span><span class="sxs-lookup"><span data-stu-id="24bd8-116">Develop</span></span>
<span data-ttu-id="24bd8-117">在完成其中一个"绑定"示例[示例页](https://developer.microsoft.com/en-us/windows/iot/samples)，或生成你自己的项目 ！</span><span class="sxs-lookup"><span data-stu-id="24bd8-117">Complete one of the "Wiring" samples on the [Samples Page](https://developer.microsoft.com/en-us/windows/iot/samples), or build your own project!</span></span> <span data-ttu-id="24bd8-118">将列出我们创建的任何使用 Arduino 接线编写的示例，如下所示：[Blinky（接线）](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring)。</span><span class="sxs-lookup"><span data-stu-id="24bd8-118">Any of the samples we've created that are written using Arduino Wiring will be listed like so: [Blinky (Wiring)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span></span> <span data-ttu-id="24bd8-119">适用于 IoT 项目的经典“Hello World”项目 Blinky 是适合作为你的第一个项目的良好起点！</span><span class="sxs-lookup"><span data-stu-id="24bd8-119">Blinky, the cononical "Hello World" project for IoT projects, is a great place to start for your first project!</span></span>

### <a name="create-a-new-project"></a><span data-ttu-id="24bd8-120">创建一个新项目</span><span class="sxs-lookup"><span data-stu-id="24bd8-120">Create a new Project</span></span>
1. <span data-ttu-id="24bd8-121">打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="24bd8-121">Open Visual Studio.</span></span>

2. <span data-ttu-id="24bd8-122">选择文件-> 新建-> 项目...</span><span class="sxs-lookup"><span data-stu-id="24bd8-122">Select File -> New -> Project...</span></span>

3. <span data-ttu-id="24bd8-123">从显示的对话框中，选择：</span><span class="sxs-lookup"><span data-stu-id="24bd8-123">From the dialogue that appears, choose:</span></span>  
<span data-ttu-id="24bd8-124">Visual C++ -> Windows-> Windows IoT Core-> Arduino 绑定适用于 Windows IoT Core 的应用程序</span><span class="sxs-lookup"><span data-stu-id="24bd8-124">Visual C++ -> Windows -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span>  
<span data-ttu-id="24bd8-125">(可能会改为显示为)</span><span class="sxs-lookup"><span data-stu-id="24bd8-125">(might appear instead as)</span></span>  
<span data-ttu-id="24bd8-126">Visual C++ -> Windows IoT Core-> Arduino 绑定适用于 Windows IoT Core 的应用程序</span><span class="sxs-lookup"><span data-stu-id="24bd8-126">Visual C++ -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span> 


![创建应用](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a><span data-ttu-id="24bd8-128">移植</span><span class="sxs-lookup"><span data-stu-id="24bd8-128">Porting</span></span>

<span data-ttu-id="24bd8-129">已仔细实现 Arduino 接线 API，以便你可以将库和草图复制/粘贴到 Arduino 接线项目中。</span><span class="sxs-lookup"><span data-stu-id="24bd8-129">The Arduino Wiring API has been carefully implemented to make it possible to copy/paste your libraries and sketches into an Arduino Wiring project.</span></span> <span data-ttu-id="24bd8-130">尽管如此，在某些情况下，你可能需要对草图或库进行轻微修改。</span><span class="sxs-lookup"><span data-stu-id="24bd8-130">Nevertheless there are, in some circumstances, slight modifications you may have to make to your sketches or libraries.</span></span> <span data-ttu-id="24bd8-131">我们创建了一个易于遵循的 [Arduino 接线移植指南](ArduinoWiringPortingGuide.md)来涵盖这些潜在问题。</span><span class="sxs-lookup"><span data-stu-id="24bd8-131">We've created an easy to follow [Arduino Wiring Porting Guide](ArduinoWiringPortingGuide.md) to cover these potential issues.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="24bd8-132">生成和部署</span><span class="sxs-lookup"><span data-stu-id="24bd8-132">Build and Deploy</span></span>

- <span data-ttu-id="24bd8-133">在 Visual Studio 中，确保选择“远程计算机”作为你的部署目标。</span><span class="sxs-lookup"><span data-stu-id="24bd8-133">In Visual Studio, make sure "Remote Machine" is selected as your deployment target.</span></span>
- <span data-ttu-id="24bd8-134">此外，请确保该体系结构设置为匹配的看板运行你的项目。</span><span class="sxs-lookup"><span data-stu-id="24bd8-134">Also, make sure the  architecture is set to match the board you're running your project on.</span></span> <span data-ttu-id="24bd8-135">Raspberry Pi 2 或 3 中，选择"ARM"和对于 Minnowboard 最大值，请选择"x86"。</span><span class="sxs-lookup"><span data-stu-id="24bd8-135">For Raspberry Pi 2 or 3 choose "ARM" and for Minnowboard Max, choose "x86".</span></span>

![远程计算机](../media/ArduinoWiring/wiringapp_remotemachine.png)

- <span data-ttu-id="24bd8-137">在 Visual Studio 中打开在“调试”上下文菜单中找到的解决方案属性。</span><span class="sxs-lookup"><span data-stu-id="24bd8-137">Open the solution properties found on the Debug context menu in Visual Studio.</span></span>

![解决方案属性](../media/ArduinoWiring/wiringapp_properties.png)

- <span data-ttu-id="24bd8-139">找到你的设备的 IP 地址或计算机名称。</span><span class="sxs-lookup"><span data-stu-id="24bd8-139">locate the IP address or machine name of your device.</span></span> <span data-ttu-id="24bd8-140">使用 Windows 10 IoT 核心版仪表板应用程序，或者将挂接到你的设备到监视器。</span><span class="sxs-lookup"><span data-stu-id="24bd8-140">Either use the Windows 10 IoT Core Dashboard application or hook up your device to a monitor.</span></span>
- <span data-ttu-id="24bd8-141">在“计算机名称”字段中键入远程计算机的计算机名称（默认为 minwinpc）或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="24bd8-141">Type the machine name (minwinpc by default) or the IP address of the remote machine into the 'machine name' field.</span></span> <span data-ttu-id="24bd8-142">如果你已将设备命名为“minwinpc”以外的某个名称，请在登录框中改用该名称。</span><span class="sxs-lookup"><span data-stu-id="24bd8-142">If you have renamed your device to something besides 'minwinpc' use that name in the login box instead.</span></span>
- <span data-ttu-id="24bd8-143">请确保 Authentican 类型是：通用 （未加密的协议）</span><span class="sxs-lookup"><span data-stu-id="24bd8-143">Ensure the Authentican Type is: Universal (Unencrypted Protocol)</span></span>

![解决方案属性](../media/ArduinoWiring/wiringapp_properties2.png)

- <span data-ttu-id="24bd8-145">按 F5 以生成和部署你的设备上的项目。</span><span class="sxs-lookup"><span data-stu-id="24bd8-145">Press F5 to build and deploy your project on your device.</span></span>
