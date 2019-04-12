---
title: 通用驱动程序创建
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解如何创建通用驱动程序以在设备上启用单个驱动程序创建包。
keywords: windows iot、 通用驱动程序，驱动程序，Windows 10，UWP
ms.openlocfilehash: 839a742598481e3ff70e3a0ccf1ff072bd62e051
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510625"
---
# <a name="universal-driver-creation"></a><span data-ttu-id="83d8a-104">通用驱动程序创建</span><span class="sxs-lookup"><span data-stu-id="83d8a-104">Universal Driver Creation</span></span>

<span data-ttu-id="83d8a-105">本文档将指导你通过 IoT Core 设备创建通用驱动程序。</span><span class="sxs-lookup"><span data-stu-id="83d8a-105">This document will walk you through the creation of Universal Drivers for your IoT Core device.</span></span>

<span data-ttu-id="83d8a-106">通用驱动程序，可以创建运行跨多个运行基于 UWP 的 Windows 10，包括 IoT Core 版本的设备类型的单个驱动程序包。</span><span class="sxs-lookup"><span data-stu-id="83d8a-106">Universal Drivers enable you to create a single driver package that runs across several device types running UWP-based editions of Windows 10, including IoT Core.</span></span>

<span data-ttu-id="83d8a-107">此驱动程序包包含通用 INF 文件和多个二进制文件。</span><span class="sxs-lookup"><span data-stu-id="83d8a-107">This driver package contains a Universal INF file and several binaries.</span></span> <span data-ttu-id="83d8a-108">每个的要求如下所示：</span><span class="sxs-lookup"><span data-stu-id="83d8a-108">The requirements for each are as follows:</span></span>
- <span data-ttu-id="83d8a-109">只能使用通用 INF 文件[INF 基于 UWP 的 Windows 版本上受支持的语法的子集](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file)。</span><span class="sxs-lookup"><span data-stu-id="83d8a-109">Universal INF files can only use [the subset of INF syntax supported on UWP-based editions of Windows](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file).</span></span> <span data-ttu-id="83d8a-110">在编写您的 INF 文件，使用[InfVerif 工具](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif)以验证是否在文件遵循该语法。</span><span class="sxs-lookup"><span data-stu-id="83d8a-110">While writing your INF file, use the [InfVerif tool](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) to verify that the file adheres to that syntax.</span></span>

- <span data-ttu-id="83d8a-111">基于 UWP 的 Windows 10 （标记为通用文档参考页上） 的版本上支持的设备驱动程序接口，可以仅使用二进制文件：[KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index)， [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2)，或 Windows 驱动程序模型 (WDM)。</span><span class="sxs-lookup"><span data-stu-id="83d8a-111">binaries can only use device driver interfaces supported on UWP-based editions of Windows 10 (marked as Universal on the documentation reference pages): [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), or the Windows Driver Model (WDM).</span></span> <span data-ttu-id="83d8a-112">它们也只能调用 OneCore 子集中包括的 Api。</span><span class="sxs-lookup"><span data-stu-id="83d8a-112">They can also only call APIs included in the OneCore Subset.</span></span> <span data-ttu-id="83d8a-113">使用[ApiValidator 工具](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers)以验证您的二进制文件的 Api 调用都有效。</span><span class="sxs-lookup"><span data-stu-id="83d8a-113">Use the [ApiValidator tool](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) to verify that the APIs your binaries call are valid.</span></span>

<span data-ttu-id="83d8a-114">若要了解如何**Visual Studio 中创建驱动程序包**，请访问[创建驱动程序包](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span><span class="sxs-lookup"><span data-stu-id="83d8a-114">To learn how to **create a driver package in Visual Studio**, please visit [Creating a Driver Package](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span></span>

<span data-ttu-id="83d8a-115">如果想要**示例，帮助你在 IoT Core 上创建通用驱动程序**，请访问我们[通用驱动程序示例](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span><span class="sxs-lookup"><span data-stu-id="83d8a-115">If you would like **a sample to help you create a Universal Driver on IoT Core**, please visit our [Universal Driver sample](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span></span>

## <a name="additional-universal-driver-resources"></a><span data-ttu-id="83d8a-116">其他的通用驱动程序资源</span><span class="sxs-lookup"><span data-stu-id="83d8a-116">Additional Universal Driver Resources</span></span>

1. <span data-ttu-id="83d8a-117">有关其他详细信息**设计原则**并**最佳做法**开发时的通用驱动程序包，请访问[通用驱动程序入门](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span><span class="sxs-lookup"><span data-stu-id="83d8a-117">For additional details on **design principles** and **best practices** when developing a Universal Driver package, please visit [Getting Started with Universal Drivers](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span></span>

2. <span data-ttu-id="83d8a-118">获取帮助**调试您的通用驱动程序**，请访问[调试通用 Windows 驱动程序](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver)。</span><span class="sxs-lookup"><span data-stu-id="83d8a-118">For help **debugging your Universal Driver**, please visit [Debugging a Universal Windows driver](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).</span></span>

