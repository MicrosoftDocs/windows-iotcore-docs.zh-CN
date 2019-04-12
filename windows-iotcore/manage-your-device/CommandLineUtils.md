---
title: Windows 10 IoT Core 命令行实用程序
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解要连接到你的设备后用于 PowreShell 的命令行实用程序。
keywords: windows iot、 命令行、 命令行实用工具，PowerShell
ms.openlocfilehash: 2fb009115dc929540c30d5403c1877051f6b7037
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510878"
---
# <a name="windows-10-iot-core-command-line-utils"></a><span data-ttu-id="9fda2-104">Windows 10 IoT Core 命令行实用程序</span><span class="sxs-lookup"><span data-stu-id="9fda2-104">Windows 10 IoT Core Command Line Utils</span></span>

<span data-ttu-id="9fda2-105">正在寻找可用于配置设备上的某些设置的工具？</span><span class="sxs-lookup"><span data-stu-id="9fda2-105">Looking to configure some of the settings on your device?</span></span> <span data-ttu-id="9fda2-106">以下工具是可供您使用可用。</span><span class="sxs-lookup"><span data-stu-id="9fda2-106">The below tools are available at your disposal.</span></span> <span data-ttu-id="9fda2-107">在[连接到你的设备](../connect-your-device/PowerShell.md)后，使用 PowerShell 运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="9fda2-107">Use PowerShell to run these commands after [connecting to your device](../connect-your-device/PowerShell.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9fda2-108">这些工具不会预先加载-你将需要包括适当的功能 Id 以在图像中获取这些工具。</span><span class="sxs-lookup"><span data-stu-id="9fda2-108">These tools are not pre-loaded - you will need to include appropriate feature IDs to get these tools in the image.</span></span>

## <a name="iot-core-specific-command-line-utils"></a><span data-ttu-id="9fda2-109">特定于 IoT Core 的命令行实用工具</span><span class="sxs-lookup"><span data-stu-id="9fda2-109">IoT Core-specific Command Line Utils</span></span>

### **<a name="setting-startup-app"></a><span data-ttu-id="9fda2-110">设置启动应用程序：</span><span class="sxs-lookup"><span data-stu-id="9fda2-110">Setting startup app:</span></span>**
<span data-ttu-id="9fda2-111">使用启动编辑器在你的 Windows 10 IoT Core 设备上配置启动应用。</span><span class="sxs-lookup"><span data-stu-id="9fda2-111">Use the startup editor to configure startup apps on your Windows IoT Core device.</span></span> <span data-ttu-id="9fda2-112">借助以下选项之一，运行 `IotStartup`：</span><span class="sxs-lookup"><span data-stu-id="9fda2-112">Run `IotStartup` with any of the following options:</span></span>

* `IotStartup list` <span data-ttu-id="9fda2-113">列出已安装的应用程序</span><span class="sxs-lookup"><span data-stu-id="9fda2-113">lists installed applications</span></span>
* `IotStartup list headed` <span data-ttu-id="9fda2-114">列出已安装向应用程序</span><span class="sxs-lookup"><span data-stu-id="9fda2-114">lists installed headed applications</span></span>
* `IotStartup list headless` <span data-ttu-id="9fda2-115">列出已安装的无外设的应用程序</span><span class="sxs-lookup"><span data-stu-id="9fda2-115">lists installed headless applications</span></span>
* `IotStartup list [MyApp]` <span data-ttu-id="9fda2-116">列出已安装的应用程序与模式匹配</span><span class="sxs-lookup"><span data-stu-id="9fda2-116">list installed applications that match pattern</span></span> `MyApp`
* `IotStartup add` <span data-ttu-id="9fda2-117">添加主和无外设的应用程序</span><span class="sxs-lookup"><span data-stu-id="9fda2-117">adds headed and headless applications</span></span>
* `IotStartup add headed [MyApp]` <span data-ttu-id="9fda2-118">将与模式匹配的主应用程序添加`MyApp`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-118">adds headed applications that match pattern `MyApp`.</span></span>  <span data-ttu-id="9fda2-119">模式必须只匹配一个应用程序。</span><span class="sxs-lookup"><span data-stu-id="9fda2-119">Pattern must match only one application.</span></span>
* `IotStartup add headless [Task1]` <span data-ttu-id="9fda2-120">添加无外设与模式匹配的应用程序</span><span class="sxs-lookup"><span data-stu-id="9fda2-120">adds headless applications that match pattern</span></span> `Task1`
* `IotStartup remove` <span data-ttu-id="9fda2-121">删除讲述的内容和无外设的应用程序</span><span class="sxs-lookup"><span data-stu-id="9fda2-121">removes headed and headless applications</span></span>
* `IotStartup remove headed [MyApp]` <span data-ttu-id="9fda2-122">删除讲述的内容与模式匹配的应用程序</span><span class="sxs-lookup"><span data-stu-id="9fda2-122">removes headed applications that match pattern</span></span> `MyApp`
* `IotStartup remove headless [Task1]` <span data-ttu-id="9fda2-123">删除无外设与模式匹配的应用程序</span><span class="sxs-lookup"><span data-stu-id="9fda2-123">removes headless applications that match pattern</span></span> `Task1`
* `IotStartup startup` <span data-ttu-id="9fda2-124">为启动讲述的内容的列表和无外设的应用程序注册</span><span class="sxs-lookup"><span data-stu-id="9fda2-124">lists headed and headless applications registered for startup</span></span>
* `IotStartup startup [MyApp]` <span data-ttu-id="9fda2-125">讲述的内容的列表和无外设的应用程序注册为启动该匹配模式</span><span class="sxs-lookup"><span data-stu-id="9fda2-125">lists headed and headless applications registered for startup that match pattern</span></span> `MyApp`
* `IotStartup startup headed [MyApp]` <span data-ttu-id="9fda2-126">列表讲述的内容匹配的应用程序启动时注册</span><span class="sxs-lookup"><span data-stu-id="9fda2-126">lists headed applications registered for startup that match</span></span> `MyApp`
* `IotStartup startup headless [Task1]` <span data-ttu-id="9fda2-127">列出了无外设匹配的应用程序启动时注册</span><span class="sxs-lookup"><span data-stu-id="9fda2-127">lists headless applications registered for startup that match</span></span> `Task1`

    * <span data-ttu-id="9fda2-128">有关更多帮助，请尝试</span><span class="sxs-lookup"><span data-stu-id="9fda2-128">For further help, try</span></span> `IotStartup help`
    
### **<a name="change-settings-for-region-and-user-or-speech-language"></a><span data-ttu-id="9fda2-129">更改区域和用户或语音语言设置：</span><span class="sxs-lookup"><span data-stu-id="9fda2-129">Change settings for region and user or speech language:</span></span>**

<span data-ttu-id="9fda2-130">`IoTSettings`工具更改区域、 用户语言或语音语言。</span><span class="sxs-lookup"><span data-stu-id="9fda2-130">The `IoTSettings` tool changes region, user language or speech language.</span></span> <span data-ttu-id="9fda2-131">这是可以从使用 ProcessLauncher API 的应用程序调用的命令行工具。</span><span class="sxs-lookup"><span data-stu-id="9fda2-131">This is a command line tool that can be invoked from an application using the ProcessLauncher API.</span></span> <span data-ttu-id="9fda2-132">这些命令必须作为默认帐户，不是管理员身份运行。</span><span class="sxs-lookup"><span data-stu-id="9fda2-132">These commands must be run as default account, not administrator.</span></span>

* `IotSettings del account {all | username}` <span data-ttu-id="9fda2-133">删除系统上的所有 MSA 或 AAD 帐户或特定的帐户。</span><span class="sxs-lookup"><span data-stu-id="9fda2-133">deletes all MSA or AAD accounts on the system or a specific account.</span></span>  <span data-ttu-id="9fda2-134">特定帐户采用窗体 username@provider.com</span><span class="sxs-lookup"><span data-stu-id="9fda2-134">Specific accounts take the form username@provider.com</span></span>
* `IotSettings del diagnostics` <span data-ttu-id="9fda2-135">删除当前的设备在云中的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="9fda2-135">deletes diagnostic information in the cloud for the current device.</span></span>  <span data-ttu-id="9fda2-136">请注意，这将删除到调用的时间的历史记录。</span><span class="sxs-lookup"><span data-stu-id="9fda2-136">Note that this removes the history up to the time of invocation.</span></span>  <span data-ttu-id="9fda2-137">新的诊断信息仍要记入日志。</span><span class="sxs-lookup"><span data-stu-id="9fda2-137">New diagnostics information will continue to be logged.</span></span>
* `IotSettings list account` <span data-ttu-id="9fda2-138">列出所有 MSA 或 AAD 帐户登录到的设备。</span><span class="sxs-lookup"><span data-stu-id="9fda2-138">lists all MSA or AAD accounts that have been signed into the device.</span></span>
* `IotSettings list uilanguage` <span data-ttu-id="9fda2-139">列出所有的 UI 语言</span><span class="sxs-lookup"><span data-stu-id="9fda2-139">lists all UI languages</span></span>
* `IotSettings list speechlanguage` <span data-ttu-id="9fda2-140">列出所有语音语言</span><span class="sxs-lookup"><span data-stu-id="9fda2-140">lists all speech languages</span></span>
* `IotSettings get uilanguage` <span data-ttu-id="9fda2-141">显示当前 UI 语言</span><span class="sxs-lookup"><span data-stu-id="9fda2-141">displays current UI language</span></span>
* `IotSettings get speechlanguage` <span data-ttu-id="9fda2-142">显示当前语音语言</span><span class="sxs-lookup"><span data-stu-id="9fda2-142">displays current speech language</span></span>
* `IotSettings get region` <span data-ttu-id="9fda2-143">显示当前的区域</span><span class="sxs-lookup"><span data-stu-id="9fda2-143">displays current region</span></span>
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)` <span data-ttu-id="9fda2-144">设置默认 UI 语言加拿大法语）</span><span class="sxs-lookup"><span data-stu-id="9fda2-144">sets default UI language French Canadian)</span></span>
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` <span data-ttu-id="9fda2-145">设置语音语言加拿大法语）</span><span class="sxs-lookup"><span data-stu-id="9fda2-145">sets speech language French Canadian)</span></span>
* `IotSettings set region region\_code - (e.g. CA)` <span data-ttu-id="9fda2-146">将默认区域设置为加拿大）</span><span class="sxs-lookup"><span data-stu-id="9fda2-146">sets default region to Canada)</span></span>
* `IotSettings set bluetoothpref {sink | source}` <span data-ttu-id="9fda2-147">指定蓝牙角色首选项时使用 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 功能生成的设备连接到另一台设备同时支持这两个角色选择。</span><span class="sxs-lookup"><span data-stu-id="9fda2-147">Specifies the Bluetooth role preference to select when devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK features connect to another device that also supports both roles.</span></span>
* `IotSettings get bluetoothpref` <span data-ttu-id="9fda2-148">返回使用 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 构建的设备的当前蓝牙角色首选项。</span><span class="sxs-lookup"><span data-stu-id="9fda2-148">returns the current Bluetooth role preference for devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK.</span></span>  <span data-ttu-id="9fda2-149">默认值为源。</span><span class="sxs-lookup"><span data-stu-id="9fda2-149">The default is source.</span></span>

