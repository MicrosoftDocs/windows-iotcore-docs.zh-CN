---
title: Windows 10 IoT Core 默认应用
ms.date: 08/08/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 阅读有关 Windows 10 IoT Core 默认应用的概述。 获取有关 (OOBE) 、命令栏、开始菜单等的全新体验的信息。
keywords: windows iot，windows 10 iot core，默认应用
ms.custom: RS5
ms.openlocfilehash: b24c7a269627b4b9f118f9dc3da183889470292d
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656373"
---
# <a name="windows-10-iot-core-default-app-overview"></a>Windows 10 IoT Core 默认应用概述

> [!TIP]
> 如果你发现想要查看已添加到此示例应用的功能，请在 GitHub 上提出 [问题](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) ，让我们知道。 如果你想要提交 bug，请按照 [此处](https://social.msdn.microsoft.com/Forums/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT)的反馈中心的说明进行操作。

初次刷新 Windows 10 IoT Core 时，将在启动时向你显示 Windows 10 IoT Core 默认应用，如下所示：

![IoT Core 默认应用的屏幕截图](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

此应用程序的目的不仅是为了让你在首次启动 Windows 10 IoT Core 时，为你提供与交互的友好 shell，但我们在 [此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) 提供了此应用程序的代码，以便你可以在自己的自定义应用程序 () 上插入和使用这些功能。

本文将为你提供 Windows 10 IoT Core 默认应用提供的不同功能的说明，以及你可以如何对自己的应用程序使用这些不同功能。

## <a name="leveraging-the-iot-core-default-app"></a>利用 IoT 核心默认应用

> [!IMPORTANT]
> 请勿将创客映像用于商业化。 若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。 在[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。

IoT Core 默认应用可进行自定义和扩展，也可将源代码用作你自己的应用的示例。 若要亲自尝试此问题，请下载我们的示例的 zip，或在 [此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)查看 IoT Core 默认应用的代码。 如有任何问题，请在 [此处](https://github.com/Microsoft/Windows-iotcore-samples/issues)提出有关示例存储库的问题。

如下面的 [设置部分](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) 中所示，在某些情况下，你可以代表最终用户配置客户系统上的默认设置和功能。 但是，如果在默认情况下启用这些设置和功能，或者诊断高于 "基本" 设置，则必须执行以下操作：

* 通知最终用户这些功能已启用，并向最终用户提供 [此处](https://go.microsoft.com/fwlink/?LinkId=521839)指向 Microsoft 隐私声明网页的链接。
* 根据适用法律) 的要求，在默认情况下启用此类功能，以确保基于相关最终用户的许可 (。
* 向最终用户提供将诊断设置更改回 "基本" 设置的能力。
* 如果你启用 Microsoft 帐户，并且你有权访问最终用户数据，则在最终用户删除 Microsoft 帐户后，你必须在设备上启用所有最终用户的 Microsoft 帐户数据的同时删除。

## <a name="out-of-box-experience-oobe"></a> (OOBE) 的全新体验

IoT 核心默认应用的全新体验在获取时与之相关。 第一页将要求提供默认语言和 wi-fi 设置。 从这里开始，你的应用程序必须与 GDPR 兼容，你必须有一个诊断数据屏幕，并且如果你计划跟踪位置，则还需要具有位置权限屏幕。 下面显示了二者的示例。

![OOBE 的 OOBE ](../media/IoTCoreDefaultApp/OOBE3.jpg)
 ![ 诊断设置的位置设置](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a>命令栏
命令栏是位于屏幕底部的持久性水平条。 这样就可以轻松访问以下功能：
- 前进和后退页面导航
- 基本设备信息，无需离开当前页面
- 打开或关闭全屏模式
- 前进快捷方式
- 页面特定按钮

命令栏中有许多按钮，有时这些按钮可能会令人费解或隐藏。 若要展开命令栏并访问这些按钮，请按下右端的菜单按钮：

![如何展开命令栏](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a>开始菜单-播放

"开始" 菜单是最活跃的即插即用功能。

### <a name="weather"></a>天气
使用国家天气服务中的数据，天气页面将在你的当前位置呈现天气信息。

### <a name="web-browser"></a>Web 浏览器
通过 web 浏览器，你可以从 web 中提取大多数站点。

### <a name="music"></a>Music
此页面将从 " **音乐库**" 播放 MP3 和 WAV 文件，可以通过 [Windows 设备门户](../manage-your-device/DevicePortal.md)访问这些文件。  若要将文件上传到音乐播放机，你需要导航到 Windows 设备门户，单击 "应用" 下拉列表，导航到 "文件资源管理器"，选择 "音乐"，然后上传文件。


![如何上传音乐文件](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a>幻灯片放映
此页将显示 " **图片库**" 中的任何 PNG 或 JPEG 图像文件，可以通过 [Windows 设备门户](../manage-your-device/DevicePortal.md)进行访问。 若要将图像上传到幻灯片，你将需要导航到 Windows 设备门户，单击 "应用" 下拉列表，导航到 "文件资源管理器"，选择 "图片"，然后上传文件。


![如何上传音乐文件1](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a>绘制
此页面允许你测试 Windows 10 IoT Core 的墨迹功能。

## <a name="start-menu---explore"></a>开始菜单-浏览

### <a name="apps"></a>应用
此页面允许你启动在设备上安装的其他前台应用程序。 启动应用程序将挂起 IoT Core 默认应用，可通过在 [Windows 设备门户](../manage-your-device/DevicePortal.md)中使用应用管理器变该应用。

不需要任何特殊内容即可在页面中列出前景应用程序，只需 [安装](AppInstaller.md) 或 [部署](AppDeployment.md) 应用程序即可。 成功安装或部署后，请重新导航到 "应用" 页，刷新应用程序列表。

请注意，我们筛选掉了几个自动生成的与 OS 相关的应用程序，可以在 [此处](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)找到应用名称的列表。

### <a name="notifications"></a>通知
此页将列出过去20个通知，因为 IoT Core 默认应用已启动。 当 IoT 核心默认应用在调试模式下运行时，将添加用于创建测试通知的按钮。

### <a name="logs"></a>日志
此页将列出所有自动生成的崩溃或错误日志，然后可以将其移出设备并进行分析。

### <a name="github"></a>GitHub
此页将转到 IoT Core 默认应用代码的开源 GitHub 位置。

## <a name="start-menu---windows-device-portal"></a>"开始" 菜单-Windows 设备门户

此部分中的页面利用 Windows 设备门户 REST Api，这要求你使用 Windows 设备门户凭据进行登录。

## <a name="device-information"></a>设备信息

此页面允许你查看设备的不同功能，包括以太网、OS 版本、连接的设备等。

## <a name="command-line"></a>命令行

此页面允许你直接在设备上运行命令。

若要启用此功能，必须设置一个注册表项，以便应用可以运行这些命令。 第一次尝试运行命令时，你将看到一个链接，该链接允许你使用对 Windows 设备门户的调用来设置注册表项。 单击链接以使你的设备能够运行命令。

某些命令需要管理员访问权限。 为了安全起见，默认情况下，应用程序使用非管理员帐户运行命令。 如果需要以管理员身份运行命令，则可以 <your command> 在命令行提示符中键入 "RunAsAdmin"。

## <a name="settings"></a>设置
你将能够在此处配置许多设置，包括 Wi-fi、蓝牙、电源选项等。

### <a name="app-settings"></a>应用设置
" **应用设置** " 部分允许你为应用中的页面配置各种设置。  

您可以自定义的一些设置如下：

##### <a name="general-settings"></a>常规设置
* 设置在应用程序启动时显示的默认页面
* 启用/禁用屏幕保护程序

##### <a name="weather-settings"></a>天气设置
* 更改位置
  > 仅当您提供有效的 [Bing 地图服务令牌](https://msdn.microsoft.com/library/ff428642.aspx)时，才会启用此功能。  若要将令牌传递给应用，请在应用的 LocalState 文件夹中创建 **MapToken.config** 文件 (例如 C:\Data\Users \\ [用户帐户] \AppData\Local\Packages \\ [包全名] \LocalState\MapToken.config) 并重新启动应用。  
 (示例： C:\Data\Users\DefaultAccount\AppData\Local\Packages\16454Windows10IOTCore. IOTCoreDefaultApplication_rz84sjny4rf58 \LocalState\)
* 展开地图
* 启用/禁用地图翻转以便定期放置地图和天气交换机，以防屏幕烧入

##### <a name="web-browser-settings"></a>Web 浏览器设置
* 设置 Web 浏览器的主页

##### <a name="slideshow-settings"></a>幻灯片放映设置
* 设置幻灯片放映间隔

##### <a name="appearance"></a>外观
* 为磁贴图标使用 MDL2 资产而不是表情符号
* 设置图块宽度和高度
* 设置 UI 缩放-默认设置自动缩放
* 设置磁贴颜色

#### <a name="system"></a>系统
更改语言、键盘布局和时区。

#### <a name="network--wi-fi"></a>网络 & Wi-fi
查看网络适配器属性或连接到可用的 Wi-fi 网络。

#### <a name="bluetooth"></a>Bluetooth
与蓝牙设备配对。

#### <a name="app-updates"></a>应用更新
检查应用更新或更改自动更新设置。

#### <a name="power-options"></a>电源选项
重新启动或关闭设备。

#### <a name="diagnostics"></a>诊断
选择要向 Microsoft 提供的诊断数据量。  我们鼓励用户选择 **完整** 的诊断数据，以便可以快速诊断问题并对产品进行改进。

##### <a name="basic"></a>基本
仅发送有关你的设备的信息、其设置和功能以及它是否正确执行。

##### <a name="full"></a>完全
发送所有基本诊断数据，以及有关浏览的网站以及如何使用应用程序和功能的信息，以及有关设备运行状况、设备活动和增强的错误报告的其他信息。

#### <a name="location"></a>位置
允许或拒绝应用访问你的位置。
