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
ms.openlocfilehash: 8e7566d1bc3554adfc9ef83d59cad3b080ed53bb
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656693"
---
# <a name="using-powershell-for-windows-iot"></a>使用适用于 Windows IoT 的 PowerShell

使用 Windows PowerShell 远程配置和管理任何 Windows 10 IoT Core 设备。
PowerShell 是一种基于任务的命令行 shell 和脚本语言，专为系统管理而设计。

请确保按照以下步骤正确配置运行 Windows 10 IoT Core 的设备，使其能够与 Visual Studio 2017 良好配合使用。

## <a name="initiating-a-powershell-session"></a>启动 PowerShell 会话
1. 若要使用 Windows 10 IoT Core 设备启动 PowerShell 会话，首先需要在主机 PC 和设备之间创建信任关系。 启动 Windows IoT Core 设备后，连接到设备的屏幕上将显示一个 IP 地址。

    ![Windows 10 IoT Core 上的 Defaultapp.osd](../media/PowerShell/DefaultApp.png)

   您可以在 Windows 10 IoT 核心仪表板上找到相同的信息。

2. 在本地电脑上打开管理员 PowerShell 控制台。 在 Windows "开始" 菜单附近的 "**搜索 web 和 Windows** " 框中键入 " **powershell** "。 Windows 将在你的电脑上查找 PowerShell。

    ![查找 PowerShell](../media/PowerShell/start-ps.png)

3. 若要以管理员身份启动 PowerShell，请右键单击 " **Windows PowerShell**"，然后选择 "以 **管理员身份运行**"。

    ![以管理员身份运行 PowerShell](../media/PowerShell/start-ps2.png)

   现在应会看到 PowerShell 控制台。

    ![PS 控制台](../media/PowerShell/ps.PNG)

4. 可能需要在桌面上启动 WinRM 服务才能启用远程连接。 为此，请在 PowerShell 控制台中键入以下命令：
```
        net start WinRM
```
5. 在 PowerShell 控制台中，键入以下内容， `<machine-name or IP address>` 使用适当的值替换 (**计算机名称** 最简单，但如果你的设备未在网络上唯一命名，请尝试) IP 地址：
```
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>
```
6. 输入 `Y` 以确认更改。
```
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
```
> [!NOTE]
> 如果要连接多台设备，则可以使用逗号和引号分隔每个设备。

7. 现在，你可以使用 Windows IoT Core 设备开始会话了。 在管理员 PowerShell 控制台中，键入：
```
        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator
```
8. 在 "凭据" 对话框中，输入以下默认密码： `p@ssw0rd`

    <div class="alert alert-note">
      <h5><span class="win-icon win-icon-Page"></span> 纪录 </h5>
      <p>连接过程不是即时过程，可能需要最多30秒。</p>
    </div>    

    如果已成功连接到设备，则会在提示之前看到设备的 IP 地址。

    ![PowerShell 控制台](../media/PowerShell/ps_device.png)

9. 更新你的帐户密码。 我们 *强烈建议* 你更新管理员帐户的默认密码。 为此，请在 PowerShell 连接中发出以下命令：

    a. `[new password]`使用强密码替换：
```
            net user Administrator [new password]
```
b. 接下来，使用 `Exit-PSSession` 和新凭据建立新的 PowerShell 会话 `Enter-PSSession` 。
```
            Exit-PSSession

            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator
```
## <a name="commonly-used-powershell-commands"></a>常用 PowerShell 命令

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a>Visual Studio 远程调试器疑难解答

若要从 Visual Studio 2017 部署应用程序，需要确保 Visual Studio 远程调试器在 Windows IoT Core 设备上运行。 启动计算机时，应该会自动打开远程调试器。 若要仔细检查，请使用 `tlist` 命令从 PowerShell 列出所有正在运行的进程。 设备上应运行 msvsmon.exe 的两个实例。

在长时间的非活动状态后，Visual Studio 远程调试器可能会超时。 如果 Visual Studio 无法连接到 Windows IoT Core 设备，请尝试重新启动设备。

### <a name="configure-your-windows-iot-core-device"></a>配置 Windows IoT Core 设备

如果需要，可以重命名设备。

1. 若要更改计算机名，请使用 `setcomputername` 实用工具：
```
        setcomputername <new-name>
```
2. 重新启动设备以使更改生效。 你可以使用命令，如下所示 `shutdown` ：
```
        shutdown /r /t 0
```
3. 由于计算机名称已更改，因此在重启后，你将需要重新运行此命令以使用新名称连接到你的设备：
```
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
```
Windows IoT Core 设备现在应已正确配置并可供使用！

### <a name="commonly-used-utilities"></a>常用实用程序

有关可与 PowerShell 一起使用的命令和实用工具的列表，请参阅 [命令行 Utils](../manage-your-device/CommandLineUtils.md) 页。

## <a name="known-issues-and-workarounds"></a>已知问题和解决方法

**问题**： PowerShell 安全策略中的已知 bug 会导致远程会话中出现以下问题：
* Get-help 返回意外的匹配项。
* 指定模块上的 Get-Command 返回空的命令列表。
* 从任何这些模块运行 cmdlet 都将引发 System.management.automation.commandnotfoundexception： Appx、Get-netadapter、NetSecurity、NetTCPIP、Pnp 设备。
* 以上任何模块上的 import-module 都将引发 PSSecurityException 异常和 UnauthorizedAccess。 模块自动加载似乎不起作用。

**解决方法**：在远程 PowerShell 会话中将执行策略修改到 **RemoteSigned**。 有关不同的执行策略的详细信息，请参阅 [使用 Set-executionpolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx)。

**问题**：某些模块（如 get-netadapter）中的 cmdlet 有时不可见。 例如，Get-netadapter 返回一个空列表。

**解决方法**：将-Force 参数与 Import-module 一起使用。 例如，`Import-Module NetAdapter -Force`。

**问题**：将执行策略设置为 "AllSigned" 会中断 PowerShell 远程处理。 尝试创建远程会话的后续尝试将失败，并 Typesv3.ps1xml 中加载 SecurityException。

**解决方法**：使用 winrs.exe 还原 PowerShell 的执行策略：
* 更改控制台代码页 `Chcp 65001`
* 登录到远程 cmd.exe shell `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* 在远程 cmd.exe 中，修改相应的注册表项 `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* 退出远程 cmd.exe 会话 `exit`

### <a name="other-known-issues"></a>其他已知问题

- 在 PowerShell 脚本中，PowerShell 类或枚举的属性不起作用。 添加特性化结果引发了以下异常： *Type 必须是运行时类型对象*。

- 不支持出站 CIM 和 PowerShell 远程处理。 依赖 cmdlet 中的相关功能将不起作用。 其中包括输入-PSSession、获取作业、接收作业、导入模块、调用命令和复制项。

- SecureString 命令 Convertfrom-csv-SecureString 和 Convertto-html-SecureString 在使用 CredSSP 身份验证创建会话之前不起作用。 否则，必须指定-Key 参数。 有关配置 CredSSP 身份验证的详细信息，请参阅 [使用 CredSSP 启用 PowerShell "第二跃点" 功能](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/)。
