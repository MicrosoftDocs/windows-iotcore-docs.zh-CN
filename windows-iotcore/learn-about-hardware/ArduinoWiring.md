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
# <a name="arduino-wiring-for-windows-iot-core-devices"></a><span data-ttu-id="6d831-104">适用于 IoT 核心Windows的 Arduino 布线</span><span class="sxs-lookup"><span data-stu-id="6d831-104">Arduino Wiring for Windows IoT Core Devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d831-105">Windows 10 IoT 团队不再主动维护 Arduino。</span><span class="sxs-lookup"><span data-stu-id="6d831-105">The Windows 10 IoT team is no longer actively maintaining Arduino.</span></span>

<span data-ttu-id="6d831-106">若要在 IoT Core 设备上开发和重复使用熟悉的[Arduino](https://www.arduino.cc/en/Reference/HomePage)布线草图，在[Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472)Project 模板扩展中提供了用于 Arduino 布线的 Visual Studio 项目模板。</span><span class="sxs-lookup"><span data-stu-id="6d831-106">To enable the development and reuse of the familiar [Arduino Wiring](https://www.arduino.cc/en/Reference/HomePage) sketches on IoT Core devices, a Visual Studio project template for Arduino Wiring is provided as part of the [Windows IoT Core Project Templates extension](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>

<span data-ttu-id="6d831-107">通过 Arduino 布线项目模板，开发人员和制造商可以使用 Arduino 平台上提供的相同 Arduino 布线语言语义和构造，在支持的 IoT 核心设备上创建、部署和调试 Arduino 布线草图。</span><span class="sxs-lookup"><span data-stu-id="6d831-107">The Arduino Wiring project template enables developers and makers to create, deploy and debug Arduino Wiring sketches on supported IoT Core devices using the same Arduino Wiring language semantics and constructs available on Arduino platforms.</span></span> <span data-ttu-id="6d831-108">这不仅有助于以很少的成本将现有 Arduino 草图移植到 IoT 核心，而且 IoT 核心上运行的 Arduino 线路草图是完整的 Windows 10 应用，可以使用 Univeral Windows Platform (UWP) API。</span><span class="sxs-lookup"><span data-stu-id="6d831-108">Not only this can help port existing Arduino sketches to IoT Core with very little cost, but Arduino Wiring sketches running on IoT Core are full Windows 10 apps that can make use of the Univeral Windows Platform (UWP) API.</span></span> <span data-ttu-id="6d831-109">因此，Arduino 线路草图可以完全访问通信、数据访问、网络、图形等 API，这些 API 可用于创建在 Windows 10 IoT 核心版 设备上运行的端到端方案。</span><span class="sxs-lookup"><span data-stu-id="6d831-109">So, Arduino Wiring sketches have full access to APIs such as communication, data access, networking, graphics, among many others, which can be used to create end to end scenarios running on Windows 10 IoT Core devices.</span></span> <span data-ttu-id="6d831-110">若要详细了解如何开发通用 Windows 平台 (UWP) 应用，请参阅生成适用于 Windows 10 IoT 核心版[的应用程序](../develop-your-app/BuildingAppsForIoTCore.md)。</span><span class="sxs-lookup"><span data-stu-id="6d831-110">For more information on developing Universal Windows Platform (UWP) Apps, please refer to [Building Applications for Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md).</span></span>

<span data-ttu-id="6d831-111">此外，Arduino 布线草图使用直接内存映射驱动程序，该驱动程序在受支持的设备上提供高性能。</span><span class="sxs-lookup"><span data-stu-id="6d831-111">Additionally, Arduino Wiring sketches make use of a direct memory mapped driver that offers high performance on supported devices.</span></span> <span data-ttu-id="6d831-112">有关性能详细信息的详细信息，请参阅 Windows [IoT 闪电性能测试](../develop-your-app/LightningPerformance.md)报表。</span><span class="sxs-lookup"><span data-stu-id="6d831-112">For more details on performance details, please refer to the [Windows IoT Lightning Performance Testing](../develop-your-app/LightningPerformance.md) report.</span></span>

<span data-ttu-id="6d831-113">若要开始为 Raspberry Pi2、Pi3 或 Minnowboard Max 生成 Arduino 布线项目，请参阅 [Arduino 布线项目指南](ArduinoWiringProjectGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="6d831-113">To start building Arduino Wiring projects for Raspberry Pi2, Pi3 or Minnowboard Max, please refer to the [Arduino Wiring project guide](ArduinoWiringProjectGuide.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6d831-114">DragonBoard 410c 当前不支持 Arduino 布线。 </span><span class="sxs-lookup"><span data-stu-id="6d831-114">Arduino Wiring is *not* currently supported on DragonBoard 410c.</span></span>
