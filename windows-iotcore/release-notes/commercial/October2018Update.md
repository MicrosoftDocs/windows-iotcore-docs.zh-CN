---
title: 2018年10月更新-版本17763
ms.date: 10/02/2018
ms.topic: article
description: 了解 Windows 10 月2018版更新中的新增功能。
keywords: Windows IoT，10月2018更新，发行说明
ms.openlocfilehash: 30292437da20a577a319fe47b3f5c2647df00382
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918704"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>2018年10月更新发行说明，适用于 Windows 10 IoT
内部版本号17763。 2018 年 10 月

> [!IMPORTANT]
> 如果你使用的是[10 2018 月版更新](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/october2018update)，请改为使用[10 月更新版（与1月版服务包、版本17763.253）](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/17763) 。 我们发现存在一些已知问题，这些问题会影响10月2018更新的用户。 

Windows 10 IoT 允许开发嵌入或专用设备，并且是为为智能设备构建 Windows 解决方案的 Oem 和开发人员选择的。

本文档提供了有关此版本的 Windows 10 IoT 的补充其他内容和文档的信息。

## <a name="privacy-statement"></a>隐私声明

可以[https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)查看此版本 Windows 操作系统的隐私声明。

## <a name="whats-new-in-october-2018-update"></a>2018年10月更新中的新增功能

