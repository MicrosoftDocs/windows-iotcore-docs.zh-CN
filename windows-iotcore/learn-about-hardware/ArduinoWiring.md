---
title: Arduino 开发适用于 Windows IoT Core 设备布线
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/17
ms.topic: article
description: 了解如何创建、 部署和调试支持的 Windows IoT Core 设备上连接 Arduino 草图。
keywords: windows iot，Arduino，Arduino 绑定，模板中，IoT Core UWP
ms.openlocfilehash: ee6c64bdfd01e79d26bfa0a6c5f88f7735150393
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744789"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a>Arduino 开发适用于 Windows IoT Core 设备布线

> [!IMPORTANT]
> Windows 10 IoT 团队正在不再主动维护 arduino 开发。

若要启用的开发和重复使用的常见[Arduino 接线](https://www.arduino.cc/en/Reference/HomePage)IoT Core 设备上的草图，用于绑定 Arduino 的 Visual Studio 项目模板提供作为的一部分[Windows IoT Core 项目模板扩展](https://go.microsoft.com/fwlink/?linkid=847472)。

Arduino 绑定项目模板，开发人员和决策者可以创建、 部署和调试支持使用相同的 Arduino 绑定语言语义的 IoT Core 设备上的接线 Arduino 草图并构造在 arduino 开发平台上可用。 不仅这有助于端口现有 Arduino 草图 IoT 核心版具有很少的费用，而且连接 Arduino 草图 IoT Core 上运行完整 Windows 10 的应用程序可以使用的通用 Windows 平台 (UWP) API。 因此，绑定 Arduino 草图具有完全访问权限的 Api 如通信、 数据访问、 网络、 图形及许多其他可用于创建 Windows 10 IoT Core 设备上运行的端到端方案。 有关开发通用 Windows 平台 (UWP) 应用程序的详细信息，请参阅[构建应用程序的 Windows 10 IoT 核心版](../develop-your-app/BuildingAppsForIoTCore.md)。

此外，Arduino 绑定草图使使用直接内存映射驱动程序提供支持的设备上的高性能。 有关详细信息的性能详细信息，请参阅[Windows IoT 闪电性能测试](../develop-your-app/LightningPerformance.md)报表。

若要启动 Raspberry Pi2、 Pi3 或 Minnowboard 最大生成 Arduino 绑定项目，请参阅[Arduino 连接项目向导](ArduinoWiringProjectGuide.md)。

> [!NOTE]
> Arduino 绑定是*不*DragonBoard 410 c 上当前受支持。
