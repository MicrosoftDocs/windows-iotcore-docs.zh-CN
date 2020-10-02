---
title: 安全外壳(SSH)
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用安全外壳远程管理和配置 IoT Core 设备。
keywords: windows iot，安全 shell，远程，SSH 客户端，PuTTY，SSH
ms.openlocfilehash: c30586135883cfe03a8aa9c6d7318717f07e9d7e
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656673"
---
# <a name="secure-shell-ssh"></a>安全外壳(SSH)
安全外壳 (SSH) 允许远程管理和配置 Windows IoT 核心设备

## <a name="using-the-windows-10-openssh-client"></a>使用 Windows 10 OpenSSH 客户端
> [!IMPORTANT]
> Windows OpenSSH 客户端要求 SSH 客户端主机操作系统为 Windows 10 版本 1803 (17134) 。 此外，Windows 10 IoT Core 设备必须运行 RS5 Windows 有问必答 Preview 版本17723或更高版本。

**OpenSSH 客户端**已添加到 1803 (生成 17134) 中的 Windows 10 作为可选功能。 若要安装客户端，你可以在 Windows 10 设置中搜索 " **管理可选功能** "。 如果已安装功能列表中未列出 OpenSSH 客户端，请选择 " **添加功能**"。

![添加功能](../media/SSH/add_a_feature.png)

接下来，在列表中选择 " **OpenSSH 客户端** "，然后单击 " **安装**"。

![OpenSSH 客户端安装](../media/SSH/optional_features.png)

若要使用用户名和密码登录，请使用以下命令：

```cmd
ssh administrator@host
```

其中 host 是 Windows IoT 核心设备的 IP 地址或设备名称。

首次连接时，会看到如下所示的消息：

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

键入 **yes** ，然后按 **enter**。

如果需要以 DefaultAccount 而不是管理员身份登录，则需要生成密钥并使用密钥登录。  在要从其连接到 IoT 设备的桌面中，打开 PowerShell 窗口，并更改为你的个人数据文件夹 (例如 cd ~) 

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

将密钥注册到 ssh 代理 (可选，以便) 单一登录体验。  请注意，ssh 添加必须从作为 ACL 的文件夹执行，作为已登录用户 (Builtin\Administrators，并且 NT_AUTHORITY \System 用户也是 ") "。  默认情况下，PowerShell 中的 cd ~ 应足以，如下所示。

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> 如果你收到一条消息，指出 ssh 代理服务已禁用，则可以使用 **sc.exe 配置 ssh-代理启动 = 自动**

若要启用单一登录，请将公钥附加到 Windows IoT Core 设备 **authorized_keys** 文件中。  或者，如果只有一个密钥，请将公钥文件复制到远程 **authorized_keys** 文件中。

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

如果未向 ssh 代理注册该密钥，则必须在命令行上指定该密钥才能登录：

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

如果私钥已注册到 ssh 代理，则只需指定 <strong>DefaultAccount@host</strong> ：

```cmd
ssh DefaultAccount@host
```

首次连接时，会看到如下所示的消息：

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

键入 **yes** ，然后按 **enter**。

现在，你应该已连接到 **DefaultAccount**

若要使用 **管理员** 帐户进行单一登录，请在 Windows IoT Core 设备上将公钥附加到 c:\data\programdata\ssh\ administrators_authorized_keys。

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

还需要将 administrators_authorized_keys 的 ACL 设置为与同一目录中 ssh_host_dsa_key 的 ACL 匹配。

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

使用 PowerShell 设置 ACL

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> 如果在更改 Windows 10 IoT Core 设备后看到**远程主机标识更改**消息，则编辑 C:\Users \<username> \. ssh \ known_hosts 并删除已更改的主机。

另请参阅： [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)

## <a name="using-putty"></a>使用 PuTTY

### <a name="download-an-ssh-client"></a>下载 SSH 客户端
要使用 SSH 连接到设备，首先需要下载 SSH 客户端，例如 [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)。

### <a name="connect-to-your-device"></a>连接到设备
* 若要连接到设备，需要首先获取设备的 IP 地址。  启动 Windows IoT Core 设备后，会在连接到设备的屏幕上显示一个 IP 地址：

    ![Windows IoT Core 上的 Defaultapp.osd](../media/SSH/DefaultApp.png)

* 现在，请启动 PuTTY 并在文本框中输入 IP 地址 `Host Name` ，并确保 `SSH` 选中 "单选按钮"。  然后单击 `Open` 。

    ![PuTTY 配置](../media/SSH/putty_config.png)

* 如果是第一次从计算机连接到设备，可能会看到以下安全警报。  只需单击 `Yes` 即可继续。

    ![PuTTY 安全警报](../media/SSH/putty_security_prompt.png)

* 如果连接成功，则会 `login as:` 在屏幕上看到提示你进行登录。  
    输入 `Administrator` ，然后按 enter。  然后输入默认密码 `p@ssw0rd` 作为密码，然后按 enter。

    ![PuTTY 登录](../media/SSH/putty_login.png)

    如果能够成功登录，应会看到如下所示的内容：

    ![PuTTY 控制台](../media/ssh/putty_console.png)

### <a name="update-account-password"></a>更新帐户密码

**强烈建议**您更新管理员帐户的默认密码。

为此，请在 PuTTY 控制台中输入以下命令， `[new password]` 并将替换为强密码：
```    
    net user Administrator [new password]
```    
### <a name="configure-your-windows-iot-core-device"></a>配置 Windows IoT Core 设备
* 若要从 Visual Studio 2017 部署应用程序，需要确保 Visual Studio 远程调试器在 Windows IoT Core 设备上运行。 远程调试器应在计算机启动时自动启动。 若要仔细检查，请使用 tlist.exe 命令列出 PowerShell 中所有正在运行的进程。 设备上应运行 msvsmon.exe 的两个实例。

* 在长时间的非活动状态后，Visual Studio 远程调试器可能会超时。 如果 Visual Studio 无法连接到 Windows IoT Core 设备，请尝试重新启动设备。

* 如果需要，也可以重命名设备。 若要更改 "计算机名称"，请使用 `setcomputername` 实用工具：
```
        setcomputername <new-name>
```
你将需要重新启动设备以使更改生效。 你可以使用命令，如下所示 `shutdown` ：
```
        shutdown /r /t 0
```
### <a name="commonly-used-utilities"></a>常用实用程序

请参阅 [命令行 Utils](../manage-your-device/CommandLineUtils.md) 页，获取可用于 SSH 的命令和实用工具的列表。
