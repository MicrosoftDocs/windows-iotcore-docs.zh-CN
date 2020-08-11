---
title: 通过 Azure IoT 中心管理 Windows 设备
ms.date: 01/08/2018
ms.topic: article
description: 通过 Azure IoT 中心管理 Windows 设备。 通过设备管理，操作员可以同时远程配置和监视高 IoT 设备卷。
keywords: windows iot，Azure，DM，设备管理，Azure IoT 中心，IoT 中心，设备运行状况
ms.openlocfilehash: ff6171fd028d62c3f1b1d6c8bd04994e7c85399c
ms.sourcegitcommit: 05278f1a522ed498900ce15b98bdd4389b5dde55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88081562"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a>通过 Azure IoT 中心管理 Windows 设备

## <a name="overview"></a>概述
设备管理 (DM) 允许操作员同时远程配置和监视非常大的 IoT 设备。

设备的配置可以推送到设备，无论目标设备是联机还是脱机。 如果设备处于脱机状态，它将在重新连接时选取新的配置。 设备操作员还可以检索每个设备的状态，包括是否已成功应用设备配置更新。

如果为 IoT 设备启用这些功能，则需要一种中心、强健且可靠的机制来存储和部署配置数据并将其部署到目标设备，并按比例监视设备状态。

完整的解决方案需要以下各项：

* 一种可靠/可伸缩的云服务，用于存储各种设备的所需状态和报告状态。
  * Azure IoT 中心和 Azure 设备管理提供高度可缩放且高效的云服务，可用于管理数百万台设备。

* 在设备上运行并可以应用所需配置和报告设备状态的客户端。
  * Windows IoT Azure DM 客户端 (开源 SDK + 运行时) ，与 Azure IoT 中心一起使用，可以应用和报告大量常见的（有时是关键的） Windows 配置。

* 操作员用于远程配置和查询设备的门户或应用程序。
  * 必须通过设备 OEM 或操作员对设备进行自定义。 作为此解决方案的一部分，我们还提供开源数据模型和示例实现，以便更轻松地与 IoT 中心存储和 Windows IoT 客户端交互。

若要了解有关 Windows 设备的设备管理的详细信息，请访问主要[设备管理客户端](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master)存储库。
