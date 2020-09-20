---
title: 与 Windows CE 应用容器入门
ms.date: 08/25/2020
ms.topic: article
description: Windows CE 应用容器迁移入门指南
keywords: Windows 10 IoT Core，Windows CE，应用程序迁移，cepal
ms.openlocfilehash: 14afd281b199249cb47af8378312c13b3aea81f3
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90801360"
---
# <a name="getting-started-with-windows-ce-app-container"></a><span data-ttu-id="8c353-104">与 Windows CE 应用容器入门</span><span class="sxs-lookup"><span data-stu-id="8c353-104">Getting Started with Windows CE App Container</span></span>

<span data-ttu-id="8c353-105">Windows CE 应用容器是一种技术，允许大多数 CE 应用程序运行在 Windows 10 IoT Core 的顶层。</span><span class="sxs-lookup"><span data-stu-id="8c353-105">The Windows CE App Container is a technology that allows most CE applications to run on top of Windows 10 IoT Core.</span></span>

<span data-ttu-id="8c353-106">此解决方案分为两个阶段。</span><span class="sxs-lookup"><span data-stu-id="8c353-106">The solution is built in two stages.</span></span> <span data-ttu-id="8c353-107">第一阶段使用适用于 x86 或 ARM32 体系结构的 BSP 创建 Windows CE 2013 映像。</span><span class="sxs-lookup"><span data-stu-id="8c353-107">The first stage creates a Windows CE 2013 image using a BSP for either x86 or ARM32 architecture.</span></span> <span data-ttu-id="8c353-108">然后，在第二阶段中，此映像包含在 Windows 10 IoT Core 映像中，该映像利用 x64 或 ARM32 BSP 来实现将安装解决方案的特定设备硬件。</span><span class="sxs-lookup"><span data-stu-id="8c353-108">Then in the second stage, this image is included in a Windows 10 IoT Core image that utilizes the x64 or ARM32 BSP for the specific device hardware where the solution will be installed.</span></span>

