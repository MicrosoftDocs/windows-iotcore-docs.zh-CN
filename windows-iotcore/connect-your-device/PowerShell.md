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
# <a name="using-powershell-for-windows-iot"></a>使用 PowerShell for Windows IoT

远程配置和使用 Windows PowerShell 管理 Windows 10 IoT Core 的任何设备。
PowerShell 是基于任务的命令行 Shell 和脚本语言，专为进行系统管理而设计。

请务必按照以下步骤来正确配置运行 Windows 10 IoT 核心版来很好地配合 Visual Studio 2017 的设备。

## <a name="initiating-a-powershell-session"></a>启动 PowerShell 会话
1. 若要使用 Windows 10 IoT Core 设备启动 PowerShell 会话，请将首先需要创建您的主机 PC 和设备之间的信任关系。 启动 Windows IoT Core 设备之后, 将附加到设备屏幕上显示的 IP 地址。

    ![Windows 10 IoT 核心版上的 CoreDefaultApp](../media/PowerShell/DefaultApp.png)

   您可以找到 Windows 10 IoT Core 仪表板上的相同信息。

2. 打开管理员 PowerShell 控制台在本地 PC 上。 类型**powershell**中**搜索 web 和 Windows**靠近 Windows 开始菜单的框。 Windows 将在您的 PC 上找到 PowerShell。

    ![查找 PowerShell](../media/PowerShell/start-ps.png)

3. 若要以管理员身份启动 PowerShell，右键单击**Windows PowerShell**，然后选择**以管理员身份运行**。

    ![以管理员身份运行 PowerShell](../media/PowerShell/start-ps2.png)

   现在应看到在 PowerShell 控制台。

    ![PowerShell 控制台](../media/PowerShell/ps.PNG)

4. 您可能需要在您的桌面上以启用远程连接启动 WinRM 服务。 为此，请从 PowerShell 控制台中，键入以下命令：

        net start WinRM

5. 从 PowerShell 控制台中，键入以下内容，并替换`<machine-name or IP address>`用相应的值 (使用你**计算机名称**是最简单的方法，但如果你的设备不唯一上名为您的网络，请尝试使用 IP 地址):

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. 输入`Y`以确认更改。

> [!NOTE]
> 如果你想要连接多个设备，可以使用逗号和引号来分隔每个设备。
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
7. 现在，你可以使用你的 Windows IoT 核心版设备启动会话。 在您管理员 PowerShell 控制台中，键入：

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. 在凭据对话框中，输入以下默认密码： `p@ssw0rd`
    
    <div class="alert alert-note">
      <h5><span class="win-icon win-icon-Page"></span> 请注意 </h5>
      <p>连接过程不会立即完成，最多需要 30 秒。</p>
    </div>    
    
    如果您已成功连接到设备，你应看到之前提示你的设备的 IP 地址。

    ![PowerShell 控制台](../media/PowerShell/ps_device.png)

9. 更新你的帐户密码。 我们*强烈建议*更新的默认密码为管理员帐户。 若要执行此操作，请在 PowerShell 连接中发出以下命令：

    a. 使用强密码替换 `[new password]`：
    
            net user Administrator [new password]
            
    b. 接下来，建立新的 PowerShell 会话使用`Exit-PSSession`和`Enter-PSSession`使用新的凭据。
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a>常用 PowerShell 命令

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a>使用 Visual Studio 远程调试器进行故障排除

若要能够从 Visual Studio 2017 部署应用程序，将需要确保在 Windows IoT Core 设备上运行的 Visual Studio 远程调试器。 启动计算机时，远程调试器应自动打开。 若要仔细检查，使用`tlist`从 PowerShell 处理命令以列出所有正在运行。 应有两个 msvsmon.exe 的实例正在设备上运行。

在很长一段时间都处于非活动状态后，Visual Studio 远程调试器可能会超时。 如果 Visual Studio 无法连接到 Windows IoT Core 设备，请尝试重新启动设备。

### <a name="configure-your-windows-iot-core-device"></a>配置 Windows IoT 核心版设备

如果你想，您可以重命名你的设备。 

1. 若要更改计算机名称，请使用`setcomputername`实用程序：

        setcomputername <new-name>

2. 重新启动设备进行更改才能生效。 可以使用 `shutdown` 命令，如下所示：

        shutdown /r /t 0

3. 因为计算机名称已发生更改，您重新启动后将需要重新运行此命令以连接到你的设备使用新名称：

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
Windows IoT Core 设备现在应正确配置，并且可供使用 ！

### <a name="commonly-used-utilities"></a>常用的实用工具

有关命令和实用程序可以与 PowerShell 配合使用的列表，请参阅[命令行实用工具](../manage-your-device/CommandLineUtils.md)页。

## <a name="known-issues-and-workarounds"></a>已知问题和解决方法

**问题**:PowerShell 安全策略中的一个已知 Bug 会导致远程会话内的清单出现以下问题：
* Get-Help 返回异常匹配项。
* 指定模块上的 get 命令将返回空命令列表。
* 从以下任意模块运行 cmdlet 将引发 CommandNotFoundException：Appx、NetAdapter、NetSecurity、NetTCPIP、PnpDevice。
* 上述任意模块上的 Import-Module 将引发 PSSecurityException 异常（包含 UnauthorizedAccess）。 模块自动加载似乎也不起作用。

**解决方法**：在远程 PowerShell 会话中到修改执行策略**RemoteSigned**。 有关不同的执行策略的详细信息，请参阅[使用 Set-executionpolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx)。

**问题**:如 NetAdapter 某些模块中的 Cmdlet 是有时不可见。 例如，Get-Module NetAdapter 将返回一个空列表。 

**解决方法**：使用-Force 参数与导入模块。 例如，`Import-Module NetAdapter -Force`。

**问题**:执行策略设置为"AllSigned"分页符 PowerShell 远程处理。 创建远程会话的后续尝试均失败，并且 SecurityException 正在加载 Typesv3.ps1xml。 

**解决方法**：使用 winrs.exe 还原 PowerShell 执行策略：
* 更改控制台代码页 `Chcp 65001`
* 登录到远程 cmd.exe shell `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* 在远程 cmd.exe，修改相应的注册表项 `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* 退出远程 cmd.exe 会话 `exit`

### <a name="other-known-issues"></a>其他已知问题

- 在 PowerShell 脚本中，向 PowerShell 类或枚举属性无效。 添加特性化会引发以下异常：*类型必须是运行时类型对象*。

- 不支持出站 CIM 和 PowerShell 远程处理。 依赖 cmdlet 的相关功能将不起作用。 其中包括 Enter-pssession Get-job，Receive-job，导入模块，Invoke-command，和复制项。

- 除非使用 CredSSP 身份验证创建会话，SecureString 命令 Convertfrom-securestring 和 Convertto-securestring 不会工作。 否则为-密钥必须指定参数。 有关配置 CredSSP 身份验证的详细信息，请参阅["双跃点"问题](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx)。


