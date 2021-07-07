---
title: 后台应用程序
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何为 IoT 设备开发后台应用程序。 了解后台应用程序的启动和使用方式、可用的语言等。
keywords: windows iot， 后台应用程序
ms.openlocfilehash: bfe928152c2f6d369c60ac786bb669d9bc0934a4
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229093"
---
# <a name="developing-background-applications"></a><span data-ttu-id="4bd34-105">开发后台应用程序</span><span class="sxs-lookup"><span data-stu-id="4bd34-105">Developing Background Applications</span></span>

> [!NOTE]
> <span data-ttu-id="4bd34-106">在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="4bd34-106">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="4bd34-107">后台应用程序是没有直接 UI 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4bd34-107">Background applications are applications that have no direct UI.</span></span> <span data-ttu-id="4bd34-108">部署和配置后，这些应用程序在计算机启动时启动并持续运行，没有任何进程生存期管理资源使用限制。</span><span class="sxs-lookup"><span data-stu-id="4bd34-108">Once deployed and configured, these applications launch at machine startup and run continuously without any process lifetime management resource use limitations.</span></span> <span data-ttu-id="4bd34-109">如果它们崩溃或退出，系统将自动重启它们。</span><span class="sxs-lookup"><span data-stu-id="4bd34-109">If they crash or exit the system will automatically restart them.</span></span>
<span data-ttu-id="4bd34-110">这些后台应用程序具有非常简单的执行模型。</span><span class="sxs-lookup"><span data-stu-id="4bd34-110">These Background Applications have a very simple execution model.</span></span> <span data-ttu-id="4bd34-111">这些模板创建一个实现"IBackgroundTask"接口的类，并生成空的"Run"方法。</span><span class="sxs-lookup"><span data-stu-id="4bd34-111">The templates create a class that implements the "IBackgroundTask" interface and generates the empty "Run" method.</span></span> <span data-ttu-id="4bd34-112">此"运行"方法是应用程序的入口点。</span><span class="sxs-lookup"><span data-stu-id="4bd34-112">This "Run" method is the entry point to your application.</span></span>

![后台任务](../media/BackgroundApplications/backgroundTaskScreenshot.png)

