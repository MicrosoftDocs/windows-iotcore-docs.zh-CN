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
# <a name="secure-shell-ssh"></a><span data-ttu-id="9b357-104">安全外壳(SSH)</span><span class="sxs-lookup"><span data-stu-id="9b357-104">Secure Shell (SSH)</span></span>
<span data-ttu-id="9b357-105">安全外壳 (SSH) ，可以远程管理和配置 Windows IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="9b357-105">Secure Shell (SSH) allows you to remotely administer and configure your Windows IoT Core device</span></span>

## <a name="using-the-windows-10-openssh-client"></a><span data-ttu-id="9b357-106">使用 Windows 10 OpenSSH 客户端</span><span class="sxs-lookup"><span data-stu-id="9b357-106">Using the Windows 10 OpenSSH client</span></span>
> [!IMPORTANT]
> <span data-ttu-id="9b357-107">OpenSSH Windows要求 SSH 客户端主机 OS Windows 10版本 1803 (17134) 。</span><span class="sxs-lookup"><span data-stu-id="9b357-107">The Windows OpenSSH client requires that your SSH client host OS is Windows 10 version 1803(17134).</span></span> <span data-ttu-id="9b357-108">此外，Windows 10 IoT 核心版设备必须运行 RS5 Windows Insider Preview版本 17723 或更大版本。</span><span class="sxs-lookup"><span data-stu-id="9b357-108">Also, the Windows 10 IoT Core device must be running RS5 Windows Insider Preview release 17723 or greater.</span></span>

<span data-ttu-id="9b357-109">**OpenSSH 客户端** 已添加到 Windows 10 1803 (版本 17134) 作为可选功能。</span><span class="sxs-lookup"><span data-stu-id="9b357-109">The **OpenSSH Client** was added to Windows 10 in 1803 (build 17134) as an optional feature.</span></span> <span data-ttu-id="9b357-110">若要安装客户端，可以在设置中搜索 **"** 管理可选Windows 10功能。</span><span class="sxs-lookup"><span data-stu-id="9b357-110">To install the client, you can search for **Manage Optional Features** in Windows 10 settings.</span></span> <span data-ttu-id="9b357-111">如果已安装功能列表中未列出 OpenSSH 客户端，请选择"**添加功能"。**</span><span class="sxs-lookup"><span data-stu-id="9b357-111">If the OpenSSH Client is not listed in the list of installed features, then choose **Add a feature**.</span></span>

![添加功能](../media/SSH/add_a_feature.png)

<span data-ttu-id="9b357-113">接下来，在 **列表中选择"OpenSSH** 客户端"，然后单击"安装 **"。**</span><span class="sxs-lookup"><span data-stu-id="9b357-113">Next select **OpenSSH Client** in the list and click **Install**.</span></span>

![OpenSSH 客户端安装](../media/SSH/optional_features.png)

<span data-ttu-id="9b357-115">若要使用用户名和密码登录，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="9b357-115">To login with a username and password use the following command:</span></span>

```cmd
ssh administrator@host
```

<span data-ttu-id="9b357-116">其中 host 是 IoT 核心Windows IP 地址或设备名称。</span><span class="sxs-lookup"><span data-stu-id="9b357-116">Where host is either the IP address of the Windows IoT Core device or the device name.</span></span>

<span data-ttu-id="9b357-117">首次连接时，会看到如下所示的消息：</span><span class="sxs-lookup"><span data-stu-id="9b357-117">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="9b357-118">键入 **"是** "，然后 **按 Enter**。</span><span class="sxs-lookup"><span data-stu-id="9b357-118">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="9b357-119">如果需要以 DefaultAccount（而不是管理员）登录，则需要生成密钥并使用密钥登录。</span><span class="sxs-lookup"><span data-stu-id="9b357-119">If you need to login as DefaultAccount rather than as administrator, you will need to generate a key and use the key to login.</span></span>  <span data-ttu-id="9b357-120">在要连接到 IoT 设备的桌面上，打开 PowerShell 窗口，并更改为个人数据文件夹 (例如 cd ~) </span><span class="sxs-lookup"><span data-stu-id="9b357-120">From the desktop that you intend to connect to your IoT Device from, open a PowerShell window and change to your personal data folder (e.g cd ~)</span></span>

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

