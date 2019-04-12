---
title: Windows 10 IoT 企业版的概述
author: saraclay
ms.author: saclayt
ms.date: 01/18/2017
ms.topic: article
description: 了解什么是 Windows 10 IoT 企业版和使用它可以执行的操作。
keywords: Windows 10 IoT 企业版、 企业版、 二进制、 Windows
ms.openlocfilehash: 1f13c4df2c40dcc4449f2e6cdd16005b1bc0069f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510836"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Windows 10 IoT 企业版的概述

## <a name="what-is-windows-10-iot-enterprise"></a>什么是 Windows 10 IoT 企业版？
Windows 10 IoT 企业版是传递到 IoT 解决方案的企业可管理性和安全性的 Windows 10 的完整版本。 因此，如果您已经知道 Windows 10 企业版的工作原理，大量的这一知识可以转移到 Windows 10 IoT 企业版，它是等效于 Windows 10 企业版的二进制文件。 但是，当涉及到许可和分发，桌面版本和 IoT 版本不同。 

## <a name="getting-started"></a>入门 
在联系到嵌入式 /iot 分发服务器之前，我们建议使用之一[这些设备](https://solutionsdirectory.intel.com/solutions-directory/processors/736/processors/766/processors/782/processors/788/processors/869/processors/879/processors/883/processors/888/processors/1053/processors/1058/processors/1103/processors/1107/processors/1110/processors/1117/processors/1133/processors/1135/processors/1139/processors/1141/processors/1175/processors/1192/processors/1344/processors/1348/processors/1349/processors/1371/processors/1392/processors/1729/processors/2284)。  您可以加载在电脑或推荐使用的设备[评估版](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise)的 Windows 10 企业版以立即开始原型设计。

为了在使用 Windows 10 IoT 企业版的生产开始之旅，您将需要从分发服务器联系[此列表](http://wincom.blob.core.windows.net/documents/Windows_IoT_Distributor_Information.pdf)。 

## <a name="fixed-purpose-devices"></a>固定的用途设备 

> [!TIP]
> 有关所有 Windows 10 IoT 企业版使用方案，请参阅许可协议的完整指南。

Windows 10 IoT 企业版是授予许可，以便您可以构建固定的用途设备，例如瘦客户端、 ATM 机、 销售点终端、 工业自动化系统，等等。有特定的限额和限制许可协议中。 

一般情况下固定的目标设备从常规用途设备在以下方面不同：  
* 在设备锁定单个应用程序或组固定的应用程序可以通过分配的访问权限或 Shell 启动程序功能。  
* 设备支持针对立即时收到的最终客户的体验。 这是通过配置的设备映像要跳过正常 Windows 开箱体验实现的。
* 键盘、 USB 端口和设备策略向下锁定，以限制设备只在其固定用途中使用。  
* OEM 附加到该设备是完整的产品的软件许可证向用户设备，并通过其自己的协议中的特定 Windows 术语。

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Windows 10 IoT 核心版和 Windows 10 IoT 企业版之间的差异
虽然 Windows 10 IoT 核心版和 Windows 10 IoT 企业版是在名称类似，有的功能以及它们所支持内容之间的差异。 下面是一个功能列表，其中突出显示了版本差异。

最低要求的详细信息，请访问[Windows 硬件站点](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview)。

> |             | Windows 10 IoT 核心版  |  Windows 10 IoT 企业版  |
> |-------------|----------|---------|
> | 用户体验 | 在提供的支持背景应用和服务启动时运行的单个 UWP 应用。 | 高级的锁定功能与传统的 Windows Shell |
> | 无外设支持 | 是 | 是 |
> | 支持的应用程序体系结构 | 仅 UWP | UWP 和 Win32 |
> | Cortana | *Cortana SDK* | 是 |
> | 域加入 | 只有 AAD | AAD 与传统的域 |
> | Management | MDM | MDM |
> | 设备安全技术 | TPM、 安全启动、 BitLocker、 设备运行状况证明和 iot 设备保护 | TPM、 安全启动、 BitLocker、 Device Guard、 Defender ATP，和设备运行状况证明 |
> | CPU 体系结构支持 | x86、 x64 和 ARM | x86、 x64 和 ARM64 |
> | 授权 | 联机免版税的许可协议和嵌入式的 OEM 协议， | 直接和间接的嵌入式的 OEM 协议 |
> | 使用方案 | 数字签名、 智能建筑、 IoT 网关、 HMI，主页，智能可穿戴设备 | 行业平板电脑、 POS、 展台、 数字签名、 ATM、 医疗设备、 制造设备，瘦客户端 |

## <a name="helpful-resources"></a>有用资源
> [!NOTE]
> 其他资源中可能会提供在分发服务器，以说明 Windows EPKEA OEM 激活并提供生成你的生产就绪 Windows IoT 企业版中的指导[WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx)设备映像。

* [桌面设备制造](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
* [适用于 Windows 10 的统一的写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [有关企业与 Pro 已分配的访问](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [用于企业和教育版的 shell 启动程序](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [锁定资源](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [启用嵌入模式和在 Windows IoT 企业版上使用后台任务](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [在你的组织中配置 Windows 遥测](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [配置运行 Windows 桌面版的网亭和共享设备](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
