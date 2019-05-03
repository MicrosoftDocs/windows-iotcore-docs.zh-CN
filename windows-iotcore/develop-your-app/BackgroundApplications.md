---
title: 后台应用程序
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何开发 IoT 设备的后台应用程序。
keywords: windows iot，后台应用程序
ms.openlocfilehash: 1b3fd831a4cdf3ebb8bc2d80c544344b13115617
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510772"
---
# <a name="developing-background-applications"></a><span data-ttu-id="c80d2-104">开发后台应用程序</span><span class="sxs-lookup"><span data-stu-id="c80d2-104">Developing Background Applications</span></span>

> [!NOTE]
> <span data-ttu-id="c80d2-105">部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。</span><span class="sxs-lookup"><span data-stu-id="c80d2-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="c80d2-106">后台应用程序是具有没有直接的用户界面的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c80d2-106">Background applications are applications that have no direct UI.</span></span> <span data-ttu-id="c80d2-107">部署和配置完成后，这些应用程序将在计算机启动时启动，并将持续运行，不受任何进程生命期管理资源使用的限制。</span><span class="sxs-lookup"><span data-stu-id="c80d2-107">Once deployed and configured, these applications launch at machine startup and run continuously without any process lifetime management resource use limitations.</span></span> <span data-ttu-id="c80d2-108">如果这些应用程序崩溃或退出，系统将自动重新启动它们。</span><span class="sxs-lookup"><span data-stu-id="c80d2-108">If they crash or exit the system will automatically restart them.</span></span>
<span data-ttu-id="c80d2-109">这些后台应用程序有一个非常简单的执行模型。</span><span class="sxs-lookup"><span data-stu-id="c80d2-109">These Background Applications have a very simple execution model.</span></span> <span data-ttu-id="c80d2-110">模板将创建实现“IBackgroundTask”接口并生成空的“运行”方法的类。</span><span class="sxs-lookup"><span data-stu-id="c80d2-110">The templates create a class that implements the "IBackgroundTask" interface and generates the empty "Run" method.</span></span> <span data-ttu-id="c80d2-111">此“运行”方法将是通向你的应用程序的入口点。</span><span class="sxs-lookup"><span data-stu-id="c80d2-111">This "Run" method is the entry point to your application.</span></span>

![后台任务](../media/BackgroundApplications/backgroundTaskScreenshot.png)

<span data-ttu-id="c80d2-113">需特别注意的一点是，默认情况下，应用程序将在运行方法完成时关闭。</span><span class="sxs-lookup"><span data-stu-id="c80d2-113">There is one critical point to note: by default, the application will shut down when the run method completes.</span></span> <span data-ttu-id="c80d2-114">这意味着遵循运行等待输入或在计时器上的服务器的常用 IoT 模式的应用将会过早地发现应用退出这一情况。</span><span class="sxs-lookup"><span data-stu-id="c80d2-114">This means that apps that follow the common IoT pattern of running a server waiting for input or on a timer will find the app exit prematurely.</span></span> <span data-ttu-id="c80d2-115">若要阻止这种情况发生，必须调用“GetDeferral”方法才能阻止应用程序退出。</span><span class="sxs-lookup"><span data-stu-id="c80d2-115">To prevent this from happening you must call the "GetDeferral" method to prevent the application from exiting.</span></span> <span data-ttu-id="c80d2-116">可在[此处](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)查找有关延迟模式的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c80d2-116">You can find more information on the deferral pattern [here](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span></span>

## <a name="where-can-background-applications-be-installed-from"></a><span data-ttu-id="c80d2-117">后台应用程序可从何处安装？</span><span class="sxs-lookup"><span data-stu-id="c80d2-117">Where can Background Applications be installed from?</span></span> 