<span data-ttu-id="4bd34-114">有一个关键点需要注意：默认情况下，应用程序将在运行方法完成时关闭。</span><span class="sxs-lookup"><span data-stu-id="4bd34-114">There is one critical point to note: by default, the application will shut down when the run method completes.</span></span> <span data-ttu-id="4bd34-115">这意味着，遵循运行服务器等待输入或计时器的常见 IoT 模式的应用将发现应用提前退出。</span><span class="sxs-lookup"><span data-stu-id="4bd34-115">This means that apps that follow the common IoT pattern of running a server waiting for input or on a timer will find the app exit prematurely.</span></span> <span data-ttu-id="4bd34-116">若要防止发生这种情况，必须调用"GetDeferral"方法来阻止应用程序退出。</span><span class="sxs-lookup"><span data-stu-id="4bd34-116">To prevent this from happening you must call the "GetDeferral" method to prevent the application from exiting.</span></span> <span data-ttu-id="4bd34-117">可在此处找到有关延迟模式 [详细信息](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)。</span><span class="sxs-lookup"><span data-stu-id="4bd34-117">You can find more information on the deferral pattern [here](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span></span>

## <a name="where-can-background-applications-be-installed-from"></a><span data-ttu-id="4bd34-118">后台应用程序可以从何处安装？</span><span class="sxs-lookup"><span data-stu-id="4bd34-118">Where can Background Applications be installed from?</span></span> 

<span data-ttu-id="4bd34-119">可以从此处的 Visual Studio 库下载并安装 IoT 模板以启用[后台应用程序](https://go.microsoft.com/fwlink/?linkid=847472)。</span><span class="sxs-lookup"><span data-stu-id="4bd34-119">You can download and install IoT templates to enable Background Applications from the Visual Studio Gallery [here](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>  <span data-ttu-id="4bd34-120">或者，可以通过在 Visual Studio 库中搜索 或直接从 Visual Studio 对话框的 (Tools > `Windows IoT Core Project Templates` Extensions and Updates > Online) [](https://visualstudiogallery.msdn.microsoft.com/)找到模板。</span><span class="sxs-lookup"><span data-stu-id="4bd34-120">Alternatively, the templates can be found by searching for `Windows IoT Core Project Templates` in the [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) or directly from Visual Studio in the Extension and Updates dialog (Tools > Extensions and Updates > Online).</span></span>

## <a name="what-languages-are-available"></a><span data-ttu-id="4bd34-121">哪些语言可用？</span><span class="sxs-lookup"><span data-stu-id="4bd34-121">What languages are available?</span></span>

<span data-ttu-id="4bd34-122">**可以在 (IoT)** 模板的后台应用程序：</span><span class="sxs-lookup"><span data-stu-id="4bd34-122">**Background Application (IoT)** templates can be found for:</span></span>

* <span data-ttu-id="4bd34-123">**C++**`File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="4bd34-123">**C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="4bd34-124">**C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="4bd34-124">**C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="4bd34-125">**Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="4bd34-125">**Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="4bd34-126">**JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="4bd34-126">**JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`</span></span>

## <a name="how-are-background-applications-used"></a><span data-ttu-id="4bd34-127">如何使用后台应用程序？</span><span class="sxs-lookup"><span data-stu-id="4bd34-127">How are background applications used?</span></span> 

<span data-ttu-id="4bd34-128">创建后台应用程序与创建后台任务非常相似。</span><span class="sxs-lookup"><span data-stu-id="4bd34-128">Creating a background application is very similar to creating a Background Task.</span></span>  <span data-ttu-id="4bd34-129">后台应用程序启动时，将调用 Run 方法：</span><span class="sxs-lookup"><span data-stu-id="4bd34-129">When the Background Application starts, the Run method is called:</span></span>

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

<span data-ttu-id="4bd34-130">Run 方法结束时，除非创建延迟对象，否则后台应用程序将结束。</span><span class="sxs-lookup"><span data-stu-id="4bd34-130">When the Run method ends, unless a deferral object is created, the background application ends.</span></span> <span data-ttu-id="4bd34-131">异步编程的常见做法是接受如下所示的延迟：</span><span class="sxs-lookup"><span data-stu-id="4bd34-131">The common practice, for asynchronous programming is to take a deferral like this:</span></span>

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

<span data-ttu-id="4bd34-132">执行延迟后，后台应用程序将继续运行，直到调用 deferral 对象的 Complete 方法。</span><span class="sxs-lookup"><span data-stu-id="4bd34-132">Once a deferral is taken, the background application will continue until the deferral object's Complete method is called.</span></span>

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a><span data-ttu-id="4bd34-133">后台应用程序如何启动？</span><span class="sxs-lookup"><span data-stu-id="4bd34-133">How do background applications start?</span></span>

<span data-ttu-id="4bd34-134">此问题可以分解为部署和调用。</span><span class="sxs-lookup"><span data-stu-id="4bd34-134">This question can be broken into deployment and invocation.</span></span>  

<span data-ttu-id="4bd34-135">若要部署后台应用程序，可以：</span><span class="sxs-lookup"><span data-stu-id="4bd34-135">To deploy a background application, you can either:</span></span>

* <span data-ttu-id="4bd34-136">使用Visual Studio F5 (，这将生成、部署和调用) 。</span><span class="sxs-lookup"><span data-stu-id="4bd34-136">Use Visual Studio's F5 (which will build, deploy, and invoke).</span></span>  <span data-ttu-id="4bd34-137">有关更多详细信息，[请参阅Hello World示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld)，其中介绍了如何从 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4bd34-137">For more details, see our [Hello World sample](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) where we describe how to deploy and launch from Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="4bd34-138">这不会将后台应用程序配置为在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="4bd34-138">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="4bd34-139">通过在"创建应用包"Visual Studio选择"Project >应用商店> AppX。</span><span class="sxs-lookup"><span data-stu-id="4bd34-139">Create an AppX in Visual Studio by selecting Project > Store > Create App Packages.</span></span>  <span data-ttu-id="4bd34-140">创建 AppX 后，可以使用[Windows 设备门户将其部署到](../manage-your-device/DevicePortal.md)Windows 10 IoT 核心版 设备。</span><span class="sxs-lookup"><span data-stu-id="4bd34-140">Once you have created an AppX, you can use [Windows Device Portal](../manage-your-device/DevicePortal.md) to deploy it to your Windows 10 IoT Core device.</span></span>

<span data-ttu-id="4bd34-141">若要调用后台应用程序，可以：</span><span class="sxs-lookup"><span data-stu-id="4bd34-141">To invoke a background application, you can either:</span></span>

* <span data-ttu-id="4bd34-142">如上所述，Visual Studio F5 功能将部署并立即启动后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="4bd34-142">As mentioned above, Visual Studio's F5 functionality will deploy and immediately start your Background Application.</span></span>

> [!NOTE]
> <span data-ttu-id="4bd34-143">这不会将后台应用程序配置为在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="4bd34-143">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="4bd34-144">对于已部署到 IoT 设备的后台应用程序，可以使用 iotstartup.exe 实用工具将后台应用程序配置为在设备启动时启动。</span><span class="sxs-lookup"><span data-stu-id="4bd34-144">For a background application that has been deployed to an IoT device, you can use the iotstartup.exe utility to configure your background application to start when the device boots.</span></span>  <span data-ttu-id="4bd34-145">若要将后台应用程序指定为启动应用，请按照以下说明 (将应用的名称替换为 `BackgroundApplication1` 以下) ：</span><span class="sxs-lookup"><span data-stu-id="4bd34-145">To specify your background application as a Startup App, follow these instructions (**substitute your app's name** for `BackgroundApplication1` below):</span></span>

1. <span data-ttu-id="4bd34-146">启动 PowerShell (PS) 会话Windows IoT Core 设备，[如此处所述](../connect-your-device/PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd34-146">Start a PowerShell (PS) session with your Windows IoT Core device as described [here](../connect-your-device/PowerShell.md).</span></span>

2. <span data-ttu-id="4bd34-147">在 PS 会话中，键入：</span><span class="sxs-lookup"><span data-stu-id="4bd34-147">From the PS session, type:</span></span>
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. <span data-ttu-id="4bd34-148">应会看到后台应用程序的全名，例如：</span><span class="sxs-lookup"><span data-stu-id="4bd34-148">You should see the full name of your background application, i.e. something like:</span></span>

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. <span data-ttu-id="4bd34-149">实用工具正在确认后台应用程序是"无头"应用程序，并且已正确安装。</span><span class="sxs-lookup"><span data-stu-id="4bd34-149">The utility is confirming that your background application is an 'headless' application, and is installed correctly.</span></span>  <span data-ttu-id="4bd34-150">你很可能会看到后台应用程序的"前向"条目，但可能会忽略此条目。</span><span class="sxs-lookup"><span data-stu-id="4bd34-150">You will likely see a Headed entry as well for your Background Applications, but this can be disregarded.</span></span>

5. <span data-ttu-id="4bd34-151">现在，可以轻松将此应用设置为"启动应用"。</span><span class="sxs-lookup"><span data-stu-id="4bd34-151">Now, it's easy to set this app as a 'Startup App'.</span></span> <span data-ttu-id="4bd34-152">只需键入命令：</span><span class="sxs-lookup"><span data-stu-id="4bd34-152">Just type the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. <span data-ttu-id="4bd34-153">实用工具将确认后台应用程序已添加到无头"启动应用"列表：</span><span class="sxs-lookup"><span data-stu-id="4bd34-153">The utility will confirm that your background application has been added to the list of headless 'Startup Apps':</span></span>

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. <span data-ttu-id="4bd34-154">继续重启 IoT 核心Windows设备。</span><span class="sxs-lookup"><span data-stu-id="4bd34-154">Go ahead and restart your Windows IoT Core device.</span></span> <span data-ttu-id="4bd34-155">在 PS 会话中，可以发出 shutdown 命令：</span><span class="sxs-lookup"><span data-stu-id="4bd34-155">From the PS session, you can issue the shutdown command:</span></span>

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. <span data-ttu-id="4bd34-156">重启设备后，后台应用程序将自动启动，Windows 10 IoT 核心版确保它随时停止时重启。</span><span class="sxs-lookup"><span data-stu-id="4bd34-156">Once the device has restarted, your background application will start automatically and Windows 10 IoT Core will make sure that it gets restarted anytime it stops.</span></span>  

> [!NOTE]
> <span data-ttu-id="4bd34-157">将后台应用注册为自动运行后，如果应用退出或崩溃，它将自动重启。</span><span class="sxs-lookup"><span data-stu-id="4bd34-157">Once a background app is registered to run automatically, if the app exits or crashes it will be automatically restarted.</span></span>  <span data-ttu-id="4bd34-158">不会通知应用启动或重启的原因，因此，如果要在重启时采取特殊操作，则需要跟踪应用中的应用状态。</span><span class="sxs-lookup"><span data-stu-id="4bd34-158">The app isn't informed of the reason that it's being started or restarted so if you want to take special action on a restart you will need to track the app state in your app.</span></span>

9. <span data-ttu-id="4bd34-159">可以通过键入命令从无头启动应用列表中删除后台应用程序：</span><span class="sxs-lookup"><span data-stu-id="4bd34-159">You can remove your background application from the list of headless Startup Apps by typing the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. <span data-ttu-id="4bd34-160">实用工具将确认背景应用程序已从无头"启动应用"列表中删除：</span><span class="sxs-lookup"><span data-stu-id="4bd34-160">The utility will confirm that your background application has been removed from the list of headless 'Startup Apps':</span></span>

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

## <a name="see-also"></a><span data-ttu-id="4bd34-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4bd34-161">See Also</span></span>
<span data-ttu-id="4bd34-162">若要在生成自定义映像时添加后台应用，请参阅 [创建 Appx 包](../build-your-image/createinstallpackage.md)</span><span class="sxs-lookup"><span data-stu-id="4bd34-162">To add a background app when building a custom image see [Create an Appx package](../build-your-image/createinstallpackage.md)</span></span>
