---
title: Windows 10 IoT Core 命令行实用程序
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解连接到设备后用于 PowerShell 的命令行实用程序。
keywords: windows iot，命令行，命令行实用工具，PowerShell
ms.openlocfilehash: ff92b0be7c9613cd7adb52d6e4a9a0f4b4716903
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782919"
---
# <a name="windows-10-iot-core-command-line-utils"></a><span data-ttu-id="dcdf1-104">Windows 10 IoT Core 命令行 Utils</span><span class="sxs-lookup"><span data-stu-id="dcdf1-104">Windows 10 IoT Core Command Line Utils</span></span>

<span data-ttu-id="dcdf1-105">想要在设备上配置某些设置？</span><span class="sxs-lookup"><span data-stu-id="dcdf1-105">Looking to configure some of the settings on your device?</span></span> <span data-ttu-id="dcdf1-106">以下工具可供你使用。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-106">The below tools are available at your disposal.</span></span> <span data-ttu-id="dcdf1-107">在 [连接到你的设备](../connect-your-device/PowerShell.md)后，使用 PowerShell 来运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-107">Use PowerShell to run these commands after [connecting to your device](../connect-your-device/PowerShell.md).</span></span>

> [!NOTE]
> <span data-ttu-id="dcdf1-108">这些工具未预先加载-需要包含相应的功能 Id 才能在映像中获取这些工具。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-108">These tools are not pre-loaded - you will need to include appropriate feature IDs to get these tools in the image.</span></span>

## <a name="iot-core-specific-command-line-utils"></a><span data-ttu-id="dcdf1-109">IoT Core 特定的命令行 Utils</span><span class="sxs-lookup"><span data-stu-id="dcdf1-109">IoT Core-specific Command Line Utils</span></span>

### <a name="setting-startup-app"></a><span data-ttu-id="dcdf1-110">**设置启动应用程序：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-110">**Setting startup app:**</span></span>
<span data-ttu-id="dcdf1-111">使用启动编辑器在 Windows IoT Core 设备上配置启动应用。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-111">Use the startup editor to configure startup apps on your Windows IoT Core device.</span></span> <span data-ttu-id="dcdf1-112">`IotStartup`用以下任一选项运行：</span><span class="sxs-lookup"><span data-stu-id="dcdf1-112">Run `IotStartup` with any of the following options:</span></span>

