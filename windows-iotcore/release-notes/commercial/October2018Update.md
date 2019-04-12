---
title: 2018 年 10 月更新-生成 17763
author: saraclay
ms.author: saclayt
ms.date: 10/02/2018
ms.topic: article
description: 了解有关新增功能在 2018 年 10 月更新的 Windows 中。
keywords: Windows IoT 2018 年 10 月更新，发行说明
ms.openlocfilehash: 886f86a733f53632dee73d0af7b2c172693bc3a5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512095"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>Windows 10 IoT 的 2018 年 10 月更新版发行说明
生成号 17763。 2018 年 10 月

> [!IMPORTANT]
> 如果您使用的[2018 年 10 月更新](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/october2018update)，请使用[年 10 月更新 （与服务包，生成 17763.253 年 1 月）](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/17763)改为 release。 我们发现，存在一些已知问题会影响用户的 2018 年 10 月的更新。 

Windows 10 IoT 支持嵌入式或专用用途设备的开发，Oem 和构建智能设备的 Windows 解决方案的开发人员的选择。

本文档提供补充其他内容和文档，了解此版本的 Windows 10 IoT 的信息。

## <a name="privacy-statement"></a>隐私声明

可以在查看此版本的 Windows 操作系统的隐私声明[ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839)。

## <a name="whats-new-in-october-2018-update"></a>什么是 2018 年 10 月中的新增功能更新

