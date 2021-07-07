---
title: 通用驱动程序创建
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何创建通用驱动程序，以便跨设备创建单个驱动程序包。
keywords: windows iot， 通用驱动程序， 驱动程序， Windows 10， UWP
ms.openlocfilehash: f3b65b084d35cb95253c39b52b3cf9b14108568e
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229654"
---
# <a name="universal-driver-creation"></a><span data-ttu-id="79cb9-104">通用驱动程序创建</span><span class="sxs-lookup"><span data-stu-id="79cb9-104">Universal Driver Creation</span></span>

<span data-ttu-id="79cb9-105">本文档将介绍为 IoT Core 设备创建通用驱动程序。</span><span class="sxs-lookup"><span data-stu-id="79cb9-105">This document will walk you through the creation of Universal Drivers for your IoT Core device.</span></span>

<span data-ttu-id="79cb9-106">通用驱动程序允许创建一个驱动程序包，该包跨运行基于 UWP 的版本的多个设备类型运行，Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="79cb9-106">Universal Drivers enable you to create a single driver package that runs across several device types running UWP-based editions of Windows 10, including IoT Core.</span></span>

<span data-ttu-id="79cb9-107">此驱动程序包包含通用 INF 文件和多个二进制文件。</span><span class="sxs-lookup"><span data-stu-id="79cb9-107">This driver package contains a Universal INF file and several binaries.</span></span> <span data-ttu-id="79cb9-108">每个要求如下：</span><span class="sxs-lookup"><span data-stu-id="79cb9-108">The requirements for each are as follows:</span></span>
- <span data-ttu-id="79cb9-109">通用 INF 文件只能使用基于 UWP 的版本支持的[INF](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file)语法的子集Windows。</span><span class="sxs-lookup"><span data-stu-id="79cb9-109">Universal INF files can only use [the subset of INF syntax supported on UWP-based editions of Windows](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file).</span></span> <span data-ttu-id="79cb9-110">编写 INF 文件时，请使用 [InfVerif](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) 工具验证该文件是否遵循该语法。</span><span class="sxs-lookup"><span data-stu-id="79cb9-110">While writing your INF file, use the [InfVerif tool](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) to verify that the file adheres to that syntax.</span></span>

- <span data-ttu-id="79cb9-111">二进制文件只能使用文档参考页上标记为通用版本的 Windows 10 () 支持的设备驱动程序接口[：KMDF、UMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index) [2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2)或 Windows 驱动程序模型 (WDM) 。</span><span class="sxs-lookup"><span data-stu-id="79cb9-111">binaries can only use device driver interfaces supported on UWP-based editions of Windows 10 (marked as Universal on the documentation reference pages): [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), or the Windows Driver Model (WDM).</span></span> <span data-ttu-id="79cb9-112">它们只能调用子子集中包含的OneCore API。</span><span class="sxs-lookup"><span data-stu-id="79cb9-112">They can also only call APIs included in the OneCore Subset.</span></span> <span data-ttu-id="79cb9-113">使用 [ApiValidator 工具](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) 验证二进制文件调用的 API 是否有效。</span><span class="sxs-lookup"><span data-stu-id="79cb9-113">Use the [ApiValidator tool](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) to verify that the APIs your binaries call are valid.</span></span>

<span data-ttu-id="79cb9-114">若要了解如何在 **Visual Studio** 创建驱动程序包，请访问 [创建驱动程序包](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span><span class="sxs-lookup"><span data-stu-id="79cb9-114">To learn how to **create a driver package in Visual Studio**, please visit [Creating a Driver Package](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span></span>

<span data-ttu-id="79cb9-115">如果需要一 **个示例来帮助你在 IoT 核心** 上创建通用驱动程序，请访问通用 [驱动程序示例](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span><span class="sxs-lookup"><span data-stu-id="79cb9-115">If you would like **a sample to help you create a Universal Driver on IoT Core**, please visit our [Universal Driver sample](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span></span>

## <a name="additional-universal-driver-resources"></a><span data-ttu-id="79cb9-116">其他通用驱动程序资源</span><span class="sxs-lookup"><span data-stu-id="79cb9-116">Additional Universal Driver Resources</span></span>

1. <span data-ttu-id="79cb9-117">有关开发通用 **驱动程序** 包时的设计原则与最佳做法的更多详细信息，请访问入门 [驱动程序的驱动程序](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span><span class="sxs-lookup"><span data-stu-id="79cb9-117">For additional details on **design principles** and **best practices** when developing a Universal Driver package, please visit [Getting Started with Universal Drivers](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span></span>

2. <span data-ttu-id="79cb9-118">有关调试 **通用驱动程序的帮助，** 请访问 [调试通用Windows驱动程序](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver)。</span><span class="sxs-lookup"><span data-stu-id="79cb9-118">For help **debugging your Universal Driver**, please visit [Debugging a Universal Windows driver](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).</span></span>

