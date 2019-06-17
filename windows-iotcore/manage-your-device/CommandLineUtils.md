---
title: Windows 10 IoT Core 命令行实用程序
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解要连接到你的设备后用于 PowreShell 的命令行实用程序。
keywords: windows iot、 命令行、 命令行实用工具，PowerShell
ms.openlocfilehash: 4ba4ce1b77e14bb6cd8323ce44cb3a7b82ae8dbc
ms.sourcegitcommit: 3aaacf5e3ddbebb4a9324cfc8688110a2eb067ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132263"
---
# <a name="windows-10-iot-core-command-line-utils"></a><span data-ttu-id="61c1f-104">Windows 10 IoT Core 命令行实用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-104">Windows 10 IoT Core Command Line Utils</span></span>

<span data-ttu-id="61c1f-105">正在寻找可用于配置设备上的某些设置的工具？</span><span class="sxs-lookup"><span data-stu-id="61c1f-105">Looking to configure some of the settings on your device?</span></span> <span data-ttu-id="61c1f-106">以下工具是可供您使用可用。</span><span class="sxs-lookup"><span data-stu-id="61c1f-106">The below tools are available at your disposal.</span></span> <span data-ttu-id="61c1f-107">在[连接到你的设备](../connect-your-device/PowerShell.md)后，使用 PowerShell 运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="61c1f-107">Use PowerShell to run these commands after [connecting to your device](../connect-your-device/PowerShell.md).</span></span>

> [!NOTE]
> <span data-ttu-id="61c1f-108">这些工具不会预先加载-你将需要包括适当的功能 Id 以在图像中获取这些工具。</span><span class="sxs-lookup"><span data-stu-id="61c1f-108">These tools are not pre-loaded - you will need to include appropriate feature IDs to get these tools in the image.</span></span>

## <a name="iot-core-specific-command-line-utils"></a><span data-ttu-id="61c1f-109">特定于 IoT Core 的命令行实用工具</span><span class="sxs-lookup"><span data-stu-id="61c1f-109">IoT Core-specific Command Line Utils</span></span>

### <a name="setting-startup-app"></a><span data-ttu-id="61c1f-110">**设置启动应用：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-110">**Setting startup app:**</span></span>
<span data-ttu-id="61c1f-111">使用启动编辑器在你的 Windows 10 IoT Core 设备上配置启动应用。</span><span class="sxs-lookup"><span data-stu-id="61c1f-111">Use the startup editor to configure startup apps on your Windows IoT Core device.</span></span> <span data-ttu-id="61c1f-112">借助以下选项之一，运行 `IotStartup`：</span><span class="sxs-lookup"><span data-stu-id="61c1f-112">Run `IotStartup` with any of the following options:</span></span>