<span data-ttu-id="c80d2-118">可在[此处](https://go.microsoft.com/fwlink/?linkid=847472)从 Visual Studio 库中下载并安装 IoT 模板以启用后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="c80d2-118">You can download and install IoT templates to enable Background Applications from the Visual Studio Gallery [here](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>  <span data-ttu-id="c80d2-119">或者，可通过在 [Visual Studio 库](https://visualstudiogallery.msdn.microsoft.com/)中或直接从“扩展和更新”对话框（“工具”>“扩展和更新”>“联机”）中的 Visual Studio 搜索 `Windows IoT Core Project Templates` 来找到模板。</span><span class="sxs-lookup"><span data-stu-id="c80d2-119">Alternatively, the templates can be found by searching for `Windows IoT Core Project Templates` in the [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) or directly from Visual Studio in the Extension and Updates dialog (Tools > Extensions and Updates > Online).</span></span>

## <a name="what-languages-are-available"></a><span data-ttu-id="c80d2-120">哪些语言可用？</span><span class="sxs-lookup"><span data-stu-id="c80d2-120">What languages are available?</span></span>

<span data-ttu-id="c80d2-121">可找到采用以下语言的**后台应用程序 (IoT)** 模板：</span><span class="sxs-lookup"><span data-stu-id="c80d2-121">**Background Application (IoT)** templates can be found for:</span></span>

* **<span data-ttu-id="c80d2-122">C++</span><span class="sxs-lookup"><span data-stu-id="c80d2-122">C++</span></span>** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **<span data-ttu-id="c80d2-123">C#</span><span class="sxs-lookup"><span data-stu-id="c80d2-123">C#</span></span>** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **<span data-ttu-id="c80d2-124">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c80d2-124">Visual Basic</span></span>** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **<span data-ttu-id="c80d2-125">JavaScript</span><span class="sxs-lookup"><span data-stu-id="c80d2-125">JavaScript</span></span>** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a><span data-ttu-id="c80d2-126">如何使用后台应用程序？</span><span class="sxs-lookup"><span data-stu-id="c80d2-126">How are background applications used?</span></span> 

<span data-ttu-id="c80d2-127">创建后台应用程序是非常类似于创建后台任务。</span><span class="sxs-lookup"><span data-stu-id="c80d2-127">Creating a background application is very similar to creating a Background Task.</span></span>  <span data-ttu-id="c80d2-128">在启动后台应用程序时，将调用运行方法：</span><span class="sxs-lookup"><span data-stu-id="c80d2-128">When the Background Application starts, the Run method is called:</span></span>

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

<span data-ttu-id="c80d2-129">Run 方法结束时，除非创建延迟对象，否则，后台应用程序结束。</span><span class="sxs-lookup"><span data-stu-id="c80d2-129">When the Run method ends, unless a deferral object is created, the background application ends.</span></span> <span data-ttu-id="c80d2-130">针对异步编程，常见做法是使用延迟，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c80d2-130">The common practice, for asynchronous programming is to take a deferral like this:</span></span>

```csharp
private BackgroundTaskDeferral deferral;
public void Run(IBackgroundTaskInstance taskInstance)
{
    deferral = taskInstance.GetDeferral();
    
    //
    // TODO: Insert code to start one or more asynchronous methods
    //
}
```

<span data-ttu-id="c80d2-131">执行延迟之后, 的后台应用程序将继续，直到调用延迟对象的完整方法。</span><span class="sxs-lookup"><span data-stu-id="c80d2-131">Once a deferral is taken, the background application will continue until the deferral object's Complete method is called.</span></span>

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a><span data-ttu-id="c80d2-132">如何启动后台应用程序？</span><span class="sxs-lookup"><span data-stu-id="c80d2-132">How do background applications start?</span></span>

<span data-ttu-id="c80d2-133">此问题可分解为部署和调用两个方面。</span><span class="sxs-lookup"><span data-stu-id="c80d2-133">This question can be broken into deployment and invocation.</span></span>  

<span data-ttu-id="c80d2-134">若要部署的后台应用程序，您可以：</span><span class="sxs-lookup"><span data-stu-id="c80d2-134">To deploy a background application, you can either:</span></span>

* <span data-ttu-id="c80d2-135">使用 Visual Studio 的 F5（将生成、部署和调用）。</span><span class="sxs-lookup"><span data-stu-id="c80d2-135">Use Visual Studio's F5 (which will build, deploy and invoke).</span></span>  <span data-ttu-id="c80d2-136">有关更多详细信息，请参阅我们[Hello World 示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld)我们介绍如何部署和启动 Visual Studio 中的位置。</span><span class="sxs-lookup"><span data-stu-id="c80d2-136">For more details, see our [Hello World sample](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) where we describe how to deploy and launch from Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="c80d2-137">这不会将配置您的后台应用程序以启动设备启动时。</span><span class="sxs-lookup"><span data-stu-id="c80d2-137">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="c80d2-138">通过依次选择“项目”>“应用商店”>“创建应用包”，在 Visual Studio 中创建 AppX。</span><span class="sxs-lookup"><span data-stu-id="c80d2-138">Create an AppX in Visual Studio by selecting Project > Store > Create App Packages.</span></span>  <span data-ttu-id="c80d2-139">创建 AppX 后，可使用 [Windows Device Portal](../manage-your-device/DevicePortal.md) 来将其部署到 Windows 10 IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="c80d2-139">Once you have created an AppX, you can use [Windows Device Portal](../manage-your-device/DevicePortal.md) to deploy it to your Windows 10 IoT Core device.</span></span>

<span data-ttu-id="c80d2-140">若要调用的后台应用程序，您可以：</span><span class="sxs-lookup"><span data-stu-id="c80d2-140">To invoke a background application, you can either:</span></span>

* <span data-ttu-id="c80d2-141">如上所述，Visual Studio 的 F5 功能将部署并立即启动后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="c80d2-141">As mentioned above, Visual Studio's F5 functionality will deploy and immediately start your Background Application.</span></span>

> [!NOTE]
> <span data-ttu-id="c80d2-142">这不会将配置您的后台应用程序以启动设备启动时。</span><span class="sxs-lookup"><span data-stu-id="c80d2-142">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="c80d2-143">有关已部署到 IoT 设备的后台应用程序，您可以使用 iotstartup.exe 实用工具来配置后台应用程序，以启动设备启动时。</span><span class="sxs-lookup"><span data-stu-id="c80d2-143">For a background application that has been deployed to an IoT device, you can use the iotstartup.exe utility to configure your background application to start when the device boots.</span></span>  <span data-ttu-id="c80d2-144">若要指定启动应用程序作为后台应用程序，请按照这些说明进行操作 (**替换为你的应用名称**为`BackgroundApplication1`下面):</span><span class="sxs-lookup"><span data-stu-id="c80d2-144">To specify your background application as a Startup App, follow these instructions (**substitute your app's name** for `BackgroundApplication1` below):</span></span>

1. <span data-ttu-id="c80d2-145">通过 Windows IoT 核心版设备启动 PowerShell (PS) 会话，如[此处](../connect-your-device/PowerShell.md)所述。</span><span class="sxs-lookup"><span data-stu-id="c80d2-145">Start a PowerShell (PS) session with your Windows IoT Core device as described [here](../connect-your-device/PowerShell.md).</span></span>

2. <span data-ttu-id="c80d2-146">在 PS 会话中，键入：</span><span class="sxs-lookup"><span data-stu-id="c80d2-146">From the PS session, type:</span></span>
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. <span data-ttu-id="c80d2-147">如下所示，应即查看后台应用程序的完整名称：</span><span class="sxs-lookup"><span data-stu-id="c80d2-147">You should see the full name of your background application, i.e. something like:</span></span>

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. <span data-ttu-id="c80d2-148">该实用工具确认后台应用程序是一个无外设应用程序，以及正确安装。</span><span class="sxs-lookup"><span data-stu-id="c80d2-148">The utility is confirming that your background application is an 'headless' application, and is installed correctly.</span></span>  <span data-ttu-id="c80d2-149">你还可能看到后台应用程序的有外设项，但这可以忽略不计。</span><span class="sxs-lookup"><span data-stu-id="c80d2-149">You will likely see a Headed entry as well for your Background Applications, but this can be disregarded.</span></span>

5. <span data-ttu-id="c80d2-150">现在，可轻松地将此应用设置为“启动应用”。</span><span class="sxs-lookup"><span data-stu-id="c80d2-150">Now, it's easy to set this app as a 'Startup App'.</span></span> <span data-ttu-id="c80d2-151">只需键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="c80d2-151">Just type the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. <span data-ttu-id="c80d2-152">该实用工具将确认已将后台应用程序添加到的无外设启动应用列表：</span><span class="sxs-lookup"><span data-stu-id="c80d2-152">The utility will confirm that your background application has been added to the list of headless 'Startup Apps':</span></span>

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. <span data-ttu-id="c80d2-153">继续下一步，然后重新启动 Windows IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="c80d2-153">Go ahead and restart your Windows IoT Core device.</span></span> <span data-ttu-id="c80d2-154">在 PS 会话中，可以发出关闭命令：</span><span class="sxs-lookup"><span data-stu-id="c80d2-154">From the PS session, you can issue the shutdown command:</span></span>

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. <span data-ttu-id="c80d2-155">设备已重新启动后，后台应用程序会自动启动和 Windows 10 IoT Core 会确保它获取随时停止时的重启。</span><span class="sxs-lookup"><span data-stu-id="c80d2-155">Once the device has restarted, your background application will start automatically and Windows 10 IoT Core will make sure that it gets restarted anytime it stops.</span></span>  

> [!NOTE]
> <span data-ttu-id="c80d2-156">后台应用注册来自动运行，如果应用程序退出或出现故障后它将自动重新启动。</span><span class="sxs-lookup"><span data-stu-id="c80d2-156">Once a background app is registered to run automatically, if the app exits or crashes it will be automatically restarted.</span></span>  <span data-ttu-id="c80d2-157">应用程序不被通知它正在启动或重新启动，如果你想要重新启动您将需要跟踪应用程序状态应用程序中的对其执行特殊操作的原因。</span><span class="sxs-lookup"><span data-stu-id="c80d2-157">The app isn't informed of the reason that it's being started or restarted so if you want to take special action on a restart you will need to track the app state in your app.</span></span>

9. <span data-ttu-id="c80d2-158">通过键入命令，可以从列表中的无外设启动应用程序删除后台应用程序：</span><span class="sxs-lookup"><span data-stu-id="c80d2-158">You can remove your background application from the list of headless Startup Apps by typing the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. <span data-ttu-id="c80d2-159">该实用工具将确认已从无外设启动应用列表中删除了后台应用程序：</span><span class="sxs-lookup"><span data-stu-id="c80d2-159">The utility will confirm that your background application has been removed from the list of headless 'Startup Apps':</span></span>

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a><span data-ttu-id="c80d2-160">请参阅</span><span class="sxs-lookup"><span data-stu-id="c80d2-160">See Also</span></span>
<span data-ttu-id="c80d2-161">若要添加的后台应用程序时生成自定义映像，请参阅[创建 Appx 包](../build-your-image/createinstallpackage.md)</span><span class="sxs-lookup"><span data-stu-id="c80d2-161">To add a background app when building a custom image see [Create an Appx package](../build-your-image/createinstallpackage.md)</span></span>