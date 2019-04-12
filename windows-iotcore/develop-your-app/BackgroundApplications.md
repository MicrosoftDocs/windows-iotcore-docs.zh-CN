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
# <a name="developing-background-applications"></a>开发后台应用程序

> [!NOTE]
> 部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。

后台应用程序是具有没有直接的用户界面的应用程序。 部署和配置完成后，这些应用程序将在计算机启动时启动，并将持续运行，不受任何进程生命期管理资源使用的限制。 如果这些应用程序崩溃或退出，系统将自动重新启动它们。
这些后台应用程序有一个非常简单的执行模型。 模板将创建实现“IBackgroundTask”接口并生成空的“运行”方法的类。 此“运行”方法将是通向你的应用程序的入口点。

![后台任务](../media/BackgroundApplications/backgroundTaskScreenshot.png)

需特别注意的一点是，默认情况下，应用程序将在运行方法完成时关闭。 这意味着遵循运行等待输入或在计时器上的服务器的常用 IoT 模式的应用将会过早地发现应用退出这一情况。 若要阻止这种情况发生，必须调用“GetDeferral”方法才能阻止应用程序退出。 可在[此处](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)查找有关延迟模式的详细信息。

## <a name="where-can-background-applications-be-installed-from"></a>后台应用程序可从何处安装？ 

可在[此处](https://go.microsoft.com/fwlink/?linkid=847472)从 Visual Studio 库中下载并安装 IoT 模板以启用后台应用程序。  或者，可通过在 [Visual Studio 库](https://visualstudiogallery.msdn.microsoft.com/)中或直接从“扩展和更新”对话框（“工具”>“扩展和更新”>“联机”）中的 Visual Studio 搜索 `Windows IoT Core Project Templates` 来找到模板。

## <a name="what-languages-are-available"></a>哪些语言可用？

可找到采用以下语言的**后台应用程序 (IoT)** 模板：

* **C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a>如何使用后台应用程序？ 

创建后台应用程序是非常类似于创建后台任务。  在启动后台应用程序时，将调用运行方法：

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

Run 方法结束时，除非创建延迟对象，否则，后台应用程序结束。 针对异步编程，常见做法是使用延迟，如下所示：

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

执行延迟之后, 的后台应用程序将继续，直到调用延迟对象的完整方法。

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a>如何启动后台应用程序？

此问题可分解为部署和调用两个方面。  

若要部署的后台应用程序，您可以：

* 使用 Visual Studio 的 F5（将生成、部署和调用）。  有关更多详细信息，请参阅我们[Hello World 示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld)我们介绍如何部署和启动 Visual Studio 中的位置。

> [!NOTE]
> 这不会将配置您的后台应用程序以启动设备启动时。

* 通过依次选择“项目”>“应用商店”>“创建应用包”，在 Visual Studio 中创建 AppX。  创建 AppX 后，可使用 [Windows Device Portal](../manage-your-device/DevicePortal.md) 来将其部署到 Windows 10 IoT 核心版设备。

若要调用的后台应用程序，您可以：

* 如上所述，Visual Studio 的 F5 功能将部署并立即启动后台应用程序。

> [!NOTE]
> 这不会将配置您的后台应用程序以启动设备启动时。

* 有关已部署到 IoT 设备的后台应用程序，您可以使用 iotstartup.exe 实用工具来配置后台应用程序，以启动设备启动时。  若要指定启动应用程序作为后台应用程序，请按照这些说明进行操作 (**替换为你的应用名称**为`BackgroundApplication1`下面):

1. 通过 Windows IoT 核心版设备启动 PowerShell (PS) 会话，如[此处](../connect-your-device/PowerShell.md)所述。

2. 在 PS 会话中，键入：
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. 如下所示，应即查看后台应用程序的完整名称：

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. 该实用工具确认后台应用程序是一个无外设应用程序，以及正确安装。  你还可能看到后台应用程序的有外设项，但这可以忽略不计。

5. 现在，可轻松地将此应用设置为“启动应用”。 只需键入以下命令：

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. 该实用工具将确认已将后台应用程序添加到的无外设启动应用列表：

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. 继续下一步，然后重新启动 Windows IoT 核心版设备。 在 PS 会话中，可以发出关闭命令：

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. 设备已重新启动后，后台应用程序会自动启动和 Windows 10 IoT Core 会确保它获取随时停止时的重启。  

> [!NOTE]
> 后台应用注册来自动运行，如果应用程序退出或出现故障后它将自动重新启动。  应用程序不被通知它正在启动或重新启动，如果你想要重新启动您将需要跟踪应用程序状态应用程序中的对其执行特殊操作的原因。

9. 通过键入命令，可以从列表中的无外设启动应用程序删除后台应用程序：

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. 该实用工具将确认已从无外设启动应用列表中删除了后台应用程序：

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a>请参阅
若要添加的后台应用程序时生成自定义映像，请参阅[创建 Appx 包](../build-your-image/createinstallpackage.md)
