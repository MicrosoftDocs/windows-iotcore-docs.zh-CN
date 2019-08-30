---
title: 后台应用程序
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何为 IoT 设备开发后台应用程序。
keywords: windows iot, 后台应用程序
ms.openlocfilehash: 1b3fd831a4cdf3ebb8bc2d80c544344b13115617
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167879"
---
# <a name="developing-background-applications"></a>开发后台应用程序

> [!NOTE]
> 在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。

后台应用程序是没有直接 UI 的应用程序。 部署和配置完成后，这些应用程序将在计算机启动时启动，并将持续运行，不受任何进程生命期管理资源使用的限制。 如果这些应用程序崩溃或退出，系统将自动重新启动它们。
这些后台应用程序有一个非常简单的执行模型。 模板将创建实现“IBackgroundTask”接口并生成空的“运行”方法的类。 此“运行”方法将是通向你的应用程序的入口点。

![后台任务](../media/BackgroundApplications/backgroundTaskScreenshot.png)

需特别注意的一点是，默认情况下，应用程序将在运行方法完成时关闭。 这意味着遵循运行等待输入或在计时器上的服务器的常用 IoT 模式的应用将会过早地发现应用退出这一情况。 若要阻止这种情况发生，必须调用“GetDeferral”方法才能阻止应用程序退出。 可在[此处](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)查找有关延迟模式的详细信息。

## <a name="where-can-background-applications-be-installed-from"></a>后台应用程序可从何处安装？ 

可在[此处](https://go.microsoft.com/fwlink/?linkid=847472)从 Visual Studio 库中下载并安装 IoT 模板以启用后台应用程序。  或者，可通过在 [Visual Studio 库](https://visualstudiogallery.msdn.microsoft.com/)中或直接从“扩展和更新”对话框（“工具”>“扩展和更新”>“联机”）中的 Visual Studio 搜索 `Windows IoT Core Project Templates` 来找到模板。

## <a name="what-languages-are-available"></a>哪些语言可用？

可找到采用以下语言的**后台应用程序 (IoT)** 模板：

* **C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **Visual Basic**`File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **JavaScript**`File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a>后台应用程序如何使用？ 

创建后台应用程序非常类似于创建后台任务。  在启动后台应用程序时，将调用运行方法：

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

当 Run 方法结束时, 除非创建延迟对象, 否则后台应用程序将结束。 针对异步编程，常见做法是使用延迟，如下所示：

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

延迟完成后, 后台应用程序将继续运行, 直到调用延迟对象的完整方法。

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a>后台应用程序如何启动？

此问题可分解为部署和调用两个方面。  

若要部署后台应用程序, 可以执行以下操作之一:

* 使用 Visual Studio 的 F5（将生成、部署和调用）。  有关更多详细信息, 请参阅我们的[Hello World 示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld), 其中介绍了如何从 Visual Studio 部署和启动。

> [!NOTE]
> 这不会将后台应用程序配置为在设备启动时启动。

* 通过依次选择“项目”>“应用商店”>“创建应用包”，在 Visual Studio 中创建 AppX。  创建 AppX 后，可使用 [Windows Device Portal](../manage-your-device/DevicePortal.md) 来将其部署到 Windows 10 IoT 核心版设备。

若要调用后台应用程序, 可以执行以下操作之一:

* 如上所述，Visual Studio 的 F5 功能将部署并立即启动后台应用程序。

> [!NOTE]
> 这不会将后台应用程序配置为在设备启动时启动。

* 对于已部署到 IoT 设备的后台应用程序, 可以使用 iotstartup 实用程序将后台应用程序配置为在设备启动时启动。  若要将后台应用程序指定为启动应用程序, 请按照以下说明进行操作 (将`BackgroundApplication1`以下说明**替换为你的应用程序的名称**):

1. 通过 Windows IoT 核心版设备启动 PowerShell (PS) 会话，如[此处](../connect-your-device/PowerShell.md)所述。

2. 在 PS 会话中，键入：
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. 你应看到后台应用程序的完整名称, 例如:

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. 实用工具确认后台应用程序是 "无外设" 应用程序, 并且已正确安装。  你还可能看到后台应用程序的有外设项，但这可以忽略不计。

5. 现在，可轻松地将此应用设置为“启动应用”。 只需键入以下命令：

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. 实用程序将确认您的后台应用程序已添加到无外设 "启动应用程序" 列表中:

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. 继续下一步，然后重新启动 Windows IoT 核心版设备。 在 PS 会话中，可以发出关闭命令：

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. 设备重新启动后, 后台应用程序将自动启动, Windows 10 IoT Core 将确保它在任何时间停止时重新启动。  

> [!NOTE]
> 将后台应用注册为自动运行后, 如果应用退出或发生故障, 它将自动重新启动。  由于应用程序正在启动或重新启动, 因此, 如果想要在重新启动时执行特殊操作, 则需要在应用程序中跟踪应用程序状态。

9. 可以通过键入以下命令从无外设启动应用列表中删除后台应用程序:

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. 实用程序将确认您的后台应用程序已从无外设 "启动应用程序" 列表中删除:

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a>请参阅
若要在生成自定义映像时添加后台应用, 请参阅[创建 Appx 包](../build-your-image/createinstallpackage.md)
