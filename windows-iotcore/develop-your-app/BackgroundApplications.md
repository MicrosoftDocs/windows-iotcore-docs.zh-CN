---
title: 后台应用程序
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何为 IoT 设备开发后台应用程序。 了解后台应用程序的启动和使用方式、可用的语言等。
keywords: windows iot，后台应用程序
ms.openlocfilehash: 1749bca8ce4d8ccf99aa5e622b60461f3657f851
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656473"
---
# <a name="developing-background-applications"></a><span data-ttu-id="0e363-105">开发后台应用程序</span><span class="sxs-lookup"><span data-stu-id="0e363-105">Developing Background Applications</span></span>

> [!NOTE]
> <span data-ttu-id="0e363-106">在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="0e363-106">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="0e363-107">后台应用程序是没有直接 UI 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0e363-107">Background applications are applications that have no direct UI.</span></span> <span data-ttu-id="0e363-108">部署和配置后，这些应用程序在计算机启动时启动并连续运行，而不会有任何进程生存期管理资源使用限制。</span><span class="sxs-lookup"><span data-stu-id="0e363-108">Once deployed and configured, these applications launch at machine startup and run continuously without any process lifetime management resource use limitations.</span></span> <span data-ttu-id="0e363-109">如果系统崩溃或退出，系统会自动重新启动它们。</span><span class="sxs-lookup"><span data-stu-id="0e363-109">If they crash or exit the system will automatically restart them.</span></span>
<span data-ttu-id="0e363-110">这些后台应用程序的执行模型非常简单。</span><span class="sxs-lookup"><span data-stu-id="0e363-110">These Background Applications have a very simple execution model.</span></span> <span data-ttu-id="0e363-111">模板创建一个实现 "IBackgroundTask" 接口的类，并生成空的 "Run" 方法。</span><span class="sxs-lookup"><span data-stu-id="0e363-111">The templates create a class that implements the "IBackgroundTask" interface and generates the empty "Run" method.</span></span> <span data-ttu-id="0e363-112">此 "运行" 方法是应用程序的入口点。</span><span class="sxs-lookup"><span data-stu-id="0e363-112">This "Run" method is the entry point to your application.</span></span>

![后台任务](../media/BackgroundApplications/backgroundTaskScreenshot.png)

<span data-ttu-id="0e363-114">需要注意的一点是：默认情况下，当 run 方法完成时，应用程序将关闭。</span><span class="sxs-lookup"><span data-stu-id="0e363-114">There is one critical point to note: by default, the application will shut down when the run method completes.</span></span> <span data-ttu-id="0e363-115">这意味着，遵循运行等待输入的服务器或在计时器上的常见 IoT 模式的应用会提前发现应用退出。</span><span class="sxs-lookup"><span data-stu-id="0e363-115">This means that apps that follow the common IoT pattern of running a server waiting for input or on a timer will find the app exit prematurely.</span></span> <span data-ttu-id="0e363-116">若要防止此情况发生，必须调用 "GetDeferral" 方法，以防止应用程序退出。</span><span class="sxs-lookup"><span data-stu-id="0e363-116">To prevent this from happening you must call the "GetDeferral" method to prevent the application from exiting.</span></span> <span data-ttu-id="0e363-117">可在 [此处](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)找到有关延期模式的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0e363-117">You can find more information on the deferral pattern [here](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span></span>

## <a name="where-can-background-applications-be-installed-from"></a><span data-ttu-id="0e363-118">后台应用程序的安装位置</span><span class="sxs-lookup"><span data-stu-id="0e363-118">Where can Background Applications be installed from?</span></span> 

