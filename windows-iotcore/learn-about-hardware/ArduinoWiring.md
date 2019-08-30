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
# <a name="arduino-wiring-for-windows-iot-core-devices"></a><span data-ttu-id="9ce9c-104">适用于 Windows IoT 核心设备的 Arduino 布线</span><span class="sxs-lookup"><span data-stu-id="9ce9c-104">Arduino Wiring for Windows IoT Core Devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ce9c-105">Windows 10 IoT 团队不再主动维护 Arduino。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-105">The Windows 10 IoT team is no longer actively maintaining Arduino.</span></span>

<span data-ttu-id="9ce9c-106">为了能够在 IoT Core 设备上进行开发和重复使用熟悉的[Arduino 接线图](https://www.arduino.cc/en/Reference/HomePage), 在[Windows Iot core 项目模板扩展](https://go.microsoft.com/fwlink/?linkid=847472)中提供了用于 Arduino 布线的 Visual Studio 项目模板。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-106">To enable the development and reuse of the familiar [Arduino Wiring](https://www.arduino.cc/en/Reference/HomePage) sketches on IoT Core devices, a Visual Studio project template for Arduino Wiring is provided as part of the [Windows IoT Core Project Templates extension](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>

<span data-ttu-id="9ce9c-107">使用 Arduino 布线项目模板, 开发人员和开发人员可以使用 Arduino 平台上提供的相同 Arduino 布线语言语义和构造, 在受支持的 IoT Core 设备上创建、部署和调试 Arduino 布线草绘。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-107">The Arduino Wiring project template enables developers and makers to create, deploy and debug Arduino Wiring sketches on supported IoT Core devices using the same Arduino Wiring language semantics and constructs available on Arduino platforms.</span></span> <span data-ttu-id="9ce9c-108">这不仅可以帮助将现有的 Arduino 草绘移植到 IoT 核心, 只需极少的成本, 而在 IoT Core 上运行的 Arduino 接线图是完整的 Windows 10 应用, 可以利用通用 Windows 平台 (UWP) API。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-108">Not only this can help port existing Arduino sketches to IoT Core with very little cost, but Arduino Wiring sketches running on IoT Core are full Windows 10 apps that can make use of the Univeral Windows Platform (UWP) API.</span></span> <span data-ttu-id="9ce9c-109">因此, Arduino 布线草绘具有对 Api (如通信、数据访问、网络、图形等) 的完全访问权限, 可用于创建在 Windows 10 IoT Core 设备上运行的端到端方案。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-109">So, Arduino Wiring sketches have full access to APIs such as communication, data access, networking, graphics, among many others, which can be used to create end to end scenarios running on Windows 10 IoT Core devices.</span></span> <span data-ttu-id="9ce9c-110">有关开发通用 Windows 平台 (UWP) 应用的详细信息, 请参阅[构建适用于 Windows 10 IoT Core 的应用程序](../develop-your-app/BuildingAppsForIoTCore.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-110">For more information on developing Universal Windows Platform (UWP) Apps, please refer to [Building Applications for Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md).</span></span>

<span data-ttu-id="9ce9c-111">此外, Arduino 布线草绘使用直接内存映射驱动程序, 该驱动程序在支持的设备上提供高性能。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-111">Additionally, Arduino Wiring sketches make use of a direct memory mapped driver that offers high performance on supported devices.</span></span> <span data-ttu-id="9ce9c-112">有关性能详细信息的详细信息, 请参阅[Windows IoT 闪电性能测试](../develop-your-app/LightningPerformance.md)报告。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-112">For more details on performance details, please refer to the [Windows IoT Lightning Performance Testing](../develop-your-app/LightningPerformance.md) report.</span></span>

<span data-ttu-id="9ce9c-113">若要开始构建 Raspberry Pi2、Pi3 或 Minnowboard 最大的 Arduino 布线项目, 请参阅[Arduino 布线项目指南](ArduinoWiringProjectGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-113">To start building Arduino Wiring projects for Raspberry Pi2, Pi3 or Minnowboard Max, please refer to the [Arduino Wiring project guide](ArduinoWiringProjectGuide.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9ce9c-114">DragonBoard 410c 目前*不*支持 Arduino 布线。</span><span class="sxs-lookup"><span data-stu-id="9ce9c-114">Arduino Wiring is *not* currently supported on DragonBoard 410c.</span></span>
