---
title: 适用于 IoT 核心Windows的 Arduino 布线
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在受支持的 IoT 核心设备上创建、部署和调试 Arduino Windows草图。
keywords: windows iot， Arduino， Arduino 连接， 模板， IoT 核心版， UWP
ms.openlocfilehash: 72ea96e58667b67e9b697e2c25d99067b9ac2c39
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228813"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a>适用于 IoT 核心Windows的 Arduino 布线

> [!IMPORTANT]
> Windows 10 IoT 团队不再主动维护 Arduino。

若要在 IoT Core 设备上开发和重复使用熟悉的[Arduino](https://www.arduino.cc/en/Reference/HomePage)布线草图，在[Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472)Project 模板扩展中提供了用于 Arduino 布线的 Visual Studio 项目模板。

通过 Arduino 布线项目模板，开发人员和制造商可以使用 Arduino 平台上提供的相同 Arduino 布线语言语义和构造，在支持的 IoT 核心设备上创建、部署和调试 Arduino 布线草图。 这不仅有助于以很少的成本将现有 Arduino 草图移植到 IoT 核心，而且 IoT 核心上运行的 Arduino 线路草图是完整的 Windows 10 应用，可以使用 Univeral Windows Platform (UWP) API。 因此，Arduino 线路草图可以完全访问通信、数据访问、网络、图形等 API，这些 API 可用于创建在 Windows 10 IoT 核心版 设备上运行的端到端方案。 若要详细了解如何开发通用 Windows 平台 (UWP) 应用，请参阅生成适用于 Windows 10 IoT 核心版[的应用程序](../develop-your-app/BuildingAppsForIoTCore.md)。

此外，Arduino 布线草图使用直接内存映射驱动程序，该驱动程序在受支持的设备上提供高性能。 有关性能详细信息的详细信息，请参阅 Windows [IoT 闪电性能测试](../develop-your-app/LightningPerformance.md)报表。

若要开始为 Raspberry Pi2、Pi3 或 Minnowboard Max 生成 Arduino 布线项目，请参阅 [Arduino 布线项目指南](ArduinoWiringProjectGuide.md)。

> [!NOTE]
> DragonBoard 410c 当前不支持 Arduino 布线。 