* <span data-ttu-id="61c1f-113">`IotStartup list`，用于列出已安装的应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-113">`IotStartup list` lists installed applications</span></span>
* <span data-ttu-id="61c1f-114">`IotStartup list headed`，用于列出已安装的有外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-114">`IotStartup list headed` lists installed headed applications</span></span>
* <span data-ttu-id="61c1f-115">`IotStartup list headless`，用于列出已安装的无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-115">`IotStartup list headless` lists installed headless applications</span></span>
* <span data-ttu-id="61c1f-116">`IotStartup list [MyApp]`，用于列出已安装的与模式 `MyApp` 匹配的应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-116">`IotStartup list [MyApp]` list installed applications that match pattern `MyApp`</span></span>
* <span data-ttu-id="61c1f-117">`IotStartup add`，用于添加有外设和无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-117">`IotStartup add` adds headed and headless applications</span></span>
* <span data-ttu-id="61c1f-118">`IotStartup add headed [MyApp]`，用于添加与模式 `MyApp` 匹配的有外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-118">`IotStartup add headed [MyApp]` adds headed applications that match pattern `MyApp`.</span></span>  <span data-ttu-id="61c1f-119">模式必须只匹配一个应用程序。</span><span class="sxs-lookup"><span data-stu-id="61c1f-119">Pattern must match only one application.</span></span>
* <span data-ttu-id="61c1f-120">`IotStartup add headless [Task1]`，用于添加与模式 `Task1` 匹配的无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-120">`IotStartup add headless [Task1]` adds headless applications that match pattern `Task1`</span></span>
* <span data-ttu-id="61c1f-121">`IotStartup remove`，用于删除有外设和无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-121">`IotStartup remove` removes headed and headless applications</span></span>
* <span data-ttu-id="61c1f-122">`IotStartup remove headed [MyApp]`，用于删除与模式 `MyApp` 匹配的有外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-122">`IotStartup remove headed [MyApp]` removes headed applications that match pattern `MyApp`</span></span>
* <span data-ttu-id="61c1f-123">`IotStartup remove headless [Task1]`，用于删除与模式 `Task1` 匹配的无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-123">`IotStartup remove headless [Task1]` removes headless applications that match pattern `Task1`</span></span>
* <span data-ttu-id="61c1f-124">`IotStartup startup`，用于列出针对启动所注册的有外设和无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-124">`IotStartup startup` lists headed and headless applications registered for startup</span></span>
* <span data-ttu-id="61c1f-125">`IotStartup startup [MyApp]`，用于列出针对启动所注册的且与模式 `MyApp` 匹配的有外设和无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-125">`IotStartup startup [MyApp]` lists headed and headless applications registered for startup that match pattern `MyApp`</span></span>
* <span data-ttu-id="61c1f-126">`IotStartup startup headed [MyApp]`，用于列出针对启动所注册的且与 `MyApp` 匹配的有外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-126">`IotStartup startup headed [MyApp]` lists headed applications registered for startup that match `MyApp`</span></span>
* <span data-ttu-id="61c1f-127">`IotStartup startup headless [Task1]`，用于列出针对启动所注册的且与 `Task1` 匹配的无外设应用程序</span><span class="sxs-lookup"><span data-stu-id="61c1f-127">`IotStartup startup headless [Task1]` lists headless applications registered for startup that match `Task1`</span></span>
* <span data-ttu-id="61c1f-128">`IotStartup run [MyApp]` 启动应用程序标识 `MyApp`</span><span class="sxs-lookup"><span data-stu-id="61c1f-128">`IotStartup run [MyApp]` start app identified by `MyApp`</span></span>
* <span data-ttu-id="61c1f-129">`IotStartup stop [MyApp]` 停止由标识的应用 `MyApp`</span><span class="sxs-lookup"><span data-stu-id="61c1f-129">`IotStartup stop [MyApp]` stop app identified by `MyApp`</span></span>
* <span data-ttu-id="61c1f-130">若要获取进一步帮助，请尝试 `IotStartup help`</span><span class="sxs-lookup"><span data-stu-id="61c1f-130">For further help, try `IotStartup help`</span></span>

### <a name="change-settings-for-region-and-user-or-speech-language"></a><span data-ttu-id="61c1f-131">**更改区域和用户或语音语言设置：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-131">**Change settings for region and user or speech language:**</span></span>

<span data-ttu-id="61c1f-132">`IoTSettings`工具更改区域、 用户语言或语音语言。</span><span class="sxs-lookup"><span data-stu-id="61c1f-132">The `IoTSettings` tool changes region, user language or speech language.</span></span> <span data-ttu-id="61c1f-133">这是可以从使用 ProcessLauncher API 的应用程序调用的命令行工具。</span><span class="sxs-lookup"><span data-stu-id="61c1f-133">This is a command line tool that can be invoked from an application using the ProcessLauncher API.</span></span> <span data-ttu-id="61c1f-134">这些命令必须作为默认帐户，不是管理员身份运行。</span><span class="sxs-lookup"><span data-stu-id="61c1f-134">These commands must be run as default account, not administrator.</span></span>