<span data-ttu-id="9b357-121">将密钥注册到 ssh-agent (可选，用于单一登录) 。</span><span class="sxs-lookup"><span data-stu-id="9b357-121">Register the key with ssh-agent (optional, for single sign-on experience).</span></span>  <span data-ttu-id="9b357-122">请注意，ssh-add 必须从 ACL 为 d 的文件夹执行，因为登录用户 (Builtin\Administrators 和 NT_AUTHORITY\System 用户也) 。</span><span class="sxs-lookup"><span data-stu-id="9b357-122">Note that ssh-add must be performed from a folder that is  ACL'd to you as the signed-in user (Builtin\Administrators and the NT_AUTHORITY\System user are also ok).</span></span>  <span data-ttu-id="9b357-123">默认情况下，PowerShell 中的 cd ~ 应已足够，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9b357-123">By default cd ~ from PowerShell should be sufficient as shown below.</span></span>

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> <span data-ttu-id="9b357-124">如果收到 ssh-agent 服务已禁用的消息，可以使用配置 **ssh-agent start=auto** sc.exe启用它</span><span class="sxs-lookup"><span data-stu-id="9b357-124">If you receive a message that the ssh-agent service is disabled you can enable it with **sc.exe config ssh-agent start=auto**</span></span>

<span data-ttu-id="9b357-125">若要启用单一登录，请将公钥追加到 Windows IoT Core 设备 **authorized_keys** 文件。</span><span class="sxs-lookup"><span data-stu-id="9b357-125">To enable single sign, append the public key to the Windows IoT Core device **authorized_keys** file.</span></span>  <span data-ttu-id="9b357-126">或者，如果只有一个密钥，则将公钥文件 **复制到远程authorized_keys** 文件。</span><span class="sxs-lookup"><span data-stu-id="9b357-126">Or if you only have one key you copy the public key file to the remote **authorized_keys** file.</span></span>

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

<span data-ttu-id="9b357-127">如果未向 ssh-agent 注册密钥，则必须在命令行上指定该密钥才能登录：</span><span class="sxs-lookup"><span data-stu-id="9b357-127">If the key is not registered with ssh-agent, it must be specified on the command line to login:</span></span>

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

<span data-ttu-id="9b357-128">如果私钥已注册到 ssh-agent，则只需指定 <strong>DefaultAccount@host</strong> ：</span><span class="sxs-lookup"><span data-stu-id="9b357-128">If the private key is registered with ssh-agent, then you only need to specify <strong>DefaultAccount@host</strong>:</span></span>

```cmd
ssh DefaultAccount@host
```

<span data-ttu-id="9b357-129">首次连接时，会看到如下所示的消息：</span><span class="sxs-lookup"><span data-stu-id="9b357-129">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="9b357-130">键入 **"是** "，然后 **按 Enter**。</span><span class="sxs-lookup"><span data-stu-id="9b357-130">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="9b357-131">现在应作为 **DefaultAccount 进行连接**</span><span class="sxs-lookup"><span data-stu-id="9b357-131">You should now be connected as **DefaultAccount**</span></span>

