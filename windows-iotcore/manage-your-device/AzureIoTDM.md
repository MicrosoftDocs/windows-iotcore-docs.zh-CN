---
title: Azure IoT设备管理
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 IoT Azure IoT 设备管理 Windows设备。
keywords: windows iot、Azure IoT、Azure 设备管理、设备管理
ms.openlocfilehash: a04535fbe3e0de33b3ed0328df23462756813672
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228683"
---
# <a name="azure-iot-device-management"></a>Azure IoT设备管理   

对于连接的设备，远程设备管理是系统操作员使用的主要功能之一。 它使操作员能够远程重新配置和更新设备的软件和参数，而无需对设备进行本地物理访问。 借助Windows 10 IoT 核心版，OEM 可以构建可开箱即用地提供这些功能的设备。 Windows 10 IoT 核心版以及其他 Windows 10 版本，已基于[OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)设备管理 (MDM) 移动版。 这主要在具有管理工具（如 SCCM 或 Intune）的企业解决方案中利用。 虽然这些解决方案非常适合放置在企业设置中的设备，但它在 IoT 解决方案中看到的更不同的设置中也带来了挑战。 在需要轻型设备管理的 IoT 设备中也看到了这些难题。 对于这些设备，Microsoft 通过[中心 提供Azure IoT管理](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)。    

## <a name="scalable-device-management-with-windows-iot"></a>使用 IoT 进行可Windows设备管理  

由于Windows设备（如家庭设备、HVAC 系统等）中运行 IoT 核心，因此需要可自定义的轻型设备管理解决方案。 在 Windows Creator Edition 中，Microsoft Azure IoT[中心设备管理](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)。 OEM 可以使用[IoT azure DM Windows](https://aka.ms/iot-core-azure-dm-client)库将设备管理功能添加到其Azure IoT连接的设备。 此库将访问配置Windows提供程序、CSP [ (设备管理](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)组件) 。  OEM 现在可以构建支持 SCCM、Intune 和 Azure IoT 中心的设备进行设备管理，并让客户选择最适合它们的 DM 解决方案类型。   

![Azure IoT中心设备管理](../media/AzureIoTDM/azureDM.png) 

## <a name="how-does-it-work"></a>它是如何工作的？    

托管[Windows IoT Azure DM 客户端](https://aka.ms/iot-core-azure-dm-client)库链接在主机应用程序中。 它与Azure IoT应用共享中心连接。 因此，无需进行额外的注册来启用设备管理。 下图显示了使用 Azure IoT IoT Azure DM 客户端库Windows中心 DM 解决方案的体系结构。     

![Azure DM Flow图表](../media/AzureIoTDM/AzureDM-Architecture.png)    

Microsoft 提供了两个CommProxy.exe组件SystemConfigurator.exe，OEM 需要在设备映像中包括这两个组件。 这些组件提供对 CSP 的访问权限。 IoTDMClientLib 将 CSP 接口映射到中心设备管理Azure IoT的函数。 它还提供不使用 CSP 的 DM 函数，例如设置时区。 IoTDMClientLib 作为开源组件提供。 OEM 可以扩展它，以添加特定于其设备的 DM 功能，例如传感器或运动器的配置。  

## <a name="device-health-attestation"></a>设备运行状况证明    
若要安全操作 IoT 设备，必须评估设备是否启动到受信任且合规的状态。 使用[Windows IoT 设备运行状况证明 (DHA) ](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)操作员可以验证设备的安全状态，并在必要时通过 Azure IoT Hub[设备管理](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md)。 DHA 是 IoT 核心Windows Azure 设备管理客户端的一部分。 若要在解决方案中使用 DHA 功能，需要访问 Microsoft DHA 服务。 该服务的订阅可以通过 Windows 10 IoT 核心版 服务[。](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) 

### <a name="reference"></a>参考   
[设备运行状况证明 DM Azure IoT](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)  

[部署 Azure 资源设备运行状况证明](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)  


## <a name="how-to-get-started"></a>如何开始？  

WindowsIoT Azure DM 客户端库在 GitHub。 除了 IoTDMClientLib 项目外，它还包含快速入门的示例。 有关详细信息，请参阅以下链接。    

### <a name="project-github-page"></a>Project GitHub页 

[Windows上提供了 IoT Azure DM](https://aka.ms/iot-core-azure-dm-client)客户端GitHub。  

### <a name="dm-dashboard"></a>DM 仪表板    

[DM](https://aka.ms/iot-core-azure-dm-client-dashboard) 仪表板是一个应用程序，用于测试设备上 DM 函数。 应用通过中心连接到Azure IoT设备。 应用可用于验证设备的 DM 功能。 可以扩展它以测试已添加到 IoTDMClientLib 的任何第三方 DM 函数。    

### <a name="dm-background-application"></a>DM 后台应用程序   

[DM 后台应用程序](https://aka.ms/iot-core-azure-dm-client-backgroundapp)演示如何在连接到 Azure IoT Hub 且需要在 Windows IoT Core 上作为后台应用运行的应用程序中使用 IoTDMClientLib。    

### <a name="toaster-application"></a>Toaster 应用程序 

[Toaster 应用程序（](https://aka.ms/iot-core-azure-dm-client-toasterapp)如上面的设备管理后台应用）将为设备启用 Azure DM 功能。 此应用将在前台运行，并允许通过设备 UI 访问 DM 参数和函数。   

### <a name="registering-your-device-with-the-azure-device-provision-service-dps"></a>将设备注册到 AZURE 设备预配服务 (DPS)    

Azure 设备预配服务允许客户在生产后自动将设备与 IoT 中心关联和配置。 对于此过程，设备预配服务需要唯一且可质询的设备 ID，以帮助在设备投入运行时安全地配置设备。 设备预配服务使用 TPM 的公共认可密钥 (EKeyPub) 实现此目的。 若要将设备注册到 DPS，需要从设备获取 EKeyPub。 此步骤的首选时间是在生产期间 (在设备测试的行尾测试) 。 但是，如果需要，也可在生产后完成此过程。   

Microsoft 提供了 Limpet 工具，用于简化设备预配服务注册过程。 根据制造设置，如果有可用的联机连接，则可直接使用 Limpet 向设备预配服务注册设备，或者 Limpet 可以获取 EKeyPub，供以后使用设备预配服务脱机注册设备。  

有关 Limpet 的设备预配服务注册过程的更多详细信息，请参阅 Limpet[](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources)文档中的在设备预配服务中[注册设备部分](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md)。    

Project存储库[：Limpet 项目存储库](https://github.com/ms-iot/azure-dm-client/)     


许可证：Limpet 根据 MIT 开放源代码许可证获得许可   

