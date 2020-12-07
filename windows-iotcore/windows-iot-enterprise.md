---
title: Windows 10 IoT 企业版概述
ms.date: 12/01/2020
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Windows 10 IoT 企业版是什么，以及可以用它执行什么操作。
keywords: Windows 10 IoT 企业版, 企业, 二进制, Windows
ms.openlocfilehash: 39f968ad71d2588655e42beaf9215bd645476a60
ms.sourcegitcommit: d6b6a659b64193d1a9ef785871ab2beff3bb2590
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2020
ms.locfileid: "96481063"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Windows 10 IoT 企业版概述

## <a name="what-is-windows-10-iot-enterprise"></a>什么是 Windows 10 IoT 企业版？
Windows 10 IoT 企业版是完整版本的 Windows 10，可以为 IoT 解决方案提供企业可管理性和安全性。 Windows 10 IoT 企业版享有全球 Windows 生态系统的所有权益。 它是 Windows 10 企业版的二进制等效文件，因此你可以使用类似的开发和管理工具，就像在客户端电脑和笔记本电脑上使用一样。  但是，在许可和分发方面，桌面版本和 IoT 版本存在差异。 请注意，Windows 10 IoT 企业版提供长期服务频道 (LTSC) 和半年频道 (SAC) 两个选项。 OEM 可以选择需要用于设备的版本。

## <a name="getting-started"></a>入门

若要开始使用 Windows 10 IoT 企业版进行制造，需要联系某位 [Windows IoT 分发商](https://aka.ms/IoTDistributorList)。

也可试用 Windows 10 IoT 企业版 [90 天评估](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)。

这样就可以参阅 [Windows 10 IoT 企业版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/desktop/iot-ent-overview)，了解如何使用 Windows 10 IoT 企业版进行制造。

## <a name="fixed-purpose-devices"></a>固定用途设备

> [!TIP]
> 若要完全了解所有 Windows 10 IoT 企业版使用方案，请查看许可协议。 如果没有此许可协议，请要求你的 OEM 提供商业协议。

Windows 作为可供全世界消费者和企业使用的笔记本电脑和台式机的操作系统享有盛誉。  其不太为人所知的是，多年来，Windows 还为许多 ATM 机、销售点终端、工业自动化系统、瘦客户端、医疗设备、数字签名、网亭和其他固定用途设备提供支持。  Windows 10 IoT 企业版允许你构建固定用途设备，在许可协议中提供特定的许可和限制。  

固定用途设备在以下方面不同于常规用途设备：  
* 已通过“分配访问权限”或“Shell 启动程序”功能将设备与单个应用程序或固定的应用程序集锁定。  
* 当客户打开电源时，可以即时获得设备体验。 若要实现这一点，可以将设备映像配置为跳过正常的 Windows 全新安装体验。
* 键盘、USB 端口和设备策略都已锁定，使设备只能用于固定用途。  
* OEM 会将软件附加到设备，以这种方式将设备作为一个完整的产品许可给用户，并在其自己的协议中阐明特定的 Windows 条款。
* OEM 为完整的产品提供客户支持，其中包括操作系统执行的功能。

## <a name="long-term-servicing-channel-ltsc"></a>长期服务频道 (LTSC)

专用系统（例如控制医疗设备的电脑、销售点系统和 ATM）出于其目的原因，通常需要长期维护选项。 这些设备通常执行一项重要的任务，并且不像组织中其他设备那样频繁需要功能更新。 相比通过 UI 更改保持最新状态，这些设备更应该尽可能地保持稳定和安全。 LTSC 服务模式将阻止 Windows 10 IoT 企业版 LTSC 设备接收常规功能更新，仅提供质量更新，确保设备安全性保持最新。 有鉴于此，质量更新仍可立即用于 Windows 10 IoT 企业版 LTSC 客户端，但客户可以使用“维护工具”部分提到的某项维护工具来选择延迟更新。

Microsoft 大约每三年提供一个新的 Windows 10 IoT 企业版 LTSC 版本。 每个 Windows 10 IoT 企业版 LTSC 版本都是其自己的 SKU，还带有自上次 LTSC 版本以来包含在 Windows 10 IoT 企业版功能更新中的所有新功能和支持更新。 若要访问这些功能更新，必须购买新的 Windows 10 IoT 企业版 LTSC SKU 许可证。 例如，若要访问自 Windows 10 IoT 企业版 2016 LTSC 发布以来新推出的安全、部署和管理更新及功能，必须购买 Windows 10 IoT 企业版 2019 LTSC 许可证，并向设备应用更新。

* [了解有关 LTSC 的详细信息](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)

> [!NOTE]
> 考虑到 LTSC 版本的生命期很长，以及保持特定版本 10 年时间有很多好处，因此我们会对从一个 LTSC 版本转到另一个版本的客户收取升级费用。

## <a name="long-term-support-silicon-details"></a>长期支持芯片详细信息

Windows 10 IoT 企业 2019 版将是一个 LTSC 版本。 有关 Windows 10 LTSC 和其他可用渠道的一般说明，请参阅[此处](https://docs.microsoft.com/windows/whats-new/ltsc)。 可在[此处](https://docs.microsoft.com/windows-hardware/design/minimum/windows-processor-requirements#windows-iot-enterprise--embedded-processor-table)详细了解对 Windows 10 的每个版本和渠道的处理器支持。

## <a name="helpful-resources"></a>有用资源
> [!NOTE]
> 分发商可能会提供其他资源来说明 Windows EPKEA OEM 激活，并介绍如何生成制造就绪型 Windows IoT 企业版 [WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx) 设备映像。

* [企业版桌面设备自定义](https://docs.microsoft.com/windows-hardware/customize/enterprise/enterprise-custom-portal)
* [适用于 Windows 10 的统一写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [为企业版和专业版分配的访问权限](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [适用于企业版和教育版的 Shell 启动程序](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [锁定资源](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image)
* [在 Windows IoT 企业版上启用嵌入模式和使用后台任务](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [在组织中配置 Windows 遥测](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [配置运行 Windows 桌面版的网亭和共享设备](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
* [桌面设备制造](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
