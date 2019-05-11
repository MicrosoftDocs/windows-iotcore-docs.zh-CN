---
title: 使用 Visual Studio 部署应用
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Visual Studio 远程调试功能部署应用。
keywords: windows iot、 visual studio、 应用部署、 远程调试
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533354"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="331e3-104">使用 Visual Studio 部署应用</span><span class="sxs-lookup"><span data-stu-id="331e3-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="331e3-105">使用 Visual Studio 部署和调试应用程序很简单。</span><span class="sxs-lookup"><span data-stu-id="331e3-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="331e3-106">我们将使用**远程调试**功能将应用部署到本地连接的 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="331e3-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="331e3-107">部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。</span><span class="sxs-lookup"><span data-stu-id="331e3-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="331e3-108">若要使用远程调试，必须首先将 IoT Core 设备连接到进行开发的电脑与位于同一本地网络，应在网络上允许 UDP/TCP 通信。</span><span class="sxs-lookup"><span data-stu-id="331e3-108">In order to use remote debugging, your IoT Core device must first be connected to the same local network as your development PC and UDP/TCP communications should be allowed on the network.</span></span> <span data-ttu-id="331e3-109">如果在有任何疑问，请与您的 IT 上允许的网络流量。</span><span class="sxs-lookup"><span data-stu-id="331e3-109">If in doubt, check with your IT on allowed network traffic.</span></span> <span data-ttu-id="331e3-110">请参阅[连接到的设备](../connect-your-device/SetupWiFi.md)有关的说明。</span><span class="sxs-lookup"><span data-stu-id="331e3-110">See [Connecting to a device](../connect-your-device/SetupWiFi.md) for instructions.</span></span>

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a><span data-ttu-id="331e3-111">将应用部署到 Windows 10 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="331e3-111">Deploy apps to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="331e3-112">应用程序在 Visual Studio 中打开后，在工具栏下拉列表中设置体系结构。</span><span class="sxs-lookup"><span data-stu-id="331e3-112">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="331e3-113">如果您正在构建的 Minnowboard 最大，则选择`x86`。</span><span class="sxs-lookup"><span data-stu-id="331e3-113">If you're building for a Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="331e3-114">如果您正在构建为 Raspberry Pi 2、 Raspberry Pi 3 或 Dragonboard，选择`ARM`。</span><span class="sxs-lookup"><span data-stu-id="331e3-114">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="331e3-115">接下来，在 Visual Studio 工具栏中，单击`Local Machine`下拉列表中，然后选择`Remote Machine`。</span><span class="sxs-lookup"><span data-stu-id="331e3-115">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![在 Visual Studio 中的远程计算机](../media/AppDeployment/remote-vs.png)

3. <span data-ttu-id="331e3-117">此时，Visual Studio 将显示“远程连接”对话框。</span><span class="sxs-lookup"><span data-stu-id="331e3-117">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="331e3-118">如果以前使用过[PowerShell](../connect-your-device/PowerShell.md)若要设置你的设备的唯一名称，您可以在此处输入 (在此示例中，我们使用**我的设备**)。</span><span class="sxs-lookup"><span data-stu-id="331e3-118">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="331e3-119">否则，使用 Windows IoT 核心版设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="331e3-119">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="331e3-120">输入设备名称/IP 后选择`Universal (Unencrypted Protocol)`身份验证模式，然后单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="331e3-120">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![通用身份验证模式](../media/AppDeployment/remote-connections.png)

<span data-ttu-id="331e3-122">可通过导航到项目属性（在解决方案资源管理器中选择“属性”）并在左侧选择 `Debug` 选项卡来验证或修改这些值：</span><span class="sxs-lookup"><span data-stu-id="331e3-122">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![“调试”选项卡](../media/AppDeployment/debug-tab.png)

5. <span data-ttu-id="331e3-124">现在我们已准备好部署。</span><span class="sxs-lookup"><span data-stu-id="331e3-124">Now we're ready to deploy.</span></span> <span data-ttu-id="331e3-125">只需按 F5（或依次选择“调试”|“启动调试”）即可开始调试应用。</span><span class="sxs-lookup"><span data-stu-id="331e3-125">Simply press F5 (or select Debug | Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="331e3-126">你应该会看到你的设备的屏幕上显示应用。</span><span class="sxs-lookup"><span data-stu-id="331e3-126">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="331e3-127">部署完成后，可设置断点、查看变量值等。若要停止应用程序按停止调试按钮 (或选择调试 |停止调试）。</span><span class="sxs-lookup"><span data-stu-id="331e3-127">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug | Stop Debugging).</span></span>

7. <span data-ttu-id="331e3-128">已成功部署和调试 UWP 应用程序，创建的发布版本的后更改 Visual Studio 工具栏配置下拉列表从`Debug`到`Release`。</span><span class="sxs-lookup"><span data-stu-id="331e3-128">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="331e3-129">现在，可通过依次选择“生成”|“重新生成解决方案”和“生成”|“部署解决方案”，生成应用并将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="331e3-129">You can now build and deploy your app to your device by selecting Build | Rebuild Solution and Build | Deploy Solution.</span></span>
