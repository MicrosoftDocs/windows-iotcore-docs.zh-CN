---
title: 2018 年 10 月更新 - 版本 17763
ms.date: 10/02/2018
ms.topic: article
description: 阅读 Windows 10 IoT 的 2018 年 10 月更新的发行说明。 查看新增功能，了解已分配的访问权限的改进之处等等。
keywords: Windows IoT，2018 年 10 月更新，发行说明
ms.openlocfilehash: 2d82d4053fac3cf9c333816c30f1515e1737638f
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782779"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>适用于 Windows 10 IoT 的 2018 年 10 月更新的发行说明
内部版本号 17763。 2018 年 10 月

> [!IMPORTANT]
> 如果你使用的是 [2018 年 10 月更新](https://docs.microsoft.com/windows/iot-core/release-notes/commercial/october2018update)，请改用 [10 月更新（含 1 月服务包，版本 17763.253）](https://docs.microsoft.com/windows/iot-core/release-notes/commercial/17763)。 我们发现了一些已知问题，这些问题会影响使用 2018 年 10 月更新的用户。 

Windows 10 IoT 支持开发嵌入式设备或专用设备，适合 OEM 和开发人员用来为智能设备构建 Windows 解决方案。

本文档旨在为此版本 Windows 10 IoT 的其他内容和文档提供补充。

## <a name="privacy-statement"></a>隐私声明

如需查看有关此版本 Windows 操作系统的隐私声明，请访问 [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)。

## <a name="whats-new-in-october-2018-update"></a>2018 年 10 月更新中的新增功能

Windows 10 IoT 企业版和 Windows 10 IoT 核心版
* Windows 10 IoT 2018 年 10 月更新将为 IoT 核心版和 IoT 企业版提供 10 年的支持。
* [Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart) 是一种完全托管的服务，可通过直接在 Windows 10 IoT 设备上部署和运行人工 (AI) 工作负载、Azure 服务和自定义逻辑，在本地提供云智能。
* 借助 [Windows 机器学习](https://docs.microsoft.com/windows/ai/)，开发人员可在其应用程序中使用预先训练的机器学习模型。 这些模型通常在云中训练，以便在边缘设备上进行评估。 在运行 Windows 10 IoT 的设备上进行本地评估有助于减轻连接性、带宽和数据隐私方面的问题。  

_Windows 10 IoT Core_
* [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) 订阅现已正式发布。 此订阅具有三大优点：10 年的 OS 支持、[设备更新中心](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center)的更新控制和设备运行状况证明 (DHA)。
* 为了应对客户和合作伙伴对晶片多样性需求不断增长的趋势，Microsoft 与 NXP 密切合作，向 Windows 10 IoT 核心版添加了对 NXP i.MX 6、7 和 8M 系列处理器的支持。 
* Qualcomm 和 Microsoft 制定了一个解决方案，该解决方案将 Windows 10 IoT 企业版与 Snapdragon 处理器相结合，以构建功耗更低、始终保持连接并可立即唤醒的设备。 较长的电池续航时间使移动 POS 和业务线平板电脑等专用设备可以持续使用一整天。 
* [Windows 10 IoT 核心版默认应用](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)具有更多功能，用户可以将这些功能用于自己的应用程序，尤其是在将设备推向市场时。 这些功能包括天气、墨迹功能和音频功能。 
* 如果要构建一个开源零售设备，用于商业部署到“特定/有限安装”（即工厂或零售商店），然后由最终用户进行最终配置，并且您要为客户登记归档，他们必须[获取 WDP 证书，并将其安装到 WDP 和联网的浏览器上，且在 WDP 更改了密码](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)，那么在这种范围狭窄的商用实例中使用 WDP 是可以接受的。 此场景中的零售映像仍不包含 IOT_TOOLKIT，但应使用 IOT_WEBBEXTN 拉取 WDP。 
* Limpet.exe 现在可作为[开源项目](https://github.com/ms-iot/azure-dm-client)。 为了简化测试，我们提供了一个未签名的预构建版本的 Limpet.exe，它可从 WDP 下载。 有关此功能的详细信息，请参阅 [Windows 设备门户文档](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)。  
* 使用 RS5，开发人员现在可以使用仪表板将自定义 FFU 闪存到其设备上。 可以使用 DragonBoard 410C 或 NXP 来完成此操作。 请在[此处](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup)了解详细信息并开始使用。
* Windows 10 IoT 核心版现使用与 Windows 桌面版相同的触摸键盘组件，该组件支持听写模式及整套 Windows 键盘语言布局等功能。 此新的更新还支持表情符和大多数输入“范围”，并改善了多语言支持。 请在[此处](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard)了解如何利用这些功能。
* 了解如何[将设备配置为在不使用时关闭](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch)并在用户触摸屏幕时打开。
* 现可根据需要支持蓝牙 A2DP-SINK（例如，允许从 iPhone 等远程媒体源控制 IoT 设备播放），且蓝牙 A2DP-SRC 现为可选包（2018 年 4 月版默认提供）。 当两个配置文件都存在，且与另一个同时支持这两个配置文件的设备配对时，可控制蓝牙 A2DP-SRC 和 A2DP-SINK 配置文件首选项。 
* 按照设计，Windows 10 IoT 核心版不会在应用程序的窗口周围显示应用程序边框，也就是说，应用程序显示为全屏。 但在此版本中，开发人员可以选择[配置标题栏](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars)。
* 现在，[我们的示例存储库](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools)中提供了用于与 Gpio、I2c、Spi 和 UART 交互的总线工具。 这些工具可在任意版本的 Windows 上运行，包括 Windows 10 IoT 核心版和 Windows 企业版。 
* [Windows.System.Update 命名空间 API](https://docs.microsoft.com/uwp/api/windows.system.update)支持调用系统更新的交互式控件。 此命名空间仅适用于 Windows 10 IoT 核心版。
* 如果你希望将 IoT Central 用作 Windows 10 IoT 解决方案的一部分，现在可以进行准备并[将 Windows 10 IoT 核心版设备连接到 Azure IoT Central 应用程序](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore)。 
* Raspberry Pi 3B+ 的版本（[在此处](https://go.microsoft.com/fwlink/?LinkID=708576)可找到可供下载的 ISO）为技术预览版，目前尚无发行版本的时间表。 若要获得更好的评估体验和任何商品，请使用 Raspberry Pi 3B 或其他采用受支持的 Intel、Qualcomm 或 NXP SoC 的设备。 

## <a name="iot-enterprise-manufacturing-guide"></a>IoT 企业版生产指南

* 适用于 Windows 10 IoT 企业版的新生产指南[现已发布](https://docs.microsoft.com/windows-hardware/manufacture/desktop/iot-ent-overview)。 

## <a name="improvements-in-assigned-access"></a>分配的访问权限中的改进 

_Windows 10 IoT 企业版_

* 展台和数字签名通常放置在人们经常查看发布内容的公共位置。 通过内置状态报告，设备管理系统会自动了解问题，并且可以发出更正操作，如重新启动设备或派遣服务技术人员。 
* 降低部署和管理成本是 ROI 的关键驱动因素。 Windows 10 IoT 企业版改进了一些功能，包括通过“设置”应用中的新向导配置展台体验、管理多应用展台并[为展台设备定制 Microsoft Edge 浏览器体验](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy)。
* 虽然设备构建者可以非常灵活地使用预配包、“设置”应用和移动设备管理系统配置分配的访问权限，但某些客户仍有更多需求。 [使用一组新的已分配访问权限 API](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings)，开发人员现在可以在应用程序中以编程方式配置已分配的访问权限。
* 在 2018 年 10 月版中，客户可以将自动启动体验指定为多应用分配的访问配置的一部分，以便最终用户始终可以拥有默认的主应用体验。
* 你可以控制用户从设备打开到关闭时所看到的内容。 在启动时首先显示你的徽标而不是 Windows 徽标，或者在应用崩溃、系统出现问题或电源中断后自动重新启动应用，而不显示错误消息。 
* 您可以使用统一写入筛选器 (UWF) 功能来构建“只读”设备，该设备将磁盘更改保存在内存中而不是将其写入磁盘，在重启后即可返回到已知状态。 你还可以将 UWF 与一次休眠多次启动 (HORM) 功能结合使用，以恢复到预定义的会话。 


## <a name="more-management-support"></a>更多管理支持

_Windows 10 IoT 企业版_
* Azure IoT 中心提供了轻量级的设备管理功能和可扩展模型，使设备和云开发人员能够构建可靠的设备管理解决方案。 Windows 10 IoT 核心版和企业版现在都可与[Azure IoT 设备管理](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm)集成。 

_Windows 10 IoT Core_
* 使用 [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) 进行设备管理的企业现在可以管理 Windows 10 IoT 核心版设备以及 Windows 10 IoT 企业版设备和其他托管设备。 这样，操作员可以采取一致的方式，使用相同的管理界面和控件管理 Windows 10 IoT 设备。 


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


## <a name="known-issues"></a>已知问题
* 不能在 Windows 10 IoT 核心版上通过 Visual Studio 进行 F5 驱动程序部署。 必须手动复制驱动程序并在设备上注册。
* 通过 NOOBS 安装的设备不能运行 bcdedit 工具来启用内核调试程序。
* Windows IoT 远程客户端不适用于 Raspberry Pi。 使用带加速图形的板（例如 Minnowboard Max 或 Dragonboard），或者连接一个用于本地显示的监视器。
