---
title: Windows 10 IoT 企业版概述
author: saraclay
ms.author: saclayt
ms.date: 01/18/2017
ms.topic: article
description: 了解 Windows 10 IoT 企业版是什么，以及可以用它执行什么操作。
keywords: Windows 10 IoT 企业版, 企业, 二进制, Windows
ms.openlocfilehash: 4dd488ece7ae60074de75756272f52f392ebf322
ms.sourcegitcommit: 38de3aad11845248dac393ffc51b18c5596af4c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68155385"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Windows 10 IoT 企业版概述

## <a name="what-is-windows-10-iot-enterprise"></a>什么是 Windows 10 IoT 企业版？
Windows 10 IoT 企业版是完整版本的 Windows 10，可以为 IoT 解决方案提供企业可管理性和安全性。 它是等效于 Windows 10 企业版的二进制文件, 因此, 如果您已经了解 Windows 10 企业版的工作原理, 则很多知识可转移 Windows 10 IoT 企业版。 但是, 当涉及到授权和分发时, 桌面版本和 IoT 版本会有所不同。 

## <a name="getting-started"></a>入门 
在与嵌入的/IoT 分发服务器联系之前, 建议使用其中一种[设备](https://solutionsdirectory.intel.com/solutions-directory/processors/736/processors/766/processors/782/processors/788/processors/869/processors/879/processors/883/processors/888/processors/1053/processors/1058/processors/1103/processors/1107/processors/1110/processors/1117/processors/1133/processors/1135/processors/1139/processors/1141/processors/1175/processors/1192/processors/1344/processors/1348/processors/1349/processors/1371/processors/1392/processors/1729/processors/2284)。  您可以使用 Windows 10 企业[版的评估副本](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise)加载您的 PC 或推荐设备, 以便立即开始制作原型。

若要开始使用 Windows 10 IoT Enterprise 进行生产, 你需要通过[此列表](http://wincom.blob.core.windows.net/documents/Windows_IoT_Distributor_Information.pdf)与分销商联系。 

## <a name="fixed-purpose-devices"></a>固定用途设备 

> [!TIP]
> 若要完全了解所有 Windows 10 IoT 企业版使用方案，请查看许可协议。

Windows 10 IoT 企业版已获得许可, 可让你构建固定用途的设备, 如瘦客户端、ATM 机、销售点终端、工业自动化系统等。许可协议中有特定的补助和限制。 

通常, 固定用途的设备与常规用途设备在以下方面有所不同:  
* 已通过“分配访问权限”或“Shell 启动程序”功能将设备与单个应用程序或固定的应用程序集锁定。  
* 当最终客户收到设备时, 设备会立即开机。 若要实现这一点，可以将设备映像配置为跳过正常的 Windows 全新安装体验。
* 键盘、USB 端口和设备策略都已锁定，使设备只能用于固定用途。  
* OEM 会将软件附加到设备，以这种方式将设备作为一个完整的产品许可给用户，并在其自己的协议中阐明特定的 Windows 条款。

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Windows 10 IoT 核心版和 Windows 10 IoT 企业版之间的差异
虽然 Windows 10 IoT 核心版和 Windows 10 IoT 企业版在名称上类似，但其提供的东西和支持的东西存在差异。 下面是一个功能列表，其中突出显示了版本差异。

如需最低要求的详细信息，请访问 [Windows 硬件站点](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview)。

> |             | Windows 10 IoT 核心版  |  Windows 10 IoT 企业版  |
> |-------------|----------|---------|
> | 用户体验 | 在启动时运行的单个 UWP 应用支持后台应用和服务。 | 带有高级锁定功能的传统 Windows Shell |
> | 支持无外设 | 是 | 是 |
> | 支持应用体系结构 | 仅 UWP | UWP 和 Win32 |
> | Cortana | *Cortana SDK* | 是 |
> | 域加入 | 仅 AAD | AAD 和传统域 |
> | 管理 | MDM | MDM |
> | 设备安全技术 | 适用于 IoT 的 TPM、安全启动、BitLocker、设备运行状况证明和 Device Guard | TPM、安全启动、BitLocker、Device Guard、Defender ATP 和设备运行状况证明 |
> | CPU 体系结构支持 | x86、x64、ARM32 和 ARM64 | x86、x64 和 ARM64 |
> | 授权 | 免版税联机许可协议和嵌入式 OEM 协议 | 直接和间接嵌入式 OEM 协议 |
> | 使用方案 | 数字告示, 智能建筑物, IoT 网关, HMI, 智能 Home, 可穿戴设备 | 业内板, POS, 展台, 数字告示, ATM, 医疗设备, 制造设备, 瘦客户端 |

## <a name="helpful-resources"></a>有用资源
> [!NOTE]
> 你的分发服务器上可能提供了其他资源, 用于说明 Windows EPKEA OEM 激活并提供有关生成生产就绪的 Windows IoT 企业[WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx)设备映像的指南。

* [桌面设备制造](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
* [适用于 Windows 10 的统一写入筛选器](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [为企业版和专业版分配的访问权限](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [适用于企业版和教育版的 Shell 启动程序](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [锁定资源](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [在 Windows IoT 企业版上启用嵌入模式和使用后台任务](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [在组织中配置 Windows 遥测](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [配置运行 Windows 桌面版的网亭和共享设备](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