* <span data-ttu-id="61c1f-135">`IotSettings del account {all | username}` 删除系统上的所有 MSA 或 AAD 帐户或特定的帐户。</span><span class="sxs-lookup"><span data-stu-id="61c1f-135">`IotSettings del account {all | username}` deletes all MSA or AAD accounts on the system or a specific account.</span></span>  <span data-ttu-id="61c1f-136">特定帐户采用窗体 username@provider.com</span><span class="sxs-lookup"><span data-stu-id="61c1f-136">Specific accounts take the form username@provider.com</span></span>
* <span data-ttu-id="61c1f-137">`IotSettings del diagnostics` 删除当前的设备在云中的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="61c1f-137">`IotSettings del diagnostics` deletes diagnostic information in the cloud for the current device.</span></span>  <span data-ttu-id="61c1f-138">请注意，这将删除到调用的时间的历史记录。</span><span class="sxs-lookup"><span data-stu-id="61c1f-138">Note that this removes the history up to the time of invocation.</span></span>  <span data-ttu-id="61c1f-139">新的诊断信息仍要记入日志。</span><span class="sxs-lookup"><span data-stu-id="61c1f-139">New diagnostics information will continue to be logged.</span></span>
* <span data-ttu-id="61c1f-140">`IotSettings list account` 列出所有 MSA 或 AAD 帐户登录到的设备。</span><span class="sxs-lookup"><span data-stu-id="61c1f-140">`IotSettings list account` lists all MSA or AAD accounts that have been signed into the device.</span></span>
* <span data-ttu-id="61c1f-141">`IotSettings list uilanguage` 列出所有的 UI 语言</span><span class="sxs-lookup"><span data-stu-id="61c1f-141">`IotSettings list uilanguage` lists all UI languages</span></span>
* <span data-ttu-id="61c1f-142">`IotSettings list speechlanguage` 列出所有语音语言</span><span class="sxs-lookup"><span data-stu-id="61c1f-142">`IotSettings list speechlanguage` lists all speech languages</span></span>
* <span data-ttu-id="61c1f-143">`IotSettings get uilanguage` 显示当前 UI 语言</span><span class="sxs-lookup"><span data-stu-id="61c1f-143">`IotSettings get uilanguage` displays current UI language</span></span>
* <span data-ttu-id="61c1f-144">`IotSettings get speechlanguage` 显示当前语音语言</span><span class="sxs-lookup"><span data-stu-id="61c1f-144">`IotSettings get speechlanguage` displays current speech language</span></span>
* <span data-ttu-id="61c1f-145">`IotSettings get region` 显示当前的区域</span><span class="sxs-lookup"><span data-stu-id="61c1f-145">`IotSettings get region` displays current region</span></span>
* <span data-ttu-id="61c1f-146">`IotSettings set uilanguage language\_tag - (e.g. fr-CA)` 设置默认 UI 语言加拿大法语）</span><span class="sxs-lookup"><span data-stu-id="61c1f-146">`IotSettings set uilanguage language\_tag - (e.g. fr-CA)` sets default UI language French Canadian)</span></span>
* <span data-ttu-id="61c1f-147">`IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` 设置语音语言加拿大法语）</span><span class="sxs-lookup"><span data-stu-id="61c1f-147">`IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` sets speech language French Canadian)</span></span>
* <span data-ttu-id="61c1f-148">`IotSettings set region region\_code - (e.g. CA)` 将默认区域设置为加拿大）</span><span class="sxs-lookup"><span data-stu-id="61c1f-148">`IotSettings set region region\_code - (e.g. CA)` sets default region to Canada)</span></span>
* <span data-ttu-id="61c1f-149">`IotSettings set bluetoothpref {sink | source}` 指定蓝牙角色首选项时使用 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 功能生成的设备连接到另一台设备同时支持这两个角色选择。</span><span class="sxs-lookup"><span data-stu-id="61c1f-149">`IotSettings set bluetoothpref {sink | source}` Specifies the Bluetooth role preference to select when devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK features connect to another device that also supports both roles.</span></span>
* <span data-ttu-id="61c1f-150">`IotSettings get bluetoothpref` 返回使用 IOT_BLUETOOTH_A2DP_SOURCE 和 IOT_BLUETOOTH_A2DP_SINK 构建的设备的当前蓝牙角色首选项。</span><span class="sxs-lookup"><span data-stu-id="61c1f-150">`IotSettings get bluetoothpref` returns the current Bluetooth role preference for devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK.</span></span>  <span data-ttu-id="61c1f-151">默认值为源。</span><span class="sxs-lookup"><span data-stu-id="61c1f-151">The default is source.</span></span>

> [!TIP]
> <span data-ttu-id="61c1f-152">`IoTSettings -list uiLanguage` 将为返回受支持的 UI 语言的列表 （在 Windows IoT core 映像已针对执行的版本）</span><span class="sxs-lookup"><span data-stu-id="61c1f-152">`IoTSettings -list uiLanguage` will give back the list of supported UI language (in the version of Windows IoT core image it has been executed against)</span></span>
    
### <a name="change-default-audio-device-and-volume"></a><span data-ttu-id="61c1f-153">**更改默认音频设备和卷：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-153">**Change default audio device and volume:**</span></span>

