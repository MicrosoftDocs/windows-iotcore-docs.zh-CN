---
title: Windows 10 IoT 核心版默认应用
ms.date: 08/08/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 阅读有关默认Windows 10 IoT 核心版的概述。 获取有关 OOBE (、命令) 菜单等的开箱即用体验的信息。
keywords: windows iot， windows 10 iot 核心， 默认应用
ms.custom: RS5
ms.openlocfilehash: 02b24ec4f37f7ce2c212581cfe13ef740cd2ec01
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229053"
---
# <a name="windows-10-iot-core-default-app-overview"></a>Windows 10 IoT 核心版默认应用概述
最初刷Windows 10 IoT 核心版时，启动时Windows 10 IoT 核心版默认应用，如下所示：

![IoT 核心默认应用的屏幕截图](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

此应用程序的用途不仅是在首次启动 Windows 10 IoT 核心版 时提供一个友好的 shell 来与之交互，而且我们在此处开放了此应用程序的代码，以便可以在你自己的自定义应用程序 () [](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)上即插即用这些功能。

本文将提供默认应用提供Windows 10 IoT 核心版功能，以及如何为你自己的应用程序利用这些不同功能。

## <a name="leveraging-the-iot-core-default-app"></a>利用 IoT 核心默认应用

> [!IMPORTANT]
> 请勿将创客映像用于商业化。 若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。 在[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。

可以自定义和扩展 IoT 核心默认应用，也可以将源代码用作自己的应用示例。 若要自己尝试此操作，请下载示例的 zip，或在此处查看 IoT 核心默认应用 [的代码](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)。 如有任何疑问，请在此处的示例[存储库提出问题。](https://github.com/Microsoft/Windows-iotcore-samples/issues)

如下面的设置[部分](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
)所示，在某些情况下，你可以代表最终用户在客户系统上配置默认设置和功能。 但是，如果默认启用这些设置和功能，或者诊断高于基本设置，则必须：

* 通知最终用户这些功能已启用，并在此处向最终用户提供 Microsoft 隐私声明网页 [的链接](https://go.microsoft.com/fwlink/?LinkId=521839)。
* 确保相关最终用户同意在默认情况下启用此类功能 (根据) 。
* 使最终用户能够将诊断设置更改回基本设置。
* 如果启用 Microsoft 帐户并且你有权访问最终用户数据，则如果最终用户删除了 Microsoft 帐户，则必须在设备上同时删除所有最终用户的 Microsoft 帐户数据。

## <a name="out-of-box-experience-oobe"></a>OOBE (开箱) 

IoT 核心默认应用的开箱即用体验非常精简。 前一页将要求提供默认语言和 wi-fi 设置。 若要使应用符合 GDPR，必须具有诊断数据屏幕，并且如果计划跟踪位置，则还需要具有位置权限屏幕。 下面显示了这两者的示例。

![OOBE 的 OOBE ](../media/IoTCoreDefaultApp/OOBE3.jpg)
 ![ 诊断设置的位置设置](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a>命令栏
命令栏是位于屏幕底部的持久水平条。 这样可以轻松访问以下功能：
- 向前和向后页面导航
- 无需离开当前页即可获取基本设备信息
- 打开或关闭全屏模式
- 高级快捷方式
- 特定于页面的按钮

命令栏中有许多按钮，有时这些按钮可能会令人困惑或隐藏。 若要展开命令栏并访问这些按钮，请按右下角的菜单按钮：

![如何展开命令栏](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a>"开始"菜单 - 播放

"开始"菜单是大多数即插即用功能的地方。

### <a name="weather"></a>天气
使用国家天气服务的数据，天气页将在当前位置呈现天气信息。

### <a name="web-browser"></a>Web 浏览器
Web 浏览器允许从 Web 拉取大多数站点。

### <a name="music"></a>Music
此页面将播放来自 音乐 **库中** 的 MP3 和 WAV 文件，这些文件可以通过 [Windows 设备门户。](../manage-your-device/DevicePortal.md)  若要将文件上传到音乐播放器，需要导航到 Windows 设备门户，单击"应用"下拉列表，导航到"文件资源管理器"，选择"音乐"，然后从此处上传文件。


![如何上传音乐文件](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a>幻灯片放映
此页将显示图片库中的任何 PNG 或 JPEG图像文件，这些文件可以通过[Windows 设备门户。](../manage-your-device/DevicePortal.md) 若要将图像上传到幻灯片放映，需要导航到 Windows 设备门户，单击"应用"下拉列表，导航到"文件资源管理器"，选择"图片"，然后从此处上传文件。


![如何上传音乐文件 1](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a>绘制
此页面可用于测试Windows 10 IoT 核心版的墨迹书写功能。

## <a name="start-menu---explore"></a>"开始"菜单 - 浏览

### <a name="apps"></a>应用
通过此页，可以启动设备上安装的其他前台应用程序。 启动应用程序将挂起 IoT 核心默认应用，可通过在 Windows 设备门户 中[重新启动](../manage-your-device/DevicePortal.md)。

只需安装或部署应用程序，就不需要在页面中列出前台[应用程序。](AppInstaller.md) [](AppDeployment.md) 成功安装或部署后，重新导航到"应用"页以刷新应用程序列表。

请注意，我们筛选出几个自动生成的与 OS 相关的应用程序，可在此处找到应用 [名称列表](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)。

### <a name="notifications"></a>通知
此页将列出自 IoT 核心默认应用启动以来过去 20 个通知。 当 IoT 核心默认应用在调试模式下运行时，将添加用于创建测试通知的按钮。

### <a name="logs"></a>日志
此页将列出任何自动生成的崩溃或错误日志，这些日志随后可关闭设备并进行分析。

### <a name="github"></a>GitHub
此页将你访问 IoT 核心GitHub应用代码的开源应用位置。

## <a name="start-menu---windows-device-portal"></a>"开始"菜单 - Windows 设备门户

本部分中的页面利用 Windows 设备门户 REST API，这些 API 要求使用 Windows 设备门户 凭据登录。

## <a name="device-information"></a>设备信息

此页允许查看设备的不同功能，包括以太网、OS 版本、连接的设备等。

## <a name="command-line"></a>命令行

此页允许你直接在设备上运行命令。

若要启用此功能，必须设置注册表项，以便应用可以运行命令。 首次尝试运行命令时，将看到一个链接，该链接允许你使用调用 Windows 设备门户。 单击链接，使设备能够运行命令。

某些命令需要管理员访问权限。 出于安全考虑，应用默认使用非管理员帐户来运行命令。 如果需要以管理员角色运行命令，可以在命令行提示符下键入"RunAsAdmin"。 <your command>

## <a name="settings"></a>设置
你将能够在此处配置许多设置，包括 Wi-Fi、蓝牙、电源选项等。

### <a name="app-settings"></a>应用设置
"**应用设置"** 部分允许为应用中的页面配置各种设置。  

可以自定义的一些设置包括：

##### <a name="general-settings"></a>常规设置
* 设置启动应用时显示的默认页面
* 启用/禁用屏幕保护程序

##### <a name="weather-settings"></a>天气设置
* 更改位置
  > 只有在已提供有效的映射服务令牌[必应，才启用此功能](https://msdn.microsoft.com/library/ff428642.aspx)。  若要将令牌传递给应用，在应用的 LocalState 文件夹中创建 **MapToken.config** 文件 (例如 C：\Data\Users \\ [用户帐户]\AppData\Local\Packages \\ [包全名]\LocalState\MapToken.config) 并重启应用。  
 (示例：C：\Data\Users\DefaultAccount\AppData\Local\Packages\16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58\LocalState\)
* 展开地图
* 启用/禁用地图翻转，以便地图和天气开关定期放置以防止屏幕被消耗

##### <a name="web-browser-settings"></a>Web 浏览器设置
* 设置 Web 浏览器的主页

##### <a name="slideshow-settings"></a>幻灯片设置
* 设置幻灯片放映间隔

##### <a name="appearance"></a>外观
* 为磁贴图标使用 MDL2 资产而不是表情符号
* 设置图块宽度和高度
* 设置 UI 缩放-默认设置自动缩放
* 设置磁贴颜色

#### <a name="system"></a>系统
更改语言、键盘布局和时区。

#### <a name="network--wi-fi"></a>网络 & Wi-Fi
查看网络适配器属性或连接到可用的 Wi-Fi 网络。

#### <a name="bluetooth"></a>蓝牙
与蓝牙设备配对。

#### <a name="app-updates"></a>应用更新
检查应用更新或更改自动更新设置。

#### <a name="power-options"></a>电源选项
重新启动或关闭设备。

#### <a name="diagnostics"></a>诊断
选择要向 Microsoft 提供的诊断数据量。  我们鼓励用户选择 **完整** 的诊断数据，以便可以快速诊断问题并对产品进行改进。

##### <a name="basic"></a>基本
仅发送有关你的设备的信息、其设置和功能以及它是否正确执行。

##### <a name="full"></a>完整
发送所有基本诊断数据，以及有关浏览的网站以及如何使用应用程序和功能的信息，以及有关设备运行状况、设备活动和增强的错误报告的其他信息。

#### <a name="location"></a>位置
允许或拒绝应用访问你的位置。
