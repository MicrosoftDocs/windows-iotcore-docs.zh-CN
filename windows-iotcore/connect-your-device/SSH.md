---
title: 安全外壳 (SSH)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用安全外壳远程管理和配置 IoT Core 设备。
keywords: windows iot, 安全 shell, 远程, SSH 客户端, PuTTY, SSH
ms.openlocfilehash: 2c83184507a840c6017b1dfe36ac915004057d9a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168722"
---
# <a name="secure-shell-ssh"></a><span data-ttu-id="3f262-104">安全外壳 (SSH)</span><span class="sxs-lookup"><span data-stu-id="3f262-104">Secure Shell (SSH)</span></span>
<span data-ttu-id="3f262-105">安全外壳 (SSH) 允许远程管理和配置 Windows IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="3f262-105">Secure Shell (SSH) allows you to remotely administer and configure your Windows IoT Core device</span></span>

## <a name="using-the-windows-10-openssh-client"></a><span data-ttu-id="3f262-106">使用 Windows 10 OpenSSH 客户端</span><span class="sxs-lookup"><span data-stu-id="3f262-106">Using the Windows 10 OpenSSH client</span></span>
> [!IMPORTANT]
> <span data-ttu-id="3f262-107">Windows OpenSSH 客户端要求 SSH 客户端主机操作系统为 Windows 10 版本 1803 (版本 17134)。</span><span class="sxs-lookup"><span data-stu-id="3f262-107">The Windows OpenSSH client requires that your SSH client host OS is Windows 10 version 1803(17134).</span></span> <span data-ttu-id="3f262-108">此外, Windows 10 IoT Core 设备必须运行 RS5 Windows 有问必答 Preview 版本17723或更高版本。</span><span class="sxs-lookup"><span data-stu-id="3f262-108">Also, the Windows 10 IoT Core device must be running RS5 Windows Insider Preview release 17723 or greater.</span></span>

<span data-ttu-id="3f262-109">**OpenSSH 客户端**已添加到 1803 (版本 17134) 中的 Windows 10 作为可选功能。</span><span class="sxs-lookup"><span data-stu-id="3f262-109">The **OpenSSH Client** was added to Windows 10 in 1803 (build 17134) as an optional feature.</span></span> <span data-ttu-id="3f262-110">若要安装客户端, 你可以在 Windows 10 设置中搜索 "**管理可选功能**"。</span><span class="sxs-lookup"><span data-stu-id="3f262-110">To install the client you can search for **Manage Optional Features** in Windows 10 settings.</span></span> <span data-ttu-id="3f262-111">如果已安装功能列表中未列出**OpenSSH 客户端**, 请选择 "**添加功能**"。</span><span class="sxs-lookup"><span data-stu-id="3f262-111">If the **OpenSSH Client** is not listed in the list of installed features then choose **Add a feature**.</span></span>

![添加功能](../media/SSH/add_a_feature.png)

<span data-ttu-id="3f262-113">接下来, 在列表中选择 " **OpenSSH 客户端**", 然后单击 "**安装**"。</span><span class="sxs-lookup"><span data-stu-id="3f262-113">Next select **OpenSSH Client** in the list and click **Install**.</span></span>

![OpenSSH 客户端安装](../media/SSH/optional_features.png)

<span data-ttu-id="3f262-115">若要使用用户名和密码登录, 请使用以下命令:</span><span class="sxs-lookup"><span data-stu-id="3f262-115">To login with a username and password use the following command:</span></span>

```cmd
ssh administrator@host
```

<span data-ttu-id="3f262-116">其中 host 是 Windows IoT 核心设备的 IP 地址或设备名称。</span><span class="sxs-lookup"><span data-stu-id="3f262-116">Where host is either the IP address of the Windows IoT Core device or the device name.</span></span>

