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
# <a name="developing-background-applications"></a>开发后台应用程序

> [!NOTE]
> 在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。

后台应用程序是没有直接 UI 的应用程序。 部署和配置后，这些应用程序在计算机启动时启动并连续运行，而不会有任何进程生存期管理资源使用限制。 如果系统崩溃或退出，系统会自动重新启动它们。
这些后台应用程序的执行模型非常简单。 模板创建一个实现 "IBackgroundTask" 接口的类，并生成空的 "Run" 方法。 此 "运行" 方法是应用程序的入口点。

![后台任务](../media/BackgroundApplications/backgroundTaskScreenshot.png)

需要注意的一点是：默认情况下，当 run 方法完成时，应用程序将关闭。 这意味着，遵循运行等待输入的服务器或在计时器上的常见 IoT 模式的应用会提前发现应用退出。 若要防止此情况发生，必须调用 "GetDeferral" 方法，以防止应用程序退出。 可在 [此处](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)找到有关延期模式的详细信息。

## <a name="where-can-background-applications-be-installed-from"></a>后台应用程序的安装位置 

你可以从 Visual [Studio 库下载](https://go.microsoft.com/fwlink/?linkid=847472)并安装 IoT 模板来启用后台应用程序。  此外，还可以通过在 `Windows IoT Core Project Templates` [Visual studio 库](https://visualstudiogallery.msdn.microsoft.com/) 中搜索或直接从 visual Studio 的 "扩展和更新" 对话框中的 visual studio 查找模板， (工具 > 扩展和更新 > 联机) 。

## <a name="what-languages-are-available"></a>可用的语言有哪些？

可在以下内容中找到**后台应用程序 (IoT) **模板：

* **C + +**`File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a>后台应用程序如何使用？ 

创建后台应用程序非常类似于创建后台任务。  后台应用程序启动时，将调用 Run 方法：

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

当 Run 方法结束时，除非创建延迟对象，否则后台应用程序将结束。 异步编程的常见做法是按如下所示延迟：

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

延迟完成后，后台应用程序将继续运行，直到调用延迟对象的完整方法。

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a>后台应用程序如何启动？

此问题可能会被分解为部署和调用。  

若要部署后台应用程序，可以执行以下操作之一：

* 使用 Visual Studio 的 F5 (将生成、部署和调用) 。  有关更多详细信息，请参阅我们的 [Hello World 示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) ，其中介绍了如何从 Visual Studio 部署和启动。

> [!NOTE]
> 这不会将后台应用程序配置为在设备启动时启动。

* 在 Visual Studio 中创建 AppX，方法是选择 "项目 > 存储" > 创建应用包 "。  创建 AppX 后，可以使用 [Windows 设备门户](../manage-your-device/DevicePortal.md) 将其部署到 Windows 10 IoT Core 设备。

若要调用后台应用程序，可以执行以下操作之一：

* 如上所述，Visual Studio 的 F5 功能将部署并立即启动后台应用程序。

> [!NOTE]
> 这不会将后台应用程序配置为在设备启动时启动。

* 对于已部署到 IoT 设备的后台应用程序，可以使用 iotstartup.exe 实用程序将后台应用程序配置为在设备启动时启动。  若要将后台应用程序指定为启动应用程序，请按照以下说明 (**将应用程序的名称替换** `BackgroundApplication1`) ：

1. 如 [此处](../connect-your-device/PowerShell.md)所述，使用 Windows IoT Core 设备启动 POWERSHELL (PS) 会话。

2. 在 PS 会话中键入：
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. 你应看到后台应用程序的完整名称，例如：

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. 实用工具确认后台应用程序是 "无外设" 应用程序，并且已正确安装。  你可能还会看到适用于你的后台应用程序的头条目，但这可能会被忽略。

5. 现在，可以轻松地将此应用程序设置为 "启动应用程序"。 只需键入命令：

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. 实用程序将确认您的后台应用程序已添加到无外设 "启动应用程序" 列表中：

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. 继续重启 Windows IoT Core 设备。 通过 PS 会话，可以发出 shutdown 命令：

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. 设备重新启动后，后台应用程序将自动启动，Windows 10 IoT Core 将确保它在任何时间停止时重新启动。  

> [!NOTE]
> 将后台应用注册为自动运行后，如果应用退出或发生故障，它将自动重新启动。  由于应用程序正在启动或重新启动，因此，如果想要在重新启动时执行特殊操作，则需要在应用程序中跟踪应用程序状态。

9. 可以通过键入以下命令从无外设启动应用列表中删除后台应用程序：

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. 实用程序将确认您的后台应用程序已从无外设 "启动应用程序" 列表中删除：

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

## <a name="see-also"></a>另请参阅
若要在生成自定义映像时添加后台应用，请参阅 [创建 Appx 包](../build-your-image/createinstallpackage.md)