* <span data-ttu-id="dcdf1-113">`IotStartup list` 列出已安装的应用程序</span><span class="sxs-lookup"><span data-stu-id="dcdf1-113">`IotStartup list` lists installed applications</span></span>
* <span data-ttu-id="dcdf1-114">`IotStartup list headed` 列出已安装的应用程序</span><span class="sxs-lookup"><span data-stu-id="dcdf1-114">`IotStartup list headed` lists installed headed applications</span></span>
* <span data-ttu-id="dcdf1-115">`IotStartup list headless` 列出安装的无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="dcdf1-115">`IotStartup list headless` lists installed headless applications</span></span>
* <span data-ttu-id="dcdf1-116">`IotStartup list [MyApp]` 列出与模式匹配的已安装应用程序 `MyApp`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-116">`IotStartup list [MyApp]` list installed applications that match pattern `MyApp`</span></span>
* <span data-ttu-id="dcdf1-117">`IotStartup add` 添加头和无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="dcdf1-117">`IotStartup add` adds headed and headless applications</span></span>
* <span data-ttu-id="dcdf1-118">`IotStartup add headed [MyApp]` 添加匹配模式的应用程序 `MyApp` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-118">`IotStartup add headed [MyApp]` adds headed applications that match pattern `MyApp`.</span></span>  <span data-ttu-id="dcdf1-119">模式只能与一个应用程序匹配。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-119">Pattern must match only one application.</span></span>
* <span data-ttu-id="dcdf1-120">`IotStartup add headless [Task1]` 添加匹配模式的无外设应用程序 `Task1`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-120">`IotStartup add headless [Task1]` adds headless applications that match pattern `Task1`</span></span>
* <span data-ttu-id="dcdf1-121">`IotStartup remove` 删除头和无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="dcdf1-121">`IotStartup remove` removes headed and headless applications</span></span>
* <span data-ttu-id="dcdf1-122">`IotStartup remove headed [MyApp]` 删除匹配模式的头应用程序 `MyApp`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-122">`IotStartup remove headed [MyApp]` removes headed applications that match pattern `MyApp`</span></span>
* <span data-ttu-id="dcdf1-123">`IotStartup remove headless [Task1]` 删除与模式匹配的无外设应用程序 `Task1`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-123">`IotStartup remove headless [Task1]` removes headless applications that match pattern `Task1`</span></span>
* <span data-ttu-id="dcdf1-124">`IotStartup startup` 列出注册为启动的头和无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="dcdf1-124">`IotStartup startup` lists headed and headless applications registered for startup</span></span>
* <span data-ttu-id="dcdf1-125">`IotStartup startup [MyApp]` 列出注册为与模式匹配的启动的头和无外设应用程序 `MyApp`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-125">`IotStartup startup [MyApp]` lists headed and headless applications registered for startup that match pattern `MyApp`</span></span>
* <span data-ttu-id="dcdf1-126">`IotStartup startup headed [MyApp]` 列出注册为启动的应用程序匹配的应用程序 `MyApp`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-126">`IotStartup startup headed [MyApp]` lists headed applications registered for startup that match `MyApp`</span></span>
* <span data-ttu-id="dcdf1-127">`IotStartup startup headless [Task1]` 列出注册为启动的无外设应用程序匹配 `Task1`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-127">`IotStartup startup headless [Task1]` lists headless applications registered for startup that match `Task1`</span></span>
* <span data-ttu-id="dcdf1-128">`IotStartup run [MyApp]` 启动应用标识 `MyApp`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-128">`IotStartup run [MyApp]` start app identified by `MyApp`</span></span>
* <span data-ttu-id="dcdf1-129">`IotStartup stop [MyApp]` 停止应用标识 `MyApp`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-129">`IotStartup stop [MyApp]` stop app identified by `MyApp`</span></span>
* <span data-ttu-id="dcdf1-130">如需进一步的帮助，请尝试 `IotStartup help`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-130">For further help, try `IotStartup help`</span></span>

### <a name="change-settings-for-region-and-user-or-speech-language"></a><span data-ttu-id="dcdf1-131">**更改区域和用户或语音语言的设置：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-131">**Change settings for region and user or speech language:**</span></span>

<span data-ttu-id="dcdf1-132">该 `IoTSettings` 工具更改了区域、用户语言或语音语言。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-132">The `IoTSettings` tool changes region, user language, or speech language.</span></span> <span data-ttu-id="dcdf1-133">这是一个命令行工具，可使用 ProcessLauncher API 从应用程序中调用。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-133">This is a command line tool that can be invoked from an application using the ProcessLauncher API.</span></span> <span data-ttu-id="dcdf1-134">这些命令必须作为默认帐户运行，而不是以管理员身份运行。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-134">These commands must be run as default account, not administrator.</span></span>

