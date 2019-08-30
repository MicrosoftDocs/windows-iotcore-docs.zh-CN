---
title: 使用远程控制台应用调试调试应用
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/17
ms.topic: article
description: 了解如何在 Visual Studio 中远程调试 IoT 核心控制台应用程序。
keywords: windows iot, visual studio, 应用部署, 远程调试
ms.openlocfilehash: dc3afad193bc6356a5f897f386f5061adaf6bc01
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170526"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a><span data-ttu-id="73a26-104">使用远程控制台应用调试调试应用</span><span class="sxs-lookup"><span data-stu-id="73a26-104">Debug your app using Remote Console App Debugging</span></span>

<span data-ttu-id="73a26-105">下面介绍如何在 Visual Studio 中远程调试 IoT 核心控制台应用程序:</span><span class="sxs-lookup"><span data-stu-id="73a26-105">Here's how to debug your IoT Core console application remotely in Visual Studio:</span></span>

* <span data-ttu-id="73a26-106">首先，需要在 Windows IoT 核心版设备上设置远程调试器。</span><span class="sxs-lookup"><span data-stu-id="73a26-106">You will first need to setup the Remote Debugger on your Windows IoT Core device.</span></span> <span data-ttu-id="73a26-107">首先, 请按照[此处](AppDeployment.md)的步骤在设备上部署任何其他通用 Windows 应用程序 (尝试 HelloWorld 项目)。</span><span class="sxs-lookup"><span data-stu-id="73a26-107">First follow the steps [here](AppDeployment.md) to deploy any other Universal Windows Application on your device (try the HelloWorld project).</span></span> <span data-ttu-id="73a26-108">这会将所有必需的二进制文件复制到你的设备。</span><span class="sxs-lookup"><span data-stu-id="73a26-108">This will copy all the required binaries to your device.</span></span> 

* <span data-ttu-id="73a26-109">若要在设备上启动远程调试器, 请在电脑上打开 Web 浏览器, 并将`http://<device name/IP address>:8080`其指向以启动[Windows 设备门户](../manage-your-device/DevicePortal.md)。</span><span class="sxs-lookup"><span data-stu-id="73a26-109">To start the remote debugger on your device, open a Web Browser on your PC and point it to `http://<device name/IP address>:8080` to launch [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="73a26-110">在凭据对话框中，使用默认的用户名和密码：`Administrator`，`p@ssw0rd`。</span><span class="sxs-lookup"><span data-stu-id="73a26-110">In the credentials dialog, use the default username and password: `Administrator`, `p@ssw0rd`.</span></span> <span data-ttu-id="73a26-111">Windows 设备管理应启动并显示 Web 管理主屏幕。</span><span class="sxs-lookup"><span data-stu-id="73a26-111">Windows Device Management should launch and display the web management home screen.</span></span>

* <span data-ttu-id="73a26-112">现在, 导航到 Windows 设备门户的 "调试设置" 部分, 然后单击 "开始 Visual Studio 远程调试器下的" 开始 "按钮。</span><span class="sxs-lookup"><span data-stu-id="73a26-112">Now navigate to the Debug settings section of Windows Device Portal and click the Start button under Start Visual Studio Remote Debugger.</span></span> 

    ![WindowsDevicePortalDebugSettings 启动远程调试器](../media/Console/device_portal_start_debugger.png)

* <span data-ttu-id="73a26-114">这将弹出一个消息框并提供连接信息。</span><span class="sxs-lookup"><span data-stu-id="73a26-114">This will show pop-up a message box and give you the connection information.</span></span> 

*  <span data-ttu-id="73a26-115">在 Visual Studio 中，你可以通过编辑项目的属性配置你的目标（请确保所有突出显示的更改均适用于开发板的名称或 IP 地址）：</span><span class="sxs-lookup"><span data-stu-id="73a26-115">In Visual Studio, you can configure your target by editing your project's properties (be sure to make all of the highlighted changes as appropriate to your board's name or IP address):</span></span>

    ![控制台应用程序远程计算机项目设置](../media/Console/console_project_settings.png)
    
> [!NOTE]
> <span data-ttu-id="73a26-117">如果未看到上述图像, 请前往上下文菜单中的 "解决方案资源管理器", 并进入 "项目属性"。</span><span class="sxs-lookup"><span data-stu-id="73a26-117">If you're not seeing the image above, please go to the "Solution Explorer" in the context menu, and go to "Project Properties".</span></span> <span data-ttu-id="73a26-118">可在[此处](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)找到有关项目属性的详细信息。</span><span class="sxs-lookup"><span data-stu-id="73a26-118">You can find more information for project properties [here](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).</span></span>

