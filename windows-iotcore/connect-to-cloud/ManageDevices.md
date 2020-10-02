---
title: 通过 Azure IoT 中心管理 Windows 设备
ms.date: 01/08/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 通过 Azure IoT 中心管理 Windows 设备。 通过设备管理，操作员可以同时远程配置和监视高 IoT 设备卷。
keywords: windows iot，Azure，DM，设备管理，Azure IoT 中心，IoT 中心，设备运行状况
ms.openlocfilehash: 8fdec35f8328668de9ffd3623795243a052351e3
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656833"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a><span data-ttu-id="3180b-105">通过 Azure IoT 中心管理 Windows 设备</span><span class="sxs-lookup"><span data-stu-id="3180b-105">Manage your Windows devices with the Azure IoT Hub</span></span>

## <a name="overview"></a><span data-ttu-id="3180b-106">概述</span><span class="sxs-lookup"><span data-stu-id="3180b-106">Overview</span></span>
<span data-ttu-id="3180b-107">设备管理 (DM) 允许操作员同时远程配置和监视非常大的 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="3180b-107">Device Management (DM) allows operators to remotely configure and monitor very high volumes of IoT devices simultaneously.</span></span>

<span data-ttu-id="3180b-108">设备的配置可以推送到设备，无论目标设备是联机还是脱机。</span><span class="sxs-lookup"><span data-stu-id="3180b-108">Configuration for the devices can be pushed to devices, whether the target devices are online or offline.</span></span> <span data-ttu-id="3180b-109">如果设备处于脱机状态，它将在重新连接时选取新的配置。</span><span class="sxs-lookup"><span data-stu-id="3180b-109">If the device is offline it will pick up the new configuration when it reconnects.</span></span> <span data-ttu-id="3180b-110">设备操作员还可以检索每个设备的状态，包括是否已成功应用设备配置更新。</span><span class="sxs-lookup"><span data-stu-id="3180b-110">Device operators can also retrieve the status of each device, including whether device configuration updates have been successfully applied or not.</span></span>

<span data-ttu-id="3180b-111">如果为 IoT 设备启用这些功能，则需要一种中心、强健且可靠的机制来存储和部署配置数据并将其部署到目标设备，并按比例监视设备状态。</span><span class="sxs-lookup"><span data-stu-id="3180b-111">Enabling these features for IoT devices requires a central, robust, and reliable mechanism to store and to deploy the configuration data to the target devices, and monitor device status - at scale.</span></span>

<span data-ttu-id="3180b-112">完整的解决方案需要以下各项：</span><span class="sxs-lookup"><span data-stu-id="3180b-112">A complete solution requires the following:</span></span>

* <span data-ttu-id="3180b-113">一种可靠/可伸缩的云服务，用于存储各种设备的所需状态和报告状态。</span><span class="sxs-lookup"><span data-stu-id="3180b-113">A Robust/Scalable Cloud Service to store the desired and reported states of the various devices.</span></span>
  * <span data-ttu-id="3180b-114">Azure IoT 中心和 Azure 设备管理提供高度可缩放且高效的云服务，可用于管理数百万台设备。</span><span class="sxs-lookup"><span data-stu-id="3180b-114">Azure IoT Hub and Azure Device Management offer a highly scalable and efficient cloud service for managing millions of devices.</span></span>

* <span data-ttu-id="3180b-115">在设备上运行并可以应用所需配置和报告设备状态的客户端。</span><span class="sxs-lookup"><span data-stu-id="3180b-115">A Client that runs on the device and can apply the desired configuration and report the state of the device.</span></span>
  * <span data-ttu-id="3180b-116">Windows IoT Azure DM 客户端 (开源 SDK + 运行时) ，与 Azure IoT 中心一起使用，可以应用和报告大量常见的（有时是关键的） Windows 配置。</span><span class="sxs-lookup"><span data-stu-id="3180b-116">The Windows IoT Azure DM Client (an open source SDK + runtime), in conjunction with Azure IoT Hub, can apply and report on a large set of common, sometimes critical, Windows configurations.</span></span>

* <span data-ttu-id="3180b-117">操作员用于远程配置和查询设备的门户或应用程序。</span><span class="sxs-lookup"><span data-stu-id="3180b-117">A Portal or an Application that will be used by the operator to configure and query the devices remotely.</span></span>
  * <span data-ttu-id="3180b-118">必须通过设备 OEM 或操作员对设备进行自定义。</span><span class="sxs-lookup"><span data-stu-id="3180b-118">This must be customized for devices by the device OEM or operator.</span></span> <span data-ttu-id="3180b-119">作为此解决方案的一部分，我们还提供开源数据模型和示例实现，以便更轻松地与 IoT 中心存储和 Windows IoT 客户端交互。</span><span class="sxs-lookup"><span data-stu-id="3180b-119">As part of this solution, we also provide an open source data model and sample implementation for easier interaction with the IoT Hub storage and the Windows IoT client.</span></span>

<span data-ttu-id="3180b-120">若要了解有关 Windows 设备的设备管理的详细信息，请访问主要 [设备管理客户端](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master)存储库。</span><span class="sxs-lookup"><span data-stu-id="3180b-120">To learn more about device management for Windows devices, visit the main [Device Management Client repo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span></span>