> [!TIP]
> `IoTSettings -list uiLanguage` <span data-ttu-id="9fda2-150">将为返回受支持的 UI 语言的列表 （在 Windows IoT core 映像已针对执行的版本）</span><span class="sxs-lookup"><span data-stu-id="9fda2-150">will give back the list of supported UI language (in the version of Windows IoT core image it has been executed against)</span></span>
    
### **<a name="change-default-audio-device-and-volume"></a><span data-ttu-id="9fda2-151">更改默认音频设备和卷：</span><span class="sxs-lookup"><span data-stu-id="9fda2-151">Change default audio device and volume:</span></span>**

<span data-ttu-id="9fda2-152">`IoTCoreAudioControlTool`工具控制音频相关的选项，如设置捕获和播放设备的默认值和更改音量。</span><span class="sxs-lookup"><span data-stu-id="9fda2-152">The `IoTCoreAudioControlTool` tool controls audio related options, such as setting default capture and playback devices and changing the volume.</span></span> <span data-ttu-id="9fda2-153">有关参数的完整列表，运行`IoTCoreAudioControlTool h`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-153">For a full list of parameters, run `IoTCoreAudioControlTool h`.</span></span>

### **<a name="manually-installing-appx-files"></a><span data-ttu-id="9fda2-154">手动安装。APPX 文件：</span><span class="sxs-lookup"><span data-stu-id="9fda2-154">Manually installing .APPX files:</span></span>**
<span data-ttu-id="9fda2-155">DeployAppx 使安装和删除。在开发方案的 APPX 包。</span><span class="sxs-lookup"><span data-stu-id="9fda2-155">DeployAppx enables installing, and removing in .APPX packages in development scenarios.</span></span>  <span data-ttu-id="9fda2-156">安装的正确方法。在生产映像中的 APPX 包是使用预配包，如中所述[安装您的应用程序](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd)主题。</span><span class="sxs-lookup"><span data-stu-id="9fda2-156">The correct method for installing .APPX packages in production images is to use a provisioning package as documented in the [Install your app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) subject.</span></span>  <span data-ttu-id="9fda2-157">DeployAppx 还支持查询。APPX 包信息。</span><span class="sxs-lookup"><span data-stu-id="9fda2-157">DeployAppx also supports querying .APPX package information.</span></span>

