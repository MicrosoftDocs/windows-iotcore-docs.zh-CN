---
title: 2018 年 4 月更新-内部版本 17134
author: saraclay
ms.author: saclayt
ms.date: 05/01/2018
ms.topic: article
description: 了解什么具有新在 2018 年 4 月更新适用于 Windows 10 IoT。
keywords: Windows IoT 2018 年 4 月更新，发行说明
ms.openlocfilehash: b61ee94651c2bea0ec0582669b62867d47c85a0c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510628"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>Windows 10 IoT 的 2018 年 4 月更新版发行说明
内部版本 17134 版本号。 2018 年 5 月

Windows 10 IoT 支持嵌入式或专用用途设备的开发，Oem 和构建智能设备的 Windows 解决方案的开发人员的选择。

本文档提供补充其他内容和文档，了解此版本的 Windows 10 IoT 的信息。

## <a name="privacy-statement"></a>隐私声明

可以在查看此版本的 Windows 操作系统的隐私声明[ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839)。

## <a name="whats-new-in-april-2018-update"></a>什么是 2018 年 4 月中的新增功能更新
* [Visual Studio 测试平台](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/)随[Visual Studio 15.6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support)现在支持在 Windows 10 IoT Core 上测试。 当[编写单元测试](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)的项目面向 Windows 10 IoT 核心版 Visual Studio 2017 中，对于开发人员现在可以执行直接从 Visual Studio 而无需部署到设备的测试设备上远程这些单元测试与手动运行它们。
* 开发人员可以利用中的功能[Windows AI 平台](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/)上 Windows 10 IoT 来创建更智能设备并加速机器学习模型评估使用 CPU 还是 GPU。
* 想要将具有语音功能的设备要快地进入市场的 Oem 可以将 Cortana 支持集成到其设备 using [Cortana 设备 SDK 的预览](http://www.aka.ms/cortanadevices)。
* Oem 可以利用一组丰富的 Csp 提供对 Windows 进行远程配置和使用设备的管理[Azure IoT 设备管理](https://github.com/ms-iot/iot-core-azure-dm-client)。 本地客户端、 云服务和管理门户中，启用 IoT 操作员执行大规模云的设备管理结合了此新的示例实现。
* 使用此版本中，可以编写[UWP 控制台应用](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)控制台主机，如命令控制台或 PowerShell 中运行。 UWP 控制台应用程序还可以使用适用于 UWP 应用的 Win32 Api 和可以发布和更新通过 Microsoft Store。
* 我们添加了新[Miracast 功能包](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast)IoT core 连同[组的强制转换 Api](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting)要使设备能够充当 Miracast 发送器或接收方。
* 我们添加了对[蓝牙 A2DP SRC](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth)通过蓝牙使用 AVRCP 配置文件包括远程控制功能，允许设备充当蓝牙流式处理的音频源的配置文件。
* 我们最受欢迎 Qualcomm 板 DragonBoard 410 c 之一已成为闪烁，此版本中容易得多。 使用最新版[Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)，只需将开发板连接，将其放到闪存模式，并[闪存设备](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice)直接从仪表板。
* 用于查找和连接到 WiFi 网络，我们已更新[WiFi 连接器示例](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS)要与相媲美的 netcmd 命令已被弃用。 此示例使用[WiFiAdapter Api](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter)来管理无线网络连接和适配器。
* 我们会自动将系统时钟设置为具有与时间相关的新 Api[本地时间](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime)并[时区](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_)基于设备的位置，使 Oem 可以创建更流畅全新安装体验。
* 我们设置首选的用户有新的语言 Api[语言](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__)，[区域](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_)，默认[语音](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync)语言和默认[语音](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync)。
* 有一个新[MTP 功能包](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md)，可以通过 USB 使用媒体传输协议 (MTP) 传输到和从 Windows 10 IoT Core 设备的文件。 这包括位于设备的内部存储和 SD 卡上，如果存在的文件。
* 我们发布了一个新[GitHub 上的示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients)并[第 9 频道视频](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central)显示获取 Windows 10 IoT 多么设备集成到 Azure IoT 中心。 我们还更新了我们的文档来描述[如何将设备连接](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore)到 Azure IoT Central 运行 Windows 10 IoT Core。

## <a name="improvements-in-assigned-access"></a>已分配的访问中的改进
* 我们添加了对数字签名用例的多个屏幕。
* 注册状态页现在包含的功能，以确保之前输入分配的访问设备上强制使用所有 MDM 配置。
* 我们已添加了配置和运行 Shell 启动程序，除了现有的 UWP 应用商店应用程序的功能。
* 使用已分配的访问的设备可以配置为自动重新启动用于创建和配置自动登录帐户使用的简化的过程后输入所需的状态。
* 对于多个用户的设备，而不是指定每个用户，现可以将不同的已分配的访问配置分配给 Azure AD 组或 Active Directory 组。
* 如果分配的访问权限配置的应用有问题，为了帮助解决问题，现在可以查看生成的错误报告。

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>对于开发和测试方案的预览版功能
* 设备更新中心 [预览] 使 Oem 可以全局管理他们的应用并将更新的操作系统、 应用、 设置和文件从云中推送到设备以使它们保持最新和安全。
* 支持托管[Nano Server 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/index)上的 Windows 10 IoT 核心版和企业版 64 位版本，使应用程序和其数据能相互隔离和快速移动从开发到生产环境或云到边缘。
* Windows 设备运行状况证明 [预览] 服务使用的硬件功能和云服务提供防篡改攻击和远程证明的设备运行状况根据硬件级别的度量值和已证明数据。
* [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) Windows IoT 上 [预览] 允许 IoT 解决方案来协调云和边缘设备，以确保应用程序和服务可以处理 IoT 数据最有利位置之间的智能。
* Azure IoT 中心[设备预配服务 [预览]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/)使在制造期间使用的通用映像创建和配置为自动连接到 Azure IoT 中心检索的第一次启动在 Windows 10 IoT 设备特定于设备的设置信息。

## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT 核心版参考映像
___ 
* Minnowboard Max
  * 处理器：Intel Atom E3825
  * 体系结构： x86

* Raspberry Pi 3 机型 B
  * 处理器：Broadcom BCM2837
  * 体系结构：ARM

* DragonBoard 410c
  * 处理器：Qualcomm Snapdragon 410
  * 体系结构：ARM
  * BSP 版本：2120.0.0.0

## <a name="additional-information"></a>其他信息
* 根据最新的 Intel 公告，停止生成 Intel Joule 平台，为 Intel Joule FFUs 将已停止使用在以前的版本。 评估 Intel Joule 客户应确定一种替代方法使用的另一个平台支持 Soc-请参阅[建议的看板和 Soc](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards)的列表。

## <a name="known-issues"></a>已知问题
* 从 Visual Studio 的 F5 驱动程序部署不适用于 Windows 10 IoT Core。 驱动程序必须手动复制并在设备上注册。
* 通过 NOOBS 安装的设备不能运行 bcdedit 工具来启用内核调试程序。
* Windows IoT 远程客户端并不适用于 Raspberry Pi。 使用如 Minnowboard 最大或 Dragonboard 加速图形使用看板或附加的本地显示的监视器。
