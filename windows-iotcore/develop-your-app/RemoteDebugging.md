---
title: 使用远程控制台应用程序调试调试应用
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/17
ms.topic: article
description: 了解如何在 Visual Studio 中的远程 IoT Core 控制台应用程序进行远程调试。
keywords: windows iot、 visual studio、 应用部署、 远程调试
ms.openlocfilehash: dc3afad193bc6356a5f897f386f5061adaf6bc01
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510766"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a><span data-ttu-id="d5f55-104">使用远程控制台应用程序调试调试应用</span><span class="sxs-lookup"><span data-stu-id="d5f55-104">Debug your app using Remote Console App Debugging</span></span>

<span data-ttu-id="d5f55-105">下面介绍了如何调试在 Visual Studio 中的远程 IoT Core 控制台应用程序：</span><span class="sxs-lookup"><span data-stu-id="d5f55-105">Here's how to debug your IoT Core console application remotely in Visual Studio:</span></span>

* <span data-ttu-id="d5f55-106">首先，需要在 Windows IoT 核心版设备上设置远程调试器。</span><span class="sxs-lookup"><span data-stu-id="d5f55-106">You will first need to setup the Remote Debugger on your Windows IoT Core device.</span></span> <span data-ttu-id="d5f55-107">首先按照步骤[此处](AppDeployment.md)部署任何其他通用 Windows 应用程序在你的设备 （尝试 HelloWorld 项目）。</span><span class="sxs-lookup"><span data-stu-id="d5f55-107">First follow the steps [here](AppDeployment.md) to deploy any other Universal Windows Application on your device (try the HelloWorld project).</span></span> <span data-ttu-id="d5f55-108">这会将所有必需的二进制文件复制到你的设备。</span><span class="sxs-lookup"><span data-stu-id="d5f55-108">This will copy all the required binaries to your device.</span></span> 

* <span data-ttu-id="d5f55-109">若要在设备上启动远程调试器，打开您的 PC 上的 Web 浏览器并之指向`http://<device name/IP address>:8080`以启动[Windows Device Portal](../manage-your-device/DevicePortal.md)。</span><span class="sxs-lookup"><span data-stu-id="d5f55-109">To start the remote debugger on your device, open a Web Browser on your PC and point it to `http://<device name/IP address>:8080` to launch [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="d5f55-110">在凭据对话框中，使用默认的用户名和密码：`Administrator`，`p@ssw0rd`。</span><span class="sxs-lookup"><span data-stu-id="d5f55-110">In the credentials dialog, use the default username and password: `Administrator`, `p@ssw0rd`.</span></span> <span data-ttu-id="d5f55-111">Windows 设备管理应启动并显示 Web 管理主屏幕。</span><span class="sxs-lookup"><span data-stu-id="d5f55-111">Windows Device Management should launch and display the web management home screen.</span></span>

* <span data-ttu-id="d5f55-112">现在导航到 Windows Device Portal 调试设置部分并单击开始按钮下启动 Visual Studio 远程调试器。</span><span class="sxs-lookup"><span data-stu-id="d5f55-112">Now navigate to the Debug settings section of Windows Device Portal and click the Start button under Start Visual Studio Remote Debugger.</span></span> 

    ![WindowsDevicePortalDebugSettings 启动远程调试器](../media/Console/device_portal_start_debugger.png)

* <span data-ttu-id="d5f55-114">这将弹出一个消息框并提供连接信息。</span><span class="sxs-lookup"><span data-stu-id="d5f55-114">This will show pop-up a message box and give you the connection information.</span></span> 

*  <span data-ttu-id="d5f55-115">在 Visual Studio 中，你可以通过编辑项目的属性配置你的目标（请确保所有突出显示的更改均适用于开发板的名称或 IP 地址）：</span><span class="sxs-lookup"><span data-stu-id="d5f55-115">In Visual Studio, you can configure your target by editing your project's properties (be sure to make all of the highlighted changes as appropriate to your board's name or IP address):</span></span>

    ![控制台应用程序远程计算机项目设置](../media/Console/console_project_settings.png)
    
> [!NOTE]
> <span data-ttu-id="d5f55-117">如果你看不到上面的图像，请转到"解决方案资源管理器"上下文菜单中，转到"项目属性"。</span><span class="sxs-lookup"><span data-stu-id="d5f55-117">If you're not seeing the image above, please go to the "Solution Explorer" in the context menu, and go to "Project Properties".</span></span> <span data-ttu-id="d5f55-118">你可以找到有关项目属性的详细信息[此处](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)。</span><span class="sxs-lookup"><span data-stu-id="d5f55-118">You can find more information for project properties [here](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).</span></span>