> [!TIP]
> <span data-ttu-id="73a26-119">你可以使用 IP 地址而不使用 Windows IoT 核心版设备名称。</span><span class="sxs-lookup"><span data-stu-id="73a26-119">You can use the IP address instead of the Windows IoT Core device name.</span></span>

* <span data-ttu-id="73a26-120">项目配置需修改为启用部署。</span><span class="sxs-lookup"><span data-stu-id="73a26-120">The project configuration needs to be modified to enable deployment.</span></span>  <span data-ttu-id="73a26-121">为此，请从工具栏的“解决方案配置”下拉菜单中选择“配置管理器”，以打开配置管理器。</span><span class="sxs-lookup"><span data-stu-id="73a26-121">To do this, open the Configuration Manager by selecting the Configuration manger from the Solution Configuration drop-down menu on the toolbar.</span></span>

    ![控制台应用程序 SolutionConfiguration](../media/Console/configuration_management.png)

    <span data-ttu-id="73a26-123">在配置管理器中，确保已针对自己的项目配置选中了“部署”复选框（如果此选项处于禁用状态，则很可能是因为部署选项未全部输入到项目属性的“调试”选项卡中）</span><span class="sxs-lookup"><span data-stu-id="73a26-123">From the Configuration Manager, ensure that the Deploy checkbox is selected for your project configuration (if this options is disabled, it is likely that the deployment options have not been fully entered into the Debugging tab of the project properties)</span></span>

    ![控制台应用程序远程计算机项目设置](../media/Console/deploy_checkbox.png)

* <span data-ttu-id="73a26-125">现在，我们可以随时部署到远程 Windows IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="73a26-125">Now we're ready to deploy to the remote Windows IoT Core device.</span></span> <span data-ttu-id="73a26-126">只需按 F5 (或选择\| "调试" "开始调试") 即可开始调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="73a26-126">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="73a26-127">你还可以使用生成\|部署解决方案来部署应用程序, 而无需启动调试会话。</span><span class="sxs-lookup"><span data-stu-id="73a26-127">You can also use Build \| Deploy Solution to simply deploy your application without starting a debug session.</span></span>

> [!NOTE]
> <span data-ttu-id="73a26-128">在 Visual Studio 中运行时, 输出将不会显示在任何位置, 但你将能够设置断点、查看变量值等。</span><span class="sxs-lookup"><span data-stu-id="73a26-128">When run from Visual Studio, the output will not display anywhere, but you will be able to set breakpoints, see variable values, etc.</span></span>

* <span data-ttu-id="73a26-129">若要停止应用, 请按 "停止调试" 按钮 (或选择 "调试\| " "停止调试")。</span><span class="sxs-lookup"><span data-stu-id="73a26-129">To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

* <span data-ttu-id="73a26-130">你现在可以运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="73a26-130">You can now run the application.</span></span>  <span data-ttu-id="73a26-131">只需打开 PowerShell/SSH 连接 ([对于 PowerShell](../connect-your-device/PowerShell.md) , 可以在此处找到有关[SSH](../connect-your-device/SSH.md)的说明), 然后输入前面指定的远程命令。</span><span class="sxs-lookup"><span data-stu-id="73a26-131">Simply open a PowerShell/SSH connection (instructions can be found [here for PowerShell](../connect-your-device/PowerShell.md) and [here for SSH](../connect-your-device/SSH.md)) and enter the Remote Command you specified above.</span></span>

    ![控制台应用程序输出](../media/Console/console_output.png)

* <span data-ttu-id="73a26-133">调试完应用程序后, 请记得在 Windows IoT Core 设备上停止远程调试器。</span><span class="sxs-lookup"><span data-stu-id="73a26-133">Once you are done debugging your application, remember to stop the remote debugger on the Windows IoT Core device.</span></span> <span data-ttu-id="73a26-134">要执行此操作, 可以导航到 Windows 设备门户的 "调试设置" 部分, 然后单击 "停止远程调试器" 按钮。</span><span class="sxs-lookup"><span data-stu-id="73a26-134">You can do this by navigating to Debug settings section of Windows Device Portal and clicking on the Stop Remote Debugger button.</span></span>

    ![WindowsDevicePortalDebugSettings 停止远程调试器](../media/Console/device_portal_stop_debugger.PNG)

