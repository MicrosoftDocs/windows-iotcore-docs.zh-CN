---
title: 通过 Windows 10 IoT 核心版生成更安全的设备
author: TorstenStein
ms.author: torstens
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何通过启用安全启动、实现 Tpm 等来构建更安全的设备。
keywords: windows iot，安全性，固件，安全启动，TPM，Bitlocker，加密
ms.openlocfilehash: 0a0768aba88967b2c1bcaaf87786c5dd0fd3ad40
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230713"
---
# <a name="building-more-secure-devices-with-windows-10-iot-core"></a>通过 Windows 10 IoT 核心版生成更安全的设备

## <a name="introduction"></a>简介  

Windows 10 IoT 核心版提供了强大的企业级安全功能，可用于较小的、资源受限的 IoT 设备类别。 为了使这些安全功能提供实实在在的优势，硬件平台还必须提供一种方法来定位它们。 本文提供了 OEM 设备构建者和安全意识制造商的高级指导，他们希望选择适当的硬件并构建、配置更安全的 IoT 设备并将其交付给客户。
![数据安全性](../media/SecurityFlowAndCertificates/DataRestExecutionMotion.png)

## <a name="building-a-more-secure-iot-device"></a>构建更安全的 IoT 设备  
用 IoT Core 构建更安全的 IoT 设备的过程包括选择支持平台安全功能的硬件，以及生产启用安全功能的 IoT 设备。

![设备生成过程](../media/SecurityFlowAndCertificates/DeviceBuildProcess.png)


## <a name="choosing-security-enabled-hardware"></a>选择启用安全的硬件
尽管 IoT 核心在平台中内置了用于保护客户数据的安全功能，但它依赖于硬件安全功能来完全利用这些功能。 事实上，软件无法自行保护，因为可以对内存进行操作，并且没有可通过软件单独提供的信任密钥或不可变设备标识。 有多种方法可提供基于硬件的安全性，例如智能卡、受信任的平台模块 (Tpm) ，或在 SoC 中内置的安全功能。 

有关支持的硬件平台的详细信息，请参阅 [soc 和自定义板](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards)。 

### <a name="trusted-platform-module"></a>受信任的平台模块
IoT 核心使用受信任的平台模块 2.0 (TPM 2.0) 为硬件安全平台。 建议 Oem 使用提供 TPM 2.0 的硬件平台，以充分利用 IoT 核心安全功能，例如 BitLocker、安全启动、Azure 凭据存储等。 生产设备有两个选项可用于实现 TPM：作为合理的 TPM (dTPM) 或固件 TPM (fTPM) 。 若干制造商（如 Infineon、NazionZ 等）提供了离散 Tpm。 某些 SoC 制造商将 fTPM 实现作为板支持包的一部分提供 (BSP) 。 

有关 Tpm 的详细信息，请参阅 [Tpm 概述](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm) 和 [如何设置 tpm](https://docs.microsoft.com/windows/iot-core/secure-your-device/setuptpm)。

### <a name="storage-options"></a>存储选项
与流行的 Raspberry Pi 3 一样，开发板可提供灵活性，并使开发人员能够通过可移动 SD 卡轻松启动任何平台。 对于大多数业界 IoT 设备，这种灵活性并不理想，可使设备成为攻击的目标。 相反，在设计硬件时，请考虑对小型、低成本的 IoT 设备使用 eMMC 存储。 利用嵌入的存储空间，可以很难将内容从设备中分离出来，进而降低数据被盗的可能性或引入到设备上的恶意软件。

## <a name="create-a-retail-image"></a>创建零售映像 
[创建 Windows IoT 核心零售映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)时，请确保生产系统中不存在允许远程访问和调试的开发人员工具，因为这可能会使你的设备遭受攻击。 如果在开发过程中使用映像中的开发人员工具（如[Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/remotedisplay)、 [FTP 服务器](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)、 [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/ssh)或[PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) ），请确保在不包含这些工具的零售 IoT 核心映像上测试和验证方案。

### <a name="user-accounts"></a>用户帐户
大多数用户都熟悉了获取设备（如电脑和手机）的 *所有权* 的概念：对设备进行取消装箱和设置凭据以访问设备时，对其进行个性化的理念。 不同于消费者电脑和手机，IoT 设备并不旨在用作常规用途计算设备。 相反，它们通常是单应用、固定用途设备。 尽管 Windows 支持在开发周期内可远程连接到设备的设备管理员的概念，但在行业 IoT 设备上，此类支持可能会造成威胁，尤其当使用弱密码时。 通常，建议不要在 IoT Core 设备上创建默认帐户或密码。

## <a name="lockdown-a-retail-image"></a>锁定零售映像
在常规用途计算设备（如 Pc）上，用户可以安装应用程序并更改设置，包括安全功能，以确保设备最适合其需求。 大多数 IoT 设备是固定功能设备，不会在设备生存期内改变其用途。 它们会在其操作边界内接收软件更新或启用功能更新，如智能恒温器上改进的 UI 或温度规定。 此信息可用于通过只允许执行已知和受信任的代码来完全锁定 IoT 设备。 Windows 10 IoT 核心版上的设备防护可以确保无法在锁定的设备上运行未知或不受信任的可执行代码，从而帮助保护 IoT 设备。

Microsoft 提供了 [全包式安全包](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) ，有助于在 IoT 核心设备上启用关键安全功能。 这允许设备构建者创建完全锁定的 IoT 设备。 此包将帮助你：

* 设置安全启动密钥并在支持的 IoT 平台上启用该功能。
* 使用 BitLocker 进行设备加密的设置和配置。 
* 启动设备锁定，只允许执行已签名的应用程序和驱动程序。

[启用安全启动、BitLocker 和设备防护](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker)部分介绍了循序渐进指南。

## <a name="device-production"></a>设备生产
锁定映像经过验证后，即可用于制造。 有关详细信息，请参阅 [IoT 核心制造](https://docs.microsoft.com/windows-hardware/manufacture/iot/)。