<span data-ttu-id="9b357-132">若要对管理员帐户使用单一登录，请在你的 IoT 核心设备上将公钥追加到 c：\data\ProgramData\ssh\administrators_authorized_keys Windows。</span><span class="sxs-lookup"><span data-stu-id="9b357-132">To use single sign-on with the **administrator** account, append your public key to c:\data\ProgramData\ssh\administrators_authorized_keys on the Windows IoT Core device.</span></span>

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="9b357-133">还需要为同一目录中administrators_authorized_keys ACL，以匹配ssh_host_dsa_key的 ACL。</span><span class="sxs-lookup"><span data-stu-id="9b357-133">You will also need to set the ACL for administrators_authorized_keys to match the ACL of ssh_host_dsa_key in the same directory.</span></span>

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="9b357-134">使用 PowerShell 设置 ACL</span><span class="sxs-lookup"><span data-stu-id="9b357-134">To set the ACL using PowerShell</span></span>

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> <span data-ttu-id="9b357-135">如果在 **对设备进行更改** 后看到"远程主机标识已更改Windows 10 IoT 核心版，请编辑 C：\Users \<username> \. ssh\known_hosts并删除已更改的主机。</span><span class="sxs-lookup"><span data-stu-id="9b357-135">If you see a **REMOTE HOST IDENTIFICATION CHANGED** message after making changes to the Windows 10 IoT Core device, then edit C:\Users\<username>\.ssh\known_hosts and remove the host that has changed.</span></span>

