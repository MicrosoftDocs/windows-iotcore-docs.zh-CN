---
title: 构建更安全使用 Windows 10 IoT Core 设备
author: TorstenStein
ms.author: torstens
ms.date: 08/28/2017
ms.topic: article
description: 了解如何通过启用安全启动，实现了 Tpm，和的详细信息生成更安全的设备。
keywords: windows iot、 安全性、 固件、 安全启动，TPM，Bitlocker 加密
ms.openlocfilehash: b7340ce168f766eb13e00bfca39619e92a931c30
ms.sourcegitcommit: 2e7e9555fe71ca60b5f41dbf06051a50520a368a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491716"
---
# <a name="building-more-secure-devices-with-windows-10-iot-core"></a>构建更安全使用 Windows 10 IoT Core 设备

## <a name="introduction"></a>简介  

Windows 10 IoT 核心版提供了强，企业级安全功能，可以利用这些较小的、 资源约束类 IoT 设备上。 若要提供切实的益处这些安全功能，硬件平台还必须提供一种方法，若要定位到它们。 本文提供了概括性指导，到 OEM 设备构建者和安全意识的创建者想要选择适当的硬件以及生成、 配置和交付更安全的 IoT 设备向其客户。
![数据安全性](../media/SecurityFlowAndCertificates/DataRestExecutionMotion.png)

## <a name="building-a-more-secure-iot-device"></a>构建更安全的 IoT 设备  
使用 IoT Core 构建更安全 IoT 设备的过程包括选择的硬件以支持平台的安全功能，以及已启用安全性的 IoT 设备的生产。

![设备生成过程](../media/SecurityFlowAndCertificates/DeviceBuildProcess.png)


## <a name="choosing-security-enabled-hardware"></a>选择已启用安全性的硬件
虽然 IoT 核心安全功能内置到平台以保护客户数据，它依赖于硬件的安全功能，以充分利用这些功能。 实际上，软件无法保护本身可以操作内存，因此不存在信任锚点或可以通过单独的软件提供的不可变的设备标识。 有几种方法来提供基于硬件的安全，如智能卡、 受信任的平台模块 (Tpm) 或 SoC.中内置的安全功能 

有关支持的硬件平台的详细信息，请参阅[Soc 和自定义看板](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards)。 

### <a name="trusted-platform-module"></a>受信任的平台模块
IoT 核心版使用受信任的平台模块 2.0 (TPM 2.0) 作为硬件的安全平台。 我们建议 Oem 使用提供 TPM 2.0 能够充分利用 IoT 核心安全功能，如 BitLocker、 安全启动、 Azure 凭据存储，以及其他的硬件平台。 有两个选项适用于生产设备来实现 TPM： 作为离散 TPM (dTPM) 或固件 TPM (fTPM)。 可从多个制造商，如 Infineon、 NazionZ，及其他离散 Tpm。 某些 SoC 制造商提供 fTPM 实现看板支持包 (BSP) 的一部分。 

有关 Tpm 的详细信息，请参阅[TPM 概述](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/tpm)并[如何设置 TPM](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/setuptpm)。

### <a name="storage-options"></a>存储选项
开发板，如常用的 Raspberry Pi 3，提供的灵活性，并允许开发人员能够轻松地启动任何平台通过可移动的 SD 卡。 适用于大多数行业 IoT 设备，这种灵活性是不可取的并可以使攻击容易实现的目标设备。 相反，在设计时您的硬件，请考虑对较小的、 低成本 IoT 设备使用 eMMC 存储。 嵌入的存储可以大大增强其难度单独从设备的内容，并进而，降低数据被盗的可能性或引入到设备上的恶意软件。

## <a name="create-a-retail-image"></a>创建零售映像 
当[创建 Windows IoT Core 零售映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)，确保没有开发人员工具，允许远程访问并且调试在生产系统上存在，将根据这些潜在可打开你的设备受到攻击。 如果使用像这样的开发人员工具[Windows Device Portal](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/remotedisplay)， [FTP 服务器](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ftp)， [SSH](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ssh)，或者[PowerShell](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/powershell)在映像中开发，请确保你测试和验证的零售映像 IoT Core 上您不包括这些工具的方案。

### <a name="user-accounts"></a>用户帐户
大多数用户都熟悉利用这一概念*所有权*的电脑和手机之类的设备： 了解和设置凭据，才能访问设备的个性化设置设备时已取消装箱。 与不同的使用者电脑和手机，IoT 设备不应作为常规用途计算设备。 相反，它们是通常的单应用、 固定用途设备。 尽管 Windows 支持可以远程连接到设备在开发周期内的设备管理员的概念，工业 IoT 设备上的此类支持可能会带来威胁，尤其是在使用弱密码。 一般情况下，我们建议在 IoT Core 设备上创建任何默认帐户或密码。

## <a name="lockdown-a-retail-image"></a>锁定零售映像
在常规用途计算设备，如 Pc，用户可以安装应用程序，并更改设置，包括安全功能，以确保设备最适合其需求。 IoT 设备的大多数都是固定的函数-的设备将设备生存期内更改它们的用途。 它们接收软件更新，或启用其操作的边界，如改进的 UI 或温度条例上智能调温器内的功能更新。 此信息可以用于完全锁定 IoT 设备通过仅允许已知且受信任代码的执行。 在 Windows 10 IoT Core 上的设备保护可帮助保护 IoT 设备通过确保未知或不受信任的可执行代码，不能锁定的设备上运行。

Microsoft 将提供[统包安全包](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)以便启用 IoT Core 设备上的主要安全功能。 这样，创建完全锁定 IoT 设备的设备构建者。 包将帮助了解：

* 预配安全启动密钥和上启用该功能支持的 IoT 平台。
* 安装程序并使用 BitLocker 设备加密配置。 
* 启动设备锁定为只允许已签名的应用程序和驱动程序的执行。

分步指南中所述[启用安全引导、 BitLocker、 和 Device Guard](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/securebootandbitlocker)部分。

## <a name="device-production"></a>设备生产
锁定映像验证后，它可以用于生产。 有关详细信息请参阅[生产的 IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/)。
