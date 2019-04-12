---
title: 使用 PowerShell for Windows IoT
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 PowerShell 连接到你的设备，以及管理你的设备。
keywords: windows iot、 PowerShell、 Windows PowerShell、 命令行、 命令行 shell
ms.openlocfilehash: 1519fb9dd61a8d6521757fdd97999f03b74afa7d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59511023"
---
# <a name="using-powershell-for-windows-iot"></a><span data-ttu-id="f3c6b-104">使用 PowerShell for Windows IoT</span><span class="sxs-lookup"><span data-stu-id="f3c6b-104">Using PowerShell for Windows IoT</span></span>

<span data-ttu-id="f3c6b-105">远程配置和使用 Windows PowerShell 管理 Windows 10 IoT Core 的任何设备。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-105">Remotely configure and manage any Windows 10 IoT Core device by using Windows PowerShell.</span></span>
<span data-ttu-id="f3c6b-106">PowerShell 是基于任务的命令行 Shell 和脚本语言，专为进行系统管理而设计。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-106">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span>

<span data-ttu-id="f3c6b-107">请务必按照以下步骤来正确配置运行 Windows 10 IoT 核心版来很好地配合 Visual Studio 2017 的设备。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-107">Make sure to follow these steps to correctly configure your device running Windows 10 IoT Core to work well with Visual Studio 2017.</span></span>

## <a name="initiating-a-powershell-session"></a><span data-ttu-id="f3c6b-108">启动 PowerShell 会话</span><span class="sxs-lookup"><span data-stu-id="f3c6b-108">Initiating a PowerShell session</span></span>
1. <span data-ttu-id="f3c6b-109">若要使用 Windows 10 IoT Core 设备启动 PowerShell 会话，请将首先需要创建您的主机 PC 和设备之间的信任关系。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-109">To start a PowerShell session with your Windows 10 IoT Core device, you'll first need to create a trust relationship between your host PC and your device.</span></span> <span data-ttu-id="f3c6b-110">启动 Windows IoT Core 设备之后, 将附加到设备屏幕上显示的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-110">After starting your Windows IoT Core device, an IP address will be shown on the screen attached to the device.</span></span>

    ![Windows 10 IoT 核心版上的 CoreDefaultApp](../media/PowerShell/DefaultApp.png)

   <span data-ttu-id="f3c6b-112">您可以找到 Windows 10 IoT Core 仪表板上的相同信息。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-112">You can find the same information on the Windows 10 IoT Core Dashboard.</span></span>

2. <span data-ttu-id="f3c6b-113">打开管理员 PowerShell 控制台在本地 PC 上。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-113">Open an administrator PowerShell console on your local PC.</span></span> <span data-ttu-id="f3c6b-114">类型**powershell**中**搜索 web 和 Windows**靠近 Windows 开始菜单的框。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-114">Type **powershell** in the **Search the web and Windows** box near the Windows Start menu.</span></span> <span data-ttu-id="f3c6b-115">Windows 将在您的 PC 上找到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-115">Windows will find PowerShell on your PC.</span></span>

    ![查找 PowerShell](../media/PowerShell/start-ps.png)

3. <span data-ttu-id="f3c6b-117">若要以管理员身份启动 PowerShell，右键单击**Windows PowerShell**，然后选择**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-117">To start PowerShell as an administrator, right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>

    ![以管理员身份运行 PowerShell](../media/PowerShell/start-ps2.png)

   <span data-ttu-id="f3c6b-119">现在应看到在 PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-119">Now you should see the PowerShell console.</span></span>

    ![PowerShell 控制台](../media/PowerShell/ps.PNG)

4. <span data-ttu-id="f3c6b-121">您可能需要在您的桌面上以启用远程连接启动 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-121">You may need to start the WinRM service on your desktop to enable remote connections.</span></span> <span data-ttu-id="f3c6b-122">为此，请从 PowerShell 控制台中，键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-122">To do so, from the PowerShell console, type the following command:</span></span>

        net start WinRM

