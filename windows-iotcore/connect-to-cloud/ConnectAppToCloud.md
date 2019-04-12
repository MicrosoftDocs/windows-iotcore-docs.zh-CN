---
title: 将应用连接到云
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何将应用连接到云。
keywords: windows iot，云，Azure，Azure IoT 中心
ms.openlocfilehash: 3f7f50ba87e269fa8ac958f80affbd2fd0af5c53
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510881"
---
# <a name="connect-your-app-to-the-cloud"></a><span data-ttu-id="46991-104">将应用连接到云</span><span class="sxs-lookup"><span data-stu-id="46991-104">Connect your app to the cloud</span></span>

<span data-ttu-id="46991-105">本循序渐进指南将允许你以自己熟悉 Windows 10 IoT 核心版、 设置你的设备并创建第一个应用程序连接到 Azure IoT 中心。</span><span class="sxs-lookup"><span data-stu-id="46991-105">This step-by-step guide will allow you to familiarize yourself with Windows 10 IoT Core, set up your device and create your first application that connects to Azure IoT Hub.</span></span>

## <a name="step-1-prepare-your-device"></a><span data-ttu-id="46991-106">第 1 步：准备你的设备</span><span class="sxs-lookup"><span data-stu-id="46991-106">Step 1: Prepare your device</span></span>

<span data-ttu-id="46991-107">您可以找到有关如何准备你的设备上的说明[获取启动页](https://developer.microsoft.com/en-us/windows/iot/getstarted)请确保您[设置 TPM 的设备](../connect-to-cloud/ConnectDeviceToCloud.md)</span><span class="sxs-lookup"><span data-stu-id="46991-107">You can find instructions on how to prepare your device on the [Get Started Page](https://developer.microsoft.com/en-us/windows/iot/getstarted) Make sure you [provision the TPM of your device](../connect-to-cloud/ConnectDeviceToCloud.md)</span></span>

## <a name="step-2-install-visual-studio-2017-and-tools"></a><span data-ttu-id="46991-108">步骤 2：安装 Visual Studio 2017 和工具</span><span class="sxs-lookup"><span data-stu-id="46991-108">Step 2: Install Visual Studio 2017 and tools</span></span>

<span data-ttu-id="46991-109">安装[Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271)。</span><span class="sxs-lookup"><span data-stu-id="46991-109">Install [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271).</span></span> <span data-ttu-id="46991-110">可以安装任意版本的 Visual Studio 中，包括免费的 Community 版本。</span><span class="sxs-lookup"><span data-stu-id="46991-110">You can install any edition of Visual Studio, including the free Community edition.</span></span>

<span data-ttu-id="46991-111">请务必选择**通用 Windows 应用开发工具**，编写 Windows 10 应用所需的组件：</span><span class="sxs-lookup"><span data-stu-id="46991-111">Make sure to select the **Universal Windows App Development Tools**, the component required for writing apps Windows 10:</span></span>

![通用 Windows 应用开发工具](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a><span data-ttu-id="46991-113">步骤 3:安装 Azure IoT 中心的连接的服务</span><span class="sxs-lookup"><span data-stu-id="46991-113">Step 3: Install the Connected Services for Azure IoT Hub</span></span>

<span data-ttu-id="46991-114">Azure IoT 中心的 Visual Studio 扩展的连接的服务，可连接并开始在一分钟内使用 Azure IoT 中心进行交互。</span><span class="sxs-lookup"><span data-stu-id="46991-114">The Connected Services for Azure IoT Hub Visual Studio extension allows you to connect and start interacting with Azure IoT Hub in less than a minute.</span></span>

<span data-ttu-id="46991-115">可以安装中的扩展插件[VS 库](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)。</span><span class="sxs-lookup"><span data-stu-id="46991-115">You can install the extension from the [VS Gallery](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).</span></span>

## <a name="step-4-create-a-visual-studio-uwp-solution"></a><span data-ttu-id="46991-116">步骤 4：创建 Visual Studio UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="46991-116">Step 4: Create a Visual Studio UWP solution</span></span>

<span data-ttu-id="46991-117">若要创建的 UWP 解决方案在 Visual Studio 中，在**文件**菜单上，单击**新建**然后**项目**:</span><span class="sxs-lookup"><span data-stu-id="46991-117">To create a UWP solution in Visual Studio, on the **File** menu, click **New** then **Project**:</span></span>

![创建新项目](../media/ConnectAppToCloud/new_project_menu.png)

<span data-ttu-id="46991-119">在出现新建项目对话框中选择**空白应用 (通用 Windows) Visual C#** 。</span><span class="sxs-lookup"><span data-stu-id="46991-119">In the New Project dialog that comes up, select **Blank App (Universal Windows) Visual C#**.</span></span> <span data-ttu-id="46991-120">为项目名称 （例如</span><span class="sxs-lookup"><span data-stu-id="46991-120">Give your project a name (e.x.</span></span> <span data-ttu-id="46991-121">**MyFirstIoTCoreApp**):</span><span class="sxs-lookup"><span data-stu-id="46991-121">**MyFirstIoTCoreApp**):</span></span>

![新建解决方案对话框](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a><span data-ttu-id="46991-123">使用适用于 Azure IoT 中心的连接服务连接到 Azure IoT 中心</span><span class="sxs-lookup"><span data-stu-id="46991-123">Use the Connected Services for Azure IoT Hub to connect to Azure IoT Hub</span></span>

<span data-ttu-id="46991-124">请按照中的说明[连接服务工具](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)以将项目连接到 Azure IoT 中心。</span><span class="sxs-lookup"><span data-stu-id="46991-124">Follow the instructions from the [Connected Services tool](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) to connect your project to Azure IoT Hub.</span></span> <span data-ttu-id="46991-125">此工具将生成两个函数`SendDeviceToCloudMessageAsync`和`ReceiveCloudToDeviceMessageAsync`，可以在应用中任意位置调用。</span><span class="sxs-lookup"><span data-stu-id="46991-125">The tool will generate two functions, `SendDeviceToCloudMessageAsync` and `ReceiveCloudToDeviceMessageAsync` that you can invoke anywhere in your app.</span></span> <span data-ttu-id="46991-126">根据需要，您可以修改这些函数。</span><span class="sxs-lookup"><span data-stu-id="46991-126">You can modify these functions as you see fit.</span></span>  

