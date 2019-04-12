---
title: 调查内存泄漏
author: paulmon
ms.author: paulmon
ms.date: 09/20/2017
ms.topic: article
description: 了解如何调查内存泄漏。
keywords: windows iot，Visual Studio 中，泄漏，故障排除
ms.openlocfilehash: 8385ae621c18c079d0a2ec7bf7b0b4042359eccc
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510729"
---
# <a name="investigating-memory-leaks"></a>调查内存泄漏

调查使用 Visual Studio Windows IoT Core 上的内存泄漏的最佳工具是集成[诊断工具](https://docs.microsoft.com/visualstudio/profiling/memory-usage)

![诊断工具](../media/MemoryLeaks/DiagnosticTools.PNG)

可以为前台应用程序[按照文档说明](https://docs.microsoft.com/visualstudio/profiling/memory-usage)。

但是，这些工具不能直接与 Windows IoT Core**后台应用程序**。 后台应用程序中使用的分析代码的一种方法是将其包装在前台应用程序以进行分析：

1. 添加**空白应用**到**背景应用**解决方案
2. 右键单击**空白应用**引用，然后添加对引用**背景应用**
3. 更改**后台应用**run （） 方法检查 taskInstance 参数是否为 null，并处理这些情况下，以不同的方式。
4. 从**BlankApp**调用 BackgroundApp::Run(null)
5. 对 BackgroundApp::Run 调用上设置断点
6. 当命中断点时发现**诊断工具**windows 和单击![快照](../media/MemoryLeaks/Snapshot.PNG)按钮。

8. 重现此问题
9. 创建另一个快照
10. 使用**诊断工具**窗口进行诊断泄漏。

## <a name="create-a-test-app"></a>创建一个测试应用

让我们开始分配内存并不会释放它模拟了泄漏的应用程序。
首先，创建一个新C#后台应用程序：[开发后台应用程序](./BackgroundApplications.md)

与此替换 StartupTask.cs 中的代码
```C#
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Threading;
using Windows.ApplicationModel.Background;
using Windows.System;

namespace LeakyBackgroundApp
{
    public sealed class StartupTask : IBackgroundTask
    {
        private Timer timer;
        private BackgroundTaskDeferral deferral;
        List<byte[]> buffer = new List<byte[]>();
        private const ulong minRemaining = 300 * 1024 * 1024;

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            deferral = taskInstance.GetDeferral();
            timer = new Timer(Timer_Tick, null, 500, 500);
        }

        private void Timer_Tick(object state)
        {
            ulong remaining = (MemoryManager.AppMemoryUsageLimit - MemoryManager.AppMemoryUsage);
            ulong chunkSize = remaining / 100;

            try
            {
                if (remaining > minRemaining)
                {
                    var chunk = new byte[chunkSize];

                    // force virtual memory to be commited by writing to it
                    for (int i = 0; i < chunk.Length; i += 4096)
                    {
                        chunk[i] = 0xDA;
                    }

                    // "leak" memory by adding it to the list
                    buffer.Add(chunk);
                    Debug.WriteLine(String.Format("Allocated {0} chunk(s)", buffer.Count));
                }
                else
                {
                    timer.Change(Timeout.Infinite, Timeout.Infinite);
                }
            }
            catch (OutOfMemoryException ex)
            {
                Debug.Write(ex.Message);
                timer.Change(Timeout.Infinite, Timeout.Infinite);
            }
        }
    }
}
```

此时在 IoT 设备上运行的后台应用程序如果它应会消耗大量内存并永远不会释放它。 如果尝试使用诊断工具现在您将看到类似如下所示，因为当前不支持与后台应用程序使用的工具。

![诊断工具后台应用程序](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

若要解决此我们要将前台应用程序添加到解决方案。 在中**解决方案资源管理器**右键单击解决方案文件夹，然后选择**Add.New 项目**。

![添加新项目](../media/MemoryLeaks/AddNewProject.png)

选择**可视化C#> Windows 通用 > 空白应用**作为项目类型，命名你的项目，然后单击**确定**。

![添加新项目](../media/MemoryLeaks/NewForegroundApp.PNG)

右键单击新前台应用程序项目的**引用**节点，然后选择**添加引用...**

![添加新项目](../media/MemoryLeaks/AddReference.PNG)

在中**引用管理器**对话框中，选择**项目**的左窗格中。  在中心窗格中在后台应用程序项目旁边的复选框中添加检查，然后单击**确定**。

![添加新项目](../media/MemoryLeaks/AddReferenceDialog.PNG)

接下来右键单击前台应用程序项目，然后单击**设为启动项目**。

![添加新项目](../media/MemoryLeaks/SetAsStartup.PNG)

添加代码以创建您的后台应用程序对象的实例并调用 Run 传递空值作为唯一参数。
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

然后在后台应用程序的运行方法检查并确保 taskInstance 不为 null 然后再使用它。

```C#
public void Run(IBackgroundTaskInstance taskInstance)
{
    if (taskInstance != null)
    {
        deferral = taskInstance.GetDeferral();
    }

    timer = new Timer(Timer_Tick, null, 500, 500);
}
```

1. 对任务的调用上设置断点。Run(null)。
2. 设置计时器另一个断点。在中 StartupTask.cs Timer_Tick 中的更改 （Timeout.Infinite，Timeout.Infinite）。
3. 按 F5 开始调试
4. 当命中第一个断点按快照按钮以设置要比较的基线

![快照](../media/MemoryLeaks/Snapshot.PNG)

5. 按 F5
6. 当你命中第二个断点按快照按钮再次捕获的当前状态。

现在的诊断工具应显示具有增加内存使用和 2 个快照，像这样的关系图：

![与泄漏的诊断工具](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

查看堆大小列中的第 2 行。 单击包含加号和向上键的第二个数字。 你应该会看到如下内容：

![快照表](../media/MemoryLeaks/Snapshot2_1.PNG)

按大小差异排序，以便最大数量是在顶部，然后单击顶部的行。 第二个详细信息表上单击**引用的类型**。  现在应显示第二个表**列表\<Byte []\>** 作为所有的内存使用率的源。

![快照表](../media/MemoryLeaks/Snapshot2_2.PNG)