_Windows 10 IoT Enterprise & Windows 10 IoT Core_
* Windows 10 IoT 10 月2018更新将为 IoT 核心和 IoT Enterprise 提供10年的支持。
* [Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart)是一种完全托管的服务，可通过直接在 Windows 10 IoT 设备上部署和运行人工（AI）工作负荷、Azure 服务和自定义逻辑，在本地提供云智能。
* [Windows 机器学习](https://docs.microsoft.com/windows/ai/)允许开发人员在其应用程序中使用预先训练机器学习模型。 通常，在云中训练这些模型以在边缘进行评估。 运行 Windows 10 IoT 的设备上的本地评估有助于缓解连接性、带宽和数据隐私问题。  

_Windows 10 IoT 核心板_
* [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)订阅现已正式发布。 此订阅附带三个主要优点，包括10年的操作系统支持、通过[设备更新中心](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center)进行的更新控制，以及设备运行状况证明（DHA）。
* 为了满足不断增长的客户和合作伙伴对硅多样性的需求，Microsoft 在与 NXP 的密切合作中增加了对 NXP i.MX 6、7和8分钟系列处理器到 Windows 10 IoT Core 的支持。 
* Qualcomm 和 Microsoft 创建了一个解决方案，该解决方案将 Windows 10 IoT Enterprise 与 Snapdragon 处理器组合在一起，以构建消耗更少电源、始终处于连接状态且可立即唤醒的设备。 使用电池电量长时，mobile POS 和业务线平板电脑等专用设备将一直使用一整天。 
* [Windows 10 IoT Core 默认应用](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)具有更多功能，用户可将其用于自己的应用程序，尤其是在将其设备投放市场时。 这些功能包括天气、墨迹功能、音频功能。 
* 如果要为商业部署构建开放零售设备，使其最终用户执行最终配置，并记录客户必须[为 WDP 获取证书的 "特定/限制安装" （即工厂或零售商店）。并将其安装在 WDP 和连接浏览器上并更改 WDP 上的密码](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)，然后在此窄的商业实例中使用 WDP 是可接受的。 此方案中的零售映像应仍不包含 IOT_TOOLKIT，但应使用 IOT_WEBBEXTN 包拉取 WDP。 
* Limpet 现在作为[开源项目](https://github.com/ms-iot/azure-dm-client)提供。 为了使测试变得更容易，我们提供了一个未签名的预构建版本的 Limpet，可从 WDP 下载。 从[Windows 设备门户文档](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)中了解有关此功能的详细信息。  
* 使用 RS5，开发人员现在可以使用仪表板将自定义 FFUs 闪存到其设备上。 可以通过 DragonBoard 410C 或 NXP 实现此目的。 [在此处](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup)了解详细信息并开始。
* Windows 10 IoT Core 现在使用与 Windows 桌面版本相同的触摸键盘组件，这允许使用听写模式、整套 Windows 键盘语言布局等功能。 此新更新还包括图释、大多数输入 "作用域" 和更好的多语言支持 supprt。 [在此处](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard)了解如何利用这些功能。
* 了解如何[将设备配置为允许](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch)在不使用时关闭，并在用户触摸屏幕时启用。
* 现在可以选择支持蓝牙 A2DP （例如，允许从 iPhone 到 IoT 设备等远程源播放）和蓝牙 A2DP-SRC 现在是可选包（在2018年4月发行版中默认提供）。 当两个配置文件都存在时以及同时同时支持这两个配置文件的其他设备时，可以控制蓝牙 A2DP-SRC 和 A2DP 配置文件首选项。 
* 按照设计，Windows 10 IoT Core 不会在应用程序窗口周围显示应用程序框架–按照顺序，应用程序将显示为全屏。 但在此版本中，开发人员可以选择[配置标题栏](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars)。
* 现在[我们的示例存储库](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools)中提供了可用于与 Gpio、I2c、SPI 和 UART 交互的总线工具。 这些工具将在任何 Windows 版本（包括 Windows 10 IoT Core 和 Windows Enterprise）上运行。 
* [Windows. Update 命名空间 API](https://docs.microsoft.com/uwp/api/windows.system.update)启用对系统更新的交互式控制的调用。 此命名空间仅适用于 Windows 10 IoT 核心版。
* 如果希望将 IoT Central 用作 Windows 10 IoT 解决方案的一部分，现在可以准备[windows 10 Iot Core 设备并将其连接到 Azure IoT Central 应用程序](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore)。 
* Raspberry Pi 3B + （可下载[ISO）的](http://go.microsoft.com/fwlink/?LinkID=708576)发行版是 technical preview，当前没有适用于发布版本的时间线。 若要获得更好的评估体验和 fr 任何商业产品，请使用 Raspberry Pi 3B 或支持 Intel、Qualcomm 或 NXP Soc 的其他设备。 

## <a name="iot-enterprise-manufacturing-guide"></a>IoT 企业生产指南

* [现已推出](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview)适用于 Windows 10 IoT 企业版的新生产指南。 

## <a name="improvements-in-assigned-access"></a>已分配的访问的改进 

_Windows 10 IoT 企业版_

* 网亭和数字签名通常放置在人们广泛了解问题的公共位置。 使用内置状态报告，设备管理系统会自动感知问题，并且可以发出更正操作，如重新启动设备或分派服务技术人员。 
* 降低部署和管理成本是 ROI 的关键驱动因素。 Windows 10 IoT 企业版改进了用于通过 "设置" 应用程序中的新向导配置展台体验的功能，管理多应用展台，并[为展台设备定制 Microsoft Edge 浏览器体验](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy)。
* 尽管设备构建者可以非常灵活地使用预配包、设置应用和移动设备管理系统配置分配的访问权限，但某些客户仍需要更多。 [通过使用一组新的已分配访问 api](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings)，开发人员现在可以在其应用程序中以编程方式配置分配的访问权限。
* 在10月2018版中，客户可以指定自动启动体验作为多应用分配的访问配置的一部分，因此最终用户可以始终具有默认的主要应用体验。
* 你可以控制用户在设备打开之前看到的内容，直到设备关机。 在应用程序崩溃、系统问题或电源中断后，开始显示徽标（而不是 Windows 徽标），或自动重新启动应用而不显示错误消息。 
* 可以使用统一写入筛选器（UWF）功能，通过在内存中保留磁盘更改而不是将磁盘更改写入磁盘来构建一个 "只读" 设备，该设备在电源周期后返回到已知状态。 你还可以将 UWF 与休眠一次结合使用，恢复多个（HORM）功能以恢复到预定义的会话中。 


## <a name="more-management-support"></a>更多管理支持

_Windows 10 IoT 企业版_
* Azure IoT 中心提供轻型设备管理功能和可扩展性模型，使设备和云开发人员能够构建强大的设备管理解决方案。 [Azure Iot 设备管理](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm)的集成现在适用于 Windows 10 IoT 核心版和企业版。 

_Windows 10 IoT 核心板_
* 使用[Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune)的设备管理的企业现在可以将 Windows 10 iot Core 设备与其 Windows 10 iot 企业设备和其他托管设备一起管理。 这为操作员提供了使用相同的管理界面和控件管理 Windows 10 IoT 设备的一致方式。 


## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT 核心参考映像
___ 
* Minnowboard Max
  * 处理器： Intel Atom E3825
  * 体系结构： x86

* Raspberry Pi 3 模型 B
  * 处理器： Broadcom BCM2837
  * 体系结构： ARM

* DragonBoard 410c
  * 处理器： Qualcomm Snapdragon 410
  * 体系结构： ARM
  * BSP 版本：2120.0.0。0


## <a name="known-issues"></a>已知问题
* 不能在 Windows 10 IoT 核心版上通过 Visual Studio 进行 F5 驱动程序部署。 必须手动复制驱动程序并将其注册到设备上。
* 通过 NOOBS 安装的设备不能运行 bcdedit 工具来启用内核调试程序。
* Windows IoT 远程客户端不适用于 Raspberry Pi。 使用带加速图形的板（例如 Minnowboard Max 或 Dragonboard），或者连接一个用于本地显示的监视器。
