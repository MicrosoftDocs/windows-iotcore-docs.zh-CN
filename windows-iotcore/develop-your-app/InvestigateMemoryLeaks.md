---
title: 调查内存泄漏
author: paulmon
ms.author: paulmon
ms.date: 09/20/2017
ms.topic: article
description: 了解如何使用集成诊断工具通过 Visual Studio 调查 Windows IoT 代码上的内存泄漏。
keywords: windows iot，Visual Studio，泄漏，故障排除
ms.openlocfilehash: f3a6651f163fbad332c6cfac2edd1de04fb54f9b
ms.sourcegitcommit: 05278f1a522ed498900ce15b98bdd4389b5dde55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88081622"
---
# <a name="investigating-memory-leaks"></a>调查内存泄漏

通过 Visual Studio 调查 Windows IoT Core 上的内存泄漏的最佳工具是集成的[诊断工具](https://docs.microsoft.com/visualstudio/profiling/memory-usage)

![诊断工具](../media/MemoryLeaks/DiagnosticTools.PNG)

对于前台应用程序，你可以[按照文档操作](https://docs.microsoft.com/visualstudio/profiling/memory-usage)。

但是，这些工具不会直接使用 Windows IoT Core**后台应用程序**。 分析后台应用程序中使用的代码的一种方法是将其包装在前台应用程序中进行分析：

1. 将**空白应用**添加到**后台应用**解决方案
2. 右键单击**空白应用**引用并添加对**后台应用**的引用
3. 将**后台应用**运行 ( # A1 方法，检查 taskInstance 参数是否为 null，并以不同的方式处理这些情况。
4. 从**BlankApp**调用 BackgroundApp：： Run (null) 
5. 在调用 BackgroundApp：： Run 时设置断点
6. 命中断点时，查找**诊断工具**窗口，然后单击 " ![ 快照" ](../media/MemoryLeaks/Snapshot.PNG) 按钮。

8. 重现问题
9. 拍摄另一个快照
10. 使用 "**诊断工具**" 窗口诊断泄露。

## <a name="create-a-test-app"></a>创建测试应用

让我们从分配内存的应用程序开始，而不释放内存来模拟泄露。
首先创建一个新的 c # 后台应用程序：[开发后台应用程序](./BackgroundApplications.md)

将 StartupTask.cs 中的代码替换为此
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

此时，如果你在 IoT 设备上运行后台应用程序，它应该会占用大量内存，并且永远不会释放。 如果此时尝试使用诊断工具，你将看到如下所示的内容，因为当前不支持使用带后台应用的工具。

![诊断工具后台应用](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

若要解决此情况，我们将向解决方案中添加一个前景应用。 在**解决方案资源管理器**右键单击解决方案文件夹，然后选择 "添加" "**新建项目**"。

![添加新项目](../media/MemoryLeaks/AddNewProject.png)

选择 " **Visual c # >Windows 通用>" 空白应用程序**"作为项目类型，为项目命名，然后单击 **" 确定 "**。

![添加新项目](../media/MemoryLeaks/NewForegroundApp.PNG)

右键单击新的前台应用项目的 "**引用**" 节点，然后选择 "**添加引用 ...** "

![添加新项目](../media/MemoryLeaks/AddReference.PNG)

在 "**引用管理器**" 对话框中，选择左窗格中的 "**项目**"。  在中心窗格中，在后台应用程序项目旁边的复选框中添加一个复选框，然后单击 **"确定"**。

![添加新项目](../media/MemoryLeaks/AddReferenceDialog.PNG)

接下来，右键单击前台应用项目，然后单击 "**设为启动项目**"。

![添加新项目](../media/MemoryLeaks/SetAsStartup.PNG)

添加代码以创建后台应用程序对象的实例，并以 null 作为唯一参数传入。
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

然后，在后台应用的 Run 方法中检查以确保 taskInstance 在使用之前不为 null。

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

1. 在对任务的调用上设置断点。运行 (null) 。
2. 设置计时器上的另一个断点。更改 StartupTask.cs 中 Timer_Tick 中 (超时。无限) 。
3. 按 F5 开始调试
4. 点击第一个断点时，请按 "快照" 按钮，设置比较基线

![快照](../media/MemoryLeaks/Snapshot.PNG)

5. 按 F5
6. 命中第二个断点时，请再次按 "快照" 按钮以捕获当前状态。

现在，诊断工具应显示一个图表，其中包含增加的内存使用情况和2个快照，如下所示：

![泄漏诊断工具](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

查看 "堆大小" 列中的第2行。 单击带有加号和向上键的第二个数字。 你应看到与下面类似的内容：

![快照表](../media/MemoryLeaks/Snapshot2_1.PNG)

按大小差异排序，使最大数值位于顶部，然后单击顶部的行。 在第二个详细信息表上方，单击 "**引用的类型**"。  第二个表现在应**显示 \<Byte[]\> 列表**作为所有内存使用情况的源。

![快照表](../media/MemoryLeaks/Snapshot2_2.PNG)