> [!TIP]
> <span data-ttu-id="d5f55-119">你可以使用 IP 地址而不使用 Windows IoT 核心版设备名称。</span><span class="sxs-lookup"><span data-stu-id="d5f55-119">You can use the IP address instead of the Windows IoT Core device name.</span></span>

* <span data-ttu-id="d5f55-120">项目配置需修改为启用部署。</span><span class="sxs-lookup"><span data-stu-id="d5f55-120">The project configuration needs to be modified to enable deployment.</span></span>  <span data-ttu-id="d5f55-121">为此，请从工具栏的“解决方案配置”下拉菜单中选择“配置管理器”，以打开配置管理器。</span><span class="sxs-lookup"><span data-stu-id="d5f55-121">To do this, open the Configuration Manager by selecting the Configuration manger from the Solution Configuration drop-down menu on the toolbar.</span></span>

    ![ConsoleApplication SolutionConfiguration](../media/Console/configuration_management.png)

    <span data-ttu-id="d5f55-123">在配置管理器中，确保已针对自己的项目配置选中了“部署”复选框（如果此选项处于禁用状态，则很可能是因为部署选项未全部输入到项目属性的“调试”选项卡中）</span><span class="sxs-lookup"><span data-stu-id="d5f55-123">From the Configuration Manager, ensure that the Deploy checkbox is selected for your project configuration (if this options is disabled, it is likely that the deployment options have not been fully entered into the Debugging tab of the project properties)</span></span>

    ![控制台应用程序远程计算机项目设置](../media/Console/deploy_checkbox.png)

* <span data-ttu-id="d5f55-125">现在，我们可以随时部署到远程 Windows IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="d5f55-125">Now we're ready to deploy to the remote Windows IoT Core device.</span></span> <span data-ttu-id="d5f55-126">只需按 F5 (或选择调试\|开始调试) 若要开始调试我们的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d5f55-126">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="d5f55-127">你还可以使用生成\|部署解决方案，只需将应用程序部署而无需启动调试会话。</span><span class="sxs-lookup"><span data-stu-id="d5f55-127">You can also use Build \| Deploy Solution to simply deploy your application without starting a debug session.</span></span>

> [!NOTE]
> <span data-ttu-id="d5f55-128">从 Visual Studio 运行时，输出将不显示任何位置，但您将能够设置断点，请参阅变量值，等等。</span><span class="sxs-lookup"><span data-stu-id="d5f55-128">When run from Visual Studio, the output will not display anywhere, but you will be able to set breakpoints, see variable values, etc.</span></span>

* <span data-ttu-id="d5f55-129">若要停止应用，请按停止调试按钮 (或选择调试\|停止调试)。</span><span class="sxs-lookup"><span data-stu-id="d5f55-129">To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

* <span data-ttu-id="d5f55-130">你现在可以运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="d5f55-130">You can now run the application.</span></span>  <span data-ttu-id="d5f55-131">只需打开的 PowerShell/SSH 连接。 (可以找到说明[在此处供 PowerShell](../connect-your-device/PowerShell.md)和[在此处供 SSH](../connect-your-device/SSH.md))，然后输入上面指定的远程命令。</span><span class="sxs-lookup"><span data-stu-id="d5f55-131">Simply open a PowerShell/SSH connection (instructions can be found [here for PowerShell](../connect-your-device/PowerShell.md) and [here for SSH](../connect-your-device/SSH.md)) and enter the Remote Command you specified above.</span></span>

    ![控制台应用程序输出](../media/Console/console_output.png)

* <span data-ttu-id="d5f55-133">完成后调试应用程序，请记住，在 Windows IoT Core 设备上停止远程调试器。</span><span class="sxs-lookup"><span data-stu-id="d5f55-133">Once you are done debugging your application, remember to stop the remote debugger on the Windows IoT Core device.</span></span> <span data-ttu-id="d5f55-134">可以通过导航来调试 Windows Device Portal 设置部分并单击停止远程调试器按钮来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d5f55-134">You can do this by navigating to Debug settings section of Windows Device Portal and clicking on the Stop Remote Debugger button.</span></span>

    ![WindowsDevicePortalDebugSettings 停止远程调试器](../media/Console/device_portal_stop_debugger.PNG)

