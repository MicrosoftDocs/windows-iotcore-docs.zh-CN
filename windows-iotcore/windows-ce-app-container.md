---
title: Windows CE 应用容器概述
ms.date: 08/12/2020
ms.topic: article
description: Windows CE 应用容器迁移技术
keywords: Windows 10 IoT Core，Windows CE，应用程序迁移，cepal
ms.openlocfilehash: 63d51ffcdd2add8db375ae5915a58e73418bfa9f
ms.sourcegitcommit: bc01e7c74b93d1af533e2fe498551e1720f9ddb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/12/2020
ms.locfileid: "88140326"
---
# <a name="an-overview-of-the-windows-ce-app-container"></a><span data-ttu-id="21fd4-104">Windows CE 应用容器概述</span><span class="sxs-lookup"><span data-stu-id="21fd4-104">An Overview of the Windows CE App Container</span></span>

<span data-ttu-id="21fd4-105">Microsoft 为 embedded 设备提供了平台和操作系统，数十年。</span><span class="sxs-lookup"><span data-stu-id="21fd4-105">Microsoft has provided platforms and operating systems for embedded devices for decades.</span></span> <span data-ttu-id="21fd4-106">随着 Windows 10 IoT 等新产品/服务的推出，我们的客户和合作伙伴对这些操作系统提供的高级安全性、平台和云连接功能的兴趣越来越大。</span><span class="sxs-lookup"><span data-stu-id="21fd4-106">As new offerings such as Windows 10 IoT have become available, our customers and partners are increasingly interested in the advanced security, platform, and cloud connectivity features that these OS provide.</span></span> <span data-ttu-id="21fd4-107">从大多数早期版本的 Windows （如 Windows XP 和 Windows 7）迁移的客户可以轻松完成此操作，因为二进制兼容的应用程序。</span><span class="sxs-lookup"><span data-stu-id="21fd4-107">Customers moving from most earlier editions of Windows, like Windows XP and Windows 7, can do so with little effort because of binary compatible applications.</span></span> <span data-ttu-id="21fd4-108">其他操作系统（如 Windows CE）需要设备构建者来修改源代码。</span><span class="sxs-lookup"><span data-stu-id="21fd4-108">Other operating systems, like Windows CE, require device builders to modify source code.</span></span> <span data-ttu-id="21fd4-109">迁移此类应用程序可能会很困难。</span><span class="sxs-lookup"><span data-stu-id="21fd4-109">Porting applications like this can be challenging.</span></span>

<span data-ttu-id="21fd4-110">为了帮助这些客户移动到 Windows 10 IoT 并充分利用智能边缘（包括人工智能和机器学习）的全部功能，Microsoft 开发了一项技术，使大多数客户可以在 Windows 10 IoT 上运行其现有的、未修改的 Windows CE 应用程序，同时他们会继续投入更新应用程序。</span><span class="sxs-lookup"><span data-stu-id="21fd4-110">To help these customers move to Windows 10 IoT and harness the full power of the intelligent edge including artificial intelligence and machine learning, Microsoft has developed technology that will allow most customers to run their existing, unmodified Windows CE applications on Windows 10 IoT while they continue to invest in updating their applications.</span></span> <span data-ttu-id="21fd4-111">可以在 IoT Show 剧集[现代化 Windows CE 设备](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices)中了解有关此技术工作原理的详细信息</span><span class="sxs-lookup"><span data-stu-id="21fd4-111">You can learn more about how this technology works in the IoT Show episode [Modernizing Windows CE Devices](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices)</span></span>

## <a name="what-are-the-platform-requirements"></a><span data-ttu-id="21fd4-112">什么是平台要求</span><span class="sxs-lookup"><span data-stu-id="21fd4-112">What are the platform requirements</span></span>

<span data-ttu-id="21fd4-113">Windows CE 应用迁移技术的工作原理是在 Windows 10 IoT Core 之上运行 Windows CE 2013 实例。</span><span class="sxs-lookup"><span data-stu-id="21fd4-113">The Windows CE App Migration technology works by running a Windows CE 2013 instance on top of Windows 10 IoT Core.</span></span>

<span data-ttu-id="21fd4-114">此解决方案适用于32位应用程序代码，需要与 Windows 10 IoT Core[兼容](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards)的 ARM32 或 x64 基本平台。</span><span class="sxs-lookup"><span data-stu-id="21fd4-114">The solution works with 32-bit application code and requires an ARM32 or x64 base platform that is [compatible](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards) with Windows 10 IoT Core.</span></span>
<span data-ttu-id="21fd4-115">你应该使用平台生成器以及为 Windows 10 IoT Core 构建映像，来熟悉如何构建 Windows CE 2013 系统映像。</span><span class="sxs-lookup"><span data-stu-id="21fd4-115">You should be comfortable building a Windows CE 2013 system image using platform builder as well as building an image for Windows 10 IoT Core.</span></span>

