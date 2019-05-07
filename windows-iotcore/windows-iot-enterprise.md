---
title: Windows 10 IoT 企业版的概述
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: 了解什么是 Windows 10 IoT 企业版和使用它可以执行的操作。
keywords: Windows 10 IoT 企业版、 企业版、 二进制、 Windows
ms.openlocfilehash: c8e9eed02a9ae3010ceb10c78bd8a01c4535e383
ms.sourcegitcommit: 1f6afcfee0cb5557dc21c7b15e199bc557d8eedb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2019
ms.locfileid: "65171341"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Windows 10 IoT 企业版的概述

> [!NOTE]
> Windows 10 容器可以仅用于 Windows IoT Core 和 Windows IoT 企业版与商业利用 Microsoft Azure IoT Edge 的部署。

## <a name="what-is-windows-10-iot-enterprise"></a>什么是 Windows 10 IoT 企业版？
Windows 10 IoT 企业版是传递到 IoT 解决方案的企业可管理性和安全性的 Windows 10 的完整版本。 Windows 10 IoT 企业版共享全球范围内 Windows 生态系统的所有的权益。 它是二进制文件等效于 Windows 10 企业版，因此可以使用同一个熟悉的开发和管理工具为客户端 Pc 和便携式计算机。  但是，当涉及到许可和分发，桌面版本和 IoT 版本不同。 请注意，Windows 10 IoT 企业版提供了长期服务频道 (LTSC) 和半年频道 (SAC) 选项。 Oem 可以选择他们需要为其设备的版本。

## <a name="getting-started"></a>即刻体验 

为了在使用 Windows 10 IoT 企业版的生产开始之旅，您将需要从分发服务器联系[此列表](https://go.microsoft.com/fwlink/p/?linkid=2069623)。

在这里，可以了解如何使用 Windows 10 IoT 企业版与制造我们[Windows 10 IoT 企业交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview)。 

## <a name="fixed-purpose-devices"></a>固定的用途设备 

> [!TIP]
> 有关所有 Windows 10 IoT 企业版使用方案，请参阅许可协议的完整指南。 如果没有此许可协议，要求 OEM 商业协议的使用。 

众所周知便携式计算机和使用者和企业全球范围内使用的台式计算机上的操作系统是 Windows。  不太常见的是，多年以来，Windows 已还提供许多 ATM 机、 销售点终端、 工业自动化系统、 瘦客户端、 医疗设备、 数字签名、 网亭和其他固定的用途设备。  Windows 10 IoT 企业版，可生成具有特定限额和限制的固定的用途设备许可协议中。  

固定的目标设备不同于常规用途设备通过以下方式：  
* 在设备锁定单个应用程序或组固定的应用程序可以通过分配的访问权限或 Shell 启动程序功能。  
* 设备体验是即时发生时客户幂上。 这是通过配置的设备映像要跳过正常 Windows 开箱体验实现的。 
* 键盘、 USB 端口和设备策略向下锁定，以限制设备只在其固定用途中使用。  
* OEM 附加到该设备是完整的产品的软件许可证向用户设备，并通过其自己的协议中的特定 Windows 术语。
* OEM 提供客户支持对其完整的产品，包括由操作系统执行的函数。

## <a name="long-term-servicing-channel-ltsc"></a>长期服务频道 (LTSC)

专用的系统，如 Pc 控制医疗设备、 销售点系统和 atm 机，通常需要再维护服务选项，由于它们的用途。 这些设备通常执行一项重要的任务，并且不像组织中其他设备那样频繁需要功能更新。 很多重要为稳定并尽可能安全比它们是最新 UI 更改的情况下保持这些设备。 服务模型 LTSC 会阻止 Windows 10 企业版 LTSB 设备接收的常用功能更新，并提供仅质量更新，以确保设备安全功能保持最新。 这一点，质量更新仍立即可用于 Windows 10 企业版 LTSB 的客户端，但客户可以选择将其延迟使用维护服务工具部分中提到的维护工具之一。

* [了解有关 LTSC 的详细信息](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)

## <a name="long-term-support-silicon-details"></a>长期支持硅详细信息

Windows 10 IoT 企业 2019年版本将会 LTSC 版本。 下面的列表包含预期的此版本支持的所有处理器。 如果想要使用早期版本的 Windows 10 IoT 企业版，您可以找到有关处理器支持详细信息[此处](https://docs.microsoft.com/windows-hardware/design/minimum/windows-processor-requirements#windows-iot-enterprise--embedded-processor-table)。

> | Windows 10 IoT 企业版  |
> |-------------|
> | AMD® 第六代处理器系列 Ax-8xxx E 系列 Ex 8xxx & FX-870 K | 
> | AMD® 第 7 个代处理器系列 Ax-9xxx E 系列 Ex 9xxx & FX 9xxx | 
> | AMD® Ryzen™ 3/5/7 1xxx | 
> | AMD® Ryzen™ 3/5/7 2xxx | 
> | AMD® G 系列 | 
> | AMD® R 系列 | 
> | AMD® V1xxx | 
> | 第四代 Intel® Core™ 处理器 | 
> | 第 5 代 Intel® Core™ 处理器 |
> | 第六代 Intel® Core™ 处理器 |
> | 第 7 个代 Intel® Core™ 处理器 |
> | 第 8 个代 Intel® Core™ 处理器 |
> | Intel® Atom™ 处理器 E3900 系列 |
> | Intel® Atom™ x5 E8000 处理器 |
> | Intel® Atom™ x5 Z8350 处理器 |
> | Intel® Atom™ 处理器 E3800 产品系列 |
> | Intel® Pentium® 和 Celeron® 处理器 N 和 J 系列 |

## <a name="helpful-resources"></a>有用资源
> [!NOTE]
> 其他资源都存在于分发服务器，以说明 Windows EPKEA OEM 激活并提供生成你的生产就绪 Windows IoT 企业版中的指导[WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx)设备映像。

* [企业版桌面设备自定义](https://docs.microsoft.com/windows-hardware/customize/enterprise/enterprise-custom-portal)
* [适用于 Windows 10 的统一的写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [有关企业与 Pro 已分配的访问](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [用于企业和教育版的 shell 启动程序](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [锁定资源](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [启用嵌入模式和在 Windows IoT 企业版上使用后台任务](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [在你的组织中配置 Windows 遥测数据](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [配置展台和共享运行 Windows 桌面版本的设备](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
* [桌面设备制造](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
