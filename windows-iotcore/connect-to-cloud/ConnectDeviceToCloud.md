---
title: 将设备连接到云
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何将设备连接到云。
keywords: windows iot，Azure，安全性，受信任的平台模块、 SoC
ms.openlocfilehash: ff54bbfa1aaf30d08107fac72ba59ae5a04aa247
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59511004"
---
# <a name="connect-your-device-to-the-cloud"></a>将设备连接到云

将安全信息，例如密码或证书存储在设备上无法使设备受到危害。 密码是欢心办法危及设备或整个系统的安全。 在 Windows 系列，支持的操作系统的安全性的技术是受信任的平台模块。

一个[受信任的平台模块](https://en.wikipedia.org/wiki/Trusted_Platform_Module)(TPM) 设备是可以存储数据和执行计算的微型控制器。 它可以是焊接到计算机的主板的离散芯片或集成到芯片 (SoC) 上的系统制造商的模块。 

## <a name="inside-the-tpm"></a>TPM 内部 

TPM 的关键功能是它只写的内存。 根据在其中的数据，TPM 还可以计算的加密哈希 (如[HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code))、 基于该数据。
不可能的秘密给定哈希，但如果机密识别这两个参与方的通信，就可以确定是否从另一方收到的哈希通过生成的该机密。

使用加密密钥的基本理念： 建立并在设备预配过程期间的 IoT 设备和云之间共享的机密 （也称为共享的访问密钥）。 从该点开始，将使用派生自该机密的 HMAC IoT 设备进行身份验证。

## <a name="device-provisioning"></a>设备预配 

预配 Windows 10 IoT Core 设备的工具称为 IoT 核心版仪表板，可以从下载[下载页面](http://go.microsoft.com/fwlink/?LinkID=708576)。

在仪表板生成的 OS 映像，并安全地将你的设备连接到 Azure。 这是通过将物理设备与 Azure IoT 中心中的设备 ID 相关联并 imprinting 到设备的 TPM 的特定于设备的共享的访问密钥。 

对于不带 TPM 芯片的设备，该工具可以安装软件模拟的 TPM。 这不提供安全性，但允许您开发应用程序使用的创建者设备 （如 Raspberry Pi 2 或 3） 和使用 TPM 的硬件设备上有"点燃"的安全，而无需更改应用。 

若要将设备连接到 Azure 中，单击"连接到 Azure"选项卡上：

![打开连接到 Azure 的选项卡](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

你将需要登录到你的 Azure 帐户。 选择 Azure IoT 中心的所需的实例，并将你的物理设备与之关联。 如果在 Azure 订阅中没有任何 IoT 中心实例，该工具将允许您创建一个免费的实例。 

选择 IoT 中心和设备 ID 将与设备相关联之后, 可以上的共享的访问密钥，该设备的标记在 TPM 上：

![设备预配](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

你的设备现在已准备好以安全方式连接到 Azure。 

Windows Device Portal 还可用于动态获取 IoT 中心连接字符串，当它首次连接到 internet 后正在预配。 这可以从设备门户的"Azure 客户端"选项卡。

![Azure 客户端选项卡](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a>有用的资源：
* [将应用连接到 Azure](../connect-to-cloud/ConnectAppToCloud.md)
* [IoT 核心版为构建安全应用程序](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