_Windows 10 IoT 企业版和 Windows 10 IoT 核心版_
* Windows 10 IoT 年 10 月 2018年更新将具有 10 年的 IoT 核心版和 IoT 企业版的支持。
* [Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart)是完全托管的服务可将云提供智能本地的部署和 Windows 10 IoT 设备上直接运行人工 (AI) 工作负荷、 Azure 服务和自定义逻辑。
* [Windows 机器学习](https://docs.microsoft.com/windows/ai/)允许开发人员使用预先训练的机器学习模型的应用程序中。 对模型进行通常训练在云中以在 edge 上进行评估。 在运行 Windows 10 IoT 设备上的本地计算可帮助缓解的连接、 带宽和数据隐私问题。  

_Windows 10 IoT 核心版_
* [Windows 10 IoT 核心服务](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)订阅现已公开发布。 此订阅提供具有三个主要优势包括 10 年的 OS 支持，请更新具有控件[设备更新中心](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center)，和设备运行状况证明 (DHA)。
* 以满足不断发展的客户和合作伙伴索要 Microsoft，与 NXP，关闭合作关系中的 silicon 多样性，添加了对支持 NXP i.MX 6、 7 和 8 M 系列处理器到 Windows 10 IoT Core。 
* Qualcomm 和 Microsoft 创建了一种解决方案，将 Windows 10 IoT 企业版与 Snapdragon 处理器生成的消耗较少的电量，始终连接并立即唤醒设备相结合。 长的电池使用寿命使得移动 POS 和业务线平板电脑到最后一个全天的大量使用等专用的设备。 
* [Windows 10 IoT Core 默认应用](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)具有更多的功能，用户可以利用自己的应用程序，尤其是在将其设备推向市场。 这些功能包括天气、 墨迹功能、 音频功能。 
* 如果您正在构建商业上部署的"特定于/受限安装"将打开零售设备 （即工厂或零售商店） 的最终用户执行最终配置和文档客户，他们必须[获取它同时 WDP 和连接的浏览器和密码时更改 WDP WDP 和安装证书](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)，则此窄的商业实例中使用 WDP 是可接受。 零售映像在此方案中应仍包括 IOT_TOOLKIT，但应使用 IOT_WEBBEXTN 包 WDP 拉取。 
* 现可作为 Limpet.exe[开放源代码项目](https://github.com/ms-iot/azure-dm-client)。 若要使测试更加轻松，我们有一个非签名、 预建的 Limpet.exe 可用版本，并且可以直接从 WDP 下载。 了解有关此功能的详细信息[Windows Device Portal 文档](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)。  
* RS5，开发人员现在可以刷写到其设备使用仪表板上的自定义 FFUs。 这可以与 DragonBoard 410 C 或 NXP。 了解详细信息并开始[此处](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup)。
* Windows 10 IoT 核心版现在为允许听写模式、 Windows 键盘语言布局，整个集和的详细信息等功能的 Windows 桌面版使用相同的触摸键盘组件。 此新的更新还包括 supprt 图释、 最输入"作用域"，和更好的多语言支持。 了解如何利用这些功能[此处](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard)。
* 了解如何[配置设备以允许将其关闭](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch)而不在使用，以在用户触摸屏幕时启用。
* 现在可以选择支持蓝牙 A2DP 接收器 （例如允许播放来自远程源，如 iPhone 到 IoT 设备） 和蓝牙 A2DP SRC 现在是一种可选包 (2018 年 4 月已按默认提供的版本)。 存在两个配置文件时，并与另一台设备同时支持两者配对时，可以控制蓝牙 A2DP SRC 和 A2DP 接收器配置文件首选项。 
* 根据设计，Windows 10 IoT 核心版中顺序的单词不会显示应用程序的窗口 – 周围应用程序框架，应用程序显示为全屏显示。 但此版本中，开发人员可以选择[配置标题栏](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars)。
* 允许你使用 Gpio、 I2c、 Spi 和 UART 交互的总线工具现可[我们的示例存储库](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools)。 这些工具将在任何版本的 Windows 10 IoT 核心版和 Windows 企业的 Windows 上运行。 
* [Windows.System.Update Namespace API](https://docs.microsoft.com/uwp/api/windows.system.update)允许以交互方式控制系统更新的调用。 此命名空间功能仅适用于 Windows 10 IoT Core。
* 如果您希望使用 IoT 中心作为 Windows 10 IoT 解决方案的一部分，现在可以准备并[Windows 10 IoT Core 设备连接到 Azure IoT Central 应用程序](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore)。 
* 适用于 Raspberry Pi 3B + 的版本 (可以找到可下载的 ISO[此处](http://go.microsoft.com/fwlink/?LinkID=708576)) 是技术预览版，目前没有发行版本的时间线。 更好的评估体验和 fr 任何商业产品，请使用 Raspberry Pi 3B 或其他设备以及的受支持的 Intel、 Qualcomm 或 NXP Soc。 

## <a name="iot-enterprise-manufacturing-guide"></a>IoT 企业版制造指南

* 新 Windows 10 IoT 企业版的制造参考线[现已推出](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview)。 

## <a name="improvements-in-assigned-access"></a>已分配的访问中的改进 

_Windows 10 IoT 企业版_

* 网亭和数字符号通常放置在其中问题广泛被人的公共位置。 使用内置的状态报告，设备管理系统会自动将注意到问题，并可发布纠正操作，例如重新启动设备或分派服务技术人员。 
* 缩减的部署和管理成本是关键驱动程序的投资回报率。 Windows 10 IoT 企业版改进了功能用于在设置应用中配置新的向导通过的网亭体验、 管理多应用展台和定制[展台设备的 Microsoft Edge 浏览器体验](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy)。
* 尽管设备构建者可以非常灵活地配置预配包、 设置应用和移动设备管理系统使用的分配的访问权限，某些客户仍然需要更多。 [使用一组新的分配访问 Api](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings)，开发人员现在可以配置分配的访问权限以编程方式从其应用程序中。
* 2018 年 10 月版本中，客户可以指定自动启动体验作为多应用分配的访问权限配置的一部分以便最终用户就可以始终拥有默认主应用程序体验。
* 您可以控制用户从那一刻起，直到它处于关闭状态，打开设备所看到的内容。 启动应用程序崩溃、 系统问题或电源中断后显示你的徽标而不是在启动卷或自动重启应用，无错误消息的 Windows 徽标。 
* 可以使用统一写入筛选器 (UWF) 功能生成电源周期通过将磁盘更改保留在内存而不是写入到磁盘后，返回到已知状态的"只读"设备。 也可以组合使用休眠一次，恢复 Many (HORM) 功能，若要恢复到预定义会话 UWF。 


## <a name="more-management-support"></a>更多管理支持

_Windows 10 IoT 企业版_
* Azure IoT 中心提供轻量设备管理功能和可扩展性模型，使设备和云开发人员可以构建功能强大的设备管理解决方案。 与集成[Azure IoT 设备管理](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm)现已推出适用于 Windows 10 IoT 核心版和 Enterprise。 

_Windows 10 IoT 核心版_
* 使用企业[Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune)为其设备管理现在可以管理 Windows 10 IoT Core 设备以及其 Windows 10 IoT 企业版设备和其他托管的设备。 这样，运算符以一致的方式来管理 Windows 10 IoT 设备使用同一管理界面和控件。 


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


## <a name="known-issues"></a>已知问题
* 从 Visual Studio 的 F5 驱动程序部署不适用于 Windows 10 IoT Core。 驱动程序必须手动复制并在设备上注册。
* 通过 NOOBS 安装的设备不能运行 bcdedit 工具来启用内核调试程序。
* Windows IoT 远程客户端并不适用于 Raspberry Pi。 使用如 Minnowboard 最大或 Dragonboard 加速图形使用看板或附加的本地显示的监视器。
