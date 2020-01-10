---
title: 嵌入模式
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: 了解如何将 Windows 配置为允许嵌入模式，启用后台应用程序和其他功能。
keywords: windows iot，embedded 模式，后台应用程序
ms.openlocfilehash: 7305853515b5bd1ca53c9b8be34c2449752c4897
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721667"
---
# <a name="embedded-mode"></a><span data-ttu-id="d96b2-104">嵌入模式</span><span class="sxs-lookup"><span data-stu-id="d96b2-104">Embedded mode</span></span>

<span data-ttu-id="d96b2-105">Windows IoT Core 和 Windows IoT Enterprise 支持嵌入模式。</span><span class="sxs-lookup"><span data-stu-id="d96b2-105">Embedded Mode is supported on Windows IoT Core and Windows IoT Enterprise.</span></span> <span data-ttu-id="d96b2-106">嵌入模式启用：</span><span class="sxs-lookup"><span data-stu-id="d96b2-106">Embedded Mode enables:</span></span>

* [<span data-ttu-id="d96b2-107">后台应用程序（了解详细信息）</span><span class="sxs-lookup"><span data-stu-id="d96b2-107">Background Applications (read more)</span></span>](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* <span data-ttu-id="d96b2-108">LowLevelDevice 功能的使用</span><span class="sxs-lookup"><span data-stu-id="d96b2-108">Use of the lowLevelDevice capability</span></span>
* <span data-ttu-id="d96b2-109">SystemManagement 功能的使用</span><span class="sxs-lookup"><span data-stu-id="d96b2-109">Use of systemManagement capability</span></span>

<span data-ttu-id="d96b2-110">Windows IoT Core 上始终启用嵌入模式。</span><span class="sxs-lookup"><span data-stu-id="d96b2-110">Embedded mode is always enabled on Window IoT Core.</span></span>
<span data-ttu-id="d96b2-111">必须通过在 Windows IoT Enterprise 上执行以下步骤来启用嵌入模式。</span><span class="sxs-lookup"><span data-stu-id="d96b2-111">Embedded mode must be enabled by following the steps below on Windows IoT Enterprise.</span></span>

## <a name="background-applications"></a><span data-ttu-id="d96b2-112">后台应用程序</span><span class="sxs-lookup"><span data-stu-id="d96b2-112">Background Applications</span></span>

<span data-ttu-id="d96b2-113">后台应用程序是使用 Visual Studio 中的后台应用程序（IoT）模板创建的。</span><span class="sxs-lookup"><span data-stu-id="d96b2-113">Background Applications are created using the Background Application (IoT) template in Visual Studio.</span></span>
<span data-ttu-id="d96b2-114">阅读有关创建[后台应用程序](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d96b2-114">Read more about creating [Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

<span data-ttu-id="d96b2-115">后台应用程序在运行时无需停止并且没有资源限制。</span><span class="sxs-lookup"><span data-stu-id="d96b2-115">Background applications run without stopping and without resource limits.</span></span> <span data-ttu-id="d96b2-116">此外，如果后台应用程序因某种原因而停止并且嵌入模式已启用，则系统会重新启动后台应用程序。</span><span class="sxs-lookup"><span data-stu-id="d96b2-116">Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.</span></span>

<span data-ttu-id="d96b2-117">当系统将自动重新启动后台应用程序时，必须启用系统锁定功能，以防止用户停止或干扰后台应用程序的操作。</span><span class="sxs-lookup"><span data-stu-id="d96b2-117">While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.</span></span>

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a><span data-ttu-id="d96b2-118">lowLevel 设备功能和 lowLevelDevice 功能</span><span class="sxs-lookup"><span data-stu-id="d96b2-118">lowLevel device Capability and lowLevelDevice capability</span></span>

<span data-ttu-id="d96b2-119">**LowLevel**设备功能提供对低级硬件接口（如 GPIO、SPI 和 I2C）的访问权限。</span><span class="sxs-lookup"><span data-stu-id="d96b2-119">The **lowLevel** device Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.</span></span>

* [<span data-ttu-id="d96b2-120">Blinky 示例（GPIO）</span><span class="sxs-lookup"><span data-stu-id="d96b2-120">Blinky Sample(GPIO)</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [<span data-ttu-id="d96b2-121">加速感应示例</span><span class="sxs-lookup"><span data-stu-id="d96b2-121">Accelerometer Sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

<span data-ttu-id="d96b2-122">当满足一些额外的要求时， **lowLevelDevices**功能允许应用访问自定义设备。</span><span class="sxs-lookup"><span data-stu-id="d96b2-122">The **lowLevelDevices** Capability allows apps to access custom devices when a number of additional requirements are met.</span></span> <span data-ttu-id="d96b2-123">不应将此功能与 lowLevel 设备功能混淆，这允许访问 GPIO、I2C、SPI 和 PWM 设备。</span><span class="sxs-lookup"><span data-stu-id="d96b2-123">This capability should not be confused with the lowLevel device capability, which allows access to GPIO, I2C, SPI, and PWM devices.</span></span>

<span data-ttu-id="d96b2-124">有关详细信息，请参阅[应用功能声明](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations)。</span><span class="sxs-lookup"><span data-stu-id="d96b2-124">Refer to [App capability declarations](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) for details.</span></span>

## <a name="systemmanagment-capability"></a><span data-ttu-id="d96b2-125">systemManagment 功能</span><span class="sxs-lookup"><span data-stu-id="d96b2-125">systemManagment Capability</span></span>

<span data-ttu-id="d96b2-126">为应用程序启用 systemManagment 功能时，此为已解除锁定的 Api 集：</span><span class="sxs-lookup"><span data-stu-id="d96b2-126">When you enable the systemManagment capabilities for your application this is the set of APIs that gets unlocked:</span></span>  

* [<span data-ttu-id="d96b2-127">ProcessLauncher</span><span class="sxs-lookup"><span data-stu-id="d96b2-127">Windows.System.ProcessLauncher</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [<span data-ttu-id="d96b2-128">TimeZoneSettings</span><span class="sxs-lookup"><span data-stu-id="d96b2-128">Windows.System.TimeZoneSettings</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [<span data-ttu-id="d96b2-129">ShutdownManager</span><span class="sxs-lookup"><span data-stu-id="d96b2-129">Windows.System.ShutdownManager</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [<span data-ttu-id="d96b2-130">Windows TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="d96b2-130">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a><span data-ttu-id="d96b2-131">调试后台应用程序</span><span class="sxs-lookup"><span data-stu-id="d96b2-131">Debugging Background Applications</span></span>

<span data-ttu-id="d96b2-132">如果正在调试的设备运行的不是 Windows IoT 核心版，并且看到以下任一错误消息，你需要确保该设备上已启用 AllowEmbeddedMode 且“嵌入模式”服务处于运行状态：</span><span class="sxs-lookup"><span data-stu-id="d96b2-132">If you are debugging on a device that is not running Windows IoT Core and you see either of the following error messages you need to ensure AllowEmbeddedMode is enabled on the device and that the Embedded Mode service is running:</span></span>

* <span data-ttu-id="d96b2-133">端点映射程序中未提供更多端点。</span><span class="sxs-lookup"><span data-stu-id="d96b2-133">There are no more endpoints available from the endpoint mapper.</span></span>
* <span data-ttu-id="d96b2-134">此程序由组策略阻止。</span><span class="sxs-lookup"><span data-stu-id="d96b2-134">This program is blocked by group policy.</span></span> <span data-ttu-id="d96b2-135">有关详细信息，请与系统管理员联系。</span><span class="sxs-lookup"><span data-stu-id="d96b2-135">For more information, contact your system administrator.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="d96b2-136">更改模式</span><span class="sxs-lookup"><span data-stu-id="d96b2-136">Changing the mode</span></span>
<span data-ttu-id="d96b2-137">若要启用嵌入模式，你将需要在映像和配置设计器 (ICD)（将 AllowEmbeddedMode 设置为 1）中创建设置包。</span><span class="sxs-lookup"><span data-stu-id="d96b2-137">To enable embedded mode you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1.</span></span>  <span data-ttu-id="d96b2-138">若要安装 ICD，你需要下载并安装适用于 Windows 10 的 Windows ADK。</span><span class="sxs-lookup"><span data-stu-id="d96b2-138">To install ICD you need to download and install the Windows ADK for Windows 10.</span></span>

* [<span data-ttu-id="d96b2-139">下载适用于 Windodws 10 的 Windows ADK</span><span class="sxs-lookup"><span data-stu-id="d96b2-139">Download the Windows ADK for Windows 10</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526740)
* <span data-ttu-id="d96b2-140">[了解适用于 Windows 10 的 Windows ADK 中的新增功能](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="d96b2-140">[Learn about what's new in the Windows ADK for Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span></span>

1. <span data-ttu-id="d96b2-141">安装 ADK 时，请选择**映像和配置设计器（ICD）**</span><span class="sxs-lookup"><span data-stu-id="d96b2-141">When installing the ADK select **Imaging and Configuration Designer (ICD)**</span></span>
2. <span data-ttu-id="d96b2-142">安装完成后，运行 Windows 映像和配置设计器（WICD）。</span><span class="sxs-lookup"><span data-stu-id="d96b2-142">After installation is complete run Windows Imaging and Configuration Designer (WICD).</span></span>

    ![WICD 图标](../media/EmbeddedMode/WICD_Icon.png)

3. <span data-ttu-id="d96b2-144">单击“高级预配”。</span><span class="sxs-lookup"><span data-stu-id="d96b2-144">Click **Advanced provisioning**.</span></span>  <span data-ttu-id="d96b2-145">将项目命名为**AllowEmbeddedMode** ，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="d96b2-145">Name the project **AllowEmbeddedMode** and click **Next**.</span></span>
    <span data-ttu-id="d96b2-146">![步骤 3](../media/EmbeddedMode/Step3.png)</span><span class="sxs-lookup"><span data-stu-id="d96b2-146">![Step3](../media/EmbeddedMode/Step3.png)</span></span>

4. <span data-ttu-id="d96b2-147">选择 "**通用"，** 然后选择 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="d96b2-147">Choose **Common to all Windows editions** then **Next**.</span></span>
    <span data-ttu-id="d96b2-148">![步骤 4](../media/EmbeddedMode/Step4.png)</span><span class="sxs-lookup"><span data-stu-id="d96b2-148">![Step4](../media/EmbeddedMode/Step4.png)</span></span>

5. <span data-ttu-id="d96b2-149">单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="d96b2-149">Click **Finish**.</span></span>

    ![步骤 5](../media/EmbeddedMode/Step5.png)

6. <span data-ttu-id="d96b2-151">在搜索框中键入 " **EmbeddedMode** "，然后单击 " **AllowEmbeddedMode**"。</span><span class="sxs-lookup"><span data-stu-id="d96b2-151">In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.</span></span>

    ![步骤 6](../media/EmbeddedMode/Step6.png)

7. <span data-ttu-id="d96b2-153">在中心窗格中，将 " **AllowEmbeddedMode** " 的值设置为 **"是"** ![Step7](../media/EmbeddedMode/Step7.png)</span><span class="sxs-lookup"><span data-stu-id="d96b2-153">In the center pane set the value of **AllowEmbeddedMode** to **Yes** ![Step7](../media/EmbeddedMode/Step7.png)</span></span>

8. <span data-ttu-id="d96b2-154">单击 "导出" > 预配包</span><span class="sxs-lookup"><span data-stu-id="d96b2-154">Click Export > Provisioning Package</span></span>

    ![步骤 8](../media/EmbeddedMode/Step8.png)

9. <span data-ttu-id="d96b2-156">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96b2-156">Click Next.</span></span>

    ![步骤 9](../media/EmbeddedMode/Step9.png)

10. <span data-ttu-id="d96b2-158">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96b2-158">Click Next.</span></span>

    ![步骤 10](../media/EmbeddedMode/Step10.png)

11. <span data-ttu-id="d96b2-160">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d96b2-160">Click Next.</span></span>

    ![步骤 11](../media/EmbeddedMode/Step11.png)

12. <span data-ttu-id="d96b2-162">单击“生成”。</span><span class="sxs-lookup"><span data-stu-id="d96b2-162">Click Build.</span></span>

    ![步骤 12](../media/EmbeddedMode/Step12.png)

13. <span data-ttu-id="d96b2-164">安装嵌入模式。PPKG 在 Windows IoT Enterprise 上双击。PPKG.</span><span class="sxs-lookup"><span data-stu-id="d96b2-164">To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.</span></span>

14. <span data-ttu-id="d96b2-165">单击 **"是，添加它"** 。</span><span class="sxs-lookup"><span data-stu-id="d96b2-165">Click **Yes, add it**.</span></span>
    <span data-ttu-id="d96b2-166">在 LUA 对话框上单击 "是" （如果出现），然后单击 **"是，将其添加**到下面显示的对话框中"。</span><span class="sxs-lookup"><span data-stu-id="d96b2-166">Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.</span></span>
    <span data-ttu-id="d96b2-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span><span class="sxs-lookup"><span data-stu-id="d96b2-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span></span>


## <a name="configuring-a-background-application-to-run-automatically"></a><span data-ttu-id="d96b2-168">将后台应用程序配置为自动运行</span><span class="sxs-lookup"><span data-stu-id="d96b2-168">Configuring a Background Application to Run automatically</span></span>
1. <span data-ttu-id="d96b2-169">若要将后台应用程序配置为自动运行，需要按照说明[创建 MINNOWBOARDMAX SD 卡](https://developer.microsoft.com/en-us/windows/iot/getstarted)，并复制 `D:\windows\system32\iotstartup.exe` （其中 D：是 SD 卡）。</span><span class="sxs-lookup"><span data-stu-id="d96b2-169">To configure a Background Application to automatically run you will need to follow the directions to [create an MinnowBoardMax SD Card](https://developer.microsoft.com/en-us/windows/iot/getstarted) and copy `D:\windows\system32\iotstartup.exe` (where D: is your SD Card).</span></span>

2. <span data-ttu-id="d96b2-170">若要获取已安装后台应用程序的列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="d96b2-170">To get a list of installed Background Applications type:</span></span>

        C:\> iotstartup list BackgroundApplication1

3. <span data-ttu-id="d96b2-171">输出应包括每个已安装后台应用程序的完整名称，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d96b2-171">The output should include the full name of each installed Background Application, which will look like this:</span></span>

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. <span data-ttu-id="d96b2-172">将此应用配置为在启动时运行类型：</span><span class="sxs-lookup"><span data-stu-id="d96b2-172">To configure this app to run at boot type:</span></span>

        C:\> iotstartup add headless BackgroundApplication1

6. <span data-ttu-id="d96b2-173">如果后台应用程序已成功添加到启动列表，你应看到：</span><span class="sxs-lookup"><span data-stu-id="d96b2-173">If the Background Application has been successfully added to the startup list you should see this:</span></span>

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. <span data-ttu-id="d96b2-174">重新启动嵌入的模式设备：</span><span class="sxs-lookup"><span data-stu-id="d96b2-174">Restart the embedded mode device:</span></span>

8. <span data-ttu-id="d96b2-175">设备重新启动后，后台应用程序将自动启动。</span><span class="sxs-lookup"><span data-stu-id="d96b2-175">Once the device has restarted, your Background Application will start automatically.</span></span>  <span data-ttu-id="d96b2-176">管理后台应用程序的嵌入模式服务可能需要几分钟的时间才能启动。</span><span class="sxs-lookup"><span data-stu-id="d96b2-176">The Embedded Mode service which manages Background Applications can take a few minutes to start.</span></span>  <span data-ttu-id="d96b2-177">嵌入模式服务将监视启动列表上的后台应用程序，并确保它们在停止时重新启动。</span><span class="sxs-lookup"><span data-stu-id="d96b2-177">The embedded mode service will monitor Background Applications on the startup list and make sure they get restarted if they stops.</span></span>  <span data-ttu-id="d96b2-178">如果后台应用程序在很短的时间内停止多次，将不再重新启动该应用程序。</span><span class="sxs-lookup"><span data-stu-id="d96b2-178">If a Background Application stops several times in a short period of time it will no longer be restarted.</span></span>

9. <span data-ttu-id="d96b2-179">若要从启动列表中删除后台应用程序，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d96b2-179">To remove your Background Application from the startup list type:</span></span>

        C:\> iotstartup remove headless BackgroundApplication1

10. <span data-ttu-id="d96b2-180">如果从启动列表中删除后台应用程序，输出将如下所示：</span><span class="sxs-lookup"><span data-stu-id="d96b2-180">If the Background Application is removed from the startup list the output will look like this:</span></span>

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