* <span data-ttu-id="dcdf1-135">`IotSettings del account {all | username}` 删除系统上的所有 MSA 或 Azure AD 帐户或特定的帐户。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-135">`IotSettings del account {all | username}` deletes all MSA or Azure AD accounts on the system or a specific account.</span></span>  <span data-ttu-id="dcdf1-136">特定帐户采用窗体 username@provider.com</span><span class="sxs-lookup"><span data-stu-id="dcdf1-136">Specific accounts take the form username@provider.com</span></span>
* <span data-ttu-id="dcdf1-137">`IotSettings del diagnostics` 为当前设备删除云中的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-137">`IotSettings del diagnostics` deletes diagnostic information in the cloud for the current device.</span></span>  <span data-ttu-id="dcdf1-138">请注意，这会删除与调用时相同的历史记录。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-138">Note that this removes the history up to the time of invocation.</span></span>  <span data-ttu-id="dcdf1-139">将继续记录新的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-139">New diagnostics information will continue to be logged.</span></span>
* <span data-ttu-id="dcdf1-140">`IotSettings list account` 列出已登录到设备的所有 MSA 或 Azure AD 帐户。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-140">`IotSettings list account` lists all MSA or Azure AD accounts that have been signed into the device.</span></span>
* <span data-ttu-id="dcdf1-141">`IotSettings list uilanguage` 列出所有 UI 语言</span><span class="sxs-lookup"><span data-stu-id="dcdf1-141">`IotSettings list uilanguage` lists all UI languages</span></span>
* <span data-ttu-id="dcdf1-142">`IotSettings list speechlanguage` 列出所有语音语言</span><span class="sxs-lookup"><span data-stu-id="dcdf1-142">`IotSettings list speechlanguage` lists all speech languages</span></span>
* <span data-ttu-id="dcdf1-143">`IotSettings get uilanguage` 显示当前 UI 语言</span><span class="sxs-lookup"><span data-stu-id="dcdf1-143">`IotSettings get uilanguage` displays current UI language</span></span>
* <span data-ttu-id="dcdf1-144">`IotSettings get speechlanguage` 显示当前语音语言</span><span class="sxs-lookup"><span data-stu-id="dcdf1-144">`IotSettings get speechlanguage` displays current speech language</span></span>
* <span data-ttu-id="dcdf1-145">`IotSettings get region` 显示当前区域</span><span class="sxs-lookup"><span data-stu-id="dcdf1-145">`IotSettings get region` displays current region</span></span>
* <span data-ttu-id="dcdf1-146">`IotSettings set uilanguage language\_tag - (e.g. fr-CA)` 设置默认的 UI 语言加拿大法语) </span><span class="sxs-lookup"><span data-stu-id="dcdf1-146">`IotSettings set uilanguage language\_tag - (e.g. fr-CA)` sets default UI language French Canadian)</span></span>
* <span data-ttu-id="dcdf1-147">`IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` 设置语音语言法语（加拿大）) </span><span class="sxs-lookup"><span data-stu-id="dcdf1-147">`IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` sets speech language French Canadian)</span></span>
* <span data-ttu-id="dcdf1-148">`IotSettings set region region\_code - (e.g. CA)` 将默认区域设置为加拿大) </span><span class="sxs-lookup"><span data-stu-id="dcdf1-148">`IotSettings set region region\_code - (e.g. CA)` sets default region to Canada)</span></span>
* <span data-ttu-id="dcdf1-149">`IotSettings set bluetoothpref {sink | source}` 指定在采用 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 功能构建的设备连接到同时支持这两种角色的另一台设备时要选择的蓝牙角色首选项。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-149">`IotSettings set bluetoothpref {sink | source}` Specifies the Bluetooth role preference to select when devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK features connect to another device that also supports both roles.</span></span>
* <span data-ttu-id="dcdf1-150">`IotSettings get bluetoothpref` 返回 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 生成的设备的当前蓝牙角色首选项。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-150">`IotSettings get bluetoothpref` returns the current Bluetooth role preference for devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK.</span></span>  <span data-ttu-id="dcdf1-151">默认值为 source。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-151">The default is source.</span></span>

> [!TIP]
> <span data-ttu-id="dcdf1-152">`IoTSettings -list uiLanguage` 会在对其执行的 Windows IoT core 映像的版本中，为 (提供支持的 UI 语言的列表) </span><span class="sxs-lookup"><span data-stu-id="dcdf1-152">`IoTSettings -list uiLanguage` will give back the list of supported UI language (in the version of Windows IoT core image it has been executed against)</span></span>
    