<span data-ttu-id="21fd4-116">可在下面的[先决条件](#prerequisites)中找到更详细的要求列表。</span><span class="sxs-lookup"><span data-stu-id="21fd4-116">A more detailed list of the requirements can be found below at [Prerequisites](#prerequisites).</span></span>

## <a name="is-windows-ce-app-container-the-right-choice-for-me"></a><span data-ttu-id="21fd4-117">Windows CE 应用容器是正确的选择</span><span class="sxs-lookup"><span data-stu-id="21fd4-117">Is Windows CE App Container the right choice for me</span></span>

<span data-ttu-id="21fd4-118">对于需要使用 ARM32 或拥有需要多个开发周期才能迁移的复杂 CE 应用程序的设计，具有[Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)的 Ce 应用容器为逐步迁移提供了一个很好的解决方案。</span><span class="sxs-lookup"><span data-stu-id="21fd4-118">For designs that need to leverage ARM32 or have complex CE applications that will require multiple development cycles to migrate, the CE App Container with [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) offers a great solution for gradual migration.</span></span>

<span data-ttu-id="21fd4-119">开发人员在其 IoT 核心系统映像中放置了一个特殊的 ARM32 或 x86 Windows CE2013 平台映像，这些映像在 Windows 10 IoT Core 兼容硬件上部署。</span><span class="sxs-lookup"><span data-stu-id="21fd4-119">Developers place a special ARM32 or x86 Windows CE2013 platform image within their IoT Core system image which they deploy on Windows 10 IoT Core compatible hardware.</span></span> <span data-ttu-id="21fd4-120">开发人员可以通过 Windows 10 层开始添加功能，如 Azure 云连接或新式外设，还可以移动 CE 应用程序的某些部分，并将其用于在2029之前完成迁移。</span><span class="sxs-lookup"><span data-stu-id="21fd4-120">Developers have access to begin adding functionality, like Azure cloud connectivity or modern peripherals, though the Windows 10 layer and can move portions of the CE application over as well aiming for complete migration before 2029.</span></span>

<span data-ttu-id="21fd4-121">对于 IoT 核心服务，Windows 10 IoT Core OS 将继续接收安全更新，直至2029。</span><span class="sxs-lookup"><span data-stu-id="21fd4-121">With IoT Core Services, your Windows 10 IoT Core OS will continue to receive security updates until 2029.</span></span> <span data-ttu-id="21fd4-122">而且，通过设备更新中心等功能，Oem 可以管理操作系统更新的时间，并可以轻松地分发应用程序更新。</span><span class="sxs-lookup"><span data-stu-id="21fd4-122">And, with capabilities like Device Update Center, OEMs can manage the timing of the OS updates as well as distribute application updates easily.</span></span>

<span data-ttu-id="21fd4-123">但是，如果现有设计只需要几年的生产，最佳做法是继续 Windows CE 2013。</span><span class="sxs-lookup"><span data-stu-id="21fd4-123">However, if you have existing designs that just need a few more years of manufacturing, the best course is to remain on Windows CE 2013.</span></span> <span data-ttu-id="21fd4-124">[使用 Windows 10 IoT Core 上的 Windows CE 应用容器](https://techcommunity.microsoft.com/t5/internet-of-things/moving-forward-with-windows-ce-using-the-windows-ce-app/ba-p/1582360)，更深入地介绍了前进 Windows CE。</span><span class="sxs-lookup"><span data-stu-id="21fd4-124">The path forward is explained more deeply in [Moving forward with Windows CE using the Windows CE App Container on Windows 10 IoT Core](https://techcommunity.microsoft.com/t5/internet-of-things/moving-forward-with-windows-ce-using-the-windows-ce-app/ba-p/1582360).</span></span>

## <a name="getting-started"></a><span data-ttu-id="21fd4-125">入门</span><span class="sxs-lookup"><span data-stu-id="21fd4-125">Getting Started</span></span>

<span data-ttu-id="21fd4-126">Windows CE 应用容器是一种技术，允许大多数 CE 应用程序运行在 Windows 10 IoT Core 的顶层。</span><span class="sxs-lookup"><span data-stu-id="21fd4-126">The Windows CE App Container is a technology that allows most CE applications to run on top of Windows 10 IoT Core.</span></span>

<span data-ttu-id="21fd4-127">此解决方案分为两个阶段。</span><span class="sxs-lookup"><span data-stu-id="21fd4-127">The solution is built in two stages.</span></span> <span data-ttu-id="21fd4-128">第一阶段使用适用于 x86 或 ARM32 体系结构的 BSP 创建 Windows CE 2013 映像。</span><span class="sxs-lookup"><span data-stu-id="21fd4-128">The first stage creates a Windows CE 2013 image using a BSP for either x86 or ARM32 architecture.</span></span> <span data-ttu-id="21fd4-129">此映像将包含在 Windows 10 IoT Core 映像中，该映像利用 x64 或 ARM32 BSP 来实现将安装解决方案的特定设备硬件。</span><span class="sxs-lookup"><span data-stu-id="21fd4-129">This image is then included in a Windows 10 IoT Core image that utilizes the x64 or ARM32 BSP for the specific device hardware where the solution will be installed.</span></span>

![CE 应用容器体系结构](.//media/WindowsCEAppContainer/image1.png)

<span data-ttu-id="21fd4-131">有关此体系结构的详细信息，请查看此视频：[现代化 Windows CE 设备](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices)。</span><span class="sxs-lookup"><span data-stu-id="21fd4-131">For more information about this architecture please review this video: [Modernizing Windows CE Devices](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="21fd4-132">先决条件</span><span class="sxs-lookup"><span data-stu-id="21fd4-132">Prerequisites</span></span>
<span data-ttu-id="21fd4-133">Windows CE 应用容器软件需要2013年 6) 2020 月版的 Windows Compact (版本6294的更新版本，以及适用于 x64 和 ARM32 的更新的 Windows 10 IoT 核心包 (8 月2020更新或更高) 版本。</span><span class="sxs-lookup"><span data-stu-id="21fd4-133">The Windows CE App Container software requires an updated version of Windows Compact 2013 (Build number 6294 from June 2020 or later) along with updated Windows 10 IoT Core Packages for x64 and ARM32 (August 2020 update or later).</span></span> <span data-ttu-id="21fd4-134">注意：必须具有有效的[IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)订阅才能分发采用 CE 应用容器技术的设备。</span><span class="sxs-lookup"><span data-stu-id="21fd4-134">Note: You must have a valid [IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) subscription to distribute a device that employs the CE App Container technology.</span></span>

<span data-ttu-id="21fd4-135">Windows CE 应用容器软件需要2013年 6) 2020 月版的 Windows Compact (版本6294的更新版本，以及适用于 x64 和 ARM32 的更新的 Windows 10 IoT 核心包 (8 月2020更新或更高) 版本。</span><span class="sxs-lookup"><span data-stu-id="21fd4-135">The Windows CE App Container software requires an updated version of Windows Compact 2013 (Build number 6294 from June 2020 or later) along with updated Windows 10 IoT Core Packages for x64 and ARM32 (August 2020 update or later).</span></span>

> [!NOTE]
> <span data-ttu-id="21fd4-136">你必须具有有效的[IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)订阅才能分发采用 CE 应用容器技术的设备。</span><span class="sxs-lookup"><span data-stu-id="21fd4-136">You must have a valid [IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) subscription to distribute a device that employs the CE App Container technology.</span></span>


<span data-ttu-id="21fd4-137">此外，你将需要以下各项：</span><span class="sxs-lookup"><span data-stu-id="21fd4-137">Additionally, you will need the following:</span></span>

- <span data-ttu-id="21fd4-138">[Microsoft Visual Studio 2013 专业版或 Visual Studio 2015 professional](<https://visualstudio.microsoft.com/vs/>)。</span><span class="sxs-lookup"><span data-stu-id="21fd4-138">[Microsoft Visual Studio 2013 Professional or Visual Studio 2015 Professional](<https://visualstudio.microsoft.com/vs/>).</span></span> <span data-ttu-id="21fd4-139">这些版本是应用程序生成器和平台生成器工具所必需的。</span><span class="sxs-lookup"><span data-stu-id="21fd4-139">These versions are required for both the Application Builder and Platform Builder tools.</span></span>

- [<span data-ttu-id="21fd4-140">适用于 Windows Embedded Compact 2013 的应用程序生成器</span><span class="sxs-lookup"><span data-stu-id="21fd4-140">Application Builder for Windows Embedded Compact 2013</span></span>](<https://www.microsoft.com/download/details.aspx?id=38819>)

- <span data-ttu-id="21fd4-141">适用于 Windows Compact 2013 的平台生成器</span><span class="sxs-lookup"><span data-stu-id="21fd4-141">Platform Builder for Windows Compact 2013</span></span>

- <span data-ttu-id="21fd4-142">[Windows IoT 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)中引用的工具</span><span class="sxs-lookup"><span data-stu-id="21fd4-142">The tools referenced in the [Windows IoT Manufacturing   Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)</span></span>
- <span data-ttu-id="21fd4-143">请记住，安装已更新的组件来代替本指南中所述的组件 (Windows 10 ADK 和 Windows 10 ADK PE 加载项、IoT Core ADK 外接程序、Windows 10 IoT 核心仪表板) </span><span class="sxs-lookup"><span data-stu-id="21fd4-143">Remember to install the updated components in place of the ones referenced in this guide (Windows 10 ADK and Windows 10 ADK PE Add-on, IoT Core ADK Add-ons, Windows 10 IoT Core Dashboard)</span></span>

- <span data-ttu-id="21fd4-144">工作 IoT 核心 BSP</span><span class="sxs-lookup"><span data-stu-id="21fd4-144">A Working IoT Core BSP</span></span>

### <a name="configuring-building-and-packaging-ce-for-the-windows-ce-app-container"></a><span data-ttu-id="21fd4-145">为 Windows CE 应用容器配置、构建和打包 CE</span><span class="sxs-lookup"><span data-stu-id="21fd4-145">Configuring, Building, and Packaging CE for the Windows CE App Container</span></span>

<span data-ttu-id="21fd4-146">[用于创建 Windows Embedded Compact 2013 映像的过程](https://docs.microsoft.com/previous-versions/windows/embedded/jj200349(v=winembedded.80))没有明显更新。</span><span class="sxs-lookup"><span data-stu-id="21fd4-146">The [process for creating a Windows Embedded Compact 2013 image](https://docs.microsoft.com/previous-versions/windows/embedded/jj200349(v=winembedded.80)) has not been updated significantly.</span></span> <span data-ttu-id="21fd4-147">生成映像的一般过程如下：</span><span class="sxs-lookup"><span data-stu-id="21fd4-147">The general process for building an image is:</span></span>

1. <span data-ttu-id="21fd4-148">在平台生成器中创建 OS 设计项目</span><span class="sxs-lookup"><span data-stu-id="21fd4-148">Create OS Design project with Platform Builder</span></span>

2. <span data-ttu-id="21fd4-149">选择 "平台生成器" 支持包 (BSP) </span><span class="sxs-lookup"><span data-stu-id="21fd4-149">Select the Platform Builder Board Support Package (BSP)</span></span>

3. <span data-ttu-id="21fd4-150">选择适当的设计模板</span><span class="sxs-lookup"><span data-stu-id="21fd4-150">Choose the appropriate design template</span></span>

4. <span data-ttu-id="21fd4-151">配置设计模板提供的选项</span><span class="sxs-lookup"><span data-stu-id="21fd4-151">Configure the options provided by the design template</span></span>

5. <span data-ttu-id="21fd4-152">选择性地将子项目添加到设计项目</span><span class="sxs-lookup"><span data-stu-id="21fd4-152">Optionally add Sub-projects to the design project</span></span>

6. <span data-ttu-id="21fd4-153">生成映像</span><span class="sxs-lookup"><span data-stu-id="21fd4-153">Build the image</span></span>

<span data-ttu-id="21fd4-154">主要更改是为 CE 映像选择正确的 BSP 和其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="21fd4-154">The primary change is in the selection of the correct BSP and additional considerations for the CE image.</span></span> <span data-ttu-id="21fd4-155">本指南假定你已熟悉构建 Windows CE 系统映像的过程，但在 "已更改" 部分有必要更深入地查看。</span><span class="sxs-lookup"><span data-stu-id="21fd4-155">This guide assumes you are already familiar with the process to build a Windows CE system image, but it is worth looking more deeply at the changed section.</span></span>

<span data-ttu-id="21fd4-156">以下步骤是指上面的步骤2。</span><span class="sxs-lookup"><span data-stu-id="21fd4-156">The following step refers to Step 2 above.</span></span> <span data-ttu-id="21fd4-157">这是以前的 OS 设计项目过程的唯一组成部分，它是在使用 CE 应用程序容器时进行更改的。</span><span class="sxs-lookup"><span data-stu-id="21fd4-157">It is the only part of the previous OS Design project process that is changed when using the CE App Container.</span></span>

#### <a name="step-2---platform-builder-bsp-selection"></a><span data-ttu-id="21fd4-158">步骤 2-平台生成器 BSP 选择</span><span class="sxs-lookup"><span data-stu-id="21fd4-158">Step 2 - Platform Builder BSP Selection</span></span>

<span data-ttu-id="21fd4-159">为了支持 Windows CE 应用容器，已将面向 x86 和 ARM 体系结构的新 BSP 添加到了平台生成器中。</span><span class="sxs-lookup"><span data-stu-id="21fd4-159">To support the Windows CE App Container, a new BSP that targets x86 and ARM architectures has been added to Platform Builder.</span></span>

<span data-ttu-id="21fd4-160">为 CE 应用容器创建 OS 设计时，请选择 "Windows CE App Container： x86" 或 "Windows CE App Container： ARMv7" (ARM32) ，具体取决于基于 IoT 内核的设备的底层硬件。</span><span class="sxs-lookup"><span data-stu-id="21fd4-160">When creating an OS Design for the CE App Container, select either the “Windows CE App Container: x86” or “Windows CE App Container: ARMv7” (ARM32) depending on the underlying hardware for your IoT Core based device.</span></span> <span data-ttu-id="21fd4-161">例如，如果目标 IoT 核心设备使用 Intel 硬件，你将选择 "Windows CE 应用容器： x86" 选项。</span><span class="sxs-lookup"><span data-stu-id="21fd4-161">For example, if your target IoT Core device uses Intel hardware, you will select the “Windows CE App Container: x86” option.</span></span> <span data-ttu-id="21fd4-162">或者，如果 IoT 核心硬件使用 NXP MX6，将选择 "Windows CE App Container： ARMv7" 选项。</span><span class="sxs-lookup"><span data-stu-id="21fd4-162">Alternatively, if your IoT Core hardware uses NXP i.MX6, you will select the “Windows CE App Container: ARMv7” option.</span></span>

![选择 CE 应用容器 BSP](./media/WindowsCEAppContainer/image2.png)

<span data-ttu-id="21fd4-164">完成此操作后，就可以像平常一样为 Windows Embedded Compact 映像配置选项和子项目。</span><span class="sxs-lookup"><span data-stu-id="21fd4-164">After doing this you will have the ability to configure the options and sub-projects just like you would normally do for a Windows Embedded Compact image.</span></span> <span data-ttu-id="21fd4-165">这些配置将内置到 CE 容器，你将部署到 Windows 10 IoT Core 映像。</span><span class="sxs-lookup"><span data-stu-id="21fd4-165">These configurations will be built into the CE Container that you will deploy into your Windows 10 IoT Core image.</span></span>

### <a name="building-the-windows-10-iot-core-image"></a><span data-ttu-id="21fd4-166">构建 Windows 10 IoT Core 映像</span><span class="sxs-lookup"><span data-stu-id="21fd4-166">Building the Windows 10 IoT Core Image</span></span>

> [!NOTE]
> <span data-ttu-id="21fd4-167">作为[Windows 10 IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)一部分的实验室中更详细地介绍了此过程。</span><span class="sxs-lookup"><span data-stu-id="21fd4-167">This process is covered in more detail in the labs that are part of the [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image).</span></span> <span data-ttu-id="21fd4-168">以下部分仅提供在 IoT Core 映像生成过程的某些阶段执行的其他操作。</span><span class="sxs-lookup"><span data-stu-id="21fd4-168">The section below only provides additional actions to execute at certain stages of the IoT Core image building process.</span></span> <span data-ttu-id="21fd4-169">在继续操作之前，强烈建议先熟悉 Windows 10 IoT 核心制造指南。</span><span class="sxs-lookup"><span data-stu-id="21fd4-169">It is highly recommended to familiarize yourself with the Windows 10 IoT Core Manufacturing Guide before proceeding.</span></span>

#### <a name="process-overview"></a><span data-ttu-id="21fd4-170">过程概述</span><span class="sxs-lookup"><span data-stu-id="21fd4-170">Process overview</span></span>

<span data-ttu-id="21fd4-171">与构建 Windows Embedded Compact 映像的过程不同，Windows 10 IoT Core 分离还集成了固件的创建、板支持包、映像定义和应用程序包含。</span><span class="sxs-lookup"><span data-stu-id="21fd4-171">Unlike the process of building a Windows Embedded Compact image, Windows 10 IoT Core decouples yet integrates the creation of firmware, board support packages, image definition and application inclusion.</span></span> <span data-ttu-id="21fd4-172">通过利用这些组件的不同技术，你可以将所需的工作划分为不同团队或组织中的个人所需的工作。</span><span class="sxs-lookup"><span data-stu-id="21fd4-172">By utilizing different technologies for these pieces, you can separate the work you need to do amongst different teams or individuals in your organization.</span></span>

<span data-ttu-id="21fd4-173">创建映像的基本步骤如下：</span><span class="sxs-lookup"><span data-stu-id="21fd4-173">The basic steps in creating an image are:</span></span>

1. [<span data-ttu-id="21fd4-174">创建工作区</span><span class="sxs-lookup"><span data-stu-id="21fd4-174">Create a  workspace</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

2. [<span data-ttu-id="21fd4-175"> (BSP) 导入相应的 IoT 核心板支持包</span><span class="sxs-lookup"><span data-stu-id="21fd4-175">Import the appropriate IoT Core Board Support Package  (BSP)</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

3. <span data-ttu-id="21fd4-176">导入先前创建的 CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="21fd4-176">Import the CE App Container you created previously</span></span>

4. [<span data-ttu-id="21fd4-177">创建产品定义</span><span class="sxs-lookup"><span data-stu-id="21fd4-177">Create your product  definition</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

5. [<span data-ttu-id="21fd4-178">向产品添加功能和应用程序</span><span class="sxs-lookup"><span data-stu-id="21fd4-178">Add features and applications to your  product</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

6. [<span data-ttu-id="21fd4-179"> (FFU 创建完整的闪存更新) </span><span class="sxs-lookup"><span data-stu-id="21fd4-179">Build your Full Flash Update  (FFU)</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

7. [<span data-ttu-id="21fd4-180">将 FFU 部署到设备并测试</span><span class="sxs-lookup"><span data-stu-id="21fd4-180">Deploy the FFU to the device and  test</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

8. [<span data-ttu-id="21fd4-181">完成零售 FFU 并为其签名</span><span class="sxs-lookup"><span data-stu-id="21fd4-181">Finalize and sign your retail  FFU</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/build-retail-image)

<span data-ttu-id="21fd4-182">在[Windows 10 IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)中，每个步骤都有详细指南。</span><span class="sxs-lookup"><span data-stu-id="21fd4-182">There are detailed guides for each of these steps as part of the [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image).</span></span> <span data-ttu-id="21fd4-183">尽管其中一些步骤类似于使用平台生成器 (PB) 创建设备映像这一过程，但有必要更深入地探讨一些区域。</span><span class="sxs-lookup"><span data-stu-id="21fd4-183">While some of these steps are like the process of using Platform Builder (PB) to create a device image it is worth exploring some areas more deeply.</span></span>

<span data-ttu-id="21fd4-184">以下各节介绍了上述步骤，其中存在其他信息或更改。</span><span class="sxs-lookup"><span data-stu-id="21fd4-184">The following sections refer to the steps above where additional information or changes exist.</span></span> <span data-ttu-id="21fd4-185">由于不是每个步骤都发生了更改，或者某些步骤具有多个选项，因此标题会将你返回到你在过程中所处的位置。</span><span class="sxs-lookup"><span data-stu-id="21fd4-185">As not every step changes or some steps have multiple options the title will refer you back to where you are in the process.</span></span>

##### <a name="step-3---importing-the-windows-ce-app-container"></a><span data-ttu-id="21fd4-186">步骤 3-导入 Windows CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="21fd4-186">Step 3 - Importing the Windows CE App Container</span></span>

<span data-ttu-id="21fd4-187">Windows CE 应用容器使用上图所述的 PB 创建，并使用[IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-IoTCEPAL.md#Import-IoTCEPAL)命令导入到 IoT 核心工作区。</span><span class="sxs-lookup"><span data-stu-id="21fd4-187">The Windows CE App Container is created using PB as discussed above and imported into your IoT Core workspace by using the [Import-IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-IoTCEPAL.md#Import-IoTCEPAL) command.</span></span> <span data-ttu-id="21fd4-188">此命令会将 CE 单层发布目录中所需的内容复制到 IoT ADK 工作区。</span><span class="sxs-lookup"><span data-stu-id="21fd4-188">This command will copy the required contents from the CE flat release directory into the IoT ADK workspace.</span></span> <span data-ttu-id="21fd4-189">如果多次调用，则会在工作区中的目录下备份以前的状态 `Source-\$Arch\CEPAL.OLD` 。</span><span class="sxs-lookup"><span data-stu-id="21fd4-189">If invoked multiple times, the previous state is backed up under the `Source-\$Arch\CEPAL.OLD` directory in the workspace.</span></span>

##### <a name="step-5---adding-ce-app-container-to-a-product"></a><span data-ttu-id="21fd4-190">步骤 5-将 CE 应用容器添加到产品</span><span class="sxs-lookup"><span data-stu-id="21fd4-190">Step 5 - Adding CE App Container to a product</span></span>

<span data-ttu-id="21fd4-191">将 CE 应用容器定义导入到工作区后，需要确保运行[IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTCEPAL.md#Add-IoTCEPAL)命令，该命令会将对 CE 应用容器包的引用添加到相关产品 OEMInput.xml 文件 (测试和零售) 。</span><span class="sxs-lookup"><span data-stu-id="21fd4-191">Once you have imported your CE App Container definition to your workspace you will need to ensure that you run the [Add-IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTCEPAL.md#Add-IoTCEPAL) command, which will add a reference to CE App Container packages to the relevant product OEMInput.xml files (Test and Retail).</span></span>

<span data-ttu-id="21fd4-192">下一步是使用[IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTProductFeature.md#Add-IoTProductFeature)命令将 IOT \_ CEPAL 功能添加到 OEMInput.xml。</span><span class="sxs-lookup"><span data-stu-id="21fd4-192">The next step is to use the [Add-IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTProductFeature.md#Add-IoTProductFeature) command to add the IOT\_CEPAL feature to the OEMInput.xml.</span></span> <span data-ttu-id="21fd4-193">这会将 Windows CE 应用容器的 Windows 主机支持添加 (Windows CE 的前端 UWP 应用 + 支持驱动程序) 到我们的产品定义，并在默认应用组中包含 CE 应用容器。</span><span class="sxs-lookup"><span data-stu-id="21fd4-193">This adds the Windows Host support for the Windows CE App Container (Windows CE front end UWP app + support drivers) to  our product definition and includes the CE App Container in the default Apps group.</span></span> <span data-ttu-id="21fd4-194">我们将在后面的部分中讨论启动配置。</span><span class="sxs-lookup"><span data-stu-id="21fd4-194">We’ll discuss start-up configuration in a later section.</span></span>

##### <a name="step-6---build-your-cab-files"></a><span data-ttu-id="21fd4-195">步骤 6-生成 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="21fd4-195">Step 6 - Build your CAB files</span></span>

<span data-ttu-id="21fd4-196">这是在创建 FFU 的过程中的一个重要步骤，并且应在每次更改配置、添加/更改应用程序或驱动程序时执行。</span><span class="sxs-lookup"><span data-stu-id="21fd4-196">This is an important step during the creation of your FFU and should be done whenever you change a configuration, add/change an application or drivers.</span></span> <span data-ttu-id="21fd4-197">将使用[IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md#New-IoTCabPackage)和 "All" 选项。</span><span class="sxs-lookup"><span data-stu-id="21fd4-197">You will use the [New-IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md#New-IoTCabPackage) with the “All” option.</span></span> <span data-ttu-id="21fd4-198">你还可以根据需要构建单一功能，但通常应在生成 FFU 的步骤之前重新生成所有包。</span><span class="sxs-lookup"><span data-stu-id="21fd4-198">You can also build Single features as needed but in general you should rebuild all the packages prior to the step of building your FFU as best practice.</span></span>

##### <a name="step-7---deploying-your-ffu-to-your-device"></a><span data-ttu-id="21fd4-199">步骤 7-将 FFU 部署到设备</span><span class="sxs-lookup"><span data-stu-id="21fd4-199">Step 7 - Deploying your FFU to your device</span></span>

<span data-ttu-id="21fd4-200">构建映像后，可以将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="21fd4-200">Once the image is built you can deploy it to a device.</span></span> <span data-ttu-id="21fd4-201">这可以通过使用[DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/what-is-dism)的命令行通过设备特定的部署过程或通过使用[Windows 10 IoT 核心仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)来完成。</span><span class="sxs-lookup"><span data-stu-id="21fd4-201">This can be done from the command line using [DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/what-is-dism), via your device specific deployment process or by using the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="21fd4-202">有关更多详细信息，请访问[Windows 10 IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)。</span><span class="sxs-lookup"><span data-stu-id="21fd4-202">More details are available as part of the [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image).</span></span>

##### <a name="additional-step-7-information---deploying-the-windows-ce-app-container-to-a-device-when-using-an-existing-ffu"></a><span data-ttu-id="21fd4-203">其他步骤7信息-使用现有 FFU 时将 Windows CE 应用容器部署到设备</span><span class="sxs-lookup"><span data-stu-id="21fd4-203">Additional Step 7 Information - Deploying the Windows CE App Container to a device when using an existing FFU</span></span>

<span data-ttu-id="21fd4-204">CE Cab 是 IoT Core 上的可部署包。</span><span class="sxs-lookup"><span data-stu-id="21fd4-204">The CE CABs are deployable packages on IoT Core.</span></span> <span data-ttu-id="21fd4-205">如果存在现有的 IoT 核心映像，可以使用命令将这些 Cab 部署到设备 `APPLYUPDATE` 。</span><span class="sxs-lookup"><span data-stu-id="21fd4-205">If there is an existing IoT Core image, these CABs can be deployed to the device using the `APPLYUPDATE` command.</span></span> <span data-ttu-id="21fd4-206">首先将 Cab 复制到设备，然后通过暂存并提交 Cab `APPLYUPDATE` 。</span><span class="sxs-lookup"><span data-stu-id="21fd4-206">First copy the CABs to the device, then stage and commit the CABs with `APPLYUPDATE`.</span></span> <span data-ttu-id="21fd4-207">请注意，更新此方法会使包版本控制更为强大，因此，如果要将包的更新版本部署到设备，则这些版本的版本号必须更高。</span><span class="sxs-lookup"><span data-stu-id="21fd4-207">Do note that updating this way respects package versioning, so if updated versions of packages are to be deployed to the device, they must have a greater version number.</span></span> <span data-ttu-id="21fd4-208"> (参阅 IoT ADK 环境) 中的 IoTCabVersion 命令。</span><span class="sxs-lookup"><span data-stu-id="21fd4-208">(See the Set-IoTCabVersion command in the IoT ADK environment).</span></span> <span data-ttu-id="21fd4-209">有关此方面的详细信息，请参阅[创建和安装包](https://docs.microsoft.com/enus/windows-hardware/manufacture/iot/create-install-package.)</span><span class="sxs-lookup"><span data-stu-id="21fd4-209">More information on this can be found in [Create and Install Packages](https://docs.microsoft.com/enus/windows-hardware/manufacture/iot/create-install-package.)</span></span>

##### <a name="step-8---building-a-retail-image"></a><span data-ttu-id="21fd4-210">步骤 8-构建零售映像</span><span class="sxs-lookup"><span data-stu-id="21fd4-210">Step 8 - Building a retail image</span></span>

<span data-ttu-id="21fd4-211">使用正确的签名映像是保护和更新设备的重要部分。</span><span class="sxs-lookup"><span data-stu-id="21fd4-211">Having a properly signed image is an important part of securing and updating a device.</span></span> <span data-ttu-id="21fd4-212">对于 Windows 10 IoT Core，此外观显示为测试签名版本和已签名零售版本之间的差异。</span><span class="sxs-lookup"><span data-stu-id="21fd4-212">For Windows 10 IoT Core this appears as the difference between Test signed and Retail signed builds.</span></span> <span data-ttu-id="21fd4-213">绝不应公开部署测试已签名映像。</span><span class="sxs-lookup"><span data-stu-id="21fd4-213">You should never publicly deploy a test signed image.</span></span> <span data-ttu-id="21fd4-214">测试签名映像只应用于调试目的，在创建最终零售签名映像之前，应更正任何错误或配置更改。</span><span class="sxs-lookup"><span data-stu-id="21fd4-214">Test signed images should only be used for debug purposes and you should correct any errors or configuration changes prior to creating your final retail signed image.</span></span>

> [!NOTE]
> <span data-ttu-id="21fd4-215">除了计算机上安装的开发和部署工具外，还需要以下内容来启用零售签名：</span><span class="sxs-lookup"><span data-stu-id="21fd4-215">In addition to the development and deployment tools installed on your machine you will also need the following to enable retail signing:</span></span>
>
> - <span data-ttu-id="21fd4-216">零售代码签名证书</span><span class="sxs-lookup"><span data-stu-id="21fd4-216">A retail code-signing certificate</span></span>
> - <span data-ttu-id="21fd4-217">交叉签名证书</span><span class="sxs-lookup"><span data-stu-id="21fd4-217">A cross-signing certificate</span></span>

#### <a name="properly-signing-and-including-your-applications"></a><span data-ttu-id="21fd4-218">正确签名和包括应用程序</span><span class="sxs-lookup"><span data-stu-id="21fd4-218">Properly signing and including your applications</span></span>

<span data-ttu-id="21fd4-219">如果你有一个或多个你想要包含在 Windows 10 IoT 核心零售映像中的自定义应用程序，则需要验证这些应用程序是否已在零售映像中包含它们时进行了正确签名。</span><span class="sxs-lookup"><span data-stu-id="21fd4-219">If you have one or more custom applications that you want to include in your Windows 10 IoT Core retail image, you need to verify that these applications are signed properly when including them in your retail image.</span></span>

## <a name="additional-information"></a><span data-ttu-id="21fd4-220">其他信息</span><span class="sxs-lookup"><span data-stu-id="21fd4-220">Additional Information</span></span>

### <a name="adding-new-applications-to-an-existing-image"></a><span data-ttu-id="21fd4-221">将新应用程序添加到现有映像</span><span class="sxs-lookup"><span data-stu-id="21fd4-221">Adding new applications to an existing image</span></span>

<span data-ttu-id="21fd4-222">若要将新应用程序添加到现有的操作系统设计中，可以将该项目作为子项目添加到 OS 设计项目，也可以创建常规部署 CAB 包，将这些包部署到作为初始设备设置的一部分的设备上。</span><span class="sxs-lookup"><span data-stu-id="21fd4-222">To add a new application to an existing OS Design you can either add the project as a sub-project to the OS Design Project or you can create normal deployment CAB packages to deploy those to the device as part of the initial device setup.</span></span>

### <a name="packaging-best-practices"></a><span data-ttu-id="21fd4-223">打包最佳实践</span><span class="sxs-lookup"><span data-stu-id="21fd4-223">Packaging Best Practices</span></span>

<span data-ttu-id="21fd4-224">应始终确保包尽可能细化，以减少更新时间。</span><span class="sxs-lookup"><span data-stu-id="21fd4-224">You should always aim to make sure packages are as granular as possible to reduce update time.</span></span>

<span data-ttu-id="21fd4-225">由于包是更新的最小单位，因此请确保每个包尽可能小。</span><span class="sxs-lookup"><span data-stu-id="21fd4-225">Since a package is the smallest unit of updating, make sure that each package is as small as possible.</span></span> <span data-ttu-id="21fd4-226">在平台生成器中生成时，根据选手文件自动将生成的包与内存部分和模块/文件类型分隔开来。</span><span class="sxs-lookup"><span data-stu-id="21fd4-226">When building in Platform Builder, the generated packages are separated according to memory section and module/file type according to the bib file automatically.</span></span>

- <span data-ttu-id="21fd4-227">对于在平台生成器中构建并通过 OSDesign 进行打包的自定义资产，请考虑将自定义资产添加到选手 (不在 NK) 中的单独内存部分，以便自定义代码更新与 CE OS 的更新不同。</span><span class="sxs-lookup"><span data-stu-id="21fd4-227">For custom assets built in Platform Builder and packaged through OSDesign.bib, consider adding custom assets into a separate memory section in the BIB (not in NK), so that updates to custom code can ship separate from updates to the CE OS.</span></span>

- <span data-ttu-id="21fd4-228">对于通过 IoT ADK 打包命令添加的自定义资产：请确保创建的包尽可能小。</span><span class="sxs-lookup"><span data-stu-id="21fd4-228">For custom assets added through the IoT ADK packaging commands: Make sure the packages created are as small as possible.</span></span>

### <a name="adding-other-things-to-the-platform-builder-package"></a><span data-ttu-id="21fd4-229">向平台生成器包添加其他项</span><span class="sxs-lookup"><span data-stu-id="21fd4-229">Adding other things to the Platform Builder package</span></span>

<span data-ttu-id="21fd4-230">通常，建议不要修改平台生成器生成的生成的包，以将其他组件包括到系统映像中。</span><span class="sxs-lookup"><span data-stu-id="21fd4-230">In general, the recommendation is not to modify the resulting package produced by Platform Builder to include additional components into the system image.</span></span> <span data-ttu-id="21fd4-231">而应按照[Windows 10 IoT Core 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)进行操作。</span><span class="sxs-lookup"><span data-stu-id="21fd4-231">Instead, follow the [Windows 10 IoT Core manufacturing guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="21fd4-232">但是，如果必须将文件添加到平台生成器创建的包中，请按照现有过程进行操作。</span><span class="sxs-lookup"><span data-stu-id="21fd4-232">However, if files must be added to the package that is created by Platform Builder, follow your existing process.</span></span> <span data-ttu-id="21fd4-233">向 PB 生成的包添加内容时，请考虑以下事项：</span><span class="sxs-lookup"><span data-stu-id="21fd4-233">When adding content to the package generated by PB, consider the following:</span></span>

- <span data-ttu-id="21fd4-234">包的最大大小 (有关 400MB) ，超过此大小将阻止更新。</span><span class="sxs-lookup"><span data-stu-id="21fd4-234">There is a maximum size for packages (about 400MB) and exceeding this size will prevent updating.</span></span>

- <span data-ttu-id="21fd4-235">更新会在包粒度进行。</span><span class="sxs-lookup"><span data-stu-id="21fd4-235">Updates happen on package granularity.</span></span> <span data-ttu-id="21fd4-236">如果需要更新包中的单个资产，则该程序包的所有资产将同时更新。</span><span class="sxs-lookup"><span data-stu-id="21fd4-236">If a single asset in the package needs to be updated, then all the assets of that package will be updated at the same time.</span></span> <span data-ttu-id="21fd4-237">若要减少更新的大小，请将内容隔离到单独的包中，以最大程度地减少总体更新大小。</span><span class="sxs-lookup"><span data-stu-id="21fd4-237">To reduce the size of updates, isolate content into separate packages to minimize the overall update size.</span></span>

### <a name="adding-additional-files-through-platform-builder"></a><span data-ttu-id="21fd4-238">通过平台生成器添加其他文件</span><span class="sxs-lookup"><span data-stu-id="21fd4-238">Adding additional files through Platform Builder</span></span>

<span data-ttu-id="21fd4-239">上面详述的打包过程由与构建 CE 箱文件相同的输入驱动。</span><span class="sxs-lookup"><span data-stu-id="21fd4-239">The packaging process detailed above is driven by the same inputs that go into building a CE BIN file.</span></span> <span data-ttu-id="21fd4-240">因此，如果在 OSDesign 中引用了文件，则会将选手中的注册表项添加到 OSDesign 中， `MAKEIMG` 进程将在生成的 CAB 文件中包含这些文件。</span><span class="sxs-lookup"><span data-stu-id="21fd4-240">So, if the files are referenced in OSDesign.bib and registry entries are added to OSDesign.reg, the `MAKEIMG` process will include these files in the resulting CAB file.</span></span> <span data-ttu-id="21fd4-241">在此过程中， `MAKEIMG` 将立即执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="21fd4-241">During this process `MAKEIMG` will now:</span></span>

1. <span data-ttu-id="21fd4-242">`ROMIMAGE`将在平面发布目录中创建一个名为的目录 `CEPAL\_PKG` (FRD) ，该目录将 Windows CE 的目录结构暂存用于 CEPAL。</span><span class="sxs-lookup"><span data-stu-id="21fd4-242">`ROMIMAGE` will create a directory named `CEPAL\_PKG` within the Flat Release Directory (FRD) that stages an installed directory structure for Windows CE for CEPAL.</span></span>

2. <span data-ttu-id="21fd4-243">`ROMIMAGE`列出基于 CE 选手文件放入的所有 CE 文件的清单 `CEPAL\_PKG` 。</span><span class="sxs-lookup"><span data-stu-id="21fd4-243">`ROMIMAGE` inventories all CE files that were placed into `CEPAL\_PKG` based on CE BIB files.</span></span>

3. <span data-ttu-id="21fd4-244">`ROMIMAGE`将为每个内存部分创建多个 WM.XML 文件。</span><span class="sxs-lookup"><span data-stu-id="21fd4-244">`ROMIMAGE` will create multiple WM.XML files for each memory section.</span></span> <span data-ttu-id="21fd4-245">这样做的目的是为了使更新以更精细的方式推送，因为更新的最小单位是包。</span><span class="sxs-lookup"><span data-stu-id="21fd4-245">This is done so that updates can be pushed in a more granular fashion as the minimum unit of update is a package.</span></span>

4. <span data-ttu-id="21fd4-246">`ROMIMAGE`将创建 `CEPALFM.xml` 引用所有已创建的包的。</span><span class="sxs-lookup"><span data-stu-id="21fd4-246">`ROMIMAGE` will create `CEPALFM.xml` which references all the created packages.</span></span>

<span data-ttu-id="21fd4-247">所有创建的包都将使用固定的前缀命名 `“%OEM\_NAME%.WindowsCE.\*”` ，其中， `%OEM\_NAME%` 将在调用[IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md)时在 IoT Core 创建过程中填充。</span><span class="sxs-lookup"><span data-stu-id="21fd4-247">All of the packages created will be named with a fixed prefix of `“%OEM\_NAME%.WindowsCE.\*”`, where `%OEM\_NAME%` is populated during the IoT Core creation process when calling [New-IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md).</span></span> <span data-ttu-id="21fd4-248">命名空间中的包名称是从选手文件的内存部分派生的 (例如，NK) 后跟模块/文件 (也由选手文件) 决定。</span><span class="sxs-lookup"><span data-stu-id="21fd4-248">The Package Name within the name space is derived from the memory section in the BIB file (e.g. NK) followed by modules / files (also determined by the BIB file).</span></span>

#### <a name="communicating-between-windows-embedded-compact-2013-and-windows-10-iot-core-applications"></a><span data-ttu-id="21fd4-249">Windows Embedded Compact 2013 和 Windows 10 IoT Core 应用程序之间的通信</span><span class="sxs-lookup"><span data-stu-id="21fd4-249">Communicating between Windows Embedded Compact 2013 and Windows 10 IoT Core applications</span></span>

<span data-ttu-id="21fd4-250">在 CE 容器中运行的应用程序之间进行通信的建议方法是使用本地环回。</span><span class="sxs-lookup"><span data-stu-id="21fd4-250">The recommended approach to communicate between applications running in the CE Container is to use Local Loopback.</span></span> <span data-ttu-id="21fd4-251">有关详细信息，请参阅[本文档中的本地环回。](https://docs.microsoft.com/windows/iot-core/develop-your-app/loopback)</span><span class="sxs-lookup"><span data-stu-id="21fd4-251">You can read more on [Local Loopback in this document.](https://docs.microsoft.com/windows/iot-core/develop-your-app/loopback)</span></span>

### <a name="automatically-starting-the-ce-app-container-application"></a><span data-ttu-id="21fd4-252">自动启动 CE 应用容器应用程序</span><span class="sxs-lookup"><span data-stu-id="21fd4-252">Automatically starting the CE App Container application</span></span>

<span data-ttu-id="21fd4-253">若要自动启动 CE 容器应用程序，可以创建一个设置[包](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)，将启动应用程序设置为 "CEPAL. DkMonUWP \_ cw5n1h2txyewy！应用 "，并将其包含在映像中。</span><span class="sxs-lookup"><span data-stu-id="21fd4-253">To automatically start the CE Container application, you can create a [Provisioning Package](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image) that sets the startup application to “Microsoft.Windows.IoT.CEPAL.DkMonUWP\_cw5n1h2txyewy!App”, and included this provisioning package in the image.</span></span> <span data-ttu-id="21fd4-254">还需要使用[IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Remove-IoTProductFeature.md)命令删除默认启动应用程序，并 \_ 从 iot 核心产品定义中删除 IOT BERTHA 功能 ID。</span><span class="sxs-lookup"><span data-stu-id="21fd4-254">You will also need to remove the default startup application by using the [Remove-IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Remove-IoTProductFeature.md) command and removing the IOT\_BERTHA Feature ID from the IoT Core product definition.</span></span>

### <a name="available-configuration-settings-for-the-windows-ce-app-container"></a><span data-ttu-id="21fd4-255">Windows CE 应用容器的可用配置设置</span><span class="sxs-lookup"><span data-stu-id="21fd4-255">Available Configuration settings for the Windows CE App Container</span></span>

#### <a name="registry-based-configuration-in-ce"></a><span data-ttu-id="21fd4-256">CE 中基于注册表的配置</span><span class="sxs-lookup"><span data-stu-id="21fd4-256">Registry based configuration in CE</span></span>

##### <a name="non-executable-stack-by-default"></a><span data-ttu-id="21fd4-257">默认情况下，不可执行的堆栈</span><span class="sxs-lookup"><span data-stu-id="21fd4-257">Non-Executable Stack by Default</span></span>

<span data-ttu-id="21fd4-258">默认情况下，Windows CE 应用容器已禁用可执行堆栈页，以提高安全性。</span><span class="sxs-lookup"><span data-stu-id="21fd4-258">The Windows CE App Container has disabled executable stack pages by default to improve security.</span></span> <span data-ttu-id="21fd4-259">但是，某些旧版应用程序可能依赖于此行为才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="21fd4-259">However, some legacy applications may rely on this behavior to run correctly.</span></span> <span data-ttu-id="21fd4-260">若要启用可执行堆栈，请在 CE 映像中设置以下注册表值 (建议在平台生成器中将其放入 OSDesign) </span><span class="sxs-lookup"><span data-stu-id="21fd4-260">To Enable an Executable Stack, set the following registry value in the CE image (It is recommended that this goes into OSDesign.reg in Platform Builder)</span></span>

```AsciiDoc
KeyPath = HKEY\_LOCAL\_MACHINE\CEPAL
ValueName = MemoryOptions Type = REG\_DWORD
Value = 1
```

##### <a name="16-bit-565-override-for-gwes"></a><span data-ttu-id="21fd4-261">16位565替代 GWES</span><span class="sxs-lookup"><span data-stu-id="21fd4-261">16-bit 565 Override for GWES</span></span>

<span data-ttu-id="21fd4-262">如果 Windows CE 应用容器配置了32位显示，则 GWES 完成了16位到32位的 RGB 转换，假设16位 RGB 像素数据采用 RGB555 格式。</span><span class="sxs-lookup"><span data-stu-id="21fd4-262">If the Windows CE App Container is configured with a 32-bit display, then 16-bit to 32-bit RGB conversions are done by GWES are done with the assumption that 16-bit RGB pixel data is in RGB555 format.</span></span> <span data-ttu-id="21fd4-263">如果位图资源采用16位565，并且无法转换为 RGB555 的这些资源，则可以通过注册表项更改 GWES 的默认转换行为。</span><span class="sxs-lookup"><span data-stu-id="21fd4-263">If bitmap resources are in 16-bit 565, and conversion to a RGB555 of these resources is not possible, GWES’s default conversion behavior can be changed via a registry key.</span></span> <span data-ttu-id="21fd4-264">创建以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="21fd4-264">Create the following registry key:</span></span>

```AsciiDoc
HKEY\_LOCAL\_MACHINE\SYSTEM\GDI\16bpp565RGBPalette.
```

#### <a name="registry-based-configuration-in-host-iot-core"></a><span data-ttu-id="21fd4-265">Host 中基于注册表的配置 (IoT 核心) </span><span class="sxs-lookup"><span data-stu-id="21fd4-265">Registry based configuration in Host (IoT Core)</span></span>

##### <a name="configuring-serial-ports-for-the-windows-ce-app-container"></a><span data-ttu-id="21fd4-266">为 Windows CE 应用容器配置串行端口</span><span class="sxs-lookup"><span data-stu-id="21fd4-266">Configuring serial ports for the Windows CE App Container</span></span>

<span data-ttu-id="21fd4-267">需要将主机串行端口映射到 CE 环境。</span><span class="sxs-lookup"><span data-stu-id="21fd4-267">Host Serial ports need to be mapped into the CE environment.</span></span> <span data-ttu-id="21fd4-268">此映射存在于 IoT 核心的注册表中，需要由映像创建者进行配置。</span><span class="sxs-lookup"><span data-stu-id="21fd4-268">This mapping exists in registry in IoT Core and needs to be configured by the image creator.</span></span>

<span data-ttu-id="21fd4-269">在 `HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial` 中，存在使用以下架构将来宾 COM 端口映射到主机 COM 端口的配置条目。</span><span class="sxs-lookup"><span data-stu-id="21fd4-269">Under `HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial`, configuration entries exist to map Guest COM ports to Host COM ports using the following schema.</span></span>

```AsciiDoc
KeyPath = HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial\0

ValueName = Guest Type = REG\_SZ Value = COM1

ValueName = Host

Type = REG\_SZ

Value = \\?\Some\DeviceInterface\Path

KeyPath= HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial\1

ValueName = Guest Type = REG\_SZ Value = COM2

ValueName= Host Type = REG\_SZ

Value = \\?\Some\Other\DeviceInterface\Path
```

<span data-ttu-id="21fd4-270">如果上面的注册表路径在启动 CE 时不存在，则将根据系统上发现的串行设备来写入默认配置。</span><span class="sxs-lookup"><span data-stu-id="21fd4-270">If the registry path above does not exist when CE is booted, a default configuration will be written based on discovered serial devices on the system.</span></span>

#### <a name="file-based-configuration-in-host"></a><span data-ttu-id="21fd4-271">主机中基于文件的配置</span><span class="sxs-lookup"><span data-stu-id="21fd4-271">File Based configuration in Host</span></span>

<span data-ttu-id="21fd4-272">可以使用主机上的本地文件配置 CE 容器 `C:\WindowsCE\CEEnvConfig.json` 。</span><span class="sxs-lookup"><span data-stu-id="21fd4-272">The CE Container can be configured using a local file on the host `C:\WindowsCE\CEEnvConfig.json`.</span></span> <span data-ttu-id="21fd4-273">下面是此配置文件的示例：</span><span class="sxs-lookup"><span data-stu-id="21fd4-273">Here is a sample of this configuration file:</span></span>

```xml
{
 "OEMOptions" :
    {
     "GUI" : true,
     "Width" : 1024,
     "Height" : 768, "FillScreen" : true, "ColorDepth" : 32,
     "RefreshRate" : 30, "noAslrSupport" : true, "OemConfigApp" : "",
     "OemConfigFile" : ""
    },
 "CEPALDevOptions" :
    {
     "VsDebugMode" : true, "FastDebugBoot" : false
    }
 }
 ```

#### <a name="oemoptions"></a><span data-ttu-id="21fd4-274">OEMOptions</span><span class="sxs-lookup"><span data-stu-id="21fd4-274">OEMOptions</span></span>

| <span data-ttu-id="21fd4-275">键</span><span class="sxs-lookup"><span data-stu-id="21fd4-275">Key</span></span>           | <span data-ttu-id="21fd4-276">说明</span><span class="sxs-lookup"><span data-stu-id="21fd4-276">Description</span></span>                                                                                                            |
|---------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="21fd4-277">GUI</span><span class="sxs-lookup"><span data-stu-id="21fd4-277">GUI</span></span>           | <span data-ttu-id="21fd4-278">启动带有 UI (默认为 true) 的 CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="21fd4-278">Launch the CE app container with UI (default true)</span></span>                                                                     |
| <span data-ttu-id="21fd4-279">宽度</span><span class="sxs-lookup"><span data-stu-id="21fd4-279">Width</span></span>         | <span data-ttu-id="21fd4-280">CE 应用容器的宽度显示 (默认 1024) </span><span class="sxs-lookup"><span data-stu-id="21fd4-280">Width of the CE app container display (default 1024)</span></span>                                                                   |
| <span data-ttu-id="21fd4-281">高度</span><span class="sxs-lookup"><span data-stu-id="21fd4-281">Height</span></span>        | <span data-ttu-id="21fd4-282">CE 应用容器的高度显示 (默认 768) </span><span class="sxs-lookup"><span data-stu-id="21fd4-282">Height of the CE app container display (default 768)</span></span>                                                                   |
| <span data-ttu-id="21fd4-283">FillScreen</span><span class="sxs-lookup"><span data-stu-id="21fd4-283">FillScreen</span></span>    |                                                                                                                        |
| <span data-ttu-id="21fd4-284">ColorDepth</span><span class="sxs-lookup"><span data-stu-id="21fd4-284">ColorDepth</span></span>    | <span data-ttu-id="21fd4-285">设置默认的每像素 (默认位数 32) </span><span class="sxs-lookup"><span data-stu-id="21fd4-285">Sets default bits per pixel (default 32)</span></span>                                                                               |
| <span data-ttu-id="21fd4-286">RefreshRate</span><span class="sxs-lookup"><span data-stu-id="21fd4-286">RefreshRate</span></span>   | <span data-ttu-id="21fd4-287">每秒重绘显示的次数</span><span class="sxs-lookup"><span data-stu-id="21fd4-287">How many times the display is redrawn per second</span></span>                                                                       |
| <span data-ttu-id="21fd4-288">noAslrSupport</span><span class="sxs-lookup"><span data-stu-id="21fd4-288">noAslrSupport</span></span> | <span data-ttu-id="21fd4-289">在 CE 应用容器中禁用地址空间布局随机化 (默认值为 true) </span><span class="sxs-lookup"><span data-stu-id="21fd4-289">Disables address space layout randomization in the CE app container (default true)</span></span>                                     |
| <span data-ttu-id="21fd4-290">OEMConfigApp</span><span class="sxs-lookup"><span data-stu-id="21fd4-290">OEMConfigApp</span></span>  | <span data-ttu-id="21fd4-291">应为配置启动的 OEM 提供的应用的包系列名称。</span><span class="sxs-lookup"><span data-stu-id="21fd4-291">Package Family Name of an OEM provided app that should be launched for configuration.</span></span>                                  |
| <span data-ttu-id="21fd4-292">OEMConfigFile</span><span class="sxs-lookup"><span data-stu-id="21fd4-292">OEMConfigFile</span></span> | <span data-ttu-id="21fd4-293">文件的路径，该文件包含 OEMConfigApp 与 CE 应用容器之间共享的其他配置选项</span><span class="sxs-lookup"><span data-stu-id="21fd4-293">Path to a file that contains additional configuration options shared between the OEMConfigApp and the CE app container</span></span> |

<span data-ttu-id="21fd4-294">CE 应用容器只会使1个网络接口可供使用。</span><span class="sxs-lookup"><span data-stu-id="21fd4-294">The CE app container only makes 1 network interface available for use.</span></span> <span data-ttu-id="21fd4-295">如果主机系统中有多个 Nic，则必须在主机注册表中选择一个接口，以确保所选 NIC 是确定性的。</span><span class="sxs-lookup"><span data-stu-id="21fd4-295">If multiple NICs are present in the Host System, one interface must be selected in the Host Registry to ensure the selected NIC is deterministic.</span></span>

##### <a name="oemconfigfile"></a><span data-ttu-id="21fd4-296">OEMConfigFile</span><span class="sxs-lookup"><span data-stu-id="21fd4-296">OEMConfigFile</span></span>

<span data-ttu-id="21fd4-297">OEMConfigFile 在中指定 `C:\WindowsCE\CEEnvConfig.json` 。</span><span class="sxs-lookup"><span data-stu-id="21fd4-297">The OEMConfigFile is specified in `C:\WindowsCE\CEEnvConfig.json`.</span></span> <span data-ttu-id="21fd4-298">请确保此文件可由 UWP 应用程序读取。</span><span class="sxs-lookup"><span data-stu-id="21fd4-298">Make sure this file can be read by a UWP application.</span></span> <span data-ttu-id="21fd4-299">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="21fd4-299">The following is a sample:</span></span>

```xml
{
   “FactoryReset”: false, “PlatformBuilderDebugMode”: false,
   “NetInterface”: “Some Network Profile Id”
}
```

<span data-ttu-id="21fd4-300">选项：</span><span class="sxs-lookup"><span data-stu-id="21fd4-300">Options:</span></span>

| <span data-ttu-id="21fd4-301">键</span><span class="sxs-lookup"><span data-stu-id="21fd4-301">Key</span></span>                      | <span data-ttu-id="21fd4-302">说明</span><span class="sxs-lookup"><span data-stu-id="21fd4-302">Description</span></span>                                                                              |
|--------------------------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="21fd4-303">FactoryReset</span><span class="sxs-lookup"><span data-stu-id="21fd4-303">FactoryReset</span></span>             | <span data-ttu-id="21fd4-304">由 config 应用用来指示 CE 应用容器转储持久状态。</span><span class="sxs-lookup"><span data-stu-id="21fd4-304">Used by the config app to signal the CE App Container to dump persistent state.</span></span>          |
| <span data-ttu-id="21fd4-305">PlatformBuilderDebugMode</span><span class="sxs-lookup"><span data-stu-id="21fd4-305">PlatformBuilderDebugMode</span></span> | <span data-ttu-id="21fd4-306">用于使用支持使用平台生成器进行调试的 KITL 支持启动 CE 应用程序容器。</span><span class="sxs-lookup"><span data-stu-id="21fd4-306">Used to boot the CE App Container with KITL support for debugging with Platform Builder.</span></span> |
| <span data-ttu-id="21fd4-307">NetInterface</span><span class="sxs-lookup"><span data-stu-id="21fd4-307">NetInterface</span></span>             | <span data-ttu-id="21fd4-308">基于配置文件名称为 CE 选择一个网络接口。</span><span class="sxs-lookup"><span data-stu-id="21fd4-308">Select a Network Interface for CE based on profile name.</span></span>                                 |


## <a name="references"></a><span data-ttu-id="21fd4-309">参考</span><span class="sxs-lookup"><span data-stu-id="21fd4-309">References</span></span>

- [<span data-ttu-id="21fd4-310">获取自定义 Windows 10 IoT Core 所需的工具</span><span class="sxs-lookup"><span data-stu-id="21fd4-310">Get the tools needed to customize Windows 10 IoT Core</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)
- [<span data-ttu-id="21fd4-311">IoT 核心板支持的包 (BSP) </span><span class="sxs-lookup"><span data-stu-id="21fd4-311">IoT Core Board Supported Packages (BSP)</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/bsphardware)
- [<span data-ttu-id="21fd4-312">IoT 核心制造指南</span><span class="sxs-lookup"><span data-stu-id="21fd4-312">IoT Core Manufacturing Guide</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)
- [<span data-ttu-id="21fd4-313">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="21fd4-313">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)
- [<span data-ttu-id="21fd4-314">创建和安装包</span><span class="sxs-lookup"><span data-stu-id="21fd4-314">Create and Install Packages</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-install-package)
