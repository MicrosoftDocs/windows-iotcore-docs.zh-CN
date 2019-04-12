---
title: 快如闪电性能测试
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解如何针对不同平台和语言的 Windows IoT 闪电般的功能和切换频率。
keywords: windows iot、 闪电般的性能、 快如闪电的功能，GPIO
ms.openlocfilehash: 65f6732dd945b199902bb7eb4a9e0cc41aac2131
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510940"
---
# <a name="windows-iot-lightning-performance-testing"></a><span data-ttu-id="a820b-104">Windows IoT Lightning 性能测试</span><span class="sxs-lookup"><span data-stu-id="a820b-104">Windows IoT Lightning Performance Testing</span></span>

<span data-ttu-id="a820b-105">GPIO 性能进行了测试使用一个简单的 GPIO 切换应用程序，Windows IoT 闪电功能[可从以下站点](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)。</span><span class="sxs-lookup"><span data-stu-id="a820b-105">The GPIO performance was tested for Windows IoT Lightning functionality using a simple GPIO toggle app, [available here](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span></span> <span data-ttu-id="a820b-106">通过以尽可能快的速度切换 0 和 1 之间的 GPIO 5 来执行测试。</span><span class="sxs-lookup"><span data-stu-id="a820b-106">The tests were performed by toggling GPIO 5 between 0 and 1 at the fastest possible speed.</span></span> <span data-ttu-id="a820b-107">每个用例的切换频率已使用 Tektronix TP 2024 Oscilloscope 测量。</span><span class="sxs-lookup"><span data-stu-id="a820b-107">The toggle frequency for each case was measured using a Tektronix TPS 2024 Oscilloscope.</span></span>

<span data-ttu-id="a820b-108">通过分析得出以下结果：</span><span class="sxs-lookup"><span data-stu-id="a820b-108">The following results were obtained from the analysis:</span></span>

> | <span data-ttu-id="a820b-109">测试平台</span><span class="sxs-lookup"><span data-stu-id="a820b-109">Platform Tested</span></span>                     | <span data-ttu-id="a820b-110">语言</span><span class="sxs-lookup"><span data-stu-id="a820b-110">Language</span></span>        | <span data-ttu-id="a820b-111">频率</span><span class="sxs-lookup"><span data-stu-id="a820b-111">Frequency</span></span>     |
> | ----------------------------------- | --------------- | ------------- |
> | <span data-ttu-id="a820b-112">Arduino Uno</span><span class="sxs-lookup"><span data-stu-id="a820b-112">Arduino Uno</span></span>                         | <span data-ttu-id="a820b-113">Arduino 草图</span><span class="sxs-lookup"><span data-stu-id="a820b-113">Arduino Sketch</span></span>  | <span data-ttu-id="a820b-114">75.06 kHz</span><span class="sxs-lookup"><span data-stu-id="a820b-114">75.06 kHz</span></span>     |
> | <span data-ttu-id="a820b-115">Windows 10 IoT 核心版本机堆栈</span><span class="sxs-lookup"><span data-stu-id="a820b-115">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="a820b-116">C#</span><span class="sxs-lookup"><span data-stu-id="a820b-116">C#</span></span>              | <span data-ttu-id="a820b-117">239 KHz</span><span class="sxs-lookup"><span data-stu-id="a820b-117">239 KHz</span></span>       |
> | <span data-ttu-id="a820b-118">Windows 10 IoT 核心版本机堆栈</span><span class="sxs-lookup"><span data-stu-id="a820b-118">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="a820b-119">C++/CX</span><span class="sxs-lookup"><span data-stu-id="a820b-119">C++/CX</span></span>          | <span data-ttu-id="a820b-120">278 kHz</span><span class="sxs-lookup"><span data-stu-id="a820b-120">278 kHz</span></span>       |
> | <span data-ttu-id="a820b-121">Windows 10 IoT 核心版本机堆栈</span><span class="sxs-lookup"><span data-stu-id="a820b-121">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="a820b-122">WinJS</span><span class="sxs-lookup"><span data-stu-id="a820b-122">WinJS</span></span>           | <span data-ttu-id="a820b-123">34 kHz</span><span class="sxs-lookup"><span data-stu-id="a820b-123">34 kHz</span></span>        |
> | <span data-ttu-id="a820b-124">Windows 10 IoT 核心版 Arduino 布线</span><span class="sxs-lookup"><span data-stu-id="a820b-124">Windows 10 IoT Core Arduino Wiring</span></span>  | <span data-ttu-id="a820b-125">Arduino 接线</span><span class="sxs-lookup"><span data-stu-id="a820b-125">Arduino Wiring</span></span>  | **<span data-ttu-id="a820b-126">7.36 MHz</span><span class="sxs-lookup"><span data-stu-id="a820b-126">7.36 MHz</span></span>**  |
> | <span data-ttu-id="a820b-127">Windows 10 IoT 核心版 DMAP 堆栈</span><span class="sxs-lookup"><span data-stu-id="a820b-127">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="a820b-128">C#</span><span class="sxs-lookup"><span data-stu-id="a820b-128">C#</span></span>              | **<span data-ttu-id="a820b-129">1.76 MHz</span><span class="sxs-lookup"><span data-stu-id="a820b-129">1.76 MHz</span></span>**  |
> | <span data-ttu-id="a820b-130">Windows 10 IoT 核心版 DMAP 堆栈</span><span class="sxs-lookup"><span data-stu-id="a820b-130">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="a820b-131">C++/CX</span><span class="sxs-lookup"><span data-stu-id="a820b-131">C++/CX</span></span>          | **<span data-ttu-id="a820b-132">3.78 MHz</span><span class="sxs-lookup"><span data-stu-id="a820b-132">3.78 MHz</span></span>**  |
> | <span data-ttu-id="a820b-133">Windows 10 IoT 核心版 DMAP 堆栈</span><span class="sxs-lookup"><span data-stu-id="a820b-133">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="a820b-134">WinJS</span><span class="sxs-lookup"><span data-stu-id="a820b-134">WinJS</span></span>           | <span data-ttu-id="a820b-135">42 kHz</span><span class="sxs-lookup"><span data-stu-id="a820b-135">42 kHz</span></span>        |

<span data-ttu-id="a820b-136">Windows 10 IoT 核心版测试已在使用 Windows 10 IoT Core Insider Preview 构建 15026 (codename Redstone 2) Raspberry Pi 3 上运行，并使用 Microsoft IoT 闪电 SDK 1.1.0 生成。</span><span class="sxs-lookup"><span data-stu-id="a820b-136">Windows 10 IoT Core tests were run on a Raspberry Pi 3 using Windows 10 IoT Core Insider Preview Build 15026 (codename Redstone 2) and built using Microsoft IoT Lightning SDK 1.1.0.</span></span>
