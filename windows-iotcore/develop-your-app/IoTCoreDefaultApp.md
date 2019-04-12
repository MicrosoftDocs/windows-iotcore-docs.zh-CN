---
title: Windows 10 IoT 核心版默认应用程序
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: 了解有关 Windows 10 IoT Core 默认的应用及其功能。
keywords: windows iot、 windows 10 iot 核心版，默认的应用
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510645"
---
# <a name="windows-10-iot-core-default-app-overview"></a>Windows 10 IoT 核心版默认应用程序概述

> [!TIP]
> 如果你想要发现某项功能添加到此示例应用，找到[提出问题](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)GitHub，让我们了解上。 如果你想要提交 bug，按照说明在反馈中心[此处](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT)。

当最初 flash Windows 10 IoT 核心版时，你将看到与 Windows 10 IoT Core 默认应用程序启动后，其外观如下所示：

![IoT 核心版默认应用的屏幕截图](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

此应用程序的目的不是仅为你提供友好的外壳程序，以便与当你首次启动 Windows 10 IoT 核心版，但我们已进行开源此应用程序的代码[此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)，以便您可以插有了这些自定义应用程序的功能。

本文将为您提供的不同功能的 Windows 10 IoT Core 默认应用还提供了如何为自己的应用程序可以利用这些不同的功能的简要介绍。

## <a name="leveraging-the-iot-core-default-app"></a>利用 IoT 核心版默认应用 

> [!IMPORTANT]
> 请不要将 maker 映像用于商品化。 如果 commercializing 设备，则必须使用自定义 FFU 为获得最佳安全性。 在[此处](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。

可自定义 IoT Core 默认应用和扩展，或为你自己的应用使用作为示例的源代码。 若要尝试此操作为自己，下载我们的示例的 zip 文件或签出代码 IoT Core 默认应用[此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)。 对于任何问题，请记录相应的问题上我们的示例存储库[此处](https://github.com/Microsoft/Windows-iotcore-samples/issues)。

如中所示[设置部分](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
)下面，在某些情况下，您可能会配置默认设置和功能在客户系统上代表最终用户。 但是，如果您启用这些设置和功能在默认情况下，或如果诊断是上述基本设置，则必须：

* 通知最终用户，这些功能已启用，并向最终用户提供指向 Microsoft 的隐私声明 web 页的链接[此处](http://go.microsoft.com/fwlink/?LinkId=521839)。 
* 从相关的最终用户，默认情况下，（根据需要在适用法律） 启用此类功能安全许可。
* 向最终用户能够返回到基本设置更改诊断设置。
* 如果启用 Microsoft 帐户，并且如果最终用户中删除 Microsoft 帐户具有对最终用户数据的访问，必须启用将要同时删除的设备上的所有最终用户的 Microsoft 帐户数据。 

## <a name="out-of-box-experience-oobe"></a>开箱体验 (OOBE)

原因是它获得精益化 IoT Core 默认应用程序的开箱体验。 第一个页面将要求提供默认语言和 wi-fi 设置。 从此处，为了使您的应用程序才能符合 GDPR 必须必须诊断数据屏幕，并且，如果您计划跟踪的位置，你将需要也有一个位置的权限屏幕。 这两者的示例如下所示。 

![位置设置为 OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![OOBE 的诊断设置](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a>命令栏
在命令栏是持久性 horizonatal 栏位于屏幕的底部。 这可轻松访问以下功能：
- 向前和向后的页导航
- 无需离开当前页面的基本设备信息
- 打开或关闭全屏幕模式
- 提前快捷方式
- 特定页的按钮

在命令栏中，有许多按钮，这些按钮有时可能会令人困惑的还是隐藏。 若要展开命令栏和访问这些按钮，请在右下方按菜单按钮：

![如何扩展命令栏](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a>播放开始菜单-

开始菜单是大多数插功能所在。

### <a name="weather"></a>天气
使用国家/地区的天气服务中的数据，天气页面会呈现天气信息在你的当前位置。

### <a name="web-browser"></a>Web 浏览器
Web 浏览器，可从 web 大多数站点中请求。

### <a name="music"></a>音乐
此页将在播放 MP3 和 WAV 文件**音乐库**，可通过访问[Windows Device Portal](../manage-your-device/DevicePortal.md)。  若要将文件上传到音乐播放机，将需要以导航到 Windows Device Portal，单击"应用"下拉列表中，导航到"文件资源管理器"，选择"音乐"从此处将文件上传。


![如何将音乐文件上传](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a>“幻灯片放映”
此页面将显示从任何 PNG 或 JPEG 图像文件**图片库**，可通过访问[Windows Device Portal](../manage-your-device/DevicePortal.md)。 若要将图像上载到幻灯片放映中，将需要以导航到 Windows Device Portal，单击"应用"下拉列表中，导航到"文件资源管理器"，选择"图片"从此处将文件上传。


![如何将音乐文件上传](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a>Draw
此页可以查看 Windows 10 IoT Core 的墨迹功能测试。

## <a name="start-menu---explore"></a>开始菜单-浏览 

### <a name="apps"></a>应用 
此页可以启动设备上安装其他前台应用程序。 启动应用程序将挂起 IoT Core 默认应用，可以使用应用程序管理器中重新启动该应用[Windows Device Portal](../manage-your-device/DevicePortal.md)。

没有任何特殊需要能够在页中，只需列出前台应用程序[安装](AppInstaller.md)或[部署](AppDeployment.md)应用程序。 成功安装或部署之后, 重新导航到应用程序页面以刷新应用程序的列表。

请注意，有几个自动生成 OS 相关的我们筛选出的应用程序，则可以找到应用名称的列表[此处](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)。

### <a name="notifications"></a>通知
此页将列出在过去 20 IoT Core 默认应用程序启动以来的通知。 当 IoT Core 默认应用在调试模式下运行时，这会创建测试通知添加按钮。

### <a name="logs"></a>日志
此页将列出任何自动生成崩溃或错误日志，然后可以从设备和分析。

### <a name="github"></a>GitHub
此页将转到 IoT Core 默认应用程序代码的开放源代码 GitHub 位置。

## <a name="start-menu---windows-device-portal"></a>开始菜单-Windows Device Portal

在本部分页面可利用 Windows Device Portal REST Api，这要求使用 Windows Device Portal 凭据进行登录。

## <a name="device-information"></a>设备信息

此页可以查看你的设备包括以太网、 OS 版本、 已连接的设备、 和的详细信息的不同功能。

## <a name="command-line"></a>命令行

此页，可直接在你的设备上运行命令。

若要启用此功能需要设置注册表项，以便应用程序可以运行命令。 第一次尝试运行一个命令将看到一个链接，可以设置使用 Windows Device Portal 调用的注册表项。 单击链接以启用你的设备以运行命令。

某些命令需要管理员访问权限。 出于安全考虑该应用使用非管理员帐户默认情况下运行命令。 如果需要以管理员身份运行命令可以键入"RunAsAdmin <your command>"在命令行提示符下。

## <a name="settings"></a>设置
你可以配置大量设置此处包括的 Wi-fi、 蓝牙、 电源选项和的详细信息。

### <a name="app-settings"></a>应用设置
**应用设置**部分允许您在应用程序配置页的各种设置。  

下面是一些你可以自定义的设置：

##### <a name="general-settings"></a>常规设置
* 设置显示应用程序启动时的默认页
* 启用/禁用屏幕保护程序

##### <a name="weather-settings"></a>天气设置
* 更改位置
  > 你提供一个有效才会启用此功能[必应地图服务令牌](https://msdn.microsoft.com/library/ff428642.aspx)。  若要将令牌传递给应用程序，创建**MapToken.config** LocalState 文件夹中的应用程序文件 (例如 C:\Data\USERS\\[User Account] \AppData\Packages\\[包的完整名称] \LocalState\MapToken.config) 并重新启动该应用程序。
* 展开代码图
* 启用/禁用映射翻转，以便将地图和天气交换机定期的放置以防止屏幕刻录中

##### <a name="web-browser-settings"></a>Web 浏览器设置
* 为 Web 浏览器设置主页页面

##### <a name="slideshow-settings"></a>幻灯片放映设置
* 设置幻灯片放映间隔

##### <a name="appearance"></a>外观
* MDL2 资产而不是表情符号用于磁贴图标
* 设置磁贴宽度和高度
* 设置 UI 缩放-默认情况下自动缩放设置
* 设置磁贴颜色

#### <a name="system"></a>系统
更改语言、 键盘布局和时区。

#### <a name="network--wi-fi"></a>网络和 Wi-fi
查看网络适配器属性或连接到可用的 Wi-fi 网络。

#### <a name="bluetooth"></a>蓝牙
与蓝牙设备配对。

#### <a name="app-updates"></a>应用更新
检查应用更新或更改自动更新设置。

#### <a name="power-options"></a>电源选项
重新启动或关闭设备。

#### <a name="diagnostics"></a>诊断
选择你想要提供 Microsoft 的诊断数据量。  我们鼓励用户选择加入**完整**使我们能够快速诊断问题并可对该产品的改进的诊断数据。

##### <a name="basic"></a>基本 
发送有关你的设备、 其设置和功能，仅信息是否正确执行。

##### <a name="full"></a>完全
发送所有基本的诊断数据，以及了解你浏览的网站以及如何使用应用程序和功能，外加有关设备运行状况、 设备活动和增强的错误报告的其他信息。

#### <a name="location"></a>位置
允许或拒绝对你的位置的应用程序访问权限。