### <a name="change-default-audio-device-and-volume"></a><span data-ttu-id="dcdf1-153">**更改默认音频设备和卷：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-153">**Change default audio device and volume:**</span></span>

<span data-ttu-id="dcdf1-154">该 `IoTCoreAudioControlTool` 工具控制音频相关的选项，如设置默认捕获和播放设备以及更改卷。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-154">The `IoTCoreAudioControlTool` tool controls audio related options, such as setting default capture and playback devices and changing the volume.</span></span> <span data-ttu-id="dcdf1-155">有关参数的完整列表，请运行 `IoTCoreAudioControlTool h` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-155">For a full list of parameters, run `IoTCoreAudioControlTool h`.</span></span>

### <a name="manually-installing-appx-files"></a><span data-ttu-id="dcdf1-156">**手动安装。APPX 文件：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-156">**Manually installing .APPX files:**</span></span>
<span data-ttu-id="dcdf1-157">DeployAppx 支持在中安装和删除。开发方案中的 APPX 包。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-157">DeployAppx enables installing, and removing in .APPX packages in development scenarios.</span></span>  <span data-ttu-id="dcdf1-158">用于安装的正确方法。生产映像中的 APPX 包是使用 [安装应用程序](https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) 主题中所述的预配包。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-158">The correct method for installing .APPX packages in production images is to use a provisioning package as documented in the [Install your app](https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) subject.</span></span>  <span data-ttu-id="dcdf1-159">DeployAppx 还支持查询。APPX 包信息。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-159">DeployAppx also supports querying .APPX package information.</span></span>

*  <span data-ttu-id="dcdf1-160">`DeployAppx install MyApp.appx` 安装。如果找到，则为 APPX 和同名证书。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-160">`DeployAppx install MyApp.appx` installs the .APPX and the certificate of the same name if found.</span></span>
* <span data-ttu-id="dcdf1-161">`DeployAppx install force MyApp.appx` 强制卸载当前安装的。如果在安装新的之前找到了相同的包名称，则为 APPX。约.</span><span class="sxs-lookup"><span data-stu-id="dcdf1-161">`DeployAppx install force MyApp.appx` forces uninstalling the currently installed .APPX with the same package name if found before installing the new .APPX.</span></span>  <span data-ttu-id="dcdf1-162">这对于安装是非常有用的。APPX，与当前安装的版本号相同或较低。约.</span><span class="sxs-lookup"><span data-stu-id="dcdf1-162">This is useful for installing an .APPX with the same or lower version number as the currently installed .APPX.</span></span>
* <span data-ttu-id="dcdf1-163">`DeployAppx install retry MyApp.appx` 重试安装。APPX 10 次失败，两次尝试之间的延迟为2秒。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-163">`DeployAppx install retry MyApp.appx` retry installing the .APPX 10 times on failure with 2-second delay between attempts.</span></span>
* <span data-ttu-id="dcdf1-164">`DeployAppx uninstall App_1.0.1.0_x86__publisherid123` 卸载具有匹配的包全名的 .appx。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-164">`DeployAppx uninstall App_1.0.1.0_x86__publisherid123` uninstall the .appx with the matching package full name.</span></span>
*  <span data-ttu-id="dcdf1-165">`DeployAppx uninstall MyApp.appx` 卸载已安装的任何。具有匹配包系列名称的 APPX。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-165">`DeployAppx uninstall MyApp.appx` uninstall any installed .APPX with a matching package family name.</span></span>
* <span data-ttu-id="dcdf1-166">`DeployAppx getpackages` 列出已安装的包的完整名称。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-166">`DeployAppx getpackages` lists installed package full names.</span></span>
* <span data-ttu-id="dcdf1-167">`DeployAppx getpackageid IotCoreDefaultApp.appx` 输出包名称、包系列名称和包的完整名称。约.</span><span class="sxs-lookup"><span data-stu-id="dcdf1-167">`DeployAppx getpackageid IotCoreDefaultApp.appx` prints out the package name, the package family name, and the package full name for the .APPX.</span></span>
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* <span data-ttu-id="dcdf1-168">`DeployAppx register appxmanifest.xml` 不支持</span><span class="sxs-lookup"><span data-stu-id="dcdf1-168">`DeployAppx register appxmanifest.xml` unsupported</span></span>