<span data-ttu-id="9b357-136">另请参阅 [：Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span><span class="sxs-lookup"><span data-stu-id="9b357-136">See also: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span></span>

## <a name="using-putty"></a><span data-ttu-id="9b357-137">使用 PuTTY</span><span class="sxs-lookup"><span data-stu-id="9b357-137">Using PuTTY</span></span>

### <a name="download-an-ssh-client"></a><span data-ttu-id="9b357-138">下载 SSH 客户端</span><span class="sxs-lookup"><span data-stu-id="9b357-138">Download an SSH client</span></span>
<span data-ttu-id="9b357-139">若要使用 SSH 连接到设备，首先需要下载 SSH 客户端，例如[PuTTY。](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)</span><span class="sxs-lookup"><span data-stu-id="9b357-139">In order to connect to your device using SSH, you'll first need to download an SSH client, such as [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).</span></span>

### <a name="connect-to-your-device"></a><span data-ttu-id="9b357-140">连接到设备</span><span class="sxs-lookup"><span data-stu-id="9b357-140">Connect to your device</span></span>
* <span data-ttu-id="9b357-141">若要连接到设备，首先需要获取设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="9b357-141">In order to connect to your device, you need to first get the IP address of the device.</span></span>  <span data-ttu-id="9b357-142">启动 IoT 核心Windows后，附加到设备的屏幕上会显示一个 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="9b357-142">After booting your Windows IoT Core device, an IP address will be shown on the screen attached to the device:</span></span>

    ![IoT 核心Windows DefaultApp](../media/SSH/DefaultApp.png)

* <span data-ttu-id="9b357-144">现在启动 PuTTY，在文本框中输入 IP 地址 `Host Name` ，并确保选中 `SSH` 单选按钮。</span><span class="sxs-lookup"><span data-stu-id="9b357-144">Now launch PuTTY and enter the IP address in the `Host Name` text box and make sure the `SSH` radio button is selected.</span></span>  <span data-ttu-id="9b357-145">然后单击 `Open` 。</span><span class="sxs-lookup"><span data-stu-id="9b357-145">Then click `Open`.</span></span>

    ![PuTTY 配置](../media/SSH/putty_config.png)

* <span data-ttu-id="9b357-147">如果首次从计算机连接到设备，可能会看到以下安全警报。</span><span class="sxs-lookup"><span data-stu-id="9b357-147">If you're connecting to your device for the first time from your computer, you may see the following security alert.</span></span>  <span data-ttu-id="9b357-148">只需单击 `Yes` 以继续。</span><span class="sxs-lookup"><span data-stu-id="9b357-148">Just click `Yes` to continue.</span></span>

    ![PuTTY 安全警报](../media/SSH/putty_security_prompt.png)

* <span data-ttu-id="9b357-150">如果连接成功，应会 `login as:` 在屏幕上看到 ，提示你登录。</span><span class="sxs-lookup"><span data-stu-id="9b357-150">If the connection was successful, you should see `login as:` on the screen, prompting you to login.</span></span>  
    <span data-ttu-id="9b357-151">输入 `Administrator` 并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="9b357-151">Enter `Administrator` and press enter.</span></span>  <span data-ttu-id="9b357-152">然后输入默认密码 `p@ssw0rd` 作为密码，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="9b357-152">Then enter the default password `p@ssw0rd` as the password and press enter.</span></span>

    ![PuTTY 登录](../media/SSH/putty_login.png)

    <span data-ttu-id="9b357-154">如果能够成功登录，应会看到如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b357-154">If you were able to login successfully, you should see something like this:</span></span>

    ![PuTTY 控制台](../media/ssh/putty_console.png)

### <a name="update-account-password"></a><span data-ttu-id="9b357-156">更新帐户密码</span><span class="sxs-lookup"><span data-stu-id="9b357-156">Update account password</span></span>

<span data-ttu-id="9b357-157">强烈建议 **更新** 管理员帐户的默认密码。</span><span class="sxs-lookup"><span data-stu-id="9b357-157">It is **highly recommended** that you update the default password for the Administrator account.</span></span>

<span data-ttu-id="9b357-158">为此，请在 PuTTY 控制台中输入以下命令，将 `[new password]` 替换为强密码：</span><span class="sxs-lookup"><span data-stu-id="9b357-158">To do this, enter the following command in the PuTTY console, replacing `[new password]` with a strong password:</span></span>
```    
    net user Administrator [new password]
```    
### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="9b357-159">配置 Windows IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="9b357-159">Configure your Windows IoT Core device</span></span>
* <span data-ttu-id="9b357-160">若要从 2017 Visual Studio部署应用程序，需要确保 Visual Studio 远程调试器 IoT Core 设备上Windows运行。</span><span class="sxs-lookup"><span data-stu-id="9b357-160">To be able to deploy applications from Visual Studio 2017, you will need to make sure the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="9b357-161">远程调试器应在计算机启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="9b357-161">The remote debugger should launch automatically at machine boot time.</span></span> <span data-ttu-id="9b357-162">若要仔细检查，请使用 tlist 命令列出 PowerShell 中所有正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="9b357-162">To double check, use the tlist command to list all the running processes from PowerShell.</span></span> <span data-ttu-id="9b357-163">设备上应运行两msvsmon.exe实例。</span><span class="sxs-lookup"><span data-stu-id="9b357-163">There should be two instances of msvsmon.exe running on the device.</span></span>

* <span data-ttu-id="9b357-164">长时间处于非Visual Studio 远程调试器后，系统可能会超时。</span><span class="sxs-lookup"><span data-stu-id="9b357-164">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="9b357-165">如果Visual Studio IoT Core Windows，请尝试重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="9b357-165">If Visual Studio cannot connect to your Windows IoT Core device, try rebooting the device.</span></span>

* <span data-ttu-id="9b357-166">如果需要，还可以重命名设备。</span><span class="sxs-lookup"><span data-stu-id="9b357-166">If you want, you can also rename your device.</span></span> <span data-ttu-id="9b357-167">若要更改"计算机名"，请使用 `setcomputername` 实用工具：</span><span class="sxs-lookup"><span data-stu-id="9b357-167">To change the 'computer name', use the `setcomputername` utility:</span></span>
```
        setcomputername <new-name>
```
<span data-ttu-id="9b357-168">需要重新启动设备，更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="9b357-168">You will need to reboot the device for the change to take effect.</span></span> <span data-ttu-id="9b357-169">可以使用 命令 `shutdown` ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b357-169">You can use the `shutdown` command as follows:</span></span>
```
        shutdown /r /t 0
```
### <a name="commonly-used-utilities"></a><span data-ttu-id="9b357-170">常用实用工具</span><span class="sxs-lookup"><span data-stu-id="9b357-170">Commonly used utilities</span></span>

<span data-ttu-id="9b357-171">有关可用于 SSH 的命令和实用程序的列表，请参阅命令行 [Utils](../manage-your-device/CommandLineUtils.md) 页。</span><span class="sxs-lookup"><span data-stu-id="9b357-171">See the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page for a list of commands and utilities you can use with SSH.</span></span>
