---
title: Windows CE 应用容器入门
ms.date: 08/25/2020
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows CE 应用容器迁移入门指南
keywords: Windows 10 IoT 核心版，Windows CE，应用程序迁移，cepal
ms.openlocfilehash: 6e1fb421df4ecb26099a08c489c4c6eeca0a392e
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230414"
---
# <a name="getting-started-with-windows-ce-app-container"></a><span data-ttu-id="57e07-104">Windows CE 应用容器入门</span><span class="sxs-lookup"><span data-stu-id="57e07-104">Getting Started with Windows CE App Container</span></span>

<span data-ttu-id="57e07-105">Windows CE 应用容器是一种技术，允许大多数 CE 应用程序在 Windows 10 IoT 核心版之上运行。</span><span class="sxs-lookup"><span data-stu-id="57e07-105">The Windows CE App Container is a technology that allows most CE applications to run on top of Windows 10 IoT Core.</span></span>

<span data-ttu-id="57e07-106">此解决方案分为两个阶段。</span><span class="sxs-lookup"><span data-stu-id="57e07-106">The solution is built in two stages.</span></span> <span data-ttu-id="57e07-107">第一阶段使用适用于 x86 或 ARM32 体系结构的 BSP 创建 Windows CE 2013 映像。</span><span class="sxs-lookup"><span data-stu-id="57e07-107">The first stage creates a Windows CE 2013 image using a BSP for either x86 or ARM32 architecture.</span></span> <span data-ttu-id="57e07-108">然后，在第二阶段中，此映像包含在一个 Windows 10 IoT 核心版映像中，该映像利用 x64 或 ARM32 BSP 来实现将安装解决方案的特定设备硬件。</span><span class="sxs-lookup"><span data-stu-id="57e07-108">Then in the second stage, this image is included in a Windows 10 IoT Core image that utilizes the x64 or ARM32 BSP for the specific device hardware where the solution will be installed.</span></span>

