---
title: Fall Creators Update - 版本 16299
ms.date: 10/12/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解适用于 Windows 10 IoT 的 Fall Creators Update 的新增功能。
keywords: Windows IoT, Fall Creators Update, 发行说明
ms.openlocfilehash: 09564bafb4356115312ca2c3260eea4f1a852cc3
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91657333"
---
# <a name="fall-creators-update-release-notes-for-windows-10-iot"></a>适用于 Windows 10 IoT 的 Fall Creators Update 的发行说明
内部版本号 16299。 2017 年 10 月

Windows 10 IoT 支持开发嵌入式设备或专用设备，适合 OEM 和开发人员用来为智能设备构建 Windows 解决方案。

本文档旨在为此版本 Windows 10 IoT 的其他内容和文档提供补充。

若要下载此最新内部版本和程序包，请访问 [Windows 预览体验成员下载页面](https://www.microsoft.com/en-us/software-download/windowsiot)。

## <a name="privacy-statement"></a>隐私声明

如需查看有关此版本 Windows 操作系统的隐私声明，请访问 [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)。

## <a name="whats-new-in-fall-creators-update"></a>Fall Creators Update 的新增内容
* [适用于 UWP 应用的 .NET](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx?f=255&mspperror=-2147217396) 是一组可用于使用 C# 或 Visual Basic 生成通用 Windows 平台应用的托管类型，已扩充了 [几千个新 API](https://blogs.msdn.microsoft.com/dotnet/2017/08/25/uwp-net-standard-2-0-preview/)，符合 .NET 标准 2.0。
* 更新了 Windows 10 IoT 核心版上的语言支持，包括英语（en-US 和 en-GB）、法语（fr-FR 和 fr-CA）、西班牙语（es-ES 和 es-MX）以及简体中文 (zh-CN)。 可以创建支持多种语言的 FFU - 请参阅 [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/MultiLangSample) 和 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/SingleLangSample) 获取详细信息。
* 支持 Windows 10 IoT 核心版上的 [紧急管理服务](https://technet.microsoft.com/library/cc736319(v=ws.10).aspx)。
* 改进了 Windows 10 IoT 核心版上的[墨迹支持](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions)。 借助兼容的触控笔数字化器，你现在可以使用 DirectInk API 来处理荧光笔、铅笔和基于矢量的墨迹。 此外，我们还添加了适用于 UWP 的 XAML 墨迹控件，包括 InkCanvas 和 InkToolbar，它们可以启用标尺和量角器等模具，还可以实现多模式交互，例如在兼容硬件上同时使用触控笔和触摸。 不支持智能墨迹功能（如墨迹识别和墨迹分析）。
* 另外，支持控制行显示，包括自定义光标样式、亮度、闪烁速度和字符集。 还添加了对自定义字形、事务描述符和滚动文本的字幕模式的支持。
* 在 Windows 10 IoT 企业版上，我们已在用户模式中通过 [Windows.Devices API](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) 启用了对行业标准总线（如 GPIO、I2C、SPI 和 UART）的访问。
* [分配的访问权限](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps) 是 Windows 10 IoT 企业版中的一项功能，可用于限制特定用户帐户仅使用一个通用 Windows 应用。 我们拓展了“分配的访问权限”支持，允许在锁定体验中运行多个 UWP 和 Win32 应用，并从云端管理这些设置。
* 可以使用 IoTSettings.exe 或新 API 更改系统语言。 有关详细信息，请参阅[命令行 Utils](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) 的语言配置部分和[语言支持](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang)文档。
* 更新至 Raspberry Pi UEFI 以启用引导卷监视器。
* 向 Windows 10 IoT 核心版的所有体系结构添加了 SMSC 网络驱动程序。
* 为 Windows 10 IoT 核心版上的音频终结点设备启用了[专用模式音频流](https://msdn.microsoft.com/library/windows/desktop/dd370844(v=vs.85).aspx)。
* 在 WinRT 中添加了新的 API，用于设置 Windows 10 IoT 核心版上的系统日期和时间。
* 添加了对 [通用 BSP (wm.xml)](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-packages) 的支持。 将 iot-adk-addonkit v4.0 与当前版本的 ADK 配合使用。
* 向屏幕键盘添加了语言选择和本地化布局。 有关详细信息，请参阅[屏幕键盘布局](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboardlayouts)。

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>预览版可用于开发和测试场景的功能
* 组件更新服务[预览版]允许 OEM 在全局管理应用并将操作系统、应用、设置和文件的更新从云端推送到设备，以保持更新和保障安全。
* 支持在 64 位 Windows 10 IoT 核心版和企业版上托管 [Nano Server 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/index)，从而实现应用程序及其数据彼此隔离，并快速地从开发环境转到生产环境或从云端转到边缘设备。
* Windows 设备运行状况证明[预览版]服务使用硬件功能和云服务，根据硬件级别的指标和经过证明的数据防止进行篡改操作并远程证明设备的运行状况。
* 借助 Windows IoT [预览版]上的 [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/)，IoT 解决方案能够协调云端和边缘设备之间的信息，以确保应用程序和服务可以最适当地处理 IoT 数据。
* 使用 Azure IoT 中心[设备预配服务[预览版]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/)，可以在制造过程中使用公共映像创建 Windows 10 IoT 设备，并将其配置为在首次启动时自动连接到 Azure IoT 中心，以检索特定于设备的预配信息。
* 借助 [Azure IoT 设备管理[预览版]](https://docs.microsoft.com/windows/iot-core/manage-your-device/AzureIoTDM)，IoT 运营商能够从云端远程管理设备配置，例如已安装的应用程序、Windows 更新、证书和网络设置。

## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT 核心版参考映像
___ 
* Minnowboard Max
  * 处理器：Intel Atom E3825
  * 体系结构：x86
  * BSP 版本：10.0.4.0
* Raspberry Pi 3
  * 处理器：Broadcom BCM2837
  * 体系结构：ARM
  * BSP 版本：10.0.16248.1001
* DragonBoard 410c
  * 处理器：Qualcomm Snapdragon 410
  * 体系结构：ARM
  * BSP 版本：2112.0.0.0

## <a name="additional-information"></a>其他信息
* 根据 Intel 关于停止生产 Intel Joule 平台的最新公告，此版本将不再提供用于 Intel Joule 的 FFU。 评估 Intel Joule 的客户应找到一种使用其他某种受支持的 SoC 的替代平台，请参阅[建议的主板和 SoC](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/prototypeboards) 以获取相关列表。
* IOT_WEBB_EXTN 功能已重构，删除了载入功能，该功能现在作为 IOT_ONBOARDING_APP 提供。 在此更新中将删除载入功能，并且使用此功能的设备应经过重新闪存才能再次获得此功能。

## <a name="known-issues"></a>已知问题
* 不能在 Windows 10 IoT 核心版上通过 Visual Studio 进行 F5 驱动程序部署。 必须手动复制驱动程序并在设备上注册。
* Windows IoT 远程客户端不适用于 Raspberry Pi。 使用带加速图形的板（例如 Minnowboard Max 或 Dragonboard），或者连接一个用于本地显示的监视器。
