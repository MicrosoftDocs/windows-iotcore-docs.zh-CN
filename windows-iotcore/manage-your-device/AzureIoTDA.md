---
title: Azure IoT 设备代理
author: rcheeran
ms.author: rcheeran
ms.date: 06/25/2019
ms.topic: article
description: 了解有关如何在 Windows IoT 上使用 Azure IoT 设备代理管理设备。
keywords: windows iot，Azure IoT，设备管理、 远程管理的 Azure 设备代理
ms.openlocfilehash: 4f7336cd1c4c2af903c0a74254e1b8e73ff077b9
ms.sourcegitcommit: 823ca02f515a577a2bdc469602a228365cb6ebf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67467679"
---
# <a name="azure-iot-device-agent"></a>Azure IoT 设备代理

当涉及到连接的设备时，远程设备管理是系统操作员需要的主要功能之一。 它使操作员能够配置属性，而无需具有本地或物理访问设备远程更新设备上的软件。 使用 Windows IoT Core 和 Windows IoT 企业版如家用电器、 HVAC 系统以及其他设备上运行，则可自定义、 浅权重设备管理解决方案的需求。 尽管 Windows 10 版本已提供移动设备管理 (MDM) 根据[OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)，这主要是利用与 SCCM 或 Intune 等管理工具的企业解决方案中。 虽然这些解决方案非常适合放置在企业设置的设备，它更多样化我们看到 IoT 解决方案中的设置中具有挑战。 IoT 设备也需要轻型、 小占用空间设备管理解决方案可以是一项挑战。 Microsoft 还提供设备使用的管理功能[Azure IoT 中心](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)并将其[SDK](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-devguide-sdks)。[Azure IoT 设备代理](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md)汇集了这两种功能： 在云中通过适用于同一个标准 IoT 中心设备管理功能[配置服务 Providers(CSP)](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference)与使用的移动设备管理。 使用 Azure 设备代理，Oem 可以构建无需编写任何代码提供这些设备管理功能的设备。 

Azure 设备代理是启用管理功能，远程设备就绪生成开放源代码包。 Azure 设备代理在 Windows 10 IoT 核心版和 Windows 10 IoT 企业版上受支持，适用于已连接设备通过 IoT 中心。 Oem 现在可以生成支持 SCCM、 Intune 或 Azure IoT 中心设备管理并将其保留到其客户能够选择适合它们的设备管理解决方案最佳设备。   

![Azure IoT 中心设备管理](../media/AzureIoTDM/azureDM.png)


## <a name="how-does-it-work"></a>如何运作？

[Azure IoT 设备代理](https://aka.ms/iot-core-azure-dm-client)包含 2 个核心组件。 

设备预配服务客户端 （DPS 客户端） 会自动将设备预配。 使用设备的注册密钥和 DPS ScopeID 连接到 Azure 设备预配服务。 Azure DPS 服务将设备标识和设置中配置 IoT 中心并连接字符串返回到设备。 然后，分发点客户端使用此连接字符串以将设备连接到合适的 IoT 中心。  

设备管理客户端启用远程设备管理功能，使用[配置服务提供商](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)，CSP) 的 Azure 设备代理的远程管理功能支持插件模型，可让你为选择所需的功能。 除此之外，插件体系结构是可扩展的。 您可以编写您自己的插件的设备管理功能，您需要并将其添加到 Azure 设备代理。 所有的设备管理功能进行远程访问使用设备孪生或模块孪生属性和命令，从而使所有 Windows IoT 设备的单玻璃管理方法。 有关设备管理的完整列表提供的功能指[这](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/reference.md)

除此之外，Azure 设备代理还会创建并管理其他设备上运行的 UWP 应用程序的 SAS 令牌。 Azure 设备代理可预配其他 UWP 应用与设备孪生或作为模块孪生，并将其连接字符串添加到各自的 TPM 插槽。 UWP 应用利用[UWP 桥](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/uwp-bridge.md)读取其连接字符串从 TPM 槽，并可以使用该连接到 IoT 中心。 

## <a name="how-to-get-started"></a>如何开始？

Azure IoT 设备代理是 GitHub 上提供。 该项目还包括示例来快速入门。 有关详细信息，请查看我们的 GitHub[存储库](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md)

## <a name="migrating-from-azure-device-agent-v1-to-v2"></a>从 Azure 设备代理 V1 迁移到 V2
如果你当前使用设备代理的 v1 版本，V1 与 V2 之间的一个显著的更改是，在 V2 版本中，Azure 设备代理不再与共享连接与 UWP 应用。 使用 IoT 中心的增强功能您可以拥有 UWP 应用和 Azure 设备代理有独立的连接字符串，仍可以与同一设备在 IoT 中心关联。 请参阅[此处](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/migration-from-old-client.md)的更多详细信息。

Azure 设备代理 V1 的详细信息，请参阅[此处](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/azureiotdm)。

## <a name="other-useful-tools"></a>其他有用工具 
### <a name="dm-mock-portal"></a>DM 模拟门户
[DM 模拟门户](https://github.com/ms-iot/azure-client-tools/blob/master/docs/dm-mock-portal/dm-mock-portal.md)是可用于设置设备孪生或模块孪生的属性，单个设备上或跨多个设备，使用 IoT 中心自动设备管理功能的应用程序。 

### <a name="tpm-tool---limpetexe"></a>TPM 工具-Limpet.exe
Azure 设备预配服务使客户能够自动将关联和配置设备与 IoT 中心后期制作。 对于此过程中，设备预配服务将需要一个唯一且 challengeable 设备 ID 以帮助安全地配置设备，设备放入操作时。 设备预配服务使用 TPM 的公共认可密钥 (EKeyPub) 实现此目的。 若要使用 DPS 注册设备，需要从设备中捕获 EKeyPub。 此步骤的最佳的时间是设备的在生产环境 （在行结束测试）。 但是，该过程也可以后期制作必要。  

Microsoft 提供了 Limpet 工具来简化设备预配服务注册过程。 具体取决于您制造的设置，如果没有可用的在线连接，则可以直接与设备预配服务，使用 Limpet 注册该设备或 Limpet 可以获取更高版本的脱机注册的设备与设备 EKeyPub预配服务。

有关使用 Limpet 设备预配服务注册过程的更多详细信息，请参阅此[存储库](https://github.com/ms-iot/azure-client-tools/blob/master/docs/limpet/limpet.md)。

许可证Limpet 是麻省理工学院的开放源代码许可的许可。 
