---
title: 使用 Visual Studio 部署应用
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Visual Studio 远程调试功能部署应用。
keywords: windows iot，visual studio，应用部署，远程调试
ms.openlocfilehash: ca9568bccd32cbcd06edf35fc5b89b7a4cd4caae
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656493"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="e0a68-104">使用 Visual Studio 部署应用</span><span class="sxs-lookup"><span data-stu-id="e0a68-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="e0a68-105">部署和调试应用程序与 Visual Studio 非常直接。</span><span class="sxs-lookup"><span data-stu-id="e0a68-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="e0a68-106">我们将使用 **远程调试** 功能将应用程序部署到本地连接的 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="e0a68-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="e0a68-107">在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="e0a68-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="e0a68-108">若要使用远程调试，IoT Core 设备必须首先连接到与开发计算机相同的本地网络，并在网络上允许 UDP/TCP 通信。</span><span class="sxs-lookup"><span data-stu-id="e0a68-108">In order to use remote debugging, your IoT Core device must first be connected to the same local network as your development PC and UDP/TCP communications should be allowed on the network.</span></span> <span data-ttu-id="e0a68-109">如果有疑问，请检查是否存在允许的网络流量。</span><span class="sxs-lookup"><span data-stu-id="e0a68-109">If in doubt, check with your IT on allowed network traffic.</span></span> <span data-ttu-id="e0a68-110">有关说明，请参阅 [连接到设备](../connect-your-device/SetupWiFi.md) 。</span><span class="sxs-lookup"><span data-stu-id="e0a68-110">See [Connecting to a device](../connect-your-device/SetupWiFi.md) for instructions.</span></span>

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a><span data-ttu-id="e0a68-111">将应用部署到 Windows 10 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="e0a68-111">Deploy apps to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="e0a68-112">在 Visual Studio 中打开应用程序后，在工具栏下拉列表中设置体系结构。</span><span class="sxs-lookup"><span data-stu-id="e0a68-112">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="e0a68-113">如果要生成 Minnowboard Max，请选择 `x86` 。</span><span class="sxs-lookup"><span data-stu-id="e0a68-113">If you're building for a Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="e0a68-114">如果要生成 Raspberry Pi 2、Raspberry Pi 3 或 Dragonboard，请选择 `ARM` 。</span><span class="sxs-lookup"><span data-stu-id="e0a68-114">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="e0a68-115">接下来，在 Visual Studio 工具栏中，单击 `Local Machine` 下拉列表并选择 `Remote Machine` 。</span><span class="sxs-lookup"><span data-stu-id="e0a68-115">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![Visual Studio 中的远程计算机](../media/AppDeployment/remote-vs.png)

3. <span data-ttu-id="e0a68-117">此时，Visual Studio 将显示 " **远程连接** " 对话框。</span><span class="sxs-lookup"><span data-stu-id="e0a68-117">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="e0a68-118">如果你以前使用 [PowerShell](../connect-your-device/PowerShell.md) 为你的设备设置唯一名称，则可以在此处输入该名称 (在本示例中，我们使用的是 **设备**) 。</span><span class="sxs-lookup"><span data-stu-id="e0a68-118">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="e0a68-119">否则，请使用 Windows IoT 核心设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e0a68-119">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="e0a68-120">输入设备名称/ip 后，选择 " `Universal (Unencrypted Protocol)` 身份验证模式"，然后单击 " **选择**"。</span><span class="sxs-lookup"><span data-stu-id="e0a68-120">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![通用身份验证模式](../media/AppDeployment/remote-connections.png)

<span data-ttu-id="e0a68-122">可以通过导航到 "项目属性" 来验证或修改这些值， (在解决方案资源管理器) 选择 " **属性** "，然后选择 `Debug` 左侧的选项卡：</span><span class="sxs-lookup"><span data-stu-id="e0a68-122">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![“调试”选项卡](../media/AppDeployment/debug-tab.png)

5. <span data-ttu-id="e0a68-124">现在，我们已准备好进行部署。</span><span class="sxs-lookup"><span data-stu-id="e0a68-124">Now we're ready to deploy.</span></span> <span data-ttu-id="e0a68-125">只需按 F5 (或选择 "调试" |开始调试) ，开始调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="e0a68-125">Simply press F5 (or select Debug | Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="e0a68-126">你应看到该应用程序出现在设备屏幕上。</span><span class="sxs-lookup"><span data-stu-id="e0a68-126">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="e0a68-127">部署后，可以设置断点、查看变量值等。若要停止应用，请按 "停止调试" 按钮 (或选择 "调试" |停止调试) 。</span><span class="sxs-lookup"><span data-stu-id="e0a68-127">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug | Stop Debugging).</span></span>

7. <span data-ttu-id="e0a68-128">成功部署和调试 UWP 应用程序后，创建发布版本-将 Visual Studio 工具栏配置下拉列表从更改 `Debug` 为 `Release` 。</span><span class="sxs-lookup"><span data-stu-id="e0a68-128">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="e0a68-129">你现在可以通过选择 "生成" |重新生成解决方案和生成 |部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="e0a68-129">You can now build and deploy your app to your device by selecting Build | Rebuild Solution and Build | Deploy Solution.</span></span>
