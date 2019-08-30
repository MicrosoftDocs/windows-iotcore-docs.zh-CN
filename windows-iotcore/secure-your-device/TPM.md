---
title: 受信任的平台模块 (TPM)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用受信任的平台模块启用加密功能, 从而更好地保护设备。
keywords: windows iot, 安全性, 受信任的平台模块, TPM, 加密, 密钥
ms.openlocfilehash: 70552a5f98891281879f1d45cbdbd671b56dd902
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533321"
---
# <a name="trusted-platform-module-tpm-on-windows-10-iot-core"></a>Windows 10 IoT Core 上的受信任的平台模块 (TPM)

## <a name="what-is-tpm"></a>什么是 TPM？
受信任的平台模块 (TPM) 是加密协处理器，其中包含随机数生成、加密密钥的安全生成以及它们的使用限制的功能。 它还包括诸如远程证明和密封存储等功能。
TPM 的技术规范由受信任的计算组 (TCG) 来制定并公开发行。 最新版本的 TPM 2.0（2014 年 10 月发布）主要对规范进行了重新设计，该版本添加了新的功能并修复了之前 TPM 1.2 的缺陷。

## <a name="why-tpm"></a>为什么选择 TPM？  
采用 TPM 的计算机可以创建加密密钥并对它们加密，这样一来它们只能由 TPM 进行解密。 此过程（通常称为“封装”或“绑定”密钥）可以帮助保护密钥以避免泄露。 每个 TPM 都有一个主“封装”密钥（称为存储根密钥），它存储在 TPM 本身的内部。 TPM 中创建的密钥的私钥部分永远不会公开给任何其他组件、软件、进程或用户。  

采用 TPM 的计算机还可以创建一个密钥，该密钥不仅可被封装而且还可以被绑定到特定平台测量。 仅当这些平台测量具有的值与创建该密钥时所具有的值相同时，才可以解封此类型的密钥。 此过程称为将密钥“封装”到 TPM。 解密密钥的过程称为“解封”。 TPM 还可以对 TPM 外部生成的数据进行封装和解封。 使用此封装的密钥和软件（例如 BitLocker 驱动器加密），可以锁定数据，直到符合特定的硬件或软件条件为止。  

借助 TPM，可保持密钥对的私钥部分独立于操作系统控制的内存。 可以将密钥封装到 TPM，并且在解封并释放该密钥以供使用之前，可以就系统的状态（定义系统”可信赖”的保证）提供某些保证。 由于 TPM 使用自己的内部固件和逻辑电路来处理指令，因此它不依赖于操作系统，并且它不会公开给操作系统或应用程序软件中可能存在的安全漏洞。

## <a name="tpm-architecture"></a>TPM 体系结构
_TPM 1.2 和 TPM 2.0 之间的区别。_  
TPM 规范已开发了两次。 第一次是从 1.1 b 开发到 1.2, 其中包含由规范委员会请求/确定的新功能。 此种功能扩展形式的演变使得最终的 TPM 1.2 规范非常复杂。 最后，SHA-1（TPM 1.2 中最强的商业算法）加密缺陷的暴露导致有必要对规范进行更改。 从头开始重新设计 TPM 体系结构，从而诞生更集成和统一设计的 TPM 2.0。  

相较于以前的 TPM 1.2，更改和增强功能如下所示：

* 对其他加密算法的支持
* 应用程序的 TPM 可用性增强
* 增强的授权机制
* 简化的 TPM 管理
* 增强平台服务安全性的其他功能

> [!NOTE] 
> Windows IoT Core 仅支持 TPM 2.0, 并且不支持过时的 TPM 1.2。

## <a name="what-is-tbs"></a>什么是 TBS？ 
TPM 基本服务 (TBS) 功能是系统服务，支持透明共享 TPM 资源。 它通过远程过程调用 (RPC) 在同一台物理计算机上的多个应用程序之间共享 TPM 资源。 它使用调用应用程序指定的优先级来集中跨应用程序的 TPM 访问。  

TPM 提供加密功能，设计用于提供平台内的信任。 由于通过硬件实现 TPM，因此它的资源有限。 TCG 定义的 TPM 软件堆栈 (TSS) 使用这些资源来提供应用程序软件的受信任操作。 但是，未预配为支持 TSS 实现可与操作系统软件（也可能正使用 TPM 资源）并行运行。 TBS 功能解决了此问题，方法是支持每个与 TBS 通信使用 TPM 资源的软件堆栈（可检查其他任何软件堆栈是否正在计算机上运行）。

## <a name="tpm-solutions-available-on-windows-iot-core"></a>Windows IoT 核心版上可用的 TPM 解决方案  
_有关软件 TPM (sTPM)、固件 TPM (fTPM)、离散 TPM (dTPM) 的一些字词 .。。_

### <a name="firmware-tpm-ftpm"></a>固件 TPM (fTPM)  
固件 TPM (fTPM) 需要特殊处理器/SoC 支持，因此，fTPM 当前在 Raspberry Pi 2 或 3 上无法实现。 MinnowBoard Max 需要版本 0.80 或更高版本的固件。 默认情况下, DragonBoard410c 提供已启用的 fTPM 功能。  

### <a name="discrete-tpm-dtpm"></a>离散 TPM (dTPM)  
离散 TPM (dTPM) 被认为是最值得信赖的解决方案。  
Windows IoT 核心版上受支持的 dTPM 芯片和 PCB 模块有多个制造商：

> | 制造商 | 网页 | Modul 类型 | TPM 芯片 |
> |-------------|----------|----------|----------| 
> | Infineon | [Infineon TPM](https://www.infineon.com/cms/en/product/evaluation-boards/iridium9670-tpm2.0-linux/)| Evalboard | [Infineon SLB9670 TPM 2。0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |
> | Pi3g | [Pi3g.com](https://pi3g.com/eigene-produkte/)| 批量产品 & Evalboard | [Infineon SLB9670 TPM 2。0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |


### <a name="software-tpm-stpm"></a>软件 TPM (sTPM)  
软件 TPM (sTPM) 也称为 TPM 模拟器。 它独立于平台，在 Windows IoT 核心版上受支持。  

> [!NOTE]
> sTPM 仅用于开发目的, 不提供任何真正的安全优势。  


## <a name="samples"></a>示例  
<!--
* [TBSSample project C++](https://developer.microsoft.com/en-us/windows/iot/samples/tbssample)
  This tutorial demonstrates how to create a basic C++ application that uses TBS to poll the TPM.  -->
* [Urchin 库示例](https://github.com/ms-iot/security/tree/master/Urchin/Lib) 本教程演示如何创建一个练习使用 [Urchin 库](https://github.com/ms-iot/security)的 TPM 功能的示例 C++ 应用程序。 Urchin 是一个派生自 TPM 2.0 参考实现、符合规范的库。 它向客户端提供封送/取消封送所有数据结构、正确计算授权、执行参数加密和执行审核功能。

## <a name="additional-resources"></a>其他资源  
* [受信任的平台模块 (TPM) 规范](http://www.trustedcomputinggroup.org/developers/trusted_platform_module) 
* [TCG TPM 2.0 库规范](http://www.trustedcomputinggroup.org/resources/tpm_library_specification)
* [TPM 基本服务](https://msdn.microsoft.com/library/windows/desktop/aa446796(v=vs.85).aspx) 
* [启用安全启动和 BitLocker](SecureBootAndBitLocker.md)

