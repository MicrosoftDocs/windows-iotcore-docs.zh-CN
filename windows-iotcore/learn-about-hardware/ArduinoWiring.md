---
title: 适用于 Windows IoT 核心设备的 Arduino 布线
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/17
ms.topic: article
description: 了解如何在受支持的 Windows IoT Core 设备上创建、部署和调试 Arduino 接线草图。
keywords: windows iot, Arduino, Arduino 布线, 模板, IoT Core, UWP
ms.openlocfilehash: ee6c64bdfd01e79d26bfa0a6c5f88f7735150393
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744789"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a>适用于 Windows IoT 核心设备的 Arduino 布线

> [!IMPORTANT]
> Windows 10 IoT 团队不再主动维护 Arduino。

为了能够在 IoT Core 设备上进行开发和重复使用熟悉的[Arduino 接线图](https://www.arduino.cc/en/Reference/HomePage), 在[Windows Iot core 项目模板扩展](https://go.microsoft.com/fwlink/?linkid=847472)中提供了用于 Arduino 布线的 Visual Studio 项目模板。

使用 Arduino 布线项目模板, 开发人员和开发人员可以使用 Arduino 平台上提供的相同 Arduino 布线语言语义和构造, 在受支持的 IoT Core 设备上创建、部署和调试 Arduino 布线草绘。 这不仅可以帮助将现有的 Arduino 草绘移植到 IoT 核心, 只需极少的成本, 而在 IoT Core 上运行的 Arduino 接线图是完整的 Windows 10 应用, 可以利用通用 Windows 平台 (UWP) API。 因此, Arduino 布线草绘具有对 Api (如通信、数据访问、网络、图形等) 的完全访问权限, 可用于创建在 Windows 10 IoT Core 设备上运行的端到端方案。 有关开发通用 Windows 平台 (UWP) 应用的详细信息, 请参阅[构建适用于 Windows 10 IoT Core 的应用程序](../develop-your-app/BuildingAppsForIoTCore.md)。

此外, Arduino 布线草绘使用直接内存映射驱动程序, 该驱动程序在支持的设备上提供高性能。 有关性能详细信息的详细信息, 请参阅[Windows IoT 闪电性能测试](../develop-your-app/LightningPerformance.md)报告。

若要开始构建 Raspberry Pi2、Pi3 或 Minnowboard 最大的 Arduino 布线项目, 请参阅[Arduino 布线项目指南](ArduinoWiringProjectGuide.md)。

> [!NOTE]
> DragonBoard 410c 目前*不*支持 Arduino 布线。
