---
title: 使用 Windows 中心管理Azure IoT设备
ms.date: 01/08/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 使用 Windows 中心管理Azure IoT设备。 借助设备管理，操作员可以同时远程配置和监视高 IoT 设备卷。
keywords: windows iot， Azure， DM， 设备管理， Azure IoT中心， IoT 中心， 设备运行状况
ms.openlocfilehash: b74b91d1a7e48de2724e4b81fe5c30cca020bb8f
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229214"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a><span data-ttu-id="bcfb8-105">使用 Windows 中心管理Azure IoT设备</span><span class="sxs-lookup"><span data-stu-id="bcfb8-105">Manage your Windows devices with the Azure IoT Hub</span></span>

## <a name="overview"></a><span data-ttu-id="bcfb8-106">概述</span><span class="sxs-lookup"><span data-stu-id="bcfb8-106">Overview</span></span>
<span data-ttu-id="bcfb8-107">设备管理 (DM) 允许操作员同时远程配置和监视极大量的 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-107">Device Management (DM) allows operators to remotely configure and monitor very high volumes of IoT devices simultaneously.</span></span>

<span data-ttu-id="bcfb8-108">无论目标设备是联机还是脱机，都可以将设备的配置推送到设备。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-108">Configuration for the devices can be pushed to devices, whether the target devices are online or offline.</span></span> <span data-ttu-id="bcfb8-109">如果设备处于脱机状态，它将在重新连接时选取新配置。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-109">If the device is offline it will pick up the new configuration when it reconnects.</span></span> <span data-ttu-id="bcfb8-110">设备操作员还可以检索每个设备的状态，包括是否已成功应用设备配置更新。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-110">Device operators can also retrieve the status of each device, including whether device configuration updates have been successfully applied or not.</span></span>

<span data-ttu-id="bcfb8-111">为 IoT 设备启用这些功能需要一个集中、可靠且可靠的机制来存储和部署配置数据到目标设备，并大规模监视设备状态。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-111">Enabling these features for IoT devices requires a central, robust, and reliable mechanism to store and to deploy the configuration data to the target devices, and monitor device status - at scale.</span></span>

<span data-ttu-id="bcfb8-112">完整的解决方案需要以下各项：</span><span class="sxs-lookup"><span data-stu-id="bcfb8-112">A complete solution requires the following:</span></span>

* <span data-ttu-id="bcfb8-113">可靠/可缩放的云服务，用于存储各种设备的所需状态和已报告状态。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-113">A Robust/Scalable Cloud Service to store the desired and reported states of the various devices.</span></span>
  * <span data-ttu-id="bcfb8-114">Azure IoT中心和 Azure 设备管理提供高度可缩放且高效的云服务，用于管理数百万台设备。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-114">Azure IoT Hub and Azure Device Management offer a highly scalable and efficient cloud service for managing millions of devices.</span></span>

* <span data-ttu-id="bcfb8-115">在设备上运行的客户端，可以应用所需的配置并报告设备的状态。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-115">A Client that runs on the device and can apply the desired configuration and report the state of the device.</span></span>
  * <span data-ttu-id="bcfb8-116">Windows IoT Azure DM 客户端 (开放源代码 SDK + 运行时) 与 Azure IoT 中心一起，可以应用并报告大量常见的（有时Windows配置）。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-116">The Windows IoT Azure DM Client (an open source SDK + runtime), in conjunction with Azure IoT Hub, can apply and report on a large set of common, sometimes critical, Windows configurations.</span></span>

* <span data-ttu-id="bcfb8-117">操作员将用于远程配置和查询设备的门户或应用程序。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-117">A Portal or an Application that will be used by the operator to configure and query the devices remotely.</span></span>
  * <span data-ttu-id="bcfb8-118">这必须由设备 OEM 或操作员为设备自定义。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-118">This must be customized for devices by the device OEM or operator.</span></span> <span data-ttu-id="bcfb8-119">作为此解决方案的一部分，我们还提供开源数据模型和示例实现，以便更轻松地与 IoT 中心存储和 ioT Windows交互。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-119">As part of this solution, we also provide an open source data model and sample implementation for easier interaction with the IoT Hub storage and the Windows IoT client.</span></span>

<span data-ttu-id="bcfb8-120">若要了解有关设备设备管理Windows，请访问客户端设备管理[存储库](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master)。</span><span class="sxs-lookup"><span data-stu-id="bcfb8-120">To learn more about device management for Windows devices, visit the main [Device Management Client repo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span></span>