![CE 应用容器体系结构](.//media/WindowsCEAppContainer/image1.png)

<span data-ttu-id="8c353-110">有关此体系结构的详细信息，请查看以下视频： [现代化 Windows CE 设备](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices)。</span><span class="sxs-lookup"><span data-stu-id="8c353-110">For more information about this architecture, please review this video: [Modernizing Windows CE Devices](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c353-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="8c353-111">Prerequisites</span></span>
<span data-ttu-id="8c353-112">Windows CE 应用容器软件需要 2013 [年 6) 2020 月版的 Windows Compact (版本 6294 ](https://support.microsoft.com/help/4566035/update-for-windows-embedded-compact-2013) 的更新版本，以及适用于 [x64 和 ARM32 的更新的 Windows 10 IoT 核心包 (8 月2020更新或更高) 版本 ](https://support.microsoft.com/help/4565349/windows-10-update-kb4565349)。</span><span class="sxs-lookup"><span data-stu-id="8c353-112">The Windows CE App Container software requires an updated version of [Windows Compact 2013 (Build number 6294 from June 2020 or later)](https://support.microsoft.com/help/4566035/update-for-windows-embedded-compact-2013) along with updated [Windows 10 IoT Core Packages for x64 and ARM32 (August 2020 update or later)](https://support.microsoft.com/help/4565349/windows-10-update-kb4565349).</span></span> <span data-ttu-id="8c353-113">若要获取适用于 Windows 10 IoT Core 的最新包，请联系你的 Microsoft 分发服务器。</span><span class="sxs-lookup"><span data-stu-id="8c353-113">To obtain the latest packages for Windows 10 IoT Core, please contact your Microsoft distributor.</span></span>

> [!NOTE]
> <span data-ttu-id="8c353-114">你必须具有有效的 [IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) 订阅才能分发采用 CE 应用容器技术的设备。</span><span class="sxs-lookup"><span data-stu-id="8c353-114">You must have a valid [IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) subscription to distribute a device that employs the CE App Container technology.</span></span>

<span data-ttu-id="8c353-115">此外，你将需要以下各项：</span><span class="sxs-lookup"><span data-stu-id="8c353-115">Additionally, you will need the following:</span></span>

- <span data-ttu-id="8c353-116">[Microsoft Visual Studio 2013 专业版或 Visual Studio 2015 professional](<https://visualstudio.microsoft.com/vs/>)。</span><span class="sxs-lookup"><span data-stu-id="8c353-116">[Microsoft Visual Studio 2013 Professional or Visual Studio 2015 Professional](<https://visualstudio.microsoft.com/vs/>).</span></span> <span data-ttu-id="8c353-117">这些版本是应用程序生成器和平台生成器工具所必需的。</span><span class="sxs-lookup"><span data-stu-id="8c353-117">These versions are required for both the Application Builder and Platform Builder tools.</span></span>

- [<span data-ttu-id="8c353-118">适用于 Windows Embedded Compact 2013 的应用程序生成器</span><span class="sxs-lookup"><span data-stu-id="8c353-118">Application Builder for Windows Embedded Compact 2013</span></span>](<https://www.microsoft.com/download/details.aspx?id=38819>)

- <span data-ttu-id="8c353-119">适用于 Windows Compact 2013 的平台生成器</span><span class="sxs-lookup"><span data-stu-id="8c353-119">Platform Builder for Windows Compact 2013</span></span>

- <span data-ttu-id="8c353-120">工作 IoT 核心 BSP</span><span class="sxs-lookup"><span data-stu-id="8c353-120">A Working IoT Core BSP</span></span>

- <span data-ttu-id="8c353-121">[Windows IoT 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)中引用的工具</span><span class="sxs-lookup"><span data-stu-id="8c353-121">The tools referenced in the [Windows IoT Manufacturing   Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)</span></span>
- <span data-ttu-id="8c353-122">请记住，安装已更新的组件来代替本指南中所述的组件 (Windows 10 ADK 和 Windows 10 ADK PE 加载项、IoT Core ADK 外接程序、Windows 10 IoT 核心仪表板) </span><span class="sxs-lookup"><span data-stu-id="8c353-122">Remember to install the updated components in place of the ones referenced in this guide (Windows 10 ADK and Windows 10 ADK PE Add-on, IoT Core ADK Add-ons, Windows 10 IoT Core Dashboard)</span></span>


## <a name="configuring-building-and-packaging-ce-for-the-windows-ce-app-container"></a><span data-ttu-id="8c353-123">为 Windows CE 应用容器配置、构建和打包 CE</span><span class="sxs-lookup"><span data-stu-id="8c353-123">Configuring, Building, and Packaging CE for the Windows CE App Container</span></span>

<span data-ttu-id="8c353-124">[用于创建 Windows Embedded Compact 2013 映像的过程](https://docs.microsoft.com/previous-versions/windows/embedded/jj200349(v=winembedded.80))没有明显更新。</span><span class="sxs-lookup"><span data-stu-id="8c353-124">The [process for creating a Windows Embedded Compact 2013 image](https://docs.microsoft.com/previous-versions/windows/embedded/jj200349(v=winembedded.80)) has not been updated significantly.</span></span> <span data-ttu-id="8c353-125">生成映像的一般过程如下：</span><span class="sxs-lookup"><span data-stu-id="8c353-125">The general process for building an image is:</span></span>

1. <span data-ttu-id="8c353-126">在平台生成器中创建 OS 设计项目</span><span class="sxs-lookup"><span data-stu-id="8c353-126">Create OS Design project with Platform Builder</span></span>

2. <span data-ttu-id="8c353-127">选择 "平台生成器" 支持包 (BSP) </span><span class="sxs-lookup"><span data-stu-id="8c353-127">Select the Platform Builder Board Support Package (BSP)</span></span>

3. <span data-ttu-id="8c353-128">选择适当的设计模板</span><span class="sxs-lookup"><span data-stu-id="8c353-128">Choose the appropriate design template</span></span>

4. <span data-ttu-id="8c353-129">配置设计模板提供的选项</span><span class="sxs-lookup"><span data-stu-id="8c353-129">Configure the options provided by the design template</span></span>

5. <span data-ttu-id="8c353-130">选择性地将子项目添加到设计项目</span><span class="sxs-lookup"><span data-stu-id="8c353-130">Optionally add Sub-projects to the design project</span></span>

6. <span data-ttu-id="8c353-131">生成映像</span><span class="sxs-lookup"><span data-stu-id="8c353-131">Build the image</span></span>

<span data-ttu-id="8c353-132">主要更改是为 CE 映像选择正确的 BSP 和其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="8c353-132">The primary change is in the selection of the correct BSP and additional considerations for the CE image.</span></span> <span data-ttu-id="8c353-133">本指南假定你已熟悉构建 Windows CE 系统映像的过程，但在 "已更改" 部分有必要更深入地查看。</span><span class="sxs-lookup"><span data-stu-id="8c353-133">This guide assumes you are already familiar with the process to build a Windows CE system image, but it is worth looking more deeply at the changed section.</span></span>

<span data-ttu-id="8c353-134">步骤2是以前的 OS 设计项目过程的唯一一部分，该过程是在使用 CE 应用容器时更改的，请参阅下面的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8c353-134">Step 2 is the only part of the previous OS Design project process that is changed when using the CE App Container, see below for additional details.</span></span>

### <a name="step-2---platform-builder-bsp-selection"></a><span data-ttu-id="8c353-135">步骤 2-平台生成器 BSP 选择</span><span class="sxs-lookup"><span data-stu-id="8c353-135">Step 2 - Platform Builder BSP Selection</span></span>

<span data-ttu-id="8c353-136">为了支持 Windows CE 应用容器，已将面向 x86 和 ARM 体系结构的新 BSP 添加到了平台生成器中。</span><span class="sxs-lookup"><span data-stu-id="8c353-136">To support the Windows CE App Container, a new BSP that targets x86 and ARM architectures has been added to Platform Builder.</span></span>

<span data-ttu-id="8c353-137">为 CE 应用容器创建 OS 设计时，请选择 "Windows CE App Container： x86" 或 "Windows CE App Container： ARMv7" (ARM32) ，具体取决于基于 IoT 内核的设备的底层硬件。</span><span class="sxs-lookup"><span data-stu-id="8c353-137">When creating an OS Design for the CE App Container, select either the “Windows CE App Container: x86” or “Windows CE App Container: ARMv7” (ARM32) depending on the underlying hardware for your IoT Core based device.</span></span>

<span data-ttu-id="8c353-138">例如，如果目标 IoT 核心设备使用 Intel 硬件，你将选择 "Windows CE 应用容器： x86" 选项。</span><span class="sxs-lookup"><span data-stu-id="8c353-138">For example, if your target IoT Core device uses Intel hardware, you will select the “Windows CE App Container: x86” option.</span></span> <span data-ttu-id="8c353-139">或者，如果 IoT 核心硬件使用 NXP MX6，将选择 "Windows CE App Container： ARMv7" 选项。</span><span class="sxs-lookup"><span data-stu-id="8c353-139">Alternatively, if your IoT Core hardware uses NXP i.MX6, you will select the “Windows CE App Container: ARMv7” option.</span></span>

![选择 CE 应用容器 BSP](./media/WindowsCEAppContainer/image2.png)

<span data-ttu-id="8c353-141">完成此操作后，你将能够配置选项和子项目，就像通常为 Windows Embedded Compact 映像执行的操作一样。</span><span class="sxs-lookup"><span data-stu-id="8c353-141">After doing this, you will have the ability to configure the options and sub-projects just like you would normally do for a Windows Embedded Compact image.</span></span> <span data-ttu-id="8c353-142">这些配置将内置到 CE 容器，你将部署到 Windows 10 IoT Core 映像。</span><span class="sxs-lookup"><span data-stu-id="8c353-142">These configurations will be built into the CE Container that you will deploy into your Windows 10 IoT Core image.</span></span>

## <a name="building-the-windows-10-iot-core-image"></a><span data-ttu-id="8c353-143">构建 Windows 10 IoT Core 映像</span><span class="sxs-lookup"><span data-stu-id="8c353-143">Building the Windows 10 IoT Core Image</span></span>

> [!NOTE]
> <span data-ttu-id="8c353-144">作为 [Windows 10 IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)一部分的实验室中更详细地介绍了此过程。</span><span class="sxs-lookup"><span data-stu-id="8c353-144">This process is covered in more detail in the labs that are part of the [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image).</span></span> <span data-ttu-id="8c353-145">以下部分仅提供在 IoT Core 映像生成过程的某些阶段执行的其他操作。</span><span class="sxs-lookup"><span data-stu-id="8c353-145">The section below only provides additional actions to execute at certain stages of the IoT Core image building process.</span></span> <span data-ttu-id="8c353-146">在继续操作之前，强烈建议先熟悉 Windows 10 IoT 核心制造指南。</span><span class="sxs-lookup"><span data-stu-id="8c353-146">It is highly recommended to familiarize yourself with the Windows 10 IoT Core Manufacturing Guide before proceeding.</span></span>

### <a name="process-overview"></a><span data-ttu-id="8c353-147">过程概述</span><span class="sxs-lookup"><span data-stu-id="8c353-147">Process overview</span></span>

<span data-ttu-id="8c353-148">与构建 Windows Embedded Compact 映像的过程不同，Windows 10 IoT Core 分离还集成了固件的创建、板支持包、映像定义和应用程序包含。</span><span class="sxs-lookup"><span data-stu-id="8c353-148">Unlike the process of building a Windows Embedded Compact image, Windows 10 IoT Core decouples yet integrates the creation of firmware, board support packages, image definition, and application inclusion.</span></span> <span data-ttu-id="8c353-149">通过利用这些组件的不同技术，你可以将所需的工作划分为不同团队或组织中的个人所需的工作。</span><span class="sxs-lookup"><span data-stu-id="8c353-149">By utilizing different technologies for these pieces, you can separate the work you need to do amongst different teams or individuals in your organization.</span></span>

<span data-ttu-id="8c353-150">创建映像的基本步骤如下：</span><span class="sxs-lookup"><span data-stu-id="8c353-150">The basic steps in creating an image are:</span></span>

1. [<span data-ttu-id="8c353-151">创建工作区</span><span class="sxs-lookup"><span data-stu-id="8c353-151">Create a  workspace</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

2. [<span data-ttu-id="8c353-152"> (BSP) 导入相应的 IoT 核心板支持包 </span><span class="sxs-lookup"><span data-stu-id="8c353-152">Import the appropriate IoT Core Board Support Package  (BSP)</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

3. <span data-ttu-id="8c353-153">导入先前创建的 CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="8c353-153">Import the CE App Container you created previously</span></span>

4. [<span data-ttu-id="8c353-154">创建产品定义</span><span class="sxs-lookup"><span data-stu-id="8c353-154">Create your product  definition</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

5. [<span data-ttu-id="8c353-155">向产品添加功能和应用程序</span><span class="sxs-lookup"><span data-stu-id="8c353-155">Add features and applications to your  product</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

6. [<span data-ttu-id="8c353-156"> (FFU 创建完整的闪存更新) </span><span class="sxs-lookup"><span data-stu-id="8c353-156">Build your Full Flash Update  (FFU)</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

7. [<span data-ttu-id="8c353-157">将 FFU 部署到设备并测试</span><span class="sxs-lookup"><span data-stu-id="8c353-157">Deploy the FFU to the device and  test</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

8. [<span data-ttu-id="8c353-158">完成零售 FFU 并为其签名</span><span class="sxs-lookup"><span data-stu-id="8c353-158">Finalize and sign your retail  FFU</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/build-retail-image)

<span data-ttu-id="8c353-159">在 [Windows 10 IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)中，每个步骤都有详细指南。</span><span class="sxs-lookup"><span data-stu-id="8c353-159">There are detailed guides for each of these steps as part of the [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image).</span></span> <span data-ttu-id="8c353-160">尽管其中一些步骤类似于使用平台生成器 (PB) 创建设备映像的过程，但有必要更深入地探讨一些区域。</span><span class="sxs-lookup"><span data-stu-id="8c353-160">While some of these steps are like the process of using Platform Builder (PB) to create a device image, it is worth exploring some areas more deeply.</span></span>

#### <a name="step-1---create-a-workspace"></a><span data-ttu-id="8c353-161">步骤 1-创建工作区</span><span class="sxs-lookup"><span data-stu-id="8c353-161">Step 1 - Create a Workspace</span></span>

<span data-ttu-id="8c353-162">请查看 IoT 核心制造指南中的文档 " [创建基本图像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)"，了解如何创建工作区。</span><span class="sxs-lookup"><span data-stu-id="8c353-162">Review the documentation, [Create a Basic Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image), in the IoT Core Manufacturing Guide to learn how to create a workspace.</span></span>

#### <a name="step-2---import-the-appropriate-iot-core-board-support-package-bsp"></a><span data-ttu-id="8c353-163">步骤 2-导入适当的 IoT 核心板支持包 (BSP) </span><span class="sxs-lookup"><span data-stu-id="8c353-163">Step 2 - Import the appropriate IoT Core Board Support Package (BSP)</span></span>

<span data-ttu-id="8c353-164">查看 IoT 核心制造指南中的文档 " [创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)"，以获取有关板的支持。</span><span class="sxs-lookup"><span data-stu-id="8c353-164">Review the documentation, [Create a Basic Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image), in the IoT Core Manufacturing Guide for support for your board.</span></span>

#### <a name="step-3---importing-the-windows-ce-app-container"></a><span data-ttu-id="8c353-165">步骤 3-导入 Windows CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="8c353-165">Step 3 - Importing the Windows CE App Container</span></span>

<span data-ttu-id="8c353-166">Windows CE 应用容器使用上图所述的 PB 创建，并使用 [IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-IoTCEPAL.md#Import-IoTCEPAL) 命令导入到 IoT 核心工作区。</span><span class="sxs-lookup"><span data-stu-id="8c353-166">The Windows CE App Container is created using PB as discussed above and imported into your IoT Core workspace by using the [Import-IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-IoTCEPAL.md#Import-IoTCEPAL) command.</span></span> <span data-ttu-id="8c353-167">此命令会将 CE 单层发布目录中所需的内容复制到 IoT ADK 工作区。</span><span class="sxs-lookup"><span data-stu-id="8c353-167">This command will copy the required contents from the CE flat release directory into the IoT ADK workspace.</span></span> <span data-ttu-id="8c353-168">如果多次调用，则会在工作区中的目录下备份以前的状态 `Source-\$Arch\CEPAL.OLD` 。</span><span class="sxs-lookup"><span data-stu-id="8c353-168">If invoked multiple times, the previous state is backed up under the `Source-\$Arch\CEPAL.OLD` directory in the workspace.</span></span>

#### <a name="step-4---create-your-product-definition"></a><span data-ttu-id="8c353-169">步骤 4-创建产品定义</span><span class="sxs-lookup"><span data-stu-id="8c353-169">Step 4 - Create your product definition</span></span>

<span data-ttu-id="8c353-170">请查看 IoT 核心制造指南中的文档， [创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)，创建产品定义。</span><span class="sxs-lookup"><span data-stu-id="8c353-170">Review the documentation, [Create a Basic Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image), in the IoT Core Manufacturing Guide to create your product definition.</span></span>


#### <a name="step-5---adding-ce-app-container-to-a-product"></a><span data-ttu-id="8c353-171">步骤 5-将 CE 应用容器添加到产品</span><span class="sxs-lookup"><span data-stu-id="8c353-171">Step 5 - Adding CE App Container to a product</span></span>

<span data-ttu-id="8c353-172">将 CE 应用容器定义导入到工作区后，需要确保运行 [IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTCEPAL.md#Add-IoTCEPAL) 命令，该命令会将对 CE 应用容器包的引用添加到相关产品 OEMInput.xml 文件 (测试和零售) 。</span><span class="sxs-lookup"><span data-stu-id="8c353-172">Once you have imported your CE App Container definition to your workspace you will need to ensure that you run the [Add-IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTCEPAL.md#Add-IoTCEPAL) command, which will add a reference to CE App Container packages to the relevant product OEMInput.xml files (Test and Retail).</span></span>

<span data-ttu-id="8c353-173">下一步是使用 [IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTProductFeature.md#Add-IoTProductFeature) 命令将 IOT \_ CEPAL 功能添加到 OEMInput.xml。</span><span class="sxs-lookup"><span data-stu-id="8c353-173">The next step is to use the [Add-IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTProductFeature.md#Add-IoTProductFeature) command to add the IOT\_CEPAL feature to the OEMInput.xml.</span></span> <span data-ttu-id="8c353-174">这会将 Windows CE 应用容器的 Windows 主机支持添加 (Windows CE 的前端 UWP 应用 + 支持驱动程序) 到我们的产品定义，并在默认应用组中包含 CE 应用容器。</span><span class="sxs-lookup"><span data-stu-id="8c353-174">This adds the Windows Host support for the Windows CE App Container (Windows CE front-end UWP app + support drivers) to  our product definition and includes the CE App Container in the default Apps group.</span></span> <span data-ttu-id="8c353-175">我们将在后面的部分中讨论启动配置。</span><span class="sxs-lookup"><span data-stu-id="8c353-175">We’ll discuss start-up configuration in a later section.</span></span>

#### <a name="step-6---build-your-cab-files"></a><span data-ttu-id="8c353-176">步骤 6-生成 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="8c353-176">Step 6 - Build your CAB files</span></span>

<span data-ttu-id="8c353-177">这是在创建 FFU 的过程中的一个重要步骤，并且应在每次更改配置、添加/更改应用程序或驱动程序时执行。</span><span class="sxs-lookup"><span data-stu-id="8c353-177">This is an important step during the creation of your FFU and should be done whenever you change a configuration, add/change an application or drivers.</span></span> <span data-ttu-id="8c353-178">将使用 [IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md#New-IoTCabPackage) 和 "All" 选项。</span><span class="sxs-lookup"><span data-stu-id="8c353-178">You will use the [New-IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md#New-IoTCabPackage) with the “All” option.</span></span> <span data-ttu-id="8c353-179">你还可以根据需要构建单一功能，但通常应在生成 FFU 的步骤之前重新生成所有包。</span><span class="sxs-lookup"><span data-stu-id="8c353-179">You can also build Single features as needed but in general you should rebuild all the packages prior to the step of building your FFU as best practice.</span></span>

#### <a name="step-7---deploying-your-ffu-to-your-device"></a><span data-ttu-id="8c353-180">步骤 7-将 FFU 部署到设备</span><span class="sxs-lookup"><span data-stu-id="8c353-180">Step 7 - Deploying your FFU to your device</span></span>

<span data-ttu-id="8c353-181">构建映像后，可以将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="8c353-181">Once the image is built, you can deploy it to a device.</span></span> <span data-ttu-id="8c353-182">这可以通过使用 [DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/what-is-dism)的命令行通过特定于设备的部署过程或通过使用 [Windows 10 IoT 核心仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)来完成。</span><span class="sxs-lookup"><span data-stu-id="8c353-182">This can be done from the command line using [DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/what-is-dism), via your device-specific deployment process or by using the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="8c353-183">有关更多详细信息，请访问 [Windows 10 IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)。</span><span class="sxs-lookup"><span data-stu-id="8c353-183">More details are available as part of the [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image).</span></span>

##### <a name="deploying-the-windows-ce-app-container-to-a-device-when-using-an-existing-ffu"></a><span data-ttu-id="8c353-184">使用现有 FFU 将 Windows CE 应用容器部署到设备</span><span class="sxs-lookup"><span data-stu-id="8c353-184">Deploying the Windows CE App Container to a device when using an existing FFU</span></span>

<span data-ttu-id="8c353-185">CE Cab 是 IoT Core 上的可部署包。</span><span class="sxs-lookup"><span data-stu-id="8c353-185">The CE CABs are deployable packages on IoT Core.</span></span> <span data-ttu-id="8c353-186">如果存在现有的 IoT 核心映像，可以使用命令将这些 Cab 部署到设备 `APPLYUPDATE` 。</span><span class="sxs-lookup"><span data-stu-id="8c353-186">If there is an existing IoT Core image, these CABs can be deployed to the device using the `APPLYUPDATE` command.</span></span> <span data-ttu-id="8c353-187">首先将 Cab 复制到设备，然后通过暂存并提交 Cab `APPLYUPDATE` 。</span><span class="sxs-lookup"><span data-stu-id="8c353-187">First copy the CABs to the device, then stage and commit the CABs with `APPLYUPDATE`.</span></span> <span data-ttu-id="8c353-188">请注意，更新此方法会使包版本控制更为强大，因此，如果要将包的更新版本部署到设备，则这些版本的版本号必须更高。</span><span class="sxs-lookup"><span data-stu-id="8c353-188">Do note that updating this way respects package versioning, so if updated versions of packages are to be deployed to the device, they must have a greater version number.</span></span> <span data-ttu-id="8c353-189"> (参阅 IoT ADK 环境) 中的 IoTCabVersion 命令。</span><span class="sxs-lookup"><span data-stu-id="8c353-189">(See the Set-IoTCabVersion command in the IoT ADK environment).</span></span> <span data-ttu-id="8c353-190">有关此方面的详细信息，请参阅 [创建和安装包](https://docs.microsoft.com/enus/windows-hardware/manufacture/iot/create-install-package.)</span><span class="sxs-lookup"><span data-stu-id="8c353-190">More information on this can be found in [Create and Install Packages](https://docs.microsoft.com/enus/windows-hardware/manufacture/iot/create-install-package.)</span></span>

#### <a name="step-8---building-a-retail-image"></a><span data-ttu-id="8c353-191">步骤 8-构建零售映像</span><span class="sxs-lookup"><span data-stu-id="8c353-191">Step 8 - Building a retail image</span></span>

<span data-ttu-id="8c353-192">使用正确的签名映像是保护和更新设备的重要部分。</span><span class="sxs-lookup"><span data-stu-id="8c353-192">Having a properly signed image is an important part of securing and updating a device.</span></span> <span data-ttu-id="8c353-193">对于 Windows 10 IoT Core，此外观显示为测试签名版本和零售签名版本之间的差异。</span><span class="sxs-lookup"><span data-stu-id="8c353-193">For Windows 10 IoT Core, this appears as the difference between Test signed and Retail signed builds.</span></span> <span data-ttu-id="8c353-194">绝不应公开部署测试已签名映像。</span><span class="sxs-lookup"><span data-stu-id="8c353-194">You should never publicly deploy a test signed image.</span></span> <span data-ttu-id="8c353-195">测试签名映像只应用于调试目的，在创建最终零售签名映像之前，应更正任何错误或配置更改。</span><span class="sxs-lookup"><span data-stu-id="8c353-195">Test signed images should only be used for debug purposes and you should correct any errors or configuration changes prior to creating your final retail signed image.</span></span>

> [!NOTE]
> <span data-ttu-id="8c353-196">除了计算机上安装的开发和部署工具外，还需要以下内容来启用零售签名：</span><span class="sxs-lookup"><span data-stu-id="8c353-196">In addition to the development and deployment tools installed on your machine you will also need the following to enable retail signing:</span></span>
>
> - <span data-ttu-id="8c353-197">零售代码签名证书</span><span class="sxs-lookup"><span data-stu-id="8c353-197">A retail code-signing certificate</span></span>
> - <span data-ttu-id="8c353-198">交叉签名证书</span><span class="sxs-lookup"><span data-stu-id="8c353-198">A cross-signing certificate</span></span>

### <a name="properly-signing-and-including-your-applications"></a><span data-ttu-id="8c353-199">正确签名和包括应用程序</span><span class="sxs-lookup"><span data-stu-id="8c353-199">Properly signing and including your applications</span></span>

<span data-ttu-id="8c353-200">如果你有一个或多个你想要包含在 Windows 10 IoT 核心零售映像中的自定义应用程序，则需要验证这些应用程序是否已在零售映像中包含它们时进行了正确签名。</span><span class="sxs-lookup"><span data-stu-id="8c353-200">If you have one or more custom applications that you want to include in your Windows 10 IoT Core retail image, you need to verify that these applications are signed properly when including them in your retail image.</span></span>

## <a name="additional-information"></a><span data-ttu-id="8c353-201">其他信息</span><span class="sxs-lookup"><span data-stu-id="8c353-201">Additional Information</span></span>

### <a name="adding-new-applications-to-an-existing-image"></a><span data-ttu-id="8c353-202">将新应用程序添加到现有映像</span><span class="sxs-lookup"><span data-stu-id="8c353-202">Adding new applications to an existing image</span></span>

<span data-ttu-id="8c353-203">若要将新应用程序添加到现有的操作系统设计中，可以将该项目作为子项目添加到 OS 设计项目，也可以创建常规部署 CAB 包，将这些包部署到作为初始设备设置的一部分的设备上。</span><span class="sxs-lookup"><span data-stu-id="8c353-203">To add a new application to an existing OS Design you can either add the project as a sub-project to the OS Design Project or you can create normal deployment CAB packages to deploy those to the device as part of the initial device setup.</span></span>

### <a name="packaging-best-practices"></a><span data-ttu-id="8c353-204">打包最佳实践</span><span class="sxs-lookup"><span data-stu-id="8c353-204">Packaging Best Practices</span></span>

<span data-ttu-id="8c353-205">应始终确保包尽可能细化，以减少更新时间。</span><span class="sxs-lookup"><span data-stu-id="8c353-205">You should always aim to make sure packages are as granular as possible to reduce update time.</span></span>

<span data-ttu-id="8c353-206">由于包是更新的最小单位，因此请确保每个包尽可能小。</span><span class="sxs-lookup"><span data-stu-id="8c353-206">Since a package is the smallest unit of updating, make sure that each package is as small as possible.</span></span> <span data-ttu-id="8c353-207">在平台生成器中生成时，根据选手文件自动将生成的包与内存部分和模块/文件类型分隔开来。</span><span class="sxs-lookup"><span data-stu-id="8c353-207">When building in Platform Builder, the generated packages are separated according to memory section and module/file type according to the bib file automatically.</span></span>

- <span data-ttu-id="8c353-208">对于在平台生成器中构建并通过 OSDesign 进行打包的自定义资产，请考虑将自定义资产添加到选手 (不在 NK) 中的单独内存部分，以便自定义代码更新与 CE OS 的更新不同。</span><span class="sxs-lookup"><span data-stu-id="8c353-208">For custom assets built in Platform Builder and packaged through OSDesign.bib, consider adding custom assets into a separate memory section in the BIB (not in NK), so that updates to custom code can ship separate from updates to the CE OS.</span></span>

- <span data-ttu-id="8c353-209">对于通过 IoT ADK 打包命令添加的自定义资产：请确保创建的包尽可能小。</span><span class="sxs-lookup"><span data-stu-id="8c353-209">For custom assets added through the IoT ADK packaging commands: Make sure the packages created are as small as possible.</span></span>

### <a name="adding-other-things-to-the-platform-builder-package"></a><span data-ttu-id="8c353-210">向平台生成器包添加其他项</span><span class="sxs-lookup"><span data-stu-id="8c353-210">Adding other things to the Platform Builder package</span></span>

<span data-ttu-id="8c353-211">通常，建议不要修改平台生成器生成的生成的包，以将其他组件包括到系统映像中。</span><span class="sxs-lookup"><span data-stu-id="8c353-211">In general, the recommendation is not to modify the resulting package produced by Platform Builder to include additional components into the system image.</span></span> <span data-ttu-id="8c353-212">而应按照 [Windows 10 IoT Core 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)进行操作。</span><span class="sxs-lookup"><span data-stu-id="8c353-212">Instead, follow the [Windows 10 IoT Core manufacturing guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="8c353-213">但是，如果必须将文件添加到平台生成器创建的包中，请按照现有过程进行操作。</span><span class="sxs-lookup"><span data-stu-id="8c353-213">However, if files must be added to the package that is created by Platform Builder, follow your existing process.</span></span> <span data-ttu-id="8c353-214">向 PB 生成的包添加内容时，请考虑以下事项：</span><span class="sxs-lookup"><span data-stu-id="8c353-214">When adding content to the package generated by PB, consider the following:</span></span>

- <span data-ttu-id="8c353-215">包的最大大小 (大约 400 MB) ，超过此大小将阻止更新。</span><span class="sxs-lookup"><span data-stu-id="8c353-215">There is a maximum size for packages (about 400 MB) and exceeding this size will prevent updating.</span></span>

- <span data-ttu-id="8c353-216">更新会在包粒度进行。</span><span class="sxs-lookup"><span data-stu-id="8c353-216">Updates happen on package granularity.</span></span> <span data-ttu-id="8c353-217">如果需要更新包中的单个资产，则该程序包的所有资产将同时更新。</span><span class="sxs-lookup"><span data-stu-id="8c353-217">If a single asset in the package needs to be updated, then all the assets of that package will be updated at the same time.</span></span> <span data-ttu-id="8c353-218">若要减少更新的大小，请将内容隔离到单独的包中，以最大程度地减少总体更新大小。</span><span class="sxs-lookup"><span data-stu-id="8c353-218">To reduce the size of updates, isolate content into separate packages to minimize the overall update size.</span></span>

### <a name="adding-additional-files-through-platform-builder"></a><span data-ttu-id="8c353-219">通过平台生成器添加其他文件</span><span class="sxs-lookup"><span data-stu-id="8c353-219">Adding additional files through Platform Builder</span></span>

<span data-ttu-id="8c353-220">上面详述的打包过程由与构建 CE 箱文件相同的输入驱动。</span><span class="sxs-lookup"><span data-stu-id="8c353-220">The packaging process detailed above is driven by the same inputs that go into building a CE BIN file.</span></span> <span data-ttu-id="8c353-221">因此，如果在 OSDesign 中引用了文件，则会将选手中的注册表项添加到 OSDesign 中， `MAKEIMG` 进程将在生成的 CAB 文件中包含这些文件。</span><span class="sxs-lookup"><span data-stu-id="8c353-221">So, if the files are referenced in OSDesign.bib and registry entries are added to OSDesign.reg, the `MAKEIMG` process will include these files in the resulting CAB file.</span></span> <span data-ttu-id="8c353-222">在此过程中， `MAKEIMG` 将立即执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8c353-222">During this process `MAKEIMG` will now:</span></span>

1. <span data-ttu-id="8c353-223">`ROMIMAGE` 将在平面发布目录中创建一个名为的目录 `CEPAL\_PKG` (FRD) ，该目录将 Windows CE 的目录结构暂存用于 CEPAL。</span><span class="sxs-lookup"><span data-stu-id="8c353-223">`ROMIMAGE` will create a directory named `CEPAL\_PKG` within the Flat Release Directory (FRD) that stages an installed directory structure for Windows CE for CEPAL.</span></span>

2. <span data-ttu-id="8c353-224">`ROMIMAGE` 列出基于 CE 选手文件放入的所有 CE 文件的清单 `CEPAL\_PKG` 。</span><span class="sxs-lookup"><span data-stu-id="8c353-224">`ROMIMAGE` inventories all CE files that were placed into `CEPAL\_PKG` based on CE BIB files.</span></span>

3. <span data-ttu-id="8c353-225">`ROMIMAGE` 将为每个内存部分创建多个 WM.XML 文件。</span><span class="sxs-lookup"><span data-stu-id="8c353-225">`ROMIMAGE` will create multiple WM.XML files for each memory section.</span></span> <span data-ttu-id="8c353-226">这样做的目的是为了使更新以更精细的方式推送，因为更新的最小单位是包。</span><span class="sxs-lookup"><span data-stu-id="8c353-226">This is done so that updates can be pushed in a more granular fashion as the minimum unit of update is a package.</span></span>

4. <span data-ttu-id="8c353-227">`ROMIMAGE` 将创建 `CEPALFM.xml` 引用所有已创建的包的。</span><span class="sxs-lookup"><span data-stu-id="8c353-227">`ROMIMAGE` will create `CEPALFM.xml` which references all the created packages.</span></span>

<span data-ttu-id="8c353-228">所有创建的包都将使用固定的前缀命名 `“%OEM\_NAME%.WindowsCE.\*”` ，其中， `%OEM\_NAME%` 将在调用 [IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md)时在 IoT Core 创建过程中填充。</span><span class="sxs-lookup"><span data-stu-id="8c353-228">All of the packages created will be named with a fixed prefix of `“%OEM\_NAME%.WindowsCE.\*”`, where `%OEM\_NAME%` is populated during the IoT Core creation process when calling [New-IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md).</span></span> <span data-ttu-id="8c353-229">命名空间中的包名称是从选手文件的内存部分派生的 (例如，NK) 后跟模块/文件 (也由选手文件) 决定。</span><span class="sxs-lookup"><span data-stu-id="8c353-229">The Package Name within the name space is derived from the memory section in the BIB file (e.g. NK) followed by modules / files (also determined by the BIB file).</span></span>

#### <a name="communicating-between-windows-embedded-compact-2013-and-windows-10-iot-core-applications"></a><span data-ttu-id="8c353-230">Windows Embedded Compact 2013 和 Windows 10 IoT Core 应用程序之间的通信</span><span class="sxs-lookup"><span data-stu-id="8c353-230">Communicating between Windows Embedded Compact 2013 and Windows 10 IoT Core applications</span></span>

<span data-ttu-id="8c353-231">在 CE 容器中运行的应用程序之间进行通信的建议方法是使用本地环回。</span><span class="sxs-lookup"><span data-stu-id="8c353-231">The recommended approach to communicate between applications running in the CE Container is to use Local Loopback.</span></span> <span data-ttu-id="8c353-232">有关详细信息，请参阅 [本文档中的本地环回。](https://docs.microsoft.com/windows/iot-core/develop-your-app/loopback)</span><span class="sxs-lookup"><span data-stu-id="8c353-232">You can read more on [Local Loopback in this document.](https://docs.microsoft.com/windows/iot-core/develop-your-app/loopback)</span></span>

### <a name="automatically-starting-the-ce-app-container-application"></a><span data-ttu-id="8c353-233">自动启动 CE 应用容器应用程序</span><span class="sxs-lookup"><span data-stu-id="8c353-233">Automatically starting the CE App Container application</span></span>

<span data-ttu-id="8c353-234">若要自动启动 CE 容器应用程序，可以创建一个设置 [包](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image) ，将启动应用程序设置为 "CEPAL. DkMonUWP \_ cw5n1h2txyewy！应用 "，并将其包含在映像中。</span><span class="sxs-lookup"><span data-stu-id="8c353-234">To automatically start the CE Container application, you can create a [Provisioning Package](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image) that sets the startup application to “Microsoft.Windows.IoT.CEPAL.DkMonUWP\_cw5n1h2txyewy!App”, and included this provisioning package in the image.</span></span> <span data-ttu-id="8c353-235">还需要使用 [IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Remove-IoTProductFeature.md) 命令删除默认启动应用程序，并 \_ 从 iot 核心产品定义中删除 IOT BERTHA 功能 ID。</span><span class="sxs-lookup"><span data-stu-id="8c353-235">You will also need to remove the default startup application by using the [Remove-IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Remove-IoTProductFeature.md) command and removing the IOT\_BERTHA Feature ID from the IoT Core product definition.</span></span>

### <a name="available-configuration-settings-for-the-windows-ce-app-container"></a><span data-ttu-id="8c353-236">Windows CE 应用容器的可用配置设置</span><span class="sxs-lookup"><span data-stu-id="8c353-236">Available Configuration settings for the Windows CE App Container</span></span>

#### <a name="registry-based-configuration-in-ce"></a><span data-ttu-id="8c353-237">CE 中基于注册表的配置</span><span class="sxs-lookup"><span data-stu-id="8c353-237">Registry-based configuration in CE</span></span>

##### <a name="non-executable-stack-by-default"></a><span data-ttu-id="8c353-238">默认情况下，不可执行的堆栈</span><span class="sxs-lookup"><span data-stu-id="8c353-238">Non-Executable Stack by Default</span></span>

<span data-ttu-id="8c353-239">默认情况下，Windows CE 应用容器已禁用可执行堆栈页，以提高安全性。</span><span class="sxs-lookup"><span data-stu-id="8c353-239">The Windows CE App Container has disabled executable stack pages by default to improve security.</span></span> <span data-ttu-id="8c353-240">但是，某些旧版应用程序可能依赖于此行为才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="8c353-240">However, some legacy applications may rely on this behavior to run correctly.</span></span> <span data-ttu-id="8c353-241">若要启用可执行堆栈，请在 CE 映像中设置以下注册表值 (建议在平台生成器中将其放入 OSDesign) </span><span class="sxs-lookup"><span data-stu-id="8c353-241">To Enable an Executable Stack, set the following registry value in the CE image (It is recommended that this goes into OSDesign.reg in Platform Builder)</span></span>

```AsciiDoc
KeyPath = HKEY\_LOCAL\_MACHINE\CEPAL
ValueName = MemoryOptions Type = REG\_DWORD
Value = 1
```

##### <a name="16-bit-565-override-for-gwes"></a><span data-ttu-id="8c353-242">16位565替代 GWES</span><span class="sxs-lookup"><span data-stu-id="8c353-242">16-bit 565 Override for GWES</span></span>

<span data-ttu-id="8c353-243">如果 Windows CE 应用容器配置了32位显示，则 GWES 完成了16位到32位的 RGB 转换，假设16位 RGB 像素数据采用 RGB555 格式。</span><span class="sxs-lookup"><span data-stu-id="8c353-243">If the Windows CE App Container is configured with a 32-bit display, then 16-bit to 32-bit RGB conversions are done by GWES are done with the assumption that 16-bit RGB pixel data is in RGB555 format.</span></span> <span data-ttu-id="8c353-244">如果位图资源采用16位565，并且无法转换为 RGB555 的这些资源，则可以通过注册表项更改 GWES 的默认转换行为。</span><span class="sxs-lookup"><span data-stu-id="8c353-244">If bitmap resources are in 16-bit 565, and conversion to a RGB555 of these resources is not possible, GWES’s default conversion behavior can be changed via a registry key.</span></span> <span data-ttu-id="8c353-245">创建以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="8c353-245">Create the following registry key:</span></span>

```AsciiDoc
HKEY\_LOCAL\_MACHINE\SYSTEM\GDI\16bpp565RGBPalette.
```

#### <a name="registry-based-configuration-in-host-iot-core"></a><span data-ttu-id="8c353-246">Host 中基于注册表的配置 (IoT 核心) </span><span class="sxs-lookup"><span data-stu-id="8c353-246">Registry-based configuration in Host (IoT Core)</span></span>

##### <a name="configuring-serial-ports-for-the-windows-ce-app-container"></a><span data-ttu-id="8c353-247">为 Windows CE 应用容器配置串行端口</span><span class="sxs-lookup"><span data-stu-id="8c353-247">Configuring serial ports for the Windows CE App Container</span></span>

<span data-ttu-id="8c353-248">需要将主机串行端口映射到 CE 环境。</span><span class="sxs-lookup"><span data-stu-id="8c353-248">Host Serial ports need to be mapped into the CE environment.</span></span> <span data-ttu-id="8c353-249">此映射存在于 IoT 核心的注册表中，需要由映像创建者进行配置。</span><span class="sxs-lookup"><span data-stu-id="8c353-249">This mapping exists in registry in IoT Core and needs to be configured by the image creator.</span></span>

<span data-ttu-id="8c353-250">在 `HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial` 中，存在使用以下架构将来宾 COM 端口映射到主机 COM 端口的配置条目。</span><span class="sxs-lookup"><span data-stu-id="8c353-250">Under `HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial`, configuration entries exist to map Guest COM ports to Host COM ports using the following schema.</span></span>

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

<span data-ttu-id="8c353-251">如果上面的注册表路径在启动 CE 时不存在，则将根据系统上发现的串行设备来写入默认配置。</span><span class="sxs-lookup"><span data-stu-id="8c353-251">If the registry path above does not exist when CE is booted, a default configuration will be written based on discovered serial devices on the system.</span></span>

#### <a name="file-based-configuration-in-host"></a><span data-ttu-id="8c353-252">主机中基于文件的配置</span><span class="sxs-lookup"><span data-stu-id="8c353-252">File Based configuration in Host</span></span>

<span data-ttu-id="8c353-253">可以使用主机上的本地文件配置 CE 容器 `C:\WindowsCE\CEEnvConfig.json` 。</span><span class="sxs-lookup"><span data-stu-id="8c353-253">The CE Container can be configured using a local file on the host `C:\WindowsCE\CEEnvConfig.json`.</span></span> <span data-ttu-id="8c353-254">下面是此配置文件的示例：</span><span class="sxs-lookup"><span data-stu-id="8c353-254">Here is a sample of this configuration file:</span></span>

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

#### <a name="oemoptions"></a><span data-ttu-id="8c353-255">OEMOptions</span><span class="sxs-lookup"><span data-stu-id="8c353-255">OEMOptions</span></span>

| <span data-ttu-id="8c353-256">键</span><span class="sxs-lookup"><span data-stu-id="8c353-256">Key</span></span>           | <span data-ttu-id="8c353-257">说明</span><span class="sxs-lookup"><span data-stu-id="8c353-257">Description</span></span>                                                                                                            |
|---------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8c353-258">GUI</span><span class="sxs-lookup"><span data-stu-id="8c353-258">GUI</span></span>           | <span data-ttu-id="8c353-259">启动带有 UI (默认为 true) 的 CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="8c353-259">Launch the CE app container with UI (default true)</span></span>                                                                     |
| <span data-ttu-id="8c353-260">宽度</span><span class="sxs-lookup"><span data-stu-id="8c353-260">Width</span></span>         | <span data-ttu-id="8c353-261">CE 应用容器的宽度显示 (默认 1024) </span><span class="sxs-lookup"><span data-stu-id="8c353-261">Width of the CE app container display (default 1024)</span></span>                                                                   |
| <span data-ttu-id="8c353-262">高度</span><span class="sxs-lookup"><span data-stu-id="8c353-262">Height</span></span>        | <span data-ttu-id="8c353-263">CE 应用容器的高度显示 (默认 768) </span><span class="sxs-lookup"><span data-stu-id="8c353-263">Height of the CE app container display (default 768)</span></span>                                                                   |
| <span data-ttu-id="8c353-264">FillScreen</span><span class="sxs-lookup"><span data-stu-id="8c353-264">FillScreen</span></span>    |                                                                                                                        |
| <span data-ttu-id="8c353-265">ColorDepth</span><span class="sxs-lookup"><span data-stu-id="8c353-265">ColorDepth</span></span>    | <span data-ttu-id="8c353-266">设置默认的每像素 (默认位数 32) </span><span class="sxs-lookup"><span data-stu-id="8c353-266">Sets default bits per pixel (default 32)</span></span>                                                                               |
| <span data-ttu-id="8c353-267">RefreshRate</span><span class="sxs-lookup"><span data-stu-id="8c353-267">RefreshRate</span></span>   | <span data-ttu-id="8c353-268">每秒重绘显示的次数</span><span class="sxs-lookup"><span data-stu-id="8c353-268">How many times the display is redrawn per second</span></span>                                                                       |
| <span data-ttu-id="8c353-269">noAslrSupport</span><span class="sxs-lookup"><span data-stu-id="8c353-269">noAslrSupport</span></span> | <span data-ttu-id="8c353-270">在 CE 应用容器中禁用地址空间布局随机化 (默认值为 true) </span><span class="sxs-lookup"><span data-stu-id="8c353-270">Disables address space layout randomization in the CE app container (default true)</span></span>                                     |
| <span data-ttu-id="8c353-271">OEMConfigApp</span><span class="sxs-lookup"><span data-stu-id="8c353-271">OEMConfigApp</span></span>  | <span data-ttu-id="8c353-272">应为配置启动的 OEM 提供的应用的包系列名称。</span><span class="sxs-lookup"><span data-stu-id="8c353-272">Package Family Name of an OEM provided app that should be launched for configuration.</span></span>                                  |
| <span data-ttu-id="8c353-273">OEMConfigFile</span><span class="sxs-lookup"><span data-stu-id="8c353-273">OEMConfigFile</span></span> | <span data-ttu-id="8c353-274">文件的路径，该文件包含 OEMConfigApp 与 CE 应用容器之间共享的其他配置选项</span><span class="sxs-lookup"><span data-stu-id="8c353-274">Path to a file that contains additional configuration options shared between the OEMConfigApp and the CE app container</span></span> |

<span data-ttu-id="8c353-275">CE 应用容器只会使一个网络接口可供使用。</span><span class="sxs-lookup"><span data-stu-id="8c353-275">The CE app container only makes one network interface available for use.</span></span> <span data-ttu-id="8c353-276">如果主机系统中有多个 Nic，则必须在主机注册表中选择一个接口，以确保所选 NIC 是确定性的。</span><span class="sxs-lookup"><span data-stu-id="8c353-276">If multiple NICs are present in the Host System, one interface must be selected in the Host Registry to ensure the selected NIC is deterministic.</span></span>

##### <a name="oemconfigfile"></a><span data-ttu-id="8c353-277">OEMConfigFile</span><span class="sxs-lookup"><span data-stu-id="8c353-277">OEMConfigFile</span></span>

<span data-ttu-id="8c353-278">OEMConfigFile 在中指定 `C:\WindowsCE\CEEnvConfig.json` 。</span><span class="sxs-lookup"><span data-stu-id="8c353-278">The OEMConfigFile is specified in `C:\WindowsCE\CEEnvConfig.json`.</span></span> <span data-ttu-id="8c353-279">请确保此文件可由 UWP 应用程序读取。</span><span class="sxs-lookup"><span data-stu-id="8c353-279">Make sure this file can be read by a UWP application.</span></span> <span data-ttu-id="8c353-280">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="8c353-280">The following is a sample:</span></span>

```xml
{
   “FactoryReset”: false, “PlatformBuilderDebugMode”: false,
   “NetInterface”: “Some Network Profile Id”
}
```

<span data-ttu-id="8c353-281">选项：</span><span class="sxs-lookup"><span data-stu-id="8c353-281">Options:</span></span>

| <span data-ttu-id="8c353-282">键</span><span class="sxs-lookup"><span data-stu-id="8c353-282">Key</span></span>                      | <span data-ttu-id="8c353-283">说明</span><span class="sxs-lookup"><span data-stu-id="8c353-283">Description</span></span>                                                                              |
|--------------------------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="8c353-284">FactoryReset</span><span class="sxs-lookup"><span data-stu-id="8c353-284">FactoryReset</span></span>             | <span data-ttu-id="8c353-285">由 config 应用用来指示 CE 应用容器转储持久状态。</span><span class="sxs-lookup"><span data-stu-id="8c353-285">Used by the config app to signal the CE App Container to dump persistent state.</span></span>          |
| <span data-ttu-id="8c353-286">PlatformBuilderDebugMode</span><span class="sxs-lookup"><span data-stu-id="8c353-286">PlatformBuilderDebugMode</span></span> | <span data-ttu-id="8c353-287">用于使用支持使用平台生成器进行调试的 KITL 支持启动 CE 应用程序容器。</span><span class="sxs-lookup"><span data-stu-id="8c353-287">Used to boot the CE App Container with KITL support for debugging with Platform Builder.</span></span> |
| <span data-ttu-id="8c353-288">NetInterface</span><span class="sxs-lookup"><span data-stu-id="8c353-288">NetInterface</span></span>             | <span data-ttu-id="8c353-289">基于配置文件名称为 CE 选择一个网络接口。</span><span class="sxs-lookup"><span data-stu-id="8c353-289">Select a Network Interface for CE based on profile name.</span></span>                                 |


## <a name="references"></a><span data-ttu-id="8c353-290">参考</span><span class="sxs-lookup"><span data-stu-id="8c353-290">References</span></span>

- [<span data-ttu-id="8c353-291">获取自定义 Windows 10 IoT Core 所需的工具</span><span class="sxs-lookup"><span data-stu-id="8c353-291">Get the tools needed to customize Windows 10 IoT Core</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)
- [<span data-ttu-id="8c353-292">IoT 核心板支持的包 (BSP) </span><span class="sxs-lookup"><span data-stu-id="8c353-292">IoT Core Board Supported Packages (BSP)</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/bsphardware)
- [<span data-ttu-id="8c353-293">IoT 核心制造指南</span><span class="sxs-lookup"><span data-stu-id="8c353-293">IoT Core Manufacturing Guide</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)
- [<span data-ttu-id="8c353-294">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="8c353-294">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)
- [<span data-ttu-id="8c353-295">创建和安装包</span><span class="sxs-lookup"><span data-stu-id="8c353-295">Create and Install Packages</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-install-package)
