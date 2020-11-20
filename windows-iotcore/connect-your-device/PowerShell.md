---
title: 使用适用于 Windows IoT 的 PowerShell
author: paulmon
ms.author: riameser
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 PowerShell 连接到你的设备并管理你的设备。
keywords: windows iot，PowerShell，Windows PowerShell，命令行，命令行 shell
ms.openlocfilehash: 87f8755ec7601fa9669b2a9516b6aa2df8c5a2b5
ms.sourcegitcommit: 3d2e11ed186dc224672acf5ecc539fa9afd10a95
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2020
ms.locfileid: "94943090"
---
# <a name="using-powershell-for-windows-iot"></a><span data-ttu-id="4a660-104">使用适用于 Windows IoT 的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a660-104">Using PowerShell for Windows IoT</span></span>
> [!NOTE]
> <span data-ttu-id="4a660-105">使用[Import-PSCoreRelease (importps) ](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease)添加[开源 powershell](https://github.com/PowerShell/PowerShell/releases)版本。</span><span class="sxs-lookup"><span data-stu-id="4a660-105">Add the [open source powershell](https://github.com/PowerShell/PowerShell/releases) version using [Import-PSCoreRelease (importps)](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease).</span></span> <span data-ttu-id="4a660-106">你仍需要 IOT_POWERSHELL 功能才能包含 WinRM 二进制文件</span><span class="sxs-lookup"><span data-stu-id="4a660-106">You will still require IOT_POWERSHELL feature to include WinRM binaries</span></span>

<span data-ttu-id="4a660-107">使用 Windows PowerShell 远程配置和管理任何 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="4a660-107">Remotely configure and manage any Windows 10 IoT Core device by using Windows PowerShell.</span></span>
<span data-ttu-id="4a660-108">PowerShell 是一种基于任务的命令行 shell 和脚本语言，专为系统管理而设计。</span><span class="sxs-lookup"><span data-stu-id="4a660-108">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span>

<span data-ttu-id="4a660-109">请确保按照以下步骤正确配置运行 Windows 10 IoT Core 的设备，使其能够与 Visual Studio 2017 良好配合使用。</span><span class="sxs-lookup"><span data-stu-id="4a660-109">Make sure to follow these steps to correctly configure your device running Windows 10 IoT Core to work well with Visual Studio 2017.</span></span>

## <a name="initiating-a-powershell-session"></a><span data-ttu-id="4a660-110">启动 PowerShell 会话</span><span class="sxs-lookup"><span data-stu-id="4a660-110">Initiating a PowerShell session</span></span>
1. <span data-ttu-id="4a660-111">若要使用 Windows 10 IoT Core 设备启动 PowerShell 会话，首先需要在主机 PC 和设备之间创建信任关系。</span><span class="sxs-lookup"><span data-stu-id="4a660-111">To start a PowerShell session with your Windows 10 IoT Core device, you'll first need to create a trust relationship between your host PC and your device.</span></span> <span data-ttu-id="4a660-112">启动 Windows IoT Core 设备后，连接到设备的屏幕上将显示一个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="4a660-112">After starting your Windows IoT Core device, an IP address will be shown on the screen attached to the device.</span></span>

    ![Windows 10 IoT Core 上的 Defaultapp.osd](../media/PowerShell/DefaultApp.png)

   <span data-ttu-id="4a660-114">您可以在 Windows 10 IoT 核心仪表板上找到相同的信息。</span><span class="sxs-lookup"><span data-stu-id="4a660-114">You can find the same information on the Windows 10 IoT Core Dashboard.</span></span>

2. <span data-ttu-id="4a660-115">在本地电脑上打开管理员 PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="4a660-115">Open an administrator PowerShell console on your local PC.</span></span> <span data-ttu-id="4a660-116">在 Windows "开始" 菜单附近的 "**搜索 web 和 Windows** " 框中键入 " **powershell** "。</span><span class="sxs-lookup"><span data-stu-id="4a660-116">Type **powershell** in the **Search the web and Windows** box near the Windows Start menu.</span></span> <span data-ttu-id="4a660-117">Windows 将在你的电脑上查找 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4a660-117">Windows will find PowerShell on your PC.</span></span>

    ![查找 PowerShell](../media/PowerShell/start-ps.png)

3. <span data-ttu-id="4a660-119">若要以管理员身份启动 PowerShell，请右键单击 " **Windows PowerShell**"，然后选择 "以 **管理员身份运行**"。</span><span class="sxs-lookup"><span data-stu-id="4a660-119">To start PowerShell as an administrator, right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>

    ![以管理员身份运行 PowerShell](../media/PowerShell/start-ps2.png)

   <span data-ttu-id="4a660-121">现在应会看到 PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="4a660-121">Now you should see the PowerShell console.</span></span>

    ![PS 控制台](../media/PowerShell/ps.PNG)

4. <span data-ttu-id="4a660-123">可能需要在桌面上启动 WinRM 服务才能启用远程连接。</span><span class="sxs-lookup"><span data-stu-id="4a660-123">You may need to start the WinRM service on your desktop to enable remote connections.</span></span> <span data-ttu-id="4a660-124">为此，请在 PowerShell 控制台中键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="4a660-124">To do so, from the PowerShell console, type the following command:</span></span>
```
        net start WinRM
```
5. <span data-ttu-id="4a660-125">在 PowerShell 控制台中，键入以下内容， `<machine-name or IP address>` 使用适当的值替换 (**计算机名称** 最简单，但如果你的设备未在网络上唯一命名，请尝试) IP 地址：</span><span class="sxs-lookup"><span data-stu-id="4a660-125">From the PowerShell console, type the following, substituting `<machine-name or IP address>` with the appropriate value (using your **machine-name** is the easiest, but if your device is not uniquely named on your network, try the IP address):</span></span>
```
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>
```
6. <span data-ttu-id="4a660-126">输入 `Y` 以确认更改。</span><span class="sxs-lookup"><span data-stu-id="4a660-126">Enter `Y` to confirm the change.</span></span>
```
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
```
> [!NOTE]
> <span data-ttu-id="4a660-127">如果要连接多台设备，则可以使用逗号和引号分隔每个设备。</span><span class="sxs-lookup"><span data-stu-id="4a660-127">If you want to connect multiple devices, you can use commas and quotation marks to separate each device.</span></span>

7. <span data-ttu-id="4a660-128">现在，你可以使用 Windows IoT Core 设备开始会话了。</span><span class="sxs-lookup"><span data-stu-id="4a660-128">Now you can start a session with your Windows IoT Core device.</span></span> <span data-ttu-id="4a660-129">在管理员 PowerShell 控制台中，键入：</span><span class="sxs-lookup"><span data-stu-id="4a660-129">From your administrator PowerShell console, type:</span></span>
```
        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator
```
8. <span data-ttu-id="4a660-130">在 "凭据" 对话框中，输入以下默认密码： `p@ssw0rd`</span><span class="sxs-lookup"><span data-stu-id="4a660-130">In the credential dialog, enter the following default password: `p@ssw0rd`</span></span>

    <div class="alert alert-note">
      <h5><span data-ttu-id="4a660-131"><span class="win-icon win-icon-Page"></span> 纪录</span><span class="sxs-lookup"><span data-stu-id="4a660-131"><span class="win-icon win-icon-Page"></span> NOTE</span></span> </h5>
      <p><span data-ttu-id="4a660-132">连接过程不是即时过程，可能需要最多30秒。</span><span class="sxs-lookup"><span data-stu-id="4a660-132">The connection process is not immediate and can take up to 30 seconds.</span></span></p>
    </div>    

    <span data-ttu-id="4a660-133">如果已成功连接到设备，则会在提示之前看到设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="4a660-133">If you successfully connected to the device, you should see the IP address of your device before the prompt.</span></span>

    ![PowerShell 控制台](../media/PowerShell/ps_device.png)

9. <span data-ttu-id="4a660-135">更新你的帐户密码。</span><span class="sxs-lookup"><span data-stu-id="4a660-135">Update your account password.</span></span> <span data-ttu-id="4a660-136">我们 *强烈建议* 你更新管理员帐户的默认密码。</span><span class="sxs-lookup"><span data-stu-id="4a660-136">We *highly recommend* that you update the default password for the Administrator account.</span></span> <span data-ttu-id="4a660-137">为此，请在 PowerShell 连接中发出以下命令：</span><span class="sxs-lookup"><span data-stu-id="4a660-137">To do this, issue the following commands in your PowerShell connection:</span></span>

    <span data-ttu-id="4a660-138">a.</span><span class="sxs-lookup"><span data-stu-id="4a660-138">a.</span></span> <span data-ttu-id="4a660-139">`[new password]`使用强密码替换：</span><span class="sxs-lookup"><span data-stu-id="4a660-139">Replace `[new password]` with a strong password:</span></span>
```
            net user Administrator [new password]
```
<span data-ttu-id="4a660-140">b.</span><span class="sxs-lookup"><span data-stu-id="4a660-140">b.</span></span> <span data-ttu-id="4a660-141">接下来，使用 `Exit-PSSession` 和新凭据建立新的 PowerShell 会话 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="4a660-141">Next, establish a new PowerShell session using `Exit-PSSession` and `Enter-PSSession` with the new credentials.</span></span>
```
            Exit-PSSession

            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator
```
## <a name="commonly-used-powershell-commands"></a><span data-ttu-id="4a660-142">常用 PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="4a660-142">Commonly used PowerShell commands</span></span>

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a><span data-ttu-id="4a660-143">Visual Studio 远程调试器疑难解答</span><span class="sxs-lookup"><span data-stu-id="4a660-143">Troubleshooting with Visual Studio Remote Debugger</span></span>

<span data-ttu-id="4a660-144">若要从 Visual Studio 2017 部署应用程序，需要确保 Visual Studio 远程调试器在 Windows IoT Core 设备上运行。</span><span class="sxs-lookup"><span data-stu-id="4a660-144">To be able to deploy applications from Visual Studio 2017, you will need to make sure that the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="4a660-145">启动计算机时，应该会自动打开远程调试器。</span><span class="sxs-lookup"><span data-stu-id="4a660-145">The remote debugger should open automatically when you start your computer.</span></span> <span data-ttu-id="4a660-146">若要仔细检查，请使用 `tlist` 命令从 PowerShell 列出所有正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="4a660-146">To double check, use the `tlist` command to list all the running processes from PowerShell.</span></span> <span data-ttu-id="4a660-147">设备上应运行 msvsmon.exe 的两个实例。</span><span class="sxs-lookup"><span data-stu-id="4a660-147">There should be two instances of msvsmon.exe running on the device.</span></span>

<span data-ttu-id="4a660-148">在长时间的非活动状态后，Visual Studio 远程调试器可能会超时。</span><span class="sxs-lookup"><span data-stu-id="4a660-148">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="4a660-149">如果 Visual Studio 无法连接到 Windows IoT Core 设备，请尝试重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="4a660-149">If Visual Studio cannot connect to your Windows IoT Core device, try restarting the device.</span></span>

### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="4a660-150">配置 Windows IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="4a660-150">Configure your Windows IoT Core device</span></span>

<span data-ttu-id="4a660-151">如果需要，可以重命名设备。</span><span class="sxs-lookup"><span data-stu-id="4a660-151">If you want, you can rename your device.</span></span>

1. <span data-ttu-id="4a660-152">若要更改计算机名，请使用 `setcomputername` 实用工具：</span><span class="sxs-lookup"><span data-stu-id="4a660-152">To change the computer name, use the `setcomputername` utility:</span></span>
```
        setcomputername <new-name>
```
2. <span data-ttu-id="4a660-153">重新启动设备以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="4a660-153">Restart the device for the change to take effect.</span></span> <span data-ttu-id="4a660-154">你可以使用命令，如下所示 `shutdown` ：</span><span class="sxs-lookup"><span data-stu-id="4a660-154">You can use the `shutdown` command as follows:</span></span>
```
        shutdown /r /t 0
```
3. <span data-ttu-id="4a660-155">由于计算机名称已更改，因此在重启后，你将需要重新运行此命令以使用新名称连接到你的设备：</span><span class="sxs-lookup"><span data-stu-id="4a660-155">Because the computer name was changed, after you restart you will need to rerun this command to connect to your device using the new name:</span></span>
```
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
```
<span data-ttu-id="4a660-156">Windows IoT Core 设备现在应已正确配置并可供使用！</span><span class="sxs-lookup"><span data-stu-id="4a660-156">Your Windows IoT Core device should now be properly configured and ready to use!</span></span>

### <a name="commonly-used-utilities"></a><span data-ttu-id="4a660-157">常用实用程序</span><span class="sxs-lookup"><span data-stu-id="4a660-157">Commonly used utilities</span></span>

<span data-ttu-id="4a660-158">有关可与 PowerShell 一起使用的命令和实用工具的列表，请参阅 [命令行 Utils](../manage-your-device/CommandLineUtils.md) 页。</span><span class="sxs-lookup"><span data-stu-id="4a660-158">For a list of commands and utilities that you can use with PowerShell, see the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page.</span></span>

## <a name="known-issues-and-workarounds"></a><span data-ttu-id="4a660-159">已知问题和解决方法</span><span class="sxs-lookup"><span data-stu-id="4a660-159">Known issues and workarounds</span></span>

<span data-ttu-id="4a660-160">**问题**： PowerShell 安全策略中的已知 bug 会导致远程会话中出现以下问题：</span><span class="sxs-lookup"><span data-stu-id="4a660-160">**ISSUE**: A known bug in PowerShell security policies causes the following issues to manifest within the remote session:</span></span>
* <span data-ttu-id="4a660-161">Get-Help 返回意外的匹配项。</span><span class="sxs-lookup"><span data-stu-id="4a660-161">Get-Help returns unexpected matches.</span></span>
* <span data-ttu-id="4a660-162">指定模块上的 Get-Command 返回空的命令列表。</span><span class="sxs-lookup"><span data-stu-id="4a660-162">Get-Command on a specified module returns an empty command list.</span></span>
* <span data-ttu-id="4a660-163">从任何这些模块运行 cmdlet 都将引发 System.management.automation.commandnotfoundexception： Appx、Get-netadapter、NetSecurity、NetTCPIP、Pnp 设备。</span><span class="sxs-lookup"><span data-stu-id="4a660-163">Running a cmdlet from any of these modules throws CommandNotFoundException: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.</span></span>
* <span data-ttu-id="4a660-164">在上述任何模块上 Import-Module 都将引发 UnauthorizedAccess 的 PSSecurityException 异常。</span><span class="sxs-lookup"><span data-stu-id="4a660-164">Import-Module on any of the above modules throws PSSecurityException exception with UnauthorizedAccess.</span></span> <span data-ttu-id="4a660-165">模块自动加载似乎不起作用。</span><span class="sxs-lookup"><span data-stu-id="4a660-165">Module auto loading does not seem to work either.</span></span>

<span data-ttu-id="4a660-166">**解决方法**：在远程 PowerShell 会话中将执行策略修改到 **RemoteSigned**。</span><span class="sxs-lookup"><span data-stu-id="4a660-166">**Workaround**: Modify the execution policy within the remote PowerShell session to **RemoteSigned**.</span></span> <span data-ttu-id="4a660-167">有关不同的执行策略的详细信息，请参阅 [使用 Set-ExecutionPolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4a660-167">For more information on the different execution policies, see [Using the Set-ExecutionPolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx).</span></span>

<span data-ttu-id="4a660-168">**问题**：某些模块（如 get-netadapter）中的 cmdlet 有时不可见。</span><span class="sxs-lookup"><span data-stu-id="4a660-168">**ISSUE**: Cmdlets from some modules such as NetAdapter are sometimes not visible.</span></span> <span data-ttu-id="4a660-169">例如，Get-Module Get-netadapter 返回一个空列表。</span><span class="sxs-lookup"><span data-stu-id="4a660-169">For example, Get-Module NetAdapter returns an empty list.</span></span>

<span data-ttu-id="4a660-170">**解决方法**：将-Force 参数与 Import-module 一起使用。</span><span class="sxs-lookup"><span data-stu-id="4a660-170">**Workaround**: Use the -Force parameter with Import-Module.</span></span> <span data-ttu-id="4a660-171">例如，`Import-Module NetAdapter -Force`。</span><span class="sxs-lookup"><span data-stu-id="4a660-171">For example, `Import-Module NetAdapter -Force`.</span></span>

<span data-ttu-id="4a660-172">**问题**：将执行策略设置为 "AllSigned" 会中断 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="4a660-172">**ISSUE**: Setting execution policy to "AllSigned" breaks PowerShell remoting.</span></span> <span data-ttu-id="4a660-173">尝试创建远程会话的后续尝试将失败，并 Typesv3.ps1xml 中加载 SecurityException。</span><span class="sxs-lookup"><span data-stu-id="4a660-173">Subsequent attempts to create a remote session fail with a SecurityException loading Typesv3.ps1xml.</span></span>

<span data-ttu-id="4a660-174">**解决方法**：使用 winrs.exe 还原 PowerShell 的执行策略：</span><span class="sxs-lookup"><span data-stu-id="4a660-174">**Workaround**: Use winrs.exe to restore PowerShell's execution policy:</span></span>
* <span data-ttu-id="4a660-175">更改控制台代码页 `Chcp 65001`</span><span class="sxs-lookup"><span data-stu-id="4a660-175">Change console code page `Chcp 65001`</span></span>
* <span data-ttu-id="4a660-176">登录到远程 cmd.exe shell `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`</span><span class="sxs-lookup"><span data-stu-id="4a660-176">Log on to a remote cmd.exe shell `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`</span></span>
* <span data-ttu-id="4a660-177">在远程 cmd.exe 中，修改相应的注册表项 `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`</span><span class="sxs-lookup"><span data-stu-id="4a660-177">Within remote cmd.exe, modify the appropriate registry key `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`</span></span>
* <span data-ttu-id="4a660-178">退出远程 cmd.exe 会话 `exit`</span><span class="sxs-lookup"><span data-stu-id="4a660-178">Exit remote cmd.exe session `exit`</span></span>

### <a name="other-known-issues"></a><span data-ttu-id="4a660-179">其他已知问题</span><span class="sxs-lookup"><span data-stu-id="4a660-179">Other known issues</span></span>

- <span data-ttu-id="4a660-180">在 PowerShell 脚本中，PowerShell 类或枚举的属性不起作用。</span><span class="sxs-lookup"><span data-stu-id="4a660-180">In PowerShell scripts, attributes to PowerShell class or enumeration do not work.</span></span> <span data-ttu-id="4a660-181">添加特性化结果引发了以下异常： *Type 必须是运行时类型对象*。</span><span class="sxs-lookup"><span data-stu-id="4a660-181">Adding attributed results in the following exception thrown: *Type must be a runtime Type object*.</span></span>

- <span data-ttu-id="4a660-182">不支持出站 CIM 和 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="4a660-182">Outbound CIM and PowerShell remoting are not supported.</span></span> <span data-ttu-id="4a660-183">依赖 cmdlet 中的相关功能将不起作用。</span><span class="sxs-lookup"><span data-stu-id="4a660-183">Relevant functionality in relying cmdlets will not work.</span></span> <span data-ttu-id="4a660-184">其中包括输入-PSSession、获取作业、接收作业、导入模块、调用命令和复制项。</span><span class="sxs-lookup"><span data-stu-id="4a660-184">These include  Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command, and Copy-Item.</span></span>

- <span data-ttu-id="4a660-185">SecureString 命令 ConvertFrom-SecureString 和 ConvertTo-SecureString 不起作用，除非使用 CredSSP 身份验证创建了会话。</span><span class="sxs-lookup"><span data-stu-id="4a660-185">SecureString commands ConvertFrom-SecureString and ConvertTo-SecureString do not work unless the session is created using CredSSP authentication.</span></span> <span data-ttu-id="4a660-186">否则，必须指定-Key 参数。</span><span class="sxs-lookup"><span data-stu-id="4a660-186">Otherwise, the -Key parameter must be specified.</span></span> <span data-ttu-id="4a660-187">有关配置 CredSSP 身份验证的详细信息，请参阅 [使用 CredSSP 启用 PowerShell "第二跃点" 功能](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/)。</span><span class="sxs-lookup"><span data-stu-id="4a660-187">For details on configuring CredSSP authentication, see [Enable PowerShell “Second-Hop” Functionality with CredSSP](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/).</span></span>
