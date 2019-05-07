---
title: 快如闪电性能测试
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解如何针对不同平台和语言的 Windows IoT 闪电般的功能和切换频率。
keywords: windows iot、 闪电般的性能、 快如闪电的功能，GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744778"
---
# <a name="windows-iot-lightning-performance-testing"></a><span data-ttu-id="51b6b-104">Windows IoT Lightning 性能测试</span><span class="sxs-lookup"><span data-stu-id="51b6b-104">Windows IoT Lightning Performance Testing</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51b6b-105">Windows 10 IoT 团队不再主动支持 Arduino。</span><span class="sxs-lookup"><span data-stu-id="51b6b-105">The Windows 10 IoT team is no longer actively supporting Arduino.</span></span>

<span data-ttu-id="51b6b-106">GPIO 性能进行了测试使用一个简单的 GPIO 切换应用程序，Windows IoT 闪电功能[可从以下站点](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)。</span><span class="sxs-lookup"><span data-stu-id="51b6b-106">The GPIO performance was tested for Windows IoT Lightning functionality using a simple GPIO toggle app, [available here](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span></span> <span data-ttu-id="51b6b-107">通过以尽可能快的速度切换 0 和 1 之间的 GPIO 5 来执行测试。</span><span class="sxs-lookup"><span data-stu-id="51b6b-107">The tests were performed by toggling GPIO 5 between 0 and 1 at the fastest possible speed.</span></span> <span data-ttu-id="51b6b-108">每个用例的切换频率已使用 Tektronix TP 2024 Oscilloscope 测量。</span><span class="sxs-lookup"><span data-stu-id="51b6b-108">The toggle frequency for each case was measured using a Tektronix TPS 2024 Oscilloscope.</span></span>

<span data-ttu-id="51b6b-109">通过分析得出以下结果：</span><span class="sxs-lookup"><span data-stu-id="51b6b-109">The following results were obtained from the analysis:</span></span>

> | <span data-ttu-id="51b6b-110">测试平台</span><span class="sxs-lookup"><span data-stu-id="51b6b-110">Platform Tested</span></span>                     | <span data-ttu-id="51b6b-111">语言</span><span class="sxs-lookup"><span data-stu-id="51b6b-111">Language</span></span>        | <span data-ttu-id="51b6b-112">频率</span><span class="sxs-lookup"><span data-stu-id="51b6b-112">Frequency</span></span>     |
> | ----------------------------------- | --------------- | ------------- |
> | <span data-ttu-id="51b6b-113">Arduino Uno</span><span class="sxs-lookup"><span data-stu-id="51b6b-113">Arduino Uno</span></span>                         | <span data-ttu-id="51b6b-114">Arduino 草图</span><span class="sxs-lookup"><span data-stu-id="51b6b-114">Arduino Sketch</span></span>  | <span data-ttu-id="51b6b-115">75.06 kHz</span><span class="sxs-lookup"><span data-stu-id="51b6b-115">75.06 kHz</span></span>     |
> | <span data-ttu-id="51b6b-116">Windows 10 IoT 核心版本机堆栈</span><span class="sxs-lookup"><span data-stu-id="51b6b-116">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="51b6b-117">C#</span><span class="sxs-lookup"><span data-stu-id="51b6b-117">C#</span></span>              | <span data-ttu-id="51b6b-118">239 KHz</span><span class="sxs-lookup"><span data-stu-id="51b6b-118">239 KHz</span></span>       |
> | <span data-ttu-id="51b6b-119">Windows 10 IoT 核心版本机堆栈</span><span class="sxs-lookup"><span data-stu-id="51b6b-119">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="51b6b-120">C++/CX</span><span class="sxs-lookup"><span data-stu-id="51b6b-120">C++/CX</span></span>          | <span data-ttu-id="51b6b-121">278 kHz</span><span class="sxs-lookup"><span data-stu-id="51b6b-121">278 kHz</span></span>       |
> | <span data-ttu-id="51b6b-122">Windows 10 IoT 核心版本机堆栈</span><span class="sxs-lookup"><span data-stu-id="51b6b-122">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="51b6b-123">WinJS</span><span class="sxs-lookup"><span data-stu-id="51b6b-123">WinJS</span></span>           | <span data-ttu-id="51b6b-124">34 kHz</span><span class="sxs-lookup"><span data-stu-id="51b6b-124">34 kHz</span></span>        |
> | <span data-ttu-id="51b6b-125">Windows 10 IoT 核心版 Arduino 布线</span><span class="sxs-lookup"><span data-stu-id="51b6b-125">Windows 10 IoT Core Arduino Wiring</span></span>  | <span data-ttu-id="51b6b-126">Arduino 接线</span><span class="sxs-lookup"><span data-stu-id="51b6b-126">Arduino Wiring</span></span>  | <span data-ttu-id="51b6b-127">**7.36 MHz**</span><span class="sxs-lookup"><span data-stu-id="51b6b-127">**7.36 MHz**</span></span>  |
> | <span data-ttu-id="51b6b-128">Windows 10 IoT 核心版 DMAP 堆栈</span><span class="sxs-lookup"><span data-stu-id="51b6b-128">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="51b6b-129">C#</span><span class="sxs-lookup"><span data-stu-id="51b6b-129">C#</span></span>              | <span data-ttu-id="51b6b-130">**1.76 MHz**</span><span class="sxs-lookup"><span data-stu-id="51b6b-130">**1.76 MHz**</span></span>  |
> | <span data-ttu-id="51b6b-131">Windows 10 IoT 核心版 DMAP 堆栈</span><span class="sxs-lookup"><span data-stu-id="51b6b-131">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="51b6b-132">C++/CX</span><span class="sxs-lookup"><span data-stu-id="51b6b-132">C++/CX</span></span>          | <span data-ttu-id="51b6b-133">**3.78 MHz**</span><span class="sxs-lookup"><span data-stu-id="51b6b-133">**3.78 MHz**</span></span>  |
> | <span data-ttu-id="51b6b-134">Windows 10 IoT 核心版 DMAP 堆栈</span><span class="sxs-lookup"><span data-stu-id="51b6b-134">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="51b6b-135">WinJS</span><span class="sxs-lookup"><span data-stu-id="51b6b-135">WinJS</span></span>           | <span data-ttu-id="51b6b-136">42 kHz</span><span class="sxs-lookup"><span data-stu-id="51b6b-136">42 kHz</span></span>        |

<span data-ttu-id="51b6b-137">Windows 10 IoT 核心版测试已在使用 Windows 10 IoT Core Insider Preview 构建 15026 (codename Redstone 2) Raspberry Pi 3 上运行，并使用 Microsoft IoT 闪电 SDK 1.1.0 生成。</span><span class="sxs-lookup"><span data-stu-id="51b6b-137">Windows 10 IoT Core tests were run on a Raspberry Pi 3 using Windows 10 IoT Core Insider Preview Build 15026 (codename Redstone 2) and built using Microsoft IoT Lightning SDK 1.1.0.</span></span>
