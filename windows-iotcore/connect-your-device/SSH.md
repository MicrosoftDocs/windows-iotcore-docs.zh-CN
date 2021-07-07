---
title: 安全外壳(SSH)
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用安全外壳远程管理和配置 IoT Core 设备。
keywords: windows iot， 安全外壳， 远程， SSH 客户端， PuTTY， SSH
ms.openlocfilehash: 539e7c30e5a13477a35ee71d4660e1f4e6ed3bc8
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229195"
---
# <a name="secure-shell-ssh"></a>安全外壳(SSH)
安全外壳 (SSH) ，可以远程管理和配置 Windows IoT Core 设备

## <a name="using-the-windows-10-openssh-client"></a>使用 Windows 10 OpenSSH 客户端
> [!IMPORTANT]
> OpenSSH Windows要求 SSH 客户端主机 OS Windows 10版本 1803 (17134) 。 此外，Windows 10 IoT 核心版设备必须运行 RS5 Windows Insider Preview版本 17723 或更大版本。

**OpenSSH 客户端** 已添加到 Windows 10 1803 (版本 17134) 作为可选功能。 若要安装客户端，可以在设置中搜索 **"** 管理可选Windows 10功能。 如果已安装功能列表中未列出 OpenSSH 客户端，请选择"**添加功能"。**

![添加功能](../media/SSH/add_a_feature.png)

接下来，在 **列表中选择"OpenSSH** 客户端"，然后单击"安装 **"。**

![OpenSSH 客户端安装](../media/SSH/optional_features.png)

若要使用用户名和密码登录，请使用以下命令：

```cmd
ssh administrator@host
```

其中 host 是 IoT 核心Windows IP 地址或设备名称。

首次连接时，会看到如下所示的消息：

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

键入 **"是** "，然后 **按 Enter**。

如果需要以 DefaultAccount（而不是管理员）登录，则需要生成密钥并使用密钥登录。  在要连接到 IoT 设备的桌面上，打开 PowerShell 窗口，并更改为个人数据文件夹 (例如 cd ~) 

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

将密钥注册到 ssh-agent (可选，用于单一登录) 。  请注意，ssh-add 必须从 ACL 为 d 的文件夹执行，因为登录用户 (Builtin\Administrators 和 NT_AUTHORITY\System 用户也) 。  默认情况下，PowerShell 中的 cd ~ 应已足够，如下所示。

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> 如果收到 ssh-agent 服务已禁用的消息，可以使用配置 **ssh-agent start=auto** sc.exe启用它

若要启用单一登录，请将公钥追加到 Windows IoT Core 设备 **authorized_keys** 文件。  或者，如果只有一个密钥，则将公钥文件 **复制到远程authorized_keys** 文件。

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

如果未向 ssh-agent 注册密钥，则必须在命令行上指定该密钥才能登录：

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

如果私钥已注册到 ssh-agent，则只需指定 <strong>DefaultAccount@host</strong> ：

```cmd
ssh DefaultAccount@host
```

首次连接时，会看到如下所示的消息：

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

键入 **"是** "，然后 **按 Enter**。

现在应作为 **DefaultAccount 进行连接**

若要对管理员帐户使用单一登录，请在你的 IoT 核心设备上将公钥追加到 c：\data\ProgramData\ssh\administrators_authorized_keys Windows。

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

还需要为同一目录中administrators_authorized_keys ACL，以匹配ssh_host_dsa_key的 ACL。

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

使用 PowerShell 设置 ACL

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> 如果在 **对设备进行更改** 后看到"远程主机标识已更改Windows 10 IoT 核心版，请编辑 C：\Users \<username> \. ssh\known_hosts并删除已更改的主机。

另请参阅 [：Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)

## <a name="using-putty"></a>使用 PuTTY

### <a name="download-an-ssh-client"></a>下载 SSH 客户端
若要使用 SSH 连接到设备，首先需要下载 SSH 客户端，例如[PuTTY。](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)

### <a name="connect-to-your-device"></a>连接到设备
* 若要连接到设备，首先需要获取设备的 IP 地址。  启动 IoT 核心Windows后，附加到设备的屏幕上会显示一个 IP 地址：

    ![IoT 核心Windows DefaultApp](../media/SSH/DefaultApp.png)

* 现在启动 PuTTY，在文本框中输入 IP 地址 `Host Name` ，并确保选中 `SSH` 单选按钮。  然后单击 `Open` 。

    ![PuTTY 配置](../media/SSH/putty_config.png)

* 如果首次从计算机连接到设备，可能会看到以下安全警报。  只需单击 `Yes` 以继续。

    ![PuTTY 安全警报](../media/SSH/putty_security_prompt.png)

* 如果连接成功，应会 `login as:` 在屏幕上看到 ，提示你登录。  
    输入 `Administrator` 并按 Enter。  然后输入默认密码 `p@ssw0rd` 作为密码，然后按 Enter。

    ![PuTTY 登录](../media/SSH/putty_login.png)

    如果能够成功登录，应会看到如下所示：

    ![PuTTY 控制台](../media/ssh/putty_console.png)

### <a name="update-account-password"></a>更新帐户密码

强烈建议 **更新** 管理员帐户的默认密码。

为此，请在 PuTTY 控制台中输入以下命令，将 `[new password]` 替换为强密码：
```    
    net user Administrator [new password]
```    
### <a name="configure-your-windows-iot-core-device"></a>配置 Windows IoT Core 设备
* 若要从 2017 Visual Studio部署应用程序，需要确保 Visual Studio 远程调试器 IoT Core 设备上Windows运行。 远程调试器应在计算机启动时自动启动。 若要仔细检查，请使用 tlist 命令列出 PowerShell 中所有正在运行的进程。 设备上应运行两msvsmon.exe实例。

* 长时间处于非Visual Studio 远程调试器后，系统可能会超时。 如果Visual Studio IoT Core Windows，请尝试重新启动设备。

* 如果需要，还可以重命名设备。 若要更改"计算机名"，请使用 `setcomputername` 实用工具：
```
        setcomputername <new-name>
```
需要重新启动设备，更改才能生效。 可以使用 命令 `shutdown` ，如下所示：
```
        shutdown /r /t 0
```
### <a name="commonly-used-utilities"></a>常用实用工具

有关可用于 SSH 的命令和实用程序的列表，请参阅命令行 [Utils](../manage-your-device/CommandLineUtils.md) 页。
