---
title: 使用 Visual Studio 部署应用
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Visual Studio 远程调试功能部署应用。
keywords: windows iot、 visual studio、 应用部署、 远程调试
ms.openlocfilehash: 218cbf43a1b63a517091b80315f327954b3eae5a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510853"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="96723-104">使用 Visual Studio 部署应用</span><span class="sxs-lookup"><span data-stu-id="96723-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="96723-105">使用 Visual Studio 部署和调试应用程序很简单。</span><span class="sxs-lookup"><span data-stu-id="96723-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="96723-106">我们将使用**远程调试**功能将应用部署到本地连接的 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="96723-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="96723-107">部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。</span><span class="sxs-lookup"><span data-stu-id="96723-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="96723-108">为了使用远程调试，IoT 核心版设备必须首先连接到与开发电脑相同的本地网络。</span><span class="sxs-lookup"><span data-stu-id="96723-108">In order to use remote debugging, your IoT Core device must first be connected to same local network as your development PC.</span></span>  
><span data-ttu-id="96723-109">请参阅[连接到的设备](../connect-your-device/SetupWiFi.md)说明。</span><span class="sxs-lookup"><span data-stu-id="96723-109">See the [Connecting to a device](../connect-your-device/SetupWiFi.md) instructions.</span></span>

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a><span data-ttu-id="96723-110">部署C#应用到 Windows 10 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="96723-110">Deploy a C# app to your Windows 10 IoT Core device</span></span> 
___

1. <span data-ttu-id="96723-111">应用程序在 Visual Studio 中打开后，在工具栏下拉列表中设置体系结构。</span><span class="sxs-lookup"><span data-stu-id="96723-111">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="96723-112">如果您正在构建的 Minnowboard 最大值，则选择`x86`。</span><span class="sxs-lookup"><span data-stu-id="96723-112">If you're building for Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="96723-113">如果您正在构建为 Raspberry Pi 2、 Raspberry Pi 3 或 Dragonboard，选择`ARM`。</span><span class="sxs-lookup"><span data-stu-id="96723-113">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="96723-114">接下来，在 Visual Studio 工具栏中，单击`Local Machine`下拉列表中，然后选择`Remote Machine`。</span><span class="sxs-lookup"><span data-stu-id="96723-114">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![在 Visual Studio 中的远程计算机](../media/AppDeployment/cs-remote-machine-debugging.png)

3. <span data-ttu-id="96723-116">此时，Visual Studio 将显示“远程连接”对话框。</span><span class="sxs-lookup"><span data-stu-id="96723-116">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="96723-117">如果以前使用过[PowerShell](../connect-your-device/PowerShell.md)若要设置你的设备的唯一名称，您可以在此处输入 (在此示例中，我们使用**我的设备**)。</span><span class="sxs-lookup"><span data-stu-id="96723-117">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="96723-118">否则，使用 Windows IoT 核心版设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="96723-118">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="96723-119">输入设备名称/IP 后选择`Universal (Unencrypted Protocol)`身份验证模式，然后单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="96723-119">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![通用身份验证模式](../media/AppDeployment/cs-remote-connections.png)

<span data-ttu-id="96723-121">可通过导航到项目属性（在解决方案资源管理器中选择“属性”）并在左侧选择 `Debug` 选项卡来验证或修改这些值：</span><span class="sxs-lookup"><span data-stu-id="96723-121">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![“调试”选项卡](../media/AppDeployment/cs-debug-project-properties.png)

5. <span data-ttu-id="96723-123">现在我们已准备好部署。</span><span class="sxs-lookup"><span data-stu-id="96723-123">Now we're ready to deploy.</span></span> <span data-ttu-id="96723-124">只需按 F5 (或选择调试\|开始调试) 若要开始调试我们的应用程序。</span><span class="sxs-lookup"><span data-stu-id="96723-124">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="96723-125">你应该会看到你的设备的屏幕上显示应用。</span><span class="sxs-lookup"><span data-stu-id="96723-125">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="96723-126">部署完成后，可设置断点、查看变量值等。若要停止应用程序按停止调试按钮 (或选择调试\|停止调试)。</span><span class="sxs-lookup"><span data-stu-id="96723-126">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