*  `DeployAppx install MyApp.appx` <span data-ttu-id="9fda2-158">安装。APPX 和具有相同名称的证书如果找到。</span><span class="sxs-lookup"><span data-stu-id="9fda2-158">installs the .APPX and the certificate of the same name if found.</span></span>
* `DeployAppx install force MyApp.appx` <span data-ttu-id="9fda2-159">强制卸载当前安装。如果名称与同一个包的 APPX 安装新之前找到。APPX。</span><span class="sxs-lookup"><span data-stu-id="9fda2-159">forces uninstalling the currently installed .APPX with the same package name if found before installing the new .APPX.</span></span>  <span data-ttu-id="9fda2-160">这可用于安装。作为当前安装的相同或更低版本号的 APPX。APPX。</span><span class="sxs-lookup"><span data-stu-id="9fda2-160">This is useful for installing an .APPX with the same or lower version number as the currently installed .APPX.</span></span>
* `DeployAppx install retry MyApp.appx` <span data-ttu-id="9fda2-161">重试安装。在失败时使用 2 个第二个 APPX 10 次尝试的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="9fda2-161">retry installing the .APPX 10 times on failure with 2 second delay between attempts.</span></span>
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123` <span data-ttu-id="9fda2-162">卸载.appx 具有匹配的包完整名称。</span><span class="sxs-lookup"><span data-stu-id="9fda2-162">uninstall the .appx with the matching package full name.</span></span>
*  `DeployAppx uninstall MyApp.appx` <span data-ttu-id="9fda2-163">卸载任何已安装。具有匹配的包系列名称的 APPX。</span><span class="sxs-lookup"><span data-stu-id="9fda2-163">uninstall any installed .APPX with a matching package family name.</span></span>
* `DeployAppx getpackages` <span data-ttu-id="9fda2-164">列出已安装的包完整名称。</span><span class="sxs-lookup"><span data-stu-id="9fda2-164">lists installed package full names.</span></span>
* `DeployAppx getpackageid IotCoreDefaultApp.appx` <span data-ttu-id="9fda2-165">打印出包名称、 包系列名称和包的完整名称。APPX。</span><span class="sxs-lookup"><span data-stu-id="9fda2-165">prints out the package name, the package family name, and the package full name for the .APPX.</span></span>
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml` <span data-ttu-id="9fda2-166">不受支持</span><span class="sxs-lookup"><span data-stu-id="9fda2-166">unsupported</span></span>