<span data-ttu-id="61c1f-154">`IoTCoreAudioControlTool`工具控制音频相关的选项，如设置捕获和播放设备的默认值和更改音量。</span><span class="sxs-lookup"><span data-stu-id="61c1f-154">The `IoTCoreAudioControlTool` tool controls audio related options, such as setting default capture and playback devices and changing the volume.</span></span> <span data-ttu-id="61c1f-155">有关参数的完整列表，运行`IoTCoreAudioControlTool h`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-155">For a full list of parameters, run `IoTCoreAudioControlTool h`.</span></span>

### <a name="manually-installing-appx-files"></a><span data-ttu-id="61c1f-156">**手动安装。APPX 文件：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-156">**Manually installing .APPX files:**</span></span>
<span data-ttu-id="61c1f-157">DeployAppx 使安装和删除。在开发方案的 APPX 包。</span><span class="sxs-lookup"><span data-stu-id="61c1f-157">DeployAppx enables installing, and removing in .APPX packages in development scenarios.</span></span>  <span data-ttu-id="61c1f-158">安装的正确方法。在生产映像中的 APPX 包是使用预配包，如中所述[安装您的应用程序](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd)主题。</span><span class="sxs-lookup"><span data-stu-id="61c1f-158">The correct method for installing .APPX packages in production images is to use a provisioning package as documented in the [Install your app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) subject.</span></span>  <span data-ttu-id="61c1f-159">DeployAppx 还支持查询。APPX 包信息。</span><span class="sxs-lookup"><span data-stu-id="61c1f-159">DeployAppx also supports querying .APPX package information.</span></span>

*  <span data-ttu-id="61c1f-160">`DeployAppx install MyApp.appx` 安装。APPX 和具有相同名称的证书如果找到。</span><span class="sxs-lookup"><span data-stu-id="61c1f-160">`DeployAppx install MyApp.appx` installs the .APPX and the certificate of the same name if found.</span></span>
* <span data-ttu-id="61c1f-161">`DeployAppx install force MyApp.appx` 强制卸载当前安装。如果名称与同一个包的 APPX 安装新之前找到。APPX。</span><span class="sxs-lookup"><span data-stu-id="61c1f-161">`DeployAppx install force MyApp.appx` forces uninstalling the currently installed .APPX with the same package name if found before installing the new .APPX.</span></span>  <span data-ttu-id="61c1f-162">这可用于安装。作为当前安装的相同或更低版本号的 APPX。APPX。</span><span class="sxs-lookup"><span data-stu-id="61c1f-162">This is useful for installing an .APPX with the same or lower version number as the currently installed .APPX.</span></span>
* <span data-ttu-id="61c1f-163">`DeployAppx install retry MyApp.appx` 重试安装。在失败时使用 2 个第二个 APPX 10 次尝试的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="61c1f-163">`DeployAppx install retry MyApp.appx` retry installing the .APPX 10 times on failure with 2 second delay between attempts.</span></span>
* <span data-ttu-id="61c1f-164">`DeployAppx uninstall App_1.0.1.0_x86__publisherid123` 卸载.appx 具有匹配的包完整名称。</span><span class="sxs-lookup"><span data-stu-id="61c1f-164">`DeployAppx uninstall App_1.0.1.0_x86__publisherid123` uninstall the .appx with the matching package full name.</span></span>
*  <span data-ttu-id="61c1f-165">`DeployAppx uninstall MyApp.appx` 卸载任何已安装。具有匹配的包系列名称的 APPX。</span><span class="sxs-lookup"><span data-stu-id="61c1f-165">`DeployAppx uninstall MyApp.appx` uninstall any installed .APPX with a matching package family name.</span></span>
* <span data-ttu-id="61c1f-166">`DeployAppx getpackages` 列出已安装的包完整名称。</span><span class="sxs-lookup"><span data-stu-id="61c1f-166">`DeployAppx getpackages` lists installed package full names.</span></span>
* <span data-ttu-id="61c1f-167">`DeployAppx getpackageid IotCoreDefaultApp.appx` 打印出包名称、 包系列名称和包的完整名称。APPX。</span><span class="sxs-lookup"><span data-stu-id="61c1f-167">`DeployAppx getpackageid IotCoreDefaultApp.appx` prints out the package name, the package family name, and the package full name for the .APPX.</span></span>
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* <span data-ttu-id="61c1f-168">`DeployAppx register appxmanifest.xml` 不受支持</span><span class="sxs-lookup"><span data-stu-id="61c1f-168">`DeployAppx register appxmanifest.xml` unsupported</span></span>


