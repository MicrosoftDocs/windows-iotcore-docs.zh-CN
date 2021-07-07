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
# <a name="developing-background-applications"></a>开发后台应用程序

> [!NOTE]
> 在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。

后台应用程序是没有直接 UI 的应用程序。 部署和配置后，这些应用程序在计算机启动时启动并持续运行，没有任何进程生存期管理资源使用限制。 如果它们崩溃或退出，系统将自动重启它们。
这些后台应用程序具有非常简单的执行模型。 这些模板创建一个实现"IBackgroundTask"接口的类，并生成空的"Run"方法。 此"运行"方法是应用程序的入口点。

![后台任务](../media/BackgroundApplications/backgroundTaskScreenshot.png)

有一个关键点需要注意：默认情况下，应用程序将在运行方法完成时关闭。 这意味着，遵循运行服务器等待输入或计时器的常见 IoT 模式的应用将发现应用提前退出。 若要防止发生这种情况，必须调用"GetDeferral"方法来阻止应用程序退出。 可在此处找到有关延迟模式 [详细信息](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)。

## <a name="where-can-background-applications-be-installed-from"></a>后台应用程序可以从何处安装？ 

可以从此处的 Visual Studio 库下载并安装 IoT 模板以启用[后台应用程序](https://go.microsoft.com/fwlink/?linkid=847472)。  或者，可以通过在 Visual Studio 库中搜索 或直接从 Visual Studio 对话框的 (Tools > `Windows IoT Core Project Templates` Extensions and Updates > Online) [](https://visualstudiogallery.msdn.microsoft.com/)找到模板。

## <a name="what-languages-are-available"></a>哪些语言可用？

**可以在 (IoT)** 模板的后台应用程序：

* **C++**`File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a>如何使用后台应用程序？ 

创建后台应用程序与创建后台任务非常相似。  后台应用程序启动时，将调用 Run 方法：

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

Run 方法结束时，除非创建延迟对象，否则后台应用程序将结束。 异步编程的常见做法是接受如下所示的延迟：

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

执行延迟后，后台应用程序将继续运行，直到调用 deferral 对象的 Complete 方法。

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a>后台应用程序如何启动？

此问题可以分解为部署和调用。  

若要部署后台应用程序，可以：

* 使用Visual Studio F5 (，这将生成、部署和调用) 。  有关更多详细信息，[请参阅Hello World示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld)，其中介绍了如何从 Visual Studio。

> [!NOTE]
> 这不会将后台应用程序配置为在设备启动时启动。

* 通过在"创建应用包"Visual Studio选择"Project >应用商店> AppX。  创建 AppX 后，可以使用[Windows 设备门户将其部署到](../manage-your-device/DevicePortal.md)Windows 10 IoT 核心版 设备。

若要调用后台应用程序，可以：

* 如上所述，Visual Studio F5 功能将部署并立即启动后台应用程序。

> [!NOTE]
> 这不会将后台应用程序配置为在设备启动时启动。

* 对于已部署到 IoT 设备的后台应用程序，可以使用 iotstartup.exe 实用工具将后台应用程序配置为在设备启动时启动。  若要将后台应用程序指定为启动应用，请按照以下说明 (将应用的名称替换为 `BackgroundApplication1` 以下) ：

1. 启动 PowerShell (PS) 会话Windows IoT Core 设备，[如此处所述](../connect-your-device/PowerShell.md)。

2. 在 PS 会话中，键入：
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. 应会看到后台应用程序的全名，例如：

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. 实用工具正在确认后台应用程序是"无头"应用程序，并且已正确安装。  你很可能会看到后台应用程序的"前向"条目，但可能会忽略此条目。

5. 现在，可以轻松将此应用设置为"启动应用"。 只需键入命令：

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. 实用工具将确认后台应用程序已添加到无头"启动应用"列表：

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. 继续重启 IoT 核心Windows设备。 在 PS 会话中，可以发出 shutdown 命令：

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. 重启设备后，后台应用程序将自动启动，Windows 10 IoT 核心版确保它随时停止时重启。  

> [!NOTE]
> 将后台应用注册为自动运行后，如果应用退出或崩溃，它将自动重启。  不会通知应用启动或重启的原因，因此，如果要在重启时采取特殊操作，则需要跟踪应用中的应用状态。

9. 可以通过键入命令从无头启动应用列表中删除后台应用程序：

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. 实用工具将确认背景应用程序已从无头"启动应用"列表中删除：

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

## <a name="see-also"></a>另请参阅
若要在生成自定义映像时添加后台应用，请参阅 [创建 Appx 包](../build-your-image/createinstallpackage.md)
