---
title: 连接设备到云
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何将设备连接到云。 使用受信任的平台模块 (TPM) 微控制器设备来存储数据和执行计算。
keywords: windows iot，Azure，安全性，受信任的平台模块，SoC
ms.openlocfilehash: a6a67de380af9b88281b1134f63b4de7496fdd73
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230084"
---
# <a name="connect-your-device-to-the-cloud"></a>连接设备到云

在设备上存储安全信息（如密码或证书）可能会使设备容易遭受曝光。 泄露的密码是一种确保泄露设备或整个系统的安全性的方法。 在 Windows 系列中，支持操作系统安全的技术是受信任的平台模块。

[受信任的平台模块](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) 设备是可以存储数据和执行计算的微控制器。 它可以是焊接到计算机主板上的离散芯片，也可以是制造商 (SoC) 芯片上集成到系统中的模块。 

## <a name="inside-the-tpm"></a>TPM 内部 

TPM 的一项重要功能是它只写内存。 根据数据，TPM 还可以基于数据中的数据来计算加密哈希 (例如 [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)) 。
由于哈希，无法发现机密，但如果对双方的通信都知道密码，则可能会确定是否从该机密产生了从另一方收到的哈希。

使用加密密钥的基本思路：机密 (也称为共享访问密钥) 在设备预配过程中建立并共享 IoT 设备和云。 从此时开始，将使用从机密派生的 HMAC 对 IoT 设备进行身份验证。

## <a name="device-provisioning"></a>设备预配 

适用于 Windows 10 IoT 核心版设备的设置工具称为 IoT 核心仪表板，可轻松[下载](https://go.microsoft.com/fwlink/?LinkID=708576)和配置。

仪表板会生成操作系统映像，并将设备安全连接到 Azure。 这是通过将物理设备与 Azure IoT 中心中的设备 ID 相关联并将设备特定的共享访问密钥 imprinting 到设备的 TPM 来完成的。 

对于没有 TPM 芯片的设备，此工具可以安装软件模拟的 TPM。 这并不提供安全性，但允许你使用 maker 设备开发应用 (如 Raspberry Pi 2 或 3) ，并在具有硬件 TPM 的设备上具有安全性 "亮起"，而无需更改应用。 

若要将设备连接到 Azure，请单击 "连接到 Azure" 选项卡：

![打开连接到 Azure "选项卡](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

系统将要求你登录到 Azure 帐户。 选取所需的 Azure IoT 集线器实例，并将你的物理设备与它相关联。 如果 Azure 订阅中没有任何 IoT 中心实例，则该工具将允许你创建一个免费的实例。 

选择要与设备关联的 IoT 中心和设备 ID 后，你可以在 TPM 上为该设备的共享访问密钥加上一个选项：

![预配设备](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

你的设备现在可以通过安全方式连接到 Azure。 

你还可以使用 Windows 设备门户在设置后首次连接到 internet 时，动态获取 IoT 中心连接字符串。 这可以从设备门户中的 "Azure 客户端" 选项卡完成。

![Azure 客户端选项卡](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a>有用资源：
* [将你的应用连接到 Azure](../connect-to-cloud/ConnectAppToCloud.md)
* [为 IoT Core 构建安全应用](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