5. <span data-ttu-id="f3c6b-123">从 PowerShell 控制台中，键入以下内容，并替换`<machine-name or IP address>`用相应的值 (使用你**计算机名称**是最简单的方法，但如果你的设备不唯一上名为您的网络，请尝试使用 IP 地址):</span><span class="sxs-lookup"><span data-stu-id="f3c6b-123">From the PowerShell console, type the following, substituting `<machine-name or IP address>` with the appropriate value (using your **machine-name** is the easiest, but if your device is not uniquely named on your network, try the IP address):</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. <span data-ttu-id="f3c6b-124">输入`Y`以确认更改。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-124">Enter `Y` to confirm the change.</span></span>

> [!NOTE]
> <span data-ttu-id="f3c6b-125">如果你想要连接多个设备，可以使用逗号和引号来分隔每个设备。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-125">If you want to connect multiple devices, you can use commas and quotation marks to separate each device.</span></span>
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
7. <span data-ttu-id="f3c6b-126">现在，你可以使用你的 Windows IoT 核心版设备启动会话。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-126">Now you can start a session with your Windows IoT Core device.</span></span> <span data-ttu-id="f3c6b-127">在您管理员 PowerShell 控制台中，键入：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-127">From you administrator PowerShell console, type:</span></span>

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. <span data-ttu-id="f3c6b-128">在凭据对话框中，输入以下默认密码：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-128">In the credential dialog, enter the following default password:</span></span> `p@ssw0rd`
    
    <div class="alert alert-note">
      <h5><span data-ttu-id="f3c6b-129"><span class="win-icon win-icon-Page"></span> 请注意</span><span class="sxs-lookup"><span data-stu-id="f3c6b-129"><span class="win-icon win-icon-Page"></span> NOTE</span></span> </h5>
      <p><span data-ttu-id="f3c6b-130">连接过程不会立即完成，最多需要 30 秒。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-130">The connection process is not immediate and can take up to 30 seconds.</span></span></p>
    </div>    
    
    <span data-ttu-id="f3c6b-131">如果您已成功连接到设备，你应看到之前提示你的设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-131">If you successfully connected to the device, you should see the IP address of your device before the prompt.</span></span>

    ![PowerShell 控制台](../media/PowerShell/ps_device.png)

9. <span data-ttu-id="f3c6b-133">更新你的帐户密码。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-133">Update your account password.</span></span> <span data-ttu-id="f3c6b-134">我们*强烈建议*更新的默认密码为管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-134">We *highly recommend* that you update the default password for the Administrator account.</span></span> <span data-ttu-id="f3c6b-135">若要执行此操作，请在 PowerShell 连接中发出以下命令：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-135">To do this, issue the following commands in your PowerShell connection:</span></span>

    <span data-ttu-id="f3c6b-136">a.</span><span class="sxs-lookup"><span data-stu-id="f3c6b-136">a.</span></span> <span data-ttu-id="f3c6b-137">使用强密码替换 `[new password]`：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-137">Replace `[new password]` with a strong password:</span></span>
    
            net user Administrator [new password]
            
    <span data-ttu-id="f3c6b-138">b.</span><span class="sxs-lookup"><span data-stu-id="f3c6b-138">b.</span></span> <span data-ttu-id="f3c6b-139">接下来，建立新的 PowerShell 会话使用`Exit-PSSession`和`Enter-PSSession`使用新的凭据。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-139">Next, establish a new PowerShell session using `Exit-PSSession` and `Enter-PSSession` with the new credentials.</span></span>
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a><span data-ttu-id="f3c6b-140">常用 PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="f3c6b-140">Commonly used PowerShell commands</span></span>

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a><span data-ttu-id="f3c6b-141">使用 Visual Studio 远程调试器进行故障排除</span><span class="sxs-lookup"><span data-stu-id="f3c6b-141">Troubleshooting with Visual Studio Remote Debugger</span></span>

<span data-ttu-id="f3c6b-142">若要能够从 Visual Studio 2017 部署应用程序，将需要确保在 Windows IoT Core 设备上运行的 Visual Studio 远程调试器。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-142">To be able to deploy applications from Visual Studio 2017, you will need to make sure that the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="f3c6b-143">启动计算机时，远程调试器应自动打开。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-143">The remote debugger should open automatically when you start your computer.</span></span> <span data-ttu-id="f3c6b-144">若要仔细检查，使用`tlist`从 PowerShell 处理命令以列出所有正在运行。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-144">To double check, use the `tlist` command to list all the running processes from PowerShell.</span></span> <span data-ttu-id="f3c6b-145">应有两个 msvsmon.exe 的实例正在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-145">There should be two instances of msvsmon.exe running on the device.</span></span>