## <a name="general-command-line-utils"></a><span data-ttu-id="dcdf1-169">常规命令行 Utils</span><span class="sxs-lookup"><span data-stu-id="dcdf1-169">General Command Line Utils</span></span>

### <a name="update-account-password"></a><span data-ttu-id="dcdf1-170">**更新帐户密码：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-170">**Update account password:**</span></span>

<span data-ttu-id="dcdf1-171">强烈建议您更新管理员帐户的默认密码。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-171">It is highly recommended that you update the default password for the Administrator account.</span></span> <span data-ttu-id="dcdf1-172">为此，可以发出以下命令： `net user Administrator [new password]` 其中 `[new password]` 表示所选的强密码。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-172">To do this, you can issue the following command: `net user Administrator [new password]` where `[new password]` represents a strong password of your choice.</span></span>

### <a name="create-local-user-accounts"></a><span data-ttu-id="dcdf1-173">**创建本地用户帐户：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-173">**Create local user accounts:**</span></span>

<span data-ttu-id="dcdf1-174">如果要向其他人授予对 Windows IoT 核心设备的访问权限，可以通过键入来使用 PS 创建其他本地用户帐户 `net user [username] [password] /add` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-174">If you wish to give others access to your Windows IoT Core device, you can create additional local user accounts using PS by typing in `net user [username] [password] /add`.</span></span> <span data-ttu-id="dcdf1-175">如果希望将此用户添加到其他组（如管理员组），请使用 `net localgroup Administrators [username] /add` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-175">If you wish to add this user to other groups, such as the Administrator group, use `net localgroup Administrators [username] /add`.</span></span>

### <a name="set-password"></a><span data-ttu-id="dcdf1-176">**设置密码：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-176">**Set password:**</span></span>

<span data-ttu-id="dcdf1-177">若要更改设备上帐户的密码，请运行 `net user [account-username] [new-password]` 以更改帐户密码。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-177">To change the password on an account on your device, run `net user [account-username] [new-password]` to change the account password.</span></span>

### <a name="query-and-set-device-name"></a><span data-ttu-id="dcdf1-178">**查询和设置设备名称：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-178">**Query and set device name:**</span></span>

<span data-ttu-id="dcdf1-179">若要确定当前设备名称，只需键入即可 `hostname` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-179">To identify your current device name, simply type `hostname`.</span></span> <span data-ttu-id="dcdf1-180">若要更改 Windows IoT Core 设备的名称，请键入 `SetComputerName [new machinename]` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-180">To change the name of your Windows IoT Core device, type `SetComputerName [new machinename]`.</span></span> <span data-ttu-id="dcdf1-181">你可能需要重新启动设备以使名称更改生效。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-181">You may need to restart your device for the name change to take effect.</span></span>

### <a name="basic-network-configuration"></a><span data-ttu-id="dcdf1-182">**基本网络配置：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-182">**Basic network configuration:**</span></span>

<span data-ttu-id="dcdf1-183">您可能已熟悉的许多基本网络配置实用工具在 Windows IoT Core （包括、、、、和等命令）中可用 `ping.exe` `netstat.exe` `netsh.exe` `ipconfig.exe` `tracert.exe` `arp.exe` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-183">Many of the basic network configuration utilities you may already be familiar with are available in Windows IoT Core, including commands such as `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, and `arp.exe`.</span></span>

### <a name="copy-utilities"></a><span data-ttu-id="dcdf1-184">**复制实用工具：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-184">**Copy utilities:**</span></span>