## <a name="general-command-line-utils"></a><span data-ttu-id="61c1f-169">常规命令行实用工具</span><span class="sxs-lookup"><span data-stu-id="61c1f-169">General Command Line Utils</span></span>

### <a name="update-account-password"></a><span data-ttu-id="61c1f-170">**更新帐户密码：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-170">**Update account password:**</span></span>

<span data-ttu-id="61c1f-171">强烈建议你更新默认的管理员帐户密码。</span><span class="sxs-lookup"><span data-stu-id="61c1f-171">It is highly recommended that you update the default password for the Administrator account.</span></span> <span data-ttu-id="61c1f-172">若要更新帐户密码，你可以发出以下命令：`net user Administrator [new password]`（其中 `[new password]` 表示你选择的强密码）。</span><span class="sxs-lookup"><span data-stu-id="61c1f-172">To do this, you can issue the following command: `net user Administrator [new password]` where `[new password]` represents a strong password of your choice.</span></span>

### <a name="create-local-user-accounts"></a><span data-ttu-id="61c1f-173">**创建本地用户帐户：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-173">**Create local user accounts:**</span></span>

<span data-ttu-id="61c1f-174">如果你想要授予其他人访问你的 Windows IoT Core 设备的权限，你可以通过在 `net user [username] [password] /add` 中键入，并使用 PS 创建其他本地用户帐户。</span><span class="sxs-lookup"><span data-stu-id="61c1f-174">If you wish to give others access to your Windows IoT Core device, you can create additional local user accounts using PS by typing in `net user [username] [password] /add`.</span></span> <span data-ttu-id="61c1f-175">如果你想要将此用户添加到其他组（例如管理员组），则使用 `net localgroup Administrators [username] /add`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-175">If you wish to add this user to other groups, such as the Administrator group, use `net localgroup Administrators [username] /add`.</span></span>

### <a name="set-password"></a><span data-ttu-id="61c1f-176">**设置密码：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-176">**Set password:**</span></span>

<span data-ttu-id="61c1f-177">若要更改你的设备上的帐户密码，可通过运行 `net user [account-username] [new-password]` 来更改帐户密码。</span><span class="sxs-lookup"><span data-stu-id="61c1f-177">To change the password on an account on your device, run `net user [account-username] [new-password]` to change the account password.</span></span>

### <a name="query-and-set-device-name"></a><span data-ttu-id="61c1f-178">**查询和设置设备名称：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-178">**Query and set device name:**</span></span>

<span data-ttu-id="61c1f-179">若要确定当前设备名称，只需键入 `hostname`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-179">To identify your current device name, simply type `hostname`.</span></span> <span data-ttu-id="61c1f-180">若要更改你的 Windows IoT Core 设备的名称，应键入 `SetComputerName [new machinename]`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-180">To change the name of your Windows IoT Core device, type `SetComputerName [new machinename]`.</span></span> <span data-ttu-id="61c1f-181">你可能需要重新启动你的设备才能使更改的名称生效。</span><span class="sxs-lookup"><span data-stu-id="61c1f-181">You may need to restart your device for the name change to take effect.</span></span>

### <a name="basic-network-configuration"></a><span data-ttu-id="61c1f-182">**基本网络配置：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-182">**Basic network configuration:**</span></span>

<span data-ttu-id="61c1f-183">许多您可能已经熟悉的基本网络配置实用工具都可以在 Windows IoT Core 中，其中包括命令，例如`ping.exe`， `netstat.exe`， `netsh.exe`， `ipconfig.exe`， `tracert.exe`，并`arp.exe`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-183">Many of the basic network configuration utilities you may already be familiar with are available in Windows IoT Core, including commands such as `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, and `arp.exe`.</span></span>

### <a name="copy-utilities"></a><span data-ttu-id="61c1f-184">**复制实用程序：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-184">**Copy utilities:**</span></span>

<span data-ttu-id="61c1f-185">Microsoft 将提供熟悉的工具，包括 `sfpcopy.exe` 以及 `xcopy.exe`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-185">Microsoft is providing familiar tools, including `sfpcopy.exe` as well as `xcopy.exe`.</span></span>

