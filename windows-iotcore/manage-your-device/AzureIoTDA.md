---
title: Azure IoT 设备代理
author: rcheeran
ms.author: rcheeran
ms.date: 06/25/2019
ms.topic: article
description: 了解如何使用 Windows IoT 上的 Azure IoT 设备代理管理设备。
keywords: windows iot，Azure IoT，Azure 设备代理，设备管理，远程管理
ms.openlocfilehash: 762ac7c3e0b40ce3bbe5cd33fba13838318198d7
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721442"
---
# <a name="azure-iot-device-agent"></a>Azure IoT 设备代理

当涉及到连接的设备时，远程设备管理是系统操作员所需的主要功能之一。 它使操作员能够远程配置属性和更新设备上的软件，而无需对设备进行本地或物理访问。 使用在家庭设备、HVAC 系统等设备上运行的 Windows IoT Core 和 Windows IoT Enterprise，需要可自定义的轻型设备管理解决方案。 虽然 Windows 10 版本已经基于[OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)提供了移动设备管理（MDM），但它主要用于具有管理工具（例如 SCCM 或 Intune）的企业解决方案。 尽管这些解决方案非常适合于处于企业设置中的设备，但在 IoT 解决方案中看到的更多样化的设置中会出现问题。 IoT 设备还需要轻型、小型设备管理解决方案，这可能是一项挑战。 Microsoft 还提供了使用[Azure IoT 中心](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)及其[SDK](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks)的设备管理功能。[Azure IoT 设备代理](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md)同时提供这两项功能：云中的设备管理功能通过 IoT 中心，可与移动设备管理使用的相同标准[配置服务提供程序（CSP）](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)配合使用。 借助 Azure 设备代理，Oem 可以构建提供这些设备管理功能的设备，而无需编写任何代码。 

Azure 设备代理是一种可用于启用远程设备管理功能的现成的开放源包。 Windows 10 IoT Core 和 Windows 10 IoT Enterprise 支持 Azure 设备代理，并可在通过 IoT 中心连接的设备上运行。 现在，Oem 可以构建支持 SCCM、Intune 或 Azure IoT 中心进行设备管理的设备，并使其客户能够选择最适合的设备管理解决方案。   

![Azure IoT 中心设备管理](../media/AzureIoTDM/azureDM.png)


## <a name="how-does-it-work"></a>如何运作？

[Azure IoT 设备代理](https://aka.ms/iot-core-azure-dm-client)由两个核心组件组成。 

设备预配服务客户端（DPS 客户端）自动执行设备设置。 它通过设备的注册密钥和 DPS ScopeID 连接到 Azure 设备预配服务。 Azure DPS 服务标识设备并在配置的 IoT 中心预配该设备，并将连接字符串返回到设备。 然后，DPS 客户端使用此连接字符串将设备连接到正确的 IoT 中心。  

设备管理客户端使用[配置服务提供程序](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)（CSP）启用远程设备管理功能 Azure 设备代理的远程管理功能支持插件模型，使你能够仅选择所需的功能。 除此之外，插件体系结构也是可扩展的。 你可以为所需的设备管理功能编写自己的插件，并将其添加到 Azure 设备代理。 所有设备管理功能都可以使用设备克隆或模块克隆属性和命令以远程方式进行访问，从而为所有 Windows IoT 设备启用单个窗格的管理方法。 有关可用设备管理功能的完整列表，请参阅[此](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/reference.md)

除此之外，Azure 设备代理还会为设备上运行的其他 UWP 应用程序创建和管理 SAS 令牌。 Azure 设备代理可以将其他 UWP 应用预配为设备克隆或模块克隆，并将其连接字符串添加到各自的 TPM 槽。 UWP 应用利用[Uwp 桥](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/uwp-bridge.md)从 TPM 槽读取连接字符串，并可以使用它连接到 IoT 中心。 

## <a name="how-to-get-started"></a>如何开始？

GitHub 上提供了 Azure IoT 设备代理。 该项目还包括快速入门的示例。 有关详细信息，请查看我们的[GitHub 存储](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md)库

## <a name="migrating-from-azure-device-agent-v1-to-v2"></a>从 Azure 设备代理 V1 迁移到 V2
如果你当前使用的是 v1 版本的设备代理，则 V1 与 V2 之间的一个重大更改是在 V2 版本中，Azure 设备代理不再与 UWP 应用共享连接。 利用 IoT 中心的增强功能，你现在可以同时拥有 UWP 应用和 Azure 设备代理的连接字符串，并且仍与 IoT 中心中的同一设备相关联。 有关更多详细信息，请参阅[此处](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/migration-from-old-client.md)。

有关 Azure 设备代理 V1 的详细信息，请参阅[此处](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm)。

## <a name="other-useful-tools"></a>其他有用工具 
### <a name="dm-mock-portal"></a>DM 模拟门户
[DM 模拟门户](https://github.com/ms-iot/azure-client-tools/blob/master/docs/dm-mock-portal/dm-mock-portal.md)是一个应用程序，可用于在单个设备上或跨多个设备（使用 IoT 中心的自动设备管理功能）设置设备克隆或模块克隆属性。 

### <a name="tpm-tool---limpetexe"></a>TPM 工具-Limpet
使用 Azure 设备预配服务，客户可以自动将设备与 IoT 中心后期生产进行关联和配置。 对于此过程，设备预配服务将需要一个唯一的 challengeable 设备 ID，以帮助在设备进入操作时安全地配置设备。 设备预配服务使用 TPM 的公共认可密钥（EKeyPub）来实现此目的。 若要向 DPS 注册设备，需要从设备搜集 EKeyPub。 此步骤的首选时间是在生产期间（在设备的行尾测试过程中）。 不过，如果需要，也可以在生产后执行此过程。  

Microsoft 提供了 Limpet 工具来简化设备预配服务注册过程。 根据制造设置，如果有可用的联机连接，则可以使用 Limpet 直接注册设备，也可以使用设备预配服务直接注册设备，Limpet 可以获取 EKeyPub，以便以后脱机注册设备正在预配服务。

有关 Limpet 的设备预配服务注册过程的更多详细信息，请[参阅此存储](https://github.com/ms-iot/azure-client-tools/blob/master/docs/limpet/limpet.md)库。

许可证： Limpet 根据 MIT 开源许可证授权。 