<span data-ttu-id="3f262-117">首次连接时, 会看到如下所示的消息:</span><span class="sxs-lookup"><span data-stu-id="3f262-117">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="3f262-118">键入**yes** , 然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="3f262-118">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="3f262-119">如果需要以**DefaultAccount**而不是管理员身份登录, 则需要生成一个密钥并使用密钥登录。</span><span class="sxs-lookup"><span data-stu-id="3f262-119">If you need to log in as **DefaultAccount** rather than as administrator you will need to generate a key and use the key to log in.</span></span>  <span data-ttu-id="3f262-120">在要从其连接到 IoT 设备的桌面上, 打开 powershell 窗口, 并更改为你的个人数据文件夹 (例如 cd ~)</span><span class="sxs-lookup"><span data-stu-id="3f262-120">From the desktop that you intend to connect to your IoT Device from, open a powershell window and change to your personal data folder (e.g cd ~)</span></span>

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

<span data-ttu-id="3f262-121">将密钥注册到 ssh 代理 (可选, 用于单一登录体验)。</span><span class="sxs-lookup"><span data-stu-id="3f262-121">Register the key with ssh-agent (optional, for single sign-on experience).</span></span>  <span data-ttu-id="3f262-122">请注意, 必须从作为已登录用户的 ACL 的文件夹中执行 ssh 添加 (Builtin\Administrators, NT_AUTHORITY\System 用户也可以)。</span><span class="sxs-lookup"><span data-stu-id="3f262-122">Note that ssh-add must be performed from a folder that is  ACL'd to you as the signed-in user (Builtin\Administrators and the NT_AUTHORITY\System user are also ok).</span></span>  <span data-ttu-id="3f262-123">默认情况下, powershell 中的 cd ~ 应足以, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="3f262-123">By default cd ~ from powershell should be sufficient as shown below.</span></span>

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> <span data-ttu-id="3f262-124">如果你收到一条消息, 指出 ssh 代理服务已被禁用, 则可以使用**sc config ssh 启动 = 自动**</span><span class="sxs-lookup"><span data-stu-id="3f262-124">If you receive a message that the ssh-agent service is disabled you can enable it with **sc.exe config ssh-agent start=auto**</span></span>

<span data-ttu-id="3f262-125">若要启用单个 sign, 请将公钥附加到 Windows IoT Core 设备**authorized_keys**文件。</span><span class="sxs-lookup"><span data-stu-id="3f262-125">To enable single sign append the public key to the Windows IoT Core device **authorized_keys** file.</span></span>  <span data-ttu-id="3f262-126">或者, 如果只有一个密钥, 请将公钥文件复制到远程**authorized_keys**文件。</span><span class="sxs-lookup"><span data-stu-id="3f262-126">Or if you only have one key you copy the public key file to the remote **authorized_keys** file.</span></span>

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

<span data-ttu-id="3f262-127">如果未向 ssh 代理注册该密钥, 则必须在命令行上指定登录名:</span><span class="sxs-lookup"><span data-stu-id="3f262-127">If the key is not registered with ssh-agent it must be specified on the command line to login:</span></span> 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

<span data-ttu-id="3f262-128">如果私钥已注册到 ssh 代理, 则只需指定<strong>DefaultAccount@host</strong>:</span><span class="sxs-lookup"><span data-stu-id="3f262-128">If the private key is registered with ssh-agent then you only need to specify <strong>DefaultAccount@host</strong>:</span></span>

```cmd
ssh DefaultAccount@host
```

<span data-ttu-id="3f262-129">首次连接时, 会看到如下所示的消息:</span><span class="sxs-lookup"><span data-stu-id="3f262-129">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="3f262-130">键入**yes** , 然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="3f262-130">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="3f262-131">现在, 你应该已连接到**DefaultAccount**</span><span class="sxs-lookup"><span data-stu-id="3f262-131">You should now be connected as **DefaultAccount**</span></span>