### <a name="process-management"></a><span data-ttu-id="61c1f-186">**进程管理：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-186">**Process Management:**</span></span>

<span data-ttu-id="61c1f-187">若要查看当前正在运行的进程，可以尝试 `get-process` 或 `tlist.exe`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-187">To view currently running processes, you can try either `get-process` or alternatively `tlist.exe`.</span></span> <span data-ttu-id="61c1f-188">若要停止正在运行的进程，请键入 `kill.exe [pid or process name]`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-188">To stop a running process, type `kill.exe [pid or process name]`.</span></span>


### <a name="set-boot-option-headless-vs-headed-boot"></a><span data-ttu-id="61c1f-189">**设置启动选项（无外设与有外设启动）：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-189">**Set Boot Option (Headless vs. headed boot):**</span></span>

<span data-ttu-id="61c1f-190">Windows IoT Core 设备可以设置为有外设设备模式（需要显示功能时）或无外设设备模式（显示功能不是必需项或不可用时）。</span><span class="sxs-lookup"><span data-stu-id="61c1f-190">Windows IoT Core devices can be set to headed (when display capabilities are required) or headless (when a display is not required or available) device mode.</span></span> <span data-ttu-id="61c1f-191">若要更改此设置，请使用 `setbootoption.exe [headed | headless]`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-191">To change this setting, use `setbootoption.exe [headed | headless]`.</span></span>

> [!NOTE]
> <span data-ttu-id="61c1f-192">更改此设置将需要重新启动顺序的更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="61c1f-192">Changing this setting will require a reboot in order for the change to take effect.</span></span>

### <a name="task-scheduler"></a><span data-ttu-id="61c1f-193">**任务计划程序：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-193">**Task scheduler:**</span></span>

<span data-ttu-id="61c1f-194">若要查看计划任务的当前列表，请使用 `schtasks.exe` 命令。</span><span class="sxs-lookup"><span data-stu-id="61c1f-194">To view the current list of scheduled tasks, use the `schtasks.exe` command.</span></span> <span data-ttu-id="61c1f-195">你可以使用 `/create` 开关创建新任务，或使用 `/run` 开关运行按需任务。</span><span class="sxs-lookup"><span data-stu-id="61c1f-195">You can create new tasks with the `/create` switch or run on-demand tasks with the `/run` switch.</span></span> <span data-ttu-id="61c1f-196">若要获取支持的参数的完整列表，请使用 `schtasks.exe /?`</span><span class="sxs-lookup"><span data-stu-id="61c1f-196">For a full list of supported parameters, use `schtasks.exe /?`</span></span>

### <a name="device-drivers"></a><span data-ttu-id="61c1f-197">**设备驱动程序：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-197">**Device drivers:**</span></span>

<span data-ttu-id="61c1f-198">设备控制台实用程序在识别和管理已安装的设备和驱动程序方面十分有用。</span><span class="sxs-lookup"><span data-stu-id="61c1f-198">The device console utility is useful in identifying and managing installed devices and drivers.</span></span> <span data-ttu-id="61c1f-199">若要获取参数的完整列表，请使用 `devcon.exe /?`</span><span class="sxs-lookup"><span data-stu-id="61c1f-199">For a full list of parameters, use `devcon.exe /?`</span></span>

### <a name="registry-access"></a><span data-ttu-id="61c1f-200">**注册表访问：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-200">**Registry Access:**</span></span>

<span data-ttu-id="61c1f-201">如果你需要通过访问注册表来查看或修改设置，请使用 `reg.exe /?` 命令获取有关支持的参数的完整列表。</span><span class="sxs-lookup"><span data-stu-id="61c1f-201">If you need to access the registry to view or modify settings, use the `reg.exe /?` Command for the full list of supported parameters.</span></span>

### <a name="services"></a><span data-ttu-id="61c1f-202">**服务：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-202">**Services:**</span></span>