## <a name="general-command-line-utils"></a><span data-ttu-id="9fda2-167">常规命令行实用工具</span><span class="sxs-lookup"><span data-stu-id="9fda2-167">General Command Line Utils</span></span>

### **<a name="update-account-password"></a><span data-ttu-id="9fda2-168">更新帐户密码：</span><span class="sxs-lookup"><span data-stu-id="9fda2-168">Update account password:</span></span>**

<span data-ttu-id="9fda2-169">强烈建议你更新默认的管理员帐户密码。</span><span class="sxs-lookup"><span data-stu-id="9fda2-169">It is highly recommended that you update the default password for the Administrator account.</span></span> <span data-ttu-id="9fda2-170">若要更新帐户密码，你可以发出以下命令：`net user Administrator [new password]`（其中 `[new password]` 表示你选择的强密码）。</span><span class="sxs-lookup"><span data-stu-id="9fda2-170">To do this, you can issue the following command: `net user Administrator [new password]` where `[new password]` represents a strong password of your choice.</span></span>

### **<a name="create-local-user-accounts"></a><span data-ttu-id="9fda2-171">创建本地用户帐户：</span><span class="sxs-lookup"><span data-stu-id="9fda2-171">Create local user accounts:</span></span>**

<span data-ttu-id="9fda2-172">如果你想要授予其他人访问你的 Windows IoT Core 设备的权限，你可以通过在 `net user [username] [password] /add` 中键入，并使用 PS 创建其他本地用户帐户。</span><span class="sxs-lookup"><span data-stu-id="9fda2-172">If you wish to give others access to your Windows IoT Core device, you can create additional local user accounts using PS by typing in `net user [username] [password] /add`.</span></span> <span data-ttu-id="9fda2-173">如果你想要将此用户添加到其他组（例如管理员组），则使用 `net localgroup Administrators [username] /add`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-173">If you wish to add this user to other groups, such as the Administrator group, use `net localgroup Administrators [username] /add`.</span></span>

