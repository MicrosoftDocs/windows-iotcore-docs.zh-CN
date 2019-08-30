---
title: 2018年4月更新-版本17134
author: saraclay
ms.author: saclayt
ms.date: 05/01/2018
ms.topic: article
description: 了解适用于 Windows 10 IoT 的2018年4月更新版中的新增功能。
keywords: Windows IoT, 2018 年4月更新, 发行说明
ms.openlocfilehash: b61ee94651c2bea0ec0582669b62867d47c85a0c
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167435"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>适用于 Windows 10 IoT 的2018年4月更新发行说明
内部版本号17134。 2018 年 5 月

Windows 10 IoT 允许开发嵌入或专用设备, 并且是为为智能设备构建 Windows 解决方案的 Oem 和开发人员选择的。

本文档提供了有关此版本的 Windows 10 IoT 的补充其他内容和文档的信息。

## <a name="privacy-statement"></a>隐私声明

可以在[https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)中查看此版本 Windows 操作系统的隐私声明。

## <a name="whats-new-in-april-2018-update"></a>2018年4月更新中的新增功能
* [Visual studio 15.6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support)附带的[Visual studio 测试平台](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/)现在支持 Windows 10 IoT Core 上的测试。 当在面向 Windows 10 IoT Core 的 Visual Studio 2017 中编写项目的[单元测试](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)时, 开发人员现在可以直接从 Visual studio 在设备上远程执行这些单元测试, 而无需将测试部署到设备并手动运行。
* 开发人员可以利用 windows 10 IoT 上[WINDOWS AI 平台](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/)中的功能来创建更多智能设备, 并使用 CPU 或 GPU 加速 ML 模型评估。
* 希望使启用语音的设备快速投放市场的 Oem 可以使用[Cortana 设备 SDK 的预览](http://www.aka.ms/cortanadevices)将 cortana 支持集成到其设备中。
* Oem 可以利用 Windows 上提供的丰富 Csp 集, 使用[Azure IoT 设备管理](https://github.com/ms-iot/iot-core-azure-dm-client), 大规模地对设备进行远程配置和管理。 这一新的示例实现结合了本地客户端、云服务和管理门户, 使 IoT 操作员可以在云规模下执行设备管理。
* 在此版本中, 你可以编写在控制台主机 (例如命令控制台或 PowerShell) 中运行的[UWP 控制台应用](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)。 UWP 控制台应用还可以使用适用于 UWP 应用的 Win32 Api, 并可通过 Microsoft Store 进行发布和更新。
* 我们已添加 IoT Core 的新[Miracast 功能包](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast)以及一[组强制转换 api](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) , 使设备能够充当 Miracast 发送器或接收方。
* 我们添加了对[蓝牙 A2DP-SRC](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth)配置文件的支持, 该配置文件允许设备充当蓝牙流式处理的音频源, 包括使用 AVRCP 配置文件的蓝牙的远程控制功能。
* 在此版本中, 我们最流行的 Qualcomm 板 (DragonBoard 410c) 已变得更加容易。 使用最新版本的[Windows 10 IoT 核心仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard), 只需连接板, 使其进入闪光模式, 然后直接从仪表板[快速刷新设备](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice)。
* 对于查找和连接到 WiFi 网络, 我们更新了[Wifi 连接器示例](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS), 使其与先前已弃用的 netcmd 命令相同。 此示例使用[WiFiAdapter api](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter)来管理无线网络连接和适配器。
* 我们提供了新的与时间相关的 Api, 用于根据设备位置自动将系统时钟设置为[本地时间](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime)和[时区](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_), 使 oem 能够创建更简洁的全新体验。
* 我们有新的语言 Api 用于设置首选用户[语言](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__)、[区域](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_)、默认[语音](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync)语言和默认[语音](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync)。
* 使用新的[MTP 功能包](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md), 你可以使用媒体传输协议 (MTP) 在 Windows 10 IoT Core 设备之间传输文件。 这包括位于设备内部存储和 SD 卡上的文件 (如果存在)。
* 我们已[在 GitHub](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients)和第[9 频道视频](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central)上发布了一个新示例, 演示了如何轻松地将 Windows 10 IoT 设备集成到 Azure IoT Central 中。 我们还更新了文档, 介绍如何将运行 Windows 10 IoT Core 的[设备连接](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore)到 Azure IoT Central。

## <a name="improvements-in-assigned-access"></a>已分配的访问的改进
* 我们为数字告示用例添加了对多个屏幕的支持。
* "注册状态" 页现在包括在输入分配的访问权限之前确保在设备上强制所有 MDM 配置的功能。
* 除了现有的 UWP 应用商店应用外, 我们还增加了配置和运行 Shell 启动器的能力。
* 使用已分配的访问权限的设备可以配置为在重启后自动输入所需状态, 并使用简化的过程来创建和配置自动登录帐户。
* 对于多用户设备, 你现在可以为 Azure AD 组或 Active Directory 组分配不同的已分配访问配置, 而不是指定每个用户。
* 如果分配的访问权限配置的应用有问题，为了帮助解决问题，现在可以查看生成的错误报告。

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>用于开发和测试方案的预览功能
* 设备更新中心 [预览] 允许 Oem 全局管理其应用并将操作系统、应用、设置和文件的更新推送到设备, 以使其保持最新和安全。
* 支持在 Windows 10 IoT 核心版和企业版的64位版本上托管[Nano Server 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/index), 使应用程序及其数据可以相互隔离, 并从开发到生产或云到边缘快速移动。
* Windows 设备运行状况证明 [预览] 服务使用硬件功能和云服务根据硬件级别的指标和证明数据提供对设备运行状况的篡改和远程认证。
* Windows IoT [预览版] 上的[Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/)允许 IoT 解决方案协调云和边缘设备之间的智能, 以确保应用程序和服务可以在最有意义的地方处理 IoT 数据。
* Azure IoT 中心[设备预配服务 [预览版]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/)支持在制造期间使用公用映像创建 Windows 10 IoT 设备, 并将其配置为在首次启动时自动连接到 Azure IoT 中心以检索特定于设备的设置信息.

## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT 核心参考映像
___ 
* Minnowboard Max
  * 处理器：Intel Atom E3825
  * 体系结构: x86

* Raspberry Pi 3 模型 B
  * 处理器：Broadcom BCM2837
  * 体系结构：ARM

* DragonBoard 410c
  * 处理器：Qualcomm Snapdragon 410
  * 体系结构：ARM
  * BSP 版本:2120.0.0.0

## <a name="additional-information"></a>其他信息
* 根据最新的 Intel 公告, 停止产生 Intel Joule 平台, 在以前的版本中, 将不再支持 Intel Joule 的 FFUs。 评估 Intel Joule 的客户应该使用其他受支持的 Soc 之一来识别替代平台-请参阅[建议的板和列表 soc](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards) 。

## <a name="known-issues"></a>已知问题
* 不能在 Windows 10 IoT 核心版上通过 Visual Studio 进行 F5 驱动程序部署。 必须手动复制驱动程序并将其注册到设备上。
* 通过 NOOBS 安装的设备不能运行 bcdedit 工具来启用内核调试程序。
* Windows IoT 远程客户端不适用于 Raspberry Pi。 使用带加速图形的板（例如 Minnowboard Max 或 Dragonboard），或者连接一个用于本地显示的监视器。
