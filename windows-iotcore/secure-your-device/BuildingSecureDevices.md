---
title: 构建安全使用 Windows 10 IoT Core 设备
author: TorstenStein
ms.author: torstens
ms.date: 08/28/2017
ms.topic: article
description: 了解如何构建安全的设备通过启用安全启动，实现了 Tpm，和的详细信息。
keywords: windows iot、 安全性、 固件、 安全启动，TPM，Bitlocker 加密
ms.openlocfilehash: 4170b2819606b3862bb7fabfc62f73be0351cccf
ms.sourcegitcommit: fcc0c6add468040e2f676893b44b260e3ddc3c52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65779409"
---
# <a name="building-secure-devices-with-windows-10-iot-core"></a>构建安全使用 Windows 10 IoT Core 设备

## <a name="introduction"></a>简介  

使用 Windows 10 IoT Core 时，Microsoft 将强企业级安全功能，可以利用这些较小，资源受限类的 IoT 设备上。 若要提供切实的益处这些安全功能，硬件平台还必须提供一种方法，若要定位到它们。 本文档提供了概括性指导 OEM 设备构建者和安全意识制造商想要选择适当的硬件和生成、 配置和安全 IoT 设备寄给他们的客户。
![数据安全性](../media/SecurityFlowAndCertificates/DataRestExecutionMotion.png)

## <a name="building-a-secure-iot-devices"></a>构建安全的 IoT 设备  
本部分将通过构建 Windows IoT core 的安全 IoT 设备的过程帮助开发人员和 Oem。 我们将解决所选内容的支持平台的安全功能的硬件，以及启用的安全 IoT 设备的生产环境。

![设备生成过程](../media/SecurityFlowAndCertificates/DeviceBuildProcess.png)

## <a name="firmware"></a>固件  
在常规用途计算了"打开"，如 Pc 的设备，用户可以通过各种键组合 （例如 F2 进入 UEFI 设置大多数 pc 立即） 的设备启动期间访问固件设置。 这可以允许用户在该平台启动，以及启用和禁用各种设备端口、 函数和其他潜在的安全功能，可在设备上进行更改。  

给定此类修改的敏感性质，IoT 设备应不起作用"打开设备"和等更像"锁定"设备，类似于移动电话，其中对固件通常不允许访问工作。  这通常可以通过确保在你的生产设备中使用锁定的固件来完成。 锁定的固件应可通过固件提供程序。  锁定的固件不可用或可能不合适，如创建者，供使用的位置的设备上至少应考虑保护通过管理员强密码的固件设置访问权限。

## <a name="choosing-security-enabled-hardware"></a>选择启用了安全硬件
虽然 Windows IoT Core 构建到平台以保护客户数据的安全功能，它依赖于硬件的安全功能，以充分利用这些功能。 实际上，软件无法进行自我保护可操作内存并不存在信任锚点或可以通过单独的软件提供的不可变的设备标识。 有几种方法来提供基于硬件的安全，例如智能卡，受信任的平台模块 (TPM) 或安全功能构建到 SoC. 

详细了解受支持的硬件平台，请参阅部分[Soc 和自定义看板](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards) 

### <a name="trusted-platform-module"></a>受信任的平台模块
Windows IoT Core 使用 TPM 2.0 作为硬件的安全平台。 Oem 建议使用一个硬件平台，提供要充分利用 Windows IoT Core 安全功能，例如 BitLocker、 安全启动、 Azure 凭据存储和其他人的 TPM 2.0。 有两个选项适用于生产设备为实现 TPM，作为离散 TPM (dTPM) 或固件 TPM (fTPM)。 可从多个制造商如 Infineon、 NazionZ 及其他离散 Tpm。 某些 SoC 制造商 BSP 的一部分提供 fTPM 实现。 

有关 Tpm 有关的详细信息，请[TPM 概述](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/tpm)并[如何设置 TPM](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/setuptpm)。

### <a name="storage-options"></a>存储选项
开发板，如常用的 Raspberry Pi 3，提供的灵活性，并允许开发人员能够轻松地启动任何平台通过可移动的 SD 卡。 适用于大多数行业 IoT 设备，这种灵活性是不可取的并可以使此类设备的攻击容易实现的目标。 相反，在设计时您的硬件，请考虑对较小的、 低成本 IoT 设备使用 eMMC 存储。 嵌入的存储可以大大增强其难度单独从设备的内容并反过来，降低了引入恶意软件到设备或数据被盗的可能性。

## <a name="creating-a-retail-image"></a>创建零售映像 
当[创建 Windows IoT Core 零售映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)，确保没有开发人员工具，允许远程访问并且调试在生产系统上存在，将根据这些潜在可打开你的设备受到攻击。 请确保，如果使用像这样的开发人员工具[Windows Device Portal](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/remotedisplay)， [FTP 服务器](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ftp)， [SSH](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ssh)，或者[PowerShell](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/powershell)映像中在开发期间，您测试和验证您的方案不包括这些工具的零售 IoT 核心版映像上。

### <a name="user-accounts"></a>“用户帐户”
大多数用户都熟悉这一概念时取消装箱并设置凭据来访问设备执行"所有权"的电脑和手机的想法之类的设备的个性化设置设备。 与不同的使用者电脑和手机，IoT 设备不应作为常规用途计算设备。 相反，它们是通常的单应用、 固定用途设备。 尽管 Windows 支持可以远程连接到设备在开发周期内的设备管理员的概念，工业 IoT 设备上的此类支持可能会带来威胁，尤其是在使用弱密码。 一般情况下，Microsoft 建议，应在 Windows 10 IoT Core 设备上创建没有"default"帐户或密码。

## <a name="lockdown-a-retail-image"></a>锁定零售映像
在常规用途计算设备，如 Pc，用户可以安装应用程序、 更改设置，包括安全功能，以最适合的设备将函数定义到套件其操作需要。 IoT 设备的大多数都是固定的函数-的设备将设备生存期内更改目的。 这些设备仍会接收软件更新或启用的功能更新其操作的边界内，例如改进智能调温器上的用户界面或温度调整。 此信息可以用于完全锁定 IoT 设备通过仅允许已知且受信任代码的执行。 在 Windows 10 IoT Core 上的设备保护可帮助保护 IoT 设备通过确保未知或不受信任的可执行代码，不能锁定的设备上运行。

Microsoft 将提供[统包安全包](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)以便于轻松启用 IoT Core 设备上的主要安全性功能，允许设备生成器以生成完全锁定 IoT 设备。 包将帮助了解：

* 预配安全启动密钥和受支持的 IoT 平台上启用功能
* 安装和配置使用 BitLocker 设备加密 
* 启动设备锁定为只允许已签名的应用程序和驱动程序的执行

分步指南中所述[启用安全引导、 BitLocker、 和 Device Guard](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/securebootandbitlocker)部分。