<span data-ttu-id="0e363-119">你可以从 Visual [Studio 库下载](https://go.microsoft.com/fwlink/?linkid=847472)并安装 IoT 模板来启用后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="0e363-119">You can download and install IoT templates to enable Background Applications from the Visual Studio Gallery [here](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>  <span data-ttu-id="0e363-120">此外，还可以通过在 `Windows IoT Core Project Templates` [Visual studio 库](https://visualstudiogallery.msdn.microsoft.com/) 中搜索或直接从 visual Studio 的 "扩展和更新" 对话框中的 visual studio 查找模板， (工具 > 扩展和更新 > 联机) 。</span><span class="sxs-lookup"><span data-stu-id="0e363-120">Alternatively, the templates can be found by searching for `Windows IoT Core Project Templates` in the [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) or directly from Visual Studio in the Extension and Updates dialog (Tools > Extensions and Updates > Online).</span></span>

## <a name="what-languages-are-available"></a><span data-ttu-id="0e363-121">可用的语言有哪些？</span><span class="sxs-lookup"><span data-stu-id="0e363-121">What languages are available?</span></span>

<span data-ttu-id="0e363-122">可在以下内容中找到\*\*后台应用程序 (IoT) \*\*模板：</span><span class="sxs-lookup"><span data-stu-id="0e363-122">**Background Application (IoT)** templates can be found for:</span></span>

* <span data-ttu-id="0e363-123">**C + +**`File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="0e363-123">**C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="0e363-124">**C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="0e363-124">**C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="0e363-125">**Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="0e363-125">**Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="0e363-126">**JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="0e363-126">**JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`</span></span>

## <a name="how-are-background-applications-used"></a><span data-ttu-id="0e363-127">后台应用程序如何使用？</span><span class="sxs-lookup"><span data-stu-id="0e363-127">How are background applications used?</span></span> 

<span data-ttu-id="0e363-128">创建后台应用程序非常类似于创建后台任务。</span><span class="sxs-lookup"><span data-stu-id="0e363-128">Creating a background application is very similar to creating a Background Task.</span></span>  <span data-ttu-id="0e363-129">后台应用程序启动时，将调用 Run 方法：</span><span class="sxs-lookup"><span data-stu-id="0e363-129">When the Background Application starts, the Run method is called:</span></span>

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

<span data-ttu-id="0e363-130">当 Run 方法结束时，除非创建延迟对象，否则后台应用程序将结束。</span><span class="sxs-lookup"><span data-stu-id="0e363-130">When the Run method ends, unless a deferral object is created, the background application ends.</span></span> <span data-ttu-id="0e363-131">异步编程的常见做法是按如下所示延迟：</span><span class="sxs-lookup"><span data-stu-id="0e363-131">The common practice, for asynchronous programming is to take a deferral like this:</span></span>

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

<span data-ttu-id="0e363-132">延迟完成后，后台应用程序将继续运行，直到调用延迟对象的完整方法。</span><span class="sxs-lookup"><span data-stu-id="0e363-132">Once a deferral is taken, the background application will continue until the deferral object's Complete method is called.</span></span>

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a><span data-ttu-id="0e363-133">后台应用程序如何启动？</span><span class="sxs-lookup"><span data-stu-id="0e363-133">How do background applications start?</span></span>

<span data-ttu-id="0e363-134">此问题可能会被分解为部署和调用。</span><span class="sxs-lookup"><span data-stu-id="0e363-134">This question can be broken into deployment and invocation.</span></span>  

<span data-ttu-id="0e363-135">若要部署后台应用程序，可以执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="0e363-135">To deploy a background application, you can either:</span></span>

* <span data-ttu-id="0e363-136">使用 Visual Studio 的 F5 (将生成、部署和调用) 。</span><span class="sxs-lookup"><span data-stu-id="0e363-136">Use Visual Studio's F5 (which will build, deploy, and invoke).</span></span>  <span data-ttu-id="0e363-137">有关更多详细信息，请参阅我们的 [Hello World 示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) ，其中介绍了如何从 Visual Studio 部署和启动。</span><span class="sxs-lookup"><span data-stu-id="0e363-137">For more details, see our [Hello World sample](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) where we describe how to deploy and launch from Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="0e363-138">这不会将后台应用程序配置为在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="0e363-138">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="0e363-139">在 Visual Studio 中创建 AppX，方法是选择 "项目 > 存储" > 创建应用包 "。</span><span class="sxs-lookup"><span data-stu-id="0e363-139">Create an AppX in Visual Studio by selecting Project > Store > Create App Packages.</span></span>  <span data-ttu-id="0e363-140">创建 AppX 后，可以使用 [Windows 设备门户](../manage-your-device/DevicePortal.md) 将其部署到 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="0e363-140">Once you have created an AppX, you can use [Windows Device Portal](../manage-your-device/DevicePortal.md) to deploy it to your Windows 10 IoT Core device.</span></span>

<span data-ttu-id="0e363-141">若要调用后台应用程序，可以执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="0e363-141">To invoke a background application, you can either:</span></span>

* <span data-ttu-id="0e363-142">如上所述，Visual Studio 的 F5 功能将部署并立即启动后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="0e363-142">As mentioned above, Visual Studio's F5 functionality will deploy and immediately start your Background Application.</span></span>

> [!NOTE]
> <span data-ttu-id="0e363-143">这不会将后台应用程序配置为在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="0e363-143">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="0e363-144">对于已部署到 IoT 设备的后台应用程序，可以使用 iotstartup.exe 实用程序将后台应用程序配置为在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="0e363-144">For a background application that has been deployed to an IoT device, you can use the iotstartup.exe utility to configure your background application to start when the device boots.</span></span>  <span data-ttu-id="0e363-145">若要将后台应用程序指定为启动应用程序，请按照以下说明 (**将应用程序的名称替换** `BackgroundApplication1`) ：</span><span class="sxs-lookup"><span data-stu-id="0e363-145">To specify your background application as a Startup App, follow these instructions (**substitute your app's name** for `BackgroundApplication1` below):</span></span>

1. <span data-ttu-id="0e363-146">如 [此处](../connect-your-device/PowerShell.md)所述，使用 Windows IoT Core 设备启动 POWERSHELL (PS) 会话。</span><span class="sxs-lookup"><span data-stu-id="0e363-146">Start a PowerShell (PS) session with your Windows IoT Core device as described [here](../connect-your-device/PowerShell.md).</span></span>

2. <span data-ttu-id="0e363-147">在 PS 会话中键入：</span><span class="sxs-lookup"><span data-stu-id="0e363-147">From the PS session, type:</span></span>
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. <span data-ttu-id="0e363-148">你应看到后台应用程序的完整名称，例如：</span><span class="sxs-lookup"><span data-stu-id="0e363-148">You should see the full name of your background application, i.e. something like:</span></span>

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. <span data-ttu-id="0e363-149">实用工具确认后台应用程序是 "无外设" 应用程序，并且已正确安装。</span><span class="sxs-lookup"><span data-stu-id="0e363-149">The utility is confirming that your background application is an 'headless' application, and is installed correctly.</span></span>  <span data-ttu-id="0e363-150">你可能还会看到适用于你的后台应用程序的头条目，但这可能会被忽略。</span><span class="sxs-lookup"><span data-stu-id="0e363-150">You will likely see a Headed entry as well for your Background Applications, but this can be disregarded.</span></span>

5. <span data-ttu-id="0e363-151">现在，可以轻松地将此应用程序设置为 "启动应用程序"。</span><span class="sxs-lookup"><span data-stu-id="0e363-151">Now, it's easy to set this app as a 'Startup App'.</span></span> <span data-ttu-id="0e363-152">只需键入命令：</span><span class="sxs-lookup"><span data-stu-id="0e363-152">Just type the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. <span data-ttu-id="0e363-153">实用程序将确认您的后台应用程序已添加到无外设 "启动应用程序" 列表中：</span><span class="sxs-lookup"><span data-stu-id="0e363-153">The utility will confirm that your background application has been added to the list of headless 'Startup Apps':</span></span>

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. <span data-ttu-id="0e363-154">继续重启 Windows IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="0e363-154">Go ahead and restart your Windows IoT Core device.</span></span> <span data-ttu-id="0e363-155">通过 PS 会话，可以发出 shutdown 命令：</span><span class="sxs-lookup"><span data-stu-id="0e363-155">From the PS session, you can issue the shutdown command:</span></span>

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. <span data-ttu-id="0e363-156">设备重新启动后，后台应用程序将自动启动，Windows 10 IoT Core 将确保它在任何时间停止时重新启动。</span><span class="sxs-lookup"><span data-stu-id="0e363-156">Once the device has restarted, your background application will start automatically and Windows 10 IoT Core will make sure that it gets restarted anytime it stops.</span></span>  

> [!NOTE]
> <span data-ttu-id="0e363-157">将后台应用注册为自动运行后，如果应用退出或发生故障，它将自动重新启动。</span><span class="sxs-lookup"><span data-stu-id="0e363-157">Once a background app is registered to run automatically, if the app exits or crashes it will be automatically restarted.</span></span>  <span data-ttu-id="0e363-158">由于应用程序正在启动或重新启动，因此，如果想要在重新启动时执行特殊操作，则需要在应用程序中跟踪应用程序状态。</span><span class="sxs-lookup"><span data-stu-id="0e363-158">The app isn't informed of the reason that it's being started or restarted so if you want to take special action on a restart you will need to track the app state in your app.</span></span>

9. <span data-ttu-id="0e363-159">可以通过键入以下命令从无外设启动应用列表中删除后台应用程序：</span><span class="sxs-lookup"><span data-stu-id="0e363-159">You can remove your background application from the list of headless Startup Apps by typing the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. <span data-ttu-id="0e363-160">实用程序将确认您的后台应用程序已从无外设 "启动应用程序" 列表中删除：</span><span class="sxs-lookup"><span data-stu-id="0e363-160">The utility will confirm that your background application has been removed from the list of headless 'Startup Apps':</span></span>

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

## <a name="see-also"></a><span data-ttu-id="0e363-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e363-161">See Also</span></span>
<span data-ttu-id="0e363-162">若要在生成自定义映像时添加后台应用，请参阅 [创建 Appx 包](../build-your-image/createinstallpackage.md)</span><span class="sxs-lookup"><span data-stu-id="0e363-162">To add a background app when building a custom image see [Create an Appx package](../build-your-image/createinstallpackage.md)</span></span>
