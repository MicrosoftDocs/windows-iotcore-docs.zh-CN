---
title: 嵌入模式
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: 了解如何配置 Windows 以允许嵌入模式下，启用后台应用程序和其他功能。
keywords: windows iot、 嵌入的模式、 后台应用程序
ms.openlocfilehash: 1944cec09400cff4d895bb9e55b89b3b19a3f5f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510623"
---
# <a name="embedded-mode"></a><span data-ttu-id="959bc-104">嵌入模式</span><span class="sxs-lookup"><span data-stu-id="959bc-104">Embedded mode</span></span>

<span data-ttu-id="959bc-105">Windows IoT Core 和 Windows IoT 企业版支持嵌入的模式。</span><span class="sxs-lookup"><span data-stu-id="959bc-105">Embedded Mode is supported on Windows IoT Core and Windows IoT Enterprise.</span></span> <span data-ttu-id="959bc-106">使嵌入的模式：</span><span class="sxs-lookup"><span data-stu-id="959bc-106">Embedded Mode enables:</span></span>

* [<span data-ttu-id="959bc-107">后台应用程序 （阅读更多）</span><span class="sxs-lookup"><span data-stu-id="959bc-107">Background Applications (read more)</span></span>](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* <span data-ttu-id="959bc-108">LowLevelDevice 功能的使用</span><span class="sxs-lookup"><span data-stu-id="959bc-108">Use of the lowLevelDevice capability</span></span>
* <span data-ttu-id="959bc-109">系统管理功能的使用</span><span class="sxs-lookup"><span data-stu-id="959bc-109">Use of systemManagement capability</span></span>

<span data-ttu-id="959bc-110">在窗口 IoT Core 上始终启用嵌入的模式。</span><span class="sxs-lookup"><span data-stu-id="959bc-110">Embedded mode is always enabled on Window IoT Core.</span></span>
<span data-ttu-id="959bc-111">必须在 Windows IoT 企业版上按照以下步骤启用嵌入的模式。</span><span class="sxs-lookup"><span data-stu-id="959bc-111">Embedded mode must be enabled by following the steps below on Windows IoT Enterprise.</span></span>

## <a name="background-applications"></a><span data-ttu-id="959bc-112">后台应用程序</span><span class="sxs-lookup"><span data-stu-id="959bc-112">Background Applications</span></span>

<span data-ttu-id="959bc-113">使用 Visual Studio 中的后台应用程序 (IoT) 模板创建后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="959bc-113">Background Applications are created using the Background Application (IoT) template in Visual Studio.</span></span>
<span data-ttu-id="959bc-114">详细了解如何创建[后台应用程序](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)。</span><span class="sxs-lookup"><span data-stu-id="959bc-114">Read more about creating [Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

<span data-ttu-id="959bc-115">后台运行，而不停止且资源限制的应用程序。</span><span class="sxs-lookup"><span data-stu-id="959bc-115">Background applications run without stopping and without resource limits.</span></span> <span data-ttu-id="959bc-116">此外，如果出于某种原因停止后台应用程序和嵌入连接模式下启用的后台应用程序将由系统重新启动。</span><span class="sxs-lookup"><span data-stu-id="959bc-116">Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.</span></span>

<span data-ttu-id="959bc-117">时系统将自动重新启动后台应用程序，必须启用系统锁定功能以防止用户停止或干扰后台应用程序的操作。</span><span class="sxs-lookup"><span data-stu-id="959bc-117">While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.</span></span>

## <a name="lowleveldevice-capability"></a><span data-ttu-id="959bc-118">lowLevelDevice 功能</span><span class="sxs-lookup"><span data-stu-id="959bc-118">lowLevelDevice Capability</span></span>

<span data-ttu-id="959bc-119">LowLevelDevice 功能可让 GPIO、 SPI 和 I2C 等低级别的硬件接口访问。</span><span class="sxs-lookup"><span data-stu-id="959bc-119">The lowLevelDevice Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.</span></span>

* [<span data-ttu-id="959bc-120">灾难从天而降 Sample(GPIO)</span><span class="sxs-lookup"><span data-stu-id="959bc-120">Blinky Sample(GPIO)</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [<span data-ttu-id="959bc-121">加速计示例</span><span class="sxs-lookup"><span data-stu-id="959bc-121">Accelerometer Sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

## <a name="systemmanagment-capability"></a><span data-ttu-id="959bc-122">systemManagment 功能</span><span class="sxs-lookup"><span data-stu-id="959bc-122">systemManagment Capability</span></span>

<span data-ttu-id="959bc-123">为你的应用程序启用 systemManagment 功能时这是已解锁的 Api 集：</span><span class="sxs-lookup"><span data-stu-id="959bc-123">When you enable the systemManagment capabilities for your application this is the set of APIs that gets unlocked:</span></span>  

* [<span data-ttu-id="959bc-124">Windows.System.ProcessLauncher</span><span class="sxs-lookup"><span data-stu-id="959bc-124">Windows.System.ProcessLauncher</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [<span data-ttu-id="959bc-125">Windows.System.TimeZoneSettings</span><span class="sxs-lookup"><span data-stu-id="959bc-125">Windows.System.TimeZoneSettings</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [<span data-ttu-id="959bc-126">Windows.System.ShutdownManager</span><span class="sxs-lookup"><span data-stu-id="959bc-126">Windows.System.ShutdownManager</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [<span data-ttu-id="959bc-127">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="959bc-127">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a><span data-ttu-id="959bc-128">调试后台应用程序</span><span class="sxs-lookup"><span data-stu-id="959bc-128">Debugging Background Applications</span></span>

<span data-ttu-id="959bc-129">如果正在调试的设备运行的不是 Windows IoT 核心版，并且看到以下任一错误消息，你需要确保该设备上已启用 AllowEmbeddedMode 且“嵌入模式”服务处于运行状态：</span><span class="sxs-lookup"><span data-stu-id="959bc-129">If you are debugging on a device that is not running Windows IoT Core and you see either of the following error messages you need to ensure AllowEmbeddedMode is enabled on the device and that the Embedded Mode service is running:</span></span>

* <span data-ttu-id="959bc-130">端点映射程序中未提供更多端点。</span><span class="sxs-lookup"><span data-stu-id="959bc-130">There are no more endpoints available from the endpoint mapper.</span></span>
* <span data-ttu-id="959bc-131">此程序由组策略阻止。</span><span class="sxs-lookup"><span data-stu-id="959bc-131">This program is blocked by group policy.</span></span> <span data-ttu-id="959bc-132">有关详细信息，请与系统管理员联系。</span><span class="sxs-lookup"><span data-stu-id="959bc-132">For more information, contact your system administrator.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="959bc-133">更改模式</span><span class="sxs-lookup"><span data-stu-id="959bc-133">Changing the mode</span></span>
<span data-ttu-id="959bc-134">若要启用嵌入模式，你将需要在映像和配置设计器 (ICD)（将 AllowEmbeddedMode 设置为 1）中创建设置包。</span><span class="sxs-lookup"><span data-stu-id="959bc-134">To enable embedded mode you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1.</span></span>  <span data-ttu-id="959bc-135">若要安装 ICD，你需要下载并安装适用于 Windows 10 的 Windows ADK。</span><span class="sxs-lookup"><span data-stu-id="959bc-135">To install ICD you need to download and install the Windows ADK for Windows 10.</span></span>

* [<span data-ttu-id="959bc-136">下载适用于 Windows 10 的 Windows ADK</span><span class="sxs-lookup"><span data-stu-id="959bc-136">Download the Windows ADK for Windows 10</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* [<span data-ttu-id="959bc-137">了解什么是 Windows ADK for Windows 10 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="959bc-137">Learn about what's new in the Windows ADK for Windows 10</span></span>](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. <span data-ttu-id="959bc-138">当安装 ADK 选择**映像和配置设计器 (ICD)**</span><span class="sxs-lookup"><span data-stu-id="959bc-138">When installing the ADK select **Imaging and Configuration Designer (ICD)**</span></span>
2. <span data-ttu-id="959bc-139">安装完成后运行 Windows 映像和配置设计器 (WICD)。</span><span class="sxs-lookup"><span data-stu-id="959bc-139">After installation is complete run Windows Imaging and Configuration Designer (WICD).</span></span>

    ![WICD 图标](../media/EmbeddedMode/WICD_Icon.png)

3. <span data-ttu-id="959bc-141">单击“高级预配”。</span><span class="sxs-lookup"><span data-stu-id="959bc-141">Click **Advanced provisioning**.</span></span>  <span data-ttu-id="959bc-142">将项目命名**AllowEmbeddedMode**然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="959bc-142">Name the project **AllowEmbeddedMode** and click **Next**.</span></span>
    ![步骤 3](../media/EmbeddedMode/Step3.png)

4. <span data-ttu-id="959bc-144">选择**普遍适用于所有 Windows 版本**然后**下一步**。</span><span class="sxs-lookup"><span data-stu-id="959bc-144">Choose **Common to all Windows editions** then **Next**.</span></span>
    ![步骤 4](../media/EmbeddedMode/Step4.png)

5. <span data-ttu-id="959bc-146">单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="959bc-146">Click **Finish**.</span></span>

    ![步骤 5](../media/EmbeddedMode/Step5.png)

6. <span data-ttu-id="959bc-148">在搜索框中键入**EmbeddedMode** ，然后单击**AllowEmbeddedMode**。</span><span class="sxs-lookup"><span data-stu-id="959bc-148">In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.</span></span>

    ![步骤 6](../media/EmbeddedMode/Step6.png)

7. <span data-ttu-id="959bc-150">在中心窗格中设置的值**AllowEmbeddedMode**到**是** ![Step7](../media/EmbeddedMode/Step7.png)</span><span class="sxs-lookup"><span data-stu-id="959bc-150">In the center pane set the value of **AllowEmbeddedMode** to **Yes** ![Step7](../media/EmbeddedMode/Step7.png)</span></span>

8. <span data-ttu-id="959bc-151">单击导出 > 预配包</span><span class="sxs-lookup"><span data-stu-id="959bc-151">Click Export > Provisioning Package</span></span>

    ![步骤 8](../media/EmbeddedMode/Step8.png)

9. <span data-ttu-id="959bc-153">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="959bc-153">Click Next.</span></span>

    ![步骤 9](../media/EmbeddedMode/Step9.png)

10. <span data-ttu-id="959bc-155">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="959bc-155">Click Next.</span></span>

    ![步骤 10](../media/EmbeddedMode/Step10.png)

11. <span data-ttu-id="959bc-157">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="959bc-157">Click Next.</span></span>

    ![步骤 11](../media/EmbeddedMode/Step11.png)

12. <span data-ttu-id="959bc-159">单击生成。</span><span class="sxs-lookup"><span data-stu-id="959bc-159">Click Build.</span></span>

    ![步骤 12](../media/EmbeddedMode/Step12.png)

13. <span data-ttu-id="959bc-161">若要安装的嵌入的模式。双击 PPKG Windows IoT 企业版上的。PPKG。</span><span class="sxs-lookup"><span data-stu-id="959bc-161">To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.</span></span>

14. <span data-ttu-id="959bc-162">单击**可以，请将其添加**。</span><span class="sxs-lookup"><span data-stu-id="959bc-162">Click **Yes, add it**.</span></span>
    <span data-ttu-id="959bc-163">单击是开 LUA 对话框中如果出现，然后单击**是，将其添加**上如下所示的对话框。</span><span class="sxs-lookup"><span data-stu-id="959bc-163">Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.</span></span>
    ![步骤 14 标准](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a><span data-ttu-id="959bc-165">自动配置为运行一个后台应用程序</span><span class="sxs-lookup"><span data-stu-id="959bc-165">Configuring a Background Application to Run automatically</span></span>
1. <span data-ttu-id="959bc-166">若要配置后台应用程序自动运行你将需要按照的说明为[创建 MinnowBoardMax SD 卡](https://developer.microsoft.com/en-us/windows/iot/getstarted)并复制`D:\windows\system32\iotstartup.exe`（其中 d： 是 SD 卡）。</span><span class="sxs-lookup"><span data-stu-id="959bc-166">To configure a Background Application to automatically run you will need to follow the directions to [create an MinnowBoardMax SD Card](https://developer.microsoft.com/en-us/windows/iot/getstarted) and copy `D:\windows\system32\iotstartup.exe` (where D: is your SD Card).</span></span>

2. <span data-ttu-id="959bc-167">若要获取已安装的后台应用程序类型的列表：</span><span class="sxs-lookup"><span data-stu-id="959bc-167">To get a list of installed Background Applications type:</span></span>

        C:\> iotstartup list BackgroundApplication1

3. <span data-ttu-id="959bc-168">输出应包含每个已安装的后台应用将如下所示的完整名称：</span><span class="sxs-lookup"><span data-stu-id="959bc-168">The output should include the full name of each installed Background Application, which will look like this:</span></span>

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. <span data-ttu-id="959bc-169">若要配置此应用程序运行时在引导类型：</span><span class="sxs-lookup"><span data-stu-id="959bc-169">To configure this app to run at boot type:</span></span>

        C:\> iotstartup add headless BackgroundApplication1

6. <span data-ttu-id="959bc-170">如果后台应用程序已成功添加到启动列表您应看到：</span><span class="sxs-lookup"><span data-stu-id="959bc-170">If the Background Application has been successfully added to the startup list you should see this:</span></span>

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. <span data-ttu-id="959bc-171">重启嵌入的模式设备：</span><span class="sxs-lookup"><span data-stu-id="959bc-171">Restart the embedded mode device:</span></span>

8. <span data-ttu-id="959bc-172">设备已重新启动后，后台应用程序将自动启动。</span><span class="sxs-lookup"><span data-stu-id="959bc-172">Once the device has restarted, your Background Application will start automatically.</span></span>  <span data-ttu-id="959bc-173">管理后台应用程序的嵌入模式服务可能需要几分钟才能开始。</span><span class="sxs-lookup"><span data-stu-id="959bc-173">The Embedded Mode service which manages Background Applications can take a few minutes to start.</span></span>  <span data-ttu-id="959bc-174">嵌入的模式服务将监视启动列表上的后台应用程序，并确保他们获取它们停止时重新启动。</span><span class="sxs-lookup"><span data-stu-id="959bc-174">The embedded mode service will monitor Background Applications on the startup list and make sure they get restarted if they stops.</span></span>  <span data-ttu-id="959bc-175">如果在短时间内多次停止后台应用程序将无法再重启。</span><span class="sxs-lookup"><span data-stu-id="959bc-175">If a Background Application stops several times in a short period of time it will no longer be restarted.</span></span>

9. <span data-ttu-id="959bc-176">若要从启动列表类型中删除后台应用程序：</span><span class="sxs-lookup"><span data-stu-id="959bc-176">To remove your Background Application from the startup list type:</span></span>

        C:\> iotstartup remove headless BackgroundApplication1

10. <span data-ttu-id="959bc-177">如果从启动列表中删除后台应用程序输出将如下所示：</span><span class="sxs-lookup"><span data-stu-id="959bc-177">If the Background Application is removed from the startup list the output will look like this:</span></span>

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
