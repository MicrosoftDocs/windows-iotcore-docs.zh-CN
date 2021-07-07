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
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a>使用 Windows 中心管理Azure IoT设备

## <a name="overview"></a>概述
设备管理 (DM) 允许操作员同时远程配置和监视极大量的 IoT 设备。

无论目标设备是联机还是脱机，都可以将设备的配置推送到设备。 如果设备处于脱机状态，它将在重新连接时选取新配置。 设备操作员还可以检索每个设备的状态，包括是否已成功应用设备配置更新。

为 IoT 设备启用这些功能需要一个集中、可靠且可靠的机制来存储和部署配置数据到目标设备，并大规模监视设备状态。

完整的解决方案需要以下各项：

* 可靠/可缩放的云服务，用于存储各种设备的所需状态和已报告状态。
  * Azure IoT中心和 Azure 设备管理提供高度可缩放且高效的云服务，用于管理数百万台设备。

* 在设备上运行的客户端，可以应用所需的配置并报告设备的状态。
  * Windows IoT Azure DM 客户端 (开放源代码 SDK + 运行时) 与 Azure IoT 中心一起，可以应用并报告大量常见的（有时Windows配置）。

* 操作员将用于远程配置和查询设备的门户或应用程序。
  * 这必须由设备 OEM 或操作员为设备自定义。 作为此解决方案的一部分，我们还提供开源数据模型和示例实现，以便更轻松地与 IoT 中心存储和 ioT Windows交互。

若要了解有关设备设备管理Windows，请访问客户端设备管理[存储库](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master)。