<span data-ttu-id="dcdf1-185">Microsoft 提供熟悉的工具，包括 `sfpcopy.exe` 和 `xcopy.exe` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-185">Microsoft is providing familiar tools, including `sfpcopy.exe` as well as `xcopy.exe`.</span></span>

### <a name="process-management"></a><span data-ttu-id="dcdf1-186">**流程管理：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-186">**Process Management:**</span></span>

<span data-ttu-id="dcdf1-187">若要查看当前正在运行的进程，可以尝试 `get-process` 或 `tlist.exe` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-187">To view currently running processes, you can try either `get-process` or alternatively `tlist.exe`.</span></span> <span data-ttu-id="dcdf1-188">若要停止正在运行的进程，请键入 `kill.exe [pid or process name]` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-188">To stop a running process, type `kill.exe [pid or process name]`.</span></span>


### <a name="set-boot-option-headless-vs-headed-boot"></a><span data-ttu-id="dcdf1-189">**设置启动选项 (无外设 vs Boot) ：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-189">**Set Boot Option (Headless vs. headed boot):**</span></span>

<span data-ttu-id="dcdf1-190">当需要显示功能时，可以将 Windows IoT Core 设备设置为 () 或无外设 (当) 设备模式下不需要或不可用时。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-190">Windows IoT Core devices can be set to headed (when display capabilities are required) or headless (when a display is not required or available) device mode.</span></span> <span data-ttu-id="dcdf1-191">若要更改此设置，请使用 `setbootoption.exe [headed | headless]` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-191">To change this setting, use `setbootoption.exe [headed | headless]`.</span></span>

> [!NOTE]
> <span data-ttu-id="dcdf1-192">更改此设置将需要重新启动才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-192">Changing this setting will require a reboot in order for the change to take effect.</span></span>

### <a name="task-scheduler"></a><span data-ttu-id="dcdf1-193">**任务计划程序：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-193">**Task scheduler:**</span></span>

<span data-ttu-id="dcdf1-194">若要查看计划任务的当前列表，请使用 `schtasks.exe` 命令。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-194">To view the current list of scheduled tasks, use the `schtasks.exe` command.</span></span> <span data-ttu-id="dcdf1-195">可以通过开关创建新任务， `/create` 也可以用开关运行按需任务 `/run` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-195">You can create new tasks with the `/create` switch or run on-demand tasks with the `/run` switch.</span></span> <span data-ttu-id="dcdf1-196">有关受支持参数的完整列表，请使用 `schtasks.exe /?`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-196">For a full list of supported parameters, use `schtasks.exe /?`</span></span>

### <a name="device-drivers"></a><span data-ttu-id="dcdf1-197">**设备驱动程序：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-197">**Device drivers:**</span></span>

<span data-ttu-id="dcdf1-198">设备控制台实用工具可用于识别和管理已安装的设备和驱动程序。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-198">The device console utility is useful in identifying and managing installed devices and drivers.</span></span> <span data-ttu-id="dcdf1-199">有关参数的完整列表，请使用 `devcon.exe /?`</span><span class="sxs-lookup"><span data-stu-id="dcdf1-199">For a full list of parameters, use `devcon.exe /?`</span></span>

### <a name="registry-access"></a><span data-ttu-id="dcdf1-200">**注册表访问：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-200">**Registry Access:**</span></span>

<span data-ttu-id="dcdf1-201">如果需要访问注册表以查看或修改设置，请使用 `reg.exe /?` 命令获取受支持参数的完整列表。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-201">If you need to access the registry to view or modify settings, use the `reg.exe /?` Command for the full list of supported parameters.</span></span>

### <a name="services"></a><span data-ttu-id="dcdf1-202">**服务：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-202">**Services:**</span></span>

