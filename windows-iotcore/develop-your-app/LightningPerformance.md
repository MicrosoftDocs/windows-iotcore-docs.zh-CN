---
title: 闪电性能测试
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解适用于不同平台和语言的 Windows IoT 闪电功能和切换频率。
keywords: windows iot, 闪电性能, 闪电功能, GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744778"
---
# <a name="windows-iot-lightning-performance-testing"></a><span data-ttu-id="2bf70-104">Windows IoT Lightning 性能测试</span><span class="sxs-lookup"><span data-stu-id="2bf70-104">Windows IoT Lightning Performance Testing</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2bf70-105">Windows 10 IoT 团队不再主动支持 Arduino。</span><span class="sxs-lookup"><span data-stu-id="2bf70-105">The Windows 10 IoT team is no longer actively supporting Arduino.</span></span>

<span data-ttu-id="2bf70-106">使用简单的 GPIO 切换应用 ([此处提供](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)了) 对 Windows IoT 闪电功能测试了 GPIO 性能。</span><span class="sxs-lookup"><span data-stu-id="2bf70-106">The GPIO performance was tested for Windows IoT Lightning functionality using a simple GPIO toggle app, [available here](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span></span> <span data-ttu-id="2bf70-107">通过以尽可能快的速度切换 0 和 1 之间的 GPIO 5 来执行测试。</span><span class="sxs-lookup"><span data-stu-id="2bf70-107">The tests were performed by toggling GPIO 5 between 0 and 1 at the fastest possible speed.</span></span> <span data-ttu-id="2bf70-108">每个事例的切换频率均使用 Tektronix TPS 2024 Oscilloscope 进行度量。</span><span class="sxs-lookup"><span data-stu-id="2bf70-108">The toggle frequency for each case was measured using a Tektronix TPS 2024 Oscilloscope.</span></span>

<span data-ttu-id="2bf70-109">通过分析得出以下结果：</span><span class="sxs-lookup"><span data-stu-id="2bf70-109">The following results were obtained from the analysis:</span></span>

> | <span data-ttu-id="2bf70-110">测试平台</span><span class="sxs-lookup"><span data-stu-id="2bf70-110">Platform Tested</span></span>                     | <span data-ttu-id="2bf70-111">语言</span><span class="sxs-lookup"><span data-stu-id="2bf70-111">Language</span></span>        | <span data-ttu-id="2bf70-112">频率</span><span class="sxs-lookup"><span data-stu-id="2bf70-112">Frequency</span></span>     |
> | ----------------------------------- | --------------- | ------------- |
> | <span data-ttu-id="2bf70-113">Arduino Uno</span><span class="sxs-lookup"><span data-stu-id="2bf70-113">Arduino Uno</span></span>                         | <span data-ttu-id="2bf70-114">Arduino 草图</span><span class="sxs-lookup"><span data-stu-id="2bf70-114">Arduino Sketch</span></span>  | <span data-ttu-id="2bf70-115">75.06 kHz</span><span class="sxs-lookup"><span data-stu-id="2bf70-115">75.06 kHz</span></span>     |
> | <span data-ttu-id="2bf70-116">Windows 10 IoT 核心本机堆栈</span><span class="sxs-lookup"><span data-stu-id="2bf70-116">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="2bf70-117">C#</span><span class="sxs-lookup"><span data-stu-id="2bf70-117">C#</span></span>              | <span data-ttu-id="2bf70-118">239 KHz</span><span class="sxs-lookup"><span data-stu-id="2bf70-118">239 KHz</span></span>       |
> | <span data-ttu-id="2bf70-119">Windows 10 IoT 核心本机堆栈</span><span class="sxs-lookup"><span data-stu-id="2bf70-119">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="2bf70-120">C++/CX</span><span class="sxs-lookup"><span data-stu-id="2bf70-120">C++/CX</span></span>          | <span data-ttu-id="2bf70-121">278 kHz</span><span class="sxs-lookup"><span data-stu-id="2bf70-121">278 kHz</span></span>       |
> | <span data-ttu-id="2bf70-122">Windows 10 IoT 核心本机堆栈</span><span class="sxs-lookup"><span data-stu-id="2bf70-122">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="2bf70-123">WinJS</span><span class="sxs-lookup"><span data-stu-id="2bf70-123">WinJS</span></span>           | <span data-ttu-id="2bf70-124">34 kHz</span><span class="sxs-lookup"><span data-stu-id="2bf70-124">34 kHz</span></span>        |
> | <span data-ttu-id="2bf70-125">Windows 10 IoT Core Arduino 布线</span><span class="sxs-lookup"><span data-stu-id="2bf70-125">Windows 10 IoT Core Arduino Wiring</span></span>  | <span data-ttu-id="2bf70-126">Arduino 接线</span><span class="sxs-lookup"><span data-stu-id="2bf70-126">Arduino Wiring</span></span>  | <span data-ttu-id="2bf70-127">**7.36 MHz**</span><span class="sxs-lookup"><span data-stu-id="2bf70-127">**7.36 MHz**</span></span>  |
> | <span data-ttu-id="2bf70-128">Windows 10 IoT Core DMAP Stack</span><span class="sxs-lookup"><span data-stu-id="2bf70-128">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="2bf70-129">C#</span><span class="sxs-lookup"><span data-stu-id="2bf70-129">C#</span></span>              | <span data-ttu-id="2bf70-130">**1.76 MHz**</span><span class="sxs-lookup"><span data-stu-id="2bf70-130">**1.76 MHz**</span></span>  |
> | <span data-ttu-id="2bf70-131">Windows 10 IoT Core DMAP Stack</span><span class="sxs-lookup"><span data-stu-id="2bf70-131">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="2bf70-132">C++/CX</span><span class="sxs-lookup"><span data-stu-id="2bf70-132">C++/CX</span></span>          | <span data-ttu-id="2bf70-133">**3.78 MHz**</span><span class="sxs-lookup"><span data-stu-id="2bf70-133">**3.78 MHz**</span></span>  |
> | <span data-ttu-id="2bf70-134">Windows 10 IoT Core DMAP Stack</span><span class="sxs-lookup"><span data-stu-id="2bf70-134">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="2bf70-135">WinJS</span><span class="sxs-lookup"><span data-stu-id="2bf70-135">WinJS</span></span>           | <span data-ttu-id="2bf70-136">42 kHz</span><span class="sxs-lookup"><span data-stu-id="2bf70-136">42 kHz</span></span>        |

<span data-ttu-id="2bf70-137">Windows 10 IoT 核心测试使用 Windows 10 IoT Core 有问必答 Preview Build 15026 (codename Redstone 2) 在 Raspberry Pi 3 上运行, 并使用 Microsoft IoT 闪电 SDK 1.1.0 构建。</span><span class="sxs-lookup"><span data-stu-id="2bf70-137">Windows 10 IoT Core tests were run on a Raspberry Pi 3 using Windows 10 IoT Core Insider Preview Build 15026 (codename Redstone 2) and built using Microsoft IoT Lightning SDK 1.1.0.</span></span>
