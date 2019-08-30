---
title: Azure IoT 设备管理
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Azure IoT 设备管理和 Windows IoT 来管理设备。
keywords: windows iot, Azure IoT, Azure 设备管理, 设备管理
ms.openlocfilehash: 51580c2ca4c5bf653428ed83e0d6d53310ae89a3
ms.sourcegitcommit: b00cd20ca22e63b3d0795a1b8fe248963b3c74ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67467120"
---
# <a name="azure-iot-device-management"></a>Azure IoT 设备管理   

当涉及到连接的设备时, 远程设备管理是系统操作员使用的主要功能之一。 它使操作员能够远程重新配置和更新设备的软件和参数, 而无需对设备进行本地物理访问。 通过 Windows 10 IoT Core, Oem 可以构建提供这些功能的设备。 Windows 10 IoT Core 以及其他 Windows 10 版本已经基于[OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)提供了移动设备管理 (MDM)。 这主要用于使用 SCCM 或 Intune 等管理工具的企业解决方案。 尽管这些解决方案非常适合于处于企业设置中的设备, 但在 IoT 解决方案中看到的更多样化的设置中会出现问题。 还会在需要轻型设备管理的 IoT 设备中了解这些挑战。 对于这些设备, Microsoft[通过 Azure IoT 中心提供设备管理](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)。    

## <a name="scalable-device-management-with-windows-iot"></a>Windows IoT 的可伸缩设备管理  

使用在家庭设备、HVAC 系统等设备中运行的 Windows IoT Core, 需要可自定义的轻型设备管理解决方案。 在 Windows Creator 版本中, Microsoft 启用了[Azure IoT 中心设备管理](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)。 Oem 可以使用[Windows IoT AZURE DM 客户端库](https://aka.ms/iot-core-azure-dm-client)将设备管理功能添加到其 Azure IoT 中心连接的设备上。 此库将访问标准 Windows 设备管理组件 ([配置服务提供程序](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)、CSP)。  现在, Oem 可以构建支持 SCCM、Intune 和 Azure IoT 中心进行设备管理的设备, 并使其客户能够选择最适合的类型 DM 解决方案。   

![Azure IoT 中心设备管理](../media/AzureIoTDM/azureDM.png) 

## <a name="how-does-it-work"></a>如何运作？    

[Windows IoT AZURE DM 客户端库](https://aka.ms/iot-core-azure-dm-client)链接在主机应用程序中。 它与主机应用程序共享 Azure IoT 中心连接。 这样就可以进行额外的注册, 以实现不必要的设备管理。 下图显示了使用 Windows IoT Azure DM 客户端库的 Azure IoT 中心 DM 解决方案的体系结构。     

![Azure DM 流程图](../media/AzureIoTDM/AzureDM-Architecture.png)    

Microsoft 提供了两个系统组件: CommProxy 和 SystemConfigurator, OEM 需要在设备映像中包含这些组件。 这些组件允许访问 Csp。 IoTDMClientLib 将 CSP 接口映射到可由 Azure IoT 中心设备管理使用的函数。 它还提供了不使用 CSP 的 DM 函数, 例如设置时区。 IoTDMClientLib 作为开源组件提供。 Oem 可以对其进行扩展, 以添加特定于其设备的 DM 功能, 如传感器或传动装置的配置。  

## <a name="device-health-attestation"></a>设备运行状况证明    
对于 IoT 设备的安全操作, 评估设备是否启动到受信任且合规的状态至关重要。 使用[Windows IoT 设备运行状况证明 (DHA)](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)操作员可以验证设备的安全状态, 并根据需要通过[Azure IoT 中心设备管理](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md)采取适当的补救措施。 DHA 是 Windows IoT 核心 Azure 设备管理客户端的一部分。 若要在解决方案中使用 DHA 功能, 需要访问 Microsoft DHA 服务。 可以通过[Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)获取对服务的订阅。 

### <a name="reference"></a>参考   
[Azure IoT DM 的设备运行状况证明](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)  

[部署设备运行状况证明的 Azure 资源](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)  


## <a name="how-to-get-started"></a>如何开始？  

GitHub 上提供了 Windows IoT Azure DM 客户端库。 它还包含 IoTDMClientLib 项目旁边的示例来快速入门。 有关详细信息, 请参阅下面的链接。    

### <a name="project-github-page"></a>项目 GitHub 页 

GitHub 上提供了[Windows IoT AZURE DM 客户端库](https://aka.ms/iot-core-azure-dm-client)。  

### <a name="dm-dashboard"></a>DM 仪表板    

[Dm 仪表板](https://aka.ms/iot-core-azure-dm-client-dashboard)是用于测试设备上的 DM 函数的应用程序。 应用通过 Azure IoT 中心连接到设备。 应用可用于验证设备的 DM 功能。 可对其进行扩展, 以测试已添加到 IoTDMClientLib 的任何第三方 DM 函数。    

### <a name="dm-background-application"></a>DM 后台应用程序   

[DM 后台应用程序](https://aka.ms/iot-core-azure-dm-client-backgroundapp)演示如何在连接到 Azure iot 中心的应用程序中使用 IoTDMClientLib, 并需要在 Windows IoT Core 上以后台应用的形式运行。    

### <a name="toaster-application"></a>Toaster 应用程序 

作为上述设备管理后台应用的[Toaster 应用程序](https://aka.ms/iot-core-azure-dm-client-toasterapp)将为设备启用 Azure DM 功能。 此应用将在前台运行, 并允许通过设备 UI 访问 DM 参数和功能。   

### <a name="registering-your-device-with-the-azure-device-provision-service-dps"></a>将设备注册到 Azure 设备预配服务 (DPS)   

使用 Azure 设备预配服务, 客户可以自动将设备与 IoT 中心后期生产进行关联和配置。 对于此过程, 设备预配服务将需要一个唯一的 challengeable 设备 ID, 以帮助在设备进入操作时安全地配置设备。 设备预配服务使用 TPM 的公共认可密钥 (EKeyPub) 来实现此目的。 若要向 DPS 注册设备, 需要从设备搜集 EKeyPub。 此步骤的首选时间是在生产期间 (在设备的行尾测试过程中)。 不过, 如果需要, 也可以在生产后执行此过程。   

Microsoft 提供了 Limpet 工具来简化设备预配服务注册过程。 根据制造设置, 如果有可用的联机连接, 则可以使用 Limpet 直接注册设备, 也可以使用设备预配服务直接注册设备, Limpet 可以获取 EKeyPub, 以便以后脱机注册设备正在预配服务。  

有关 Limpet 的设备预配服务注册过程的更多详细信息, 请参阅[Limpet 文档](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md)中的在[设备预配服务中注册设备](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources)部分。    

项目存储库:[Limpet 项目存储库](https://github.com/ms-iot/azure-dm-client/)     


许可证Limpet 在 MIT 开源许可证下许可   