<span data-ttu-id="dcdf1-203">可以通过命令来完成管理 Windows 服务 `net.exe` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-203">Managing Windows services can be accomplished via the `net.exe` command.</span></span> <span data-ttu-id="dcdf1-204">若要查看正在运行的服务的列表，请键入 `net start` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-204">To see a list of running services, type `net start`.</span></span> <span data-ttu-id="dcdf1-205">若要启动或停止特定服务，请键入 `net [start | stop] [service name]` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-205">To start or stop a specific service, type `net [start | stop] [service name]`.</span></span> <span data-ttu-id="dcdf1-206">此外，也可以通过命令使用服务控制管理器 `sc.exe` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-206">Alternatively, you can also use the service control manager via `sc.exe` command.</span></span>

### <a name="boot-configuration"></a><span data-ttu-id="dcdf1-207">**启动配置：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-207">**Boot configuration:**</span></span>

<span data-ttu-id="dcdf1-208">你可以通过使用对 Windows IoT Core 设备的启动配置进行更改 `bcdedit.exe` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-208">You can make changes to the boot configuration of your Windows IoT Core device by using `bcdedit.exe`.</span></span> <span data-ttu-id="dcdf1-209">例如，可以使用命令来启用 testsigning `bcdedit –set testsigning on` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-209">For instance, you can enable testsigning with `bcdedit –set testsigning on` command.</span></span>

### <a name="shutdownrestart-device"></a><span data-ttu-id="dcdf1-210">**关机/重新启动设备：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-210">**Shutdown/restart device:**</span></span>

<span data-ttu-id="dcdf1-211">若要关闭设备，请键入 `shutdown /s /t 0` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-211">To shut down your device, type `shutdown /s /t 0`.</span></span> <span data-ttu-id="dcdf1-212">若要重新启动设备，请改用 `/r` 命令 `shutdown /r /t 0` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-212">To restart the device, use the `/r` switch instead with the command `shutdown /r /t 0`.</span></span>

### <a name="viewing-and-changing-display-settings"></a><span data-ttu-id="dcdf1-213">**查看和更改显示设置**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-213">**Viewing and changing display settings**</span></span>
<span data-ttu-id="dcdf1-214">SetDisplayResolution 工具可用于列出当前显示设置并显示受支持值的列表。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-214">The SetDisplayResolution tool may be used for listing the current display settings and to show the list of supported values.</span></span>  <span data-ttu-id="dcdf1-215">它可以进一步用于调整显示器的分辨率、刷新率和/或方向，以适应平台支持的值。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-215">It can further be used for adjusting the display's resolution, refresh rate and/or orientation to values supported by your platform.</span></span>  <span data-ttu-id="dcdf1-216">实用程序接受以下命令行参数：</span><span class="sxs-lookup"><span data-stu-id="dcdf1-216">The utility accepts the following command line arguments:</span></span>

* <span data-ttu-id="dcdf1-217">`SetDisplayResolution` 列出当前显示分辨率。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-217">`SetDisplayResolution` Lists the current display resolution.</span></span>
* <span data-ttu-id="dcdf1-218">`SetDisplayResolution -list` 列出支持的显示分辨率。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-218">`SetDisplayResolution -list` Lists supported display resolutions.</span></span>
* <span data-ttu-id="dcdf1-219">`SetDisplayResolution -orientation:[n]` 更改显示方向，其中 n = 0、90180或270。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-219">`SetDisplayResolution -orientation:[n]` Change the display orientation, where n=0,90,180 or 270.</span></span>
* <span data-ttu-id="dcdf1-220">`SetDisplayResolution [width] [height]` 更改宽度和高度（以像素为单位）</span><span class="sxs-lookup"><span data-stu-id="dcdf1-220">`SetDisplayResolution [width] [height]` Change the width and height in pixels</span></span> 
* <span data-ttu-id="dcdf1-221">`SetDisplayResolution [width] [height] [refreshrate]` 更改宽度、高度和刷新率，其中宽度和高度以像素为单位，refreshrate 以 Hz 为单位。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-221">`SetDisplayResolution [width] [height] [refreshrate]` Change width, height, and refresh rate where width and height are in pixels and refreshrate in Hz</span></span> 
* <span data-ttu-id="dcdf1-222">`SetDisplayResolution [width] [height] [refreshrate] [orientation]` 更改 width、height、refreshrate 和 screen 的宽度和高度（以像素为单位），refreshrate 以 Hz 为单位，方向为0、90、180或270。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-222">`SetDisplayResolution [width] [height] [refreshrate] [orientation]` Change width, height, refreshrate and screen orientation where width and height are in pixels, refreshrate in Hz and orientation is one of 0, 90, 180 or 270.</span></span>

