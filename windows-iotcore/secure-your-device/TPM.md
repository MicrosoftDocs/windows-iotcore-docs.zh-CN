---
title: 受信任的平台模块 (TPM)
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用受信任的平台模块启用加密功能，从而更好地保护设备。
keywords: windows iot，安全性，受信任的平台模块，TPM，加密，密钥
ms.openlocfilehash: 2456d403d9c593ac656587d94ec81dc736031b6b
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782389"
---
# <a name="trusted-platform-module-tpm-on-windows-10-iot-core"></a>受信任的平台模块 (Windows 10 IoT Core 上的 TPM) 

## <a name="what-is-tpm"></a>什么是 TPM？
受信任的平台模块 (TPM) ，是一种加密协处理器，其中包括用于随机编号生成的功能、安全生成的加密密钥和其使用限制。 它还包括远程证明和密封的存储等功能。
TPM 的技术规范是公开发布的，由受信任的计算组驱动 (TCG) 。 2.0 年 10) 2014 月发布的最新版本 TPM (，它是一种用于添加新功能并修复以前的 TPM 1.2 弱点的规范的主要重新设计。

## <a name="why-tpm"></a>为什么选择 TPM？  
合并 TPM 的计算机可以创建加密密钥并对其进行加密，以便只能由 TPM 进行解密。 此过程通常称为 **"覆盖** " 或 **"绑定"** 密钥，可帮助防止密钥泄漏。 每个 TPM 都有一个名为 "包装" 的主密钥，它存储在 TPM 本身中。 在 TPM 中创建的密钥的隐私部分从不暴露给其他组件、软件、进程或者人员。  

合并了 TPM 的计算机还可以创建一个密钥，该密钥不仅被包装，而且还与特定的平台测量相关。 只有在那些平台度量具有的值与创建该密钥时具有的值相同时，才能取消覆盖这种类型的密钥。 此过程称为将密钥 **"密封"** 到 TPM。 解密密钥称为 **"解封"**。 TPM 还可以对在 TPM 外部生成的数据进行密封和解封。 利用此密封密钥和软件（如 BitLocker 驱动器加密），可以在满足特定硬件或软件条件之前锁定数据。  

使用 TPM 时，密钥对的专用部分与操作系统控制的内存保持独立。 可以将密钥密封到 TPM，并对系统的状态进行一些保证，即，确定) 系统的 "可信任性" 的系统 (保证，在未密封密钥并将其释放以便使用之前。 因为 TPM 使用自身的内部固件和逻辑电路来处理指令，所以它不依赖于操作系统，也不会受操作系统或应用程序中可能存在的漏洞影响。

## <a name="tpm-architecture"></a>TPM 体系结构
_TPM 1.2 与 TPM 2.0 之间的差异。_  
TPM 规范开发了两次。 第一次是从 1.1 b 开发到1.2，其中包含由规范委员会请求/确定的新功能。 此功能爬出形式的演变使得最终的 TPM 1.2 规范非常复杂。 最后，SHA-1 (的加密漏洞是 TPM 1.2) 中最强大的商业算法，这会导致需要进行更改。 TPM 体系结构从头开始重新设计，导致 TPM 2.0 的集成和统一设计更加紧密。  

与以前的 TPM 1.2 相比，更改和增强包括：

* 支持其他加密算法
* 对应用程序的 TPM 可用性的增强
* 增强的授权机制
* 简化的 TPM 管理
* 增强了平台服务安全性的附加功能

> [!NOTE] 
> Windows IoT Core 仅支持 TPM 2.0，并且不支持过时的 TPM 1.2。

## <a name="what-is-tbs"></a>什么是 TBS？ 
TPM 基本服务 (TB) 功能是允许对 TPM 资源进行透明共享的系统服务。 它通过远程过程调用 (RPC) 来共享同一物理计算机上多个应用程序中的 TPM 资源。 它使用调用应用程序指定的优先级跨应用程序集中访问 TPM。  

TPM 提供旨在在平台中提供信任的加密功能。 由于 TPM 是在硬件中实现的，因此它具有有限的资源。 TCG 定义 TPM 软件堆栈 (TSS) ，它利用这些资源为应用程序软件提供受信任的操作。 但是，并不是为了与可能使用 TPM 资源的操作系统软件并行运行 TSS 实现。 TBS 功能通过以下方式解决了这一问题：启用每个与 TBS 通信的软件堆栈，以将 TPM 资源检查用于计算机上可能正在运行的任何其他软件堆栈。

## <a name="tpm-solutions-available-on-windows-iot-core"></a>Windows IoT Core 上提供的 TPM 解决方案  
_一些有关软件 TPM (sTPM) ，固件 TPM (fTPM) ，离散 TPM (dTPM) .。。_

### <a name="firmware-tpm-ftpm"></a>固件 TPM (fTPM)   
固件 TPM (fTPM) 需要在 Raspberry Pi 2 或3上当前未实现的特殊处理器/SoC 支持。 MinnowBoard 最大要求固件版本0.80 或更高版本。 默认情况下，DragonBoard410c 提供已启用的 fTPM 功能。  

### <a name="discrete-tpm-dtpm"></a>独立 TPM (dTPM)   
所有方法都将独立的 TPM (dTPM) 视为受信任的最佳解决方案。  
Windows IoT Core 支持多个 dTPM 芯片和 PCB 模块制造商：

> | 制造商 | 网页 | Modul 类型 | TPM 芯片 |
> |-------------|----------|----------|----------| 
> | Infineon | [Infineon TPM](https://www.infineon.com/cms/en/product/evaluation-boards/iridium9670-tpm2.0-linux/)| Evalboard | [Infineon SLB9670 TPM 2。0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |
> | Pi3g | [Pi3g.com](https://pi3g.com/eigene-produkte/)| 批量产品 & Evalboard | [Infineon SLB9670 TPM 2。0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |


### <a name="software-tpm-stpm"></a>软件 TPM (sTPM)   
软件 TPM (sTPM) 也称为 TPM 模拟器。 它独立于平台，在 Windows IoT Core 上受支持。  

> [!NOTE]
> sTPM 仅用于开发目的，不提供任何真正的安全优势。  


## <a name="samples"></a>示例  
<!--
* [TBSSample project C++](https://developer.microsoft.com/en-us/windows/iot/samples/tbssample)
  This tutorial demonstrates how to create a basic C++ application that uses TBS to poll the TPM.  -->
* [Urchin 库示例](https://github.com/ms-iot/security/tree/master/Urchin/Lib) 本教程演示如何创建一个使用 [Urchin 库](https://github.com/ms-iot/security)来演练 TPM 功能的示例 c + + 应用程序。 Urchin 是一个符合规范的库，它派生自 TPM 2.0 参考实现。 它向客户端提供封送/取消封送所有数据结构、正确计算授权、执行参数加密和审核的功能。

## <a name="additional-resources"></a>其他资源  
* [受信任的平台模块 (TPM) 规范](http://www.trustedcomputinggroup.org/developers/trusted_platform_module) 
* [TCG TPM 2.0 库规范](http://www.trustedcomputinggroup.org/resources/tpm_library_specification)
* [TPM 基本服务](https://msdn.microsoft.com/library/windows/desktop/aa446796(v=vs.85).aspx) 
* [启用安全启动和 BitLocker](SecureBootAndBitLocker.md)

