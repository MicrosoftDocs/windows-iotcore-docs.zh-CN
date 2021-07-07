---
title: 使用应用程序部署Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用远程调试功能Visual Studio应用。
keywords: windows iot， visual studio， 应用部署， 远程调试
ms.openlocfilehash: 57132a4c249e21d319d481077851ea8655b2740f
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229133"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="39a4f-104">使用应用程序部署Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39a4f-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="39a4f-105">部署和调试应用程序非常简单，Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="39a4f-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="39a4f-106">我们将使用远程 **调试** 功能将应用部署到本地连接Windows 10 IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="39a4f-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="39a4f-107">在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="39a4f-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="39a4f-108">若要使用远程调试，必须先将 IoT 核心设备连接到与开发电脑相同的本地网络，并且应在网络中允许 UDP/TCP 通信。</span><span class="sxs-lookup"><span data-stu-id="39a4f-108">In order to use remote debugging, your IoT Core device must first be connected to the same local network as your development PC and UDP/TCP communications should be allowed on the network.</span></span> <span data-ttu-id="39a4f-109">如果有疑问，请咨询 IT 部门，了解允许的网络流量。</span><span class="sxs-lookup"><span data-stu-id="39a4f-109">If in doubt, check with your IT on allowed network traffic.</span></span> <span data-ttu-id="39a4f-110">有关 [说明，请参阅连接到](../connect-your-device/SetupWiFi.md) 设备。</span><span class="sxs-lookup"><span data-stu-id="39a4f-110">See [Connecting to a device](../connect-your-device/SetupWiFi.md) for instructions.</span></span>

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a><span data-ttu-id="39a4f-111">将应用部署到 Windows 10 IoT 核心版 设备</span><span class="sxs-lookup"><span data-stu-id="39a4f-111">Deploy apps to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="39a4f-112">在应用程序打开Visual Studio，在工具栏下拉列表中设置体系结构。</span><span class="sxs-lookup"><span data-stu-id="39a4f-112">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="39a4f-113">如果要为 Minnowboard Max 生成 ，请选择 `x86` 。</span><span class="sxs-lookup"><span data-stu-id="39a4f-113">If you're building for a Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="39a4f-114">如果要为 Raspberry Pi 2、Raspberry Pi 3 或 Dragonboard 生成，请选择 `ARM` 。</span><span class="sxs-lookup"><span data-stu-id="39a4f-114">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="39a4f-115">接下来，在Visual Studio工具栏中，单击 `Local Machine` 下拉列表并选择 `Remote Machine` 。</span><span class="sxs-lookup"><span data-stu-id="39a4f-115">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![远程计算机Visual Studio](../media/AppDeployment/remote-vs.png)

3. <span data-ttu-id="39a4f-117">此时，Visual Studio"远程 **连接"** 对话框。</span><span class="sxs-lookup"><span data-stu-id="39a4f-117">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="39a4f-118">如果以前使用 [PowerShell](../connect-your-device/PowerShell.md) 为设备设置唯一名称，可以在此处输入该名称 (本示例中，我们将使用我的 **设备**) 。</span><span class="sxs-lookup"><span data-stu-id="39a4f-118">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="39a4f-119">否则，请使用 IoT 核心Windows IP 地址。</span><span class="sxs-lookup"><span data-stu-id="39a4f-119">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="39a4f-120">输入设备名称/IP 后，选择" `Universal (Unencrypted Protocol)` 身份验证模式"，然后单击"选择 **"。**</span><span class="sxs-lookup"><span data-stu-id="39a4f-120">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![通用身份验证模式](../media/AppDeployment/remote-connections.png)

<span data-ttu-id="39a4f-122">可以通过导航到项目属性来验证或修改这些值， (**选择"** 属性解决方案资源管理器) 并选择左侧 `Debug` 的选项卡：</span><span class="sxs-lookup"><span data-stu-id="39a4f-122">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![“调试”选项卡](../media/AppDeployment/debug-tab.png)

5. <span data-ttu-id="39a4f-124">现在，我们已准备好进行部署。</span><span class="sxs-lookup"><span data-stu-id="39a4f-124">Now we're ready to deploy.</span></span> <span data-ttu-id="39a4f-125">只需按 F5 (或选择"调试|启动调试) 开始调试应用。</span><span class="sxs-lookup"><span data-stu-id="39a4f-125">Simply press F5 (or select Debug | Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="39a4f-126">应会看到应用在设备的屏幕上显示。</span><span class="sxs-lookup"><span data-stu-id="39a4f-126">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="39a4f-127">部署后，可以设置断点、查看变量值等。若要停止应用，请按"停止调试"按钮 (或选择"调试|停止调试) 。</span><span class="sxs-lookup"><span data-stu-id="39a4f-127">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug | Stop Debugging).</span></span>

7. <span data-ttu-id="39a4f-128">成功部署和调试 UWP 应用程序后，创建发布版本 - 将Visual Studio工具栏配置下拉列表从 `Debug` 更改为 `Release` 。</span><span class="sxs-lookup"><span data-stu-id="39a4f-128">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="39a4f-129">现在，可以通过选择"生成应用"来生成应用，|重新生成解决方案和生成|部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="39a4f-129">You can now build and deploy your app to your device by selecting Build | Rebuild Solution and Build | Deploy Solution.</span></span>