7. <span data-ttu-id="96723-127">已成功部署和调试 UWP 应用程序，创建的发布版本的后更改 Visual Studio 工具栏配置下拉列表从`Debug`到`Release`。</span><span class="sxs-lookup"><span data-stu-id="96723-127">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="96723-128">现在可以生成，并将应用部署到你的设备，通过选择生成\|重新生成解决方案和生成\|部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="96723-128">You can now build and deploy your app to your device by selecting Build \| Rebuild Solution and Build \| Deploy Solution.</span></span>

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a><span data-ttu-id="96723-129">部署C++应用到 Windows 10 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="96723-129">Deploy a C++ app to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="96723-130">应用程序在 Visual Studio 中打开后，在工具栏下拉列表中设置体系结构。</span><span class="sxs-lookup"><span data-stu-id="96723-130">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="96723-131">如果您正在构建的 Minnowboard 最大值，则选择`86`。</span><span class="sxs-lookup"><span data-stu-id="96723-131">If you're building for Minnowboard Max, select `86`.</span></span> <span data-ttu-id="96723-132">如果你要针对 Raspberry Pi 2 或 3 进行生成，请选择 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="96723-132">If you're building for Raspberry Pi 2 or 3, select `ARM`.</span></span>

2. <span data-ttu-id="96723-133">接下来，在 Visual Studio 工具栏中，单击`Local Machine`下拉列表中，然后选择</span><span class="sxs-lookup"><span data-stu-id="96723-133">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select</span></span> `Remote Machine`

![在 Visual Studio 中的本地计算机](../media/AppDeployment/cpp-remote-machine-debugging.png)

3. <span data-ttu-id="96723-135">接下来，在“解决方案资源管理器”窗格中，右键单击该项目。</span><span class="sxs-lookup"><span data-stu-id="96723-135">Next, right click on your project in the **Solution Explorer** pane.</span></span> <span data-ttu-id="96723-136">选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="96723-136">Select **Properties**.</span></span> 

![在 Visual Studio 中的属性](../media/AppDeployment/cpp-project-properties.png)

4. <span data-ttu-id="96723-138">在“配置属性”->“调试”下，修改以下字段：</span><span class="sxs-lookup"><span data-stu-id="96723-138">Under **Configuration Properties -> Debugging**, modify the following fields:</span></span>

    * <span data-ttu-id="96723-139">**计算机名**：如果以前曾使用 PowerShell 设置设备的唯一名称，可在此处输入该名称（在此示例中，我们使用的是 **my-device**）。</span><span class="sxs-lookup"><span data-stu-id="96723-139">**Machine Name**: If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my-device**).</span></span> <span data-ttu-id="96723-140">否则，使用 Windows IoT 核心版设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="96723-140">Otherwise, use the IP address of your Windows IoT Core device.</span></span>
    * <span data-ttu-id="96723-141">**身份验证模式**：设置为“通用(未加密协议)”</span><span class="sxs-lookup"><span data-stu-id="96723-141">**Authentication Mode**: Set to **Universal (Unencrypted Protocol)**</span></span>
    
![通用身份验证模式](../media/AppDeployment/cpp-debug-project-properties.png)

5. <span data-ttu-id="96723-143">现在我们已准备好部署。</span><span class="sxs-lookup"><span data-stu-id="96723-143">Now we're ready to deploy.</span></span> <span data-ttu-id="96723-144">只需按 F5 (或选择调试\|开始调试) 若要开始调试我们的应用程序。</span><span class="sxs-lookup"><span data-stu-id="96723-144">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="96723-145">应该可以看到应用出现在 Windows IoT 核心版设备屏幕上。</span><span class="sxs-lookup"><span data-stu-id="96723-145">You should see the app come up in Windows IoT Core device screen.</span></span>

6. <span data-ttu-id="96723-146">部署完成后，可设置断点、查看变量值等。若要停止应用，请按停止调试按钮 (或选择调试\|停止调试)。</span><span class="sxs-lookup"><span data-stu-id="96723-146">Once deployed, you can set breakpoints, see variable values, etc. To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

7. <span data-ttu-id="96723-147">具有成功部署并调试 UWP 应用程序中，创建一个发布版本-更改 Visual Studio 工具栏配置下拉列表从`Debug`到`Release`。</span><span class="sxs-lookup"><span data-stu-id="96723-147">Having successfully deployed and debugged your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="96723-148">现在可以生成，并将应用部署到你的设备，通过选择生成\|重新生成解决方案和生成\|部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="96723-148">You can now build and deploy your app to your device by selecting Build \| Rebuild Solution and Build \| Deploy Solution.</span></span>