<span data-ttu-id="61c1f-203">管理 Windows 服务可以通过 `net.exe` 命令来完成。</span><span class="sxs-lookup"><span data-stu-id="61c1f-203">Managing Windows services can be accomplished via the `net.exe` command.</span></span> <span data-ttu-id="61c1f-204">若要查看运行中的服务的列表，请键入 `net start`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-204">To see a list of running services, type `net start`.</span></span> <span data-ttu-id="61c1f-205">若要启动或停止特定的服务，请键入 `net [start | stop] [service name]`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-205">To start or stop a specific service, type `net [start | stop] [service name]`.</span></span> <span data-ttu-id="61c1f-206">此外，还可以通过 `sc.exe` 命令使用服务控制管理器。</span><span class="sxs-lookup"><span data-stu-id="61c1f-206">Alternatively, you can also use the service control manager via `sc.exe` command.</span></span>

### <a name="boot-configuration"></a><span data-ttu-id="61c1f-207">**启动配置：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-207">**Boot configuration:**</span></span>

<span data-ttu-id="61c1f-208">可以在 Windows IoT Core 设备的启动配置进行更改，通过使用`bcdedit.exe`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-208">You can make changes to the boot configuration of your Windows IoT Core device by using `bcdedit.exe`.</span></span> <span data-ttu-id="61c1f-209">例如，可启用 testsigning 与`bcdedit –set testsigning on`命令。</span><span class="sxs-lookup"><span data-stu-id="61c1f-209">For instance, you can enable testsigning with `bcdedit –set testsigning on` command.</span></span>

### <a name="shutdownrestart-device"></a><span data-ttu-id="61c1f-210">**关闭/重新启动设备：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-210">**Shutdown/restart device:**</span></span>

<span data-ttu-id="61c1f-211">若要关闭设备，请键入 `shutdown /s /t 0`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-211">To shut down your device, type `shutdown /s /t 0`.</span></span> <span data-ttu-id="61c1f-212">若要重新启动设备，请使用`/r`改为开关与命令`shutdown /r /t 0`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-212">To restart the device, use the `/r` switch instead with the command `shutdown /r /t 0`.</span></span>

### <a name="viewing-and-changing-display-settings"></a><span data-ttu-id="61c1f-213">**查看和更改显示设置**</span><span class="sxs-lookup"><span data-stu-id="61c1f-213">**Viewing and changing display settings**</span></span>
<span data-ttu-id="61c1f-214">可能使用 SetDisplayResolution 工具，用于列出当前的显示设置和显示的支持的值的列表。</span><span class="sxs-lookup"><span data-stu-id="61c1f-214">The SetDisplayResolution tool may be used for listing the current display settings and to show the list of supported values.</span></span>  <span data-ttu-id="61c1f-215">它可以进一步使用调整显示器的分辨率、 刷新频率和/或为你的平台支持的值的方向。</span><span class="sxs-lookup"><span data-stu-id="61c1f-215">It can further be used for adjusting the display's resolution, refresh rate and/or orientation to values supported by your platform.</span></span>  <span data-ttu-id="61c1f-216">该实用程序接受以下的命令行参数：</span><span class="sxs-lookup"><span data-stu-id="61c1f-216">The utility accepts the following command line arguments:</span></span>

* <span data-ttu-id="61c1f-217">`SetDisplayResolution` 列出了当前显示 resoltuion。</span><span class="sxs-lookup"><span data-stu-id="61c1f-217">`SetDisplayResolution` Lists the current display resoltuion.</span></span>
* <span data-ttu-id="61c1f-218">`SetDisplayResolution -list` 列出支持的显示分辨率。</span><span class="sxs-lookup"><span data-stu-id="61c1f-218">`SetDisplayResolution -list` Lists supported display resolutions.</span></span>
* <span data-ttu-id="61c1f-219">`SetDisplayResolution -orientation:[n]` 更改显示方向，其中 n = 0、 90、 180 或 270。</span><span class="sxs-lookup"><span data-stu-id="61c1f-219">`SetDisplayResolution -orientation:[n]` Change the display orientation, where n=0,90,180 or 270.</span></span>
* <span data-ttu-id="61c1f-220">`SetDisplayResolution [width] [height]` 更改宽度和高度 （像素）</span><span class="sxs-lookup"><span data-stu-id="61c1f-220">`SetDisplayResolution [width] [height]` Change the width and height in pixels</span></span> 
* <span data-ttu-id="61c1f-221">`SetDisplayResolution [width] [height] [refreshrate]` 更改宽度、 高度和刷新率的宽度和高度位于像素和 refreshrate hz</span><span class="sxs-lookup"><span data-stu-id="61c1f-221">`SetDisplayResolution [width] [height] [refreshrate]` Change width, height and refresh rate where width and height are in pixels and refreshrate in Hz</span></span> 
* <span data-ttu-id="61c1f-222">`SetDisplayResolution [width] [height] [refreshrate] [orientation]` 更改宽度、 高度、 refreshrate 和屏幕方向的宽度和高度均以像素为单位，在 Hz refreshrate 和方向是 0、 90、 180 或 270 之一。</span><span class="sxs-lookup"><span data-stu-id="61c1f-222">`SetDisplayResolution [width] [height] [refreshrate] [orientation]` Change width, height, refreshrate and screen orientation where width and height are in pixels, refreshrate in Hz and orientation is one of 0, 90, 180 or 270.</span></span>