### **<a name="set-password"></a><span data-ttu-id="9fda2-174">设置密码：</span><span class="sxs-lookup"><span data-stu-id="9fda2-174">Set password:</span></span>**

<span data-ttu-id="9fda2-175">若要更改你的设备上的帐户密码，可通过运行 `net user [account-username] [new-password]` 来更改帐户密码。</span><span class="sxs-lookup"><span data-stu-id="9fda2-175">To change the password on an account on your device, run `net user [account-username] [new-password]` to change the account password.</span></span>

### **<a name="query-and-set-device-name"></a><span data-ttu-id="9fda2-176">查询和设置设备名称：</span><span class="sxs-lookup"><span data-stu-id="9fda2-176">Query and set device name:</span></span>**

<span data-ttu-id="9fda2-177">若要确定当前设备名称，只需键入 `hostname`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-177">To identify your current device name, simply type `hostname`.</span></span> <span data-ttu-id="9fda2-178">若要更改你的 Windows IoT Core 设备的名称，应键入 `SetComputerName [new machinename]`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-178">To change the name of your Windows IoT Core device, type `SetComputerName [new machinename]`.</span></span> <span data-ttu-id="9fda2-179">你可能需要重新启动你的设备才能使更改的名称生效。</span><span class="sxs-lookup"><span data-stu-id="9fda2-179">You may need to restart your device for the name change to take effect.</span></span>

### **<a name="basic-network-configuration"></a><span data-ttu-id="9fda2-180">基本网络配置：</span><span class="sxs-lookup"><span data-stu-id="9fda2-180">Basic network configuration:</span></span>**

<span data-ttu-id="9fda2-181">许多您可能已经熟悉的基本网络配置实用工具都可以在 Windows IoT Core 中，其中包括命令，例如`ping.exe`， `netstat.exe`， `netsh.exe`， `ipconfig.exe`， `tracert.exe`，并`arp.exe`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-181">Many of the basic network configuration utilities you may already be familiar with are available in Windows IoT Core, including commands such as `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, and `arp.exe`.</span></span>

### **<a name="copy-utilities"></a><span data-ttu-id="9fda2-182">将复制实用程序：</span><span class="sxs-lookup"><span data-stu-id="9fda2-182">Copy utilities:</span></span>**

<span data-ttu-id="9fda2-183">Microsoft 将提供熟悉的工具，包括 `sfpcopy.exe` 以及 `xcopy.exe`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-183">Microsoft is providing familiar tools, including `sfpcopy.exe` as well as `xcopy.exe`.</span></span>

### **<a name="process-management"></a><span data-ttu-id="9fda2-184">进程管理：</span><span class="sxs-lookup"><span data-stu-id="9fda2-184">Process Management:</span></span>**

<span data-ttu-id="9fda2-185">若要查看当前正在运行的进程，可以尝试 `get-process` 或 `tlist.exe`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-185">To view currently running processes, you can try either `get-process` or alternatively `tlist.exe`.</span></span> <span data-ttu-id="9fda2-186">若要停止正在运行的进程，请键入 `kill.exe [pid or process name]`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-186">To stop a running process, type `kill.exe [pid or process name]`.</span></span>


### **<a name="set-boot-option-headless-vs-headed-boot"></a><span data-ttu-id="9fda2-187">设置启动选项 （无外设与主启动）：</span><span class="sxs-lookup"><span data-stu-id="9fda2-187">Set Boot Option (Headless vs. headed boot):</span></span>**

<span data-ttu-id="9fda2-188">Windows IoT Core 设备可以设置为有外设设备模式（需要显示功能时）或无外设设备模式（显示功能不是必需项或不可用时）。</span><span class="sxs-lookup"><span data-stu-id="9fda2-188">Windows IoT Core devices can be set to headed (when display capabilities are required) or headless (when a display is not required or available) device mode.</span></span> <span data-ttu-id="9fda2-189">若要更改此设置，请使用 `setbootoption.exe [headed | headless]`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-189">To change this setting, use `setbootoption.exe [headed | headless]`.</span></span>

> [!NOTE]
> <span data-ttu-id="9fda2-190">更改此设置将需要重新启动顺序的更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="9fda2-190">Changing this setting will require a reboot in order for the change to take effect.</span></span>

