---
title: 2018 年 4 月更新 - 版本 17134
ms.date: 05/01/2018
ms.topic: article
description: 了解适用于 Windows 10 IoT 的 2018 年 4 月更新中的新增功能。
keywords: Windows IoT，2018 年 4 月更新，发行说明
ms.openlocfilehash: c33df71d3cbab03f1272d9b9bee0b5107a0c3e23
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782809"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>适用于 Windows 10 IoT 的 2018 年 4 月更新的发行说明
内部版本号 17134。 2018 年 5 月

Windows 10 IoT 支持开发嵌入式设备或专用设备，适合 OEM 和开发人员用来为智能设备构建 Windows 解决方案。

本文档旨在为此版本 Windows 10 IoT 的其他内容和文档提供补充。

## <a name="privacy-statement"></a>隐私声明

如需查看有关此版本 Windows 操作系统的隐私声明，请访问 [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)。

## <a name="whats-new-in-april-2018-update"></a>2018 年 4 月更新的新增功能
* [Visual Studio 15.6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support) 随附的 [Visual Studio 测试平台](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/)现支持在 Windows 10 IoT 核心版上进行测试。 在 Visual Studio 2017 中为面向 Windows 10 IoT 核心版的项目[编写单元测试](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)时，开发人员现在可以直接从 Visual Studio 在设备上远程执行这些单元测试，而无需将测试部署到设备并手动运行。
* 开发人员可以在 Windows 10 IoT 上利用 [Windows AI 平台](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/)的功能来创建更多智能设备，并使用 CPU 或 GPU 加速 ML 模型评估。
* 希望将支持语音的设备快速投放市场的 OEM 可以使用 [Cortana 设备 SDK 预览版](https://www.aka.ms/cortanadevices)将 Cortana 支持集成到这些设备中。
* OEM 可以利用 Windows 上提供的丰富 CSP 集，使用 [Azure IoT 设备管理](https://github.com/ms-iot/iot-core-azure-dm-client)大规模地远程配置和管理设备。 这个新的示例实现结合了本地客户端、云服务和管理门户，因此 IoT 运营商能够以云规模执行设备管理。
* 使用此版本可以编写在控制台主机（例如命令控制台或 PowerShell）中运行的 [UWP 控制台应用](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)。 UWP 控制台应用还可以使用可用于 UWP 应用的 Win32 API，并可通过 Microsoft Store 进行发布和更新。
* 我们为 IoT 核心版添加了新的 [Miracast 功能包](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast)以及[一组强制转换 API](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting)，使设备能够充当 Miracast 发送器或接收器。
* 我们添加了对[蓝牙 A2DP-SRC](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth) 配置文件的支持，以允许设备充当蓝牙流媒体的音频源，包括使用 AVRCP 配置文件通过蓝牙进行远程控制的功能。
* 使用此版本，我们的一款畅销 Qualcomm 主板 DragonBoard 410c 变得更加容易闪存。 使用最新版本的 [Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)，只需连接主板，将其设为闪存模式，然后直接从仪表板[闪存设备](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice)即可。
* 为了查找和连接 WiFi 网络，我们已更新 [WiFi 连接器示例](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS)，使其具有先前已弃用的 netcmd 命令同等的效果。 此示例使用 [WiFiAdapter API](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter) 管理无线网络连接和适配器。
* 我们提供了与时间相关的新 API，用于自动将系统时钟设置为设备位置对应的[本地时间](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime)和[时区](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_)，从而 OEM 能够创建更简洁的开箱即用体验。
* 我们提供了新的语言 API，用于设置首选用户[语言](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__)、[地区](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_)、默认[语音](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync) 语言和默认[语音](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync)。
* 借助新的 [MTP 功能包](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md)，你可以使用媒体传输协议 (MTP) 通过 USB 在 Windows 10 IoT 核心版设备之间来回传输文件。 这包括位于设备内部存储和 SD 卡（若有）上的文件。
* 我们已在 [GitHub](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients) 和 [第 9 频道视频](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central)上发布了新示例，你可以从中了解将 Windows 10 IoT 设备集成到 Azure IoT Central 是多么轻松。 我们还更新了文档，介绍[如何连接运行 Windows 10 IOT 核心版的设备](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore) Azure IoT Central。

## <a name="improvements-in-assigned-access"></a>分配的访问权限中的改进
* 我们增加了对数字标牌用例中多个屏幕的支持。
* “注册状态”页现添加了一项功能，能够确保在输入分配的访问权限之前，在设备上强制执行所有 MDM 配置。
* 除了现有 UWP 应用商店应用之外，我们还添加了用于配置和运行 Shell 启动程序的功能。
* 使用已分配访问权限的设备可以配置为在重新启动后通过一个简化的过程来创建和配置自动登录帐户，以自动进入所需的状态。
* 对于多用户设备，现在可以向 Azure AD 组或 Active Directory 组分配不同的已分配访问权限配置，而不用指定每个用户。
* 为了帮助排查故障，现在当分配的访问权限配置的应用出现问题时，可以查看生成的错误报告。

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>预览版可用于开发和测试场景的功能
* 设备更新中心[预览版]允许 OEM 在全局管理应用并将操作系统、应用、设置和文件的更新从云端推送到设备，以保持更新和保障安全。
* 支持在 64 位 Windows 10 IoT 核心版和企业版上托管 [Nano Server 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/index)，从而实现应用程序及其数据彼此隔离，并快速地从开发环境转到生产环境或从云端转到边缘设备。
* Windows 设备运行状况证明[预览版]服务使用硬件功能和云服务，根据硬件级别的指标和经过证明的数据防止进行篡改操作并远程证明设备的运行状况。
* 借助 Windows IoT [预览版]上的 [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/)，IoT 解决方案能够协调云端和边缘设备之间的信息，以确保应用程序和服务可以最适当地处理 IoT 数据。
* 使用 Azure IoT 中心[设备预配服务[预览版]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/)，可以在制造过程中使用公共映像创建 Windows 10 IoT 设备，并将其配置为在首次启动时自动连接到 Azure IoT 中心，以检索特定于设备的预配信息。

## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT 核心版参考映像
___ 
* Minnowboard Max
  * 处理器：Intel Atom E3825
  * 体系结构：x86

* Raspberry Pi 3 模型 B
  * 处理器：Broadcom BCM2837
  * 体系结构：ARM

* DragonBoard 410c
  * 处理器：Qualcomm Snapdragon 410
  * 体系结构：ARM
  * BSP 版本：2120.0.0.0

## <a name="additional-information"></a>其他信息
* 根据 Intel 关于停止生产 Intel Joule 平台的最新公告，先前的版本将不再提供用于 Intel Joule 的 FFU。 评估 Intel Joule 的客户应找到一种使用其他某种受支持的 SoC 的替代平台，请参阅[建议的主板和 SoC](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards) 以获取相关列表。

## <a name="known-issues"></a>已知问题
* 不能在 Windows 10 IoT 核心版上通过 Visual Studio 进行 F5 驱动程序部署。 必须手动复制驱动程序并在设备上注册。
* 通过 NOOBS 安装的设备不能运行 bcdedit 工具来启用内核调试程序。
* Windows IoT 远程客户端不适用于 Raspberry Pi。 使用带加速图形的板（例如 Minnowboard Max 或 Dragonboard），或者连接一个用于本地显示的监视器。