### <a name="take-screenshot"></a><span data-ttu-id="61c1f-223">**拍摄的屏幕快照：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-223">**Take screenshot:**</span></span>

<span data-ttu-id="61c1f-224">使用可用来拍摄 Windows IoTCore 设备的屏幕截图`ScreenCapture.exe`。</span><span class="sxs-lookup"><span data-stu-id="61c1f-224">You can take the screenshot of your Windows IoTCore device by using `ScreenCapture.exe`.</span></span> <span data-ttu-id="61c1f-225">例如，运行`ScreenCapture c:\folder\screencap.jpg`将屏幕截图并将其保存在 screencap.jpg 文件中。</span><span class="sxs-lookup"><span data-stu-id="61c1f-225">For example, run `ScreenCapture c:\folder\screencap.jpg` will take the screenshot and save it in screencap.jpg file.</span></span>

### <a name="get-information-about-network-adapters"></a><span data-ttu-id="61c1f-226">**获取有关网络适配器的信息：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-226">**Get information about Network Adapters:**</span></span>

<span data-ttu-id="61c1f-227">若要查看所有可用的网络适配器的列表，请运行`GetAdapterInfo`工具。</span><span class="sxs-lookup"><span data-stu-id="61c1f-227">To view the list of all the available network adapters, run `GetAdapterInfo` tool.</span></span>

### <a name="set-folder-permissions-for-uwp-apps"></a><span data-ttu-id="61c1f-228">**设置适用于 UWP 应用的文件夹权限：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-228">**Set folder permissions for UWP apps:**</span></span>

<span data-ttu-id="61c1f-229">在设备上的不是所有文件夹都是通过通用 Windows 应用的访问。</span><span class="sxs-lookup"><span data-stu-id="61c1f-229">Not all folders on your device are accesible by Universal Windows Apps.</span></span> <span data-ttu-id="61c1f-230">若要对 UWP 应用进行文件夹访问，可以使用`FolderPermissions`工具。</span><span class="sxs-lookup"><span data-stu-id="61c1f-230">To make a folder accesible to a UWP app, you can use `FolderPermissions` tool.</span></span> <span data-ttu-id="61c1f-231">例如运行`FolderPermissions c:\test -e`要提供 UWP 应用访问权限`c:\test`文件夹。</span><span class="sxs-lookup"><span data-stu-id="61c1f-231">For example run `FolderPermissions c:\test -e` to give UWP apps access to `c:\test` folder.</span></span> <span data-ttu-id="61c1f-232">请注意这会仅使用本机 Win32 api，可用于例如。</span><span class="sxs-lookup"><span data-stu-id="61c1f-232">Note this will work only with native Win32 apis for eg.</span></span> <span data-ttu-id="61c1f-233">CreateFile2 而不能使用 WinRT api，如 StorageFolder，StorageFile 等。</span><span class="sxs-lookup"><span data-stu-id="61c1f-233">CreateFile2 and not with WinRT apis like StorageFolder, StorageFile etc.</span></span>

### <a name="work-with-serial-ports"></a><span data-ttu-id="61c1f-234">**使用串行端口：**</span><span class="sxs-lookup"><span data-stu-id="61c1f-234">**Work with Serial Ports:**</span></span>
<span data-ttu-id="61c1f-235">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm)使您可以使用命令行中的串行端口。</span><span class="sxs-lookup"><span data-stu-id="61c1f-235">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) allows you to work with serial ports from the command line.</span></span> <span data-ttu-id="61c1f-236">它作为 ms iot 示例存储库中的示例项目提供。</span><span class="sxs-lookup"><span data-stu-id="61c1f-236">It is provided as a sample project in the ms-iot samples repo.</span></span> 

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