### <a name="take-screenshot"></a><span data-ttu-id="dcdf1-223">**拍摄屏幕截图：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-223">**Take screenshot:**</span></span>

<span data-ttu-id="dcdf1-224">你可以使用来获取 Windows IoTCore 设备的屏幕截图 `ScreenCapture.exe` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-224">You can take the screenshot of your Windows IoTCore device by using `ScreenCapture.exe`.</span></span> <span data-ttu-id="dcdf1-225">例如，"运行 `ScreenCapture c:\folder\screencap.jpg` " 将获取屏幕截图，并将其保存到 screencap.jpg 文件中。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-225">For example, run `ScreenCapture c:\folder\screencap.jpg` will take the screenshot and save it in screencap.jpg file.</span></span>

### <a name="get-information-about-network-adapters"></a><span data-ttu-id="dcdf1-226">**获取网络适配器的相关信息：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-226">**Get information about Network Adapters:**</span></span>

<span data-ttu-id="dcdf1-227">若要查看所有可用网络适配器的列表，请运行 `GetAdapterInfo` 工具。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-227">To view the list of all the available network adapters, run `GetAdapterInfo` tool.</span></span>

### <a name="set-folder-permissions-for-uwp-apps"></a><span data-ttu-id="dcdf1-228">**设置 UWP 应用的文件夹权限：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-228">**Set folder permissions for UWP apps:**</span></span>

<span data-ttu-id="dcdf1-229">并非设备上的所有文件夹都可供通用 Windows 应用访问。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-229">Not all folders on your device are accessible by Universal Windows Apps.</span></span> <span data-ttu-id="dcdf1-230">若要使某个文件夹可供 UWP 应用访问，可以使用 `FolderPermissions` 工具。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-230">To make a folder accessible to a UWP app, you can use `FolderPermissions` tool.</span></span> <span data-ttu-id="dcdf1-231">例如，运行 `FolderPermissions c:\test -e` 以提供 UWP 应用对 `c:\test` 文件夹的访问权限。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-231">For example, run `FolderPermissions c:\test -e` to give UWP apps access to `c:\test` folder.</span></span> <span data-ttu-id="dcdf1-232">请注意，这仅适用于示例的本机 Win32 api。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-232">Note this will work only with native Win32 apis for eg.</span></span> <span data-ttu-id="dcdf1-233">CreateFile2，而不是采用 WinRT api，如 StorageFolder、StorageFile 等。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-233">CreateFile2 and not with WinRT apis like StorageFolder, StorageFile etc.</span></span>

### <a name="work-with-serial-ports"></a><span data-ttu-id="dcdf1-234">**使用串行端口：**</span><span class="sxs-lookup"><span data-stu-id="dcdf1-234">**Work with Serial Ports:**</span></span>
<span data-ttu-id="dcdf1-235">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) 使你能够从命令行使用串行端口。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-235">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) allows you to work with serial ports from the command line.</span></span> <span data-ttu-id="dcdf1-236">它作为示例项目提供到了 ms iot 示例存储库中。</span><span class="sxs-lookup"><span data-stu-id="dcdf1-236">It is provided as a sample project in the ms-iot samples repo.</span></span> 

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