<span data-ttu-id="3f262-132">若要使用**管理员**帐户进行单一登录, 请在 Windows IoT Core 设备上将公钥附加到 c:\data\ProgramData\ssh\administrators_authorized_keys。</span><span class="sxs-lookup"><span data-stu-id="3f262-132">To use single sign-on with the **administrator** account, append your public key to c:\data\ProgramData\ssh\administrators_authorized_keys on the Windows IoT Core device.</span></span> 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="3f262-133">还需要设置 administrators_authorized_keys 的 ACL, 使其与同一个目录中 ssh_host_dsa_key 的 ACL 匹配。</span><span class="sxs-lookup"><span data-stu-id="3f262-133">You will also need to set the ACL for administrators_authorized_keys to match the ACL of ssh_host_dsa_key in the same directory.</span></span>

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="3f262-134">使用 powershell 设置 ACL</span><span class="sxs-lookup"><span data-stu-id="3f262-134">To set the ACL using powershell</span></span>

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> <span data-ttu-id="3f262-135">如果在更改 Windows 10 IoT Core 设备后看到**远程主机标识更改**消息, 则编辑 C:\Users\<username >\.ssh\known_hosts, 并删除已更改的主机。</span><span class="sxs-lookup"><span data-stu-id="3f262-135">If you see a **REMOTE HOST IDENTIFICATION CHANGED** message after making changes to the Windows 10 IoT Core device, then edit C:\Users\<username>\.ssh\known_hosts and remove the host that has changed.</span></span>