<span data-ttu-id="f3c6b-146">在很长一段时间都处于非活动状态后，Visual Studio 远程调试器可能会超时。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-146">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="f3c6b-147">如果 Visual Studio 无法连接到 Windows IoT Core 设备，请尝试重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-147">If Visual Studio cannot connect to your Windows IoT Core device, try restarting the device.</span></span>

### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="f3c6b-148">配置 Windows IoT 核心版设备</span><span class="sxs-lookup"><span data-stu-id="f3c6b-148">Configure your Windows IoT Core device</span></span>

<span data-ttu-id="f3c6b-149">如果你想，您可以重命名你的设备。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-149">If you want, you can rename your device.</span></span> 

1. <span data-ttu-id="f3c6b-150">若要更改计算机名称，请使用`setcomputername`实用程序：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-150">To change the computer name, use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

2. <span data-ttu-id="f3c6b-151">重新启动设备进行更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-151">Restart the device for the change to take effect.</span></span> <span data-ttu-id="f3c6b-152">可以使用 `shutdown` 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-152">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0

3. <span data-ttu-id="f3c6b-153">因为计算机名称已发生更改，您重新启动后将需要重新运行此命令以连接到你的设备使用新名称：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-153">Because the computer name was changed, after you restart you will need to rerun this command to connect to your device using the new name:</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
<span data-ttu-id="f3c6b-154">Windows IoT Core 设备现在应正确配置，并且可供使用 ！</span><span class="sxs-lookup"><span data-stu-id="f3c6b-154">Your Windows IoT Core device should now be properly configured and ready to use!</span></span>

### <a name="commonly-used-utilities"></a><span data-ttu-id="f3c6b-155">常用的实用工具</span><span class="sxs-lookup"><span data-stu-id="f3c6b-155">Commonly used utilities</span></span>

<span data-ttu-id="f3c6b-156">有关命令和实用程序可以与 PowerShell 配合使用的列表，请参阅[命令行实用工具](../manage-your-device/CommandLineUtils.md)页。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-156">For a list of commands and utilities that you can use with PowerShell, see the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page.</span></span>

## <a name="known-issues-and-workarounds"></a><span data-ttu-id="f3c6b-157">已知问题和解决方法</span><span class="sxs-lookup"><span data-stu-id="f3c6b-157">Known issues and workarounds</span></span>

<span data-ttu-id="f3c6b-158">**问题**:PowerShell 安全策略中的一个已知 Bug 会导致远程会话内的清单出现以下问题：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-158">**ISSUE**: A known bug in PowerShell security policies causes the following issues to manifest within the remote session:</span></span>
* <span data-ttu-id="f3c6b-159">Get-Help 返回异常匹配项。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-159">Get-Help returns unexpected matches.</span></span>
* <span data-ttu-id="f3c6b-160">指定模块上的 get 命令将返回空命令列表。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-160">Get-Command on a specified module returns an empty command list.</span></span>
* <span data-ttu-id="f3c6b-161">从以下任意模块运行 cmdlet 将引发 CommandNotFoundException：Appx、NetAdapter、NetSecurity、NetTCPIP、PnpDevice。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-161">Running a cmdlet from any of these modules throws CommandNotFoundException: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.</span></span>
* <span data-ttu-id="f3c6b-162">上述任意模块上的 Import-Module 将引发 PSSecurityException 异常（包含 UnauthorizedAccess）。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-162">Import-Module on any of the above modules throws PSSecurityException exception with UnauthorizedAccess.</span></span> <span data-ttu-id="f3c6b-163">模块自动加载似乎也不起作用。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-163">Module auto loading does not seem to work either.</span></span>

<span data-ttu-id="f3c6b-164">**解决方法**：在远程 PowerShell 会话中到修改执行策略**RemoteSigned**。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-164">**Workaround**: Modify the execution policy within the remote PowerShell session to **RemoteSigned**.</span></span> <span data-ttu-id="f3c6b-165">有关不同的执行策略的详细信息，请参阅[使用 Set-executionpolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-165">For more details on the different execution policies, see [Using the Set-ExecutionPolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx).</span></span>

