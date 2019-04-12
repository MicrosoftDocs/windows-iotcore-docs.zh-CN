---
title: 管理 Windows 设备使用 Azure IoT 中心
author: saraclay
ms.author: saclayt
ms.date: 01/08/2018
ms.topic: article
description: 了解如何管理 Windows 设备使用 Azure IoT 中心。
keywords: windows iot、 Azure、 DM、 设备管理，Azure IoT 中心、 IoT 中心、 设备运行状况
ms.openlocfilehash: f3018007c262112374fd39439bf2306675fddafe
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510832"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a><span data-ttu-id="3aed7-104">管理 Windows 设备使用 Azure IoT 中心</span><span class="sxs-lookup"><span data-stu-id="3aed7-104">Manage your Windows devices with the Azure IoT Hub</span></span>

## <a name="overview"></a><span data-ttu-id="3aed7-105">概述</span><span class="sxs-lookup"><span data-stu-id="3aed7-105">Overview</span></span>
<span data-ttu-id="3aed7-106">设备管理 (DM) 使操作员可以远程配置和同时监视极大量的 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="3aed7-106">Device Management (DM) allows operators to remotely configure and monitor very high volumes of IoT devices simultaneously.</span></span>

<span data-ttu-id="3aed7-107">适用于设备的配置可以推送到设备，无论目标设备是联机或脱机。</span><span class="sxs-lookup"><span data-stu-id="3aed7-107">Configuration for the devices can be pushed to devices, whether the target devices are online or offline.</span></span> <span data-ttu-id="3aed7-108">如果设备处于脱机状态它会选取新的配置，当重新连接。</span><span class="sxs-lookup"><span data-stu-id="3aed7-108">If the device is offline it will pick up the new configuration when it reconnects.</span></span> <span data-ttu-id="3aed7-109">设备运算符还可以检索设备配置更新已成功应用或不包括每个设备的状态。</span><span class="sxs-lookup"><span data-stu-id="3aed7-109">Device operators can also retrieve the status of each device, including whether device configuration updates have been successfully applied or not.</span></span>

<span data-ttu-id="3aed7-110">启用这些功能为 IoT 设备需要中部、 更稳定和可靠的机制来存储和到目标设备和监视设备状态-大规模部署的配置数据。</span><span class="sxs-lookup"><span data-stu-id="3aed7-110">Enabling these features for IoT devices requires a central, robust, and reliable mechanism to store and to deploy the configuration data to the target devices, and monitor device status - at scale.</span></span>

<span data-ttu-id="3aed7-111">完整的解决方案需要以下项：</span><span class="sxs-lookup"><span data-stu-id="3aed7-111">A complete solution requires the following:</span></span>

* <span data-ttu-id="3aed7-112">强健的/可缩放云服务来存储各种设备的所需和报告状态。</span><span class="sxs-lookup"><span data-stu-id="3aed7-112">A Robust/Scalable Cloud Service to store the desired and reported states of the various devices.</span></span>
  * <span data-ttu-id="3aed7-113">Azure IoT 中心和 Azure 设备管理提供高度可缩放且高效的云服务，用于管理数百万台设备。</span><span class="sxs-lookup"><span data-stu-id="3aed7-113">Azure IoT Hub and Azure Device Management offer a highly scalable and efficient cloud service for managing millions of devices.</span></span>

* <span data-ttu-id="3aed7-114">客户端在设备上运行，并可应用所需的配置和报告设备的状态。</span><span class="sxs-lookup"><span data-stu-id="3aed7-114">A Client that runs on the device and can apply the desired configuration and report the state of the device.</span></span>
  * <span data-ttu-id="3aed7-115">Windows IoT Azure DM 客户端 （一种开放源 SDK + 运行时），结合使用 Azure IoT 中心，程序可以将应用和报告大量常见，有时关键的 Windows 配置。</span><span class="sxs-lookup"><span data-stu-id="3aed7-115">The Windows IoT Azure DM Client (an open source SDK + runtime), in conjunction with Azure IoT Hub, can apply and report on a large set of common, sometimes critical, Windows configurations.</span></span>

* <span data-ttu-id="3aed7-116">门户网站或该运算符将用来配置和远程查询设备的应用程序。</span><span class="sxs-lookup"><span data-stu-id="3aed7-116">A Portal or an Application that will be used by the operator to configure and query the devices remotely.</span></span>
  * <span data-ttu-id="3aed7-117">这必须由 OEM 或运算符的设备的设备的自定义。</span><span class="sxs-lookup"><span data-stu-id="3aed7-117">This must be customized for devices by the device OEM or operator.</span></span> <span data-ttu-id="3aed7-118">作为此解决方案的一部分，我们还提供一个开放源代码数据模型并更容易使用 IoT 中心存储和 Windows IoT 客户端交互的实现示例。</span><span class="sxs-lookup"><span data-stu-id="3aed7-118">As part of this solution, we also provide an open source data model and sample implementation for easier interaction with the IoT Hub storage and the Windows IoT client.</span></span>

<span data-ttu-id="3aed7-119">若要了解有关 Windows 设备的设备管理的详细信息，请访问主[设备管理客户端存储库](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master)。</span><span class="sxs-lookup"><span data-stu-id="3aed7-119">To learn more about device management for Windows devices, visit the main [Device Management Client repo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span></span>
