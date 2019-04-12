---
title: 安全外壳 (SSH)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用安全外壳用于远程管理和配置 IoT Core 设备。
keywords: windows iot、 安全外壳、 远程、 SSH 客户端，PuTTY、 SSH
ms.openlocfilehash: 2c83184507a840c6017b1dfe36ac915004057d9a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510851"
---
# <a name="secure-shell-ssh"></a>安全外壳 (SSH)
安全外壳 (SSH) 允许您远程管理和配置 Windows IoT Core 设备

## <a name="using-the-windows-10-openssh-client"></a>使用 Windows 10 OpenSSH 客户端
> [!IMPORTANT]
> Windows OpenSSH 客户端需要 SSH 客户端主机操作系统是 Windows 10 版本 1803(17134)。 此外，Windows 10 IoT Core 设备必须运行 RS5 Windows Insider Preview 版本 17723 或更高版本。

**OpenSSH 客户端**已添加到 Windows 10 中 1803 （内部版本 17134） 作为一项可选功能。 若要安装客户端可以搜索**管理可选功能**中的 Windows 10 设置。 如果**OpenSSH 客户端**在已安装的功能列表中未列出，则选择**添加一项功能**。

![添加一项功能](../media/SSH/add_a_feature.png)

接下来，选择**OpenSSH 客户端**在列表中，单击**安装**。

![OpenSSH 客户端安装](../media/SSH/optional_features.png)

若要使用用户名和密码使用以下命令登录：

```cmd
ssh administrator@host
```

其中，主机是 Windows IoT Core 设备的 IP 地址或设备名称。

首次连接你看到一条消息如下所示：

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

类型**是**然后按**输入**。

如果您需要以登录**DefaultAccount**而非以管理员身份将需要生成密钥并使用密钥来以用户身份登录。  从想要连接到从 IoT 设备的桌面，打开 powershell 窗口并将更改为你的个人数据的文件夹 (例如 cd ~)

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

与 ssh 配合使用-代理 （可选，对于单一登录体验） 注册密钥。  请注意，ssh 配合使用-添加必须执行从文件夹的 ACL 将给您作为登录的用户 （Builtin\Administrators 和 NT_AUTHORITY\System 用户也是确定）。  通过默认 cd ~ 从 powershell 应该是够用的如下所示。

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> 如果你收到一条消息，禁用 ssh 代理服务可以让其与**sc.exe 配置 ssh 代理开始 = auto**

若要启用单一登录的公钥追加到 Windows IoT Core 设备**authorized_keys**文件。  或者如果只有一个密钥，复制公钥文件到远程**authorized_keys**文件。

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

如果不使用 ssh 代理注册的密钥，则必须登录在命令行上指定： 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

如果使用 ssh 代理注册的专用密钥，则只需指定<strong>DefaultAccount@host</strong>:

```cmd
ssh DefaultAccount@host
```

首次连接你看到一条消息如下所示：

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

类型**是**然后按**输入**。

用户现在将作为连接**DefaultAccount**

若要使用单一登录与**管理员**帐户，请将您的公钥追加到 c:\data\ProgramData\ssh\administrators_authorized_keys Windows IoT Core 设备上。 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

您还需要设置 administrators_authorized_keys 的 ACL 以匹配 ssh_host_dsa_key 相同的目录中的 ACL。

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

若要设置使用 powershell 的 ACL

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> 如果您看到**远程主机标识更改**对 Windows 10 IoT Core 设备进行更改后的消息，然后编辑 C:\Users\<用户名 >\.ssh\known_hosts 并删除已更改的主机。

另请参阅：[Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)

## <a name="using-putty"></a>使用 PuTTY

### <a name="download-a-ssh-client"></a>下载 SSH 客户端
若要使用 SSH 连接到设备，你将首先需要下载一个 SSH 客户端，例如 [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)。

### <a name="connect-to-your-device"></a>连接到设备
* 若要连接到设备，你首先需要获取设备的 IP 地址。  在启动 Windows IoT 核心版设备后，与该设备相连的屏幕上将显示一个 IP 地址：

    ![Windows IoT 核心版上的 DefaultApp](../media/SSH/DefaultApp.png)

* 现在，启动 PuTTY 并在 `Host Name` 文本框中输入 IP 地址，然后确保选择 `SSH` 单选按钮。  然后单击“`Open`”。

    ![PuTTY 配置](../media/SSH/putty_config.png)

* 如果你是首次从计算机连接到设备，你可能会看到以下安全警告。  只需单击 `Yes` 继续。

    ![PuTTY 安全警报](../media/SSH/putty_security_prompt.png)

* 如果连接成功，你应在屏幕上看到 `login as:`，提示你进行登录。  
    输入 `Administrator` 并按 Enter。  然后输入默认密码 `p@ssw0rd` 作为密码，并按 Enter。

    ![PuTTY 登录](../media/SSH/putty_login.png)

    如果你能够成功登录，你应看到如下内容：

    ![PuTTY 控制台](../media/ssh/putty_console.png)

### <a name="update-account-password"></a>更新帐户密码

**强烈建议**你更新管理员帐户的默认密码。

若要执行此操作，请在 PuTTY 控制台中输入以下命令，从而使用强密码替换 `[new password]`：
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a>配置 Windows IoT 核心版设备
* 为了能够从 Visual Studio 2017 部署应用程序，您需要确保 Windows IoT Core 设备上运行 Visual Studio 远程调试器。 远程调试器应在计算机启动时自动启动。 若要再次检查，请使用 tlist 命令从 powershell 列出所有正在运行的进程。 应有两个 msvsmon.exe 的实例正在设备上运行。

* 在很长一段时间都处于非活动状态后，Visual Studio 远程调试器可能会超时。 如果 Visual Studio 无法连接到 Windows IoT 核心版设备，请尝试重新启动设备。

* 你还可以根据需要重命名你的设备。 若要更改“计算机名”，请使用 `setcomputername` 实用工具：

        setcomputername <new-name>

    需要重新启动设备才能使更改生效。 可以使用 `shutdown` 命令，如下所示：

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a>常用的实用工具

有关可以与 SSH 结合使用的命令和实用工具的列表，请参阅[命令行实用工具](../manage-your-device/CommandLineUtils.md)页面。
