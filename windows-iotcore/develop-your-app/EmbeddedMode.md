---
title: 嵌入模式
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何配置 Windows以允许嵌入模式，从而启用后台应用程序和其他功能。
keywords: windows iot， 嵌入式模式， 后台应用程序
ms.openlocfilehash: 234ef9cf416eabd446eb3bd27b6d8004bf40cb71
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229904"
---
# <a name="embedded-mode"></a><span data-ttu-id="3d6d0-104">嵌入模式</span><span class="sxs-lookup"><span data-stu-id="3d6d0-104">Embedded mode</span></span>

<span data-ttu-id="3d6d0-105">IoT 核心Windows IoT Windows支持嵌入式Enterprise。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-105">Embedded Mode is supported on Windows IoT Core and Windows IoT Enterprise.</span></span> <span data-ttu-id="3d6d0-106">嵌入式模式启用：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-106">Embedded Mode enables:</span></span>

* [<span data-ttu-id="3d6d0-107">后台应用程序 (阅读) </span><span class="sxs-lookup"><span data-stu-id="3d6d0-107">Background Applications (read more)</span></span>](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* <span data-ttu-id="3d6d0-108">使用 lowLevelDevice 功能</span><span class="sxs-lookup"><span data-stu-id="3d6d0-108">Use of the lowLevelDevice capability</span></span>
* <span data-ttu-id="3d6d0-109">使用 systemManagement 功能</span><span class="sxs-lookup"><span data-stu-id="3d6d0-109">Use of systemManagement capability</span></span>

<span data-ttu-id="3d6d0-110">在窗口 IoT 核心上始终启用嵌入式模式。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-110">Embedded mode is always enabled on Window IoT Core.</span></span>
<span data-ttu-id="3d6d0-111">必须在 IoT 应用程序上按照以下步骤Windows嵌入式Enterprise。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-111">Embedded mode must be enabled by following the steps below on Windows IoT Enterprise.</span></span>

## <a name="background-applications"></a><span data-ttu-id="3d6d0-112">后台应用程序</span><span class="sxs-lookup"><span data-stu-id="3d6d0-112">Background Applications</span></span>

<span data-ttu-id="3d6d0-113">后台应用程序是使用 Visual Studio 中的"后台应用程序 (IoT) 模板创建的。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-113">Background Applications are created using the Background Application (IoT) template in Visual Studio.</span></span>
<span data-ttu-id="3d6d0-114">详细了解如何创建 [后台应用程序](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-114">Read more about creating [Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

<span data-ttu-id="3d6d0-115">后台应用程序无需停止且没有资源限制即可运行。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-115">Background applications run without stopping and without resource limits.</span></span> <span data-ttu-id="3d6d0-116">此外，如果后台应用程序因某种原因停止并启用了嵌入模式，则系统会重启后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-116">Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.</span></span>

<span data-ttu-id="3d6d0-117">虽然系统将自动重启后台应用程序，但必须启用系统锁定功能，以防止用户停止或干扰后台应用程序的操作。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-117">While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.</span></span>

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a><span data-ttu-id="3d6d0-118">lowLevel 设备功能以及 lowLevelDevice 功能</span><span class="sxs-lookup"><span data-stu-id="3d6d0-118">lowLevel device Capability and lowLevelDevice capability</span></span>

<span data-ttu-id="3d6d0-119">**lowLevel** 设备功能提供对低级别硬件接口（如 GPIO、SPI 和 I2C）的访问权限。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-119">The **lowLevel** device Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.</span></span>

* [<span data-ttu-id="3d6d0-120">GPIO (Blinky 示例) </span><span class="sxs-lookup"><span data-stu-id="3d6d0-120">Blinky Sample(GPIO)</span></span>](https://developer.microsoft.com/windows/iot/samples/helloblinky)
* [<span data-ttu-id="3d6d0-121">加速计示例</span><span class="sxs-lookup"><span data-stu-id="3d6d0-121">Accelerometer Sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

<span data-ttu-id="3d6d0-122">**lowLevelDevices** 功能允许应用在满足大量其他要求时访问自定义设备。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-122">The **lowLevelDevices** Capability allows apps to access custom devices when a number of additional requirements are met.</span></span> <span data-ttu-id="3d6d0-123">不能将此功能与 lowLevel 设备功能混淆，后者允许访问 GPIO、I2C、SPI 和 PWM 设备。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-123">This capability should not be confused with the lowLevel device capability, which allows access to GPIO, I2C, SPI, and PWM devices.</span></span>

<span data-ttu-id="3d6d0-124">有关详细信息 [，请参阅应用](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) 功能声明。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-124">Refer to [App capability declarations](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) for details.</span></span>

## <a name="systemmanagment-capability"></a><span data-ttu-id="3d6d0-125">systemManagment 功能</span><span class="sxs-lookup"><span data-stu-id="3d6d0-125">systemManagment Capability</span></span>

<span data-ttu-id="3d6d0-126">为应用程序启用 systemManagment 功能时，这是一组解锁的 API：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-126">When you enable the systemManagment capabilities for your application, this is the set of APIs that gets unlocked:</span></span>  

* [<span data-ttu-id="3d6d0-127">Windows.System。ProcessLauncher</span><span class="sxs-lookup"><span data-stu-id="3d6d0-127">Windows.System.ProcessLauncher</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [<span data-ttu-id="3d6d0-128">Windows.System.TimeZoneSettings</span><span class="sxs-lookup"><span data-stu-id="3d6d0-128">Windows.System.TimeZoneSettings</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [<span data-ttu-id="3d6d0-129">Windows.System。ShutdownManager</span><span class="sxs-lookup"><span data-stu-id="3d6d0-129">Windows.System.ShutdownManager</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [<span data-ttu-id="3d6d0-130">Windows。Globalization.Language.TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="3d6d0-130">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a><span data-ttu-id="3d6d0-131">调试后台应用程序</span><span class="sxs-lookup"><span data-stu-id="3d6d0-131">Debugging Background Applications</span></span>

<span data-ttu-id="3d6d0-132">如果在未运行 Windows IoT Core 的设备上进行调试，并且看到以下错误消息之一，则需要确保在设备上启用 AllowEmbeddedMode 并确保嵌入模式服务正在运行：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-132">If you are debugging on a device that is not running Windows IoT Core and you see either of the following error messages you need to ensure AllowEmbeddedMode is enabled on the device and that the Embedded Mode service is running:</span></span>

* <span data-ttu-id="3d6d0-133">终结点映射器中不再有可用的终结点。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-133">There are no more endpoints available from the endpoint mapper.</span></span>
* <span data-ttu-id="3d6d0-134">此程序被组策略阻止。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-134">This program is blocked by group policy.</span></span> <span data-ttu-id="3d6d0-135">有关详细信息，请与系统管理员联系。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-135">For more information, contact your system administrator.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="3d6d0-136">更改模式</span><span class="sxs-lookup"><span data-stu-id="3d6d0-136">Changing the mode</span></span>
<span data-ttu-id="3d6d0-137">若要启用嵌入式模式，需要在映像和配置设计器的 ICD (创建设置 AllowEmbeddedMode=1) 预配包。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-137">To enable embedded mode, you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1.</span></span>  <span data-ttu-id="3d6d0-138">若要安装 ICD，需要下载并安装 Windows ADK Windows 10。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-138">To install ICD, you need to download and install the Windows ADK for Windows 10.</span></span>

* [<span data-ttu-id="3d6d0-139">下载适用于 Windows 10 的 Windows ADK</span><span class="sxs-lookup"><span data-stu-id="3d6d0-139">Download the Windows ADK for Windows 10</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526740)
* <span data-ttu-id="3d6d0-140">[了解适用于 Windows 10 的 Windows ADK 中的新增Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="3d6d0-140">[Learn about what's new in the Windows ADK for Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span></span>

1. <span data-ttu-id="3d6d0-141">安装 ADK 时，选择"映像 **和配置设计器" (ICD)**</span><span class="sxs-lookup"><span data-stu-id="3d6d0-141">When installing the ADK select **Imaging and Configuration Designer (ICD)**</span></span>
2. <span data-ttu-id="3d6d0-142">安装完成后，在 WICD Windows映像和配置设计器 (运行) 。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-142">After installation is complete, run Windows Imaging and Configuration Designer (WICD).</span></span>

    ![WICD 图标](../media/EmbeddedMode/WICD_Icon.png)

3. <span data-ttu-id="3d6d0-144">单击 **"高级预配"。**</span><span class="sxs-lookup"><span data-stu-id="3d6d0-144">Click **Advanced provisioning**.</span></span>  <span data-ttu-id="3d6d0-145">将项目命名 **为 AllowEmbeddedMode，** 然后单击"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="3d6d0-145">Name the project **AllowEmbeddedMode** and click **Next**.</span></span>
    <span data-ttu-id="3d6d0-146">![步骤#3](../media/EmbeddedMode/Step3.png)</span><span class="sxs-lookup"><span data-stu-id="3d6d0-146">![Step #3](../media/EmbeddedMode/Step3.png)</span></span>

4. <span data-ttu-id="3d6d0-147">选择 **"通用到所有Windows"，然后选择**"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="3d6d0-147">Choose **Common to all Windows editions** then **Next**.</span></span>
    <span data-ttu-id="3d6d0-148">![步骤#4](../media/EmbeddedMode/Step4.png)</span><span class="sxs-lookup"><span data-stu-id="3d6d0-148">![Step #4](../media/EmbeddedMode/Step4.png)</span></span>

5. <span data-ttu-id="3d6d0-149">单击“完成”  。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-149">Click **Finish**.</span></span>

    ![步骤#5](../media/EmbeddedMode/Step5.png)

6. <span data-ttu-id="3d6d0-151">在搜索框中键入 **EmbeddedMode，** 然后单击 **"AllowEmbeddedMode"。**</span><span class="sxs-lookup"><span data-stu-id="3d6d0-151">In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.</span></span>

    ![步骤#6](../media/EmbeddedMode/Step6.png)

7. <span data-ttu-id="3d6d0-153">在中心窗格中，将 **AllowEmbeddedMode** 的值设置为 **"是步骤** ![ #7](../media/EmbeddedMode/Step7.png)</span><span class="sxs-lookup"><span data-stu-id="3d6d0-153">In the center pane set the value of **AllowEmbeddedMode** to **Yes** ![Step #7](../media/EmbeddedMode/Step7.png)</span></span>

8. <span data-ttu-id="3d6d0-154">单击"导出>预配包"</span><span class="sxs-lookup"><span data-stu-id="3d6d0-154">Click Export > Provisioning Package</span></span>

    ![步骤#8](../media/EmbeddedMode/Step8.png)

9. <span data-ttu-id="3d6d0-156">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-156">Click Next.</span></span>

    ![步骤#9](../media/EmbeddedMode/Step9.png)

10. <span data-ttu-id="3d6d0-158">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-158">Click Next.</span></span>

    ![步骤#10](../media/EmbeddedMode/Step10.png)

11. <span data-ttu-id="3d6d0-160">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-160">Click Next.</span></span>

    ![步骤#11](../media/EmbeddedMode/Step11.png)

12. <span data-ttu-id="3d6d0-162">单击“生成”。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-162">Click Build.</span></span>

    ![步骤#12](../media/EmbeddedMode/Step12.png)

13. <span data-ttu-id="3d6d0-164">安装嵌入模式 。在 IoT Windows上的 PPKG Enterprise双击 。PPKG。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-164">To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.</span></span>

14. <span data-ttu-id="3d6d0-165">单击 **"是，添加"。**</span><span class="sxs-lookup"><span data-stu-id="3d6d0-165">Click **Yes, add it**.</span></span>
    <span data-ttu-id="3d6d0-166">如果 LUA 对话框出现，请单击"是"，然后单击"是，在如下所示的对话框中添加它"。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-166">Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.</span></span>
    <span data-ttu-id="3d6d0-167">![标准#14步骤](../media/EmbeddedMode/Step14Standard.png)</span><span class="sxs-lookup"><span data-stu-id="3d6d0-167">![Step #14 Standard](../media/EmbeddedMode/Step14Standard.png)</span></span>


## <a name="configuring-a-background-application-to-run-automatically"></a><span data-ttu-id="3d6d0-168">将后台应用程序配置为自动运行</span><span class="sxs-lookup"><span data-stu-id="3d6d0-168">Configuring a Background Application to Run automatically</span></span>
1. <span data-ttu-id="3d6d0-169">若要将后台应用程序配置为自动运行，需要按照说明创建 [MinnowBoardMax SD](https://developer.microsoft.com/windows/iot/getstarted) 卡，并复制 (其中 D： 是 `D:\windows\system32\iotstartup.exe` SD 卡) 。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-169">To configure a Background Application to automatically run, you will need to follow the directions to [create an MinnowBoardMax SD Card](https://developer.microsoft.com/windows/iot/getstarted) and copy `D:\windows\system32\iotstartup.exe` (where D: is your SD Card).</span></span>

2. <span data-ttu-id="3d6d0-170">若要获取已安装的后台应用程序的列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-170">To get a list of installed Background Applications type:</span></span>
```
        C:\> iotstartup list BackgroundApplication1
```
3. <span data-ttu-id="3d6d0-171">输出应包含每个已安装的后台应用程序的全名，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-171">The output should include the full name of each installed Background Application, which will look like this:</span></span>
```
        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
```
5. <span data-ttu-id="3d6d0-172">若要配置此应用以在启动类型下运行，请执行：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-172">To configure this app to run at boot type:</span></span>
```
        C:\> iotstartup add headless BackgroundApplication1
```
6. <span data-ttu-id="3d6d0-173">如果后台应用程序已成功添加到启动列表中，应会看到：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-173">If the Background Application has been successfully added to the startup list, you should see this:</span></span>
```
        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1
```
7. <span data-ttu-id="3d6d0-174">重启嵌入式模式设备：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-174">Restart the embedded mode device:</span></span>

8. <span data-ttu-id="3d6d0-175">重启设备后，后台应用程序将自动启动。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-175">Once the device has restarted, your Background Application will start automatically.</span></span>  <span data-ttu-id="3d6d0-176">管理后台应用程序的嵌入式模式服务可能需要几分钟时间才能启动。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-176">The Embedded Mode service that manages Background Applications can take a few minutes to start.</span></span>  <span data-ttu-id="3d6d0-177">嵌入式模式服务将监视启动列表中的后台应用程序，并确保它们在停止时重启。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-177">The embedded mode service will monitor Background Applications on the startup list and make sure they get restarted if they stop.</span></span>  <span data-ttu-id="3d6d0-178">如果后台应用程序在短时间内多次停止，则它将不再重启。</span><span class="sxs-lookup"><span data-stu-id="3d6d0-178">If a Background Application stops several times in a short period of time, it will no longer be restarted.</span></span>

9. <span data-ttu-id="3d6d0-179">若要从启动列表中删除后台应用程序，请键入：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-179">To remove your Background Application from the startup list type:</span></span>
```
        C:\> iotstartup remove headless BackgroundApplication1
```
10. <span data-ttu-id="3d6d0-180">如果从启动列表中删除了后台应用程序，则输出将如下所示：</span><span class="sxs-lookup"><span data-stu-id="3d6d0-180">If the Background Application is removed from the startup list the output will look like this:</span></span>
```
        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
```
