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
# <a name="investigating-memory-leaks"></a><span data-ttu-id="5b665-104">调查内存泄漏</span><span class="sxs-lookup"><span data-stu-id="5b665-104">Investigating Memory Leaks</span></span>

<span data-ttu-id="5b665-105">调查使用 Visual Studio Windows IoT Core 上的内存泄漏的最佳工具是集成[诊断工具](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span><span class="sxs-lookup"><span data-stu-id="5b665-105">The best tool for investigating memory leaks on Windows IoT Core with Visual Studio is the integrated [Diagnostic Tools](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span></span>

![诊断工具](../media/MemoryLeaks/DiagnosticTools.PNG)

<span data-ttu-id="5b665-107">可以为前台应用程序[按照文档说明](https://docs.microsoft.com/visualstudio/profiling/memory-usage)。</span><span class="sxs-lookup"><span data-stu-id="5b665-107">For foreground applications you can [follow the documentation](https://docs.microsoft.com/visualstudio/profiling/memory-usage).</span></span>

<span data-ttu-id="5b665-108">但是，这些工具不能直接与 Windows IoT Core**后台应用程序**。</span><span class="sxs-lookup"><span data-stu-id="5b665-108">However, these tools don't work directly with a Windows IoT Core **Background Application**.</span></span> <span data-ttu-id="5b665-109">后台应用程序中使用的分析代码的一种方法是将其包装在前台应用程序以进行分析：</span><span class="sxs-lookup"><span data-stu-id="5b665-109">One way to profile code used in a background application is to wrap it in a foreground app for analysis:</span></span>

1. <span data-ttu-id="5b665-110">添加**空白应用**到**背景应用**解决方案</span><span class="sxs-lookup"><span data-stu-id="5b665-110">Add a **Blank App** to the **Background App** solution</span></span>
2. <span data-ttu-id="5b665-111">右键单击**空白应用**引用，然后添加对引用**背景应用**</span><span class="sxs-lookup"><span data-stu-id="5b665-111">Right-click the **Blank App** references and add a reference to the **Background App**</span></span>
3. <span data-ttu-id="5b665-112">更改**后台应用**run （） 方法检查 taskInstance 参数是否为 null，并处理这些情况下，以不同的方式。</span><span class="sxs-lookup"><span data-stu-id="5b665-112">Change the **Background App** Run() method to check if the taskInstance parameter is null and handle those cases differently.</span></span>
4. <span data-ttu-id="5b665-113">从**BlankApp**调用 BackgroundApp::Run(null)</span><span class="sxs-lookup"><span data-stu-id="5b665-113">From the **BlankApp** call BackgroundApp::Run(null)</span></span>
5. <span data-ttu-id="5b665-114">对 BackgroundApp::Run 调用上设置断点</span><span class="sxs-lookup"><span data-stu-id="5b665-114">Set a breakpoint on the call to BackgroundApp::Run</span></span>
6. <span data-ttu-id="5b665-115">当命中断点时发现**诊断工具**windows 和单击![快照](../media/MemoryLeaks/Snapshot.PNG)按钮。</span><span class="sxs-lookup"><span data-stu-id="5b665-115">When the breakpoint is hit find the **Diagnostic Tools** windows and click the ![Snapshot](../media/MemoryLeaks/Snapshot.PNG) button.</span></span>

8. <span data-ttu-id="5b665-116">重现此问题</span><span class="sxs-lookup"><span data-stu-id="5b665-116">Reproduce the problem</span></span>
9. <span data-ttu-id="5b665-117">创建另一个快照</span><span class="sxs-lookup"><span data-stu-id="5b665-117">Take another snapshot</span></span>
10. <span data-ttu-id="5b665-118">使用**诊断工具**窗口进行诊断泄漏。</span><span class="sxs-lookup"><span data-stu-id="5b665-118">Use the **Diagnostic Tools** window to diagnose the leak.</span></span>

## <a name="create-a-test-app"></a><span data-ttu-id="5b665-119">创建一个测试应用</span><span class="sxs-lookup"><span data-stu-id="5b665-119">Create a test app</span></span>

<span data-ttu-id="5b665-120">让我们开始分配内存并不会释放它模拟了泄漏的应用程序。</span><span class="sxs-lookup"><span data-stu-id="5b665-120">Let's start with an application that allocates memory and doesn't free it to simulate a leak.</span></span>
<span data-ttu-id="5b665-121">首先，创建一个新C#后台应用程序：[开发后台应用程序](./BackgroundApplications.md)</span><span class="sxs-lookup"><span data-stu-id="5b665-121">Begin by creating a new C# Background application: [Developing Background Applications](./BackgroundApplications.md)</span></span>

<span data-ttu-id="5b665-122">与此替换 StartupTask.cs 中的代码</span><span class="sxs-lookup"><span data-stu-id="5b665-122">Replace the code in StartupTask.cs with this</span></span>
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

<span data-ttu-id="5b665-123">此时在 IoT 设备上运行的后台应用程序如果它应会消耗大量内存并永远不会释放它。</span><span class="sxs-lookup"><span data-stu-id="5b665-123">At this point if you run the background application on your IoT device it should use up a lot of memory and never free it.</span></span> <span data-ttu-id="5b665-124">如果尝试使用诊断工具现在您将看到类似如下所示，因为当前不支持与后台应用程序使用的工具。</span><span class="sxs-lookup"><span data-stu-id="5b665-124">If you try to use the diagnostic tools at this point you will see something that looks like this, because using the tools with background apps is currently unsupported.</span></span>

![诊断工具后台应用程序](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

<span data-ttu-id="5b665-126">若要解决此我们要将前台应用程序添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="5b665-126">To work around this we are going to add a foreground app to the solution.</span></span> <span data-ttu-id="5b665-127">在中**解决方案资源管理器**右键单击解决方案文件夹，然后选择**Add.New 项目**。</span><span class="sxs-lookup"><span data-stu-id="5b665-127">In the **Solution Explorer** right-click on the solution folder and then select **Add.New Project**.</span></span>

![添加新项目](../media/MemoryLeaks/AddNewProject.png)

<span data-ttu-id="5b665-129">选择**可视化C#> Windows 通用 > 空白应用**作为项目类型，命名你的项目，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="5b665-129">Choose **Visual C#>Windows Universal>Blank App** as the project type, name your project and click **OK**.</span></span>

![添加新项目](../media/MemoryLeaks/NewForegroundApp.PNG)

<span data-ttu-id="5b665-131">右键单击新前台应用程序项目的**引用**节点，然后选择**添加引用...**</span><span class="sxs-lookup"><span data-stu-id="5b665-131">Right-click on the new foreground app project's **References** node and select **Add Reference...**</span></span>

![添加新项目](../media/MemoryLeaks/AddReference.PNG)

<span data-ttu-id="5b665-133">在中**引用管理器**对话框中，选择**项目**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="5b665-133">In the **Reference Manager** dialog choose **Projects** in the left-hand pane.</span></span>  <span data-ttu-id="5b665-134">在中心窗格中在后台应用程序项目旁边的复选框中添加检查，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="5b665-134">In the center pane add a check in the checkbox next to your background application project and click **OK**.</span></span>

![添加新项目](../media/MemoryLeaks/AddReferenceDialog.PNG)

<span data-ttu-id="5b665-136">接下来右键单击前台应用程序项目，然后单击**设为启动项目**。</span><span class="sxs-lookup"><span data-stu-id="5b665-136">Next right-click the foreground app project and click **Set as StartUp Project**.</span></span>

![添加新项目](../media/MemoryLeaks/SetAsStartup.PNG)

<span data-ttu-id="5b665-138">添加代码以创建您的后台应用程序对象的实例并调用 Run 传递空值作为唯一参数。</span><span class="sxs-lookup"><span data-stu-id="5b665-138">Add code to create an instance of your background application object and call Run passing in null as the only parameter.</span></span>
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

<span data-ttu-id="5b665-139">然后在后台应用程序的运行方法检查并确保 taskInstance 不为 null 然后再使用它。</span><span class="sxs-lookup"><span data-stu-id="5b665-139">Then in your background app's Run method check to make sure taskInstance is not null before using it.</span></span>

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

1. <span data-ttu-id="5b665-140">对任务的调用上设置断点。Run(null)。</span><span class="sxs-lookup"><span data-stu-id="5b665-140">Set a breakpoint on the call to task.Run(null).</span></span>
2. <span data-ttu-id="5b665-141">设置计时器另一个断点。在中 StartupTask.cs Timer_Tick 中的更改 （Timeout.Infinite，Timeout.Infinite）。</span><span class="sxs-lookup"><span data-stu-id="5b665-141">Set another breakpoint on timer.Change(Timeout.Infinite, Timeout.Infinite) in Timer_Tick in StartupTask.cs.</span></span>
3. <span data-ttu-id="5b665-142">按 F5 开始调试</span><span class="sxs-lookup"><span data-stu-id="5b665-142">Press F5 to begin debugging</span></span>
4. <span data-ttu-id="5b665-143">当命中第一个断点按快照按钮以设置要比较的基线</span><span class="sxs-lookup"><span data-stu-id="5b665-143">When you hit the first breakpoint press the snapshot button to set the baseline to compare against</span></span>

![快照](../media/MemoryLeaks/Snapshot.PNG)

5. <span data-ttu-id="5b665-145">按 F5</span><span class="sxs-lookup"><span data-stu-id="5b665-145">Press F5</span></span>
6. <span data-ttu-id="5b665-146">当你命中第二个断点按快照按钮再次捕获的当前状态。</span><span class="sxs-lookup"><span data-stu-id="5b665-146">When you hit the second breakpoint press the snapshot button again to capture the current state.</span></span>

<span data-ttu-id="5b665-147">现在的诊断工具应显示具有增加内存使用和 2 个快照，像这样的关系图：</span><span class="sxs-lookup"><span data-stu-id="5b665-147">Now the diagnostic tools should show a graph with increasing memory use and 2 snapshot like this:</span></span>

![与泄漏的诊断工具](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

<span data-ttu-id="5b665-149">查看堆大小列中的第 2 行。</span><span class="sxs-lookup"><span data-stu-id="5b665-149">Look at row 2 in the Heap Size column.</span></span> <span data-ttu-id="5b665-150">单击包含加号和向上键的第二个数字。</span><span class="sxs-lookup"><span data-stu-id="5b665-150">Click the second number with the plus sign and up arrow.</span></span> <span data-ttu-id="5b665-151">你应该会看到如下内容：</span><span class="sxs-lookup"><span data-stu-id="5b665-151">You should see something like this:</span></span>

![快照表](../media/MemoryLeaks/Snapshot2_1.PNG)

<span data-ttu-id="5b665-153">按大小差异排序，以便最大数量是在顶部，然后单击顶部的行。</span><span class="sxs-lookup"><span data-stu-id="5b665-153">Sort by size diff so that the largest number is at the top, then click the top row.</span></span> <span data-ttu-id="5b665-154">第二个详细信息表上单击**引用的类型**。</span><span class="sxs-lookup"><span data-stu-id="5b665-154">Above the second detail table click **Referenced Types**.</span></span>  <span data-ttu-id="5b665-155">现在应显示第二个表**列表\<Byte []\>** 作为所有的内存使用率的源。</span><span class="sxs-lookup"><span data-stu-id="5b665-155">The second table should now show **List\<Byte[]\>** as the source of all the memory usage.</span></span>

![快照表](../media/MemoryLeaks/Snapshot2_2.PNG)
