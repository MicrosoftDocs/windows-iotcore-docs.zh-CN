---
title: 通用驱动程序创建
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何创建通用驱动程序，以便跨设备启用单个驱动程序包创建。
keywords: windows iot，通用驱动程序，驱动程序，Windows 10，UWP
ms.openlocfilehash: 0a3707d694f0eabd2dafe35aecdbb9e88415a23a
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655833"
---
# <a name="universal-driver-creation"></a><span data-ttu-id="b404d-104">通用驱动程序创建</span><span class="sxs-lookup"><span data-stu-id="b404d-104">Universal Driver Creation</span></span>

<span data-ttu-id="b404d-105">本文档将引导你完成为 IoT 核心设备创建通用驱动程序的过程。</span><span class="sxs-lookup"><span data-stu-id="b404d-105">This document will walk you through the creation of Universal Drivers for your IoT Core device.</span></span>

<span data-ttu-id="b404d-106">利用通用驱动程序，你可以创建单个驱动程序包，该程序包可跨多个运行基于 UWP 的 Windows 10 版本的设备类型运行，包括 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="b404d-106">Universal Drivers enable you to create a single driver package that runs across several device types running UWP-based editions of Windows 10, including IoT Core.</span></span>

<span data-ttu-id="b404d-107">此驱动程序包包含通用 INF 文件和多个二进制文件。</span><span class="sxs-lookup"><span data-stu-id="b404d-107">This driver package contains a Universal INF file and several binaries.</span></span> <span data-ttu-id="b404d-108">每个的要求如下：</span><span class="sxs-lookup"><span data-stu-id="b404d-108">The requirements for each are as follows:</span></span>
- <span data-ttu-id="b404d-109">通用 INF 文件只能使用 [基于 UWP 的 Windows 版本上支持的 INF 语法的子集](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file)。</span><span class="sxs-lookup"><span data-stu-id="b404d-109">Universal INF files can only use [the subset of INF syntax supported on UWP-based editions of Windows](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file).</span></span> <span data-ttu-id="b404d-110">编写 INF 文件时，请使用 [InfVerif 工具](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) 验证该文件是否符合该语法。</span><span class="sxs-lookup"><span data-stu-id="b404d-110">While writing your INF file, use the [InfVerif tool](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) to verify that the file adheres to that syntax.</span></span>

- <span data-ttu-id="b404d-111">二进制文件只能使用在文档引用页面上标记为通用的基于 UWP 版本的 Windows 10 (设备驱动程序接口，) ： [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index)、 [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2)或 Windows 驱动模型 (WDM) 。</span><span class="sxs-lookup"><span data-stu-id="b404d-111">binaries can only use device driver interfaces supported on UWP-based editions of Windows 10 (marked as Universal on the documentation reference pages): [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), or the Windows Driver Model (WDM).</span></span> <span data-ttu-id="b404d-112">它们还可以仅调用 OneCore 子集中包含的 Api。</span><span class="sxs-lookup"><span data-stu-id="b404d-112">They can also only call APIs included in the OneCore Subset.</span></span> <span data-ttu-id="b404d-113">使用 [ApiValidator 工具](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) 验证你的二进制文件调用的 api 是否有效。</span><span class="sxs-lookup"><span data-stu-id="b404d-113">Use the [ApiValidator tool](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) to verify that the APIs your binaries call are valid.</span></span>

<span data-ttu-id="b404d-114">若要了解如何 **在 Visual Studio 中创建驱动程序包**，请访问 [创建驱动程序包](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span><span class="sxs-lookup"><span data-stu-id="b404d-114">To learn how to **create a driver package in Visual Studio**, please visit [Creating a Driver Package](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span></span>

<span data-ttu-id="b404d-115">如果你想要 **一个示例来帮助你在 IoT Core 上创建通用驱动程序**，请访问我们的 [通用驱动程序示例](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span><span class="sxs-lookup"><span data-stu-id="b404d-115">If you would like **a sample to help you create a Universal Driver on IoT Core**, please visit our [Universal Driver sample](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span></span>

## <a name="additional-universal-driver-resources"></a><span data-ttu-id="b404d-116">其他通用驱动程序资源</span><span class="sxs-lookup"><span data-stu-id="b404d-116">Additional Universal Driver Resources</span></span>

1. <span data-ttu-id="b404d-117">有关开发通用驱动程序包时的 **设计原则** 和 **最佳做法** 的其他详细信息，请访问 [使用通用驱动程序入门](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span><span class="sxs-lookup"><span data-stu-id="b404d-117">For additional details on **design principles** and **best practices** when developing a Universal Driver package, please visit [Getting Started with Universal Drivers](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span></span>

2. <span data-ttu-id="b404d-118">有关 **调试通用驱动程序**的帮助，请访问 [调试通用 Windows 驱动程序](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver)。</span><span class="sxs-lookup"><span data-stu-id="b404d-118">For help **debugging your Universal Driver**, please visit [Debugging a Universal Windows driver](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).</span></span>

