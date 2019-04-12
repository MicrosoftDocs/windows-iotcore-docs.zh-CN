---
title: Azure IoT 设备管理
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解有关如何使用 Azure IoT 设备管理和 Windows IoT 管理设备。
keywords: windows iot，Azure IoT 设备管理，设备管理
ms.openlocfilehash: eb8f99c91ec5d4b6bdb27d7aa0b1cd7e7f20cc2b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510855"
---
# <a name="azure-iot-device-management"></a>Azure IoT 设备管理

当涉及到连接的设备时，远程设备管理是由系统操作员的主要功能之一。 它使操作员能够重新配置和更新软件和远程而无需具有本地的物理访问设备的设备的参数。 使用 Windows 10 IoT Core，Oem 可以构建提供这些功能扩展的框中的设备。 Windows 10 IoT 核心版，以及其他 Windows 10 版本，已提供移动设备管理 (MDM) 根据[OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)。 这主要是在使用 SCCM 或 Intune 等管理工具的企业解决方案中利用的。 虽然这些解决方案非常适合放置在企业设置的设备，它更多样化我们看到 IoT 解决方案中的设置中具有挑战。 这些挑战也中需要轻量设备管理的 IoT 设备看到。 对于这些设备，Microsoft 提供了[通过 Azure IoT 中心设备管理](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)。

## <a name="scalable-device-management-with-windows-iot"></a>使用 Windows IoT 的可缩放的设备管理

使用在如家用电器、 HVAC 系统以及其他设备中运行 Windows IoT Core，是可自定义、 浅权重设备管理解决方案的需求。 在 Windows 创建者 Edition 中，Microsoft 使[Azure IoT 中心设备管理](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)。 Oem 可以使用[Windows IoT Azure DM 客户端库](https://aka.ms/iot-core-azure-dm-client)将设备管理功能添加到其 Azure IoT 中心连接的设备。 此库可以访问的标准的 Windows 设备管理组件 ([配置服务提供商](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)，CSP)。  Oem 现在可以生成支持 SCCM、 Intune 和 Azure IoT 中心设备管理并将其保留到其客户能够选择类型符合它们的数据挖掘解决方案最佳设备。 

![Azure IoT 中心设备管理](../media/AzureIoTDM/azureDM.png)

## <a name="how-does-it-work"></a>如何运作？

[Windows IoT Azure DM 客户端库](https://aka.ms/iot-core-azure-dm-client)主机应用程序中的链接关系。 它与主机应用程序共享的 Azure IoT 中心连接。 从而使其他注册以启用不必要的设备管理。 下图显示了使用 Windows IoT Azure DM 客户端库的 Azure IoT 中心 DM 解决方案的体系结构。 

![Azure DM 流程图](../media/AzureIoTDM/AzureDM-Architecture.png)

Microsoft 提供了两个系统组件，CommProxy.exe 和 SystemConfigurator.exe，需要在设备图像中包含 OEM。 这些组件授予访问权限的 Csp。 IoTDMClientLib 将 CSP 接口映射到可供 Azure IoT 中心设备管理的函数。 它还提供了不使用 CSP，例如设置时区的数据挖掘函数。 IoTDMClientLib 作为一个开放源代码组件提供。 Oem 可以将其添加特定于其设备配置等的传感器或传动装置的 DM 功能进行扩展。 

## <a name="device-health-attestation"></a>设备运行状况证明
IoT 设备安全地操作至关重要，评估如果设备已引导至受信任且符合的状态。 与[Windows IoT 设备运行状况证明 (DHA)](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)运算符可以验证设备的安全状态并采取相应的更正操作，如有必要通过[Azure IoT 中心设备管理](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md)。 DHA 是 Windows IoT Core Azure 设备管理客户端的一部分。 若要在解决方案中使用 DHA 功能，它需要 Microsoft DHA 服务的访问权限。 订阅服务是可通过[Windows 10 IoT 核心服务](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)。

### <a name="reference"></a>参考
[Azure iot DM 设备运行状况证明](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)

[部署 Azure 资源为设备运行状况证明](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)


## <a name="how-to-get-started"></a>如何开始？

Windows IoT Azure DM 客户端库是 GitHub 上提供。 旁边 IoTDMClientLib 项目还包括示例来快速入门。 有关详细信息，请参阅下面的链接。

### <a name="project-github-page"></a>项目的 GitHub 页面

[Windows IoT Azure DM 客户端库](https://aka.ms/iot-core-azure-dm-client)是 GitHub 上提供。

### <a name="dm-dashboard"></a>DM 仪表板

[DM 仪表板](https://aka.ms/iot-core-azure-dm-client-dashboard)是应用程序以测试在设备上的数据挖掘函数。 应用程序连接到通过 Azure IoT 中心设备。 应用程序可以用于验证设备的数据挖掘功能。 它可以扩展以测试已添加到 IoTDMClientLib 任何第三方数据挖掘函数。

### <a name="dm-background-application"></a>DM 后台应用程序

[DM 后台应用程序](https://aka.ms/iot-core-azure-dm-client-backgroundapp)演示 IoTDMClientLib 如何可以在连接到 Azure IoT 中心并需要作为后台应用程序在 Windows IoT Core 上运行的应用程序中使用。 

### <a name="toaster-application"></a>Toaster 应用程序

[Toaster application](https://aka.ms/iot-core-azure-dm-client-toasterapp)，如设备管理后台应用更高版本，将启用设备的 Azure 数据挖掘功能。 此应用将在前台中运行，并允许访问数据挖掘参数和通过设备用户界面的函数。 

### <a name="registering-your-device-with-the-azure-device-provision-service-dps"></a>注册你的设备与 Azure 设备预配服务 (DPS) 

Azure 设备预配服务使客户能够自动将关联和配置设备与 IoT 中心后期制作。 该进程的设备预配服务将需要一个唯一且 challengeable 设备 ID 以帮助安全地配置设备，设备放入操作时。 设备预配服务使用 TPM 的公共认可密钥 (EKeyPub) 实现此目的。 若要使用 DPS 注册设备，需要从设备中捕获 EKeyPub。 此步骤的最佳的时间是设备的在生产环境 （在行结束测试）。 但是，该过程也可以后期制作必要。  

Microsoft 提供了 Limpet 工具来简化设备预配服务注册过程。 具体取决于您制造的设置，如果没有可用的在线连接，则可以直接与设备预配服务，使用 Limpet 注册该设备或 Limpet 可以获取更高版本的脱机注册的设备与设备 EKeyPub预配服务。

Limpet 与设备预配服务注册过程的更多详细信息，请参阅[注册设备预配服务中的设备](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources)主题中[Limpet 文档](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md)。 

项目存储库：[Limpet 项目存储库](https://github.com/ms-iot/azure-dm-client/) 


许可证Limpet 是麻省理工学院的开放源代码许可的许可 

  
  

