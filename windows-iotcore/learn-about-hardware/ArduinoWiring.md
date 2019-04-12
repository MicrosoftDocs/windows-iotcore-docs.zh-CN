---
title: Arduino 开发适用于 Windows IoT Core 设备布线
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/17
ms.topic: article
description: 了解如何创建、 部署和调试支持的 Windows IoT Core 设备上连接 Arduino 草图。
keywords: windows iot，Arduino，Arduino 绑定，模板中，IoT Core UWP
ms.openlocfilehash: 212e69360e89daafe08c58a7b8bced94ea4410f2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510876"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a><span data-ttu-id="7e216-104">Arduino 开发适用于 Windows IoT Core 设备布线</span><span class="sxs-lookup"><span data-stu-id="7e216-104">Arduino Wiring for Windows IoT Core Devices</span></span>

<span data-ttu-id="7e216-105">若要启用的开发和重复使用的常见[Arduino 接线](https://www.arduino.cc/en/Reference/HomePage)IoT Core 设备上的草图，用于绑定 Arduino 的 Visual Studio 项目模板提供作为的一部分[Windows IoT Core 项目模板扩展](https://go.microsoft.com/fwlink/?linkid=847472)。</span><span class="sxs-lookup"><span data-stu-id="7e216-105">To enable the development and reuse of the familiar [Arduino Wiring](https://www.arduino.cc/en/Reference/HomePage) sketches on IoT Core devices, a Visual Studio project template for Arduino Wiring is provided as part of the [Windows IoT Core Project Templates extension](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>

<span data-ttu-id="7e216-106">Arduino 绑定项目模板，开发人员和决策者可以创建、 部署和调试支持使用相同的 Arduino 绑定语言语义的 IoT Core 设备上的接线 Arduino 草图并构造在 arduino 开发平台上可用。</span><span class="sxs-lookup"><span data-stu-id="7e216-106">The Arduino Wiring project template enables developers and makers to create, deploy and debug Arduino Wiring sketches on supported IoT Core devices using the same Arduino Wiring language semantics and constructs available on Arduino platforms.</span></span> <span data-ttu-id="7e216-107">不仅这有助于端口现有 Arduino 草图 IoT 核心版具有很少的费用，而且连接 Arduino 草图 IoT Core 上运行完整 Windows 10 的应用程序可以使用的通用 Windows 平台 (UWP) API。</span><span class="sxs-lookup"><span data-stu-id="7e216-107">Not only this can help port existing Arduino sketches to IoT Core with very little cost, but Arduino Wiring sketches running on IoT Core are full Windows 10 apps that can make use of the Univeral Windows Platform (UWP) API.</span></span> <span data-ttu-id="7e216-108">因此，绑定 Arduino 草图具有完全访问权限的 Api 如通信、 数据访问、 网络、 图形及许多其他可用于创建 Windows 10 IoT Core 设备上运行的端到端方案。</span><span class="sxs-lookup"><span data-stu-id="7e216-108">So, Arduino Wiring sketches have full access to APIs such as communication, data access, networking, graphics, among many others, which can be used to create end to end scenarios running on Windows 10 IoT Core devices.</span></span> <span data-ttu-id="7e216-109">有关开发通用 Windows 平台 (UWP) 应用程序的详细信息，请参阅[构建应用程序的 Windows 10 IoT 核心版](../develop-your-app/BuildingAppsForIoTCore.md)。</span><span class="sxs-lookup"><span data-stu-id="7e216-109">For more information on developing Universal Windows Platform (UWP) Apps, please refer to [Building Applications for Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md).</span></span>

<span data-ttu-id="7e216-110">此外，Arduino 绑定草图使使用直接内存映射驱动程序提供支持的设备上的高性能。</span><span class="sxs-lookup"><span data-stu-id="7e216-110">Additionally, Arduino Wiring sketches make use of a direct memory mapped driver that offers high performance on supported devices.</span></span> <span data-ttu-id="7e216-111">有关详细信息的性能详细信息，请参阅[Windows IoT 闪电性能测试](../develop-your-app/LightningPerformance.md)报表。</span><span class="sxs-lookup"><span data-stu-id="7e216-111">For more details on performance details, please refer to the [Windows IoT Lightning Performance Testing](../develop-your-app/LightningPerformance.md) report.</span></span>

<span data-ttu-id="7e216-112">若要启动 Raspberry Pi2、 Pi3 或 Minnowboard 最大生成 Arduino 绑定项目，请参阅[Arduino 连接项目向导](ArduinoWiringProjectGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="7e216-112">To start building Arduino Wiring projects for Raspberry Pi2, Pi3 or Minnowboard Max, please refer to the [Arduino Wiring project guide](ArduinoWiringProjectGuide.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7e216-113">Arduino 绑定是*不*DragonBoard 410 c 上当前受支持。</span><span class="sxs-lookup"><span data-stu-id="7e216-113">Arduino Wiring is *not* currently supported on DragonBoard 410c.</span></span>