<span data-ttu-id="f3c6b-166">**问题**:如 NetAdapter 某些模块中的 Cmdlet 是有时不可见。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-166">**ISSUE**: Cmdlets from some modules such as NetAdapter are sometimes not visible.</span></span> <span data-ttu-id="f3c6b-167">例如，Get-Module NetAdapter 将返回一个空列表。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-167">For example, Get-Module NetAdapter returns an empty list.</span></span> 

<span data-ttu-id="f3c6b-168">**解决方法**：使用-Force 参数与导入模块。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-168">**Workaround**: Use the -Force parameter with Import-Module.</span></span> <span data-ttu-id="f3c6b-169">例如，`Import-Module NetAdapter -Force`。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-169">For example, `Import-Module NetAdapter -Force`.</span></span>

<span data-ttu-id="f3c6b-170">**问题**:执行策略设置为"AllSigned"分页符 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-170">**ISSUE**: Setting execution policy to "AllSigned" breaks PowerShell remoting.</span></span> <span data-ttu-id="f3c6b-171">创建远程会话的后续尝试均失败，并且 SecurityException 正在加载 Typesv3.ps1xml。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-171">Subsequent attempts to create a remote session fail with a SecurityException loading Typesv3.ps1xml.</span></span> 

<span data-ttu-id="f3c6b-172">**解决方法**：使用 winrs.exe 还原 PowerShell 执行策略：</span><span class="sxs-lookup"><span data-stu-id="f3c6b-172">**Workaround**: Use winrs.exe to restore PowerShell's execution policy:</span></span>
* <span data-ttu-id="f3c6b-173">更改控制台代码页</span><span class="sxs-lookup"><span data-stu-id="f3c6b-173">Change console code page</span></span> `Chcp 65001`
* <span data-ttu-id="f3c6b-174">登录到远程 cmd.exe shell</span><span class="sxs-lookup"><span data-stu-id="f3c6b-174">Log on to a remote cmd.exe shell</span></span> `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* <span data-ttu-id="f3c6b-175">在远程 cmd.exe，修改相应的注册表项</span><span class="sxs-lookup"><span data-stu-id="f3c6b-175">Within remote cmd.exe, modify the appropriate registry key</span></span> `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* <span data-ttu-id="f3c6b-176">退出远程 cmd.exe 会话</span><span class="sxs-lookup"><span data-stu-id="f3c6b-176">Exit remote cmd.exe session</span></span> `exit`

### <a name="other-known-issues"></a><span data-ttu-id="f3c6b-177">其他已知问题</span><span class="sxs-lookup"><span data-stu-id="f3c6b-177">Other known issues</span></span>

- <span data-ttu-id="f3c6b-178">在 PowerShell 脚本中，向 PowerShell 类或枚举属性无效。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-178">In PowerShell scripts, attributes to PowerShell class or enumeration do not work.</span></span> <span data-ttu-id="f3c6b-179">添加特性化会引发以下异常：*类型必须是运行时类型对象*。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-179">Adding attributed results in the following exception thrown: *Type must be a runtime Type object*.</span></span>

- <span data-ttu-id="f3c6b-180">不支持出站 CIM 和 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-180">Outbound CIM and PowerShell remoting is not supported.</span></span> <span data-ttu-id="f3c6b-181">依赖 cmdlet 的相关功能将不起作用。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-181">Relevant functionality in relying cmdlets will not work.</span></span> <span data-ttu-id="f3c6b-182">其中包括 Enter-pssession Get-job，Receive-job，导入模块，Invoke-command，和复制项。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-182">These include  Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command, and Copy-Item.</span></span>

- <span data-ttu-id="f3c6b-183">除非使用 CredSSP 身份验证创建会话，SecureString 命令 Convertfrom-securestring 和 Convertto-securestring 不会工作。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-183">SecureString commands ConvertFrom-SecureString and ConvertTo-SecureString do not work unless the session is created using CredSSP authentication.</span></span> <span data-ttu-id="f3c6b-184">否则为-密钥必须指定参数。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-184">Otherwise, the -Key parameter must be specified.</span></span> <span data-ttu-id="f3c6b-185">有关配置 CredSSP 身份验证的详细信息，请参阅["双跃点"问题](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f3c6b-185">For details on configuring CredSSP authentication, see [The “Double-Hop” Problem](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx).</span></span>


