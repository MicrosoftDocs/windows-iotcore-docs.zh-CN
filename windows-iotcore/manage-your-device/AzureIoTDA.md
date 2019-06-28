---
title: Azure IoT 设备代理
author: rcheeran
ms.author: rcheeran
ms.date: 06/25/2019
ms.topic: article
description: 了解有关如何在 Windows IoT 上使用 Azure IoT 设备代理管理设备。
keywords: windows iot，Azure IoT，设备管理、 远程管理的 Azure 设备代理
ms.openlocfilehash: 63c51d6281651e8f80fb3a0bdb350f919301fa69
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412301"
---
# <a name="azure-iot-device-agent"></a>Azure IoT 设备代理

当涉及到连接的设备时，远程设备管理是由系统操作员的主要功能之一。 它使操作员能够重新配置和更新软件和远程而无需具有本地的物理访问设备的设备的参数。 使用 Windows 10 IoT Core，Oem 可以构建提供这些功能扩展的框中的设备。 Windows 10 IoT 核心版，以及其他 Windows 10 版本，已提供移动设备管理 (MDM) 根据[OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)。 这主要是在使用 SCCM 或 Intune 等管理工具的企业解决方案中利用的。 虽然这些解决方案非常适合放置在企业设置的设备，它更多样化我们看到 IoT 解决方案中的设置中具有挑战。 这些挑战也中需要轻量设备管理的 IoT 设备看到。 对于这些设备，Microsoft 提供了[通过 Azure IoT 中心设备管理](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)。

## <a name="scalable-device-management-with-windows-iot"></a>使用 Windows IoT 的可缩放的设备管理

使用在如家用电器、 HVAC 系统以及其他设备中运行 Windows IoT Core，是可自定义、 浅权重设备管理解决方案的需求。 Oem 可以使用[Azure IoT 设备代理](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md)将设备管理功能添加到其 Azure IoT 中心连接的设备。 启用远程设备管理功能通过标准的 Windows 设备管理组件访问此就绪生成开放源代码包 ([配置服务提供商](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)，CSP)。  Oem 现在可以生成支持 SCCM、 Intune 和 Azure IoT 中心设备管理并将其保留到其客户能够选择适合它们的设备管理解决方案最佳设备。 

![Azure IoT 中心设备管理](../media/AzureIoTDM/azureDM.png)


## <a name="how-does-it-work"></a>如何运作？

![Azure IoT 设备代理](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/high-level-e2e.png) [Azure IoT 设备代理](https://aka.ms/iot-core-azure-dm-client)包含 2 个核心组件。 设备预配 Client(DPS) 会自动将设备预配。 使用设备的注册密钥和 DPS ScopeID 连接到 Azure 设备预配服务。 Azure DPS 服务将设备标识和设置中配置 IoT 中心并连接字符串返回到设备。 然后，分发点客户端使用此连接字符串以将设备连接到合适的 IoT 中心。  

设备管理客户端启用远程管理功能，通过利用可通过功能 ([配置服务提供商](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)，CSP) 的 Azure 设备代理的远程管理功能基于插件体系结构让你可以有选择地选择你想要在你的设备中包含的功能。 除此之外，插件体系结构是可扩展的。 您可以编写您自己的插件的设备管理功能，您需要并将其添加到 Azure 设备代理。 所有的设备管理功能进行远程访问使用设备孪生或模块孪生属性和命令，从而支持部署的所有 Windows IoT 设备的单玻璃管理方法。 有关设备管理的完整列表提供的功能指[这](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/reference.md)

除此之外，Azure 设备代理还会创建并管理其他设备上运行的 UWP 应用程序的 SAS 令牌。 Azure 设备代理可预配其他 UWP 应用与设备孪生或作为模块孪生，并将其连接字符串添加到各自的 TPM 插槽。 UWP 应用程序会利用 [UWP 桥] (https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/uwp-bridge.md) 读取其连接字符串从 TPM 槽，并可以使用该连接到 IoT 中心。 

## <a name="how-to-get-started"></a>如何开始？

Azure IoT 设备代理是 GitHub 上提供。 它还包括示例快速入门项目。 有关详细信息，请参阅下面的链接。

### <a name="project-github-page"></a>项目的 GitHub 页面

[Azure IoT 设备代理](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md)是 GitHub 上提供。

## <a name="migrating-from-azure-device-agent-v1-to-v2"></a>从 Azure 设备代理 V1 迁移到 V2
如果你当前使用设备代理的 v1 版本，V1 与 V2 之间的一个显著的更改是，在 V2 版本中，Azure 设备代理不再与共享连接与 UWP 应用。 使用 IoT 中心的增强功能您可以拥有 UWP 应用和 Azure 设备代理有独立的连接字符串，仍可以与同一设备在 IoT 中心关联。 请参阅[此处](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/migration-from-old-client.md)的更多详细信息。
Azure 设备代理 V1 的详细信息，请参阅[此处](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/azureiotdm)

## <a name="other-useful-tools"></a>其他有用工具 
### <a name="dm-dashboard"></a>DM 仪表板
[DM 仪表板](https://aka.ms/iot-core-azure-dm-client-dashboard)是应用程序以测试在设备上的数据挖掘函数。 应用程序连接到通过 Azure IoT 中心设备。 应用程序可以用于验证设备的数据挖掘功能。 它可以扩展以测试已添加到 Azure 设备代理的任何第三方数据挖掘函数。

### <a name="tpm-tool---limpetexe"></a>TPM 工具-Limpet.exe
Azure 设备预配服务使客户能够自动将关联和配置设备与 IoT 中心后期制作。 该进程的设备预配服务将需要一个唯一且 challengeable 设备 ID 以帮助安全地配置设备，设备放入操作时。 设备预配服务使用 TPM 的公共认可密钥 (EKeyPub) 实现此目的。 若要使用 DPS 注册设备，需要从设备中捕获 EKeyPub。 此步骤的最佳的时间是设备的在生产环境 （在行结束测试）。 但是，该过程也可以后期制作必要。  

Microsoft 提供了 Limpet 工具来简化设备预配服务注册过程。 具体取决于您制造的设置，如果没有可用的在线连接，则可以直接与设备预配服务，使用 Limpet 注册该设备或 Limpet 可以获取更高版本的脱机注册的设备与设备 EKeyPub预配服务。

Limpet 与设备预配服务注册过程的更多详细信息，请参阅[注册设备预配服务中的设备](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources)主题中[Limpet 文档](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md)。 

项目存储库: [Limpet 项目存储库] (https://github.com/ms-iot/azure-dm-client/) 

许可证Limpet 是麻省理工学院的开放源代码许可的许可 

## <a name="device-health-attestation"></a>设备运行状况证明
IoT 设备安全地操作至关重要，评估如果设备已引导至受信任且符合的状态。 与[Windows IoT 设备运行状况证明 (DHA)](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)运算符可以验证设备的安全状态并采取相应的更正操作，如有必要通过[Azure IoT 中心设备管理](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md)。 DHA 是 Windows IoT Core Azure 设备管理客户端的一部分。 若要在解决方案中使用 DHA 功能，它需要 Microsoft DHA 服务的访问权限。 订阅服务是可通过[Windows 10 IoT 核心服务](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)。

### <a name="reference"></a>参考
[Azure iot DM 设备运行状况证明](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)

[部署 Azure 资源为设备运行状况证明](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)








### <a name="more-about-the-azure-device-provision-service-dps"></a>有关 Azure 设备预配服务 (DPS) 的详细信息 


  
  

