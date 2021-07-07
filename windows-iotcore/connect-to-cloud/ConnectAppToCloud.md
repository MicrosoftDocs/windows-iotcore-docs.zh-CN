---
title: 连接应用到云
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 连接你的应用程序到云。 准备好设备、为 Azure IoT 中心安装 VS 和连接的服务，创建 UWP 解决方案，然后连接到 Azure IoT 中心。
keywords: windows iot，cloud，Azure，Azure IoT 中心
ms.openlocfilehash: dcad788087c930ff1ea305b530421532e24a08ff
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230104"
---
# <a name="connect-your-app-to-the-cloud"></a><span data-ttu-id="93654-105">连接应用到云</span><span class="sxs-lookup"><span data-stu-id="93654-105">Connect your app to the cloud</span></span>

<span data-ttu-id="93654-106">此循序渐进指南使你可以熟悉 Windows 10 IoT 核心版、设置设备以及创建连接到 Azure IoT 中心的第一个应用程序。</span><span class="sxs-lookup"><span data-stu-id="93654-106">This step-by-step guide will allow you to familiarize yourself with Windows 10 IoT Core, set up your device and create your first application that connects to Azure IoT Hub.</span></span>

## <a name="step-1-prepare-your-device"></a><span data-ttu-id="93654-107">步骤1：准备设备</span><span class="sxs-lookup"><span data-stu-id="93654-107">Step 1: Prepare your device</span></span>

<span data-ttu-id="93654-108">你可以在[入门 "页](https://developer.microsoft.com/en-us/windows/iot/getstarted)上找到有关如何准备设备的说明，请确保[预配设备的 TPM](../connect-to-cloud/ConnectDeviceToCloud.md)</span><span class="sxs-lookup"><span data-stu-id="93654-108">You can find instructions on how to prepare your device on the [Get Started Page](https://developer.microsoft.com/en-us/windows/iot/getstarted) Make sure you [provision the TPM of your device](../connect-to-cloud/ConnectDeviceToCloud.md)</span></span>

## <a name="step-2-install-visual-studio-2017-and-tools"></a><span data-ttu-id="93654-109">步骤2：安装 Visual Studio 2017 和工具</span><span class="sxs-lookup"><span data-stu-id="93654-109">Step 2: Install Visual Studio 2017 and tools</span></span>

<span data-ttu-id="93654-110">安装[2017 Visual Studio](https://go.microsoft.com/fwlink/?linkid=845271)。</span><span class="sxs-lookup"><span data-stu-id="93654-110">Install [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271).</span></span> <span data-ttu-id="93654-111">可以安装任意版本的 Visual Studio，包括免费的 Community 版。</span><span class="sxs-lookup"><span data-stu-id="93654-111">You can install any edition of Visual Studio, including the free Community edition.</span></span>

<span data-ttu-id="93654-112">请确保选择 **通用 Windows 应用开发工具**、编写应用所需的组件 Windows 10：</span><span class="sxs-lookup"><span data-stu-id="93654-112">Make sure to select the **Universal Windows App Development Tools**, the component required for writing apps Windows 10:</span></span>

![通用 Windows 应用开发工具](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a><span data-ttu-id="93654-114">步骤3：安装 Azure IoT 中心的连接的服务</span><span class="sxs-lookup"><span data-stu-id="93654-114">Step 3: Install the Connected Services for Azure IoT Hub</span></span>

<span data-ttu-id="93654-115">使用 Azure IoT 中心 Visual Studio 扩展的连接的服务，可以在不到一分钟的时间内连接和开始与 Azure IoT 集线器交互。</span><span class="sxs-lookup"><span data-stu-id="93654-115">The Connected Services for Azure IoT Hub Visual Studio extension allows you to connect and start interacting with Azure IoT Hub in less than a minute.</span></span>

<span data-ttu-id="93654-116">你可以从 [VS 库](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)中安装该扩展。</span><span class="sxs-lookup"><span data-stu-id="93654-116">You can install the extension from the [VS Gallery](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).</span></span>

## <a name="step-4-create-a-visual-studio-uwp-solution"></a><span data-ttu-id="93654-117">步骤4：创建 Visual Studio UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="93654-117">Step 4: Create a Visual Studio UWP solution</span></span>

<span data-ttu-id="93654-118">若要在 Visual Studio 中创建 UWP 解决方案，请在 "**文件**" 菜单上单击 "**新建**"，然后 **Project**：</span><span class="sxs-lookup"><span data-stu-id="93654-118">To create a UWP solution in Visual Studio, on the **File** menu, click **New** then **Project**:</span></span>

![新 Project 创建](../media/ConnectAppToCloud/new_project_menu.png)

<span data-ttu-id="93654-120">在出现的 "新建 Project" 对话框中，选择 "**空白应用程序" (通用 Windows) Visual c #**。</span><span class="sxs-lookup"><span data-stu-id="93654-120">In the New Project dialog that comes up, select **Blank App (Universal Windows) Visual C#**.</span></span> <span data-ttu-id="93654-121">为项目指定名称 (e.x。</span><span class="sxs-lookup"><span data-stu-id="93654-121">Give your project a name (e.x.</span></span> <span data-ttu-id="93654-122">**MyFirstIoTCoreApp**) ：</span><span class="sxs-lookup"><span data-stu-id="93654-122">**MyFirstIoTCoreApp**):</span></span>

![新建解决方案对话框](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a><span data-ttu-id="93654-124">使用连接的服务 Azure IoT 中心连接到 Azure IoT 中心</span><span class="sxs-lookup"><span data-stu-id="93654-124">Use the Connected Services for Azure IoT Hub to connect to Azure IoT Hub</span></span>

<span data-ttu-id="93654-125">按照[连接的服务工具](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)中的说明将项目连接到 Azure IoT 中心。</span><span class="sxs-lookup"><span data-stu-id="93654-125">Follow the instructions from the [Connected Services tool](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) to connect your project to Azure IoT Hub.</span></span> <span data-ttu-id="93654-126">该工具将生成两个函数， `SendDeviceToCloudMessageAsync` 并且 `ReceiveCloudToDeviceMessageAsync` 可以在应用中的任意位置调用。</span><span class="sxs-lookup"><span data-stu-id="93654-126">The tool will generate two functions, `SendDeviceToCloudMessageAsync` and `ReceiveCloudToDeviceMessageAsync` that you can invoke anywhere in your app.</span></span> <span data-ttu-id="93654-127">您可以根据需要修改这些函数。</span><span class="sxs-lookup"><span data-stu-id="93654-127">You can modify these functions as you see fit.</span></span>  

