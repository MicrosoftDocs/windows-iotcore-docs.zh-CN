---
title: 使用 PowerShell Windows IoT
author: paulmon
ms.author: riameser
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 PowerShell 连接到设备以及管理设备。
keywords: windows iot、PowerShell、Windows PowerShell、命令行、命令行 shell
ms.openlocfilehash: dc791829f9dc17781e717ef91e5da5c129873f2d
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229994"
---
# <a name="using-powershell-for-windows-iot"></a>使用 PowerShell Windows IoT
> [!NOTE]
> 使用[Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease)将开源[powershell](https://github.com/PowerShell/PowerShell/releases)版本 (导入) 。 你仍然需要使用IOT_POWERSHELL才能包含 WinRM 二进制文件

使用 Windows PowerShell 远程配置和管理Windows 10 IoT 核心版设备。
PowerShell 是基于任务的命令行 shell 和脚本语言，专为系统管理设计。

请务必按照以下步骤正确配置运行 Windows 10 IoT 核心版 的设备，使其Visual Studio 2017 年。

## <a name="initiating-a-powershell-session"></a>启动 PowerShell 会话
1. 若要启动与 Windows 10 IoT 核心版 的 PowerShell 会话，首先需要在主机电脑和设备之间创建信任关系。 启动 IoT Core Windows后，附加到设备的屏幕上会显示 IP 地址。

    ![默认应用Windows 10 IoT 核心版](../media/PowerShell/DefaultApp.png)

   可以在数据上找到相同的Windows 10 IoT 核心版仪表板。

2. 在本地电脑上打开管理员 PowerShell 控制台。 在 **"搜索** **Web"和**"Windows"框中键入 powershell Windows "开始"菜单。 Windows电脑上找到 PowerShell。

    ![查找 PowerShell](../media/PowerShell/start-ps.png)

3. 若要以管理员角色启动 PowerShell，请右键单击 **Windows PowerShell，然后选择**"以 **管理员"运行**。

    ![以管理员身份运行 PowerShell](../media/PowerShell/start-ps2.png)

   现在，应会看到 PowerShell 控制台。

    ![PS 控制台](../media/PowerShell/ps.PNG)

4. 可能需要在桌面上启动 WinRM 服务才能启用远程连接。 为此，请从 PowerShell 控制台键入以下命令：
```
        net start WinRM
```
5. 在 PowerShell 控制台中，键入以下命令，使用计算机名称 (以适当的值 (来表示最简单的方法，但如果设备不是网络上唯一的名称，请尝试 IP 地址 `<machine-name or IP address>`) ： 
```
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>
```
6. 输入 `Y` 以确认更改。
```
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
```
> [!NOTE]
> 如果要连接多个设备，可以使用逗号和引号分隔每个设备。

7. 现在，可以开始与 IoT Core Windows会话。 在管理员 PowerShell 控制台中，键入：
```
        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator
```
8. 在凭据对话框中，输入以下默认密码： `p@ssw0rd`

    <div class="alert alert-note">
      <h5><span class="win-icon win-icon-Page"></span> 注意 </h5>
      <p>连接过程不是即时的，最多可能需要 30 秒。</p>
    </div>    

    如果已成功连接到设备，应在提示之前看到设备的 IP 地址。

    ![PowerShell 控制台](../media/PowerShell/ps_device.png)

9. 更新帐户密码。 *强烈建议更新* 管理员帐户的默认密码。 为此，在 PowerShell 连接中发出以下命令：

    a. 将 `[new password]` 替换为强密码：
```
            net user Administrator [new password]
```
b. 接下来，使用 和 与新凭据建立新的 PowerShell `Exit-PSSession` `Enter-PSSession` 会话。
```
            Exit-PSSession

            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator
```
## <a name="commonly-used-powershell-commands"></a>常用 PowerShell 命令

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a>使用 Visual Studio 远程调试器

若要从 2017 Visual Studio部署应用程序，需要确保 Visual Studio 远程调试器 IoT Core 设备上Windows运行。 启动计算机时，远程调试器应会自动打开。 若要仔细检查，请使用 `tlist` 命令列出 PowerShell 中所有正在运行的进程。 设备上应运行两msvsmon.exe实例。

长时间处于非Visual Studio 远程调试器后，系统可能会超时。 如果Visual Studio IoT 核心Windows，请尝试重启设备。

### <a name="configure-your-windows-iot-core-device"></a>配置 Windows IoT Core 设备

如果需要，可以重命名设备。

1. 若要更改计算机名称，请使用 `setcomputername` 实用工具：
```
        setcomputername <new-name>
```
2. 重启设备，使更改生效。 可以使用 命令 `shutdown` ，如下所示：
```
        shutdown /r /t 0
```
3. 由于计算机名称已更改，因此重启后，需要重新运行此命令以使用新名称连接到设备：
```
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
```
现在Windows正确配置 IoT 核心设备并准备好使用！

### <a name="commonly-used-utilities"></a>常用实用工具

有关可用于 PowerShell 的命令和实用程序的列表，请参阅命令行 [Utils](../manage-your-device/CommandLineUtils.md) 页。

## <a name="known-issues-and-workarounds"></a>已知问题和解决方法

**问题**：PowerShell 安全策略中的已知 bug 导致以下问题在远程会话中出现：
* Get-Help返回意外的匹配项。
* Get-Command模块上返回空的命令列表。
* 从任何这些模块运行 cmdlet 会引发 CommandNotFoundException：Appx、NetAdapter、NetSecurity、NetTCPIP、PnpDevice。
* Import-Module上述任何模块上，会引发具有 UnauthorizedAccess 的 PSSecurityException 异常。 模块自动加载似乎也不起作用。

**解决方法**：将远程 PowerShell 会话中的执行策略修改为 **RemoteSigned**。 有关不同执行策略的信息，请参阅 Using [the Set-ExecutionPolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx)。

**问题**：某些模块（如 NetAdapter）中的 Cmdlet 有时不可见。 例如，Get-Module NetAdapter 返回空列表。

**解决方法**：将 -Force 参数与 Import-Module 一起使用。 例如，`Import-Module NetAdapter -Force`。

**问题**：将执行策略设置为"AllSigned"会中断 PowerShell 远程处理。 后续尝试创建远程会话失败，并加载了 securityException Typesv3.ps1xml。

**解决方法**：winrs.exe还原 PowerShell 的执行策略：
* 更改控制台代码页 `Chcp 65001`
* 登录到远程 cmd.exe shell `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* 在远程cmd.exe中，修改相应的注册表项 `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* 退出远程cmd.exe会话 `exit`

### <a name="other-known-issues"></a>其他已知问题

- 在 PowerShell 脚本中，PowerShell 类或枚举的属性不起作用。 添加属性会导致引发以下异常 *：Type 必须是运行时 Type 对象*。

- 不支持出站 CIM 和 PowerShell 远程处理。 依赖 cmdlet 中的相关功能将不起作用。 其中包括 Enter-PSSession、Get-Job、Receive-Job、Import-Module、Invoke-Command 和 Copy-Item。

- 除非使用 CredSSP ConvertFrom-SecureString创建会话，否则ConvertFrom-SecureString和 ConvertTo-SecureString 的 SecureString 命令不起作用。 否则，必须指定 -Key 参数。 有关配置 CredSSP 身份验证的详细信息，请参阅 [使用 CredSSP 启用 PowerShell"第二跃点"功能](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/)。