<span data-ttu-id="3f262-136">另请参阅：[Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span><span class="sxs-lookup"><span data-stu-id="3f262-136">See also: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span></span>

## <a name="using-putty"></a><span data-ttu-id="3f262-137">使用 PuTTY</span><span class="sxs-lookup"><span data-stu-id="3f262-137">Using PuTTY</span></span>

### <a name="download-a-ssh-client"></a><span data-ttu-id="3f262-138">下载 SSH 客户端</span><span class="sxs-lookup"><span data-stu-id="3f262-138">Download a SSH client</span></span>
<span data-ttu-id="3f262-139">若要使用 SSH 连接到设备，你将首先需要下载一个 SSH 客户端，例如 [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)。</span><span class="sxs-lookup"><span data-stu-id="3f262-139">In order to connect to your device using SSH, you'll first need to download a SSH client, such as [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).</span></span>

### <a name="connect-to-your-device"></a><span data-ttu-id="3f262-140">连接到设备</span><span class="sxs-lookup"><span data-stu-id="3f262-140">Connect to your device</span></span>
* <span data-ttu-id="3f262-141">若要连接到设备，你首先需要获取设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3f262-141">In order to connect to your device, you need to first get the IP address of the device.</span></span>  <span data-ttu-id="3f262-142">在启动 Windows IoT 核心版设备后，与该设备相连的屏幕上将显示一个 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="3f262-142">After booting your Windows IoT Core device, an IP address will be shown on the screen attached to the device:</span></span>

    ![Windows IoT 核心版上的 DefaultApp](../media/SSH/DefaultApp.png)

* <span data-ttu-id="3f262-144">现在，启动 PuTTY 并在 `Host Name` 文本框中输入 IP 地址，然后确保选择 `SSH` 单选按钮。</span><span class="sxs-lookup"><span data-stu-id="3f262-144">Now launch PuTTY and enter the IP address in the `Host Name` text box and make sure the `SSH` radio button is selected.</span></span>  <span data-ttu-id="3f262-145">然后单击“`Open`”。</span><span class="sxs-lookup"><span data-stu-id="3f262-145">Then click `Open`.</span></span>

    ![PuTTY 配置](../media/SSH/putty_config.png)

* <span data-ttu-id="3f262-147">如果你是首次从计算机连接到设备，你可能会看到以下安全警告。</span><span class="sxs-lookup"><span data-stu-id="3f262-147">If you're connecting to your device for the first time from your computer, you may see the following security alert.</span></span>  <span data-ttu-id="3f262-148">只需单击 `Yes` 继续。</span><span class="sxs-lookup"><span data-stu-id="3f262-148">Just click `Yes` to continue.</span></span>

    ![PuTTY 安全警报](../media/SSH/putty_security_prompt.png)

* <span data-ttu-id="3f262-150">如果连接成功，你应在屏幕上看到 `login as:`，提示你进行登录。</span><span class="sxs-lookup"><span data-stu-id="3f262-150">If the connection was successful, you should see `login as:` on the screen, prompting you to login.</span></span>  
    <span data-ttu-id="3f262-151">输入 `Administrator` 并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="3f262-151">Enter `Administrator` and press enter.</span></span>  <span data-ttu-id="3f262-152">然后输入默认密码 `p@ssw0rd` 作为密码，并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="3f262-152">Then enter the default password `p@ssw0rd` as the password and press enter.</span></span>

    ![PuTTY 登录](../media/SSH/putty_login.png)

    <span data-ttu-id="3f262-154">如果你能够成功登录，你应看到如下内容：</span><span class="sxs-lookup"><span data-stu-id="3f262-154">If you were able to login successfully, you should see something like this:</span></span>

    ![PuTTY 控制台](../media/ssh/putty_console.png)

### <a name="update-account-password"></a><span data-ttu-id="3f262-156">更新帐户密码</span><span class="sxs-lookup"><span data-stu-id="3f262-156">Update account password</span></span>

<span data-ttu-id="3f262-157">**强烈建议**你更新管理员帐户的默认密码。</span><span class="sxs-lookup"><span data-stu-id="3f262-157">It is **highly recommended** that you update the default password for the Administrator account.</span></span>

<span data-ttu-id="3f262-158">若要执行此操作，请在 PuTTY 控制台中输入以下命令，从而使用强密码替换 `[new password]`：</span><span class="sxs-lookup"><span data-stu-id="3f262-158">To do this, enter the following command in the PuTTY console, replacing `[new password]` with a strong password:</span></span>
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="3f262-159">配置 Windows IoT 核心版设备</span><span class="sxs-lookup"><span data-stu-id="3f262-159">Configure your Windows IoT Core device</span></span>
* <span data-ttu-id="3f262-160">若要从 Visual Studio 2017 部署应用程序, 需要确保 Visual Studio 远程调试器在 Windows IoT Core 设备上运行。</span><span class="sxs-lookup"><span data-stu-id="3f262-160">To be able to deploy applications from Visual Studio 2017, you will need to make sure the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="3f262-161">远程调试器应在计算机启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="3f262-161">The remote debugger should launch automatically at machine boot time.</span></span> <span data-ttu-id="3f262-162">若要再次检查，请使用 tlist 命令从 powershell 列出所有正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="3f262-162">To double check, use the tlist command to list all the running processes from powershell.</span></span> <span data-ttu-id="3f262-163">应有两个 msvsmon.exe 的实例正在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="3f262-163">There should be two instances of msvsmon.exe running on the device.</span></span>

* <span data-ttu-id="3f262-164">在很长一段时间都处于非活动状态后，Visual Studio 远程调试器可能会超时。</span><span class="sxs-lookup"><span data-stu-id="3f262-164">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="3f262-165">如果 Visual Studio 无法连接到 Windows IoT 核心版设备，请尝试重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="3f262-165">If Visual Studio cannot connect to your Windows IoT Core device, try rebooting the device.</span></span>

* <span data-ttu-id="3f262-166">你还可以根据需要重命名你的设备。</span><span class="sxs-lookup"><span data-stu-id="3f262-166">If you want, you can also rename your device.</span></span> <span data-ttu-id="3f262-167">若要更改“计算机名”，请使用 `setcomputername` 实用工具：</span><span class="sxs-lookup"><span data-stu-id="3f262-167">To change the 'computer name', use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

    <span data-ttu-id="3f262-168">需要重新启动设备才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="3f262-168">You will need to reboot the device for the change to take effect.</span></span> <span data-ttu-id="3f262-169">可以使用 `shutdown` 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f262-169">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a><span data-ttu-id="3f262-170">常用的实用工具</span><span class="sxs-lookup"><span data-stu-id="3f262-170">Commonly used utilities</span></span>

<span data-ttu-id="3f262-171">有关可以与 SSH 结合使用的命令和实用工具的列表，请参阅[命令行实用工具](../manage-your-device/CommandLineUtils.md)页面。</span><span class="sxs-lookup"><span data-stu-id="3f262-171">See the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page for a list of commands and utilities you can use with SSH.</span></span>