### **<a name="task-scheduler"></a><span data-ttu-id="9fda2-191">任务计划程序：</span><span class="sxs-lookup"><span data-stu-id="9fda2-191">Task scheduler:</span></span>**

<span data-ttu-id="9fda2-192">若要查看计划任务的当前列表，请使用 `schtasks.exe` 命令。</span><span class="sxs-lookup"><span data-stu-id="9fda2-192">To view the current list of scheduled tasks, use the `schtasks.exe` command.</span></span> <span data-ttu-id="9fda2-193">你可以使用 `/create` 开关创建新任务，或使用 `/run` 开关运行按需任务。</span><span class="sxs-lookup"><span data-stu-id="9fda2-193">You can create new tasks with the `/create` switch or run on-demand tasks with the `/run` switch.</span></span> <span data-ttu-id="9fda2-194">对于受支持的参数的完整列表，请使用</span><span class="sxs-lookup"><span data-stu-id="9fda2-194">For a full list of supported parameters, use</span></span> `schtasks.exe /?`

### **<a name="device-drivers"></a><span data-ttu-id="9fda2-195">设备驱动程序：</span><span class="sxs-lookup"><span data-stu-id="9fda2-195">Device drivers:</span></span>**

<span data-ttu-id="9fda2-196">设备控制台实用程序在识别和管理已安装的设备和驱动程序方面十分有用。</span><span class="sxs-lookup"><span data-stu-id="9fda2-196">The device console utility is useful in identifying and managing installed devices and drivers.</span></span> <span data-ttu-id="9fda2-197">对于参数的完整列表，请使用</span><span class="sxs-lookup"><span data-stu-id="9fda2-197">For a full list of parameters, use</span></span> `devcon.exe /?`

### **<a name="registry-access"></a><span data-ttu-id="9fda2-198">注册表访问权限：</span><span class="sxs-lookup"><span data-stu-id="9fda2-198">Registry Access:</span></span>**

<span data-ttu-id="9fda2-199">如果你需要通过访问注册表来查看或修改设置，请使用 `reg.exe /?` 命令获取有关支持的参数的完整列表。</span><span class="sxs-lookup"><span data-stu-id="9fda2-199">If you need to access the registry to view or modify settings, use the `reg.exe /?` Command for the full list of supported parameters.</span></span>

### **<a name="services"></a><span data-ttu-id="9fda2-200">服务：</span><span class="sxs-lookup"><span data-stu-id="9fda2-200">Services:</span></span>**

<span data-ttu-id="9fda2-201">管理 Windows 服务可以通过 `net.exe` 命令来完成。</span><span class="sxs-lookup"><span data-stu-id="9fda2-201">Managing Windows services can be accomplished via the `net.exe` command.</span></span> <span data-ttu-id="9fda2-202">若要查看运行中的服务的列表，请键入 `net start`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-202">To see a list of running services, type `net start`.</span></span> <span data-ttu-id="9fda2-203">若要启动或停止特定的服务，请键入 `net [start | stop] [service name]`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-203">To start or stop a specific service, type `net [start | stop] [service name]`.</span></span> <span data-ttu-id="9fda2-204">此外，还可以通过 `sc.exe` 命令使用服务控制管理器。</span><span class="sxs-lookup"><span data-stu-id="9fda2-204">Alternatively, you can also use the service control manager via `sc.exe` command.</span></span>

### **<a name="boot-configuration"></a><span data-ttu-id="9fda2-205">启动配置：</span><span class="sxs-lookup"><span data-stu-id="9fda2-205">Boot configuration:</span></span>**

<span data-ttu-id="9fda2-206">可以在 Windows IoT Core 设备的启动配置进行更改，通过使用`bcdedit.exe`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-206">You can make changes to the boot configuration of your Windows IoT Core device by using `bcdedit.exe`.</span></span> <span data-ttu-id="9fda2-207">例如，可启用 testsigning 与`bcdedit –set testsigning on`命令。</span><span class="sxs-lookup"><span data-stu-id="9fda2-207">For instance, you can enable testsigning with `bcdedit –set testsigning on` command.</span></span>

### **<a name="shutdownrestart-device"></a><span data-ttu-id="9fda2-208">关闭/重新启动设备：</span><span class="sxs-lookup"><span data-stu-id="9fda2-208">Shutdown/restart device:</span></span>**

<span data-ttu-id="9fda2-209">若要关闭设备，请键入 `shutdown /s /t 0`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-209">To shut down your device, type `shutdown /s /t 0`.</span></span> <span data-ttu-id="9fda2-210">若要重新启动设备，请使用`/r`改为开关与命令`shutdown /r /t 0`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-210">To restart the device, use the `/r` switch instead with the command `shutdown /r /t 0`.</span></span>

