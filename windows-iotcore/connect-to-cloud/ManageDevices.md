---
title: 通过 Azure IoT 中心管理 Windows 设备
ms.date: 01/08/2018
ms.topic: article
description: 了解如何通过 Azure IoT 中心管理 Windows 设备。
keywords: windows iot，Azure，DM，设备管理，Azure IoT 中心，IoT 中心，设备运行状况
ms.openlocfilehash: 7eea1a8d3ccfd35bcdb7ebae44803135db05f824
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918391"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a><span data-ttu-id="4cb04-104">通过 Azure IoT 中心管理 Windows 设备</span><span class="sxs-lookup"><span data-stu-id="4cb04-104">Manage your Windows devices with the Azure IoT Hub</span></span>

## <a name="overview"></a><span data-ttu-id="4cb04-105">概述</span><span class="sxs-lookup"><span data-stu-id="4cb04-105">Overview</span></span>
<span data-ttu-id="4cb04-106">设备管理（DM）允许操作员同时远程配置和监视非常大的 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="4cb04-106">Device Management (DM) allows operators to remotely configure and monitor very high volumes of IoT devices simultaneously.</span></span>

<span data-ttu-id="4cb04-107">设备的配置可以推送到设备，无论目标设备是联机还是脱机。</span><span class="sxs-lookup"><span data-stu-id="4cb04-107">Configuration for the devices can be pushed to devices, whether the target devices are online or offline.</span></span> <span data-ttu-id="4cb04-108">如果设备处于脱机状态，它将在重新连接时选取新的配置。</span><span class="sxs-lookup"><span data-stu-id="4cb04-108">If the device is offline it will pick up the new configuration when it reconnects.</span></span> <span data-ttu-id="4cb04-109">设备操作员还可以检索每个设备的状态，包括是否已成功应用设备配置更新。</span><span class="sxs-lookup"><span data-stu-id="4cb04-109">Device operators can also retrieve the status of each device, including whether device configuration updates have been successfully applied or not.</span></span>

<span data-ttu-id="4cb04-110">如果为 IoT 设备启用这些功能，则需要一种中心、强健且可靠的机制来存储和部署配置数据并将其部署到目标设备，并按比例监视设备状态。</span><span class="sxs-lookup"><span data-stu-id="4cb04-110">Enabling these features for IoT devices requires a central, robust, and reliable mechanism to store and to deploy the configuration data to the target devices, and monitor device status - at scale.</span></span>

<span data-ttu-id="4cb04-111">完整的解决方案需要以下各项：</span><span class="sxs-lookup"><span data-stu-id="4cb04-111">A complete solution requires the following:</span></span>

* <span data-ttu-id="4cb04-112">一种可靠/可伸缩的云服务，用于存储各种设备的所需状态和报告状态。</span><span class="sxs-lookup"><span data-stu-id="4cb04-112">A Robust/Scalable Cloud Service to store the desired and reported states of the various devices.</span></span>
  * <span data-ttu-id="4cb04-113">Azure IoT 中心和 Azure 设备管理提供高度可缩放且高效的云服务，可用于管理数百万台设备。</span><span class="sxs-lookup"><span data-stu-id="4cb04-113">Azure IoT Hub and Azure Device Management offer a highly scalable and efficient cloud service for managing millions of devices.</span></span>

* <span data-ttu-id="4cb04-114">在设备上运行并可以应用所需配置和报告设备状态的客户端。</span><span class="sxs-lookup"><span data-stu-id="4cb04-114">A Client that runs on the device and can apply the desired configuration and report the state of the device.</span></span>
  * <span data-ttu-id="4cb04-115">Windows IoT Azure DM 客户端（开源 SDK + 运行时）与 Azure IoT 中心配合使用，可以应用和报告大量常见的、有时关键的 Windows 配置。</span><span class="sxs-lookup"><span data-stu-id="4cb04-115">The Windows IoT Azure DM Client (an open source SDK + runtime), in conjunction with Azure IoT Hub, can apply and report on a large set of common, sometimes critical, Windows configurations.</span></span>

* <span data-ttu-id="4cb04-116">操作员用于远程配置和查询设备的门户或应用程序。</span><span class="sxs-lookup"><span data-stu-id="4cb04-116">A Portal or an Application that will be used by the operator to configure and query the devices remotely.</span></span>
  * <span data-ttu-id="4cb04-117">必须通过设备 OEM 或操作员对设备进行自定义。</span><span class="sxs-lookup"><span data-stu-id="4cb04-117">This must be customized for devices by the device OEM or operator.</span></span> <span data-ttu-id="4cb04-118">作为此解决方案的一部分，我们还提供开源数据模型和示例实现，以便更轻松地与 IoT 中心存储和 Windows IoT 客户端交互。</span><span class="sxs-lookup"><span data-stu-id="4cb04-118">As part of this solution, we also provide an open source data model and sample implementation for easier interaction with the IoT Hub storage and the Windows IoT client.</span></span>

<span data-ttu-id="4cb04-119">若要了解有关 Windows 设备的设备管理的详细信息，请访问主要[设备管理客户端](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master)存储库。</span><span class="sxs-lookup"><span data-stu-id="4cb04-119">To learn more about device management for Windows devices, visit the main [Device Management Client repo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span></span>