![CE 应用容器体系结构](.//media/WindowsCEAppContainer/image1.png)

<span data-ttu-id="57e07-110">有关此体系结构的详细信息，请查看以下视频：[现代化 Windows CE 设备](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices)。</span><span class="sxs-lookup"><span data-stu-id="57e07-110">For more information about this architecture, please review this video: [Modernizing Windows CE Devices](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57e07-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="57e07-111">Prerequisites</span></span>
<span data-ttu-id="57e07-112">Windows CE 应用容器软件需要[从6月2020或更高版本) 的 Windows Compact 2013 (内部版本号 6294](https://support.microsoft.com/help/4566035/update-for-windows-embedded-compact-2013)的更新版本，以及[x64 和 ARM32 的更新 Windows 10 IoT 核心版包 (8 月2020更新或更高版本) ](https://support.microsoft.com/help/4565349/windows-10-update-kb4565349)。</span><span class="sxs-lookup"><span data-stu-id="57e07-112">The Windows CE App Container software requires an updated version of [Windows Compact 2013 (Build number 6294 from June 2020 or later)](https://support.microsoft.com/help/4566035/update-for-windows-embedded-compact-2013) along with updated [Windows 10 IoT Core Packages for x64 and ARM32 (August 2020 update or later)](https://support.microsoft.com/help/4565349/windows-10-update-kb4565349).</span></span> <span data-ttu-id="57e07-113">若要获取 Windows 10 IoT 核心版的最新包，请联系你的 Microsoft 分发服务器。</span><span class="sxs-lookup"><span data-stu-id="57e07-113">To obtain the latest packages for Windows 10 IoT Core, please contact your Microsoft distributor.</span></span>

> [!NOTE]
> <span data-ttu-id="57e07-114">你必须具有有效的 [IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) 订阅才能分发采用 CE 应用容器技术的设备。</span><span class="sxs-lookup"><span data-stu-id="57e07-114">You must have a valid [IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) subscription to distribute a device that employs the CE App Container technology.</span></span>

<span data-ttu-id="57e07-115">此外，你将需要以下各项：</span><span class="sxs-lookup"><span data-stu-id="57e07-115">Additionally, you will need the following:</span></span>

- <span data-ttu-id="57e07-116">[Microsoft Visual Studio 2013 Professional 或 Visual Studio 2015 Professional](<https://visualstudio.microsoft.com/vs/>)。</span><span class="sxs-lookup"><span data-stu-id="57e07-116">[Microsoft Visual Studio 2013 Professional or Visual Studio 2015 Professional](<https://visualstudio.microsoft.com/vs/>).</span></span> <span data-ttu-id="57e07-117">这些版本是应用程序生成器和平台生成器工具所必需的。</span><span class="sxs-lookup"><span data-stu-id="57e07-117">These versions are required for both the Application Builder and Platform Builder tools.</span></span>

- [<span data-ttu-id="57e07-118">适用于 Windows Embedded Compact 2013 的应用程序生成器</span><span class="sxs-lookup"><span data-stu-id="57e07-118">Application Builder for Windows Embedded Compact 2013</span></span>](<https://www.microsoft.com/download/details.aspx?id=38819>)

- <span data-ttu-id="57e07-119">适用于 Windows Compact 2013 的平台生成器</span><span class="sxs-lookup"><span data-stu-id="57e07-119">Platform Builder for Windows Compact 2013</span></span>

- <span data-ttu-id="57e07-120">工作 IoT 核心 BSP</span><span class="sxs-lookup"><span data-stu-id="57e07-120">A Working IoT Core BSP</span></span>

- <span data-ttu-id="57e07-121">[Windows IoT 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)中引用的工具</span><span class="sxs-lookup"><span data-stu-id="57e07-121">The tools referenced in the [Windows IoT Manufacturing   Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)</span></span>
- <span data-ttu-id="57e07-122">请记得安装已更新的组件来代替本指南中所述的组件 (Windows 10 ADK 和 Windows 10 ADK PE 加载项、IoT Core ADK 外接程序、Windows 10 IoT 核心版仪表板) </span><span class="sxs-lookup"><span data-stu-id="57e07-122">Remember to install the updated components in place of the ones referenced in this guide (Windows 10 ADK and Windows 10 ADK PE Add-on, IoT Core ADK Add-ons, Windows 10 IoT Core Dashboard)</span></span>


## <a name="configuring-building-and-packaging-ce-for-the-windows-ce-app-container"></a><span data-ttu-id="57e07-123">为 Windows CE 应用容器配置、构建和打包 CE</span><span class="sxs-lookup"><span data-stu-id="57e07-123">Configuring, Building, and Packaging CE for the Windows CE App Container</span></span>

<span data-ttu-id="57e07-124">[用于创建 Windows 嵌入 Compact 2013 映像的过程](https://docs.microsoft.com/previous-versions/windows/embedded/jj200349(v=winembedded.80))没有明显更新。</span><span class="sxs-lookup"><span data-stu-id="57e07-124">The [process for creating a Windows Embedded Compact 2013 image](https://docs.microsoft.com/previous-versions/windows/embedded/jj200349(v=winembedded.80)) has not been updated significantly.</span></span> <span data-ttu-id="57e07-125">生成映像的一般过程如下：</span><span class="sxs-lookup"><span data-stu-id="57e07-125">The general process for building an image is:</span></span>

1. <span data-ttu-id="57e07-126">在平台生成器中创建 OS 设计项目</span><span class="sxs-lookup"><span data-stu-id="57e07-126">Create OS Design project with Platform Builder</span></span>

2. <span data-ttu-id="57e07-127">选择 "平台生成器" 支持包 (BSP) </span><span class="sxs-lookup"><span data-stu-id="57e07-127">Select the Platform Builder Board Support Package (BSP)</span></span>

3. <span data-ttu-id="57e07-128">选择适当的设计模板</span><span class="sxs-lookup"><span data-stu-id="57e07-128">Choose the appropriate design template</span></span>

4. <span data-ttu-id="57e07-129">配置设计模板提供的选项</span><span class="sxs-lookup"><span data-stu-id="57e07-129">Configure the options provided by the design template</span></span>

5. <span data-ttu-id="57e07-130">选择性地将子项目添加到设计项目</span><span class="sxs-lookup"><span data-stu-id="57e07-130">Optionally add Sub-projects to the design project</span></span>

6. <span data-ttu-id="57e07-131">生成映像</span><span class="sxs-lookup"><span data-stu-id="57e07-131">Build the image</span></span>

<span data-ttu-id="57e07-132">主要更改是为 CE 映像选择正确的 BSP 和其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="57e07-132">The primary change is in the selection of the correct BSP and additional considerations for the CE image.</span></span> <span data-ttu-id="57e07-133">本指南假定你已熟悉构建 Windows CE 系统映像的过程，但在 "已更改" 部分有必要更深入地查看。</span><span class="sxs-lookup"><span data-stu-id="57e07-133">This guide assumes you are already familiar with the process to build a Windows CE system image, but it is worth looking more deeply at the changed section.</span></span>

<span data-ttu-id="57e07-134">步骤2是以前的 OS 设计项目过程的唯一一部分，该过程是在使用 CE 应用容器时更改的，请参阅下面的详细信息。</span><span class="sxs-lookup"><span data-stu-id="57e07-134">Step 2 is the only part of the previous OS Design project process that is changed when using the CE App Container, see below for additional details.</span></span>

### <a name="step-2---platform-builder-bsp-selection"></a><span data-ttu-id="57e07-135">步骤 2-平台生成器 BSP 选择</span><span class="sxs-lookup"><span data-stu-id="57e07-135">Step 2 - Platform Builder BSP Selection</span></span>

<span data-ttu-id="57e07-136">为了支持 Windows CE 应用容器，已将面向 x86 和 ARM 体系结构的新 BSP 添加到了平台生成器中。</span><span class="sxs-lookup"><span data-stu-id="57e07-136">To support the Windows CE App Container, a new BSP that targets x86 and ARM architectures has been added to Platform Builder.</span></span>

<span data-ttu-id="57e07-137">为 CE 应用容器创建 OS 设计时，请选择 "Windows CE 应用容器： x86" 或 "Windows CE 应用容器： ARMv7" (ARM32) ，具体取决于基于 IoT 内核的设备的底层硬件。</span><span class="sxs-lookup"><span data-stu-id="57e07-137">When creating an OS Design for the CE App Container, select either the “Windows CE App Container: x86” or “Windows CE App Container: ARMv7” (ARM32) depending on the underlying hardware for your IoT Core based device.</span></span>

<span data-ttu-id="57e07-138">例如，如果目标 IoT 核心设备使用 Intel 硬件，你将选择 "Windows CE 应用容器： x86" 选项。</span><span class="sxs-lookup"><span data-stu-id="57e07-138">For example, if your target IoT Core device uses Intel hardware, you will select the “Windows CE App Container: x86” option.</span></span> <span data-ttu-id="57e07-139">或者，如果 IoT 核心硬件使用 NXP MX6，将选择 "Windows CE 应用容器： ARMv7" 选项。</span><span class="sxs-lookup"><span data-stu-id="57e07-139">Alternatively, if your IoT Core hardware uses NXP i.MX6, you will select the “Windows CE App Container: ARMv7” option.</span></span>

![选择 CE 应用容器 BSP](./media/WindowsCEAppContainer/image2.png)

<span data-ttu-id="57e07-141">完成此操作后，你将能够配置选项和子项目，就像通常为 Windows 嵌入的压缩映像执行的操作一样。</span><span class="sxs-lookup"><span data-stu-id="57e07-141">After doing this, you will have the ability to configure the options and sub-projects just like you would normally do for a Windows Embedded Compact image.</span></span> <span data-ttu-id="57e07-142">这些配置将内置到 CE 容器，你将部署到 Windows 10 IoT 核心版映像。</span><span class="sxs-lookup"><span data-stu-id="57e07-142">These configurations will be built into the CE Container that you will deploy into your Windows 10 IoT Core image.</span></span>

## <a name="building-the-windows-10-iot-core-image"></a><span data-ttu-id="57e07-143">构建 Windows 10 IoT 核心版映像</span><span class="sxs-lookup"><span data-stu-id="57e07-143">Building the Windows 10 IoT Core Image</span></span>

> [!NOTE]
> <span data-ttu-id="57e07-144">作为[Windows 10 IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)一部分的实验室中更详细地介绍了此过程。</span><span class="sxs-lookup"><span data-stu-id="57e07-144">This process is covered in more detail in the labs that are part of the [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image).</span></span> <span data-ttu-id="57e07-145">以下部分仅提供在 IoT Core 映像生成过程的某些阶段执行的其他操作。</span><span class="sxs-lookup"><span data-stu-id="57e07-145">The section below only provides additional actions to execute at certain stages of the IoT Core image building process.</span></span> <span data-ttu-id="57e07-146">在继续操作之前，强烈建议先熟悉 Windows 10 IoT 核心版制造指南。</span><span class="sxs-lookup"><span data-stu-id="57e07-146">It is highly recommended to familiarize yourself with the Windows 10 IoT Core Manufacturing Guide before proceeding.</span></span>

### <a name="process-overview"></a><span data-ttu-id="57e07-147">过程概述</span><span class="sxs-lookup"><span data-stu-id="57e07-147">Process overview</span></span>

<span data-ttu-id="57e07-148">与构建 Windows 嵌入精简映像的过程不同，Windows 10 IoT 核心版分离还集成了固件的创建、板支持包、映像定义和应用程序包含。</span><span class="sxs-lookup"><span data-stu-id="57e07-148">Unlike the process of building a Windows Embedded Compact image, Windows 10 IoT Core decouples yet integrates the creation of firmware, board support packages, image definition, and application inclusion.</span></span> <span data-ttu-id="57e07-149">通过利用这些组件的不同技术，你可以将所需的工作划分为不同团队或组织中的个人所需的工作。</span><span class="sxs-lookup"><span data-stu-id="57e07-149">By utilizing different technologies for these pieces, you can separate the work you need to do amongst different teams or individuals in your organization.</span></span>

<span data-ttu-id="57e07-150">创建映像的基本步骤如下：</span><span class="sxs-lookup"><span data-stu-id="57e07-150">The basic steps in creating an image are:</span></span>

1. [<span data-ttu-id="57e07-151">创建工作区</span><span class="sxs-lookup"><span data-stu-id="57e07-151">Create a  workspace</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

2. [<span data-ttu-id="57e07-152"> (BSP) 导入相应的 IoT 核心板支持包 </span><span class="sxs-lookup"><span data-stu-id="57e07-152">Import the appropriate IoT Core Board Support Package  (BSP)</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

3. <span data-ttu-id="57e07-153">导入先前创建的 CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="57e07-153">Import the CE App Container you created previously</span></span>

4. [<span data-ttu-id="57e07-154">创建产品定义</span><span class="sxs-lookup"><span data-stu-id="57e07-154">Create your product  definition</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

5. [<span data-ttu-id="57e07-155">向产品添加功能和应用程序</span><span class="sxs-lookup"><span data-stu-id="57e07-155">Add features and applications to your  product</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

6. [<span data-ttu-id="57e07-156"> (FFU 创建完整的闪存更新) </span><span class="sxs-lookup"><span data-stu-id="57e07-156">Build your Full Flash Update  (FFU)</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

7. [<span data-ttu-id="57e07-157">将 FFU 部署到设备并测试</span><span class="sxs-lookup"><span data-stu-id="57e07-157">Deploy the FFU to the device and  test</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

8. [<span data-ttu-id="57e07-158">完成零售 FFU 并为其签名</span><span class="sxs-lookup"><span data-stu-id="57e07-158">Finalize and sign your retail  FFU</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/build-retail-image)

<span data-ttu-id="57e07-159">[Windows 10 IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)中提供了每个步骤的详细指南。</span><span class="sxs-lookup"><span data-stu-id="57e07-159">There are detailed guides for each of these steps as part of the [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image).</span></span> <span data-ttu-id="57e07-160">尽管其中一些步骤类似于使用平台生成器 (PB) 创建设备映像的过程，但有必要更深入地探讨一些区域。</span><span class="sxs-lookup"><span data-stu-id="57e07-160">While some of these steps are like the process of using Platform Builder (PB) to create a device image, it is worth exploring some areas more deeply.</span></span>

#### <a name="step-1---create-a-workspace"></a><span data-ttu-id="57e07-161">步骤 1-创建工作区</span><span class="sxs-lookup"><span data-stu-id="57e07-161">Step 1 - Create a Workspace</span></span>

<span data-ttu-id="57e07-162">请查看 IoT 核心制造指南中的文档 " [创建基本图像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)"，了解如何创建工作区。</span><span class="sxs-lookup"><span data-stu-id="57e07-162">Review the documentation, [Create a Basic Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image), in the IoT Core Manufacturing Guide to learn how to create a workspace.</span></span>

#### <a name="step-2---import-the-appropriate-iot-core-board-support-package-bsp"></a><span data-ttu-id="57e07-163">步骤 2-导入适当的 IoT 核心板支持包 (BSP) </span><span class="sxs-lookup"><span data-stu-id="57e07-163">Step 2 - Import the appropriate IoT Core Board Support Package (BSP)</span></span>

<span data-ttu-id="57e07-164">查看 IoT 核心制造指南中的文档 " [创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)"，以获取有关板的支持。</span><span class="sxs-lookup"><span data-stu-id="57e07-164">Review the documentation, [Create a Basic Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image), in the IoT Core Manufacturing Guide for support for your board.</span></span>

#### <a name="step-3---importing-the-windows-ce-app-container"></a><span data-ttu-id="57e07-165">步骤 3-导入 Windows CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="57e07-165">Step 3 - Importing the Windows CE App Container</span></span>

<span data-ttu-id="57e07-166">Windows CE 应用容器使用 PB 创建，并使用[IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-IoTCEPAL.md#Import-IoTCEPAL)命令导入到 IoT 核心工作区。</span><span class="sxs-lookup"><span data-stu-id="57e07-166">The Windows CE App Container is created using PB as discussed above and imported into your IoT Core workspace by using the [Import-IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-IoTCEPAL.md#Import-IoTCEPAL) command.</span></span> <span data-ttu-id="57e07-167">此命令会将 CE 单层发布目录中所需的内容复制到 IoT ADK 工作区。</span><span class="sxs-lookup"><span data-stu-id="57e07-167">This command will copy the required contents from the CE flat release directory into the IoT ADK workspace.</span></span> <span data-ttu-id="57e07-168">如果多次调用，则会在工作区中的目录下备份以前的状态 `Source-\$Arch\CEPAL.OLD` 。</span><span class="sxs-lookup"><span data-stu-id="57e07-168">If invoked multiple times, the previous state is backed up under the `Source-\$Arch\CEPAL.OLD` directory in the workspace.</span></span>

#### <a name="step-4---create-your-product-definition"></a><span data-ttu-id="57e07-169">步骤 4-创建产品定义</span><span class="sxs-lookup"><span data-stu-id="57e07-169">Step 4 - Create your product definition</span></span>

<span data-ttu-id="57e07-170">请查看 IoT 核心制造指南中的文档， [创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)，创建产品定义。</span><span class="sxs-lookup"><span data-stu-id="57e07-170">Review the documentation, [Create a Basic Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image), in the IoT Core Manufacturing Guide to create your product definition.</span></span>


#### <a name="step-5---adding-ce-app-container-to-a-product"></a><span data-ttu-id="57e07-171">步骤 5-将 CE 应用容器添加到产品</span><span class="sxs-lookup"><span data-stu-id="57e07-171">Step 5 - Adding CE App Container to a product</span></span>

<span data-ttu-id="57e07-172">将 CE 应用容器定义导入到工作区后，需要确保运行 [IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTCEPAL.md#Add-IoTCEPAL) 命令，该命令会将对 CE 应用容器包的引用添加到相关产品 OEMInput.xml 文件 (测试和零售) 。</span><span class="sxs-lookup"><span data-stu-id="57e07-172">Once you have imported your CE App Container definition to your workspace you will need to ensure that you run the [Add-IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTCEPAL.md#Add-IoTCEPAL) command, which will add a reference to CE App Container packages to the relevant product OEMInput.xml files (Test and Retail).</span></span>

<span data-ttu-id="57e07-173">下一步是使用 [IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTProductFeature.md#Add-IoTProductFeature) 命令将 IOT \_ CEPAL 功能添加到 OEMInput.xml。</span><span class="sxs-lookup"><span data-stu-id="57e07-173">The next step is to use the [Add-IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTProductFeature.md#Add-IoTProductFeature) command to add the IOT\_CEPAL feature to the OEMInput.xml.</span></span> <span data-ttu-id="57e07-174">这会将 (Windows CE 应用容器的 Windows 主机支持添加 Windows CE 的前端 UWP 应用 + 支持驱动程序) 到我们的产品定义，并在默认应用组中包含 CE 应用容器。</span><span class="sxs-lookup"><span data-stu-id="57e07-174">This adds the Windows Host support for the Windows CE App Container (Windows CE front-end UWP app + support drivers) to  our product definition and includes the CE App Container in the default Apps group.</span></span> <span data-ttu-id="57e07-175">我们将在后面的部分中讨论启动配置。</span><span class="sxs-lookup"><span data-stu-id="57e07-175">We’ll discuss start-up configuration in a later section.</span></span>

#### <a name="step-6---build-your-cab-files"></a><span data-ttu-id="57e07-176">步骤 6-生成 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="57e07-176">Step 6 - Build your CAB files</span></span>

<span data-ttu-id="57e07-177">这是在创建 FFU 的过程中的一个重要步骤，并且应在每次更改配置、添加/更改应用程序或驱动程序时执行。</span><span class="sxs-lookup"><span data-stu-id="57e07-177">This is an important step during the creation of your FFU and should be done whenever you change a configuration, add/change an application or drivers.</span></span> <span data-ttu-id="57e07-178">将使用 [IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md#New-IoTCabPackage) 和 "All" 选项。</span><span class="sxs-lookup"><span data-stu-id="57e07-178">You will use the [New-IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md#New-IoTCabPackage) with the “All” option.</span></span> <span data-ttu-id="57e07-179">你还可以根据需要构建单一功能，但通常应在生成 FFU 的步骤之前重新生成所有包。</span><span class="sxs-lookup"><span data-stu-id="57e07-179">You can also build Single features as needed but in general you should rebuild all the packages prior to the step of building your FFU as best practice.</span></span>

#### <a name="step-7---deploying-your-ffu-to-your-device"></a><span data-ttu-id="57e07-180">步骤 7-将 FFU 部署到设备</span><span class="sxs-lookup"><span data-stu-id="57e07-180">Step 7 - Deploying your FFU to your device</span></span>

<span data-ttu-id="57e07-181">构建映像后，可以将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="57e07-181">Once the image is built, you can deploy it to a device.</span></span> <span data-ttu-id="57e07-182">这可以通过使用[DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/what-is-dism)通过特定于设备的部署过程或通过使用[Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)从命令行完成。</span><span class="sxs-lookup"><span data-stu-id="57e07-182">This can be done from the command line using [DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/what-is-dism), via your device-specific deployment process or by using the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="57e07-183">[Windows 10 IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)中提供了更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="57e07-183">More details are available as part of the [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image).</span></span>

##### <a name="deploying-the-windows-ce-app-container-to-a-device-when-using-an-existing-ffu"></a><span data-ttu-id="57e07-184">使用现有 FFU 将 Windows CE 应用容器部署到设备</span><span class="sxs-lookup"><span data-stu-id="57e07-184">Deploying the Windows CE App Container to a device when using an existing FFU</span></span>

<span data-ttu-id="57e07-185">CE Cab 是 IoT Core 上的可部署包。</span><span class="sxs-lookup"><span data-stu-id="57e07-185">The CE CABs are deployable packages on IoT Core.</span></span> <span data-ttu-id="57e07-186">如果存在现有的 IoT 核心映像，可以使用命令将这些 Cab 部署到设备 `APPLYUPDATE` 。</span><span class="sxs-lookup"><span data-stu-id="57e07-186">If there is an existing IoT Core image, these CABs can be deployed to the device using the `APPLYUPDATE` command.</span></span> <span data-ttu-id="57e07-187">首先将 Cab 复制到设备，然后通过暂存并提交 Cab `APPLYUPDATE` 。</span><span class="sxs-lookup"><span data-stu-id="57e07-187">First copy the CABs to the device, then stage and commit the CABs with `APPLYUPDATE`.</span></span> <span data-ttu-id="57e07-188">请注意，更新此方法会使包版本控制更为强大，因此，如果要将包的更新版本部署到设备，则这些版本的版本号必须更高。</span><span class="sxs-lookup"><span data-stu-id="57e07-188">Do note that updating this way respects package versioning, so if updated versions of packages are to be deployed to the device, they must have a greater version number.</span></span> <span data-ttu-id="57e07-189"> (在 IoT ADK 环境) 中查看 Set-IoTCabVersion 命令。</span><span class="sxs-lookup"><span data-stu-id="57e07-189">(See the Set-IoTCabVersion command in the IoT ADK environment).</span></span> <span data-ttu-id="57e07-190">有关此方面的详细信息，请参阅 [创建和安装包](https://docs.microsoft.com/enus/windows-hardware/manufacture/iot/create-install-package.)</span><span class="sxs-lookup"><span data-stu-id="57e07-190">More information on this can be found in [Create and Install Packages](https://docs.microsoft.com/enus/windows-hardware/manufacture/iot/create-install-package.)</span></span>

#### <a name="step-8---building-a-retail-image"></a><span data-ttu-id="57e07-191">步骤 8-构建零售映像</span><span class="sxs-lookup"><span data-stu-id="57e07-191">Step 8 - Building a retail image</span></span>

<span data-ttu-id="57e07-192">使用正确的签名映像是保护和更新设备的重要部分。</span><span class="sxs-lookup"><span data-stu-id="57e07-192">Having a properly signed image is an important part of securing and updating a device.</span></span> <span data-ttu-id="57e07-193">对于 Windows 10 IoT 核心版，此外观显示为测试签名版本和已签名零售版本之间的差异。</span><span class="sxs-lookup"><span data-stu-id="57e07-193">For Windows 10 IoT Core, this appears as the difference between Test signed and Retail signed builds.</span></span> <span data-ttu-id="57e07-194">绝不应公开部署测试已签名映像。</span><span class="sxs-lookup"><span data-stu-id="57e07-194">You should never publicly deploy a test signed image.</span></span> <span data-ttu-id="57e07-195">测试签名映像只应用于调试目的，在创建最终零售签名映像之前，应更正任何错误或配置更改。</span><span class="sxs-lookup"><span data-stu-id="57e07-195">Test signed images should only be used for debug purposes and you should correct any errors or configuration changes prior to creating your final retail signed image.</span></span>

> [!NOTE]
> <span data-ttu-id="57e07-196">除了计算机上安装的开发和部署工具外，还需要以下内容来启用零售签名：</span><span class="sxs-lookup"><span data-stu-id="57e07-196">In addition to the development and deployment tools installed on your machine you will also need the following to enable retail signing:</span></span>
>
> - <span data-ttu-id="57e07-197">零售代码签名证书</span><span class="sxs-lookup"><span data-stu-id="57e07-197">A retail code-signing certificate</span></span>
> - <span data-ttu-id="57e07-198">交叉签名证书</span><span class="sxs-lookup"><span data-stu-id="57e07-198">A cross-signing certificate</span></span>

### <a name="properly-signing-and-including-your-applications"></a><span data-ttu-id="57e07-199">正确签名和包括应用程序</span><span class="sxs-lookup"><span data-stu-id="57e07-199">Properly signing and including your applications</span></span>

<span data-ttu-id="57e07-200">如果你有一个或多个要包含在 Windows 10 IoT 核心版零售映像中的自定义应用程序，则需要验证这些应用程序在零售映像中包含它们时是否已正确签名。</span><span class="sxs-lookup"><span data-stu-id="57e07-200">If you have one or more custom applications that you want to include in your Windows 10 IoT Core retail image, you need to verify that these applications are signed properly when including them in your retail image.</span></span>

## <a name="additional-information"></a><span data-ttu-id="57e07-201">其他信息</span><span class="sxs-lookup"><span data-stu-id="57e07-201">Additional Information</span></span>

### <a name="adding-new-applications-to-an-existing-image"></a><span data-ttu-id="57e07-202">将新应用程序添加到现有映像</span><span class="sxs-lookup"><span data-stu-id="57e07-202">Adding new applications to an existing image</span></span>

<span data-ttu-id="57e07-203">若要将新应用程序添加到现有 OS 设计，可以将项目作为子项目添加到 OS 设计 Project，也可以创建常规部署 CAB 包，以在初始设备设置过程中将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="57e07-203">To add a new application to an existing OS Design you can either add the project as a sub-project to the OS Design Project or you can create normal deployment CAB packages to deploy those to the device as part of the initial device setup.</span></span>

### <a name="packaging-best-practices"></a><span data-ttu-id="57e07-204">打包最佳做法</span><span class="sxs-lookup"><span data-stu-id="57e07-204">Packaging Best Practices</span></span>

<span data-ttu-id="57e07-205">应始终确保包尽可能精细，以减少更新时间。</span><span class="sxs-lookup"><span data-stu-id="57e07-205">You should always aim to make sure packages are as granular as possible to reduce update time.</span></span>

<span data-ttu-id="57e07-206">由于包是最小的更新单元，因此请确保每个包尽可能小。</span><span class="sxs-lookup"><span data-stu-id="57e07-206">Since a package is the smallest unit of updating, make sure that each package is as small as possible.</span></span> <span data-ttu-id="57e07-207">在 Platform Builder 中生成时，生成的包根据内存部分和模块/文件类型根据 bib 文件自动进行分隔。</span><span class="sxs-lookup"><span data-stu-id="57e07-207">When building in Platform Builder, the generated packages are separated according to memory section and module/file type according to the bib file automatically.</span></span>

- <span data-ttu-id="57e07-208">对于在平台生成器中构建并通过 OSDesign.bib 打包的自定义资产，请考虑将自定义资产添加到 BIB (中的单独内存部分，而不是在 NK) 中，以便自定义代码的更新可以独立于 CE OS 的更新提供。</span><span class="sxs-lookup"><span data-stu-id="57e07-208">For custom assets built in Platform Builder and packaged through OSDesign.bib, consider adding custom assets into a separate memory section in the BIB (not in NK), so that updates to custom code can ship separate from updates to the CE OS.</span></span>

- <span data-ttu-id="57e07-209">对于通过 IoT ADK 打包命令添加的自定义资产：请确保创建的包尽可能小。</span><span class="sxs-lookup"><span data-stu-id="57e07-209">For custom assets added through the IoT ADK packaging commands: Make sure the packages created are as small as possible.</span></span>

### <a name="adding-other-things-to-the-platform-builder-package"></a><span data-ttu-id="57e07-210">将其他内容添加到 Platform Builder 包</span><span class="sxs-lookup"><span data-stu-id="57e07-210">Adding other things to the Platform Builder package</span></span>

<span data-ttu-id="57e07-211">通常，建议不要修改平台生成器生成的包，以在系统映像中包括其他组件。</span><span class="sxs-lookup"><span data-stu-id="57e07-211">In general, the recommendation is not to modify the resulting package produced by Platform Builder to include additional components into the system image.</span></span> <span data-ttu-id="57e07-212">请改为按照Windows 10 IoT 核心版[指南操作](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="57e07-212">Instead, follow the [Windows 10 IoT Core manufacturing guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="57e07-213">但是，如果必须将文件添加到平台生成器创建的包中，请按照现有过程操作。</span><span class="sxs-lookup"><span data-stu-id="57e07-213">However, if files must be added to the package that is created by Platform Builder, follow your existing process.</span></span> <span data-ttu-id="57e07-214">将内容添加到 PB 生成的包时，请考虑以下事项：</span><span class="sxs-lookup"><span data-stu-id="57e07-214">When adding content to the package generated by PB, consider the following:</span></span>

- <span data-ttu-id="57e07-215">包的最大大小为 (400 MB) 超过此大小将阻止更新。</span><span class="sxs-lookup"><span data-stu-id="57e07-215">There is a maximum size for packages (about 400 MB) and exceeding this size will prevent updating.</span></span>

- <span data-ttu-id="57e07-216">更新在包粒度上发生。</span><span class="sxs-lookup"><span data-stu-id="57e07-216">Updates happen on package granularity.</span></span> <span data-ttu-id="57e07-217">如果需要更新包中的单个资产，则包的所有资产将同时更新。</span><span class="sxs-lookup"><span data-stu-id="57e07-217">If a single asset in the package needs to be updated, then all the assets of that package will be updated at the same time.</span></span> <span data-ttu-id="57e07-218">若要减小更新大小，可将内容隔离到单独的包中，以最大程度地减小总体更新大小。</span><span class="sxs-lookup"><span data-stu-id="57e07-218">To reduce the size of updates, isolate content into separate packages to minimize the overall update size.</span></span>

### <a name="adding-additional-files-through-platform-builder"></a><span data-ttu-id="57e07-219">通过平台生成器添加其他文件</span><span class="sxs-lookup"><span data-stu-id="57e07-219">Adding additional files through Platform Builder</span></span>

<span data-ttu-id="57e07-220">上面详述的打包过程由生成 CE BIN 文件的相同输入驱动。</span><span class="sxs-lookup"><span data-stu-id="57e07-220">The packaging process detailed above is driven by the same inputs that go into building a CE BIN file.</span></span> <span data-ttu-id="57e07-221">因此，如果在 OSDesign.bib 中引用文件，并且注册表项添加到 OSDesign.reg，则该过程将在生成的 CAB 文件中包括 `MAKEIMG` 这些文件。</span><span class="sxs-lookup"><span data-stu-id="57e07-221">So, if the files are referenced in OSDesign.bib and registry entries are added to OSDesign.reg, the `MAKEIMG` process will include these files in the resulting CAB file.</span></span> <span data-ttu-id="57e07-222">在此过程期间 `MAKEIMG` ，现在将：</span><span class="sxs-lookup"><span data-stu-id="57e07-222">During this process `MAKEIMG` will now:</span></span>

1. <span data-ttu-id="57e07-223">`ROMIMAGE`将在平面发布目录和 FRD (内) 一个名为 的目录，用于为 `CEPAL\_PKG` CEPAL Windows CE安装目录结构。</span><span class="sxs-lookup"><span data-stu-id="57e07-223">`ROMIMAGE` will create a directory named `CEPAL\_PKG` within the Flat Release Directory (FRD) that stages an installed directory structure for Windows CE for CEPAL.</span></span>

2. <span data-ttu-id="57e07-224">`ROMIMAGE` 根据 CE BIB 文件清点放入 `CEPAL\_PKG` 的所有 CE 文件。</span><span class="sxs-lookup"><span data-stu-id="57e07-224">`ROMIMAGE` inventories all CE files that were placed into `CEPAL\_PKG` based on CE BIB files.</span></span>

3. <span data-ttu-id="57e07-225">`ROMIMAGE` 将为每个内存WM.XML多个文件。</span><span class="sxs-lookup"><span data-stu-id="57e07-225">`ROMIMAGE` will create multiple WM.XML files for each memory section.</span></span> <span data-ttu-id="57e07-226">这样做是为了以更精细的方式推送更新，因为更新的最小单位是包。</span><span class="sxs-lookup"><span data-stu-id="57e07-226">This is done so that updates can be pushed in a more granular fashion as the minimum unit of update is a package.</span></span>

4. <span data-ttu-id="57e07-227">`ROMIMAGE` 将创建引用所有已创建的包的 。</span><span class="sxs-lookup"><span data-stu-id="57e07-227">`ROMIMAGE` will create  that references all the created packages.</span></span>

<span data-ttu-id="57e07-228">创建的所有包都将使用固定前缀 进行命名，在 `“%OEM\_NAME%.WindowsCE.\*”` `%OEM\_NAME%` 调用 [New-IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md)时，将在 IoT 核心创建过程中填充该前缀。</span><span class="sxs-lookup"><span data-stu-id="57e07-228">All of the packages created will be named with a fixed prefix of `“%OEM\_NAME%.WindowsCE.\*”`, where `%OEM\_NAME%` is populated during the IoT Core creation process when calling [New-IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md).</span></span> <span data-ttu-id="57e07-229">名称空间内的包名称派生自 BIB 文件的内存部分 (例如 NK) 后跟模块/文件 (BIB 文件也由 BIB 文件) 。</span><span class="sxs-lookup"><span data-stu-id="57e07-229">The Package Name within the name space is derived from the memory section in the BIB file (e.g. NK) followed by modules / files (also determined by the BIB file).</span></span>

#### <a name="communicating-between-windows-embedded-compact-2013-and-windows-10-iot-core-applications"></a><span data-ttu-id="57e07-230">Windows Embedded Compact 2013 与 Windows 10 IoT 核心版 应用程序之间的通信</span><span class="sxs-lookup"><span data-stu-id="57e07-230">Communicating between Windows Embedded Compact 2013 and Windows 10 IoT Core applications</span></span>

<span data-ttu-id="57e07-231">在 CE 容器中运行的应用程序之间进行通信的建议方法是使用本地环回。</span><span class="sxs-lookup"><span data-stu-id="57e07-231">The recommended approach to communicate between applications running in the CE Container is to use Local Loopback.</span></span> <span data-ttu-id="57e07-232">可以在此文档中详细了解 [本地环回。](https://docs.microsoft.com/windows/iot-core/develop-your-app/loopback)</span><span class="sxs-lookup"><span data-stu-id="57e07-232">You can read more on [Local Loopback in this document.](https://docs.microsoft.com/windows/iot-core/develop-your-app/loopback)</span></span>

### <a name="automatically-starting-the-ce-app-container-application"></a><span data-ttu-id="57e07-233">自动启动 CE 应用容器应用程序</span><span class="sxs-lookup"><span data-stu-id="57e07-233">Automatically starting the CE App Container application</span></span>

<span data-ttu-id="57e07-234">若要自动启动 CE 容器应用程序，可以创建一个预配[包，将](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)启动应用程序设置为"Microsoft" 。Windows。IoT.CEPAL.DkMonUWP \_ cw5n1h2txyewy！应用"，并且此预配包包含在映像中。</span><span class="sxs-lookup"><span data-stu-id="57e07-234">To automatically start the CE Container application, you can create a [Provisioning Package](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image) that sets the startup application to “Microsoft.Windows.IoT.CEPAL.DkMonUWP\_cw5n1h2txyewy!App”, and included this provisioning package in the image.</span></span> <span data-ttu-id="57e07-235">还需要使用 [Remove-IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Remove-IoTProductFeature.md) 命令删除默认启动应用程序，并从 IoT 核心产品定义中删除 IOT \_ BERTHA 功能 ID。</span><span class="sxs-lookup"><span data-stu-id="57e07-235">You will also need to remove the default startup application by using the [Remove-IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Remove-IoTProductFeature.md) command and removing the IOT\_BERTHA Feature ID from the IoT Core product definition.</span></span>

### <a name="available-configuration-settings-for-the-windows-ce-app-container"></a><span data-ttu-id="57e07-236">可用的配置设置Windows CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="57e07-236">Available Configuration settings for the Windows CE App Container</span></span>

#### <a name="registry-based-configuration-in-ce"></a><span data-ttu-id="57e07-237">CE 中基于注册表的配置</span><span class="sxs-lookup"><span data-stu-id="57e07-237">Registry-based configuration in CE</span></span>

##### <a name="non-executable-stack-by-default"></a><span data-ttu-id="57e07-238">默认为非可执行堆栈</span><span class="sxs-lookup"><span data-stu-id="57e07-238">Non-Executable Stack by Default</span></span>

<span data-ttu-id="57e07-239">默认情况下Windows CE 应用容器禁用可执行堆栈页以提高安全性。</span><span class="sxs-lookup"><span data-stu-id="57e07-239">The Windows CE App Container has disabled executable stack pages by default to improve security.</span></span> <span data-ttu-id="57e07-240">但是，某些旧版应用程序可能依赖于此行为来正常运行。</span><span class="sxs-lookup"><span data-stu-id="57e07-240">However, some legacy applications may rely on this behavior to run correctly.</span></span> <span data-ttu-id="57e07-241">若要启用可执行堆栈，在 CE 映像中设置以下注册表值 (建议在 Platform Builder 映像中转到 OSDesign.reg) </span><span class="sxs-lookup"><span data-stu-id="57e07-241">To Enable an Executable Stack, set the following registry value in the CE image (It is recommended that this goes into OSDesign.reg in Platform Builder)</span></span>

```AsciiDoc
KeyPath = HKEY\_LOCAL\_MACHINE\CEPAL
ValueName = MemoryOptions Type = REG\_DWORD
Value = 1
```

##### <a name="16-bit-565-override-for-gwes"></a><span data-ttu-id="57e07-242">GWES 的 16 位 565 重写</span><span class="sxs-lookup"><span data-stu-id="57e07-242">16-bit 565 Override for GWES</span></span>

<span data-ttu-id="57e07-243">如果 Windows CE 应用容器 配置为 32 位显示器，则 GWES 完成 16 位到 32 位 RGB 的转换，前提是 16 位 RGB 像素数据采用 RGB555 格式。</span><span class="sxs-lookup"><span data-stu-id="57e07-243">If the Windows CE App Container is configured with a 32-bit display, then 16-bit to 32-bit RGB conversions are done by GWES are done with the assumption that 16-bit RGB pixel data is in RGB555 format.</span></span> <span data-ttu-id="57e07-244">如果位图资源位于 16 位 565 中，并且无法转换为这些资源中的 RGB555，则可以通过注册表项更改 GWES 的默认转换行为。</span><span class="sxs-lookup"><span data-stu-id="57e07-244">If bitmap resources are in 16-bit 565, and conversion to a RGB555 of these resources is not possible, GWES’s default conversion behavior can be changed via a registry key.</span></span> <span data-ttu-id="57e07-245">创建以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="57e07-245">Create the following registry key:</span></span>

```AsciiDoc
HKEY\_LOCAL\_MACHINE\SYSTEM\GDI\16bpp565RGBPalette.
```

#### <a name="registry-based-configuration-in-host-iot-core"></a><span data-ttu-id="57e07-246">主机和 IoT Core (中基于注册表) </span><span class="sxs-lookup"><span data-stu-id="57e07-246">Registry-based configuration in Host (IoT Core)</span></span>

##### <a name="configuring-serial-ports-for-the-windows-ce-app-container"></a><span data-ttu-id="57e07-247">为端口配置串行Windows CE 应用容器</span><span class="sxs-lookup"><span data-stu-id="57e07-247">Configuring serial ports for the Windows CE App Container</span></span>

<span data-ttu-id="57e07-248">主机串行端口需要映射到 CE 环境中。</span><span class="sxs-lookup"><span data-stu-id="57e07-248">Host Serial ports need to be mapped into the CE environment.</span></span> <span data-ttu-id="57e07-249">此映射存在于 IoT 核心的注册表中，需要由映像创建者配置。</span><span class="sxs-lookup"><span data-stu-id="57e07-249">This mapping exists in registry in IoT Core and needs to be configured by the image creator.</span></span>

<span data-ttu-id="57e07-250">在 `HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial` 下，存在配置条目，以使用以下架构将来宾 COM 端口映射到主机 COM 端口。</span><span class="sxs-lookup"><span data-stu-id="57e07-250">Under `HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial`, configuration entries exist to map Guest COM ports to Host COM ports using the following schema.</span></span>

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

<span data-ttu-id="57e07-251">如果在启动 CE 时上述注册表路径不存在，将基于系统上发现的串行设备写入默认配置。</span><span class="sxs-lookup"><span data-stu-id="57e07-251">If the registry path above does not exist when CE is booted, a default configuration will be written based on discovered serial devices on the system.</span></span>

#### <a name="file-based-configuration-in-host"></a><span data-ttu-id="57e07-252">主机中的基于文件的配置</span><span class="sxs-lookup"><span data-stu-id="57e07-252">File Based configuration in Host</span></span>

<span data-ttu-id="57e07-253">CE 容器可以使用主机 上的本地文件进行配置 `C:\WindowsCE\CEEnvConfig.json` 。</span><span class="sxs-lookup"><span data-stu-id="57e07-253">The CE Container can be configured using a local file on the host `C:\WindowsCE\CEEnvConfig.json`.</span></span> <span data-ttu-id="57e07-254">下面是此配置文件的示例：</span><span class="sxs-lookup"><span data-stu-id="57e07-254">Here is a sample of this configuration file:</span></span>

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

#### <a name="oemoptions"></a><span data-ttu-id="57e07-255">OEMOptions</span><span class="sxs-lookup"><span data-stu-id="57e07-255">OEMOptions</span></span>

| <span data-ttu-id="57e07-256">密钥</span><span class="sxs-lookup"><span data-stu-id="57e07-256">Key</span></span>           | <span data-ttu-id="57e07-257">说明</span><span class="sxs-lookup"><span data-stu-id="57e07-257">Description</span></span>                                                                                                            |
|---------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="57e07-258">GUI</span><span class="sxs-lookup"><span data-stu-id="57e07-258">GUI</span></span>           | <span data-ttu-id="57e07-259">使用 UI 启动 CE 应用容器 (默认值 true) </span><span class="sxs-lookup"><span data-stu-id="57e07-259">Launch the CE app container with UI (default true)</span></span>                                                                     |
| <span data-ttu-id="57e07-260">宽度</span><span class="sxs-lookup"><span data-stu-id="57e07-260">Width</span></span>         | <span data-ttu-id="57e07-261">CE 应用容器的宽度显示 (默认为 1024) </span><span class="sxs-lookup"><span data-stu-id="57e07-261">Width of the CE app container display (default 1024)</span></span>                                                                   |
| <span data-ttu-id="57e07-262">高度</span><span class="sxs-lookup"><span data-stu-id="57e07-262">Height</span></span>        | <span data-ttu-id="57e07-263">CE 应用容器的高度 (默认为 768) </span><span class="sxs-lookup"><span data-stu-id="57e07-263">Height of the CE app container display (default 768)</span></span>                                                                   |
| <span data-ttu-id="57e07-264">FillScreen</span><span class="sxs-lookup"><span data-stu-id="57e07-264">FillScreen</span></span>    |                                                                                                                        |
| <span data-ttu-id="57e07-265">ColorDepth</span><span class="sxs-lookup"><span data-stu-id="57e07-265">ColorDepth</span></span>    | <span data-ttu-id="57e07-266">将每个像素的默认位数设置为 (默认 32) </span><span class="sxs-lookup"><span data-stu-id="57e07-266">Sets default bits per pixel (default 32)</span></span>                                                                               |
| <span data-ttu-id="57e07-267">RefreshRate</span><span class="sxs-lookup"><span data-stu-id="57e07-267">RefreshRate</span></span>   | <span data-ttu-id="57e07-268">每秒重绘显示次数</span><span class="sxs-lookup"><span data-stu-id="57e07-268">How many times the display is redrawn per second</span></span>                                                                       |
| <span data-ttu-id="57e07-269">noAslrSupport</span><span class="sxs-lookup"><span data-stu-id="57e07-269">noAslrSupport</span></span> | <span data-ttu-id="57e07-270">禁用 CE 应用容器中的地址空间布局随机化 (默认值 true) </span><span class="sxs-lookup"><span data-stu-id="57e07-270">Disables address space layout randomization in the CE app container (default true)</span></span>                                     |
| <span data-ttu-id="57e07-271">OEMConfigApp</span><span class="sxs-lookup"><span data-stu-id="57e07-271">OEMConfigApp</span></span>  | <span data-ttu-id="57e07-272">OEM 提供的应用的包系列名称，应启动该应用进行配置。</span><span class="sxs-lookup"><span data-stu-id="57e07-272">Package Family Name of an OEM provided app that should be launched for configuration.</span></span>                                  |
| <span data-ttu-id="57e07-273">OEMConfigFile</span><span class="sxs-lookup"><span data-stu-id="57e07-273">OEMConfigFile</span></span> | <span data-ttu-id="57e07-274">包含 OEMConfigApp 和 CE 应用容器之间共享的其他配置选项的文件的路径</span><span class="sxs-lookup"><span data-stu-id="57e07-274">Path to a file that contains additional configuration options shared between the OEMConfigApp and the CE app container</span></span> |

<span data-ttu-id="57e07-275">CE 应用容器仅提供一个网络接口供使用。</span><span class="sxs-lookup"><span data-stu-id="57e07-275">The CE app container only makes one network interface available for use.</span></span> <span data-ttu-id="57e07-276">如果主机系统中存在多个 NIC，则必须在主机注册表中选择一个接口，以确保所选 NIC 具有确定性。</span><span class="sxs-lookup"><span data-stu-id="57e07-276">If multiple NICs are present in the Host System, one interface must be selected in the Host Registry to ensure the selected NIC is deterministic.</span></span>

##### <a name="oemconfigfile"></a><span data-ttu-id="57e07-277">OEMConfigFile</span><span class="sxs-lookup"><span data-stu-id="57e07-277">OEMConfigFile</span></span>

<span data-ttu-id="57e07-278">OEMConfigFile 在 中指定 `C:\WindowsCE\CEEnvConfig.json` 。</span><span class="sxs-lookup"><span data-stu-id="57e07-278">The OEMConfigFile is specified in `C:\WindowsCE\CEEnvConfig.json`.</span></span> <span data-ttu-id="57e07-279">确保 UWP 应用程序可以读取此文件。</span><span class="sxs-lookup"><span data-stu-id="57e07-279">Make sure this file can be read by a UWP application.</span></span> <span data-ttu-id="57e07-280">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="57e07-280">The following is a sample:</span></span>

```xml
{
   “FactoryReset”: false, “PlatformBuilderDebugMode”: false,
   “NetInterface”: “Some Network Profile Id”
}
```

<span data-ttu-id="57e07-281">选项：</span><span class="sxs-lookup"><span data-stu-id="57e07-281">Options:</span></span>

| <span data-ttu-id="57e07-282">密钥</span><span class="sxs-lookup"><span data-stu-id="57e07-282">Key</span></span>                      | <span data-ttu-id="57e07-283">说明</span><span class="sxs-lookup"><span data-stu-id="57e07-283">Description</span></span>                                                                              |
|--------------------------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="57e07-284">FactoryReset</span><span class="sxs-lookup"><span data-stu-id="57e07-284">FactoryReset</span></span>             | <span data-ttu-id="57e07-285">由配置应用用来指示 CE 应用容器转储持久状态。</span><span class="sxs-lookup"><span data-stu-id="57e07-285">Used by the config app to signal the CE App Container to dump persistent state.</span></span>          |
| <span data-ttu-id="57e07-286">PlatformBuilderDebugMode</span><span class="sxs-lookup"><span data-stu-id="57e07-286">PlatformBuilderDebugMode</span></span> | <span data-ttu-id="57e07-287">用于启动具有 KITL 支持的 CE 应用容器，以便使用平台生成器进行调试。</span><span class="sxs-lookup"><span data-stu-id="57e07-287">Used to boot the CE App Container with KITL support for debugging with Platform Builder.</span></span> |
| <span data-ttu-id="57e07-288">NetInterface</span><span class="sxs-lookup"><span data-stu-id="57e07-288">NetInterface</span></span>             | <span data-ttu-id="57e07-289">根据配置文件名称为 CE 选择网络接口。</span><span class="sxs-lookup"><span data-stu-id="57e07-289">Select a Network Interface for CE based on profile name.</span></span>                                 |


## <a name="references"></a><span data-ttu-id="57e07-290">参考</span><span class="sxs-lookup"><span data-stu-id="57e07-290">References</span></span>

- [<span data-ttu-id="57e07-291">获取自定义数据所需的Windows 10 IoT 核心版</span><span class="sxs-lookup"><span data-stu-id="57e07-291">Get the tools needed to customize Windows 10 IoT Core</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)
- [<span data-ttu-id="57e07-292">BSP 支持 IoT 核心 (包) </span><span class="sxs-lookup"><span data-stu-id="57e07-292">IoT Core Board Supported Packages (BSP)</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/bsphardware)
- [<span data-ttu-id="57e07-293">IoT 核心制造指南</span><span class="sxs-lookup"><span data-stu-id="57e07-293">IoT Core Manufacturing Guide</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)
- [<span data-ttu-id="57e07-294">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="57e07-294">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)
- [<span data-ttu-id="57e07-295">创建和安装包</span><span class="sxs-lookup"><span data-stu-id="57e07-295">Create and Install Packages</span></span>](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-install-package)
