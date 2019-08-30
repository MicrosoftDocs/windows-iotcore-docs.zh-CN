---
title: 调查内存泄漏
author: paulmon
ms.author: paulmon
ms.date: 09/20/2017
ms.topic: article
description: 了解如何调查内存泄漏。
keywords: windows iot, Visual Studio, 泄漏, 故障排除
ms.openlocfilehash: 8385ae621c18c079d0a2ec7bf7b0b4042359eccc
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168533"
---
# <a name="investigating-memory-leaks"></a><span data-ttu-id="1539e-104">调查内存泄漏</span><span class="sxs-lookup"><span data-stu-id="1539e-104">Investigating Memory Leaks</span></span>

<span data-ttu-id="1539e-105">通过 Visual Studio 调查 Windows IoT Core 上的内存泄漏的最佳工具是集成的[诊断工具](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span><span class="sxs-lookup"><span data-stu-id="1539e-105">The best tool for investigating memory leaks on Windows IoT Core with Visual Studio is the integrated [Diagnostic Tools](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span></span>

![诊断工具](../media/MemoryLeaks/DiagnosticTools.PNG)

<span data-ttu-id="1539e-107">对于前台应用程序, 你可以[按照文档操作](https://docs.microsoft.com/visualstudio/profiling/memory-usage)。</span><span class="sxs-lookup"><span data-stu-id="1539e-107">For foreground applications you can [follow the documentation](https://docs.microsoft.com/visualstudio/profiling/memory-usage).</span></span>

<span data-ttu-id="1539e-108">但是, 这些工具不会直接使用 Windows IoT Core**后台应用程序**。</span><span class="sxs-lookup"><span data-stu-id="1539e-108">However, these tools don't work directly with a Windows IoT Core **Background Application**.</span></span> <span data-ttu-id="1539e-109">分析后台应用程序中使用的代码的一种方法是将其包装在前台应用程序中进行分析:</span><span class="sxs-lookup"><span data-stu-id="1539e-109">One way to profile code used in a background application is to wrap it in a foreground app for analysis:</span></span>

1. <span data-ttu-id="1539e-110">将**空白应用**添加到**后台应用**解决方案</span><span class="sxs-lookup"><span data-stu-id="1539e-110">Add a **Blank App** to the **Background App** solution</span></span>
2. <span data-ttu-id="1539e-111">右键单击**空白应用**引用并添加对**后台应用**的引用</span><span class="sxs-lookup"><span data-stu-id="1539e-111">Right-click the **Blank App** references and add a reference to the **Background App**</span></span>
3. <span data-ttu-id="1539e-112">更改**后台应用**Run () 方法, 检查 taskInstance 参数是否为 null, 并以不同的方式处理这些情况。</span><span class="sxs-lookup"><span data-stu-id="1539e-112">Change the **Background App** Run() method to check if the taskInstance parameter is null and handle those cases differently.</span></span>
4. <span data-ttu-id="1539e-113">从**BlankApp**调用 BackgroundApp:: Run (null)</span><span class="sxs-lookup"><span data-stu-id="1539e-113">From the **BlankApp** call BackgroundApp::Run(null)</span></span>
5. <span data-ttu-id="1539e-114">在调用 BackgroundApp:: Run 时设置断点</span><span class="sxs-lookup"><span data-stu-id="1539e-114">Set a breakpoint on the call to BackgroundApp::Run</span></span>
6. <span data-ttu-id="1539e-115">命中断点时, 查找**诊断工具**窗口, 然后单击 "快照![](../media/MemoryLeaks/Snapshot.PNG) " 按钮。</span><span class="sxs-lookup"><span data-stu-id="1539e-115">When the breakpoint is hit find the **Diagnostic Tools** windows and click the ![Snapshot](../media/MemoryLeaks/Snapshot.PNG) button.</span></span>

8. <span data-ttu-id="1539e-116">重现问题</span><span class="sxs-lookup"><span data-stu-id="1539e-116">Reproduce the problem</span></span>
9. <span data-ttu-id="1539e-117">拍摄另一个快照</span><span class="sxs-lookup"><span data-stu-id="1539e-117">Take another snapshot</span></span>
10. <span data-ttu-id="1539e-118">使用 "**诊断工具**" 窗口诊断泄露。</span><span class="sxs-lookup"><span data-stu-id="1539e-118">Use the **Diagnostic Tools** window to diagnose the leak.</span></span>

## <a name="create-a-test-app"></a><span data-ttu-id="1539e-119">创建测试应用</span><span class="sxs-lookup"><span data-stu-id="1539e-119">Create a test app</span></span>

<span data-ttu-id="1539e-120">让我们从分配内存的应用程序开始, 而不释放内存来模拟泄露。</span><span class="sxs-lookup"><span data-stu-id="1539e-120">Let's start with an application that allocates memory and doesn't free it to simulate a leak.</span></span>
<span data-ttu-id="1539e-121">首先创建一个新C#的后台应用程序:[开发后台应用程序](./BackgroundApplications.md)</span><span class="sxs-lookup"><span data-stu-id="1539e-121">Begin by creating a new C# Background application: [Developing Background Applications](./BackgroundApplications.md)</span></span>

<span data-ttu-id="1539e-122">将 StartupTask.cs 中的代码替换为此</span><span class="sxs-lookup"><span data-stu-id="1539e-122">Replace the code in StartupTask.cs with this</span></span>
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

<span data-ttu-id="1539e-123">此时, 如果你在 IoT 设备上运行后台应用程序, 它应该会占用大量内存, 并且永远不会释放。</span><span class="sxs-lookup"><span data-stu-id="1539e-123">At this point if you run the background application on your IoT device it should use up a lot of memory and never free it.</span></span> <span data-ttu-id="1539e-124">如果此时尝试使用诊断工具, 你将看到如下所示的内容, 因为当前不支持使用带后台应用的工具。</span><span class="sxs-lookup"><span data-stu-id="1539e-124">If you try to use the diagnostic tools at this point you will see something that looks like this, because using the tools with background apps is currently unsupported.</span></span>

![诊断工具后台应用](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

<span data-ttu-id="1539e-126">若要解决此情况, 我们将向解决方案中添加一个前景应用。</span><span class="sxs-lookup"><span data-stu-id="1539e-126">To work around this we are going to add a foreground app to the solution.</span></span> <span data-ttu-id="1539e-127">在**解决方案资源管理器**右键单击解决方案文件夹, 然后选择 "添加" "**新建项目**"。</span><span class="sxs-lookup"><span data-stu-id="1539e-127">In the **Solution Explorer** right-click on the solution folder and then select **Add.New Project**.</span></span>

![添加新项目](../media/MemoryLeaks/AddNewProject.png)

<span data-ttu-id="1539e-129">选择 **" C#Visual > Windows 通用 >" 空白应用程序**作为项目类型, 为项目命名, 然后单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="1539e-129">Choose **Visual C#>Windows Universal>Blank App** as the project type, name your project and click **OK**.</span></span>

![添加新项目](../media/MemoryLeaks/NewForegroundApp.PNG)

<span data-ttu-id="1539e-131">右键单击新的前台应用项目的 "**引用**" 节点, 然后选择 "**添加引用 ...** "</span><span class="sxs-lookup"><span data-stu-id="1539e-131">Right-click on the new foreground app project's **References** node and select **Add Reference...**</span></span>

![添加新项目](../media/MemoryLeaks/AddReference.PNG)

<span data-ttu-id="1539e-133">在 "**引用管理器**" 对话框中, 选择左窗格中的 "**项目**"。</span><span class="sxs-lookup"><span data-stu-id="1539e-133">In the **Reference Manager** dialog choose **Projects** in the left-hand pane.</span></span>  <span data-ttu-id="1539e-134">在中心窗格中, 在后台应用程序项目旁边的复选框中添加一个复选框, 然后单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="1539e-134">In the center pane add a check in the checkbox next to your background application project and click **OK**.</span></span>

![添加新项目](../media/MemoryLeaks/AddReferenceDialog.PNG)

<span data-ttu-id="1539e-136">接下来, 右键单击前台应用项目, 然后单击 "**设为启动项目**"。</span><span class="sxs-lookup"><span data-stu-id="1539e-136">Next right-click the foreground app project and click **Set as StartUp Project**.</span></span>

![添加新项目](../media/MemoryLeaks/SetAsStartup.PNG)

<span data-ttu-id="1539e-138">添加代码以创建后台应用程序对象的实例, 并以 null 作为唯一参数传入。</span><span class="sxs-lookup"><span data-stu-id="1539e-138">Add code to create an instance of your background application object and call Run passing in null as the only parameter.</span></span>
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

<span data-ttu-id="1539e-139">然后, 在后台应用的 Run 方法中检查以确保 taskInstance 在使用之前不为 null。</span><span class="sxs-lookup"><span data-stu-id="1539e-139">Then in your background app's Run method check to make sure taskInstance is not null before using it.</span></span>

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

1. <span data-ttu-id="1539e-140">在对任务的调用上设置断点。运行 (null)。</span><span class="sxs-lookup"><span data-stu-id="1539e-140">Set a breakpoint on the call to task.Run(null).</span></span>
2. <span data-ttu-id="1539e-141">设置计时器上的另一个断点。在 StartupTask.cs 的 Timer_Tick 中更改 (Timeout, 无限大, 无限大)。</span><span class="sxs-lookup"><span data-stu-id="1539e-141">Set another breakpoint on timer.Change(Timeout.Infinite, Timeout.Infinite) in Timer_Tick in StartupTask.cs.</span></span>
3. <span data-ttu-id="1539e-142">按 F5 开始调试</span><span class="sxs-lookup"><span data-stu-id="1539e-142">Press F5 to begin debugging</span></span>
4. <span data-ttu-id="1539e-143">点击第一个断点时, 请按 "快照" 按钮, 设置比较基线</span><span class="sxs-lookup"><span data-stu-id="1539e-143">When you hit the first breakpoint press the snapshot button to set the baseline to compare against</span></span>

![快照](../media/MemoryLeaks/Snapshot.PNG)

5. <span data-ttu-id="1539e-145">按 F5</span><span class="sxs-lookup"><span data-stu-id="1539e-145">Press F5</span></span>
6. <span data-ttu-id="1539e-146">命中第二个断点时, 请再次按 "快照" 按钮以捕获当前状态。</span><span class="sxs-lookup"><span data-stu-id="1539e-146">When you hit the second breakpoint press the snapshot button again to capture the current state.</span></span>

<span data-ttu-id="1539e-147">现在, 诊断工具应显示一个图表, 其中包含增加的内存使用情况和2个快照, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="1539e-147">Now the diagnostic tools should show a graph with increasing memory use and 2 snapshot like this:</span></span>

![泄漏诊断工具](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

<span data-ttu-id="1539e-149">查看 "堆大小" 列中的第2行。</span><span class="sxs-lookup"><span data-stu-id="1539e-149">Look at row 2 in the Heap Size column.</span></span> <span data-ttu-id="1539e-150">单击带有加号和向上键的第二个数字。</span><span class="sxs-lookup"><span data-stu-id="1539e-150">Click the second number with the plus sign and up arrow.</span></span> <span data-ttu-id="1539e-151">你应该会看到如下内容：</span><span class="sxs-lookup"><span data-stu-id="1539e-151">You should see something like this:</span></span>

![快照表](../media/MemoryLeaks/Snapshot2_1.PNG)

<span data-ttu-id="1539e-153">按大小差异排序, 使最大数值位于顶部, 然后单击顶部的行。</span><span class="sxs-lookup"><span data-stu-id="1539e-153">Sort by size diff so that the largest number is at the top, then click the top row.</span></span> <span data-ttu-id="1539e-154">在第二个详细信息表上方, 单击 "**引用的类型**"。</span><span class="sxs-lookup"><span data-stu-id="1539e-154">Above the second detail table click **Referenced Types**.</span></span>  <span data-ttu-id="1539e-155">第二个表现在应**将\<List Byte [\> ]** 显示为所有内存使用情况的源。</span><span class="sxs-lookup"><span data-stu-id="1539e-155">The second table should now show **List\<Byte[]\>** as the source of all the memory usage.</span></span>

![快照表](../media/MemoryLeaks/Snapshot2_2.PNG)