### **<a name="viewing-and-changing-display-settings"></a><span data-ttu-id="9fda2-211">查看和更改显示设置</span><span class="sxs-lookup"><span data-stu-id="9fda2-211">Viewing and changing display settings</span></span>**
<span data-ttu-id="9fda2-212">可能使用 SetDisplayResolution 工具，用于列出当前的显示设置和显示的支持的值的列表。</span><span class="sxs-lookup"><span data-stu-id="9fda2-212">The SetDisplayResolution tool may be used for listing the current display settings and to show the list of supported values.</span></span>  <span data-ttu-id="9fda2-213">它可以进一步使用调整显示器的分辨率、 刷新频率和/或为你的平台支持的值的方向。</span><span class="sxs-lookup"><span data-stu-id="9fda2-213">It can further be used for adjusting the display's resolution, refresh rate and/or orientation to values supported by your platform.</span></span>  <span data-ttu-id="9fda2-214">该实用程序接受以下的命令行参数：</span><span class="sxs-lookup"><span data-stu-id="9fda2-214">The utility accepts the following command line arguments:</span></span>

* `SetDisplayResolution` <span data-ttu-id="9fda2-215">列出了当前显示 resoltuion。</span><span class="sxs-lookup"><span data-stu-id="9fda2-215">Lists the current display resoltuion.</span></span>
* `SetDisplayResolution -list` <span data-ttu-id="9fda2-216">列出支持的显示分辨率。</span><span class="sxs-lookup"><span data-stu-id="9fda2-216">Lists supported display resolutions.</span></span>
* `SetDisplayResolution -orientation:[n]` <span data-ttu-id="9fda2-217">更改显示方向，其中 n = 0、 90、 180 或 270。</span><span class="sxs-lookup"><span data-stu-id="9fda2-217">Change the display orientation, where n=0,90,180 or 270.</span></span>
* `SetDisplayResolution [width] [height]` <span data-ttu-id="9fda2-218">更改宽度和高度 （像素）</span><span class="sxs-lookup"><span data-stu-id="9fda2-218">Change the width and height in pixels</span></span> 
* `SetDisplayResolution [width] [height] [refreshrate]` <span data-ttu-id="9fda2-219">更改宽度、 高度和刷新率的宽度和高度位于像素和 refreshrate hz</span><span class="sxs-lookup"><span data-stu-id="9fda2-219">Change width, height and refresh rate where width and height are in pixels and refreshrate in Hz</span></span> 
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]` <span data-ttu-id="9fda2-220">更改宽度、 高度、 refreshrate 和屏幕方向的宽度和高度均以像素为单位，在 Hz refreshrate 和方向是 0、 90、 180 或 270 之一。</span><span class="sxs-lookup"><span data-stu-id="9fda2-220">Change width, height, refreshrate and screen orientation where width and height are in pixels, refreshrate in Hz and orientation is one of 0, 90, 180 or 270.</span></span>

### **<a name="take-screenshot"></a><span data-ttu-id="9fda2-221">拍摄的屏幕快照：</span><span class="sxs-lookup"><span data-stu-id="9fda2-221">Take screenshot:</span></span>**

<span data-ttu-id="9fda2-222">使用可用来拍摄 Windows IoTCore 设备的屏幕截图`ScreenCapture.exe`。</span><span class="sxs-lookup"><span data-stu-id="9fda2-222">You can take the screenshot of your Windows IoTCore device by using `ScreenCapture.exe`.</span></span> <span data-ttu-id="9fda2-223">例如，运行`ScreenCapture c:\folder\screencap.jpg`将屏幕截图并将其保存在 screencap.jpg 文件中。</span><span class="sxs-lookup"><span data-stu-id="9fda2-223">For example, run `ScreenCapture c:\folder\screencap.jpg` will take the screenshot and save it in screencap.jpg file.</span></span>

### **<a name="get-information-about-network-adapters"></a><span data-ttu-id="9fda2-224">获取有关网络适配器的信息：</span><span class="sxs-lookup"><span data-stu-id="9fda2-224">Get information about Network Adapters:</span></span>**

<span data-ttu-id="9fda2-225">若要查看所有可用的网络适配器的列表，请运行`GetAdapterInfo`工具。</span><span class="sxs-lookup"><span data-stu-id="9fda2-225">To view the list of all the available network adapters, run `GetAdapterInfo` tool.</span></span>

### **<a name="set-folder-permissions-for-uwp-apps"></a><span data-ttu-id="9fda2-226">设置适用于 UWP 应用的文件夹权限：</span><span class="sxs-lookup"><span data-stu-id="9fda2-226">Set folder permissions for UWP apps:</span></span>**

<span data-ttu-id="9fda2-227">在设备上的不是所有文件夹都是通过通用 Windows 应用的访问。</span><span class="sxs-lookup"><span data-stu-id="9fda2-227">Not all folders on your device are accesible by Universal Windows Apps.</span></span> <span data-ttu-id="9fda2-228">若要对 UWP 应用进行文件夹访问，可以使用`FolderPermissions`工具。</span><span class="sxs-lookup"><span data-stu-id="9fda2-228">To make a folder accesible to a UWP app, you can use `FolderPermissions` tool.</span></span> <span data-ttu-id="9fda2-229">例如运行`FolderPermissions c:\test -e`要提供 UWP 应用访问权限`c:\test`文件夹。</span><span class="sxs-lookup"><span data-stu-id="9fda2-229">For example run `FolderPermissions c:\test -e` to give UWP apps access to `c:\test` folder.</span></span> <span data-ttu-id="9fda2-230">请注意这会仅使用本机 Win32 api，可用于例如。</span><span class="sxs-lookup"><span data-stu-id="9fda2-230">Note this will work only with native Win32 apis for eg.</span></span> <span data-ttu-id="9fda2-231">CreateFile2 而不能使用 WinRT api，如 StorageFolder，StorageFile 等。</span><span class="sxs-lookup"><span data-stu-id="9fda2-231">CreateFile2 and not with WinRT apis like StorageFolder, StorageFile etc.</span></span>

### **<a name="work-with-serial-ports"></a><span data-ttu-id="9fda2-232">使用串行端口：</span><span class="sxs-lookup"><span data-stu-id="9fda2-232">Work with Serial Ports:</span></span>**
<span data-ttu-id="9fda2-233">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm)使您可以使用命令行中的串行端口。</span><span class="sxs-lookup"><span data-stu-id="9fda2-233">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) allows you to work with serial ports from the command line.</span></span> <span data-ttu-id="9fda2-234">它作为 ms iot 示例存储库中的示例项目提供。</span><span class="sxs-lookup"><span data-stu-id="9fda2-234">It is provided as a sample project in the ms-iot samples repo.</span></span> 

``` 
Usage: MinComm.exe [-list] device_path [baud=<B>] [parity=<P>] [data=<D>] [stop=<S>] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]

  -list                List all available serial ports on the system and exit.
  device_path          Device path or COM port to open (e.g. COM1)
  baud=<B>             Specifies the transmission rate in bits per second.
  parity={n|e|o|m|s}   Specifies how the system uses the parity bit to check
                       for transmission errors. The abbreviations stand for
                       none, even, odd, mark, and space.
  data={5|6|7|8}       Specifies the number of data bits in a character.
  stop={1|1.5|2}       Specifies the number of stop bits that define the end of
                       a character.
  xon={on|off}         Specifies whether the xon or xoff protocol for data-flow
                       control is on or off.
  odsr={on|off}        Specifies whether output handshaking that uses the
                       Data Set Ready (DSR) circuit is on or off.
  octs={on|off}        Specifies whether output handshaking that uses the
                       Clear To Send (CTS) circuit is on or off.
  dtr={on|off|hs}      Specifies whether the Data Terminal Ready (DTR) circuit
                       is on or off or set to handshake.
  rts={on|off|hs|tg}   Specifies whether the Request To Send (RTS) circuit is
                       set to on, off, handshake, or toggle.
  idsr={on|off}        Specifies whether the DSR circuit sensitivity is on
                       or off.

Parameters that are not specified will default to the port's current
configuration. For more information on the connection parameters, see the
Technet documentation for the Mode command:
  https://technet.microsoft.com/library/cc732236.aspx

Examples:
  Connect to the first serial port found in the port's current configuration:
    MinComm.exe

  List all serial ports on the system:
    MinComm.exe -list

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe COM1 baud=115200 parity=n data=8 stop=1

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe \\.\COM1 baud=115200 parity=n data=8 stop=1

  Open device interface in 115200 8N1 configuration:
    MinComm.exe \\?\USB#VID_FFFF&PID_0005#{86e0d1e0-8089-11d0-9ce4-08003e301f73} baud=115200 parity=n data=8 stop=1```


