---
title: Fall 创意者更新的内部版本 16299
author: saraclay
ms.author: saclayt
ms.date: 10/12/2017
ms.topic: article
description: 了解什么是 Fall Creators Update 为 Windows 10 IoT 中的新增功能。
keywords: Windows IoT，Fall Creators Update 发行说明
ms.openlocfilehash: 00daad18d5519eee9be695105332aced81a1133f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510627"
---
# <a name="fall-creators-update-release-notes-for-windows-10-iot"></a>Fall Creators Update 发行说明适用于 Windows 10 IoT
生成号版本 16299。 2017 年 10 月

Windows 10 IoT 支持嵌入式或专用用途设备的开发，Oem 和构建智能设备的 Windows 解决方案的开发人员的选择。

本文档提供补充其他内容和文档，了解此版本的 Windows 10 IoT 的信息。

若要下载此最新版本以及程序包，请访问[Windows Insider Preview 下载页](https://www.microsoft.com/en-us/software-download/windowsiot)。

## <a name="privacy-statement"></a>隐私声明

可以在查看此版本的 Windows 操作系统的隐私声明[ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839)。

## <a name="whats-new-in-fall-creators-update"></a>中新增 Fall 创意者更新
* [适用于 UWP 应用的.NET](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx?f=255&mspperror=-2147217396)，可用于构建通用 Windows 平台应用程序使用的托管类型的集C#或 Visual Basic 中，得到增强[数千个新 Api](https://blogs.msdn.microsoft.com/dotnet/2017/08/25/uwp-net-standard-2-0-preview/)若要使符合.NET Standard2.0。
* 更新 Windows 10 IoT 核心版包括英语 （EN-US 和 EN-GB）、 法语 （FR-FR 和 FR-CA）、 西班牙语 （es ES 和 es MX） 和简体中文 (ZH-CN) 上的语言支持。 您可以创建 FFUs 支持多种语言支持-请参阅[MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/MultiLangSample)并[SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/SingleLangSample)有关详细信息。
* 为支持[紧急管理服务](https://technet.microsoft.com/library/cc736319(v=ws.10).aspx)Windows 10 IoT Core 上。
* 改进了[墨迹支持](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions)Windows 10 IoT Core 上。 使用兼容笔数字化器，现在可以为荧光笔、 铅笔和基于矢量的墨迹利用 DirectInk Api。 我们还添加了 XAML ink 控件适用于 UWP，包括 InkCanvas 和 InkToolbar，它们启用模具如标尺和 protractors，以及多模式交互，如同时进行笔和触摸兼容硬件上。 不支持墨迹识别和墨迹分析等智能墨迹功能。
* 用于控制显示一行，其中包括自定义的游标样式、 亮度、 闪烁速率和字符集的其他支持。 我们还添加了对自定义标志符号、 事务描述符和字幕滚动的文本模式的支持。
* 在 Windows 10 IoT 企业版，我们启用了访问到 GPIO、 I2C、 SPI 和 UART 等行业标准总线从用户模式下通过[Windows.Devices Api](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access)。
* [分配访问](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps)是一项功能在 Windows 10 IoT 企业可以使用只有一个通用 Windows 应用到限制特定用户帐户。 进行了扩展分配的访问权限支持，可让运行多个 UWP 和 Win32 应用程序中锁定体验，并从云中管理这些设置。
* 你可以使用 IoTSettings.exe 或新的 Api 的系统语言。 有关详细信息，请参阅的语言配置部分[命令行实用工具](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang)并[语言支持](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang)文档。
* 对 Raspberry Pi UEFI 启用启动卷监视器的更新。
* 添加了的 SMSC 网络驱动程序的 Windows 10 IoT 核心版的所有体系结构。
* 已启用[排他模式音频流](https://msdn.microsoft.com/library/windows/desktop/dd370844(v=vs.85).aspx)适用于 Windows 10 IoT Core 上的音频的终结点设备。
* 用于在 Windows 10 IoT Core 上设置系统日期和时间的 WinRT 中添加了新的 Api。
* 添加了对[通用 BSP (wm.xml)](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-packages)。 使用 iot adk addonkit v4.0 使用当前版本的 ADK。
* 添加的语言选择和本地化到屏幕键盘布局。 有关更多详细信息，请参阅[屏幕键盘布局](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboardlayouts)。

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>对于开发和测试方案的预览版功能
* 组件更新服务 [预览] 使 Oem 可以全局管理他们的应用并将更新的操作系统、 应用、 设置和文件从云中推送到设备以使它们保持最新和安全。
* 支持托管[Nano Server 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/index)上的 Windows 10 IoT 核心版和企业版 64 位版本，使应用程序和其数据能相互隔离和快速移动从开发到生产环境或云到边缘。
* Windows 设备运行状况证明 [预览] 服务使用的硬件功能和云服务提供防篡改攻击和远程证明的设备运行状况根据硬件级别的度量值和已证明数据。
* [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) Windows IoT 上 [预览] 允许 IoT 解决方案来协调云和边缘设备，以确保应用程序和服务可以处理 IoT 数据最有利位置之间的智能。
* Azure IoT 中心[设备预配服务 [预览]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/)使在制造期间使用的通用映像创建和配置为自动连接到 Azure IoT 中心检索的第一次启动在 Windows 10 IoT 设备特定于设备的设置信息。
* [Azure IoT 设备管理 [预览]](https://docs.microsoft.com/windows/iot-core/manage-your-device/AzureIoTDM)使 IoT 操作员能够管理设备配置，如安装应用程序、 Windows 更新、 证书、 设置和网络设置从云远程。

## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT 核心版参考映像
___ 
* Minnowboard Max
  * 处理器：Intel Atom E3825
  * 体系结构： x86
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
* 根据最新的 Intel 公告，停止生成 Intel Joule 平台，为 Intel Joule FFUs 将已不再使用此版本中。 评估 Intel Joule 客户应确定一种替代方法使用的另一个平台支持 Soc-请参阅[建议的看板和 Soc](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/prototypeboards)的列表。
* 若要删除载入功能现已推出 IOT_ONBOARDING_APP 重构 IOT_WEBB_EXTN 功能。 利用此更新，将删除载入功能和设备使用此功能应 reflashed 再次获取此功能。

## <a name="known-issues"></a>已知问题
* 从 Visual Studio 的 F5 驱动程序部署不适用于 Windows 10 IoT Core。 驱动程序必须手动复制并在设备上注册。
* Windows IoT 远程客户端并不适用于 Raspberry Pi。 使用如 Minnowboard 最大或 Dragonboard 加速图形使用看板或附加的本地显示的监视器。
