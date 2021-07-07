---
title: 闪电性能测试
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解不同平台和语言的 Windows IoT 闪电功能和切换频率。
keywords: windows iot，闪电性能，闪电功能，GPIO
ms.openlocfilehash: e833b9614a648276067d55c61688f1c2d213810c
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229013"
---
# <a name="windows-iot-lightning-performance-testing"></a><span data-ttu-id="4186b-104">WindowsIoT 闪电性能测试</span><span class="sxs-lookup"><span data-stu-id="4186b-104">Windows IoT Lightning Performance Testing</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4186b-105">Windows 10 IoT 团队不再主动支持 Arduino。</span><span class="sxs-lookup"><span data-stu-id="4186b-105">The Windows 10 IoT team is no longer actively supporting Arduino.</span></span>

<span data-ttu-id="4186b-106">使用简单的 gpio 切换应用（[可从此处获取](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)）为 Windows IoT 闪电功能测试了 GPIO 性能。</span><span class="sxs-lookup"><span data-stu-id="4186b-106">The GPIO performance was tested for Windows IoT Lightning functionality using a simple GPIO toggle app, [available here](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span></span> <span data-ttu-id="4186b-107">这些测试是通过在0和1之间切换，以最快的速度来执行的。</span><span class="sxs-lookup"><span data-stu-id="4186b-107">The tests were performed by toggling GPIO 5 between 0 and 1 at the fastest possible speed.</span></span> <span data-ttu-id="4186b-108">每个事例的切换频率均使用 Tektronix TPS 2024 Oscilloscope 进行度量。</span><span class="sxs-lookup"><span data-stu-id="4186b-108">The toggle frequency for each case was measured using a Tektronix TPS 2024 Oscilloscope.</span></span>

<span data-ttu-id="4186b-109">以下结果是从分析获得的：</span><span class="sxs-lookup"><span data-stu-id="4186b-109">The following results were obtained from the analysis:</span></span>

> | <span data-ttu-id="4186b-110">已测试平台</span><span class="sxs-lookup"><span data-stu-id="4186b-110">Platform Tested</span></span>                     | <span data-ttu-id="4186b-111">语言</span><span class="sxs-lookup"><span data-stu-id="4186b-111">Language</span></span>        | <span data-ttu-id="4186b-112">频率</span><span class="sxs-lookup"><span data-stu-id="4186b-112">Frequency</span></span>     |
> | ----------------------------------- | --------------- | ------------- |
> | <span data-ttu-id="4186b-113">Arduino Uno</span><span class="sxs-lookup"><span data-stu-id="4186b-113">Arduino Uno</span></span>                         | <span data-ttu-id="4186b-114">Arduino 草图</span><span class="sxs-lookup"><span data-stu-id="4186b-114">Arduino Sketch</span></span>  | <span data-ttu-id="4186b-115">75.06 kHz</span><span class="sxs-lookup"><span data-stu-id="4186b-115">75.06 kHz</span></span>     |
> | <span data-ttu-id="4186b-116">Windows 10 IoT 核心版本机堆栈</span><span class="sxs-lookup"><span data-stu-id="4186b-116">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="4186b-117">C#</span><span class="sxs-lookup"><span data-stu-id="4186b-117">C#</span></span>              | <span data-ttu-id="4186b-118">239 KHz</span><span class="sxs-lookup"><span data-stu-id="4186b-118">239 KHz</span></span>       |
> | <span data-ttu-id="4186b-119">Windows 10 IoT 核心版本机堆栈</span><span class="sxs-lookup"><span data-stu-id="4186b-119">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="4186b-120">C++/CX</span><span class="sxs-lookup"><span data-stu-id="4186b-120">C++/CX</span></span>          | <span data-ttu-id="4186b-121">278 kHz</span><span class="sxs-lookup"><span data-stu-id="4186b-121">278 kHz</span></span>       |
> | <span data-ttu-id="4186b-122">Windows 10 IoT 核心版本机堆栈</span><span class="sxs-lookup"><span data-stu-id="4186b-122">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="4186b-123">WinJS</span><span class="sxs-lookup"><span data-stu-id="4186b-123">WinJS</span></span>           | <span data-ttu-id="4186b-124">34 kHz</span><span class="sxs-lookup"><span data-stu-id="4186b-124">34 kHz</span></span>        |
> | <span data-ttu-id="4186b-125">Windows 10 IoT 核心版Arduino 布线</span><span class="sxs-lookup"><span data-stu-id="4186b-125">Windows 10 IoT Core Arduino Wiring</span></span>  | <span data-ttu-id="4186b-126">Arduino 布线</span><span class="sxs-lookup"><span data-stu-id="4186b-126">Arduino Wiring</span></span>  | <span data-ttu-id="4186b-127">**7.36 MHz**</span><span class="sxs-lookup"><span data-stu-id="4186b-127">**7.36 MHz**</span></span>  |
> | <span data-ttu-id="4186b-128">Windows 10 IoT 核心版DMAP 堆栈</span><span class="sxs-lookup"><span data-stu-id="4186b-128">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="4186b-129">C#</span><span class="sxs-lookup"><span data-stu-id="4186b-129">C#</span></span>              | <span data-ttu-id="4186b-130">**1.76 MHz**</span><span class="sxs-lookup"><span data-stu-id="4186b-130">**1.76 MHz**</span></span>  |
> | <span data-ttu-id="4186b-131">Windows 10 IoT 核心版DMAP 堆栈</span><span class="sxs-lookup"><span data-stu-id="4186b-131">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="4186b-132">C++/CX</span><span class="sxs-lookup"><span data-stu-id="4186b-132">C++/CX</span></span>          | <span data-ttu-id="4186b-133">**3.78 MHz**</span><span class="sxs-lookup"><span data-stu-id="4186b-133">**3.78 MHz**</span></span>  |
> | <span data-ttu-id="4186b-134">Windows 10 IoT 核心版DMAP 堆栈</span><span class="sxs-lookup"><span data-stu-id="4186b-134">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="4186b-135">WinJS</span><span class="sxs-lookup"><span data-stu-id="4186b-135">WinJS</span></span>           | <span data-ttu-id="4186b-136">42 kHz</span><span class="sxs-lookup"><span data-stu-id="4186b-136">42 kHz</span></span>        |

<span data-ttu-id="4186b-137">使用 Windows 10 IoT 核心版有问必答 preview Build 15026 (codename Redstone 2) 并使用 Microsoft IoT 闪电 SDK 1.1.0 构建 Windows 10 IoT 核心版测试在 Raspberry Pi 3 上运行。</span><span class="sxs-lookup"><span data-stu-id="4186b-137">Windows 10 IoT Core tests were run on a Raspberry Pi 3 using Windows 10 IoT Core Insider Preview Build 15026 (codename Redstone 2) and built using Microsoft IoT Lightning SDK 1.1.0.</span></span>
